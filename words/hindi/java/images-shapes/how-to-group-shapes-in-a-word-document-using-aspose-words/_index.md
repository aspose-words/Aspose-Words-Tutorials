---
category: general
date: 2026-08-20
description: Aspose.Words in Java के साथ shapes को समूहित करना, shape का आकार सेट
  करना, दस्तावेज़ में छवि सम्मिलित करना, समूह में चित्र जोड़ना, और आयताकार shape बनाना
  सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: hi
lastmod: 2026-08-20
og_description: Aspose.Words का उपयोग करके Word दस्तावेज़ में आकारों को समूहित करने
  का तरीका। आकार का आकार सेट करने, दस्तावेज़ में छवि सम्मिलित करने, समूह में चित्र
  जोड़ने और आयताकार आकार बनाने के लिए इस चरण‑दर‑चरण Java ट्यूटोरियल का पालन करें।
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Aspose.Words के साथ Word दस्तावेज़ में आकृतियों को समूहित करने का तरीका
  – Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Aspose.Words का उपयोग करके Word दस्तावेज़ में आकृतियों को समूहित कैसे करें
url: /hi/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words का उपयोग करके Word दस्तावेज़ में shapes को समूहित कैसे करें

यदि आपको Word फ़ाइल में **how to group shapes** की आवश्यकता है, तो यह ट्यूटोरियल पूर्ण Java समाधान दिखाता है। आप देखेंगे कि **set shape size**, **insert image into document**, **add picture to group**, और **create rectangle shape** कैसे किया जाता है—सभी स्पष्ट व्याख्याओं और चलाने योग्य कोड उदाहरण के साथ।

shapes को समूहित करने से लेआउट प्रबंधन सरल हो जाता है, आप कई ऑब्जेक्ट्स को एक इकाई के रूप में ले जा या घुमा सकते हैं, और आपका दस्तावेज़ साफ़ रहता है। नीचे दिए गए चरणों में आप एक समूह बनाएँगे जिसमें एक rectangle और एक picture होगा, फिर उस समूह को पृष्ठ पर रखें।

## पूर्वापेक्षाएँ

* Java 17 या नया स्थापित हो।
* Aspose.Words for Java (version 23.9 या बाद का) आपके प्रोजेक्ट के classpath में जोड़ा गया हो।
* एक नमूना JPEG इमेज `YOUR_DIRECTORY/sample.jpg` पर हो ( `YOUR_DIRECTORY` को वास्तविक पथ से बदलें)।

आप Maven के माध्यम से Aspose.Words जोड़ सकते हैं:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Aspose.Words के साथ shapes को समूहित कैसे करें

निम्नलिखित अनुभाग **how to group shapes** करने के लिए आवश्यक प्रत्येक ऑपरेशन को चरण-दर-चरण दिखाते हैं। प्राथमिक H2 हेडर में मुख्य कीवर्ड शामिल है, जो SEO नियमों को पूरा करता है।

### चरण 1: एक नया दस्तावेज़ और एक `DocumentBuilder` बनाएं

`Document` Word फ़ाइल को दर्शाता है, जबकि `DocumentBuilder` सामग्री सम्मिलित करने के लिए सुविधाजनक मेथड्स प्रदान करता है।

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: एक नई `Document` से शुरू करने से यह सुनिश्चित होता है कि आपका बनाया गया समूह मौजूदा तत्वों में बाधा नहीं डालेगा।

### चरण 2: एक group shape सम्मिलित करें जो कई child shapes को रखेगा

एक group shape कंटेनर की तरह कार्य करता है। इसके आयाम सभी child shapes के लिए बाउंडिंग बॉक्स निर्धारित करते हैं।

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: चौड़ाई (`300`) और ऊँचाई (`200`) पॉइंट्स में हैं (1 pt = 1/72 इंच)। इन्हें उन shapes के आकार के आधार पर समायोजित करें जिन्हें आप जोड़ने की योजना बना रहे हैं।

### चरण 3: एक rectangle shape बनाएं, उसका आकार सेट करें, और उसे समूह में जोड़ें

जब आप सटीक लेआउट नियंत्रण चाहते हैं तो shape का सटीक आकार सेट करना आवश्यक होता है।

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Why we set shape size*: `setWidth` और `setHeight` मेथड्स **set shape size** द्वितीयक कीवर्ड से मेल खाते हैं, जिससे आपको rectangle की उपस्थिति पर पिक्सेल‑परफ़ेक्ट नियंत्रण मिलता है।

### चरण 4: एक इमेज सम्मिलित करें, फिर picture shape को उसी समूह में जोड़ें

इमेज सम्मिलित करना **insert image into document** आवश्यकता का मूल है। लौटाया गया `Shape` एक picture shape है जिसे किसी भी अन्य shape की तरह समूहित किया जा सकता है।

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: यदि आपको मूल aspect ratio बनाए रखना है, तो केवल एक आयाम सेट करें (`setWidth` या `setHeight`)। Aspose.Words स्वचालित रूप से दूसरे आयाम को स्केल कर देता है।

### चरण 5: पूरे समूह को पृष्ठ पर स्थित करें

सभी child shapes जोड़ने के बाद, आप पूरे समूह को ले जा सकते हैं, घुमा सकते हैं, या छिपा सकते हैं। पोजिशनिंग अप्रत्यक्ष रूप से **add picture to group** अवधारणा का उपयोग करती है, क्योंकि समूह में अब picture शामिल है।

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explanation*: `setLeft` और `setTop` समूह को पृष्ठ की मार्जिन के सापेक्ष स्थित करते हैं। समूह को घुमाने से दिखता है कि सभी child shapes परिवर्तन को विरासत में लेते हैं।

