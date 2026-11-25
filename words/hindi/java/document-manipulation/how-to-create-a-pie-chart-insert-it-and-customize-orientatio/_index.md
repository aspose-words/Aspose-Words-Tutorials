---
category: general
date: 2026-11-25
description: जावा में पाई चार्ट कैसे बनाएं, पाई चार्ट को वर्ड दस्तावेज़ में डालें,
  पाई स्लाइस को एक्सप्लोड करें और स्पष्ट कोड उदाहरणों के साथ चार्ट की अभिविन्यास बदलें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: hi
lastmod: 2026-11-25
og_description: जावा में पाई चार्ट बनाएं, पाई चार्ट को दस्तावेज़ में सम्मिलित करें,
  पाई स्लाइस को एक्सप्लोड करें और चरण‑दर‑चरण कोड के साथ चार्ट की अभिविन्यास बदलें।
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: जावा में पाई चार्ट बनाएं – जोड़ें, स्लाइस को विस्फोटित करें, और घुमाएँ
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: जावा में पाई चार्ट कैसे बनाएं, उसे सम्मिलित करें, और अभिविन्यास को अनुकूलित
  करें
url: /hi/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में पाई चार्ट बनाना, उसे डालना और अभिविन्यास को कस्टमाइज़ करना

यदि आपको Word दस्तावेज़ के भीतर **पाई चार्ट बनाना** है, तो यह गाइड आपको ठीक‑ठीक बताता है कि कैसे करना है। आप देखेंगे कि **पाई चार्ट कैसे डालें**, ज़ोर देने के लिए एक स्लाइस को कैसे एक्सप्लोड करें, और सरल रोटेशन के साथ **चार्ट अभिविन्यास कैसे बदलें**।

यह ट्यूटोरियल सब कुछ कवर करता है—Aspose.Words for Java लाइब्रेरी सेटअप करने से लेकर एक अंतिम `.docx` फ़ाइल बनाने तक, जिसमें घुमाया हुआ और एक्सप्लोड किया हुआ पाई चार्ट दिखेगा। कोई बाहरी दस्तावेज़ आवश्यक नहीं; बस चरणों का पालन करें और कोड चलाएँ।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Java 17 या नया संस्करण स्थापित हो।
* निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।
* वैध Aspose.Words for Java लाइसेंस (या मुफ्त इवैल्यूएशन मोड)।

`pom.xml` (Maven) या `build.gradle` (Gradle) में Aspose.Words निर्भरता जोड़ें। Maven के लिए उदाहरण:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **प्रो टिप:** लाइब्रेरी संस्करण को अद्यतन रखें; लेखन के समय नवीनतम रिलीज़ (24.10) में चार्ट रेंडरिंग के बग फिक्स शामिल हैं।

## चरण 1: पाई चार्ट बनाएं और उसे दस्तावेज़ में डालें

पहला चरण **पाई चार्ट** ऑब्जेक्ट बनाना और उसे Word फ़ाइल में एम्बेड करना है। नीचे दिया गया कोड एक साधारण दस्तावेज़ बनाता है, एक चार्ट प्लेसहोल्डर जोड़ता है, और 400 × 300 पिक्सेल आकार का पाई चार्ट डालता है।

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**क्यों महत्वपूर्ण है:** `builder.insertChart` एक चार्ट प्लेसहोल्डर बनाता है जिसे Aspose.Words स्वचालित रूप से दस्तावेज़ सहेजते समय OOXML चार्ट में बदल देता है। `ChartType.PIE` आर्ग्यूमेंट लाइब्रेरी को पाई चार्ट रेंडर करने के लिए बताता है, जिससे **पाई चार्ट डालना** की आवश्यकता पूरी होती है।

## चरण 2: पाई स्लाइस को एक्सप्लोड करके एक भाग को हाइलाइट करें

एक स्लाइस को एक्सप्लोड करने से किसी विशेष डेटा पॉइंट पर ध्यान आकर्षित होता है। निम्न पंक्ति पहली स्लाइस (इंडेक्स 0) को 10 पॉइंट्स तक एक्सप्लोड करती है:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

आप इंडेक्स बदलकर किसी अन्य स्लाइस को टारगेट कर सकते हैं, या एक्सप्लोड दूरी को समायोजित करके अधिक सूक्ष्म प्रभाव प्राप्त कर सकते हैं। स्लाइस को एक्सप्लोड करना Aspose.Words में **पाई स्लाइस एक्सप्लोड** करने का मानक तरीका है।

