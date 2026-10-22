---
category: general
date: 2026-10-04
description: एक चरण‑दर‑चरण जावा उदाहरण के साथ वर्ड चार्ट में स्लाइस को एक्सप्लोड करना,
  पाई चार्ट स्लाइस को एक्सप्लोड करना और डोनट चार्ट का आकार बदलना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: hi
lastmod: 2026-10-04
og_description: Word चार्ट में स्लाइस को एक्सप्लोड करने और Java के साथ पाई या डोनट
  चार्ट को कस्टमाइज़ करने का तरीका। Word में चार्ट को संशोधित करने के लिए पूर्ण उदाहरण
  देखें।
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Word चार्ट में स्लाइस को एक्सप्लोड करने का तरीका – पूर्ण Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Word चार्ट में स्लाइस को एक्सप्लोड कैसे करें और उसकी उपस्थिति को कस्टमाइज़
  करें
url: /hi/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word चार्ट में स्लाइस को एक्सप्लोड कैसे करें और उसकी उपस्थिति को कस्टमाइज़ करें

यदि आपको Word चार्ट में **स्लाइस को एक्सप्लोड** करने की आवश्यकता है, तो यह गाइड आपको बिल्कुल वही दिखाएगा। चाहे आप बिक्री प्रस्तुति तैयार कर रहे हों या वित्तीय रिपोर्ट, पाई‑चार्ट की स्लाइस को एक्सप्लोड करना या डोनट होल को समायोजित करना सबसे महत्वपूर्ण डेटा को उजागर कर सकता है। अगले सेक्शनों में आप **Word में चार्ट को मॉडिफ़ाइ** करना, **पाई चार्ट स्लाइस को एक्सप्लोड** करना, **डोनट चार्ट का आकार बदलना**, और Aspose.Words for Java का उपयोग करके **पाई चार्ट वाले Word** दस्तावेज़ को कस्टमाइज़ करना सीखेंगे।

आप इस ट्यूटोरियल को एक पूर्ण, तैयार‑चलाने योग्य Java प्रोग्राम के साथ समाप्त करेंगे जो `.docx` फ़ाइल को लोड करता है, पाई चार्ट की पहली स्लाइस को एक्सप्लोड करता है, डोनट होल का आकार बदलता है, और परिणाम को सहेजता है। कोई बाहरी स्क्रिप्ट या मैन्युअल एडिटिंग आवश्यक नहीं है।

## Prerequisites

- आपके विकास मशीन पर Java 17 या उससे नया स्थापित हो।  
- Maven 3.6+ (या Gradle) ताकि डिपेंडेंसीज़ मैनेज की जा सकें।  
- Aspose.Words for Java लाइब्रेरी (डवलपमेंट के लिए फ्री ट्रायल काम करता है)।  
- एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक चार्ट (पाई या डोनट) हो।

## Step 1: Add Aspose.Words to your project

यदि आप Maven उपयोग करते हैं, तो अपने `pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Gradle के लिए, इसे `build.gradle` में रखें:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** अपनी लाइब्रेरी का संस्करण हमेशा अपडेट रखें; नए रिलीज़ अतिरिक्त चार्ट प्रकारों का समर्थन जोड़ते हैं और प्रदर्शन में सुधार करते हैं।

## Step 2: Load the Word document that contains a chart

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** दस्तावेज़ को लोड करने से एक इन‑मेमोरी प्रतिनिधित्व बनता है जिसे Aspose.Words ट्रैवर्स कर सकता है। इस ऑब्जेक्ट के बिना आप चार्ट नोड्स तक पहुंच नहीं सकते।

## Step 3: Retrieve the first chart in the document

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` सभी ड्रॉइंग ऑब्जेक्ट्स को कवर करता है, जिसमें चार्ट भी शामिल हैं। `true` आर्ग्यूमेंट Aspose को रीकर्सिवली सर्च करने के लिए कहता है, जिससे पहली चार्ट भी टेबल के अंदर नेस्टेड हो तो मिल जाए।

## Step 4: Explode the first slice of a pie chart

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** `setExplosion` मेथड एक संख्यात्मक मान लेता है जो निर्धारित करता है कि स्लाइस केंद्र से कितनी दूरी पर जाए। `20` का मान दृश्य रूप से स्पष्ट होता है बिना चार्ट लेआउट को बिगाड़े।

## Step 5: Adjust the doughnut hole size for a doughnut chart

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** बड़ा डोनट होल कई डेटा पॉइंट्स होने पर पठनीयता बढ़ा सकता है। `setDoughnutHoleSize` मेथड प्रतिशत (0‑100) अपेक्षित करता है।

## Step 6: Save the modified document

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Expected output

