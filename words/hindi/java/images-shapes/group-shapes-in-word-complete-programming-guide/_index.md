---
category: general
date: 2026-08-14
description: Aspose.Words का उपयोग करके जावा में Word में शैप्स को समूहित करें। सीखें
  कि कैसे आयताकार शैप बनाएं, शैप के आयाम सेट करें, और एक खाली Word दस्तावेज़ में कई
  शैप्स को समूहित करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: hi
lastmod: 2026-08-14
og_description: Aspose.Words for Java का उपयोग करके Word में आकारों को समूहित करें।
  एक खाली Word दस्तावेज़ बनाएं, आयताकार आकार बनाएं, आकार के आयाम सेट करें, और कुछ
  ही मिनटों में कई आकारों को समूहित करें।
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Word में आकारों को समूहित करें – डेवलपर्स के लिए Java उदाहरण
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Word में आकृतियों को समूहित करना – पूर्ण प्रोग्रामिंग गाइड
url: /hi/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में आकृतियों को समूहित करना – पूर्ण प्रोग्रामिंग गाइड

यदि आपको **Word में आकृतियों को समूहित** करना है, तो यह ट्यूटोरियल आपको Java और Aspose.Words के साथ पूरी प्रक्रिया के माध्यम से ले जाएगा। आप सीखेंगे कि **खाली Word दस्तावेज़ कैसे बनाएं**, **आयताकार आकृति कैसे बनाएं**, **आकृति के आयाम कैसे सेट करें**, और अंत में **कई आकृतियों को समूहित करें** ताकि वे एकल वस्तु की तरह व्यवहार करें।

Word फ़ाइल में आकृतियों के साथ काम करना अक्सर बिना पेंटब्रश के कैनवास पर चित्र बनाने जैसा लगता है। इस गाइड के अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी Java प्रोजेक्ट में डाल सकते हैं, चाहे आप रिपोर्ट, इनवॉइस या कस्टम टेम्प्लेट बना रहे हों।

## आपको क्या चाहिए

- Java 8 या नया संस्करण
- Aspose.Words for Java (नवीनतम संस्करण, उदाहरण : 24.9)
- IntelliJ IDEA या Eclipse जैसे IDE
- ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी समझ

इन सभी पूर्वापेक्षाएँ मुफ्त में इंस्टॉल की जा सकती हैं, और नीचे दिया गया कोड एक ही Maven डिपेंडेंसी के साथ कंपाइल होता है:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## चरण 1: खाली Word दस्तावेज़ बनाएं और बिल्डर को इनिशियलाइज़ करें

सबसे पहले आपको **एक खाली Word दस्तावेज़ बनाना** होगा। यह आपको एक साफ़ कैनवास देता है जिस पर आप बाद में आकृतियाँ डाल सकते हैं।

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` पूरे *.docx* फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` वह सहायक है जो पैराग्राफ, टेबल और आकृतियों को डालता है। दोनों ऑब्जेक्ट्स को इनिशियलाइज़ करना किसी भी Word ऑटोमेशन कार्य की नींव है।

## चरण 2: समूह आकृति कंटेनर डालें

