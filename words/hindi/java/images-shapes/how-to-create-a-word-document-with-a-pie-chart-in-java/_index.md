---
category: general
date: 2026-09-18
description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ बनाना और पाई चार्ट
  सम्मिलित करना सीखें। इसमें पाई चार्ट को घुमाने और Word फ़ाइल बनाने के चरण शामिल
  हैं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: hi
lastmod: 2026-09-18
og_description: जावा का उपयोग करके एक वर्ड दस्तावेज़ बनाएं और उसमें पाई चार्ट डालें।
  पाई चार्ट को घुमाने, स्लाइस को एक्सप्लोड करने और वर्ड फ़ाइल बनाने के लिए इस गाइड
  का पालन करें।
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: पाई चार्ट के साथ एक Word दस्तावेज़ बनाएं – चरण-दर-चरण Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: जावा में पाई चार्ट के साथ वर्ड दस्तावेज़ कैसे बनाएं
url: /hi/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में पाई चार्ट के साथ Word दस्तावेज़ कैसे बनाएं

यदि आपको **Word दस्तावेज़** बनाना है जो डेटा को विज़ुअलाइज़ करे, तो यह गाइड Aspose.Words for Java के साथ इसे करने का तरीका दिखाता है। आप पाई चार्ट डालना, एक स्लाइस को एक्सप्लोड करना, चार्ट को घुमाना, और अंत में **Word फ़ाइल** जेनरेट करना सीखेंगे जिसे आप Microsoft Word में खोल सकते हैं।

टेक्स्ट और चार्ट को मिलाकर रिपोर्ट बनाना अब अलग ग्राफ़िक्स टूल की जरूरत नहीं रखता। इस ट्यूटोरियल के अंत तक आपके पास एक पूर्ण, रन करने योग्य प्रोग्राम होगा जो .docx फ़ाइल बनाता है जिसमें पूरी तरह कॉन्फ़िगर किया गया पाई चार्ट होता है।

## आवश्यकताएँ

- Java 17 या बाद का संस्करण (कोड Java 8+ के साथ भी कम्पाइल होता है)
- निर्भरता प्रबंधन के लिए Maven या Gradle
- Aspose.Words for Java लाइसेंस (इस उदाहरण के लिए फ्री ट्रायल चलती है)
- Java सिंटैक्स की बुनियादी समझ

## चरण 1: Maven प्रोजेक्ट सेट अप करें

एक नया Maven प्रोजेक्ट बनाएं और `pom.xml` में Aspose.Words निर्भरता जोड़ें:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** संस्करण संख्या को अपडेट रखें; नए रिलीज़ में चार्ट‑टाइप सुधार और बग फ़िक्सेस शामिल होते हैं।

## चरण 2: नया Word दस्तावेज़ बनाएं

प्रोग्रामेटिक रूप से **Word दस्तावेज़** बनाने का पहला कदम `Document` ऑब्जेक्ट को इंस्टैंसिएट करना है। यह ऑब्जेक्ट मेमोरी में पूरे .docx फ़ाइल का प्रतिनिधित्व करता है।

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document` क्लास सभी Word‑प्रोसेसिंग फीचर्स के लिए एंट्री पॉइंट है। इस चरण पर कोई फ़ाइल डिस्क पर नहीं लिखी जाती; सब कुछ RAM में रहता है जब तक आप `save` नहीं कॉल करते।

## चरण 3: पाई चार्ट कैसे डालें

`DocumentBuilder` आपको दस्तावेज़ में कंटेंट जोड़ने देता है। `insertChart` के साथ आप सीधे **पाई चार्ट** ऑब्जेक्ट डाल सकते हैं।

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` Aspose.Words को पाई चार्ट बनाने के लिए बताता है। आकार पॉइंट्स में व्यक्त होते हैं (1 pt ≈ 1/72 in)। इस कॉल के बाद चार्ट एक नए पैराग्राफ में दिखाई देता है।

## चरण 4: चार्ट में डेटा भरें

