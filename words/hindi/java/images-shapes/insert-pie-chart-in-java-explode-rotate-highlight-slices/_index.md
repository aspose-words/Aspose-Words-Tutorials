---
category: general
date: 2026-07-20
description: जावा में पाई चार्ट डालें, चरण‑दर‑चरण मार्गदर्शिका के साथ। सीखें कि स्लाइस
  को कैसे एक्सप्लोड करें, पाई चार्ट को कैसे घुमाएँ, पाई चार्ट स्लाइस को हाइलाइट करें
  और पाई चार्ट स्लाइस को कस्टमाइज़ करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: hi
lastmod: 2026-07-20
og_description: जावा में पाई चार्ट डालें और सीखें कि स्लाइस को कैसे एक्सप्लोड करें,
  पाई चार्ट को कैसे घुमाएँ, पाई चार्ट स्लाइस को हाइलाइट करें, और पॉलिश्ड विज़ुअल रिपोर्ट्स
  के लिए पाई चार्ट स्लाइस को कैसे कस्टमाइज़ करें।
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: जावा में पाई चार्ट डालें – विस्फोट, घुमाएँ और हाइलाइट करें
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: जावा में पाई चार्ट डालें – स्लाइस को बाहर निकालें, घुमाएँ और हाइलाइट करें
url: /hi/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में पाई चार्ट डालें – स्लाइस को एक्सप्लोड करें, घुमाएँ और हाइलाइट करें

क्या आपको कभी Java रिपोर्ट में **पाई चार्ट डालना** पड़ा है लेकिन यह नहीं पता था कि एक स्लाइस को कैसे बाहर निकाला जाए? आप अकेले नहीं हैं। चाहे आप डैशबोर्ड बना रहे हों, इनवॉइस जेनरेट कर रहे हों, या सिर्फ सर्वे परिणामों को विज़ुअलाइज़ कर रहे हों, एक अच्छी तरह से स्टाइल किया गया पाई चार्ट कच्चे आंकड़ों को तुरंत समझ में आने वाले अंतर्दृष्टि में बदल सकता है।

इस ट्यूटोरियल में आप एक पूर्ण, तैयार‑चलाने योग्य उदाहरण देखेंगे जो आपको दिखाएगा कि पाई चार्ट कैसे डालें, **स्लाइस को कैसे एक्सप्लोड करें**, **पाई चार्ट को कैसे घुमाएँ**, और यहाँ तक कि कस्टम रंगों के साथ **पाई चार्ट स्लाइस को हाइलाइट करें**। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी Java प्रोजेक्ट में डाल सकते हैं जो लोकप्रिय *JFreeChart* लाइब्रेरी (या कोई समान API) का उपयोग करता है।

## आवश्यकताएँ

- Java 17 या बाद का (कोड पुराने संस्करणों के साथ भी कंपाइल होता है, लेकिन संक्षिप्तता के लिए हम आधुनिक `var` सिंटैक्स का उपयोग करेंगे)।
- Maven या Gradle का उपयोग करके `org.jfree:jfreechart` डिपेंडेंसी को जोड़ें।
- Java क्लासेस और चार्ट बिल्डर की अवधारणा की बुनियादी समझ।

यदि आपने कभी Maven प्रोजेक्ट में लाइब्रेरी नहीं जोड़ी है, तो इसे अपने `pom.xml` में डाल दें:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

बस इतना ही—कोई अतिरिक्त सेटअप आवश्यक नहीं।

## चरण 1: पाई चार्ट डालें – बिल्डर और चार्ट ऑब्जेक्ट बनाएं

सबसे पहले: हमें एक *बिल्डर* (इसे फ़ैक्टरी समझें) चाहिए जो चार्ट बनाना जानता हो। JFreeChart में `ChartFactory` यह काम करता है।

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

