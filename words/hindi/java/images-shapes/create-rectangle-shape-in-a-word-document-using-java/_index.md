---
category: general
date: 2026-11-15
description: जावा के साथ वर्ड में आयताकार आकार बनाएं और सीखें कि वर्ड में आकार कैसे
  जोड़ें, आकार के आयाम सेट करें, और वर्ड दस्तावेज़ को कुशलतापूर्वक सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: hi
lastmod: 2026-11-15
og_description: जावा का उपयोग करके वर्ड दस्तावेज़ में आयताकार आकार बनाएं। वर्ड में
  आकार जोड़ना, आकार के आयाम सेट करना, और कुछ ही मिनटों में वर्ड दस्तावेज़ को सहेजना
  सीखें।
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: जावा के साथ वर्ड में आयताकार आकार बनाएं – चरण-दर-चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: जावा का उपयोग करके वर्ड दस्तावेज़ में आयताकार आकार बनाएं
url: /hi/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा का उपयोग करके Word दस्तावेज़ में आयताकार आकार बनाएं

यदि आपको Word फ़ाइल के अंदर **आयताकार आकार बनाना** है, तो यह गाइड आपको जावा के साथ इसे कैसे करें, बिल्कुल दिखाएगा। आप देखेंगे कि **Word में आकार जोड़ें**, **आकार के आयाम सेट करें**, और अंत में **Word दस्तावेज़ सहेजें** बिना अपने IDE को छोड़े।

आगे के अनुभागों में आपको एक पूर्ण, चलाने योग्य उदाहरण, प्रत्येक पंक्ति की व्याख्या, और सामान्य समस्याओं जैसे आकार संबंधी मुद्दे और दस्तावेज़ संगतता के लिए टिप्स मिलेंगे। कोई बाहरी संदर्भ आवश्यक नहीं—केवल Aspose.Words for Java लाइब्रेरी चाहिए।

## आप क्या सीखेंगे

* `Document` और `DocumentBuilder` को कैसे प्रारंभ करें।
* **ग्रुप शेप** कैसे डालें और उसके अंदर आयताकार रखें।
* `setWidth` और `setHeight` का उपयोग करके **आकार का आकार निर्धारित करें**।
* `.docx` फ़ॉर्मेट में **Word दस्तावेज़ सहेजें**।
* विभिन्न पृष्ठ आकार और DPI सेटिंग्स के लिए किनारे‑केस हैंडलिंग।

### आवश्यकताएँ

* Java 17 या बाद का (कोड Java 8 के साथ भी संकलित होता है)।
* Aspose.Words for Java 23.10 या नया – इसे Maven Central से प्राप्त किया जा सकता है।
* जावा सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड अवधारणाओं की बुनियादी समझ।

> **Pro tip:** यदि आप बाद में अधिक आकार (जैसे, वृत्त या टेक्स्ट बॉक्स) जोड़ने की योजना बनाते हैं, तो उन्हें उसी `GroupShape` के अंदर रखें। इससे पूरे संग्रह को एक साथ स्थानांतरित, घुमाने या फ़ॉर्मेट करने में बहुत आसानी होगी।

## चरण 1: दस्तावेज़ और बिल्डर को प्रारंभ करें

