---

Copyright:
  years: 2018, 2019
lastupdated: "2019-07-24"

subcollection: speech-to-text-data

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:deprecated: .deprecated}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# About
{: #about}

{{site.data.keyword.speechtotextdatafull}} for {{site.data.keyword.icp4dfull}} provides speech recognition capabilities for your applications. The service leverages machine learning to combine knowledge of grammar, language structure, and the composition of audio and voice signals to accurately transcribe the human voice. It continuously updates and refines its transcription as it receives more speech.
{: shortdesc}

{{site.data.keyword.speechtotextshort}} for {{site.data.keyword.icp4dfull_notm}} provides various interfaces that make it suitable for any application where speech is the input and a textual transcript is the output. Example applications include

-   Voice control of applications, embedded devices, and vehicle accessories
-   Transcribing meetings and conference calls
-   Dictating email messages and notes

The service is ideal for clients who need to extract high-quality speech transcripts from call center audio. Clients in industries such as financial services, healthcare, insurance, and telecommunication can develop cloud-native applications for customer care, customer voice, agent assistance, and other solutions.

For information about installing and configuring {{site.data.keyword.speechtotextshort}} for {{site.data.keyword.icp4dfull_notm}}, see [Installing the service](/docs/services/speech-to-text-data?topic=speech-to-text-data-install).

{{site.data.keyword.speechtotextdatafull}} for {{site.data.keyword.icp4dfull}} is based on the {{site.data.keyword.speechtotextfull}} service on the public {{site.data.keyword.cloud_notm}}. For more information about the public service, see [About {{site.data.keyword.speechtotextshort}}](https://{DomainName}/docs/services/speech-to-text?topic=speech-to-text-about#about){: external}.
{: note}

## Supported interfaces
{: #interfaces}

The {{site.data.keyword.speechtotextshort}} service offers multiple interfaces for speech recognition:

-   A [WebSocket interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-websockets) for establishing persistent, full-duplex, low-latency connections with the service. You can pass a maximum of 100 MB of audio data to the service with a single request.
-   A [synchronous HTTP interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-http) for basic HTTP calls to the service. You can pass a maximum of 100 MB of audio data with a request.
-   An [asynchronous HTTP interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-async) for non-blocking calls to the service. You can pass as much as 1 GB of audio data with a request.

The service also provides a [customization interface](/docs/services/speech-to-text-data?topic=speech-to-text-data-customization) that you can use to tune speech recognition for your language and acoustic requirements. You can expand the vocabulary of a model with domain-specific terminology or adapt a model for the acoustic characteristics of your audio. You can also add [grammars](/docs/services/speech-to-text-data?topic=speech-to-text-data-grammars) to restrict the phrases that the service can recognize.

-   For information about making requests with each of the {{site.data.keyword.speechtotextshort}} interfaces, see [Making requests to the service](/docs/services/speech-to-text-data?topic=speech-to-text-data-making-requests).
-   For examples of basic speech recognition requests with each of the service's interfaces, see [Making a recognition request](/docs/services/speech-to-text-data?topic=speech-to-text-data-basic-request).
-   For a high-level description of application development with the service, see [Overview for developers](/docs/services/speech-to-text-data?topic=speech-to-text-data-developerOverview).

SDKs are available in many programming languages to simplify your use of the service. For more information, see the [API reference](https://{DomainName}/apidocs/speech-to-text-data){: external}.

## Input features
{: #inputFeatures}

The service's interfaces share many common input features for transcribing speech to text:

-   [Audio formats](/docs/services/speech-to-text-data?topic=speech-to-text-data-audio-formats) - You can transcribe Ogg or Web Media (WebM) audio with the Opus or Vorbis codec, MP3 (or MPEG), Waveform Audio File Format (WAV), Free Lossless Audio Codec (FLAC), Linear 16-bit Pulse-Code Modulation (PCM), G.729, A-law, mu-law (or u-law), and basic audio. By using a format that supports compression, you can maximize the amount of audio data that you can send with a request.
-   [Languages and models](/docs/services/speech-to-text-data?topic=speech-to-text-data-models) - You can transcribe audio by using broadband or narrowband models. Use broadband for audio that is sampled at a minimum rate of 16 kHz. Use narrowband for audio that is sampled at a minimum rate of 8 kHz.
-   [Audio transmission](/docs/services/speech-to-text-data?topic=speech-to-text-data-input#transmission) - You can pass audio as a continuous stream of data chunks or as a one-shot delivery that passes all of the data at one time. With streaming, the service enforces inactivity and session [timeouts](/docs/services/speech-to-text-data?topic=speech-to-text-data-input#timeouts).

## Output features
{: #outputFeatures}

Most interfaces also support the following common output features:

-   [Speaker labels](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#speaker_labels) recognize different speakers from US English, Japanese, or Spanish audio. The transcription labels each speaker's contributions to a multi-participant conversation. (Beta functionality.)
-   [Keyword spotting](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#keyword_spotting) identifies spoken phrases that match specified keyword strings with a user-defined level of confidence. Keyword spotting is especially useful when individual phrases from the audio are more important than the full transcription. For example, a customer support system might identify keywords to determine how to route user requests.
-   [Interim results](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#interim) return continually refined hypotheses as transcription progresses. The service returns final results when transcription is complete. Interim results are available only with the WebSocket interface.
-   [Maximum alternatives](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#max_alternatives) provide possible alternative transcripts. The service indicates final results in which it has the greatest confidence.
-   [Word alternatives](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#word_alternatives) request alternative words that are acoustically similar to the words of a transcript.
-   [Word confidence](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#word_confidence) returns confidence levels for each word of a transcript.
-   [Word timestamps](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#word_timestamps) return timestamps for the start and end of each word of a transcript.
-   [Smart formatting](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#smart_formatting) converts dates, times, numbers, currency values, phone numbers, and internet addresses into more readable, conventional forms in final transcripts. For US English, you can also provide keyword phrases to include certain punctuation symbols in final transcripts. Smart formatting is supported for US English, Japanese, and Spanish audio. (Beta functionality.)
-   [Numeric redaction](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#redaction) redacts, or masks, numeric data from a final transcript. Redaction is intended to remove sensitive personal information, such as credit card numbers, from transcripts. The feature is supported for US English, Japanese, and Korean audio. (Beta functionality.)
-   [Profanity filtering](/docs/services/speech-to-text-data?topic=speech-to-text-data-output#profanity_filter) censors profanity from US English transcripts.
-   [Processing metrics](/docs/services/speech-to-text-data?topic=speech-to-text-data-metrics#processing_metrics) provide detailed timing information about the service's analysis of the input audio.
-   [Audio metrics](/docs/services/speech-to-text-data?topic=speech-to-text-data-metrics#audio_metrics) provide detailed information about the signal characteristics of the input audio.

## Language support
{: #languages}

The service offers models for the following languages: Brazilian Portuguese, French, German, Japanese, Korean, Mandarin Chinese, Modern Standard Arabic, Spanish, UK English, and US English. The service does not support all features for all languages. Moreover, it supports some features as generally available (GA) for production use and others as beta offerings for different languages.

-   The WebSocket and synchronous and asynchronous HTTP interfaces are generally available for all languages.
-   The service offers both broadband models and narrowband models for all languages. For more information, see [Languages and models](/docs/services/speech-to-text-data?topic=speech-to-text-data-models).
-   Some speech recognition features are available only for some languages and only with some interfaces. For more information, see the [Parameter summary](/docs/services/speech-to-text-data?topic=speech-to-text-data-summary).
-   The language model customization interface is generally available for all languages. The acoustic model customization interface is available as beta functionality for all languages. For more information, see [Language support for customization](/docs/services/speech-to-text-data?topic=speech-to-text-data-customization#languageSupport).

## Try out the service
{: #tryOut}

For examples of the {{site.data.keyword.speechtotextshort}} service in action, see

-   A [quick demo](https://speech-to-text-demo.ng.bluemix.net/){: external} that transcribes text from streaming audio input or from a file that you upload.
-   Applications in the {{site.data.keyword.ibmwatson}} [Starter Kits](http://www.ibm.com/watson/developercloud/starter-kits.html){: external} that demonstrate the service.
-   The {{site.data.keyword.watson}} blog post [Getting robots to listen: Using {{site.data.keyword.watson}}'s {{site.data.keyword.speechtotextshort}} service](https://www.ibm.com/blogs/watson/2016/07/getting-robots-listen-using-watsons-speech-text-service/){: external} that shows how to use the service's WebSocket interface with Python to extract speech from audio. The post provides a thorough tutorial that demonstrates the code and steps involved.
