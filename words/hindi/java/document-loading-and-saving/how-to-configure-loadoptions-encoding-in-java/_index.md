---
category: general
date: 2026-10-20
description: Java में LoadOptions एन्कोडिंग को कॉन्फ़िगर करें ताकि दस्तावेज़ सही ढंग
  से पढ़े जा सकें और Aspose.Words के साथ दस्तावेज़ एन्कोडिंग को UTF-8 में बदलें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: hi
lastmod: 2026-10-20
og_description: जावा में LoadOptions एन्कोडिंग को कॉन्फ़िगर करें ताकि सही अक्षर हैंडलिंग
  सुनिश्चित हो और Aspose.Words का उपयोग करके दस्तावेज़ एन्कोडिंग को UTF-8 में बदलना
  सीखें।
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: जावा में LoadOptions एन्कोडिंग को कॉन्फ़िगर करें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Java में LoadOptions एन्कोडिंग को कैसे कॉन्फ़िगर करें
url: /hi/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में LoadOptions एन्कोडिंग को कॉन्फ़िगर कैसे करें

यदि आपको Java में **LoadOptions एन्कोडिंग को कॉन्फ़िगर** करने की आवश्यकता है, तो यह गाइड आपको सही कैरेक्टर सेट सेट करने और फिर Aspose.Words का उपयोग करके **डॉक्यूमेंट एन्कोडिंग को UTF-8 में बदलने** का तरीका दिखाता है। सही एन्कोडिंग बिग5, Shift_JIS, या Windows‑1252 जैसे लेगेसी कोड पेज़ वाले फ़ाइलों को लोड करते समय गड़बड़ टेक्स्ट को रोकती है।

आप सीखेंगे कैसे:

* एक विशिष्ट एन्कोडिंग के साथ `LoadOptions` इंस्टेंस बनाना,
* उस एन्कोडिंग का उपयोग करने वाले स्रोत दस्तावेज़ को लोड करना,
* दस्तावेज़ को अलग एन्कोडिंग (UTF‑8) में डेटा हानि के बिना सहेजना,
* यह सत्यापित करना कि परिवर्तन सफल रहा।

यह ट्यूटोरियल मानता है कि आपके पास एक बुनियादी Java विकास वातावरण और एक वैध Aspose.Words for Java लाइसेंस है। कोई बाहरी टूल आवश्यक नहीं है।

## Prerequisites

| आवश्यकता | क्यों महत्वपूर्ण है |
|-------------|----------------|
| Java 17 या बाद का संस्करण | आधुनिक भाषा सुविधाएँ और दीर्घकालिक समर्थन प्रदान करता है। |
| Aspose.Words for Java (v23.9 या नया) | `LoadOptions` क्लास इस लाइब्रेरी में स्थित है। |
| लेगेसी कोड पेज़ (जैसे, Big5) में एन्कोडेड स्रोत दस्तावेज़ | कस्टम एन्कोडिंग की आवश्यकता को दर्शाता है। |
| एक IDE या बिल्ड टूल (Maven/Gradle) | उदाहरण को संकलित करने और चलाने को सरल बनाता है। |

यदि आप Maven का उपयोग करते हैं तो अपने `pom.xml` में Aspose.Words निर्भरता जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Configure LoadOptions encoding

पहला कदम यह बताना है कि Aspose.Words फ़ाइल पढ़ते समय किस कैरेक्टर सेट की अपेक्षा करे। यह `LoadOptions` ऑब्जेक्ट को कॉन्फ़िगर करके किया जाता है।

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**क्यों महत्वपूर्ण है:** जब कोई दस्तावेज़ लेगेसी एन्कोडिंग के साथ सहेजा जाता है, तो डिफ़ॉल्ट लोडर UTF‑8 मान लेता है। एन्कोडिंग को स्पष्ट रूप से सेट करके आप मोजिबाके (गड़बड़ अक्षर) से बचते हैं और मूल टेक्स्ट को संरक्षित रखते हैं।

### Pro tip
यदि आप निश्चित नहीं हैं कि फ़ाइल कौन सी एन्कोडिंग उपयोग करती है, तो आप उसके बाइट‑ऑर्डर मार्क (BOM) की जाँच कर सकते हैं या दस्तावेज़ प्रदाता से पूछ सकते हैं। सामान्य लेगेसी एन्कोडिंग में `Big5`, `Shift_JIS`, और `Windows-1252` शामिल हैं।

## Load the document with the configured options

अब जब `LoadOptions` तैयार है, स्रोत फ़ाइल को लोड करें। फ़ाइल पाथ और `LoadOptions` इंस्टेंस को स्वीकार करने वाला कंस्ट्रक्टर सुनिश्चित करता है कि कस्टम एन्कोडिंग लागू हो।

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**क्यों महत्वपूर्ण है:** `Document` ऑब्जेक्ट अब मूल फ़ाइल में जैसा टेक्स्ट है, वैसा ही रखता है, क्योंकि लोडर ने आपके द्वारा प्रदान किए गए Big5 कोड पेज़ का सम्मान किया।

## Change document encoding to UTF-8

