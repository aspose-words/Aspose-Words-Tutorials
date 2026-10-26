---
category: general
date: 2026-10-26
description: LoadOptions का उपयोग करके जावा में एन्कोडिंग कैसे निर्दिष्ट करें, सीखें।
  यह गाइड कैरेक्टर एन्कोडिंग, setEncoding मेथड और दस्तावेज़ लोडिंग विकल्पों को कवर
  करता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: hi
lastmod: 2026-10-26
og_description: Aspose.Words का उपयोग करके जावा में एन्कोडिंग कैसे निर्दिष्ट करें।
  सही कैरेक्टर सेट के साथ दस्तावेज़ लोड करने के लिए इस पूर्ण ट्यूटोरियल का पालन करें।
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Aspose.Words के साथ जावा में एन्कोडिंग कैसे निर्दिष्ट करें – चरण‑दर‑चरण
  गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Aspose.Words for Java के साथ दस्तावेज़ लोड करते समय एन्कोडिंग कैसे निर्दिष्ट
  करें
url: /hi/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ दस्तावेज़ लोड करते समय एन्कोडिंग कैसे निर्दिष्ट करें

यदि आपको जावा में स्रोत फ़ाइल के लिए **how to specify encoding** की आवश्यकता है, तो यह ट्यूटोरियल आपको सटीक चरण दिखाता है। चाहे दस्तावेज़ Big5, UTF‑8, या किसी अन्य कैरेक्टर सेट का उपयोग करता हो, आप `LoadOptions` के साथ पढ़ने की प्रक्रिया को नियंत्रित कर सकते हैं। गाइड के अंत तक आप समझेंगे कि कैरेक्टर एन्कोडिंग क्यों महत्वपूर्ण है, `setEncoding` मेथड को कैसे लागू करें, और यह कैसे सत्यापित करें कि दस्तावेज़ सही ढंग से लोड हुआ है।

सही कैरेक्टर एन्कोडिंग के साथ दस्तावेज़ लोड करने से गड़बड़ टेक्स्ट से बचा जा सकता है और यह सुनिश्चित होता है कि बहुभाषी सामग्री इच्छित रूप में प्रदर्शित हो। यह ट्यूटोरियल शामिल करता है:

* फ़ाइल पढ़ते समय **character encoding in Java** की भूमिका।
* Aspose.Words के लिए **LoadOptions encoding** को कैसे कॉन्फ़िगर करें।
* व्यावहारिक कोड जिसे आप अपने प्रोजेक्ट में कॉपी कर सकते हैं।
* असंगत एन्कोडिंग जैसी सामान्य समस्याएँ और उन्हें कैसे ट्रबलशूट करें।

## आवश्यकताएँ

* Java Development Kit (JDK) 8 या उससे ऊपर।
* निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।
* Aspose.Words for Java 23.10 या बाद का संस्करण (इस गाइड में उपयोग किया गया संस्करण)।
* एक नमूना टेक्स्ट दस्तावेज़ (`input.doc`) जिसे इच्छित एन्कोडिंग (जैसे, Big5) के साथ सहेजा गया हो।

आपको कोई अतिरिक्त लाइब्रेरी की आवश्यकता नहीं है; उदाहरण केवल कोर Aspose.Words API का उपयोग करता है।

## चरण 1: अपने प्रोजेक्ट में Aspose.Words जोड़ें

यदि आप Maven का उपयोग करते हैं, तो अपने `pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Gradle के लिए, इस लाइन को अपने `build.gradle` में रखें:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

लाइब्रेरी को शामिल करने से `LoadOptions`, `Document`, और `Encoding` क्लास उपलब्ध हो जाते हैं।

## चरण 2: एक `LoadOptions` इंस्टेंस बनाएं

`LoadOptions` आपको यह कस्टमाइज़ करने देता है कि Aspose.Words फ़ाइल को कैसे खोलता है। ऑब्जेक्ट बनाना **how to specify encoding** का पहला भाग है।

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` ऑब्जेक्ट डिफ़ॉल्ट सेटिंग्स के साथ शुरू होता है। आप अगले चरण में इसकी प्रॉपर्टीज़ को समायोजित करेंगे।

