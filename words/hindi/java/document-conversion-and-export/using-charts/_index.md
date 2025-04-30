---
"description": "Java के लिए Aspose.Words में चार्ट बनाने और उन्हें कस्टमाइज़ करने का तरीका जानें। डेटा विज़ुअलाइज़ेशन के लिए चार्ट प्रकार, फ़ॉर्मेटिंग और अक्ष गुणों का अन्वेषण करें।"
"linktitle": "चार्ट का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "जावा के लिए Aspose.Words में चार्ट का उपयोग करना"
"url": "/hi/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में चार्ट का उपयोग करना


## जावा के लिए Aspose.Words में चार्ट का उपयोग करने का परिचय

इस ट्यूटोरियल में, हम जावा के लिए Aspose.Words का उपयोग करके चार्ट के साथ काम करने का तरीका जानेंगे। आप सीखेंगे कि विभिन्न प्रकार के चार्ट कैसे बनाएं, अक्ष गुणों को कस्टमाइज़ करें, डेटा लेबल को फ़ॉर्मेट करें, और बहुत कुछ। आइए शुरू करते हैं!

## लाइन चार्ट बनाना

लाइन चार्ट बनाने के लिए निम्नलिखित कोड का उपयोग करें:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// डिफ़ॉल्ट रूप से उत्पन्न श्रृंखला को हटाएँ.
chart.getSeries().clear();

// डेटा और डेटा लेबल के साथ एक श्रृंखला जोड़ना.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// या प्रारूप कोड को स्रोत सेल से लिंक करें.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## अन्य प्रकार के चार्ट बनाना

आप समान तकनीकों का उपयोग करके कॉलम, क्षेत्र, बबल, स्कैटर आदि जैसे विभिन्न प्रकार के चार्ट बना सकते हैं। यहाँ एक सरल कॉलम चार्ट सम्मिलित करने का एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// डिफ़ॉल्ट रूप से उत्पन्न श्रृंखला को हटाएँ.
chart.getSeries().clear();

// श्रेणियाँ बनाना और डेटा जोड़ना.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## अक्ष गुण अनुकूलित करना

आप अक्ष गुणों को अनुकूलित कर सकते हैं, जैसे कि अक्ष प्रकार बदलना, टिक मार्क सेट करना, लेबल फ़ॉर्मेट करना, और बहुत कुछ। यहाँ XY अक्ष गुणों को परिभाषित करने का एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// डिफ़ॉल्ट श्रृंखला साफ़ करें और अपना डेटा जोड़ें.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// X अक्ष को दिनांक के स्थान पर श्रेणी में बदलें।
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // वाई अक्ष (सैकड़ों) की प्रदर्शन इकाइयों में मापा जाता है।
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## डेटा लेबल का प्रारूपण

आप डेटा लेबल को अलग-अलग संख्या फ़ॉर्मेट में फ़ॉर्मेट कर सकते हैं। यहाँ एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// डिफ़ॉल्ट श्रृंखला साफ़ करें और अपना डेटा जोड़ें.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## अतिरिक्त चार्ट अनुकूलन

आप सीमाओं, लेबल के बीच अंतराल इकाइयों, चार्ट अक्षों को छिपाने, और बहुत कुछ समायोजित करके अपने चार्ट को और भी अधिक अनुकूलित कर सकते हैं। इन विकल्पों के बारे में अधिक जानने के लिए दिए गए कोड स्निपेट देखें।

## निष्कर्ष

इस ट्यूटोरियल में, हमने जावा के लिए Aspose.Words का उपयोग करके चार्ट के साथ काम करने का तरीका खोजा है। आपने सीखा है कि विभिन्न प्रकार के चार्ट कैसे बनाएं, अक्ष गुणों को अनुकूलित करें, डेटा लेबल को प्रारूपित करें, और बहुत कुछ। जावा के लिए Aspose.Words आपके दस्तावेज़ों में डेटा के दृश्य प्रतिनिधित्व जोड़ने के लिए शक्तिशाली उपकरण प्रदान करता है, जिससे आप जानकारी प्रस्तुत करने के तरीके को बेहतर बनाते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं एक चार्ट में एकाधिक श्रृंखलाएं कैसे जोड़ सकता हूं?

आप इसका उपयोग करके चार्ट में एकाधिक श्रृंखलाएँ जोड़ सकते हैं `chart.getSeries().add()` विधि। श्रृंखला नाम, श्रेणियाँ और डेटा मान निर्दिष्ट करना सुनिश्चित करें।

### मैं कस्टम संख्या प्रारूपों के साथ डेटा लेबल को कैसे प्रारूपित कर सकता हूं?

आप डेटा लेबल को एक्सेस करके फ़ॉर्मेट कर सकते हैं `DataLabels` किसी श्रृंखला के गुणधर्मों का उपयोग करके वांछित प्रारूप कोड सेट करना `getNumberFormat().setFormatCode()`.

### मैं चार्ट में अक्ष गुण कैसे अनुकूलित करूँ?

आप एक्सेस करके अक्ष गुण जैसे प्रकार, टिक मार्क, लेबल और अधिक को अनुकूलित कर सकते हैं `ChartAxis` जैसे गुण `setCategoryType()`, `setCrosses()`, और `setMajorTickMark()`.

### मैं स्कैटर या क्षेत्र चार्ट जैसे अन्य प्रकार के चार्ट कैसे बना सकता हूं?

आप उपयुक्त चार्ट निर्दिष्ट करके विभिन्न चार्ट प्रकार बना सकते हैं `ChartType` चार्ट का उपयोग करते समय `builder.insertChart(ChartType.TYPE, width, height)`.

### मैं चार्ट अक्ष को कैसे छिपा सकता हूँ?

आप चार्ट अक्ष को सेट करके छिपा सकते हैं `setHidden(true)` अक्ष की संपत्ति.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}