---
category: general
date: 2026-09-27
description: Java में एक खाली Word दस्तावेज़ बनाएं और Aspose.Words का उपयोग करके आकृतियों
  को समूहित करें। आकार सेट करना, आकृति का भराव रंग निर्धारित करना, और समूह में चाइल्ड
  जोड़ना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: hi
lastmod: 2026-09-27
og_description: Aspose.Words के साथ जावा में एक खाली वर्ड दस्तावेज़ बनाएं। यह ट्यूटोरियल
  दिखाता है कि वर्ड में आकृतियों को कैसे समूहित किया जाए, आकृति का आकार कैसे सेट किया
  जाए, आकृति का भराव रंग कैसे सेट किया जाए, और समूह में चाइल्ड को कैसे जोड़ें।
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: जावा में एक खाली वर्ड दस्तावेज़ बनाएं और आकृतियों को समूहित करें – चरण‑दर‑चरण
  मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: जावा में खाली वर्ड दस्तावेज़ कैसे बनाएं और आकृतियों को समूहित करें
url: /hi/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में ब्लैंक वर्ड डॉक्यूमेंट बनाना और शैप्स को ग्रुप करना

यदि आपको प्रोग्रामेटिकली **ब्लैंक वर्ड डॉक्यूमेंट बनाना** है, तो यह गाइड Aspose.Words for Java के साथ इसे कैसे करना है, बिल्कुल दिखाता है। आप यह भी सीखेंगे कि **वर्ड में शैप्स को ग्रुप कैसे करें**, प्रत्येक शैप का आकार सेट करें, फ़िल कलर लागू करें, और **ग्रुप में चाइल्ड जोड़ें** ताकि ऑब्जेक्ट्स एक इकाई की तरह व्यवहार करें।

कोड से वर्ड फ़ाइलों के साथ काम करने से मैन्युअल फ़ॉर्मेटिंग से बचा जा सकता है और रिपोर्ट, कॉन्ट्रैक्ट या मार्केटिंग ब्रोशर को स्वचालित रूप से जेनरेट किया जा सकता है। इस ट्यूटोरियल के अंत तक आपके पास एक रनएबल जावा प्रोग्राम होगा जो एक `.docx` फ़ाइल बनाता है जिसमें एक नीला आयत और एक इमेज दोनों ग्रुपेड होते हैं।

## प्रीरेक्विज़िट्स

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- Java 17 (या कोई भी नवीनतम JDK) स्थापित हो।
- निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।
- Aspose.Words for Java लाइसेंस (टेस्टिंग के लिए मुफ्त इवैल्यूएशन काम करता है)।
- एक सैंपल इमेज फ़ाइल (जैसे `sample.jpg`) को ऐसे फ़ोल्डर में रखें जिसे आप कोड से रेफ़र कर सकें।

> **Pro tip:** अपनी इमेज फ़ाइलों को `resources` डायरेक्टरी में रखें और उन्हें `ClassLoader.getResourceAsStream` से लोड करें ताकि हार्ड‑कोडेड एब्सोल्यूट पाथ से बचा जा सके।

## Step 1: Create a blank word document and add a GroupShape

पहला कदम एक नया `Document` ऑब्जेक्ट इंस्टैंशिएट करना है, जो एक खाली वर्ड फ़ाइल का प्रतिनिधित्व करता है, और फिर एक `GroupShape` इन्सर्ट करना है। यह ग्रुप बाद में आप जो भी शैप्स जोड़ेंगे, उनके लिए कंटेनर के रूप में काम करेगा।

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Why this matters:* एक `GroupShape` आपको कई शैप्स को साथ में मूव, रोटेट या फ़ॉर्मेट करने की सुविधा देता है, जो डायग्राम या वाटरमार्क जैसे जटिल लेआउट्स के लिए आवश्यक है।

## Step 2: Insert a rectangle and **set shape size**

अब एक आयत बनाएं, उसके आयाम निर्धारित करें, और उसे ग्रुप में जोड़ें। यह **set shape size** ऑपरेशन को दर्शाता है।

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explanation:* `setWidth` और `setHeight` शैप के सटीक आकार को पॉइंट्स में नियंत्रित करते हैं (1 पॉइंट = 1/72 इंच)। अपने लेआउट की जरूरतों के अनुसार इन मानों को समायोजित करें।

## Step 3: **Set shape fill color** for the rectangle