हम डेटा सेट से क्यों शुरू करते हैं? क्योंकि चार्ट स्वयं केवल संख्याओं के चारों ओर एक दृश्य रैपर है। यहाँ **पाई चार्ट डालकर** हम पहले से ही 400 × 300 कैनवास प्राप्त कर लेते हैं (आकार बाद में जब हम इसे इमेज में रेंडर करेंगे, तब लागू होगा)।

## चरण 2: स्लाइस को कैसे एक्सप्लोड करें – पहले सेगमेंट को ज़ोर दें

अब जबकि चार्ट मौजूद है, चलिए पहले स्लाइस को प्रमुख बनाते हैं। स्लाइस को एक्सप्लोड करने से वह वृत्त से थोड़ा दूर निकलता है, जिससे पाठक का ध्यान आकर्षित होता है।

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

ध्यान दें कि हमने मेथड नाम में **how to explode slice** वाक्यांश का उपयोग किया है; इससे इरादा स्पष्ट हो जाता है। `setExplodePercent` मेथड एक कुंजी (स्लाइस लेबल) और प्रतिशत लेता है, जिससे आप आवश्यकतानुसार “पॉप‑आउट” दूरी को समायोजित कर सकते हैं।

## चरण 3: पाई चार्ट को कैसे घुमाएँ – शुरुआती एंगल बदलें

डिफ़ॉल्ट पाई चार्ट 12 ओ’clock की स्थिति से शुरू होता है। कभी‑कभी आप चाहते हैं कि पहला स्लाइस कहीं और से शुरू हो—शायद डिज़ाइन मॉक‑अप के साथ संरेखित करने या किसी अन्य चार्ट से मेल खाने के लिए।

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

`rotateChart(chart, 45)` को कॉल करने से पूरा पाई घुम जाता है ताकि “Apples” स्लाइस 45‑डिग्री एंगल से शुरू हो, बिल्कुल वही जो **how to rotate pie chart** आवश्यकता मांगती है।

## चरण 4: पाई चार्ट स्लाइस को हाइलाइट करें – कस्टम रंग और लेबल

एक्सप्लोड करने के अलावा, आप स्लाइस को एक अनोखा रंग या बोल्ड लेबल देना चाह सकते हैं ताकि वास्तव में **पाई चार्ट स्लाइस को हाइलाइट** किया जा सके।

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

यहाँ हमने पेंट और लेबल स्टाइल बदलकर **customize pie chart slice** किया है। अपने ब्रांड पैलेट के अनुसार रंग या फ़ॉन्ट बदलने में संकोच न करें।

## चरण 5: चार्ट को इमेज में रेंडर करें (वैकल्पिक लेकिन उपयोगी)

अधिकांश वास्तविक‑दुनिया के ऐप्स को चार्ट PNG, JPEG, या यहाँ तक कि PDF के रूप में चाहिए। नीचे चार्ट को फ़ाइल में लिखने का एक त्वरित तरीका दिया गया है।

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

पूरा फ्लो चलाने से 400 × 300 PNG बनेगा जो कुछ इस तरह दिखेगा:

![पाई चार्ट का उदाहरण](image.png){: alt="पाई चार्ट का उदाहरण जिसमें एक्सप्लोडेड और घुमाया गया स्लाइस दिखाया गया है"}

## पूर्ण कार्यशील उदाहरण

सब कुछ एक साथ रखकर, यहाँ एक `main` मेथड है जिसे आप नई Java क्लास में कॉपी‑पेस्ट करके चला सकते हैं:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### अपेक्षित आउटपुट

प्रोग्राम चलाने से **fruit-pie.png** नाम की फ़ाइल बनती है। इसे खोलें और आप देखेंगे:

- “Fruit Distribution” शीर्षक वाला 400 × 300 पाई चार्ट।
- “Apples” स्लाइस 15 % बाहर की ओर एक्सप्लोड किया गया।
- पूरा चार्ट घुमाया गया ताकि “Apples” 45‑डिग्री स्थिति से शुरू हो।
- एक्सप्लोडेड

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में माहिर बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Java के लिए Aspose.Words का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Scatter चार्ट डालें](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Area चार्ट डालें](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}