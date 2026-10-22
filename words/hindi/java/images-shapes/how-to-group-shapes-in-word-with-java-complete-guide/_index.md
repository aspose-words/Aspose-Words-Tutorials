---
category: general
date: 2026-10-16
description: जावा का उपयोग करके वर्ड में आकारों को समूहित करना सीखें। यह ट्यूटोरियल
  दिखाता है कि कैसे आयताकार आकार जोड़ें, आकार का आकार और आयाम सेट करें, और दस्तावेज़
  को सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: hi
lastmod: 2026-10-16
og_description: जावा का उपयोग करके वर्ड में आकारों को समूहित करें। आयताकार आकार जोड़ें,
  आकार का आकार और आयाम सेट करें, और प्रोग्रामेटिक रूप से पेशेवर दस्तावेज़ बनाएं।
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Java के साथ Word में आकृतियों को समूहित करें – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: जावा के साथ वर्ड में आकृतियों को समूहित कैसे करें – पूर्ण मार्गदर्शिका
url: /hi/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word with Java – complete guide

यदि आपको **Word में आकृतियों को समूहित** करना प्रोग्रामेटिकली चाहिए, तो यह ट्यूटोरियल तैयार‑चलाने योग्य समाधान प्रदान करता है। आप देखेंगे कि **आयताकार आकृति कैसे जोड़ें**, उसका आकार समायोजित करें, आकृति के आयाम सेट करें, और अंत में एक DOCX फ़ाइल सहेजें जिसमें एक समूहित आयत और एक दीर्घवृत्त हो।

Word में आकृतियों को समूहित करना जटिल आरेख बनाने, पुन: उपयोग योग्य ग्राफ़िक घटकों को तैयार करने, या दस्तावेज़ को बाद में संपादित करते समय संबंधित वस्तुओं को साथ रखने के लिए उपयोगी है। कोड Aspose.Words for Java लाइब्रेरी का उपयोग करता है, जो किसी भी नवीनतम JDK के साथ काम करता है और Microsoft Word की स्थापना की आवश्यकता नहीं रखता।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

| Requirement | Reason |
|-------------|--------|
| Java 17 (या बाद का संस्करण) | लाइब्रेरी आधुनिक Java रनटाइम को लक्षित करती है। |
| Aspose.Words for Java (नवीनतम संस्करण) | उदाहरण में उपयोग किए गए `Document`, `DocumentBuilder`, `GroupShape`, और `Shape` क्लास प्रदान करता है। |
| कोई IDE या बिल्ड टूल (Maven/Gradle) | सैंपल को संकलित और चलाने के लिए। |
| Java सिंटैक्स का बुनियादी ज्ञान | कोड प्रवाह को समझने के लिए आवश्यक है। |

अपने प्रोजेक्ट में Aspose.Words निर्भरता जोड़ें। Maven के लिए:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

या Gradle के लिए:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Overview of the solution

ट्यूटोरियल एक स्पष्ट **समस्या → समाधान → व्याख्या** पैटर्न का अनुसरण करता है:

1. **एक नया Word दस्तावेज़ बनाएं** और एक `DocumentBuilder` प्राप्त करें।  
2. **एक `GroupShape` कंटेनर डालें** जो कई आकृतियों को रखेगा।  
3. **एक आयत जोड़ें**, उसकी चौड़ाई/ऊँचाई सेट करें (**set shape size** चरण), और उसे समूह से जोड़ें।  
4. **एक दीर्घवृत्त जोड़ें**, उसे उसी समूह के भीतर स्थित करें, और उसके आयाम भी सेट करें।  
5. **दस्तावेज़ को सहेजें**।

प्रत्येक चरण में कोड के **क्यों** को समझाया गया है, ताकि आप जान सकें API क्या करता है और इसे अन्य परिदृश्यों में कैसे अनुकूलित कर सकते हैं।

## Step 1: Create the document and a DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**यह क्यों महत्वपूर्ण है:** `Document` पूरे DOCX फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक सहायक है जो आपको लो‑लेवल नोड प्रबंधन से बचते हुए सामग्री डालने देता है। इन्हें पहले बनाकर रखने से सभी बाद के आकृति संचालन के लिए एक साफ़ कैनवास मिल जाता है।