## चरण 3: चार्ट अभिविन्यास को रोटेट करके बदलें

चार्ट को घुमाने से नया दृश्य दृष्टिकोण मिलता है। `setRotationAngle` का उपयोग करके पूरे चार्ट को घड़ी की दिशा में घुमाएँ (कोण डिग्री में मापा जाता है)।

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

ऊपर दिया गया कॉल **पाई चार्ट रोटेट** और **चार्ट अभिविन्यास बदलें** की आवश्यकताओं को पूरा करता है। 0 से 360 डिग्री के बीच कोई भी कोण स्वीकार्य है।

## पूर्ण चलाने योग्य उदाहरण

सब कुछ मिलाकर, यहाँ एक पूर्ण, स्व-निहित प्रोग्राम है जो पाई चार्ट बनाता है, एक स्लाइस को एक्सप्लोड करता है, और चार्ट को रोटेट करता है। इसे अपने IDE से या कमांड लाइन से `java -cp <classpath> PieChartDemo` के साथ चलाएँ।

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### अपेक्षित आउटपुट

* कार्य निर्देशिका में **CreatePieChartDemo.docx** नाम की फ़ाइल बनती है।
* Microsoft Word में फ़ाइल खोलने पर 400 × 300 पिक्सेल पाई चार्ट दिखता है।
* पहली स्लाइस (Q1) 10 पॉइंट्स बाहर की ओर ऑफ़सेट होती है, जिससे **पाई स्लाइस एक्सप्लोड** प्रभाव बनता है।
* पूरा चार्ट 45 डिग्री झुका होता है, जो **चार्ट अभिविन्यास बदलें** और **पाई चार्ट रोटेट** को दर्शाता है।

## सामान्य विविधताएँ और किनारे के मामले

| स्थिति | कोड को कैसे अनुकूलित करें |
|-----------|-----------------------|
| **विभिन्न चार्ट आकार** | `insertChart` में `400, 300` आर्ग्यूमेंट बदलें। |
| **एकाधिक सीरीज़** | `chart.getSeries()` में अधिक `ChartSeries` ऑब्जेक्ट जोड़ें। |
| **किसी अन्य स्लाइस को एक्सप्लोड करें** | इच्छित `sliceIndex` के साथ `setExplode(sliceIndex, distance)` उपयोग करें। |
| **रोटेशन की आवश्यकता नहीं** | `setRotationAngle` कॉल को हटाएँ या कोण को `0` सेट करें। |
| **DOCX के बजाय PDF निर्यात** | दस्तावेज़ बनाने के बाद `doc.save("output.pdf")` को PDF फ़ॉर्मेट के साथ कॉल करें। |

> **ध्यान रखें:** नकारात्मक एक्सप्लोड दूरी देने पर `IllegalArgumentException` फेंका जाता है। हमेशा गैर‑नकारात्मक मान प्रदान करें।

## प्रदर्शन टिप

यदि आप लूप में कई चार्ट बनाते हैं, तो एक ही `DocumentBuilder` को पुनः उपयोग करें और प्रत्येक इटरेशन के लिए केवल `insertChart` कॉल करें। इससे मेमोरी ओवरहेड कम होता है और प्रोसेसिंग तेज़ होती है।

## निष्कर्ष

अब आप Aspose.Words for Java का उपयोग करके **पाई चार्ट बनाना**, **पाई चार्ट डालना**, **पाई स्लाइस एक्सप्लोड**, और **पाई चार्ट रोटेट** करना जानते हैं। पूरा उदाहरण पूर्ण वर्कफ़्लो दर्शाता है—दस्तावेज़ को इनिशियलाइज़ करने से लेकर घुमाए और एक्सप्लोड किए हुए पाई चार्ट वाली फ़ाइल सहेजने तक।

आगे, आप **चार्ट अभिविन्यास बदलना** को 3‑D इफ़ेक्ट्स जोड़कर और अधिक अन्वेषण कर सकते हैं, या **बार** या **लाइन** जैसे अन्य चार्ट प्रकारों के साथ प्रयोग कर सकते हैं। वही API पैटर्न लागू होते हैं, इसलिए इस ट्यूटोरियल का विस्तार करना सीधा है।

डेटा, स्लाइस इंडेक्स, या रोटेशन एंगल को अपनी रिपोर्टिंग आवश्यकताओं के अनुसार बदलने में संकोच न करें, और अपने परिणाम समुदाय के साथ साझा करें!

## आप अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगा सकें।

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}