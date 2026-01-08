---
date: 2025-12-13
description: Aspose.Words for Java के साथ कॉलम चार्ट बनाना और चार्ट डेटा लेबल्स को
  फ़ॉर्मेट करना सीखें। कई सीरीज़ जोड़ना, एक्सिस प्रकार बदलना और चार्ट एक्सिस को छिपाना
  देखें।
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं
url: /hi/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं

इस ट्यूटोरियल में आप **कॉलम चार्ट** विज़ुअलाइज़ेशन सीधे Word दस्तावेज़ों में Aspose.Words for Java का उपयोग करके बनाएँगे। हम विभिन्न चार्ट प्रकार बनाना, कई सीरीज़ जोड़ना, चार्ट डेटा लेबल फ़ॉर्मेट करना, एक्सिस टाइप बदलना, और जब आप साफ़ लुक चाहते हैं तो चार्ट एक्सिस को छिपाना आदि दिखाएंगे। अंत तक आपके पास दस्तावेज़ों में रिच चार्ट एम्बेड करने के लिए एक ठोस, प्रोडक्शन‑रेडी तरीका होगा।

## त्वरित उत्तर
- **चार्ट बनाने के लिए मुख्य क्लास कौन सी है?** `DocumentBuilder` के साथ `insertChart`।
- **नई सीरीज़ जोड़ने वाला मेथड कौन सा है?** `chart.getSeries().add(...)`।
- **मैं चार्ट डेटा लेबल कैसे फ़ॉर्मेट करूँ?** `getDataLabels().get(...).getNumberFormat().setFormatCode(...)` का उपयोग करें।
- **क्या मैं एक्सिस को छिपा सकता हूँ?** हाँ, एक्सिस ऑब्जेक्ट पर `setHidden(true)` कॉल करें।
- **क्या Aspose.Words के लिए लाइसेंस चाहिए?** प्रोडक्शन उपयोग के लिए लाइसेंस आवश्यक है; एक फ्री ट्रायल उपलब्ध है।

## कॉलम चार्ट क्या है और इसे क्यों उपयोग करें?

कॉलम चार्ट श्रेणीबद्ध डेटा को वर्टिकल बार के रूप में दर्शाता है, जिससे समूहों (क्षेत्र अनुसार बिक्री, मासिक खर्च आदि) के बीच मानों की तुलना आसान हो जाती है। Java एप्लिकेशन में Aspose.Words के साथ कॉलम चार्ट जनरेट करने से आप इन विज़ुअल को सीधे Word / DOCX फ़ाइलों में एम्बेड कर सकते हैं, बिना Excel या बाहरी टूल्स की जरूरत के।

## कॉलम चार्ट कैसे बनाएं

नीचे एक सरल उदाहरण है जो एक बेसिक कॉलम चार्ट बनाता है। कोड मूल स्निपेट जैसा ही है – हमने केवल समझाने वाले कमेंट्स जोड़े हैं ताकि इसे फॉलो करना आसान हो।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### कई सीरीज़ जोड़ें

आप **कई सीरीज़** को `chart.getSeries().add(...)` को बार‑बार कॉल करके कॉलम चार्ट में जोड़ सकते हैं, जैसा कि ऊपर दिखाया गया है। प्रत्येक सीरीज़ का अपना कैटेगरी और वैल्यू सेट हो सकता है, जिससे आप कई डेटा सेट साइड‑बाय‑साइड तुलना कर सकते हैं।

## कस्टम डेटा लेबल वाले लाइन चार्ट कैसे बनाएं

यदि आपको कॉलम चार्ट की बजाय लाइन चार्ट चाहिए, तो वही पैटर्न लागू होता है। यह उदाहरण भी **चार्ट डेटा लेबल फ़ॉर्मेट** को विभिन्न नंबर फ़ॉर्मेट के साथ दिखाता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### डेटा लेबल जोड़ें

`series1.hasDataLabels(true)` कॉल **डेटा लेबल जोड़ती** है, जबकि `setShowValue(true)` चार्ट पर वास्तविक मान दिखाता है।

## एक्सिस टाइप बदलें और एक्सिस प्रॉपर्टीज़ कस्टमाइज़ करें

