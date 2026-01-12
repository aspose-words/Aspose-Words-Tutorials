---
category: general
date: 2026-01-11
description: DOCX फ़ाइल को बदलते समय Markdown में छवियों को एम्बेड करना सीखें, छोटे
  चित्रों के लिए Base64 का उपयोग करें और बड़े संसाधनों को अलग से सहेजें।
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: hi
og_description: DOCX फ़ाइल को परिवर्तित करते समय Markdown में छवियों को एम्बेड करना
  सीखें, छोटे चित्रों के लिए Base64 का उपयोग करें और बड़े संसाधनों को अलग से सहेजें।
og_title: DOCX को परिवर्तित करते समय मार्कडाउन में छवियों को एम्बेड कैसे करें
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: DOCX को बदलते समय मार्कडाउन में छवियों को एम्बेड कैसे करें
url: /hi/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX को Markdown में बदलते समय इमेजेज़ को कैसे एम्बेड करें

क्या आपने कभी सोचा है **कि इमेजेज़ को कैसे एम्बेड करें** एक Markdown फ़ाइल में जो Word डॉक्यूमेंट से उत्पन्न हुई है? आप अकेले नहीं हैं। अधिकांश डेवलपर्स को तब समस्या आती है जब कन्वर्ज़न के दौरान तस्वीरें हट जाती हैं या ऐसे तरीके से स्टोर हो जाती हैं जिससे अंतिम लेआउट बिगड़ जाता है।

इस गाइड में हम एक पूर्ण, तैयार‑से‑चलाने वाला उदाहरण देखेंगे जो **इमेजेज़ को एम्बेड करने** का तरीका दिखाता है: छोटे ग्राफ़िक्स को Base64 डेटा URI के रूप में एम्बेड किया जाता है, जबकि बड़े एसेट्स को एक साइड‑फ़ोल्डर में लिखा जाता है। साथ ही हम **convert docx to markdown** को कवर करेंगे, **how to convert docx** को Aspose.Words के साथ समझेंगे, और Base64 के रूप में इमेजेज़ एम्बेड करने बनाम उन्हें अलग फ़ाइलों के रूप में एक्सपोर्ट करने के बीच अंतर बताएँगे।  

> **Pro tip:** यदि आपको केवल एक त्वरित प्रूफ़‑ऑफ़‑कॉन्सेप्ट चाहिए, तो नीचे दिया गया कोड एक ही Maven डिपेंडेंसी के साथ तुरंत काम करता है।

---

## What You’ll Need

- **Java 17** (या कोई भी नया JDK) – API Java‑केन्द्रित है, लेकिन अवधारणाएँ अन्य भाषाओं में भी लागू होती हैं।
- **Aspose.Words for Java** – एक कमर्शियल लाइब्रेरी जो DOCX → Markdown कन्वर्ज़न को सपोर्ट करती है।
- एक **sample DOCX** जिसमें छोटे आइकॉन और बड़े फ़ोटो दोनों हों।
- एक फ़ोल्डर जहाँ आप Markdown और उसकी रिसोर्सेज़ रखना चाहते हैं।

कोई अतिरिक्त फ्रेमवर्क नहीं, कोई बाहरी स्क्रिप्ट नहीं। सिर्फ़ साधारण Java और Aspose.Words।

---

## Step 1 – Add Aspose.Words to Your Project (convert docx to markdown)

यदि आप Maven उपयोग कर रहे हैं, तो नीचे दिया गया स्निपेट अपने `pom.xml` में डालें। पढ़ते समय संस्करण को नवीनतम रिलीज़ से बदलने में संकोच न करें।

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Why this matters:** Aspose.Words DOCX स्ट्रक्चर को पार्स करने, इमेजेज़ निकालने, और Markdown सिंटैक्स रेंडर करने का भारी काम संभालता है। अपना खुद का पार्सर बनाने की कोशिश एक ऐसी खाई में कूदने जैसा है जिसकी आपको ज़रूरत नहीं है।

---

## Step 2 – Load the Source DOCX Document

पहले, API को उस Word फ़ाइल की ओर इशारा करें जिसे आप ट्रांसफ़ॉर्म करना चाहते हैं। `Document` कंस्ट्रक्टर सभी काम कर देता है—कोई मैन्युअल XML पार्सिंग आवश्यक नहीं।

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

ध्यान दें कि टिप्पणी यह समझाती है *क्यों* यह लाइन महत्वपूर्ण है: `Document` इंस्टेंस के बिना कुछ भी कन्वर्ट करने को नहीं रहता।