पाई चार्ट को मानों की एक श्रृंखला चाहिए। यहाँ हम तीन श्रेणियाँ जोड़ते हैं: “Apples”, “Bananas”, और “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add` मेथड श्रृंखला बनाता है और स्वचालित रूप से लेजेंड एंट्रीज बनाता है। आप इस पैटर्न को किसी भी संख्यात्मक डेटासेट के लिए पुन: उपयोग कर सकते हैं।

## चरण 5: पहले स्लाइस को हाइलाइट करें

स्लाइस को एक्सप्लोड करने से विशेष मान पर ध्यान आकर्षित होता है। पहला स्लाइस (इंडेक्स 0) 20 पॉइंट्स द्वारा एक्सप्लोड किया जाता है।

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

सीरीज़ पर `explode` सेट करने से पूरे चार्ट पर असर पड़ता है, इसलिए केवल पहला डेटा पॉइंट ऑफ़सेट होता है।

## चरण 6: पाई चार्ट को कैसे घुमाएँ

चार्ट को घुमाने से विज़ुअल बैलेंस बेहतर होता है, विशेषकर जब सबसे बड़ा स्लाइस शीर्ष पर नहीं होता। `setRotationAngle` मेथड डिग्रीज़ में मान लेता है।

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

45° का रोटेशन स्टार्ट एंगल को घड़ी की दिशा में घुमाता है, जिससे कई लेआउट में चार्ट पढ़ना आसान हो जाता है।

## चरण 7: दस्तावेज़ को सहेजें और Word फ़ाइल जेनरेट करें

अंत में, दस्तावेज़ को डिस्क पर लिखें। यह चरण **Word फ़ाइल जेनरेट** करता है जिसे Microsoft Word, LibreOffice, या किसी भी संगत व्यूअर से खोला जा सकता है।

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` मेथड स्वचालित रूप से .docx एक्सटेंशन पहचान लेता है और Word‑संगत पैकेज लिखता है। फ़ोल्डर `output` मौजूद होना चाहिए या आप इसे प्रोग्रामेटिकली बना सकते हैं।

### अपेक्षित आउटपुट

प्रोग्राम चलाने के बाद, `output/PieChart.docx` खोलें। आपको दिखना चाहिए:

- एक सिंगल पेज जिसमें 400 × 300 pt पाई चार्ट है।
- “Apples” स्लाइस 20 pt बाहर की ओर एक्सप्लोड किया गया है।
- पूरा चार्ट 45° घड़ी की दिशा में घुमाया गया है।
- तीन फल श्रेणियों के साथ मिलती-जुलती लेजेंड।

## सामान्य विविधताएँ और किनारे के मामले

### कई चार्ट डालना

यदि आपको एक से अधिक चार्ट चाहिए, तो कर्सर को मूव करने के बाद `builder.insertChart` फिर से कॉल करें:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### चार्ट रंग बदलना

आप सीरीज़ के `getPoints()` कलेक्शन के माध्यम से स्लाइस रंग कस्टमाइज़ कर सकते हैं:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### बड़े डेटासेट को संभालना

यदि डेटासेट में 10 से अधिक स्लाइस हैं, तो विज़ुअल क्लैरिटी बनाए रखने के लिए डोनट चार्ट (`ChartType.DOUGHNUT`) उपयोग करने पर विचार करें।

## निष्कर्ष

अब आप **Word दस्तावेज़ बनाना**, **पाई चार्ट डालना**, **पाई चार्ट घुमाना**, और Aspose.Words for Java का उपयोग करके **Word फ़ाइल जेनरेट करना** जानते हैं। पूरा समाधान दस्तावेज़ इनिशियलाइज़ेशन से लेकर अंतिम फ़ाइल आउटपुट तक का वर्कफ़्लो दिखाता है, जिसमें प्रत्येक चरण के “कैसे” और “क्यों” दोनों शामिल हैं।

अगला, संबंधित विषयों का अन्वेषण करें जैसे **डेटाबेस से पाई चार्ट डेटा बनाना**, डेटा लेबल जोड़ना, या चार्ट को इमेज के रूप में एक्सपोर्ट करना। विभिन्न चार्ट टाइप (बार, लाइन, डोनट) के साथ प्रयोग करें ताकि आपका Word‑ऑटोमेशन टूलकिट विस्तृत हो सके।


## अब आपको क्या सीखना चाहिए?


निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर कर सकें।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}