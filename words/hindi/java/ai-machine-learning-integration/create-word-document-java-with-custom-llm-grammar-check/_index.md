---
category: general
date: 2026-05-04
description: Aspose.Words का उपयोग करके जावा में वर्ड दस्तावेज़ बनाएं और कस्टम LLM
  के साथ व्याकरण जांचना सीखें। जावा डेवलपर्स के लिए चरण‑दर‑चरण गाइड।
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: hi
og_description: जावा में वर्ड दस्तावेज़ बनाएं और कस्टम LLM का उपयोग करके व्याकरण जांचना
  कैसे देखें। चलाने योग्य कोड के साथ पूर्ण जावा ट्यूटोरियल।
og_title: कस्टम LLM व्याकरण जांच के साथ जावा में वर्ड दस्तावेज़ बनाएं
tags:
- Java
- Aspose.Words
- LLM
title: कस्टम LLM व्याकरण जांच के साथ जावा में वर्ड दस्तावेज़ बनाएं
url: /hi/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# कस्टम LLM व्याकरण जांच के साथ जावा में वर्ड दस्तावेज़ बनाएं

क्या आपने कभी सोचा है कि **create word document java** प्रोजेक्ट्स को इस तरह बनाया जाए कि वे खुद ही प्रूफ़रीड भी कर सकें? आप अकेले नहीं हैं—कई डेवलपर्स एक ही पाइपलाइन चाहते हैं जो कई टूल्स को संभाले बिना एक पॉलिश्ड *.docx* फ़ाइल आउटपुट करे। इस ट्यूटोरियल में हम बिल्कुल यही करेंगे, आपको दिखाएंगे **how to create docx** फ़ाइलें Aspose.Words के साथ कैसे बनाएं, एक लोकली होस्टेड LLM को कैसे जोड़ें, और अंत में **how to check grammar** को ऑटोमैटिकली कैसे लागू करें। अंत तक आपके पास एक सेल्फ‑कंटेन्ड जावा प्रोग्राम होगा जो वर्ड दस्तावेज़ लिखता, वैलिडेट करता और सेव करता है—साथ ही **using custom LLM** एंडपॉइंट्स को आप नियंत्रित करेंगे।

## आपको क्या चाहिए

| पूर्वापेक्षा | क्यों महत्वपूर्ण है |
|--------------|----------------|
| Java 17+ (or any recent JDK) | आधुनिक भाषा सुविधाएँ और बेहतर मॉड्यूल समर्थन |
| Aspose.Words for Java (latest version) | लाइब्रेरी जो आपको प्रोग्रामेटिक रूप से **create word document java** फ़ाइलें बनाने देती है |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | **use custom llm** चरण के लिए आवश्यक जो व्याकरण जांच को शक्ति देता है |
| Maven or Gradle (we’ll use Maven in examples) | निर्भरता प्रबंधन को सरल बनाता है |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | कोडिंग और डिबगिंग को आसान बनाता है |

यदि इनमें से कोई भी चीज़ अपरिचित लगती है, तो घबराएँ नहीं—प्रत्येक आइटम फ्री है या इसका कम्युनिटी‑एडिशन है जो सीखने के लिए पूरी तरह काम करता है।

## चरण 1 – अपना Maven प्रोजेक्ट सेट अप करें

**create word document java** प्रोजेक्ट्स को जल्दी से शुरू करने के लिए, एक न्यूनतम Maven `pom.xml` से शुरू करें। यह फ़ाइल Aspose.Words लाइब्रेरी और आपका पसंदीदा HTTP क्लाइंट (हम Apache HttpClient इस्तेमाल करेंगे) को इम्पोर्ट करती है।

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** यदि आप Gradle का उपयोग कर रहे हैं, तो वही डिपेंडेंसीज़ `build.gradle` में `implementation` के तहत जाएँगी।