---

## Step 3 – Prepare MarkdownSaveOptions with a Resource‑Saving Callback

यह **इमेजेज़ को एम्बेड करने** का सही तरीका है। कॉलबैक आपको प्रत्येक रिसोर्स (इमेज, स्टाइल आदि) के लिए एक हुक देता है जिसे कन्वर्टर लिखना चाहता है।

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Why a callback?

- **Control:** आप तय कर सकते हैं कि इमेज इनलाइन Base64 स्ट्रिंग बन जाए या अलग फ़ाइल।
- **Performance:** छोटे आइकॉन Markdown का हिस्सा बन जाते हैं, जिससे अतिरिक्त HTTP रिक्वेस्ट नहीं करनी पड़ती।
- **Portability:** बड़े चित्र बाहरी फ़ाइलों के रूप में रहते हैं, जिससे Markdown का आकार उचित रहता है।

---

## Step 4 – Save the Document as Markdown

अंत में, Aspose.Words को बताएं कि हमने अभी कॉन्फ़िगर किए गए विकल्पों का उपयोग करके Markdown फ़ाइल लिखे।

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

प्रोग्राम चलाने पर दो चीज़ें बनती हैं:

1. `output.md` – आपके मूल DOCX का Markdown प्रतिनिधित्व।
2. एक `markdown_resources` फ़ोल्डर जिसमें कोई भी बड़ी इमेजेज़ होती हैं जो एम्बेड नहीं हुई थीं।

---

## Full Working Example (All Steps in One Place)

नीचे पूरा सोर्स फ़ाइल दिया गया है, जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं। `YOUR_DIRECTORY` को अपने मशीन पर वास्तविक पाथ से बदलें।

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Expected output:** किसी भी Markdown व्यूअर में `output.md` खोलें। छोटे आइकॉन इनलाइन दिखेंगे, उदाहरण के तौर पर:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

बड़ी तस्वीरें इस तरह रेफ़रेंस की जाती हैं:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

यही वह तरीका है जिससे आप **इमेजेज़ को एम्बेड** कर सकते हैं जबकि फ़ाइल का आकार प्रबंधनीय बना रहता है।

---

## Common Questions & Edge Cases

### What if an image is a JPEG instead of PNG?

ऊपर दिया गया कॉलबैक हमेशा URI को `image/png` से प्रीफ़िक्स करता है। JPEG के लिए, आप `args.getData()` के पहले कुछ बाइट्स देख सकते हैं या `args.getFileName()` का उपयोग करके सही MIME टाइप का अनुमान लगा सकते हैं:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Can I change the size threshold?

बिल्कुल। `10_000` बाइट की सीमा सिर्फ़ एक उदाहरण है। यदि आपके पास बैंडविड्थ की पर्याप्त गुंजाइश है, तो इसे 50 KB या उससे अधिक कर सकते हैं। उल्टा, यदि आपको अल्ट्रा‑लाइट Markdown फ़ाइल चाहिए तो इसे घटा सकते हैं।

### Does this work with tables or other Word objects?

हां। Aspose.Words स्वचालित रूप से टेबल, लिस्ट और यहाँ तक कि फुटनोट्स को भी Markdown में बदल देता है। रिसोर्स कॉलबैक केवल इमेजेज़ को इंटरसेप्ट करता है, इसलिए अन्य एलिमेंट्स के लिए अतिरिक्त कोड की ज़रूरत नहीं है।

### What about non‑ASCII filenames?

API `markdown_resources` फ़ोल्डर में लिखते समय Unicode फ़ाइल नामों को सुरक्षित रूप से एन्कोड कर देती है। बस यह सुनिश्चित करें कि आपका फ़ाइल सिस्टम UTF‑8 को सपोर्ट करता हो (ज्यादातर आधुनिक OS ऐसा करते हैं)।

---

## Pro Tips for a Smooth Conversion

- **Keep the output folder clean.** `Files.createDirectories` को प्रत्येक कन्वर्ज़न पर केवल एक बार चलाएँ, या हर रन से पहले फ़ोल्डर को डिलीट करके नया शुरू करें।
- **Validate the Markdown.** `markdownlint` जैसे टूल्स बेस64 स्ट्रिंग में गड़बड़ी से उत्पन्न अनचाहे कैरेक्टर पकड़ सकते हैं।
- **Version lock Aspose.Words.** एक विशिष्ट संस्करण लॉक करने से आपका कोड बड़े अपडेट के बाद भी सही काम करता रहेगा।
- **Use a .gitignore** entry for `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}