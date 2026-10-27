---
category: general
date: 2026-10-26
description: Aspose.Words for Java का उपयोग करके प्रोग्रामेटिक रूप से Word दस्तावेज़
  बनाना, एक आकार जोड़ना, और Word में ऑब्जेक्ट को छिपाना सीखें – चरण‑दर‑चरण मार्गदर्शिका।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: hi
lastmod: 2026-10-26
og_description: प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाएं, Aspose.Words for Java के
  साथ Word में आकार जोड़ना और वस्तु को छिपाना सीखें। पूर्ण, चलाने योग्य उदाहरण।
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाएं – Java में आकार जोड़ें और छुपाएँ
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: जावा में प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं और एक आकार जोड़ें
url: /hi/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में प्रोग्रामेटिकली Word दस्तावेज़ बनाएं और एक shape जोड़ें

यदि आपको **प्रोग्रामेटिकली Word दस्तावेज़ बनाना** है, तो यह ट्यूटोरियल आपको ठीक-ठीक दिखाता है कि इसे कैसे करें, एक shape कैसे जोड़ें, और फिर Word में ऑब्जेक्ट को कैसे छुपाएँ। चाहे आप रिपोर्ट जेनरेटर बना रहे हों या स्वचालित कॉन्ट्रैक्ट सिस्टम, आपको कुछ ही मिनटों में एक पूर्ण, तैयार‑चलाने‑योग्य समाधान मिलेगा।

आप सीखेंगे कैसे:

* Aspose.Words for Java के साथ एक Word दस्तावेज़ इनिशियलाइज़ करें।  
* **how to add shape** तकनीक का उपयोग करके एक ellipse (या कोई अन्य shape) डालें।  
* उस shape को छुपाएँ ताकि फ़ाइल खोलते समय वह कभी न दिखे, **how to hide shape** प्रश्न का उत्तर देते हुए।  

Aspose.Words लाइब्रेरी के अलावा कोई बाहरी टूल आवश्यक नहीं है, और कोड Java 17 और उसके बाद के संस्करणों के साथ काम करता है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Java Development Kit (JDK) 17 या नया संस्करण स्थापित हो।  
* Maven या Gradle ताकि डिपेंडेंसीज़ मैनेज की जा सकें (उदाहरण में Maven उपयोग किया गया है)।  
* एक वैध Aspose.Words for Java लाइसेंस (टेस्टिंग के लिए मुफ्त इवैल्यूएशन चल सकता है)।  

यदि आप Aspose.Words में नए हैं, तो आधिकारिक Getting Started गाइड देखें, लेकिन इस ट्यूटोरियल को फॉलो करने के लिए उसे पढ़ने की ज़रूरत नहीं है।

## Maven dependency

