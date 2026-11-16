---
category: general
date: 2026-11-15
description: Aspose.Words for Java के साथ Word दस्तावेज़ में पाई चार्ट कैसे जोड़ें,
  सीखें। इसमें डोनट रूपांतरण, विस्फोटित स्लाइस, और पूरा कोड नमूना शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: hi
lastmod: 2026-11-15
og_description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में पाई चार्ट जोड़ें।
  यह ट्यूटोरियल दिखाता है कि कैसे एक स्लाइस को एक्सप्लोड किया जाए और चार्ट को डोनट
  में बदला जाए।
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: जावा के साथ वर्ड दस्तावेज़ में पाई चार्ट जोड़ें – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: जावा का उपयोग करके वर्ड दस्तावेज़ में पाई चार्ट कैसे जोड़ें
url: /hi/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में पाई चार्ट जोड़ें – पूर्ण Java गाइड

यदि आपको प्रोग्रामेटिक रूप से **Word दस्तावेज़ में पाई चार्ट जोड़ना** है, तो यह ट्यूटोरियल Aspose.Words for Java के साथ इसे कैसे करना है, दिखाता है। आप पूरी प्रक्रिया देखेंगे: DOCX लोड करना, पाई चार्ट बनाना, पहले स्लाइस को एक्सप्लोड करना, और होल साइज सेट करके चार्ट को डोनट में बदलना।

गाइड में सामान्य वैरिएशन भी कवर किए गए हैं—जैसे कई सीरीज़ जोड़ना, रंग कस्टमाइज़ करना, और उन दस्तावेज़ों को संभालना जिनमें पहले से चार्ट मौजूद हैं—ताकि आप कोड को वास्तविक प्रोजेक्ट्स जैसे ऑटोमेटेड रिपोर्टिंग या डायनेमिक प्रेजेंटेशन में अनुकूलित कर सकें।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Java 17 या बाद का संस्करण (कोड JDK 11+ के साथ भी कम्पाइल होता है)
* Maven 3.6+ या Gradle, डिपेंडेंसी मैनेजमेंट के लिए
* Aspose.Words for Java लाइसेंस (टेस्टिंग के लिए फ्री ट्रायल चलती है)
* Java सिंटैक्स और Maven प्रोजेक्ट स्ट्रक्चर की बुनियादी समझ

## चरण 1: Maven प्रोजेक्ट सेट अप करें और Aspose.Words इम्पोर्ट करें

एक नया Maven प्रोजेक्ट बनाएं (या मौजूदा में जोड़ें) और Aspose.Words डिपेंडेंसी शामिल करें:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **प्रो टिप:** यदि आप Gradle उपयोग कर रहे हैं, तो समकक्ष एंट्री है `implementation 'com.aspose:aspose-words:24.9'`।

यह डिपेंडेंसी `Document`, `Chart`, और `ChartType` क्लासेज़ को लाती है, जिनकी आपको चार्ट को मैनीपुलेट करने के लिए आवश्यकता होगी।

## चरण 2: लक्ष्य दस्तावेज़ लोड करें

आप मौजूदा `.docx` फ़ाइल से शुरू कर सकते हैं या नया खाली दस्तावेज़ बना सकते हैं। नीचे दिया गया उदाहरण `src/main/resources` फ़ोल्डर में स्थित `input.docx` टेम्पलेट को लोड करता है।

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

यदि फ़ाइल मौजूद नहीं है, तो `new Document()` को बिना फ़ाइल नाम के कॉल करने पर Aspose.Words स्वचालित रूप से एक नया खाली दस्तावेज़ बना देगा।

## चरण 3: पाई चार्ट बनाएं और दस्तावेज़ में डालें

Aspose.Words एक चार्ट को शैप के रूप में मानता है जिसे पैराग्राफ जहाँ भी आ सकता है, वहाँ रखा जा सकता है। निम्न कोड एक **पाई चार्ट** बनाता है, एक डेटा सीरीज़ जोड़ता है, और पहले पैराग्राफ के बाद चार्ट को इन्सर्ट करता है।

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**यह चरण क्यों महत्वपूर्ण है:**  
* `ChartType.PIE` Aspose.Words को पारंपरिक पाई चार्ट रेंडर करने के लिए बताता है।  
* श्रेणी लेबल और संख्यात्मक मानों दोनों के साथ सीरीज़ जोड़ने से स्लाइस स्वचालित रूप से भर जाते हैं।  
* `Paragraph` के चाइल्ड के रूप में चार्ट डालने से दस्तावेज़ का फ़्लो बरकरार रहता है।

## चरण 4: पहले स्लाइस को एक्सप्लोड करके हाइलाइट करें

एक *एक्सप्लोडेड स्लाइस* विशेष डेटा पॉइंट पर ध्यान आकर्षित करता है। API `ChartSeries` ऑब्जेक्ट पर `setExplode(boolean)` मेथड प्रदान करती है। पहले सीरीज़ (इंडेक्स 0) पर इसे सेट करने से पहला स्लाइस बाहर निकलेगा।

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **सामान्य प्रश्न:** *अगर मेरे पास कई सीरीज़ हों तो?*  
> आप किसी विशिष्ट सीरीज़ को उसके इंडेक्स से टार्गेट कर सकते हैं, उदाहरण के लिए `pieChart.getSeries().get(1).setExplode(true)` दूसरे सीरीज़ के लिए।

