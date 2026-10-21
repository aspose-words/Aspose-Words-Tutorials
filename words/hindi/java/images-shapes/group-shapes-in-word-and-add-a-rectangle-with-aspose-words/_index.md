---
category: general
date: 2026-09-11
description: Word में शैप्स को समूहित करें और Aspose.Words for Java का उपयोग करके
  एक आयताकार शैप जोड़ें। शैप का आकार सेट करना, ऑब्जेक्ट्स को समूहित करना और दस्तावेज़
  को सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: hi
lastmod: 2026-09-11
og_description: Word में शैप्स को समूहित करें और Aspose.Words for Java का उपयोग करके
  एक आयताकार शैप जोड़ें। यह ट्यूटोरियल दिखाता है कि शैप का आकार कैसे सेट करें, शैप्स
  को समूहित करें, और दस्तावेज़ को निर्यात करें।
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Word में समूह आकृतियों – Aspose.Words के साथ आयत जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Word में आकृतियों को समूहित करें और Aspose.Words के साथ एक आयत जोड़ें
url: /hi/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में शैप्स को ग्रुप करें और Aspose.Words के साथ एक आयत जोड़ें

यदि आपको **Word में शैप्स को ग्रुप** करना है जबकि प्रोग्रामेटिकली एक आयत जोड़नी है, तो यह गाइड एक पूर्ण, तैयार‑चलाने‑योग्य समाधान प्रदान करता है। आप देखेंगे कि ग्रुप शैप कैसे डालें, आयत शैप जोड़ें, शैप का आकार सेट करें, और अंत में दस्तावेज़ को सहेजें ताकि आप तुरंत परिणाम देख सकें।

Word दस्तावेज़ों के साथ काम करना अक्सर कई ऑब्जेक्ट्स—चित्र, चार्ट, या साधारण ज्यामितीय शैप्स—को एक ही तार्किक इकाई में व्यवस्थित करने को शामिल करता है। इन ऑब्जेक्ट्स को ग्रुप करने से उन्हें एक साथ ले जाना, घुमाना, या स्टाइल करना आसान हो जाता है। इस ट्यूटोरियल में हम **आयत शैप्स कैसे जोड़ें** और **परिपूर्ण लेआउट नियंत्रण के लिए शैप आकार कैसे सेट करें** भी कवर करेंगे।

## आप क्या सीखेंगे

* Aspose.Words for Java के साथ एक नया Word दस्तावेज़ कैसे बनाएं।  
* **शैप्स को ग्रुप** कैसे करें ताकि वे एक ही ऑब्जेक्ट की तरह व्यवहार करें।  
* ग्रुप में **आयत शैप जोड़ें** और उसी ग्रुप में एक चित्र डालें।  
* आयत और चित्र दोनों के लिए **शैप आकार सेट** करें।  
* दस्तावेज़ को सहेजें और Microsoft Word में खोलकर परिणाम सत्यापित करें।

### पूर्वापेक्षाएँ

* Java 17 या उससे नया स्थापित हो।  
* निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।  
* एक वैध Aspose.Words for Java लाइसेंस (या एक मुफ्त इवैल्यूएशन की)।  
* एक चित्र फ़ाइल (`sample.png`) जिसे ज्ञात डायरेक्टरी में रखा गया हो (`YOUR_DIRECTORY` को अपने वास्तविक पथ से बदलें)।

---

## Aspose.Words का उपयोग करके Word में शैप्स को ग्रुप करने का तरीका

पहला कदम है एक `Document` और एक `DocumentBuilder` बनाना। बिल्डर आपको शैप्स, टेक्स्ट और अन्य तत्वों को डालने के लिए एक सुविधाजनक API प्रदान करता है।

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **यह क्यों महत्वपूर्ण है:** `DocumentBuilder` सीधे अंतर्निहित `Document` ऑब्जेक्ट के साथ काम करता है, जिससे आप शैप्स को मैन्युअली लो‑लेवल नोड कलेक्शन्स को संभाले बिना डाल सकते हैं।

### ग्रुप शैप जोड़ें

