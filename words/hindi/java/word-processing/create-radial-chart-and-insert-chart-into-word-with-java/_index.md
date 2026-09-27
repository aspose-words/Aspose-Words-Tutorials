---
category: general
date: 2026-09-27
description: जावा में रेडियल चार्ट बनाएं और चार्ट को वर्ड में डालें। चार्ट का आकार
  सेट करना, डेटा सीरीज़ जोड़ना, और एक खाली वर्ड दस्तावेज़ बनाना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: hi
lastmod: 2026-09-27
og_description: जावा में रेडियल चार्ट बनाएं, फिर चार्ट को वर्ड में डालें। यह गाइड
  दिखाता है कि चार्ट का आकार कैसे सेट करें, डेटा सीरीज़ कैसे जोड़ें, और एक खाली वर्ड
  दस्तावेज़ कैसे बनाएं।
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: जावा के साथ रेडियल चार्ट बनाएं और उसे वर्ड में सम्मिलित करें
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: जावा का उपयोग करके रेडियल चार्ट बनाएं और उसे वर्ड में सम्मिलित करें
url: /hi/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के साथ Word में रेडियल चार्ट बनाएं और चार्ट सम्मिलित करें

यदि आपको Java का उपयोग करके Word फ़ाइल में **रेडियल चार्ट बनाना** है, तो यह ट्यूटोरियल आपको बिल्कुल बताता है कि कैसे करना है। आप देखेंगे कि **चार्ट को Word में सम्मिलित करना**, चार्ट के आयाम सेट करना, और शुरू से **एक खाली Word दस्तावेज़** बनाना कैसे है।

हम हर आवश्यक चरण को विस्तार से बताएंगे, दस्तावेज़ को प्रारंभ करने से लेकर डेटा सीरीज़ जोड़ने और अंतिम `.docx` को सहेजने तक। अंत तक आपके पास एक पूरी तरह कार्यात्मक Word फ़ाइल होगी जिसमें रेडियल चार्ट होगा, और आप **चार्ट का आकार कैसे सेट करें** और **डेटा सीरीज़ चार्ट जोड़ें** को भविष्य के अनुकूलन के लिए समझेंगे।

## आवश्यकताएँ

* Java 17 या बाद का (कोड किसी भी आधुनिक JDK के साथ संकलित होता है)
* Aspose.Words for Java 24.9 या नया – `setShowGraduations` मेथड केवल इस संस्करण से उपलब्ध है
* एक IDE या बिल्ड टूल (Maven/Gradle) जो Aspose.Words JAR को शामिल कर सके
* Java सिंटैक्स और Maven/Gradle डिपेंडेंसी प्रबंधन की बुनियादी परिचितता

> **Pro tip:** यदि आप Maven का उपयोग कर रहे हैं, तो अपने `pom.xml` में निम्नलिखित जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## चरण 1: एक खाली Word दस्तावेज़ बनाएं

एक खाली दस्तावेज़ वह कैनवास है जिस पर चार्ट रखा जाएगा। `Document` क्लास पूरी `.docx` फ़ाइल का प्रतिनिधित्व करती है।

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

एक खाली दस्तावेज़ बनाना सुनिश्चित करता है कि पूर्व‑मौजूद सामग्री चार्ट लेआउट में बाधा न बनें।

## चरण 2: DocumentBuilder को प्रारंभ करें

`DocumentBuilder` दस्तावेज़ में ऑब्जेक्ट, टेक्स्ट और अन्य तत्व सम्मिलित करने के लिए सुविधाजनक मेथड प्रदान करता है।

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर का बाद में **चार्ट को Word में सम्मिलित करने** के लिए उपयोग किया जाएगा।

## चरण 3: रेडियल चार्ट बनाएं

Aspose.Words कई चार्ट प्रकारों का समर्थन करता है; `ChartType.RADIAL` एक रेडियल (ध्रुवीय) चार्ट बनाता है।

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

इस चरण पर चार्ट मौजूद है लेकिन इसमें डेटा, आकार या दृश्य विकल्प नहीं हैं।

## चरण 4: चार्ट में डेटा सीरीज़ जोड़ें

डेटा सीरीज़ के बिना चार्ट खाली रहता है। `add` मेथड एक सीरीज़ नाम और मानों की एरे लेता है।

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

आप `add` को बार‑बार कॉल करके कई सीरीज़ जोड़ सकते हैं। यह **डेटा सीरीज़ चार्ट जोड़ें** की आवश्यकता को पूरा करता है।

## चरण 5: ग्रेजुएशन्स सक्षम करें (वैकल्पिक)

ग्रेजुएशन्स वह रेडियल ग्रिड लाइन्स हैं जो पठनीयता बढ़ाती हैं। ये केवल संस्करण 24.9 से उपलब्ध हैं।

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

यदि आप पुराना Aspose.Words संस्करण उपयोग करते हैं, तो यह लाइन एक अपवाद उत्पन्न करेगी—इसलिए पहले अपनी लाइब्रेरी संस्करण की जाँच करें।