## चरण 5: होल साइज सेट करके पाई चार्ट को डोनट में बदलें

डोनट चार्ट मूल रूप से एक पाई चार्ट है जिसमें केंद्र में खाली जगह होती है। Aspose.Words आपको चार्ट के रेडियस के प्रतिशत के रूप में होल साइज परिभाषित करने की अनुमति देता है।

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize` मेथड **0** (सामान्य पाई) से **100** (पूरी तरह खाली) तक के मान लेता है। **30‑40** के आसपास का मान एक दृश्य रूप से संतुलित डोनट देता है।

## चरण 6: सहेजें और परिणाम सत्यापित करें

सभी संशोधनों के बाद, दस्तावेज़ को सहेजें। नीचे की लाइन फ़ाइल को `output` फ़ोल्डर में लिखती है।

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### अपेक्षित आउटपुट

`final-pie-doughnut.docx` को Microsoft Word में खोलें:

* पहला पैराग्राफ जहाँ था, वहाँ एक डोनट चार्ट दिखाई देगा।  
* “Apples” स्लाइस एक्सप्लोडेड (बाकी से थोड़ा अलग) होगा।  
* चार्ट में चार स्लाइस दिखेंगे: *Apples*, *Bananas*, *Cherries*, *Dates* तथा आपके द्वारा प्रदान किए गए प्रतिशत।

यदि आप PDF आउटपुट चाहते हैं, तो `SaveFormat` को `SaveFormat.PDF` में बदलें।

## किनारे के मामलों और वैरिएशन्स को संभालना

### कई सीरीज़ जोड़ना

यदि आपको कई सीरीज़ चाहिए (जैसे स्टैक्ड डोनट), तो उन्हें क्रमिक रूप से जोड़ें:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### कस्टम रंग

आप प्रत्येक स्लाइस को `ChartDataPoint.setFillFormat().setSolidFillColor()` के माध्यम से रंग दे सकते हैं:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### मौजूदा चार्ट के साथ काम करना

यदि दस्तावेज़ में पहले से एक चार्ट मौजूद है और आप केवल उसे संशोधित करना चाहते हैं, तो चार्ट शैप को लोकेट करें:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### लाइसेंस हैंडलिंग

Aspose.Words उत्पादन उपयोग के लिए लाइसेंस की आवश्यकता रखता है। अपना `Aspose.Words.lic` फ़ाइल क्लासपाथ में रखें और एप्लिकेशन स्टार्ट पर लोड करें:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

लाइसेंस सेट न करने पर जेनरेटेड दस्तावेज़ पर वॉटरमार्क जुड़ जाएगा।

## पूर्ण, चलाने योग्य उदाहरण

नीचे वह पूरा Java क्लास है जिसमें हमने चर्चा किए सभी चरण शामिल हैं। इसे `src/main/java/com/example/AddPieChart.java` में कॉपी करें और `mvn compile exec:java` चलाएँ।

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

प्रोग्राम चलाने से पहले बताए गए डोनट चार्ट का निर्माण होगा। अपने डेटा के अनुसार `categories`, `values`, या `holeSize` को समायोजित करें।

## निष्कर्ष

आप अब जानते हैं कि **Java और Aspose.Words** का उपयोग करके Word दस्तावेज़ में पाई चार्ट कैसे जोड़ें। ट्यूटोरियल ने दस्तावेज़ लोड करना, पाई चार्ट बनाना, स्लाइस एक्सप्लोड करना, चार्ट को डोनट में बदलना, और कई सीरीज़, कस्टम रंग, तथा मौजूदा चार्ट जैसी सामान्य वैरिएशन को संभालना कवर किया। इस आधार के साथ आप ऑटोमेटेड रिपोर्टिंग टूल्स बना सकते हैं, डायनेमिक प्रेजेंटेशन जेनरेट कर सकते हैं, या सीधे Word फ़ाइलों में रिच विज़ुअलाइज़ेशन एम्बेड कर सकते हैं।

### आगे क्या एक्सप्लोर करें

* **add bar chart to Word document** – समान चरण लेकिन `ChartType.BAR` उपयोग करें।  
* **customize chart legends and titles** – `pieChart.getTitle().setText("...")` और `pieChart.getLegend().setPosition(LegendPosition.RIGHT)` का उपयोग करें।  
* **export the Word document as PDF** – वितरण‑तैयार फ़ाइलों के लिए `SaveFormat` को `PDF` में बदलें।  
* **populate chart data from a database** – स्थैतिक एरे को JDBC क्वेरी परिणामों से बदलें।

विभिन्न चार्ट प्रकार, डेटा स्रोत, और स्टाइलिंग विकल्पों के साथ प्रयोग करने में संकोच न करें। हैप्पी कोडिंग!

## आप आगे क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}