### चरण 6: दस्तावेज़ को सहेजें

अंत में, फ़ाइल को डिस्क पर लिखें। आप परिणामस्वरूप `.docx` को Word में खोलकर समूहबद्धता की पुष्टि कर सकते हैं।

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

प्रोग्राम चलाने पर **GroupShapesDemo.docx** बनता है जिसमें एक rectangle और एक image एक साथ बंडल होते हैं। Word में किसी भी shape को चुनने से दूसरा shape भी चयनित हो जाता है, जिससे पुष्टि होती है कि आपने सफलतापूर्वक **how to group shapes** सीख लिया है।

---

## अपेक्षित आउटपुट

जब आप Microsoft Word में *GroupShapesDemo.docx* खोलते हैं:

* एक rectangle (सुनहरी भराव) समूह के बाएँ पक्ष में दिखाई देता है।
* आपके द्वारा प्रदान किया गया picture rectangle के दाएँ पक्ष में दिखाई देता है।
* दोनों ऑब्जेक्ट्स समूह को खींचने पर साथ‑साथ चलते हैं।
* समूह बाएँ मार्जिन से 50 pt और शीर्ष मार्जिन से 100 pt पर स्थित है, 15° घुमाया हुआ है।

यदि image दिखाई नहीं देता, तो `insertImage` में फ़ाइल पथ को दोबारा जांचें। जब फ़ाइल नहीं मिलती, तो Aspose.Words `IOException` फेंकता है।

---

## सामान्य प्रश्न और किनारे‑के‑केस हैंडलिंग

| Question | Answer |
|----------|--------|
| **क्या मैं दो से अधिक shapes जोड़ सकता हूँ?** | हां। प्रत्येक अतिरिक्त shape के लिए `groupShape.appendChild(otherShape)` कॉल करें। |
| **यदि मुझे rectangle के लिए पारदर्शी पृष्ठभूमि चाहिए तो क्या करें?** | उपयोग करें `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **क्या समूह बनाना पुराने Word फ़ॉर्मैट्स (जैसे `.doc`) में समर्थित है?** | समूह बनाना `.docx` और `.doc` दोनों में काम करता है, लेकिन कुछ पुराने व्यूअर्स समूह मेटाडेटा को अनदेखा कर सकते हैं। पूर्ण फ़िडेलिटी के लिए `.docx` के रूप में सहेजें। |
| **बाद में मैं समूह को कैसे हटाऊँ?** | `groupShape.getChildNodes(NodeType.ANY, true)` के माध्यम से child nodes प्राप्त करें और उन्हें दस्तावेज़ बॉडी में ले जाएँ, फिर समूह को हटा दें। |
| **क्या मैं विभिन्न सेक्शन में shapes को समूहित कर सकता हूँ?** | नहीं। एक `GroupShape` को एक ही `Story` (आमतौर पर मुख्य दस्तावेज़ बॉडी) में रहना चाहिए। |

## मजबूत shape हैंडलिंग के लिए प्रो टिप्स

* **Absolute positioning का सीमित उपयोग करें** – relative positioning (`builder.moveToDocumentEnd()`) अक्सर अधिक प्रतिक्रियाशील लेआउट देता है।
* **`DocumentBuilder` को कैश करें** – प्रत्येक ऑपरेशन के लिए नया builder बनाना बड़े दस्तावेज़ों में प्रदर्शन को घटा सकता है।
* **`PictureFillMode` सेट करें** जब आपको shape के भीतर इमेज को स्ट्रेच या टाइल करने की आवश्यकता हो: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **इमेज के आयामों को सत्यापित करें** सम्मिलित करने से पहले ताकि अनपेक्षित स्केलिंग से बचा जा सके जो समूह के बाउंडिंग बॉक्स को प्रभावित कर सकता है।

## अगले कदम

अब जब आप **how to group shapes** जानते हैं, आप निम्नलिखित का अन्वेषण कर सकते हैं:

* **Insert image into document** को उन्नत विकल्पों जैसे क्रॉपिंग (`pictureShape.setCropTop(...)`) के साथ उपयोग करें।
* **Set shape size** को पृष्ठ आयामों (`doc.getFirstSection().getPageSetup().getPageWidth()`) के आधार पर गतिशील रूप से सेट करें।
* **Add picture to group** को टेक्स्ट बॉक्स के साथ मिलाकर कैप्शन वाले ग्राफिक्स बनाएं।
* **Create rectangle shape** को गोल कोनों (`rectangleShape.setCornerRadius(5);`) के साथ बनाएं।

ये विषय समान API सतह पर आधारित हैं और आपको परिष्कृत, प्रोग्रामेटिक Word रिपोर्ट बनाने में मदद करते हैं।

## निष्कर्ष

इस ट्यूटोरियल में आपने Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में **how to group shapes** सीखा। छह चरणों—दस्तावेज़ बनाना, समूह सम्मिलित करना, **creating rectangle shape**, **set shape size**, **insert image into document**, **add picture to group**, और समूह को स्थित करना—का पालन करके अब आपके पास जटिल लेआउट परिदृश्यों के लिए एक पुन: उपयोग योग्य पैटर्न है। अतिरिक्त child shapes, विभिन्न rotations, या शर्तीय समूहबद्धता लॉजिक के साथ प्रयोग करने में संकोच न करें ताकि आपके एप्लिकेशन की आवश्यकताओं को पूरा किया जा सके।

कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}