एक **समूह आकृति** एक फ़ोल्डर की तरह कार्य करती है जो अन्य आकृतियों को रख सकती है। पहले हम 400 pt × 200 pt के निश्चित आकार के साथ कंटेनर बनाते हैं।

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape` मेथड एक `GroupShape` ऑब्जेक्ट लौटाता है। सभी बाद की आकृतियों जिन्हें आप एक इकाई के रूप में व्यवहार करना चाहते हैं, उन्हें इस ऑब्जेक्ट में जोड़ना होगा।

## चरण 3: आयताकार आकृतियाँ बनाएं और आकार सेट करें

अब हम **आयताकार आकृति** ऑब्जेक्ट बनाते हैं, उनका आकार कॉन्फ़िगर करते हैं, और उन्हें समूह के भीतर स्थित करते हैं। यह चरण यह भी दर्शाता है कि **आकृति के आयाम** कैसे सटीक रूप से सेट करें।

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

दोनों आयताकार एक ही आयाम साझा करते हैं, लेकिन उनके `left` प्रॉपर्टी अलग हैं, इसलिए वे एक‑दूसरे के बगल में दिखते हैं। आप `setTop` और `setLeft` को बदलकर कोई भी लेआउट बना सकते हैं।

## चरण 4: समूहित आयताकारों वाला दस्तावेज़ सहेजें

आकृतियों को समूह में डालने के बाद, आप बस `Document` को सहेज देते हैं। परिणामी फ़ाइल दो आयताकार दिखाएगी जो चयनित होने पर साथ‑साथ चलेंगे।

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

प्रोग्राम चलाने पर कार्य निर्देशिका में `GroupShape.docx` बन जाएगा। इसे Microsoft Word में खोलें, एक आयताकार चुनें, और आप देखेंगे कि पूरा समूह एक इकाई के रूप में चलता है—बिल्कुल वही जो **Word में आकृतियों को समूहित** करने से अपेक्षित है।

![Group shapes in Word example](group-shapes.png){alt="Word में समूह आकृतियों का उदाहरण"}

*चित्र: Word दस्तावेज़ में दो आयताकार आकृतियों का समूहित रूप।*

## प्रो टिप: उसी समूह आकृति को पुनः उपयोग करना

यदि बाद में आपको और आकृतियाँ जोड़नी हों (जैसे : वृत्त, टेक्स्ट बॉक्स), तो `groupShape` का रेफ़रेंस रखें और `appendChild` को कॉल करना जारी रखें। इससे कंटेनर को पुनः बनाने की आवश्यकता नहीं पड़ेगी और सभी सदस्य सिंक्रनाइज़ रहेंगे।

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## किनारे के मामलों और सामान्य प्रश्न

- **यदि आकृतियाँ ओवरलैप करती हैं तो क्या होगा?** ओवरलैप की अनुमति है; Word उन्हें उसी क्रम में रेंडर करेगा जिसमें वे जोड़ी गई थीं। यदि आपको स्पष्ट स्टैकिंग चाहिए तो `setZOrder` का उपयोग करें।
- **क्या मैं विभिन्न पृष्ठों पर आकृतियों को समूहित कर सकता हूँ?** नहीं। `GroupShape` केवल एक पृष्ठ तक सीमित रहती है क्योंकि इसका कोऑर्डिनेट सिस्टम पृष्ठ‑सापेक्ष होता है।
- **क्या समूहित आकृतियों को फ़ॉर्मेटिंग विरासत में मिलती है?** प्रत्येक चाइल्ड अपनी स्वयं की फ़ॉर्मेटिंग (फ़िल रंग, लाइन स्टाइल) रखता है। समान शैली लागू करने के लिए `groupShape.getChildNodes()` पर इटररेट करें और प्रॉपर्टी प्रोग्रामेटिकली सेट करें।

## संदर्भ के लिए पूर्ण स्रोत कोड

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

प्रोग्राम चलाने पर एक DOCX फ़ाइल बनती है जहाँ दो आयताकार **समूहित** होते हैं। किसी भी आयताकार को चुनने पर दोनों एक साथ चलते हैं, जिससे पुष्टि होती है कि आपने सफलतापूर्वक **कई आकृतियों को समूहित** किया है।

## निष्कर्ष

आप अब जानते हैं कि Java का उपयोग करके **Word में आकृतियों को समूहित** कैसे करें, **खाली Word दस्तावेज़ बनाना**, **आयताकार आकृति बनाना**, **आकृति के आयाम सेट करना**, और अंत में **कई आकृतियों को एकल, चलने योग्य वस्तु** में समूहित करना। यह पैटर्न किसी भी संख्या में आकृतियों के लिए स्केलेबल है और टेक्स्ट, इमेज या चार्ट के साथ मिलाकर समृद्ध, प्रोग्रामेटिक दस्तावेज़ बनाने में मदद करता है।

### आगे क्या है?

- विभिन्न प्रकार (एलिप्स, एरो, टेक्स्ट बॉक्स) के साथ **कई आकृतियों को समूहित** करने का अन्वेषण करें।
- `shape.getFillColor()` और `shape.getLine().setColor()` को कॉल करके फ़िल रंग या बॉर्डर लागू करें।
- संरचित रिपोर्टों के लिए टेबल सेल में समूहित आकृति डालें।
- इस दृष्टिकोण को मेल‑मर्ज के साथ संयोजित करके व्यक्तिगत अनुबंध बनाएं जिनमें ब्रांडेड ग्राफ़िक्स शामिल हों।

बिना हिचकिचाए प्रयोग करें, आयाम बदलें, या अतिरिक्त सामग्री एम्बेड करें। जब आप समूहित करने में निपुण हो जाएंगे, तो आपके Word ऑटोमेशन स्क्रिप्ट अधिक लचीले और रखरखाव योग्य बन जाएंगे। हैप्पी कोडिंग!

## अगला क्या सीखें?

यहाँ कुछ ट्यूटोरियल हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं और संबंधित विषयों को गहराई से कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच का पता लगा सकते हैं।

- [Aspose.Words for Java में दस्तावेज़ आकृतियों का उपयोग](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Word दस्तावेज़ Java – शैडो इफ़ेक्ट के साथ आयताकार आकृति जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकृति बनाएं](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}