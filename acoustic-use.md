---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-24"

subcollection: speech-to-text-data

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Using a custom acoustic model
{: #acousticUse}

Once you create and train your custom acoustic model, you can use it in speech recognition requests. You use the `acoustic_customization_id` query parameter to specify the custom acoustic model for a request, as shown in the following examples. You must issue the request with credentials for the instance of the service that owns the model.
{: shortdesc}

You can also specify a custom language model to be used with the request, which can increase transcription accuracy. For more information, see [Using custom language and custom acoustic models during speech recognition](/docs/services/speech-to-text-data?topic=speech-to-text-data-useBoth#useBothRecognize).

You can create multiple custom acoustic models for the same or different domains or environments. However, you can specify only one custom acoustic model at a time with the `acoustic_customization_id` parameter.

-   For the [WebSocket interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-websockets), use the `/v1/recognize` method. The specified custom model is used for all requests that are sent over the connection.

    ```javascript
    var my_access_token = '{token}';
    var wsURI = '{ws_url}/v1/recognize'
      + '?access_token=' + my_access_token
      + '&model=en-US_NarrowbandModel'
      + '&acoustic_customization_id={customization_id}';
    var websocket = new WebSocket(wsURI);
    ```
    {: codeblock}

-   For the [synchronous HTTP interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-http), use the `POST /v1/recognize` method. The specified custom model is used for that request.

    ```bash
    curl -X POST
    --header "Authorization: Bearer {token}"
    --header "Content-Type: audio/flac"
    --data-binary @audio-file1.flac
    "{url}/v1/recognize?acoustic_customization_id={customization_id}"
    ```
    {: pre}

-   For the [asynchronous HTTP interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-async), use the `POST /v1/recognitions` method. The specified custom model is used for that request.

    ```bash
    curl -X POST
    --header "Authorization: Bearer {token}"
    --header "Content-Type: audio/flac"
    --data-binary @audio-file.flac
    "{url}/v1/recognitions?acoustic_customization_id={customization_id}"
    ```
    {: pre}

You can omit the language model from the request if the custom model is based on the default model, `en-US_BroadbandModel`. Otherwise, you must use the `model` parameter to specify the base model, as shown for the WebSocket example. A custom model can be used only with the base model for which it is created.