अब `mvn clean install` चलाएँ ताकि जार फ़ाइलें डाउनलोड हो जाएँ। एक बार बिल्ड सफल हो जाने पर आप जावा कोड लिखने के लिए तैयार हैं जो **creates word document java** फ़ाइलें बनाता है।

## चरण 2 – वह जावा क्लास लिखें जो **Creates word document java**

नीचे पूरी, रन‑टाइम तैयार सोर्स फ़ाइल है। यह पूरे फ्लो को दिखाती है: एक खाली दस्तावेज़ इनिशियलाइज़ करना, कस्टम LLM एंडपॉइंट कॉन्फ़िगर करना, व्याकरण जांच को इनवोक करना, और अंत में परिणाम को सेव करना।

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Why this works:**  
> * `Document` Aspose.Words की मुख्य क्लास है जो मेमोरी में *.docx* का प्रतिनिधित्व करती है।  
> * `AiEndpoint` Aspose के AI मॉड्यूल को बताता है कि प्रॉम्प्ट कहाँ भेजना है। `localhost:11434` की ओर इशारा करके हम **use custom llm** को क्लाउड सर्विस की बजाय उपयोग करते हैं।  
> * `checkGrammar` के साथ `AiModelType.CUSTOM` दस्तावेज़ के टेक्स्ट को LLM को फॉरवर्ड करता है, सुधरा हुआ टेक्स्ट प्राप्त करता है, और अंतर्निहित Word नोड्स को पुनः लिखता है।  
> * अंत में हम `save` को कॉल करके फ़ाइल को डिस्क पर लिखते हैं, जिससे आपको एक पॉलिश्ड Word फ़ाइल मिलती है।

### अपेक्षित आउटपुट

`mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` चलाने के बाद आपको यह दिखना चाहिए:

```
Document saved to output/GrammarChecked.docx
```

परिणामी `GrammarChecked.docx` को Microsoft Word (या LibreOffice) में खोलें। मूल वाक्य *“Ths sentence has a typo and a grammer error.”* अब *“This sentence has a typo and a grammar error.”* दिखेगा—जिससे यह प्रमाणित होता है कि **how to check grammar** चरण सफल रहा।

## चरण 3 – विभिन्न सामग्री के साथ docx कैसे बनाएं (वैकल्पिक)

यदि आप अधिक समृद्ध दस्तावेज़ बनाना चाहते हैं—टेबल्स, इमेजेज, या स्टाइल्ड टेक्स्ट—तो बस `DocumentBuilder` का उपयोग जारी रखें। यहाँ एक त्वरित स्निपेट है जो हेडिंग और टेबल जोड़ने का प्रदर्शन करता है:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

आप इस कोड को दस्तावेज़‑क्रिएशन ब्लॉक (Step 2.1) और व्याकरण‑चेक कॉल (Step 2.3) के बीच कहीं भी रख सकते हैं। LLM अभी भी पूरा टेक्स्ट प्राप्त करेगा, इसलिए वह प्राकृतिक भाषा वाले भागों को सुधार सकता है जबकि टेबल्स को जैसा का तैसा छोड़ देगा।

## चरण 4 – एंडपॉइंट समस्याओं से निपटना (कस्टम LLM सुरक्षित रूप से उपयोग करें)

जब **using custom llm** एंडपॉइंट्स का उपयोग किया जाता है, तो कुछ सामान्य समस्याएँ आती हैं:

| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| `Connection refused` error | LLM सर्वर नहीं चल रहा या पोर्ट गलत है | Ollama (`ollama serve`) शुरू करें और `http://localhost:11434/api/generate` को `curl` से जांचें। |
| Response JSON missing `completion` field | मॉडल नाम मेल नहीं खा रहा | सुनिश्चित करें कि आप जिस मॉडल को सेट कर रहे हैं (`llama3.1:8b`) वह इंस्टॉल है (`ollama list`)। |
| Grammar check returns the original text unchanged | प्रॉम्प्ट LLM द्वारा पहचाना नहीं गया | मॉडल की सिस्टम को समायोजित करें |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}