---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Customizing

With [{{site.data.keyword.knowledgestudiofull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/watsonknowledgestudio), you can
extend {{site.data.keyword.nlushort}} with custom models that identify custom
entities and relations unique to your domain.
{: shortdesc}

## Getting started with custom models

> The {{site.data.keyword.nlushort}} Free plan limits the size and performance of your custom model. To test a custom model to its full extent, you will need to use it with the {{site.data.keyword.nlushort}} Standard plan.

1. If you haven't done so already, [get started](/docs/services/natural-language-understanding/getting-started.html) with {{site.data.keyword.nlushort}}.
1. [Get access to {{site.data.keyword.knowledgestudioshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top), and log in through the [online dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/).
1. View the {{site.data.keyword.knowledgestudioshort}} [documentation](/docs/services/knowledge-studio/index.html) to learn how to create a custom model (annotator) and deploy it to {{site.data.keyword.nlushort}}.
1. To use your model, specify the `model` that you deployed in the
[entities ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} or
[relations ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} options of your API request:
    - Example *parameters.json* file:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - Example curl request:

        ```bash
        curl --user "{username}":"{password}" \        
        "{url}/v1/analyze?version=2018-03-16" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}
        

## Deleting a custom model

The number of custom models that you deploy to {{site.data.keyword.nlushort}} affects your {{site.data.keyword.nlushort}} bill according to your [pricing plan](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). To avoid charges for a model that you no longer use, [undeploy the model with {{site.data.keyword.knowledgestudioshort}}](https://console.bluemix.net/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model), or undeploy the model with the **[Delete model](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#delete-model)** method.

Example curl request:
    
```bash
curl --user "{username}":"{password}" \
"{url}/v1/models/{model_id}?version=2018-03-16" \
--request DELETE
```
{: pre}