Aspose.Words टेक्स्ट को आंतरिक रूप से Unicode में संग्रहीत करता है, इसलिए दस्तावेज़ को सहेजने का कार्य बाहरी एन्कोडिंग निर्धारित करता है। UTF‑8 फ़ाइल बनाने के लिए, बस अतिरिक्त एन्कोडिंग निर्दिष्ट किए बिना सहेजें—UTF‑8 आधुनिक Office Open XML फ़ॉर्मेट्स के लिए डिफ़ॉल्ट है। हालांकि, स्पष्टता के लिए आप इसे स्पष्ट रूप से भी सेट कर सकते हैं।

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

यदि आपको UTF‑8 के साथ साधारण टेक्स्ट प्रतिनिधित्व (जैसे, `.txt`) बनाना है, तो एक `SaveOptions` ऑब्जेक्ट पास करें:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**क्यों महत्वपूर्ण है:** UTF‑8 में सहेजने से यह सुनिश्चित होता है कि कोई भी डाउनस्ट्रीम सिस्टम—वेब सर्विसेज, डेटाबेस, या आधुनिक एडिटर—फ़ाइल को अतिरिक्त रूपांतरण चरणों के बिना पढ़ सके।

## Verify the conversion

एन्कोडिंग परिवर्तन सफल रहा यह पुष्टि करने का एक त्वरित तरीका है कि सहेजी गई फ़ाइल को UTF‑8 रीडर से फिर पढ़ें और कुछ अक्षर प्रिंट करें।

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

यदि आउटपुट पठनीय अक्षर दिखाता है (कोई � प्रतीक नहीं), तो परिवर्तन अपेक्षित रूप से काम किया।

## Full runnable example

नीचे एक स्व-निहित प्रोग्राम है जो सभी चरणों को एक साथ जोड़ता है। फ़ाइल पाथ को अपने स्थानों से बदलें।

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Expected output**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

यदि अक्षर सही दिखते हैं, तो आपने सफलतापूर्वक **LoadOptions एन्कोडिंग को कॉन्फ़िगर** किया है और **डॉक्यूमेंट एन्कोडिंग को UTF-8 में बदल दिया** है।

## Common pitfalls and how to avoid them

| लक्षण | कारण | समाधान |
|---------|-------|-----|
| लोड करने के बाद गड़बड़ अक्षर | `LoadOptions` सेट नहीं है या गलत charset नाम | सुनिश्चित करें कि `loadOptions.setEncoding(Charset.forName("Big5"))` स्रोत फ़ाइल के कोड पेज़ से मेल खाता हो। |
| `UnsupportedEncodingException` | charset नाम की गलत वर्तनी | `Charset.availableCharsets()` में सूचीबद्ध सटीक नाम का उपयोग करें। |
| आउटपुट फ़ाइल अभी भी मोजिबाके दिखाती है | UTF‑8 विकल्पों के बिना लेगेसी फ़ॉर्मेट (जैसे, `.rtf`) में सहेजा गया | `TxtSaveOptions` के साथ `setEncoding("UTF-8")` उपयोग करें या `.docx` के रूप में सहेजें। |
| बड़ी फ़ाइलों पर प्रदर्शन में गिरावट | प्रत्येक दस्तावेज़ के लिए `LoadOptions` को फिर से बनाना | समान स्रोत एन्कोडिंग वाली कई फ़ाइलों को प्रोसेस करते समय एक ही `LoadOptions` इंस्टेंस को पुनः उपयोग करें। |

## Conclusion

अब आप जानते हैं कि Java में **LoadOptions एन्कोडिंग को कॉन्फ़िगर** करके लेगेसी‑एन्कोडेड दस्तावेज़ों को कैसे पढ़ा जाए और सुरक्षित डाउनस्ट्रीम उपयोग के लिए **डॉक्यूमेंट एन्कोडिंग को UTF-8 में कैसे बदला जाए**। यह दृष्टिकोण Java की `Charset` क्लास द्वारा समर्थित किसी भी कोड पेज़ के लिए काम करता है, जिससे यह बहुभाषी अनुप्रयोगों के लिए एक लचीला समाधान बन जाता है।

आगे आप खोज सकते हैं:

* **Batch conversion** – दस्तावेज़ों के फ़ोल्डर पर लूप चलाएँ और समान एन्कोडिंग लॉजिक लागू करें।
* **Encoding detection** – `juniversalchardet` जैसी लाइब्रेरीज़ का उपयोग करके `LoadOptions` को कॉन्फ़िगर करने से पहले स्रोत charset को स्वचालित रूप से पहचानें।
* **Preserving formatting** – PDF या HTML में सहेजने के साथ प्रयोग करें जबकि UTF‑8 अनुपालन बनाए रखें।

कोड को अपने प्रोजेक्ट की आर्किटेक्चर के अनुसार अनुकूलित करने में संकोच न करें, और मजबूत Aspose.Words API को दस्तावेज़ हेरफेर के भारी काम को संभालने दें।

![LoadOptions एन्कोडिंग कॉन्फ़िगरेशन और दस्तावेज़ सहेजने का कोड स्निपेट](/images/encoding-demo.png){: .align-center alt="Java कोड उदाहरण में LoadOptions एन्कोडिंग कॉन्फ़िगर करें"}

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकटतम संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं ताकि आप अतिरिक्त API सुविधाओं में निपुण हो सकें और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}