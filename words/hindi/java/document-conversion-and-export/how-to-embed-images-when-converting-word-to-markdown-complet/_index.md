---
category: general
date: 2026-02-28
description: डॉक्यूमेंट को मार्कडाउन में बदलते समय छवियों को एम्बेड करना सीखें। मार्कडाउन
  को छवियों के साथ निर्यात करें और जावा का उपयोग करके मार्कडाउन में इनलाइन छवियाँ
  प्राप्त करें।
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: hi
og_description: जानिए कैसे वर्ड दस्तावेज़ को मार्कडाउन में बदलते समय छवियों को एम्बेड
  किया जाए। यह गाइड आपको दिखाता है कि छवियों के साथ मार्कडाउन को कैसे निर्यात करें
  और उन्हें इनलाइन रखें।
og_title: वर्ड को मार्कडाउन में बदलते समय छवियों को कैसे एम्बेड करें
tags:
- markdown
- java
- Aspose.Words
- image handling
title: वर्ड को मार्कडाउन में बदलते समय चित्र कैसे एम्बेड करें – पूर्ण मार्गदर्शिका
url: /hi/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word को Markdown में बदलते समय छवियों को एम्बेड कैसे करें – पूर्ण गाइड

क्या आपने कभी सोचा है कि **छवियों को एम्बेड कैसे करें** एक Markdown फ़ाइल में जो आप Word दस्तावेज़ से जनरेट करते हैं? शायद आपने तेज़ एक्सपोर्ट आज़माया हो, लेकिन अंत में बिखरी हुई इमेज फ़ाइलें और टूटे हुए लिंक मिल गए हों। यह एक आम समस्या है—विशेषकर जब आपको एक ही पोर्टेबल `.md` फ़ाइल चाहिए जिसे आप static‑site generator या GitHub README में डाल सकें।

अच्छी खबर? आप एक्सपोर्टर को बता सकते हैं कि हर चित्र को Base64‑एन्कोडेड स्ट्रिंग के रूप में इनलाइन किया जाए, जिससे उत्पन्न Markdown स्वयं‑समाहित हो जाता है। इस ट्यूटोरियल में हम सटीक चरणों को बताएँगे, आपको पूरा Java कोड दिखाएँगे, और समझाएँगे कि प्रत्येक भाग क्यों महत्वपूर्ण है। अंत तक आप **doc को markdown में बदलने** में सक्षम होंगे जिसमें छवियाँ एम्बेड होंगी, और आप देखेंगे कि प्रक्रिया को अन्य परिदृश्यों जैसे “छवियों के साथ markdown एक्सपोर्ट” या “markdown में इनलाइन इमेजेज़” के लिए कैसे समायोजित किया जा सकता है।

## आप क्या सीखेंगे

- आवश्यक लाइब्रेरीज़ और न्यूनतम प्रोजेक्ट सेटअप।  
- `MarkdownSaveOptions` को इस तरह कॉन्फ़िगर करना कि छवियाँ Base64 डेटा URI बन जाएँ।  
- `ResourceSavingCallback` का उपयोग क्यों इमेज हैंडलिंग को नियंत्रित करने का सबसे साफ़ तरीका है।  
- यह सत्यापित करना कि Markdown फ़ाइल वास्तव में एम्बेडेड इमेजेज़ रखती है या नहीं।  
- किनारे के मामलों के लिए टिप्स (बड़ी छवियाँ, विभिन्न MIME प्रकार, और प्रदर्शन संबंधी विचार)।  

Aspose.Words के साथ कोई पूर्व अनुभव आवश्यक नहीं है; एक बुनियादी Java पृष्ठभूमि पर्याप्त है।

## आवश्यकताएँ

कोड में डुबकी लगाने से पहले, सुनिश्चित करें कि आपके पास है:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | Aspose.Words for Java API Java 8+ को लक्षित करता है, लेकिन नवीनतम JDK का उपयोग करने से आपको बिल्ट‑इन `Base64` यूटिलिटीज़ मिलती हैं। |
| **Aspose.Words for Java** (latest version) | यह लाइब्रेरी `MarkdownSaveOptions` और वह कॉलबैक इन्फ्रास्ट्रक्चर प्रदान करती है जिसका हम उपयोग करेंगे। |
| **A Word document** (`.docx`) that contains at least one image | हमें परिवर्तित करने के लिए कुछ चाहिए; उदाहरण में `sample.docx` नामक फ़ाइल मान ली गई है। |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | सैंपल को जल्दी से कंपाइल और चलाने के लिए। |

अपने `pom.xml` (Maven) या `build.gradle` (Gradle) में Aspose डिपेंडेंसी जोड़ें। यहाँ Maven स्निपेट है:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

