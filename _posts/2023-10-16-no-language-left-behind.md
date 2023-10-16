# No Language Left Behind

In today's globally connected world, the myriad of languages we speak stands as a testament to our diverse cultures and rich communication. 

I am  committed to eliminating language barriers in OpenVoiceOS (OVOS), an open-source voice assistant platform, ensuring no one is excluded from meaningful conversations.

At its core, OVOS is more than just a voice assistant platform. It's a community-driven effort to make technology more accessible to people worldwide. 
OVOS aims to empower individuals to interact with technology in their native language, and that's where the new language plugins come into play.


## Language Detection from Audio

To further embrace linguistic diversity, I have incorporated language detection from audio into OVOS. 
This enables OVOS to identify the language spoken in audio inputs. 
This capability is made possible through plugins such as the new [**FasterWhisperLangClassifier**](https://github.com/OpenVoiceOS/ovos-stt-plugin-fasterwhisper) plugin.

OVOS uses a Speech-to-Text (STT) plugin to convert spoken language into text. 
The STT plugin is crucial for understanding and processing user input, and the information from language detection plays a significant role in this process. 
The STT plugin must be aware of the language being spoken to provide accurate transcriptions.

I created several plugins that provide this functionality:
- [ovos-audio-transformer-plugin-speechbrain-langdetect](https://github.com/OpenVoiceOS/ovos-audio-transformer-plugin-speechbrain-langdetect)
- [ovos-audio-transformer-plugin-speechflow-langdetect](https://github.com/OpenVoiceOS/ovos-audio-transformer-plugin-speechflow-langdetect)
- [ovos-stt-plugin-fasterwhisper](https://github.com/OpenVoiceOS/ovos-stt-plugin-fasterwhisper)

NOTE: language detection from audio is constrained to the languages configured in OVOS config, this rejects all classifications for languages you know will never be spoken around your OVOS setup

```json
{
  "lang": "en-us",
  "secondary_langs": ["pt-pt", "fr-fr"]
}
```

### Configuration

You can configure the language classifier plugins with different settings and models, depending on your requirements. 

For example, to use a specific model in FasterWhisperLangClassifier:

```json
"listener": {
    "audio_transformers": {
        "ovos-audio-transformer-plugin-fasterwhisper": {
            "model": "small"
        }
    }
}
```

## Text Language Translation

In addition to language detection from audio, I also implemented text language translation.

Translation plugins are the backbone of OVOS's multilingual capabilities for text handling.
It ensures that when you communicate with OVOS in a language not natively supported, your text is translated, and you receive responses in your preferred language. 

[No Language Left Behind (NLLB)](https://ai.meta.com/research/no-language-left-behind/) is a breakthrough project from Meta that gives the name to this blog post, NLLB is a open-source model capable of delivering high-quality translations directly between 200 languages—including low-resource languages like Asturian, Luganda, Urdu and more.

The [NLLB plugin](https://github.com/OpenVoiceOS/ovos-translate-plugin-nllb) is the primary text language translation plugin that enables OVOS to handle languages that are not natively understood by the assistant. 
This is especially useful when users communicate in languages that are not part of the assistant's native language set. 
Skills are generally slow to get fully translated, a huge amount of work is needed to fully support a new language, now users no longer depend on explicit support for their language!

A remote version of this plugin also exists to allow usage of this functionality in less powerful hardware, a list of public servers is provided out of the box, but users are encouraged to self host

**Warning** there are associated risk with using a public server, read my previous blog post [The Trust Factor in Public Servers](https://jarbasal.github.io/blog/2023/10/14/the-trust-factor-in-public-servers.html)

### Key Highlights of translation plugins

- **On-Demand Translation**: With this plugin, OVOS can translate text and utterances in real-time.
- **Extensive Language Support**: It covers a wide range of languages, making it possible for OVOS to communicate effectively with users globally.
- **Easy Configuration**: Setting up the plugin is straightforward, allowing OVOS developers to integrate it seamlessly.

Translation plugins of note:
- [ovos-translate-plugin-nllb](https://github.com/OpenVoiceOS/ovos-translate-plugin-nllb)
- [ovos-translate-server-plugin](https://github.com/OpenVoiceOS/ovos-translate-server-plugin)

### Configuration

```json
"language": {
    "detection_module": "ovos-lang-detect-ngram-lm",
    "translation_module": "ovos-translate-plugin-nllb",
    "ovos-translate-plugin-nllb": {
        "model": "nllb-200_600M_int8"
    }
}
```

## The OVOS Bidirectional Translation Plugin

The [**OVOS Bidirectional Translation plugin**](https://github.com/OpenVoiceOS/ovos-bidirectional-translation-plugin/tree/dev) is a game-changer for OVOS's language capabilities. 
It includes two main components: the **Utterance Translator** and the **Dialog Translator**.
Together, they enable OVOS to understand and respond in virtually any language, breaking down the language barrier once and for all.

### Key Highlights

- **Utterance Transformer**: Translates incoming text and adjusts the language of the session temporarily, ensuring a seamless conversational experience.
- **Language Verification**: This optional feature corrects the session language based on the detected text language, ideal for chat platforms with multilingual users.
- **Dialog Transformer**: Translates the spoken dialog back to the original session language, enabling OVOS to provide responses in the original language.
- **Configurable**: The Bidirectional Translation plugin can be customized to fit your specific requirements. You can enable or disable features like language verification and more.

### Pre-Requisites

Before you can harness the power of the Bidirectional Translation Plugin, you need to have the following components in place:

- **Language Detection**: If you enabled language verification, ensure that you have a good [language detection module](https://openvoiceos.github.io/ovos-technical-manual/lang_plugins/) configured in OVOS. This is vital for the plugin to identify the language in which the text is provided.
- **Translation Module**: OVOS relies on a translation plugin to convert text from one language to another. You can use either a local translation module like **ovos-translate-plugin-nllb** or a remote translation module like **ovos-translate-server-plugin**.

### Configuration

Configuring the Bidirectional Translation plugin is straightforward. You can define your settings in the OVOS configuration file. Here's an example configuration for both the Utterance Transformer and the Dialog Transformer:

```json
"utterance_transformers": {
    "ovos-utterance-translation-plugin": {
        "bidirectional": true,
        "verify_lang": false,
        "ignore_invalid": true,
        "translate_secondary_langs": true
    }
},
"dialog_transformers": {
    "ovos-dialog-translation-plugin": {}
}
```

These configurations allow you to tailor the behavior of the Bidirectional Translation plugin to your specific requirements.

## How It Works Together

All these components can work together or standalone, depending on your specific requirements:

- **Language Detection from Audio**: This informs the STT plugin to transcribe spoken language accurately.
- **Utterance Translation**: a translation plugin is used when the text is in a language not natively understood by the assistant, ensuring a seamless conversation.
- **Dialog Translation**: even if the internally generated speech is in a different language, the translation plugin ensures output (TTS) in the original language

The Bidirectional Translation plugin comes into play when you need to communicate in your preferred language regardless of the language OVOS is configured in. It bridges the language gap and ensures that every user can comfortably communicate in their chosen language.

## The OVOS Community

Beyond software, I see a vibrant community forming around our shared passion for making technology universally accessible. 
With the introduction of these new language plugins and the capability for language detection from audio, I'm driven by a strong commitment to inclusivity and linguistic diversity.

I extend a warm invitation to developers and language enthusiasts from around the world to join me in this mission. 
Whether your goal is to contribute to language support, translate skills, or explore new features, I wholeheartedly welcome you to join me in pursuing a world where no language is left behind.
