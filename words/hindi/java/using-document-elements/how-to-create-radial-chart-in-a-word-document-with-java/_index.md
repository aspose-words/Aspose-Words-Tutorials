---
category: general
date: 2026-09-18
description: जावा का उपयोग करके वर्ड दस्तावेज़ में रेडियल चार्ट बनाना सीखें, चार्ट
  डेटा लेबल जोड़ें, और पूरी कोड उदाहरण के साथ सीरीज़ डेटा डालें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: hi
lastmod: 2026-09-18
og_description: Java का उपयोग करके Word दस्तावेज़ में रेडियल चार्ट बनाएं, चार्ट डेटा
  लेबल जोड़ें, और एक ही ट्यूटोरियल में सीरीज़ डेटा सम्मिलित करें।
og_image_alt: Radial chart displayed inside a generated Word document
og_title: जावा के साथ वर्ड में रेडियल चार्ट बनाएं – चरण-दर-चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Java के साथ Word दस्तावेज़ में रेडियल चार्ट कैसे बनाएं
url: /hi/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के साथ Word दस्तावेज़ में रेडियल चार्ट कैसे बनाएं

यदि आपको Word दस्तावेज़ में रेडियल चार्ट बनाना है, तो यह गाइड आपको सटीक चरण दिखाता है। आप चार्ट डेटा लेबल जोड़ना और सीरीज़ डेटा सम्मिलित करना भी सीखेंगे ताकि चार्ट प्रस्तुति के लिए तैयार हो।

प्रोग्रामेटिक रूप से चार्ट जेनरेट करने से मैनुअल फॉर्मेटिंग का काम हट जाता है और रिपोर्टों में स्थिरता सुनिश्चित होती है। यह ट्यूटोरियल मानता है कि आपके पास बुनियादी Java ज्ञान है और Aspose.Words for Java लाइब्रेरी का नवीनतम संस्करण स्थापित है।

## What you will need

* Java 17 या नया  
* Aspose.Words for Java (संस्करण 23.12 या बाद का)  
* एक IDE या बिल्ड टूल जो Maven/Gradle डिपेंडेंसीज़ को रिजॉल्व कर सके  

इन प्री‑रिक्विज़िट्स को स्थापित करने से आप उदाहरण को अतिरिक्त कॉन्फ़िगरेशन के बिना चला सकते हैं।

## How to create radial chart in a Word document

पहला कदम एक खाली Word फ़ाइल बनाना है जिसमें चार्ट होस्ट किया जाएगा। एक खाली दस्तावेज़ साफ़ कैनवास प्रदान करता है और अनपेक्षित स्टाइल्स से बचाता है।

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` पूरे .docx फ़ाइल को दर्शाता है, जबकि `DocumentBuilder` पैराग्राफ, टेबल और चार्ट जैसे तत्व सम्मिलित करने के मेथड्स प्रदान करता है।

## How to insert chart

अब आप स्वयं चार्ट सम्मिलित करेंगे। `insertChart` मेथड एक चार्ट ऑब्जेक्ट बनाता है और उसे बिल्डर के वर्तमान कर्सर पोज़ीशन पर रखता है।

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

एक पोलर चार्ट डेटा पॉइंट्स को केंद्रीय अक्ष के चारों ओर रेंडर करता है, जो चक्रीय जानकारी दिखाने के लिए आदर्श है। आयाम पॉइंट्स में व्यक्त होते हैं (1 pt ≈ 1/72 इंच)।

## Add series data to the chart

सीरीज़ डेटा के बिना चार्ट खाली रहता है। आप मैन्युअली सीरीज़ जोड़ सकते हैं या उसे डेटा स्रोत से बाइंड कर सकते हैं। नीचे दिया गया उदाहरण तीन डेटा पॉइंट्स वाली एक सीरीज़ जोड़ता है।

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` एक सीरीज़ नाम, श्रेणी लेबलों की सूची, और संबंधित संख्यात्मक मानों की सूची लेता है। आप अतिरिक्त सीरीज़ जोड़ने के लिए इस ब्लॉक को दोहरा सकते हैं (`addSeriesData`)।

## Add chart data labels to the first series