## चरण 3: इच्छित कैरेक्टर एन्कोडिंग सेट करें

`setEncoding` मेथड वह **character encoding in Java** निर्धारित करता है जिसे लोडर को उपयोग करना चाहिए। इस उदाहरण में हम Big5 कोड पेज चुनते हैं, जो पारंपरिक चीनी टेक्स्ट फ़ाइलों में आम है।

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*यह क्यों महत्वपूर्ण है*: यदि फ़ाइल के बाइट्स को गलत कोड पेज के साथ व्याख्या किया जाता है, तो कैरेक्टर प्रश्न चिह्न या बेतुके रूप में दिखते हैं। स्पष्ट रूप से `setEncoding` को कॉल करके, आप Aspose.Words को बताते हैं कि वह बाइट स्ट्रीम को Big5 मैपिंग टेबल का उपयोग करके डिकोड करे।

आप `"Big5"` को किसी भी charset नाम से बदल सकते हैं जो जावा द्वारा पहचाना जाता है, जैसे `"UTF-8"`, `"ISO-8859-1"`, या `"Windows-1252"`। यदि नाम अमान्य है तो मेथड `UnsupportedEncodingException` थ्रो करता है, इसलिए प्रोडक्शन कोड में आप इस एक्सेप्शन को पकड़ना चाहेंगे।

## चरण 4: कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

अब जब **LoadOptions encoding** सेट हो गया है, तो विकल्पों को `Document` कन्स्ट्रक्टर में पास करें। यह चरण कोर **how to specify encoding** वर्कफ़्लो को पूरा करता है।

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

`YOUR_DIRECTORY` को अपनी फ़ाइल के पूर्ण या सापेक्ष पाथ से बदलें। `Document` इंस्टेंस अब पूरी तरह से पार्स किया गया कंटेंट रखता है, जो आपने प्रदान की गई एन्कोडिंग का सम्मान करता है।

## चरण 5: सत्यापित करें कि टेक्स्ट सही ढंग से लोड हुआ है

एक त्वरित सत्यापन आपको यह सुनिश्चित करने में मदद करता है कि एन्कोडिंग अपेक्षित रूप से लागू हुई है। आप दस्तावेज़ का टेक्स्ट निकाल सकते हैं और कंसोल पर प्रिंट कर सकते हैं:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

यदि कंसोल में पठनीय चीनी कैरेक्टर (या वह भाषा जो आप अपेक्षा करते हैं) दिखता है, तो एन्कोडिंग सफल रही। यदि अभी भी गड़बड़ आउटपुट दिखता है, तो मूल फ़ाइल की एन्कोडिंग को दोबारा जांचें और सुनिश्चित करें कि charset नाम बिल्कुल मेल खाता है।

## सामान्य किनारे मामलों को संभालना

### 5.1 `InputStream` से लोड करना

कभी-कभी आपको दस्तावेज़ एक स्ट्रीम के रूप में मिलता है (जैसे, वेब सेवा से)। आप अभी भी `LoadOptions` के साथ स्ट्रीम पास करके एन्कोडिंग को नियंत्रित कर सकते हैं:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

एक ही **document loading options** लागू होते हैं, और `setEncoding` कॉल अपरिवर्तित रहती है।

### 5.2 जब एन्कोडिंग अज्ञात हो तो बैकअप

यदि आप स्रोत फ़ाइल के charset का निर्धारण नहीं कर सकते, तो एन्कोडिंग सेट करने से पहले एक डिटेक्शन लाइब्रेरी (जैसे ICU4J) का उपयोग कर सकते हैं। एक बार अनुमान लग जाने पर, उस मान के साथ `setEncoding` को कॉल करें। यह दृष्टिकोण गलत डिकोडेड टेक्स्ट के जोखिम को कम करता है।

### 5.3 असमर्थित एन्कोडिंग को संभालना

जावा कई कोड पेज़ को सपोर्ट करता है, लेकिन कुछ पुरानी एन्कोडिंग्स अनुपलब्ध हो सकती हैं। ऐसे में, Aspose.Words के साथ लोड करने से पहले फ़ाइल को बाहरी रूप से UTF‑8 में कनवर्ट करने पर विचार करें (जैसे, `iconv` का उपयोग करके)। रूपांतरण के बाद, आप `setEncoding` कॉल को छोड़ सकते हैं क्योंकि UTF‑8 अधिकांश आधुनिक API के लिए डिफ़ॉल्ट है।

