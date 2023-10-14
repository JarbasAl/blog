# The Trust Factor in Public Servers

In an age where digital communication and technology are at the forefront of human interaction, services that offer Speech-to-Text (STT), Text-to-Speech (TTS), and translation capabilities have become increasingly important. 
Many providers offer public servers for these services, making them easily accessible to a wide range of users. 
However, with this accessibility comes a crucial issue – the trust factor.

Trust is paramount when dealing with sensitive data, especially in the context of public servers. Users must believe that their information is handled with the utmost care and privacy. 
In this blog post, we will explore the challenges and concerns surrounding the trust factor in public servers for [STT](https://github.com/OpenVoiceOS/ovos-stt-http-server), [TTS](https://github.com/OpenVoiceOS/ovos-tts-server), and [Translation](https://github.com/OpenVoiceOS/ovos-translate-server), along with potential ways that untrustworthy servers could compromise user data.

## Promises and Their Limits

When users engage with public servers for [STT](https://github.com/OpenVoiceOS/ovos-stt-http-server), [TTS](https://github.com/OpenVoiceOS/ovos-tts-server), and [Translation](https://github.com/OpenVoiceOS/ovos-translate-server), they encounter a series of promises made by the service providers. 
These promises are designed to assure users that their data is secure and their privacy is respected. Some common promises include:

1. We promise we don't look at logs.
2. We promise we don't save logs.
3. We promise we don't even log at all.
4. We promise we don't decrypt your data.
5. We promise the code we run is the same one on GitHub.

However, there is an inherent challenge with these promises. 
While they may be well-intentioned, they often fall short in guaranteeing the trustworthiness of the service. Let's delve into the reasons why.

## The Challenge of Accidental Logging

The promises made by public server providers primarily focus on addressing accidental logging. Accidental logging occurs when sensitive user data is stored in server logs, either intentionally or unintentionally.

Encryption plays a crucial role in safeguarding user data and mitigating the risk of accidental logging on public servers. 
By encrypting sensitive data, such as the translated phrases or TTS utterances, it ensures that even if logs are inadvertently saved or accessed, the information remains secure and indecipherable to unauthorized personnel. 

In this context, I'm committed to enhancing user trust and data security under OVOS public servers. 
The measures taken, such as setting the log level to ERROR and adding encryption (TODO!!!) to non-configurable properties in the TTS and translation server plugins, address the issue of accidental logging.  

With these measures in place, OVOS strives to provide users with a reliable and privacy-conscious solution for their STT, TTS, and translation needs, ensuring that user data remains confidential and secure, even in the face of accidental logging risks.
While these measures can prevent accidental logging, they have minimal impact on the trust factor. This is because they don't address the core issue – the inherent need for the server to access and process user data.

## The Trust Gap

Public servers require access to the data being processed, whether it's audio for STT or text for TTS and translation. 
While providers can promise not to misuse this data, there's an unavoidable gap in trust. 
Users have no practical means to verify what happens to their data once it's on the server. 
The data is sent there, and users must trust that it will only be used for processing and that the promises will be upheld.

Potential Compromises

Beyond the promises, there are several ways that an untrustworthy or "evil" server could compromise user data:

1. Tampered Code: One of the most significant concerns is that the code running on the server might not be the same as the one available on GitHub or the publicly disclosed source code. If a malicious server alters the code to capture and exfiltrate data, users have no way to verify the integrity of the code in real-time.

2. Data Resale: An unscrupulous server could secretly collect and store user data, then potentially sell it to third parties, violating the promise of not saving or sharing user data. This would be a clear breach of trust and privacy.

3. Intercepting Unencrypted Data: Even if data is transmitted securely to the server, an evil server may intercept and store decrypted data before it is processed, despite the promise of data encryption.

4. Persistent Logging: Some servers may explicitly save logs despite claiming not to do so. These logs could contain sensitive user information that was supposed to be discarded, putting user privacy at risk.

5. Backdoor Access: An evil server might have hidden backdoors or vulnerabilities intentionally built into the system, enabling unauthorized access to user data, even if promises have been made to the contrary.

6. Unauthorized Data Mining: Malicious servers could use the user data they process for unauthorized data mining or profiling, which goes against the promise of only using data for processing purposes.

7. Third-party Integrations: Public servers may integrate third-party services or APIs that could compromise user data. Users might not be aware of these integrations and how they handle data, which could pose a risk to their privacy.

8. Unforeseen Security Breaches: Regardless of the promises made, public servers are still susceptible to security breaches. In the event of a data breach, malicious actors could gain unauthorized access to user data, making trust in the server irrelevant.

## Conclusion

These concerns highlight the importance of due diligence when selecting public servers for [STT](https://github.com/OpenVoiceOS/ovos-stt-http-server), [TTS](https://github.com/OpenVoiceOS/ovos-tts-server), and [Translation](https://github.com/OpenVoiceOS/ovos-translate-server) services. 
Users should be cautious and consider the potential risks associated with trusting their data to any public server, even if they claim to uphold strong privacy and security standards. 
Trust, in the end, should be earned through transparency and a proven track record of safeguarding user data. 
In an age where data privacy and security are paramount, users must remain vigilant and prioritize trustworthiness when engaging with public servers for these critical services.