यदि आप Gradle पसंद करते हैं:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Aspose एक मुफ्त 30‑दिन का ट्रायल देता है। एक अस्थायी लाइसेंस कुंजी प्राप्त करें और इसे जल्दी रजिस्टर करें ताकि वॉटरमार्क संदेशों से बचा जा सके।

## चरण 1: Markdown Save Options बनाएं

पहला काम हम `MarkdownSaveOptions` को इंस्टैंसिएट करना है। यह ऑब्जेक्ट Aspose को बताता है कि हम चाहते हैं कि रूपांतरण कैसे व्यवहार करे—फ़ॉन्ट हैंडलिंग, लिस्ट फ़ॉर्मेटिंग, और हमारे लिए सबसे महत्वपूर्ण, इमेज हैंडलिंग।

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Java में सिंटैक्स समान है; बस बाद में कोड ब्लॉक में `csharp` कीवर्ड को `java` से बदलें।  
यह क्यों महत्वपूर्ण है: विकल्पों को कस्टमाइज़ किए बिना, Aspose प्रत्येक इमेज को `.md` के बगल में एक अलग फ़ाइल में लिखेगा। अब विकल्प ऑब्जेक्ट तैयार करके, हम इस डिफ़ॉल्ट व्यवहार को इंटरसेप्ट करने के लिए एक हुक बनाते हैं।

## चरण 2: इमेज रिसोर्सेज़ को इंटरसेप्ट करें और उन्हें Base64 में एन्कोड करें

Aspose हर बार जब वह कोई रिसोर्स (इमेज, CSS, आदि) लिखना चाहता है, एक कॉलबैक फायर करता है। `IResourceSavingCallback` को इम्प्लीमेंट करके हम तय कर सकते हैं कि प्रत्येक रिसोर्स के साथ क्या करना है। नीचे दिया गया स्निपेट जांचता है कि रिसोर्स इमेज है या नहीं, फ़ाइल नाम को साफ़ करता है (ताकि कोई बाहरी फ़ाइल न बने), बाइनरी डेटा को Base64 में एन्कोड करता है, और उचित MIME टाइप सेट करता है।

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**आंतरिक रूप से क्या हो रहा है?**

1. **`args.getResourceType()`** – Aspose प्रत्येक आउटबाउंड ब्लॉब को वर्गीकृत करता है। हमें केवल `ResourceType.IMAGE` में रुचि है।  
2. **`args.setResourceFileName(null)`** – फ़ाइलनाम को null करके हम लाइब्रेरी को बताते हैं कि *भौतिक फ़ाइल* न लिखे।  
3. **`Base64.getEncoder().encodeToString(...)`** – कच्चा बाइट एरे एक टेक्स्ट स्ट्रिंग बन जाता है जिसे सुरक्षित रूप से Markdown डेटा URI में रखा जा सकता है।  
4. **`args.setResourceContentType("image/png")`** – यह सुनिश्चित करता है कि उत्पन्न Markdown टैग `![alt](data:image/png;base64,…)` जैसा दिखे। यदि आपके स्रोत दस्तावेज़ में JPEG हैं, तो आप मूल बाइट्स को देख कर `"image/jpeg"` चुन सकते हैं।  

> **Base64 क्यों?**  
> डेटा URI को समझने वाले Markdown प्रोसेसर सीधे चित्र को रेंडर करेंगे, और परिणामी फ़ाइल पोर्टेबल रहती है—कोई अतिरिक्त एसेट्स कॉपी करने की जरूरत नहीं। यह विशेष रूप से GitHub READMEs या दस्तावेज़ साइटों के लिए उपयोगी है जो बाहरी रिसोर्सेज़ को अनुमति नहीं देतीं।

## चरण 3: रूपांतरण करें

अब विकल्प तैयार हैं, बस अपना Word दस्तावेज़ लोड करें और `save` कॉल करें। आप जो पाथ देंगे वह उत्पन्न Markdown फ़ाइल का स्थान होगा।

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

बस इतना ही—वास्तविक रूपांतरण कोड की दो पंक्तियाँ। भारी काम (DOCX पढ़ना, इमेज निकालना, पैराग्राफ़ बदलना) सभी Aspose द्वारा संभाला जाता है।

## चरण 4: परिणाम सत्यापित करें – इनलाइन इमेजेज़ दिखें

`output/doc.md` को किसी भी टेक्स्ट एडिटर में खोलें। आपको कुछ इस तरह दिखना चाहिए:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

यदि आप Markdown को ऐसे व्यूअर में पेस्ट करते हैं जो डेटा URI को सपोर्ट करता है (GitHub, VS Code प्रीव्यू, या static‑site generator), तो चित्र बिना किसी अतिरिक्त फ़ाइल के रेंडर होगा।

