---
category: general
date: 2026-07-16
description: Aspose.Words का उपयोग करके जावा में समूह आकार कैसे डालें – आयताकार आकार
  जोड़ें, आकार के आयाम सेट करें, और रंगीन आयत और वृत्त बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: hi
lastmod: 2026-07-16
og_description: 'Java में ग्रुप शेप कैसे डालें: आयताकार शेप जोड़ने, शेप के आयाम सेट
  करने, और Aspose.Words के साथ रंगीन आयत और वृत्त बनाने की व्यावहारिक गाइड।'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: जावा में समूह आकृति डालें – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Java में ग्रुप शैप कैसे डालें – पूर्ण गाइड
url: /hi/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में ग्रुप शेप कैसे इन्सर्ट करें – पूर्ण गाइड

क्या आपने कभी Java का उपयोग करके Word दस्तावेज़ में **ग्रुप शेप कैसे इन्सर्ट करें** के बारे में सोचा है? आप अकेले नहीं हैं। चाहे आप रिपोर्ट जेनरेटर बना रहे हों या डायनामिक फ्लायर क्रिएटर, शेप्स को ग्रुप करने से आपका लेआउट साफ़ रहता है और आपका कोड मैनेज करने योग्य बनता है।

इस ट्यूटोरियल में हम **रेक्टैंगल शेप जोड़ें**, **शेप डाइमेंशन्स सेट करें**, और **कलरड रेक्टैंगल बनाएं** तथा **कलरड सर्कल बनाएं** Aspose.Words लाइब्रेरी का उपयोग करके करेंगे। अंत तक आपके पास एक रनएबल प्रोग्राम होगा जो एक .docx फ़ाइल बनाता है जिसमें एक नीला रेक्टैंगल और एक लाल सर्कल एक ग्रुप के अंदर सुगमता से रैप किया गया है।

## आवश्यकताएँ

- Java 17 (या कोई भी नवीनतम JDK) स्थापित और कॉन्फ़िगर किया हुआ।
- निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।
- Aspose.Words for Java 23.9 या नया – आप इसे Maven Central से प्राप्त कर सकते हैं।
- Java सिंटैक्स की बुनियादी समझ – कोई विशेष ज्ञान आवश्यक नहीं।

यदि आप इनमें से कोई भी चीज़ नहीं रखते हैं, तो Oracle की साइट से JDK प्राप्त करें और अपने `pom.xml` में Aspose.Words डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

अब बुनियादी सेटअप हो गया है, चलिए काम शुरू करते हैं।

## ग्रुप शेप कैसे इन्सर्ट करें – अवलोकन

मुख्य विचार सरल है: एक `Document` बनाएं, एक `DocumentBuilder` खोलें, एक **ग्रुप शेप** इन्सर्ट करें, फिर व्यक्तिगत शेप्स (एक रेक्टैंगल और एक सर्कल) को उस ग्रुप में डालें। ग्रुप एक कंटेनर की तरह काम करता है, इसलिए बाद में इसे मूव करने से अंदर की सभी चीज़ें साथ में शिफ्ट हो जाएँगी – जटिल लेआउट्स के लिए आदर्श।

नीचे पूरा, तैयार‑चलाने‑योग्य कोड दिया गया है। इसे `InsertGroupShapeDemo` नाम की नई Java क्लास में कॉपी‑पेस्ट करने में संकोच न करें।

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** `setLeft` और `setTop` मान ग्रुप की मूल बिंदु के सापेक्ष होते हैं, पेज के नहीं। इससे बाद में पूरे ग्रुप को पुनः स्थित करना बहुत आसान हो जाता है।

### अभी क्या हुआ?

1. **Document & Builder** – हम एक खाली Word फ़ाइल और एक `DocumentBuilder` बनाते हैं जो हमें कंटेंट इन्सर्ट करने देता है।
2. **Group Shape** – `builder.insertGroupShape()` एक कंटेनर बनाता है। इसे ड्राइंग ऑब्जेक्ट्स के फ़ोल्डर की तरह सोचें।
3. **Blue Rectangle** – हम `RECTANGLE` प्रकार का `Shape` बनाते हैं, उसका आकार और स्थिति सेट करते हैं, और उसे नीले रंग से भरते हैं – यह **create colored rectangle** चरण है।
4. **Red Circle** – वही पैटर्न, लेकिन परफेक्ट सर्कल के लिए `ELLIPSE` का उपयोग करते हैं, फिर उसे लाल रंग से भरते हैं – यह **create colored circle** भाग है।
5. **Saving** – अंत में हम सब कुछ `GroupShapeDemo.docx` में सेव कर देते हैं।

