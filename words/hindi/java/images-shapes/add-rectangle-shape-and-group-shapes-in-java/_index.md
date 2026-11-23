---
category: general
date: 2026-11-22
description: Java का उपयोग करके Word दस्तावेज़ में आयताकार आकार जोड़ें, आकार का आकार
  निर्धारित करें, कई आकारों को समूहित करें, और समूह में आकार को कुशलतापूर्वक जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: hi
lastmod: 2026-11-22
og_description: जावा का उपयोग करके वर्ड दस्तावेज़ में आयताकार आकार जोड़ें, फिर आकार
  का आकार सेट करें, कई आकारों को समूहित करें, और एक ही कार्यप्रवाह में आकार को समूह
  में जोड़ें।
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: जावा में आयताकार आकार जोड़ें और आकारों को समूहित करें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: जावा में आयताकार आकार जोड़ें और आकारों को समूहित करें
url: /hi/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में आयत आकार जोड़ें और आकारों को समूहित करें

यदि आपको Java के साथ Word दस्तावेज़ में **आयत आकार** जोड़ना है, तो यह गाइड आपको सटीक चरणों के माध्यम से ले जाता है। आप यह भी सीखेंगे कि **आकार का आकार सेट करें**, **कई आकारों को समूहित करें**, और **आकार को समूह में जोड़ें** बिना IDE छोड़े।

DOCX फ़ाइल के भीतर वेक्टर ग्राफ़िक्स के साथ काम करना अक्सर अलग‑अलग API को संभालने जैसा लगता है। इस ट्यूटोरियल के अंत तक आपके पास एक एकल, स्व-निहित प्रोग्राम होगा जो आयत, दीर्घवृत्त, और आपके आवश्यक किसी भी अतिरिक्त आकार को बनाता है, फिर उन्हें समूहित करता है ताकि वे एक ही वस्तु के रूप में चलें। Aspose.Words for Java के अलावा कोई बाहरी टूल आवश्यक नहीं है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

* Java 17 या उसके बाद का संस्करण स्थापित हो।
* Maven 3.8+ (या Gradle) ताकि निर्भरताओं का प्रबंधन किया जा सके।
* एक वैध Aspose.Words for Java लाइसेंस (परीक्षण के लिए एवाल्यूएशन काम करता है)।
* IntelliJ IDEA या VS Code जैसे IDE, हालांकि कोई भी टेक्स्ट एडिटर चल जाएगा।

इन आवश्यकताओं से कोड किसी भी आधुनिक विकास वातावरण में संकलित और चलाया जा सकता है।

## Step 1: Set up the Maven project

एक नया Maven प्रोजेक्ट बनाएं या मौजूदा `pom.xml` में Aspose.Words निर्भरता जोड़ें:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

यह निर्भरता दस्तावेज़ संचालन के लिए आवश्यक सभी क्लासेज़ को लाती है, जिसमें `Document`, `DocumentBuilder`, `Shape`, और `GroupShape` शामिल हैं। Maven `mvn compile` चलाने पर JAR फ़ाइलें स्वचालित रूप से डाउनलोड कर लेगा।

## Step 2: Load the document and create a DocumentBuilder

`DocumentBuilder` सामग्री सम्मिलित करने के लिए फ़्लुएंट API प्रदान करता है। मौजूदा DOCX लोड करें या एक खाली दस्तावेज़ से शुरू करें:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर को जल्दी बनाना आपको दस्तावेज़ की शुरुआत में एक कर्सर देता है, जो आकार सम्मिलित करने के लिए तैयार रहता है।

## Add rectangle shape to a Word document

### Step 3: Insert the rectangle shape

आयत वह पहला दृश्य तत्व है जिसे हम दस्तावेज़ में रखना चाहते हैं। `Shape` कंस्ट्रक्टर को `ShapeType.RECTANGLE` के साथ उपयोग करके आप एक पूरी तरह से संपादन योग्य वस्तु प्राप्त करते हैं।

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

इस बिंदु पर आयत जोड़ने से लेआउट पर कोई प्रभाव नहीं पड़ता जब तक उसका आकार निर्धारित नहीं किया जाता और उसे किसी कंटेनर में नहीं जोड़ा जाता।

### Set shape size and dimensions

#### Step 4: Define width and height

आकार के आयाम निर्धारित करने से यह पृष्ठ पर कैसे दिखेगा, तय होता है। चौड़ाई और ऊँचाई मान पॉइंट्स में मापे जाते हैं (1 pt = 1/72 in)।

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

आप इन संख्याओं को अपनी डिज़ाइन आवश्यकताओं के अनुसार समायोजित कर सकते हैं। वही मेथड किसी भी `Shape` इंस्टेंस पर लागू होते हैं, इसलिए आप उन्हें वृत्त, तीर, या कस्टम ड्रॉइंग के लिए भी पुनः उपयोग कर सकते हैं।

#### Step 5: Insert the rectangle into the document

अब जब आयत का आकार निर्धारित हो गया है, इसे पृष्ठ पर रखें। `DocumentBuilder` की `insertShape` मेथड आकार को वर्तमान कर्सर स्थिति पर जोड़ती है।

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

इस चरण पर आयत पृष्ठ पर अकेले दिखाई देती है। अगले चरण दिखाते हैं कि इसे अन्य आकारों के साथ कैसे मिलाया जाए।

## Group multiple shapes together