- पहली पाई चार्ट की पहली स्लाइस बाहर की ओर ऑफ़सेट हो जाएगी, जिससे वह प्रमुख दिखेगी।  
- यदि चार्ट डोनट है, तो केंद्रीय होल चार्ट त्रिज्या के 40 % तक विस्तारित हो जाएगा।  
- परिणामी फ़ाइल `PieChart.docx` को Microsoft Word, LibreOffice, या किसी भी संगत व्यूअर में खोला जा सकता है, जिससे प्रोग्रामेटिक रूप से लागू किए गए विज़ुअल बदलाव दिखेंगे।

## Full, runnable example

नीचे पूरा प्रोग्राम एक ही ब्लॉक में दिया गया है। इसे `ChartExploder.java` में कॉपी करें, फ़ाइल पाथ्स को समायोजित करें, और `mvn compile exec:java` (या अपने IDE की रन कॉन्फ़िगरेशन) के साथ चलाएँ।

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

इस कोड को चलाने से **Word में चार्ट को मॉडिफ़ाइ** किया जाएगा, **पाई चार्ट स्लाइस को एक्सप्लोड** किया जाएगा, और **डोनट चार्ट का आकार बदला** जाएगा।

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| *यदि दस्तावेज़ में कई चार्ट हैं तो क्या होगा?* | सैंपल **पहले** चार्ट (`NodeType.SHAPE, 0`) को टारगेट करता है। अन्य चार्ट्स के साथ काम करने के लिए इंडेक्स बदलें या `doc.getChildNodes(NodeType.SHAPE, true)` पर इटररेट करें और `shape.getChart() != null` द्वारा फ़िल्टर करें। |
| *क्या मैं पहली स्लाइस के अलावा किसी अन्य स्लाइस को एक्सप्लोड कर सकता हूँ?* | हाँ। इच्छित सीरीज़ को `chart.getSeries().get(seriesIndex)` से एक्सेस करें और `setExplosion(value)` कॉल करें। इंडेक्स शून्य‑आधारित होते हैं। |
| *क्या यह Word 2007‑2021 फ़ाइलों के साथ काम करता है?* | Aspose.Words `.doc`, `.docx`, `.dot`, और `.dotx` को सपोर्ट करता है। लाइब्रेरी फ़ाइल फ़ॉर्मेट को एब्स्ट्रैक्ट करती है, इसलिए कोड सभी संस्करणों में समान रूप से काम करता है। |
| *यदि चार्ट बार या लाइन चार्ट है तो क्या होगा?* | `setExplosion` और `setDoughnutHoleSize` केवल पाई‑टाइप चार्ट्स पर लागू होते हैं। जब चार्ट प्रकार अलग होता है तो कोड इन ऑपरेशन्स को सुरक्षित रूप से स्किप कर देता है। |
| *क्या Aspose.Words के लिए लाइसेंस चाहिए?* | फ्री इवैल्यूएशन लाइसेंस 30‑दिन की सीमा हटाता है लेकिन वॉटरमार्क जोड़ता है। प्रोडक्शन के लिए लाइसेंस खरीदें ताकि वॉटरमार्क हटे और पूरी फ़ंक्शनैलिटी अनलॉक हो। |

## Conclusion

अब आप जानते हैं **Word चार्ट में स्लाइस को एक्सप्लोड** कैसे करें, **Word में चार्ट को मॉडिफ़ाइ** कैसे करें, और Aspose.Words for Java का उपयोग करके **डोनट चार्ट का आकार बदलें**। पूरा उदाहरण वर्कफ़्लो—डॉक्यूमेंट लोड करने से लेकर चार्ट खोजने, विज़ुअल ट्यूनिंग लागू करने, और परिणाम सहेजने तक—को दर्शाता है, जिससे आप इन चरणों को किसी भी रिपोर्टिंग या डॉक्यूमेंट‑जनरेशन पाइपलाइन में इंटीग्रेट कर सकते हैं।

**Next steps**

- रंग बदलना, डेटा लेबल जोड़ना, या चार्ट प्रकार बदलना (`chart.setChartType(ChartType.BAR_CLUSTERED)`) जैसी अन्य चार्ट कस्टमाइज़ेशन एक्सप्लोर करें।  
- इस लॉजिक को Aspose.PDF के साथ मिलाकर उसी रिपोर्ट का PDF संस्करण जेनरेट करें।  
- फ़ाइलों की डायरेक्टरी में लूप करके कई दस्तावेज़ों के लिए प्रक्रिया को ऑटोमेट करें।

डिज़ाइन गाइडलाइन्स के अनुसार विभिन्न एक्सप्लोजन वैल्यूज़ या डोनट होल प्रतिशत के साथ प्रयोग करने में संकोच न करें। Happy coding!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}