प्रोग्राम चलाएँ (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) और उत्पन्न फ़ाइल खोलें। आपको बाएँ तरफ एक नीला रेक्टैंगल और दाएँ तरफ एक लाल सर्कल दिखना चाहिए, दोनों एक ही ग्रुप बॉक्स के अंदर लॉक किए हुए।

## रेक्टैंगल शेप जोड़ना

यदि आपको केवल रेक्टैंगल चाहिए और ग्रुपिंग नहीं चाहिए, तो आप `insertGroupShape()` कॉल को छोड़ सकते हैं और रेक्टैंगल को सीधे दस्तावेज़ के बॉडी में जोड़ सकते हैं। हालांकि, ग्रुपिंग आपको एक ही बार में कई शेप्स को मूव, रोटेट या डिलीट करने की लचीलापन देती है।

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

ध्यान दें कि हमने यहाँ **add rectangle shape** लॉजिक का उपयोग किया है। रेक्टैंगल पेज पर एक स्वतंत्र ऑब्जेक्ट के रूप में दिखाई देता है। अधिकांश वास्तविक‑दुनिया के परिदृश्यों में आप ग्रुप चाहते हैं, क्योंकि यह सापेक्ष पोजिशनिंग को बनाए रखता है।

## शेप डाइमेंशन्स सेट करना

जब आप `setWidth` और `setHeight` जैसे मेथड देखते हैं, तो याद रखें कि ये **पॉइंट्स** (1/72 इंच) स्वीकार करते हैं। यदि आप मिलीमीटर पसंद करते हैं, तो पहले कन्वर्ट करें:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

यह स्निपेट **set shape dimensions** को यूनिट कन्वर्ज़न के साथ दर्शाता है – उपयोगी जब आपके डिज़ाइन स्पेसिफ़िकेशन मीट्रिक यूनिट्स वाले UI मॉकअप से आते हैं।

## कलरड रेक्टैंगल बनाना

एक शेप को रंगना इतना सरल है जितना `getFill().setForeColor()` को कॉल करना। आप कोई भी `java.awt.Color` पास कर सकते हैं। ग्रेडिएंट चाहिए? शुरूआती रंग के लिए `setForeColor` और अंत के लिए `setBackColor` उपयोग करें।

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

यह एक तेज़ तरीका है **create colored rectangle** को ग्रेडिएंट फ़िल के साथ बनाने का, बजाय सॉलिड रंग के।

## कलरड सर्कल बनाना

सर्कल केवल समान चौड़ाई और ऊँचाई वाले एलिप्स होते हैं। वही रंग लॉजिक लागू होता है:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

यदि आपको ट्रांसपेरेंट फ़िल चाहिए, तो अल्फा चैनल सेट करें:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

अब आपने **create colored circle** तकनीक में महारत हासिल कर ली है।

## दस्तावेज़ को सेव करना

Aspose.Words आपको कई फ़ॉर्मैट्स में आउटपुट करने देता है: DOCX, PDF, HTML, PNG, जो भी आप चाहें। इस डेमो के लिए हम DOCX पर टिके रहते हैं क्योंकि यह वेक्टर शेप्स को पूरी तरह से संरक्षित रखता है।

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

`SaveFormat` को बदलना ही पर्याप्त है ताकि उसी ग्रुप्ड आर्टवर्क का PDF संस्करण जेनरेट किया जा सके।

## सामान्य गलतियाँ और उन्हें कैसे टालें

- **शेप को ग्रुप में जोड़ना भूल गए?** शेप पेज पर दिखेगा लेकिन ग्रुप के साथ नहीं चलेगा। हमेशा `group.appendChild(yourShape)` कॉल करें।

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दर्शाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का पता लगा सकें।

- [Word दस्तावेज़ Java बनाएं – शैडो इफ़ेक्ट के साथ रेक्टैंगल शेप जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और कंटेंट जोड़ना](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words के साथ Word में रेक्टैंगल शेप बनाना – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}