एक ग्रुप शैप एक कंटेनर है जो अन्य शैप्स को रख सकता है। इसे ड्राइंग ऑब्जेक्ट्स के फ़ोल्डर की तरह सोचें।

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()` मेथड एक `GroupShape` नोड बनाता है और उसे रिटर्न करता है ताकि आप बाद में चाइल्ड शैप्स को जोड़ सकें।  

---

## ग्रुप में आयत शैप जोड़ें

अब हम पहले बनाए गए ग्रुप में **आयत शैप** जोड़ेंगे। आयत चित्र के लिए बैकग्राउंड या बॉर्डर के रूप में काम करेगी।

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **टिप:** `FillColor` और `StrokeColor` सेट करने से आयत अंतिम दस्तावेज़ में दिखाई देती है। यदि आप इन प्रॉपर्टीज़ को छोड़ देते हैं, तो शैप पारदर्शी दिख सकता है।

### आयत कैसे जोड़ें

ऊपर का कोड **आयत जोड़ने** का तरीका दर्शाता है, जहाँ `Shape` इंस्टेंस को `ShapeType.RECTANGLE` के साथ बनाया जाता है और फिर `GroupShape` में अपेंड किया जाता है। यह पैटर्न किसी भी अन्य शैप टाइप (जैसे `ELLIPSE`, `POLYLINE`) के लिए भी काम करता है।

---

## आयत और चित्र के लिए शैप आकार सेट करें

सही आकार सुनिश्चित करता है कि आयत और चित्र सही ढंग से संरेखित हों। यहाँ हम अगली बार डालने वाले चित्र के लिए भी **शैप आकार सेट** करते हैं।

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

अब आयत और चित्र दोनों के आयाम समान हैं (100 × 50 पॉइंट)। क्योंकि वे एक ही ग्रुप में हैं, ग्रुप को ले जाने या घुमाने से दोनों शैप्स एक साथ प्रभावित होते हैं।

> **आकार मिलाने का कारण:** आयामों को मिलाने से यह गारंटी मिलती है कि चित्र आयत के भीतर साफ़‑सुथरे ढंग से बैठता है, जिससे एक “फ़्रेम्ड पिक्चर” प्रभाव बनता है।

---

## दस्तावेज़ सहेजें और परिणाम देखें

अंत में, हम दस्तावेज़ को डिस्क पर लिखते हैं। Microsoft Word में फ़ाइल खोलने से ग्रुपेड शैप्स एकल चयन योग्य ऑब्जेक्ट के रूप में दिखेंगे।

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

जब आप `output.docx` खोलेंगे, तो आपको आयत के अंदर चित्र दिखेगा। शैप पर क्लिक करने से आयत और चित्र दोनों चयनित हो जाते हैं क्योंकि वे **ग्रुपेड** हैं।

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*चित्र वैकल्पिक पाठ:* *group shapes in word example* – एक Word दस्तावेज़ जिसमें ग्रुपेड आयत और चित्र दिखाया गया है।

---

## सामान्य प्रश्न और किनारे‑के‑केस हैंडलिंग

| प्रश्न | उत्तर |
|----------|--------|
| **यदि मुझे चित्र का आकार अलग चाहिए तो क्या करें?** | डालने के बाद `picture.setWidth()` और `picture.setHeight()` को समायोजित करें। आयत अपना मूल आकार रख सकती है, या आप उसे भी मिलाने के लिए री‑साइज़ कर सकते हैं। |
| **क्या मैं उसी ग्रुप में और शैप्स जोड़ सकता हूँ?** | हाँ। किसी भी अतिरिक्त `Shape` ऑब्जेक्ट के लिए `group.appendChild(newShape)` कॉल करें। |
| **पूरे ग्रुप को कैसे घुमाऊँ?** | `group.setRotationAngle(double angleInRadians)` उपयोग करें। घुमाव प्रत्येक चाइल्ड शैप पर लागू होगा। |
| **यदि चित्र फ़ाइल गायब हो तो क्या होगा?** | `insertImage` `FileNotFoundException` थ्रो करता है। कॉल को try‑catch ब्लॉक में रैप करें और एक प्लेसहोल्डर शैप प्रदान करें। |
| **क्या बाद में अनग्रुप करना संभव है?** | `group.removeAllChildren()` कॉल करके चाइल्ड्स को डिटैच करें, फिर उन्हें व्यक्तिगत रूप से दस्तावेज़ में पुनः डालें। |

---

## निष्कर्ष

अब आपके पास एक पूर्ण, चलाने‑योग्य उदाहरण है जो **Word में शैप्स को ग्रुप** करने, **आयत शैप जोड़ने**, **शैप आकार सेट करने**, और Aspose.Words for Java का उपयोग करके दस्तावेज़ **सहेजने** को दर्शाता है। आयत और चित्र को ग्रुप करके आप उन्हें एक ही इकाई के रूप में ले, रिसाइज़ या घुमा सकते हैं—जो कई दस्तावेज़‑ऑटोमेशन परिदृश्यों में आवश्यक होता है।

अब आप आगे खोज सकते हैं:

* उसी ग्रुप में टेक्स्ट बॉक्स जोड़ना (`how to add rectangle`‑स्टाइल टेक्स्ट)।  
* विभिन्न फ़िल पैटर्न या ग्रेडिएंट लागू करना (`set shape size` के साथ स्टाइलिंग)।  
* इस तकनीक का उपयोग करके चार्ट, टेबल, या SmartArt को ग्रुप करना (`how to group shapes` को अन्य ऑब्जेक्ट प्रकारों पर लागू करना)।  

अन्य शैप टाइप, रंग, और लेआउट विकल्पों के साथ प्रयोग करने के लिए स्वतंत्र महसूस करें। हैप्पी कोडिंग!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}