आकारों को समूहित करने से आप उन्हें एकल इकाई के रूप में स्थानांतरित, घुमा या आकार बदल सकते हैं। यह जटिल आरेख बनाने में विशेष रूप से उपयोगी है।

### Step 6: Create a group shape container

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape` कॉल दस्तावेज़ में एक खाली कंटेनर जोड़ती है। इस कंटेनर में जोड़े गए सभी आकार समूह का हिस्सा बन जाते हैं।

### Append shape to group

#### Step 7: Add the rectangle to the group

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

ऐपेंड करने से आयत दस्तावेज़ बॉडी से समूह के आंतरिक संग्रह में चली जाती है। अब आयत समूह के ट्रांसफ़ॉर्मेशन का सम्मान करती है।

#### Step 8: Add an ellipse for demonstration

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

दीर्घवृत्त आयत के समान कोऑर्डिनेट स्पेस साझा करता है, इसलिए आप आवश्यकता पड़ने पर `setLeft` और `setTop` प्रॉपर्टी को समायोजित करके उन्हें दृश्य रूप से संरेखित कर सकते हैं।

### Step 9: Save the document

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

प्रोग्राम चलाने पर `output.docx` उत्पन्न होगा। फ़ाइल को Microsoft Word या LibreOffice में खोलें; आपको एक आयत और एक दीर्घवृत्त एक साथ समूहित दिखेंगे। किसी भी आकार का चयन करने से पूरी समूह हाइलाइट हो जाएगी, जिससे यह पुष्टि होती है कि **append shape to group** सफल रहा।

![Add rectangle shape example in Java](image.png){alt="Java में आयत आकार का उदाहरण"}

*स्क्रीनशॉट में आयत और दीर्घवृत्त एक ही समूह के भीतर दिखाए गए हैं, जो संयुक्त रूप से हेरफेर के लिए तैयार हैं।*

## Why this approach matters

* **Single source of truth** – सभी आकार गुण समूह बनाने से पहले सेट किए जाते हैं, जिससे लेआउट गड़बड़ी नहीं होती।
* **Reusability** – वही `setWidth`/`setHeight` मेथड किसी भी आकार पर काम करते हैं, इसलिए आप उदाहरण को तीर, सितारे या कस्टम SVG तक विस्तारित कर सकते हैं।
* **Performance** – समूहित करने से Word रेंडरर को संभालने वाले ड्रॉइंग ऑब्जेक्ट की संख्या कम हो जाती है, जिससे बड़े दस्तावेज़ों के खुलने की गति बेहतर होती है।
* **Maintainability** – आकार निर्माण और समूहित लॉजिक को एक साथ रखकर भविष्य के डेवलपर्स बिना असंबंधित कोड खोजे आयाम बदल या नए आकार जोड़ सकते हैं।

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different units** | `PointsToPixels` रूपांतरण का उपयोग करें या इनलाइन प्लेसमेंट के लिए `Shape.setWrapType(WrapType.INLINE)` सेट करें। |
| **Rotating the group** | `groupShape.setRotation(45);` कॉल करके सभी चाइल्ड आकारों को 45° घुमाएँ। |
| **Adding text to a shape** | आकार का आकार सेट करने के बाद `Shape.setText("Label");` उपयोग करें। |
| **Dynamic sizing** | `doc.getFirstSection().getPageSetup().getPageWidth()` के माध्यम से पृष्ठ आयाम प्राप्त करें और आकारों को अनुपातिक रूप से गणना करें। |

इन विविधताओं से यह स्पष्ट होता है कि मूल पैटर्न—**add rectangle shape**, **set shape size**, **group multiple shapes**, **append shape to group**—कई वास्तविक‑दुनिया की आवश्यकताओं के साथ कैसे अनुकूलित होता है।

## Conclusion

अब आप जानते हैं कि Java का उपयोग करके Word दस्तावेज़ में **आयत आकार** कैसे जोड़ें, **आकार का आकार सेट करें**, **कई आकारों को समूहित करें**, और **आकार को समूह में जोड़ें** एक साफ़, रखरखाव योग्य तरीके से। पूरा उदाहरण एक ही रन करने योग्य क्लास में संकलित होता है, और परिणामी DOCX फ़ाइल अपेक्षित आउटपुट दर्शाती है।

अब आप आगे कर सकते हैं:

* प्रत्येक आकार में टेक्स्ट लेबल या हाइपरलिंक जोड़ना।
* पदानुक्रमित आरेख बनाने के लिए समूहों को नेस्ट करना।
* आकार समूहों को संरक्षित रखते हुए दस्तावेज़ को PDF में निर्यात करना।

विभिन्न आयाम, रंग और अतिरिक्त आकार प्रकारों के साथ प्रयोग करने में संकोच न करें। आकार हेरफेर में महारत हासिल करने से स्वचालित रिपोर्ट जनरेशन, गतिशील आरेख, और समृद्ध दस्तावेज़ अनुभवों के द्वार खुलते हैं—सभी सीधे Java कोड से।

## What Should You Learn Next?

इन ट्यूटोरियल्स में उन विषयों को कवर किया गया है जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में निपुण हो सकें और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Java में आयत आकार डालें – समूह बनाएं और स्थिति निर्धारित करें](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Aspose.Words का उपयोग करके Word दस्तावेज़ में समूह आकार के भीतर दीर्घवृत्त और आयत आकार कैसे बनाएं और डालें](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Java का उपयोग करके Word दस्तावेज़ में आयत आकार बनाएं](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}