अपने `pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** संस्करण संख्या को अपडेट रखें; नए रिलीज़ में shape हैंडलिंग के बग फ़िक्स शामिल होते हैं।

## Step 1: Create Word document programmatically – initializing the document

जब आप **प्रोग्रामेटिकली Word दस्तावेज़ बनाते** हैं, तो पहला कदम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना होता है। यह ऑब्जेक्ट मेमोरी में पूरी .docx फ़ाइल का प्रतिनिधित्व करता है।

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters*: `Document` क्लास सभी Word‑प्रोसेसिंग ऑपरेशन्स का एंट्री पॉइंट है। इसके बिना आप पेज, पैराग्राफ या shapes नहीं जोड़ सकते।

## Step 2: How to add shape – inserting an ellipse

अब हम ट्यूटोरियल के **how to add shape** भाग को कवर करेंगे। Aspose.Words कई shape प्रकारों (Ellipse, Rectangle, TextBox, आदि) को सपोर्ट करता है। नीचे हम 50 पॉइंट की चौड़ाई और ऊँचाई वाले एक ellipse को इन्सर्ट करेंगे।

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

`insertShape` मेथड एक `Shape` ऑब्जेक्ट रिटर्न करता है जिसे आप आगे कस्टमाइज़ कर सकते हैं—रंग, लाइन स्टाइल, रोटेशन, आदि। कोऑर्डिनेट्स पॉइंट्स (1/72 इंच) में मापे जाते हैं।

*Why you might want to add a shape*: Shapes वॉटरमार्क, सजावटी एलिमेंट या प्लेसहोल्डर के लिए उपयोगी होते हैं, जिन्हें आप बाद में छुपा या बदल सकते हैं।

## Step 3: How to hide shape – making the object invisible in Word

**how to hide shape** प्रश्न का उत्तर देने के लिए, बस shape की `Hidden` प्रॉपर्टी को `true` सेट करें। इससे Word इस shape को एक छुपे हुए ऑब्जेक्ट के रूप में ट्रीट करता है, और यह दस्तावेज़ व्यू या प्रिंटआउट में कभी रेंडर नहीं होता।

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

यदि आपको किसी विशेष यूज़र या कंडीशन के लिए **Word में ऑब्जेक्ट छुपाना** है, तो आप इस प्रॉपर्टी को रनटाइम में अपने बिज़नेस लॉजिक के आधार पर टॉगल कर सकते हैं।

> **Note:** Hidden shapes अभी भी दस्तावेज़ की XML स्ट्रक्चर का हिस्सा होते हैं। उन्हें बाद में `setHidden(false)` करके फिर से दिखाया जा सकता है।

## Step 4: Save the document

shape को जोड़ने और छुपाने के बाद, दस्तावेज़ को डिस्क पर लिखें।

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

जब आप `HiddenShapeDemo.docx` को Microsoft Word में खोलेंगे, तो आपको एक खाली पेज दिखेगा क्योंकि ellipse छुपा हुआ है। दस्तावेज़ अन्यथा किसी सामान्य Word फ़ाइल की तरह व्यवहार करता है।

## Full working example

सभी हिस्सों को मिलाकर, यहाँ पूरा, रन करने योग्य प्रोग्राम है:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Expected output**

```
Document created successfully.
```

`HiddenShapeDemo.docx` खोलने पर एक खाली पेज दिखेगा; छुपा हुआ ellipse रेंडर नहीं होता, जिससे **Word में ऑब्जेक्ट छुपाने** की ऑपरेशन सफल हुई यह पुष्टि होती है।

## Edge cases and variations

| स्थिति | क्या बदलें | क्यों |
|-----------|----------------|-----|
| Hide a rectangle instead of an ellipse | Use `ShapeType.RECTANGLE` in `insertShape` | Different visual placeholder |
| Hide multiple shapes at once | Loop through `doc.getChildNodes(NodeType.SHAPE, true)` and set `setHidden(true)` | Useful for bulk processing |
| Show the shape only in print view | Set `shape.setVisible(false)` and `shape.setPrint(true)` | Word distinguishes between screen and print visibility |
| Use a different measurement unit | Call `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Aligns with your layout requirements |

## Common pitfalls

* **`setHidden(true)` कॉल करना भूल जाना** – shape सामान्य रूप से दिखाई देगा।  
* **shape को छुपाने से पहले दस्तावेज़ को सेव करना** – क्रम महत्वपूर्ण है; पहले छुपाएँ, फिर सेव करें।  
* **पुराना Aspose.Words संस्करण उपयोग करना** – पुराने रिलीज़ में `setHidden` API नहीं हो सकता।  

हमीशा उत्पन्न फ़ाइल को लक्षित Microsoft Word संस्करण में टेस्ट करें ताकि छुपी हुई स्थिति अपेक्षित रूप से काम करे।

## Conclusion

इस गाइड में आपने सीखा कि **प्रोग्रामेटिकली Word दस्तावेज़ कैसे बनाएं**, **shape कैसे जोड़ें**, और **Word में ऑब्जेक्ट कैसे छुपाएँ** Aspose.Words for Java का उपयोग करके। पूरा उदाहरण शुरुआती से लेकर फ़ाइल को सेव करने तक के सभी कदम दर्शाता है जहाँ shape कभी नहीं दिखता।

अब आप कर सकते हैं:

* अन्य shape प्रकारों (`ShapeType.LINE`, `ShapeType.TEXT_BOX`) के साथ प्रयोग करें।  
* बुकमार्क्स के साथ छुपे हुए shapes को मिलाकर डायनामिक टेम्प्लेट बनाएं।  
* `setVisible` और `setPrint` प्रॉपर्टीज़ को एक्सप्लोर करें ताकि ऑब्जेक्ट विज़िबिलिटी पर अधिक ग्रैन्युलर कंट्रोल मिल सके।

Happy coding, and enjoy automating your Word documents!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकते हैं।

- [Aspose.Words for Java के साथ खाली Word दस्तावेज़ कैसे बनाएं](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Java का उपयोग करके Word दस्तावेज़ में shape कैसे छुपाएँ](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Word दस्तावेज़ Java – Rectangle shape को शैडो इफ़ेक्ट के साथ जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}