पहला चरण एक खाली Word फ़ाइल बनाना और एक `DocumentBuilder` बनाना है जो आपको सामग्री लिखने देता है।  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* एक `Document` पूरी फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` टेक्स्ट, टेबल और **आकार** डालने के लिए उच्च‑स्तरीय मेथड प्रदान करता है। बिल्डर के बिना आपको निचले‑स्तर के नोड्स को मैन्युअल रूप से संभालना पड़ेगा।

## चरण 2: कई आकारों को रखने के लिए ग्रुप शेप डालें

एक **ग्रुप शेप** कंटेनर की तरह काम करता है; आप कई आकार जोड़ सकते हैं और बाद में उन्हें एक ही ऑब्जेक्ट के रूप में संभाल सकते हैं (जैसे, साथ‑साथ ले जाना या घुमाना)।

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use a group shape?* यदि आप बाद में आयत के चारों ओर तीर, वृत्त या लेबल जोड़ते हैं, तो ग्रुप सब कुछ संरेखित रखता है। यह **Word में आकार जोड़ें** कार्यप्रवाह को भी सरल बनाता है क्योंकि प्रत्येक नए आकार के लिए आपको केवल एक `appendChild` कॉल करनी होती है।

## चरण 3: आयताकार आकार बनाएं

अब हम वह वास्तविक आयत बनाते हैं जो ग्रुप के अंदर रहेगा। `Shape` कंस्ट्रक्टर को मालिक `Document` और इच्छित आकार प्रकार की आवश्यकता होती है।

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Why a rectangle?* `ShapeType.RECTANGLE` सबसे सामान्य प्रिमिटिव है जो सेक्शन को हाइलाइट करने, प्लेसहोल्डर बनाने, या Word के अंदर सीधे सरल UI मॉक‑अप ड्रॉ करने के लिए उपयोग किया जाता है।

## चरण 4: आयत के आकार को निर्धारित करें

आयाम सेट करना वह जगह है जहाँ **set shape dimensions** महत्वपूर्ण हो जाता है। आप Aspose.Words द्वारा समर्थित कोई भी माप इकाई उपयोग कर सकते हैं; डिफ़ॉल्ट पॉइंट्स है (1 pt = 1/72 इंच)।

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** यदि आप मिलीमीटर पसंद करते हैं, तो `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` कॉल करें जहाँ `1.39 in ≈ 35 mm`। यह **define shape size** की लचीलापन दर्शाता है।

## चरण 5: आयत को ग्रुप शेप में जोड़ें

पहले बनाए गए ग्रुप में आयत को जोड़ने से वह दस्तावेज़ में दिखाई देगा।

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

इस बिंदु पर आयत ग्रुप के शीर्ष‑बाएँ कोने में स्थित है। यदि आपको सटीक स्थान चाहिए तो आप बाद में `rectangle.setLeft(...)` और `rectangle.setTop(...)` से इसे ले जा सकते हैं।

## चरण 6: (वैकल्पिक) परिणाम देखने के लिए दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। यही **save Word document** चरण है जो एक `.docx` फ़ाइल बनाता है जिसे आप Microsoft Word, LibreOffice, या Google Docs में खोल सकते हैं।

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

प्रोग्राम चलाने से `RectangleShapeDemo.docx` बनता है जिसमें ग्रुप शेप के अंदर एकल आयत होती है। फ़ाइल खोलने पर एक साधारण सफ़ेद आयत दिखेगी—बिल्कुल वही आकार जो आपने निर्धारित किया था।

### अपेक्षित आउटपुट

* `RectangleShapeDemo.docx` नामक एक Word फ़ाइल।
* पहले पैराग्राफ के अंदर, 100 pt × 50 pt आयत वाला एक ग्रुप शेप।
* कोई टेक्स्ट नहीं जोड़ा गया, इसलिए आयत एक खाली पृष्ठ पर दिखाई देती है।

## सामान्य विविधताएँ और किनारे‑केस

| स्थिति | कोड को कैसे अनुकूलित करें |
|-----------|-----------------------|
| **विभिन्न पृष्ठ आकार** (जैसे, A4) | आकार डालने से पहले `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` कॉल करें। |
| **प्रिंटिंग के लिए उच्च DPI** | चौड़ाई/ऊँचाई को इच्छित DPI गुणक से गुणा करें, उदाहरण: `rectangle.setWidth(200 * 2);` दोहरी रिज़ॉल्यूशन के लिए। |
| **आयत के अंदर टेक्स्ट लेबल जोड़ना** | `TEXT_BOX` प्रकार का `Shape` बनाएं, उसकी `setWidth`/`setHeight` को आयत के समान सेट करें, फिर उसे उसी `GroupShape` में जोड़ें। |
| **आयत को घुमाना** | `rectangle.setRotationAngle(45);` का उपयोग करके 45 डिग्री घड़ी की दिशा में घुमाएँ। |
| **DOCX के बजाय PDF के रूप में सहेजना** | `document.save("output.docx");` को `document.save("output.pdf");` से बदलें – वही API PDF के लिए भी काम करता है, आयत को संरक्षित रखता है। |

## मजबूत कार्यान्वयन के लिए प्रो टिप्स

1. **बिल्डर को पुन: उपयोग करें** – ग्रुप शेप डालने के बाद आप नया बिल्डर बनाए बिना पैराग्राफ या टेबल जोड़ते रह सकते हैं।
2. **संसाधनों को मुक्त करें** – यद्यपि Java का गार्बेज कलेक्टर अधिकांश ऑब्जेक्ट संभालता है, स्ट्रीम उपयोग करने पर स्पष्ट रूप से `document.close();` कॉल करने से फ़ाइल‑हैंडल लीक से बचा जा सकता है।
3. **आयाम की वैधता जांचें** – `setWidth`/`setHeight` कॉल करने से पहले सुनिश्चित करें कि मान सकारात्मक हैं; नकारात्मक मान `IllegalArgumentException` फेंकेगा।
4. **संस्करण संगतता** – कोड Aspose.Words 23.x और बाद के संस्करणों के साथ काम करता है। पुराने संस्करणों में अलग‑अलग सेटर्स की बजाय `Shape.setSize(width, height)` का उपयोग आवश्यक हो सकता है।

## पूर्ण, चलाने योग्य उदाहरण

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** `output/RectangleShapeDemo.docx` को Microsoft Word में खोलें। आपको पहले पृष्ठ के शीर्ष पर निर्दिष्ट आकार की आयत दिखाई देनी चाहिए। यदि आयत बहुत छोटी दिखे, तो `setWidth` और `setHeight` में पास किए गए मानों को समायोजित करें।

## निष्कर्ष

अब आप जावा का उपयोग करके Word फ़ाइल में **आयताकार आकार बनाना**, `GroupShape` के माध्यम से **Word में आकार जोड़ें**, **आकार के आयाम सेट करें** और **आकार का आकार निर्धारित करें**, और अंत में **Word दस्तावेज़ सहेजें** के बारे में जानते हैं। वही पैटर्न अन्य आकार प्रकारों के लिए भी काम करता है, जिससे आप प्रोग्रामेटिक रूप से जटिल आरेख बना सकते हैं।

### आगे क्या करें?

* **Word में आकार जोड़ें** का अन्वेषण करें – वृत्त, तीर या टेक्स्ट बॉक्स डालें।
* कई आकारों को एक ही `GroupShape` में मिलाकर ट्रांसफ़ॉर्मेशन (घुमाना, फ़्लिप) लागू करें।
* रिपोर्ट बनाएं जो चार्ट को आकार के रूप में एम्बेड करे, फिर **Word दस्तावेज़ सहेजें** को PDF में बदलकर साझा करें।

आकार, रंग और स्थिति को अपनी विशिष्ट स्थिति के अनुसार प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## आप अगला क्या सीखेंगे?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}