## चरण 6: चार्ट के आयाम सेट करें

चार्ट के आकार को नियंत्रित करने से आप इसे पृष्ठ मार्जिन के भीतर ठीक से फिट कर सकते हैं। यह **चार्ट का आकार कैसे सेट करें** को संबोधित करता है।

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

आप अपनी लेआउट आवश्यकताओं के अनुसार चौड़ाई और ऊँचाई मानों को समायोजित कर सकते हैं। याद रखें कि 1 पॉइंट ≈ 1/72 इंच है।

## चरण 7: चार्ट को Word दस्तावेज़ में सम्मिलित करें

अब चार्ट रखने के लिए तैयार है। `DocumentBuilder` की `insertChart` मेथड सम्मिलन को संभालती है।

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

यह **चार्ट को Word में सम्मिलित करने** ऑपरेशन का मूल भाग है।

## चरण 8: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल में वह रेडियल चार्ट होगा जो आपने अभी बनाया है।

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

प्रोग्राम चलाने पर प्रोजेक्ट की कार्य निर्देशिका में `RadialChart.docx` बनता है। Microsoft Word में फ़ाइल खोलने पर तीन डेटा पॉइंट्स और दृश्यमान ग्रेजुएशन्स के साथ एक रेडियल चार्ट दिखता है।

### अपेक्षित आउटपुट

* `RadialChart.docx` नामक एक Word फ़ाइल
* फ़ाइल के भीतर, एक पृष्ठ जिसमें 400 × 300 पॉइंट आकार का रेडियल चार्ट हो
* चार्ट में **Series 1** शीर्षक वाली एक सीरीज़ दिखती है, जिसके मान **10, 20, 30** हैं
* ग्रेजुएशन्स (रेडियल ग्रिड लाइन्स) चार्ट के चारों ओर दृश्यमान हैं

## सामान्य विविधताएँ और किनारी मामलों

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **एकाधिक सीरीज़** | प्रत्येक सीरीज़ के लिए `chart.getSeries().add(...)` कॉल करें | तुलनात्मक डेटा विज़ुअलाइज़ेशन की अनुमति देता है |
| **विभिन्न चार्ट प्रकार** | `ChartType.RADIAL` को `ChartType.COLUMN` (या कोई अन्य) से बदलें | वह चार्ट प्रकार उपयोग करें जो आपके डेटा को सबसे बेहतर दर्शाता है |
| **कस्टम रंग** | `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` तक पहुँचें | दृश्य ब्रांडिंग में सुधार करता है |
| **पुराना Aspose.Words संस्करण** | `setShowGraduations` लाइन को हटाएँ या लाइब्रेरी को अपग्रेड करें | `NoSuchMethodError` को रोकता है |
| **भिन्न फ़ॉर्मेट में सहेजना** | `doc.save("RadialChart.pdf", SaveFormat.PDF)` उपयोग करें | DOCX के बजाय PDF उत्पन्न करता है |

## पूरा चलाने योग्य उदाहरण

नीचे पूर्ण, स्वतंत्र Java प्रोग्राम दिया गया है। इसे `RadialChartExample.java` नामक फ़ाइल में कॉपी करें, Aspose.Words डिपेंडेंसी जोड़ें, और चलाएँ।

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## निष्कर्ष

अब आप प्रोग्रामेटिक रूप से **रेडियल चार्ट बनाना**, **डेटा सीरीज़ चार्ट जोड़ना**, **चार्ट का आकार कैसे सेट करें** को नियंत्रित करना, और **चार्ट को Word में सम्मिलित करना** जानते हैं, जबकि आप **एक खाली Word दस्तावेज़** से शुरू करते हैं। उदाहरण Aspose.Words for Java 24.9 का उपयोग करता है, लेकिन समान अवधारणाएँ अन्य चार्ट लाइब्रेरीज़ पर भी लागू होती हैं जो समान API प्रदान करती हैं।

### अगले कदम

* अन्य चार्ट प्रकारों (`ChartType.PIE`, `ChartType.LINE`, आदि) का अन्वेषण करें – यह द्वितीयक कीवर्ड **insert chart into word** से जुड़ता है।
* अक्ष लेबल, लेजेंड और रंगों को अपने ब्रांड गाइडलाइन के अनुसार अनुकूलित करें।
* डेटाबेस क्वेरी या CSV फ़ाइलों से गतिशील रूप से चार्ट उत्पन्न करें।
* उत्पन्न `.docx` को वितरण के लिए PDF में बदलें (`doc.save("output.pdf", SaveFormat.PDF)`).

आकार, सीरीज़ डेटा और स्टाइलिंग विकल्पों के साथ प्रयोग करने में संकोच न करें ताकि आप बिल्कुल वही दृश्य बना सकें जिसकी आपको आवश्यकता है। कोडिंग का आनंद लें!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Java – आयताकार आकार को शैडो इफ़ेक्ट के साथ जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Word दस्तावेज़ में एरिया चार्ट सम्मिलित करें](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}