एक्सिस टाइप बदलने (जैसे डेट से कैटेगरी) से आप डेटा पॉइंट्स के प्लॉटिंग को नियंत्रित कर सकते हैं। यह स्निपेट यह भी दिखाता है कि **चार्ट एक्सिस को छिपाया** जा सकता है यदि आप न्यूनतम डिज़ाइन पसंद करते हैं।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### एक्सिस टाइप बदलें

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **एक्सिस टाइप** को डेट‑बेस्ड एक्सिस से कैटेगोरिकल में बदलता है, जिससे लेबल प्लेसमेंट पर पूरी नियंत्रण मिलती है।

## चार्ट डेटा लेबल फ़ॉर्मेट करें (नंबर फ़ॉर्मेट)

आप सीधे एक्सिस या डेटा लेबल पर नंबर फ़ॉर्मेट लागू कर सकते हैं। यह उदाहरण Y‑एक्सिस के नंबरों को थाउज़ेंड सेपरेटर के साथ फ़ॉर्मेट करता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## अतिरिक्त चार्ट कस्टमाइज़ेशन

बेसिक से आगे, आप बाउंड्स एडजस्ट कर सकते हैं, लेबल्स के बीच इंटरवल यूनिट सेट कर सकते हैं, विशिष्ट एक्सिस को छिपा सकते हैं, आदि। पूरी प्रॉपर्टी सूची के लिए Aspose.Words for Java API डॉक्यूमेंटेशन देखें।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: मैं चार्ट में कई सीरीज़ कैसे जोड़ूँ?**  
उत्तर: आप `chart.getSeries().add()` को प्रत्येक सीरीज़ के लिए उपयोग करें। प्रत्येक कॉल में यूनिक नाम, कैटेगरी एरे, और वैल्यू एरे प्रदान किया जा सकता है।

**प्रश्न: मैं कस्टम नंबर फ़ॉर्मेट के साथ चार्ट डेटा लेबल कैसे फ़ॉर्मेट करूँ?**  
उत्तर: किसी सीरीज़ के `DataLabels` ऑब्जेक्ट को एक्सेस करें और `getNumberFormat().setFormatCode("your format")` कॉल करें। आप `isLinkedToSource(true)` के साथ फ़ॉर्मेट को स्रोत सेल से भी लिंक कर सकते हैं।

**प्रश्न: मैं चार्ट एक्सिस को कैसे छिपा सकता हूँ?**  
उत्तर: `ChartAxis` को आप छिपाना चाहते हैं, उस पर `setHidden(true)` कॉल करें (उदा., `chart.getAxisY().setHidden(true)` )।

**प्रश्न: एक्सिस टाइप बदलने का सबसे अच्छा तरीका क्या है?**  
उत्तर: कैटेगोरिकल एक्सिस के लिए `setCategoryType(AxisCategoryType.CATEGORY)` और डेट एक्सिस के लिए `AxisCategoryType.DATE` उपयोग करें।

**प्रश्न: मैं सीरीज़ में डेटा लेबल कैसे जोड़ूँ?**  
उत्तर: `series.hasDataLabels(true)` से उन्हें एनेबल करें और फिर `series.getDataLabels().setShowValue(true)` से विज़िबिलिटी कॉन्फ़िगर करें।

## निष्कर्ष

हमने Aspose.Words for Java के साथ **कॉलम चार्ट** विज़ुअलाइज़ेशन बनाने के सभी आवश्यक पहलुओं को कवर किया—बेसिक चार्ट इन्सर्ट करना, कई सीरीज़ जोड़ना, चार्ट डेटा लेबल फ़ॉर्मेट करना, एक्सिस टाइप बदलना, और साफ़ लुक के लिए एक्सिस छिपाना। इन तकनीकों को अपने रिपोर्टिंग या डॉक्यूमेंट‑जनरेशन पाइपलाइन में इंटीग्रेट करें ताकि प्रोफेशनल, डेटा‑ड्रिवन Word दस्तावेज़ प्रदान कर सकें।

---

**अंतिम अपडेट:** 2025-12-13  
**टेस्टेड विद:** Aspose.Words for Java 24.12 (latest)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}