## Step 2: Insert a GroupShape container

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape` ड्राइंग ऑब्जेक्ट्स के लिए **फ़ोल्डर** की तरह काम करता है। जब आप समूह को ले जाते, घुमाते या हटाते हैं, तो सभी चाइल्ड आकृतियाँ स्वतः साथ चलती हैं। यह **Word में समूहित आकृतियों** का मूल सिद्धांत है।

## Step 3: Add a rectangle shape – the rectangle shape code

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape` कंस्ट्रक्टर `ShapeType.RECTANGLE` प्राप्त करता है, जो Aspose.Words को आयताकार रूपरेखा बनाने के लिए बताता है।  
- **set shape size** – `setWidth` और `setHeight` **आकृति के आयाम** को पॉइंट्स में परिभाषित करते हैं (1 pt = 1/72 in)। यह दृश्य आकार को नियंत्रित करने का सबसे सामान्य तरीका है।  
- **Why we use `appendChild`** – यह आयत को `GroupShape` से जोड़ता है ताकि वह समूह के साथ ही मूव हो।

## Step 4: Add an ellipse and position it inside the group

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

दीर्घवृत्त **set shape dimensions** को केवल आयत से आगे दिखाता है। `setLeft` को कॉल करके हम समूह के भीतर क्षैतिज ऑफ़सेट नियंत्रित करते हैं, जो कई वस्तुओं को व्यवस्थित करने में उपयोगी है।

## Step 5: Save the document

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

जब आप *GroupShapeDemo.docx* को Microsoft Word में खोलेंगे, तो आपको एक आयत और एक दीर्घवृत्त एक ही समूह में लॉक हुए दिखेंगे। किसी भी आकृति का चयन करने पर पूरा समूह चयनित हो जाएगा—बिल्कुल वही जो आप **Word में समूहित आकृतियों** से अपेक्षा करते हैं।

## Full, runnable example

सभी टुकड़ों को मिलाकर, यहाँ पूर्ण स्रोत फ़ाइल है जिसे आप अपने IDE में कॉपी कर सकते हैं:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Expected output

- प्रोजेक्ट फ़ोल्डर में **GroupShapeDemo.docx** नाम की फ़ाइल बनती है।  
- Word में फ़ाइल खोलने पर दो आकृतियाँ (एक आयत और एक दीर्घवृत्त) दिखती हैं जो एक साथ समूहित हैं।  
- किसी भी आकृति को खींचने से पूरी समूह मूव होती है, जिससे पुष्टि होती है कि **Word में समूहित आकृतियों** सही ढंग से काम कर रहा है।

## Common variations and edge cases

| Scenario | What to change | Why |
|----------|----------------|-----|
| **Different shape types** (e.g., triangle) | Use `ShapeType.TRIANGLE` or any other enum value when constructing `Shape`. | Allows you to build more complex diagrams. |
| **Setting fill color** | Call `shape.getFillColor().setColor(Color.BLUE);` after creating the shape. | Improves visual appearance without affecting grouping. |
| **Rotating the group** | `groupShape.setRotationAngle(45);` | Rotates all child shapes together, useful for icons. |
| **Adding text inside a shape** | `shape.appendChild(new Paragraph(document));` then add a `Run` with text. | Makes the shape act like a label or callout. |
| **Saving to a stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Useful for web services that return the document directly. |

### Pro tip

जब आपको **set shape dimensions** को डायनामिक डेटा (जैसे बारकोड लंबाई) के आधार पर सेट करना हो, तो पहले पॉइंट्स में चौड़ाई/ऊँचाई की गणना करें:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

यह हार्ड‑कोडेड मानों से बचाता है और आपके कोड को अनुकूलनीय बनाता है।

## Conclusion

अब आप जानते हैं कि Java का उपयोग करके **Word में आकृतियों को समूहित** कैसे करें, **आयताकार आकृति कैसे जोड़ें**, और संक्षिप्त, प्रोडक्शन‑रेडी कोड के साथ **आकृति का आकार** तथा **आकृति के आयाम** कैसे सेट करें। ऊपर दिए गए चरणों का पालन करके आप पुन: उपयोग योग्य ग्राफ़िक समूह बना सकते हैं, उन्हें स्वचालित रिपोर्टों में एम्बेड कर सकते हैं, या बिना Word खोले कस्टम आरेख निर्माण टूल बना सकते हैं।

### What’s next?

- **add rectangle shape** के विभिन्न रूपों का अन्वेषण करें जैसे गोल किनारे (`ShapeType.RECTANGLE` के साथ `setCornerRadius`)।  
- **Word में समूहित आकृतियों** को तालिकाओं या चार्ट्स के साथ मिलाकर अधिक समृद्ध दस्तावेज़ बनाएं।  
- **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) के लिए Aspose.Words API देखें, जिससे आपके समूहित ग्राफ़िक्स के आसपास का टेक्स्ट कैसे व्यवहार करता है, नियंत्रित किया जा सके।

बिना हिचकिचाहट प्रयोग करें, **आयताकार आकृति कोड** को अनुकूलित करें, और अपने परिणाम साझा करें।

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}