## प्रो टिप: बैच प्रोसेसिंग के लिए `LoadOptions` को पुन: उपयोग करें

यदि आपको कई दस्तावेज़ लोड करने हैं जिनका charset समान हो, तो एक ही `LoadOptions` इंस्टेंस बनाएं और उसे पुन: उपयोग करें:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

ऑब्जेक्ट को पुन: उपयोग करने से ऑब्जेक्ट‑क्रिएशन ओवरहेड कम होता है और बैच में लगातार एन्कोडिंग सुनिश्चित होती है।

## पूर्ण चलाने योग्य उदाहरण

नीचे वह पूर्ण प्रोग्राम है जो सभी चरणों को सम्मिलित करता है, आवश्यक इम्पोर्ट्स शामिल करता है, और संभावित एक्सेप्शन को संभालता है।

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**अपेक्षित आउटपुट** (मान लेते हैं कि स्रोत फ़ाइल में Big5 में एन्कोडेड चीनी टेक्स्ट है):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

यदि आउटपुट में अपठनीय प्रतीक दिखते हैं, तो charset नाम को फिर से देखें या फ़ाइल की मूल एन्कोडिंग सत्यापित करें।

## अक्सर पूछे जाने वाले प्रश्न

**क्या यह अन्य दस्तावेज़ फ़ॉर्मेट (DOCX, RTF, HTML) के साथ काम करता है?**  
हां। वही `LoadOptions` ऑब्जेक्ट Aspose.Words द्वारा समर्थित किसी भी फ़ॉर्मेट पर लागू होता है। एकमात्र आवश्यकता यह है कि अंतर्निहित फ़ाइल वास्तव में निर्दिष्ट charset का उपयोग करे।

**यदि दस्तावेज़ लोड होने के बाद मुझे एन्कोडिंग बदलनी पड़े तो क्या करें?**  
एन्कोडिंग केवल पढ़ने के चरण को प्रभावित करती है। एक बार `Document` ऑब्जेक्ट बन जाने के बाद, उसकी आंतरिक Unicode प्रतिनिधित्व मूल charset से स्वतंत्र हो जाता है। आउटपुट एन्कोडिंग बदलने के लिए, फ़ाइल लिखते समय `SaveOptions` को समायोजित करें।

**क्या मैं इस दृष्टिकोण को अन्य लाइब्रेरी (जैसे, Apache POI) के साथ उपयोग कर सकता हूँ?**  
Apache POI पुराने बाइनरी फ़ॉर्मेट्स के लिए अपनी charset डिटेक्शन संभालता है, लेकिन लोडर को charset प्रदान करने की अवधना समान है। Aspose.Words के लिए, `LoadOptions` **how to specify encoding** को नियंत्रित करने का आधिकारिक तरीका है।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Java के साथ दस्तावेज़ लोड करते समय **how to specify encoding** कैसे किया जाता है। एक `LoadOptions` ऑब्जेक्ट बनाकर, `setEncoding` मेथड को कॉल करके, और विकल्पों को `Document` कन्स्ट्रक्टर में पास करके, आप सुनिश्चित करते हैं कि फ़ाइल के बाइट्स सही ढंग से व्याख्यायित हों। यह प्रैक्टिस गड़बड़ टेक्स्ट को समाप्त करती है, बहुभाषी सामग्री को समर्थन देती है, और बैच प्रोसेसिंग या स्ट्रीम‑आधारित वर्कफ़्लो के साथ सहजता से एकीकृत होती है।

संबंधित विषयों जैसे **document loading options**, **specific encodings के साथ सहेजना**, और **Java में Unicode को संभालना** का अन्वेषण करें ताकि टेक्स्ट प्रोसेसिंग में आपकी महारत गहरी हो। विभिन्न charset नामों के साथ प्रयोग करें, इस दृष्टिकोण को PDF रूपांतरण के साथ मिलाएँ, या इसे ऐसे वेब सर्विस में एकीकृत करें जो विभिन्न एन्कोडिंग में अपलोड स्वीकार करता हो।

कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}