डेटा लेबल्स चार्ट को पॉइंट्स पर होवर किए बिना पढ़ने योग्य बनाते हैं। निम्न पंक्ति पहली सीरीज़ के लिए वैल्यू लेबल्स को सक्रिय करती है।

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

`showValue` को `true` सेट करने से प्रत्येक पॉइंट का मान सीधे चार्ट पर दिखाया जाता है। आप समान `DataLabelFormat` ऑब्जेक्ट के माध्यम से श्रेणी नाम, प्रतिशत, या लीडर लाइन्स भी सक्षम कर सकते हैं।

## Save the Word file

चार्ट कॉन्फ़िगर हो जाने के बाद, दस्तावेज़ को डिस्क पर लिखें। ऐसा स्थान चुनें जिसे आपका एप्लिकेशन एक्सेस कर सके।

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

फ़ाइल `RadialChart.docx` अब डेटा लेबल्स के साथ एक पूर्ण कार्यात्मक रेडियल चार्ट रखती है।

## Full working example

नीचे एक स्व-निहित प्रोग्राम है जिसे आप कॉपी, कंपाइल और रन कर सकते हैं। यह खाली Word दस्तावेज़ बनाने से लेकर डेटा लेबल्स के साथ रेडियल चार्ट सहेजने तक का पूरा वर्कफ़्लो दर्शाता है।

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Expected result**

जब आप `output/RadialChart.docx` को Microsoft Word में खोलेंगे, तो आपको *Quarterly Sales* शीर्षक वाला एक रेडियल चार्ट दिखेगा। प्रत्येक पॉइंट अपने संख्यात्मक मान (जैसे “15000”) को मार्कर के बगल में प्रदर्शित करेगा।

## Common variations and edge cases

| Situation | Recommended change |
|-----------|--------------------|
| You need a different chart type | Replace `ChartType.POLAR` with any other `ChartType` enum value (e.g., `ChartType.COLUMN`). |
| The chart must use an external Excel range | Use `chart.setDataRange("Sheet1!A1:B5")` after creating the chart and loading the workbook. |
| You want to hide the legend | `chart.getLegend().setVisible(false);` |
| The document must be saved as PDF | Call `doc.save("RadialChart.pdf");` – Aspose.Words automatically converts the chart. |

इन समायोजनों से कोर लॉजिक अपरिवर्तित रहता है जबकि आउटपुट को विशिष्ट आवश्यकताओं के अनुसार अनुकूलित किया जा सकता है।

## Pro tips

* **Reuse the builder** – आप एक ही दस्तावेज़ में कई चार्ट सम्मिलित करने के लिए `builder.insertChart` को बार‑बार कॉल कर सकते हैं।  
* **Performance** – कई चार्ट जेनरेट करते समय एक ही `DocumentBuilder` इंस्टेंस बनाकर उसे पुन: उपयोग करें ताकि ऑब्जेक्ट अलोकेशन ओवरहेड कम हो।  
* **Styling** – चार्ट की उपस्थिति (रंग, लाइन मोटाई) `Chart` ऑब्जेक्ट के `getSeries().get(i).getFormat()` मेथड्स के माध्यम से नियंत्रित होती है। इन सेटिंग्स के साथ प्रयोग करें ताकि कॉरपोरेट ब्रांडिंग से मेल खा सके।

## Conclusion

अब आप जानते हैं कि Java के साथ Word दस्तावेज़ में रेडियल चार्ट कैसे बनाएं, सीरीज़ डेटा जोड़ें, और फ़ाइल सहेजने से पहले चार्ट डेटा लेबल्स कैसे जोड़ें। पूरा उदाहरण अतिरिक्त सीरीज़, कस्टम स्टाइल्स, या वैकल्पिक आउटपुट फ़ॉर्मेट्स को संभालने के लिए विस्तारित किया जा सकता है।

संबंधित विषयों का अन्वेषण करें जैसे **how to insert chart** from external data sources, **create blank word** documents with predefined templates, और **add series data** dynamically from databases। विभिन्न चार्ट प्रकारों के साथ प्रयोग करें ताकि आप अपने डेटा को सबसे प्रभावी रूप से प्रस्तुत कर सकें।

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}