आयत की बैकग्राउंड को `setFillColor` का उपयोग करके नीला सेट किया गया है। आप कोई भी `java.awt.Color` कॉन्स्टेंट या कस्टम RGB कलर बना सकते हैं।

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Why it’s useful:* फ़िल कलर ऑब्जेक्ट्स को दृश्य रूप से अलग करने में मदद करता है, विशेषकर जब आप बाद में डॉक्यूमेंट को PDF में एक्सपोर्ट या प्रिंट करते हैं।

## Step 4: Insert an image and **append child to group**

अब उसी `GroupShape` में एक इमेज जोड़ें। इमेज `DocumentBuilder.insertImage` द्वारा इन्सर्ट की जाती है, फिर उसे ग्रुप में अपेंड किया जाता है ताकि वह आयत के साथ मूव करे।

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Edge case:* यदि इमेज पाथ गलत है, तो Aspose.Words `FileNotFoundException` थ्रो करता है। इस समस्या से बचने के लिए रिलेटिव पाथ उपयोग करें या इमेज को रिसोर्सेज से लोड करें।

## Step 5: **Save the document with the grouped shapes**

अंत में, डॉक्यूमेंट को डिस्क पर लिखें। परिणामी फ़ाइल में आयत और इमेज दोनों ग्रुपेड होंगे।

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Expected output

- निर्दिष्ट डायरेक्टरी में `GroupShape.docx` नाम की फ़ाइल बनती है।
- Microsoft Word में फ़ाइल खोलने पर एक खाली पेज पर नीला आयत और चुनी हुई इमेज दिखती है, दोनों एक ही ऑब्जेक्ट के रूप में चयनित होते हैं (आप उन्हें साथ में मूव या रिसाइज़ कर सकते हैं)।

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*ऊपर का स्क्रीनशॉट नए बनाए गए वर्ड डॉक्यूमेंट के भीतर अंतिम ग्रुपेड शैप्स को दर्शाता है।*

## Common variations and additional tips

| स्थिति | इसे कैसे संभालें |
|-----------|-----------------|
| **एकाधिक इमेजेज** | प्रत्येक इमेज को `builder.insertImage` से इन्सर्ट करें और प्रत्येक के लिए `group.appendChild(picture)` कॉल करें। |
| **विभिन्न शैप प्रकार** | `Shape` ऑब्जेक्ट बनाते समय `ShapeType.OVAL`, `ShapeType.LINE` आदि का उपयोग करें। |
| **ग्रुप की पोज़िशन बदलना** | सभी चाइल्ड जोड़ने के बाद `group.setLeft(x)` और `group.setTop(y)` सेट करके पूरे ग्रुप को मूव करें। |
| **PDF में एक्सपोर्ट** | ग्रुपिंग के बाद `doc.save("output.pdf")` कॉल करें; PDF ग्रुपिंग को बरकरार रखेगा। |
| **लाइसेंस लागू करना** | यदि आप इवैल्यूएशन वर्ज़न चलाते हैं, तो एक वाटरमार्क दिखाई देगा। इसे हटाने के लिए वैध लाइसेंस इंस्टॉल करें। |

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Java का उपयोग करके **ब्लैंक वर्ड डॉक्यूमेंट बनाना**, **GroupShape इन्सर्ट करना**, **शैप का आकार सेट करना**, **शैप का फ़िल कलर सेट करना**, और **ग्रुप में चाइल्ड जोड़ना** कैसे किया जाता है। यह पैटर्न आपको जटिल, प्रोग्रामेटिक लेआउट्स बनाने की अनुमति देता है जिन्हें बाद में वर्ड में एडिट किया जा सकता है या अन्य फ़ॉर्मेट्स में एक्सपोर्ट किया जा सकता है।

अगले चरण में, **वर्ड में शैप्स को ग्रुप करना** के साथ टेक्स्ट बॉक्सेज़, शैप्स में हाइपरलिंक जोड़ना, या मल्टी‑पेज रिपोर्ट्स को ऑटोमेटिकली जेनरेट करना एक्सप्लोर करें। वही सिद्धांत लागू होते हैं—सिर्फ अतिरिक्त शैप्स बनाएं, उनकी प्रॉपर्टीज़ कॉन्फ़िगर करें, और उन्हें उसी ग्रुप में अपेंड करें।

कोडिंग का आनंद लें!

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [जावा के साथ वर्ड में आयताकार शैप बनाना – पूर्ण गाइड](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [जावा में वर्ड डॉक्यूमेंट बनाना – शैडो इफ़ेक्ट के साथ आयताकार शैप जोड़ना](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET का उपयोग करके वर्ड डॉक्यूमेंट में ग्रुप शैप बनाना](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}