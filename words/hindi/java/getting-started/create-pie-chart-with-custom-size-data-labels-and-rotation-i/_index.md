---
category: general
date: 2026-11-22
description: जावा में पाई चार्ट बनाएं और सीखें कि चार्ट का आकार कैसे सेट करें, डेटा
  लेबल जोड़ें, प्रतिशत दिखाएँ, और स्पष्ट दृश्य प्रभाव के लिए पहला स्लाइस घुमाएँ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: hi
lastmod: 2026-11-22
og_description: Java में पाई चार्ट बनाएं, फिर चार्ट का आकार सेट करें, डेटा लेबल पर
  प्रतिशत दिखाएँ, और पहले स्लाइस को घुमाएँ—सभी एक ही चलाने योग्य उदाहरण में।
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: जावा में कस्टम आकार, लेबल और घुमाव के साथ पाई चार्ट बनाएं
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: जावा में कस्टम आकार, डेटा लेबल और घूर्णन के साथ पाई चार्ट बनाएं
url: /hi/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में कस्टम आकार, डेटा लेबल और रोटेशन के साथ पाई चार्ट बनाएं

यदि आपको Java में **create pie chart** बनाने की आवश्यकता है, तो यह गाइड आपको पूरी प्रक्रिया से गुज़राएगा। आप सीखेंगे कि कैसे **set chart size** सेट करें, **show percentages pie chart** सक्षम करें, **data labels pie chart** जोड़ें, और **rotate pie chart slice** ताकि पहला स्लाइस 45‑डिग्री कोण पर शुरू हो।

उदाहरण में **Aspose.Slides for Java** का उपयोग किया गया है, जो PowerPoint फ़ाइलों को संभालने के लिए व्यापक रूप से उपयोग की जाने वाली लाइब्रेरी है। वही अवधारणाएँ अन्य चार्टिंग लाइब्रेरीज़ पर भी लागू होती हैं; बस API कॉल्स को अपने टूलकिट में समकक्ष से बदल दें।

## पूर्वापेक्षाएँ

* Java 17 या बाद का संस्करण स्थापित हो  
* निर्भरता प्रबंधन के लिए Maven 3.8+ (या Gradle)  
* Java सिंटैक्स की बुनियादी समझ  
* Aspose.Slides for Java बाइनरी तक पहुंच (आप आधिकारिक साइट से मुफ्त ट्रायल प्राप्त कर सकते हैं)

अपने `pom.xml` में निर्भरता जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## पाई चार्ट बनाएं – पूर्ण उदाहरण

निम्नलिखित प्रोग्राम एक PowerPoint स्लाइड बनाता है जिसमें कस्टम आकार, प्रतिशत डेटा लेबल, और घुमाया गया पहला स्लाइस वाला पाई चार्ट होता है।

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### प्रत्येक चरण क्यों महत्वपूर्ण है

| चरण | उद्देश्य | कीवर्ड्स से संबंध |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – वह मुख्य ऑब्जेक्ट जो दृश्य को रेंडर करेगा। | सीधे *create pie chart* आवश्यकता को पूरा करता है। |
| **Set dimensions** | `addChart(..., 400, 300)` कॉल **set chart size** को दर्शाता है। | चौड़ाई (400 px) और ऊँचाई (300 px) को नियंत्रित करता है। |
| **Show percentages** | `setShowPercentage(true)` चार्ट को प्रत्येक स्लाइस पर **show percentages pie chart** दिखाने के लिए बनाता है। | उपयोगकर्ताओं को अक्सर कच्चे मानों के बजाय प्रतिशत चाहिए होते हैं। |
| **Add data labels** | `DataLabelFormat` कॉन्फ़िगरेशन वांछित दृश्यता के साथ **data labels pie chart** जोड़ता है। | लेबल्स पठनीयता बढ़ाते हैं और अनुकूलन योग्य होते हैं। |
| **Rotate slice** | `setFirstSliceAngle(45)` चार्ट को घुमाता है ताकि पहला स्लाइस 45‑डिग्री कोण पर शुरू हो, जिससे **rotate pie chart slice** पूरा होता है। | किसी विशेष स्लाइस के लिए दृश्य जोर को बढ़ाता है। |

## चरण‑दर‑चरण विवरण

### 1. पाई चार्ट सम्मिलित करें और चार्ट आकार सेट करें

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*`addChart` मेथड चार्ट बनाता है और साथ ही **set chart size** को 400 × 300 पॉइंट्स पर सेट करता है।*  
यदि आपको अलग आकार चाहिए, तो अंतिम दो तर्कों को समायोजित करें।

### 2. चार्ट में डेटा भरें