**त्वरित जांच**:

- **`data:image/`** की खोज करें – यदि आपको कुछ लंबे स्ट्रिंग्स मिलते हैं, तो एम्बेडिंग सफल रही।  
- **`![](`** पैटर्न की गिनती करें – ये मूल Word फ़ाइल में छवियों की संख्या से मेल खाने चाहिए।

## किनारे के मामलों को संभालना

### बड़ी छवियाँ

Base64 मूल आकार को लगभग **33 %** बढ़ा देता है। बहुत बड़ी तस्वीरों (जैसे हाई‑रेज़ोल्यूशन फ़ोटो) के लिए, Markdown फ़ाइल भारी हो सकती है। इन रणनीतियों पर विचार करें:

| Strategy | When to use |
|----------|--------------|
| **कन्वर्ज़न से पहले रिसाइज़ करें** – `java.awt.Image` का उपयोग करके आकार घटाएँ। | जब स्रोत दस्तावेज़ में हाई‑रेज़ोल्यूशन एसेट्स हों जो पूर्ण आकार में आवश्यक नहीं हैं। |
| **JPEG में बदलें** – `args.setResourceContentType("image/jpeg")` बदलें। | फ़ोटोग्राफ़ के लिए जहाँ PNG का लॉसलेस फॉर्मेट ज़रूरत से अधिक है। |
| **डॉक्यूमेंट को चंक करें** – Word फ़ाइल को सेक्शन में बाँटें और प्रत्येक को अलग‑अलग एक्सपोर्ट करें। | जब आपको Markdown फ़ाइल को एक निश्चित आकार सीमा के भीतर रखना हो (उदाहरण के लिए, GitHub की 10 MB फ़ाइल सीमा)। |

### गैर‑PNG इमेजेज़

यदि आपके Word दस्तावेज़ में मिश्रित फ़ॉर्मेट हैं, तो आप डायनामिकली MIME टाइप का पता लगा सकते हैं:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose पहले से ही `ResourceContentType` भर देता है, इसलिए अक्सर आपको `"image/png"` को हार्ड‑कोड करने की जरूरत नहीं पड़ती।

### प्रदर्शन टिप्स

- **एक ही `Base64.Encoder` इंस्टेंस को पुनः उपयोग करें** यदि आप लूप में कई इमेजेज़ को बदल रहे हैं।  
- **`markdownSaveOptions.setExportImagesAsBase64(true)` को सक्षम करें** (यदि API संस्करण इसका समर्थन करता है) ताकि कॉलबैक पूरी तरह से न हो।  
- **कन्वर्ज़न को बैकग्राउंड थ्रेड में चलाएँ** जब सर्वर वातावरण में बड़े पैमाने पर दस्तावेज़ प्रोसेस कर रहे हों।

## पूर्ण कार्यशील उदाहरण (सभी एक साथ)

नीचे एक कॉपी‑पेस्ट‑तैयार Java प्रोग्राम है जिसमें इम्पोर्ट्स, एरर हैंडलिंग, और हमने चर्चा किया पूरा फ्लो शामिल है।

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**अपेक्षित आउटपुट**: एक ही `doc.md` फ़ाइल जिसमें इनलाइन Base64 इमेजेज़ हों, जो किसी भी Markdown‑सक्षम टूल के लिए तैयार हो।

## अक्सर पूछे जाने वाले प्रश्न

**Q1: क्या यह Aspose.Words के पुराने संस्करणों के साथ काम करता है?**  
*आमतौर पर हाँ.* कॉल्बैक API संस्करण 19 से स्थिर है। हालांकि, `setExportImagesAsBase64` शॉर्टकट बाद के रिलीज़ में आया, इसलिए यदि आप पुराने बिल्ड पर हैं तो आपको ऊपर दिखाए गए स्पष्ट कॉलबैक की आवश्यकता होगी।

**Q2: यदि मुझे GitHub Flavored Markdown (GFM) में एक्सपोर्ट करना हो तो?**  
Aspose की `MarkdownSaveOptions` पहले से ही GFM‑अनुकूल सिंटैक्स उत्पन्न करती है। एकमात्र अतिरिक्त कदम यह सुनिश्चित करना है कि आपके रेपो का रेंडरिंग इंजन डेटा URI को सपोर्ट करता हो—GitHub करता है।

**Q3: क्या मैं इस विधि को अन्य फ़ॉर्मेट्स, जैसे HTML, के लिए उपयोग कर सकता हूँ?**  
बिल्कुल। वही `ResourceSavingCallback` `HtmlSaveOptions` के साथ काम करता है। बस विकल्प क्लास को बदलें और Base64 लॉजिक को रखें।

---

##
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}