डेमो तीन श्रेणियाँ और एक सिंगल सीरीज़ जोड़ता है। आवश्यकतानुसार हार्ड‑कोडेड संख्याओं को डेटाबेस, CSV, या उपयोगकर्ता इनपुट से प्राप्त डेटा से बदलें।

### 3. प्रत्येक स्लाइस पर प्रतिशत दिखाएँ

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*`setShowPercentage(true)` को सक्षम करने से चार्ट **show percentages pie chart** स्वचालित रूप से प्रत्येक स्लाइस का कुल में हिस्सा गणना करता है।*

### 4. विस्तृत डेटा लेबल जोड़ें

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

आप अन्य लेबल विकल्पों (`setShowValue`, `setShowSeriesName`, आदि) को टॉगल करके **add data labels pie chart** अनुभव को अनुकूलित कर सकते हैं।

### 5. पहला स्लाइस घुमाएँ

```java
chart.setFirstSliceAngle(45);
```

*`setFirstSliceAngle(45)` को कॉल करने से **rotate pie chart slice** होता है, जिससे पहला सेगमेंट 45‑डिग्री कोण पर शुरू होता है और वह प्रमुख बन जाता है।*

### 6. परिणाम सहेजें और देखें

प्रोग्राम चलाने पर `output/PieChartDemo.pptx` बनता है। इसे PowerPoint या किसी भी संगत व्यूअर में खोलें ताकि अंतिम पाई चार्ट देख सकें:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="कस्टम आकार, प्रतिशत लेबल और घुमाए गए पहले स्लाइस वाले बनाए गए पाई चार्ट का स्क्रीनशॉट"}

ऊपर की छवि **create pie chart** परिणाम को दर्शाती है, यह पुष्टि करती है कि आकार, लेबल, प्रतिशत, और रोटेशन सही ढंग से लागू किए गए हैं।

## सामान्य विविधताएँ और किनारे के मामलों

| स्थिति | समायोजन |
|-----------|------------|
| **विभिन्न चार्ट आयाम** | `addChart` में चौड़ाई/ऊँचाई पैरामीटर बदलें। |
| **एकाधिक श्रृंखलाएँ** | अतिरिक्त `IChartSeries` ऑब्जेक्ट जोड़ें; प्रत्येक श्रृंखला के अपने लेबल सेटिंग्स हो सकते हैं। |
| **कस्टम लेबल फ़ॉर्मेट** | दशमलव स्थानों को नियंत्रित करने के लिए `series.getDataLabelFormat().setNumberFormat("0.0%")` का उपयोग करें। |
| **दूसरे कोण पर घुमाना** | `setFirstSliceAngle` को कोई भी पूर्णांक (0‑360) पास करें। |
| **छवि के रूप में निर्यात** | सहेजने के बाद, रास्टर संस्करण के लिए `chart.writeAsSvg(outPath)` या `chart.writeAsPng(outPath)` को कॉल करें। |

> **Pro tip:** यदि आप लूप में कई चार्ट जनरेट करने की योजना बना रहे हैं, तो वही `Presentation` ऑब्जेक्ट पुन: उपयोग करें और केवल चार्ट डेटा बदलें। इससे मेमोरी ओवरहेड कम होता है और प्रोसेसिंग तेज़ होती है।

## निष्कर्ष

अब आप जानते हैं कि Java में **create pie chart** कैसे बनाएं, **set chart size** कैसे सेट करें, **show percentages pie chart** को सक्षम करें, **add data labels pie chart** जोड़ें, और बेहतर दृश्य जोर के लिए **rotate pie chart slice** कैसे घुमाएँ। पूर्ण, चलाने योग्य उदाहरण प्रारंभिक सेटअप से लेकर अंतिम PowerPoint फ़ाइल को सहेजने तक प्रत्येक चरण को दर्शाता है।

### आगे क्या?

* समान `ChartType` enum का उपयोग करके अन्य चार्ट प्रकार (बार, लाइन, एरिया) का अन्वेषण करें।  
* डैशबोर्ड के लिए एक ही स्लाइड पर कई चार्ट संयोजित करें।  
* वेब एप्लिकेशन में उपयोग के लिए चार्ट को PNG या SVG में निर्यात करें।  

रंगों, लीजेंड्स, और एनीमेशन इफ़ेक्ट्स के साथ प्रयोग करने में संकोच न करें—आपकी डेटा विज़ुअलाइज़ेशन केवल कल्पना तक सीमित हैं। चार्टिंग का आनंद लें!

## आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word में पाई चार्ट कैसे सम्मिलित करें – डेटा लेबल प्रतिशत जोड़ें](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Java में पाई स्लाइस को एक्सप्लोड कैसे करें – Aspose.Words चार्ट ट्यूटोरियल](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Java में पाई चार्ट सम्मिलित करें – एक्सप्लोड, रोटेट और स्लाइस हाइलाइट करें](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}