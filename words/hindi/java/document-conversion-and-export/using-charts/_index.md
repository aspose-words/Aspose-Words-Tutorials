---
date: 2026-02-16
description: Aspose.Words for Java में चार्ट में कई श्रृंखलाएँ जोड़ना, अक्ष के टिक
  मार्क बदलना, कस्टम नंबर फ़ॉर्मेट लागू करना, और लाइन तथा कॉलम चार्ट के साथ चार्ट
  वर्ड दस्तावेज़ बनाना सीखें।
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में चार्ट्स में कई श्रृंखलाएँ जोड़ें
url: /hi/java/document-conversion-and-export/using-charts/
weight: 12
---

 be left English. Might keep as is.

I'll translate headings and text, but keep the parenthetical tags unchanged.

Also need to translate "Pro tip:" maybe keep as "प्रो टिप:" or "उपयोगी टिप:"? Keep as "Pro tip:" maybe keep English? It's a phrase; could translate to Hindi "प्रो टिप:" but it's okay.

I'll translate.

Now produce final content with same structure.

Let's craft translation.

Start with shortcodes unchanged.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# चार्ट में कई सीरीज़ जोड़ें Aspose.Words for Java के साथ

## Aspose.Words for Java में चार्ट उपयोग करने का परिचय

इस ट्यूटोरियल में आप सीखेंगे **कैसे कई सीरीज़** को एक चार्ट में जोड़ें, अक्ष टिक मार्क्स को कस्टमाइज़ करने और कस्टम नंबर फ़ॉर्मेट लागू करने का महत्व, और कैसे एक चार्ट‑समृद्ध Word दस्तावेज़ जनरेट करें। चाहे आपको वित्तीय डेटा के लिए लाइन चार्ट चाहिए या बिक्री आंकड़ों के लिए कॉलम चार्ट, नीचे दिए गए चरण आपको प्रोग्रामेटिकली चार्ट बनाने, स्टाइल करने और फाइन‑ट्यून करने में मदद करेंगे।

## त्वरित उत्तर
- **मैं कई सीरीज़ कैसे जोड़ूँ?** प्रत्येक प्रदर्शित करने वाली सीरीज़ के लिए `chart.getSeries().add(...)` उपयोग करें।  
- **क्या मैं अक्ष टिक मार्क्स बदल सकता हूँ?** हाँ – अक्ष ऑब्जेक्ट्स पर `setMajorTickMark()` और `setMinorTickMark()` उपयोग करें।  
- **डेटा लेबल पर कौन सा फ़ॉर्मेट लागू कर सकता हूँ?** कोई भी Excel‑संगत नंबर फ़ॉर्मेट, जैसे `"$"#,##0.00` या `0.00%`।  
- **कौन‑से चार्ट प्रकार समर्थित हैं?** लाइन, कॉलम, एरिया, बबल, स्कैटर, और `ChartType` के माध्यम से कई और।  
- **उत्पादन के लिए लाइसेंस आवश्यक है?** पूर्ण कार्यक्षमता के लिए एक वैध Aspose.Words for Java लाइसेंस आवश्यक है।

## चार्ट में “कई सीरीज़ जोड़ना” क्या है?
कई सीरीज़ जोड़ना मतलब एक ही चार्ट क्षेत्र में एक से अधिक डेटा सेट डालना, जिससे आप विभिन्न श्रेणियों या समय अवधियों की तुलना साइड‑बाय‑साइड कर सकते हैं। प्रत्येक सीरीज़ अपनी स्वयं की लाइन, कॉलम या मार्कर सेट के रूप में दिखाई देती है, जिससे पाठकों को अधिक समृद्ध विज़ुअल कहानी मिलती है।

## Aspose.Words for Java से चार्ट‑युक्त Word दस्तावेज़ क्यों बनाएं?
- **पूर्ण नियंत्रण** चार्ट प्रकार, लेआउट और स्टाइलिंग पर, बिना Word को मैन्युअली खोले।  
- **प्रोग्रामेटिक जनरेशन** स्वचालित रिपोर्टिंग पाइपलाइन में फिट बैठता है।  
- **क्रॉस‑प्लेटफ़ॉर्म** – किसी भी Java‑संगत वातावरण में काम करता है।  
- **समृद्ध API** अक्ष, डेटा लेबल और नंबर फ़ॉर्मेट को कस्टमाइज़ करने के लिए।

## पूर्वापेक्षाएँ
- Java Development Kit (JDK) 8 या उससे ऊपर।  
- आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी जोड़ी गई हो (Maven/Gradle या JAR)।  
- उत्पादन के लिए वैध Aspose लाइसेंस (मूल्यांकन के लिए वैकल्पिक)।

## चरण‑दर‑चरण गाइड

### चरण 1: एक लाइन चार्ट बनाएं और **कई सीरीज़ जोड़ें**
नीचे वह मुख्य कोड है जो एक लाइन चार्ट बनाता है, डिफ़ॉल्ट सीरीज़ को साफ़ करता है, और फिर कस्टम डेटा लेबल वाले तीन अलग‑अलग सीरीज़ जोड़ता है।

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

> **Pro tip:** `chart.getSeries().add(...)` को जितनी बार जरूरत हो, उतनी बार कॉल करें ताकि **कई सीरीज़ जोड़ें** – प्रत्येक कॉल एक नई लाइन (या कॉलम, आदि) उसी चार्ट पर बनाता है।

### चरण 2: **एक कॉलम चार्ट बनाएं** (create column chart java)
अगला स्निपेट दिखाता है कि कैसे एक साधारण कॉलम चार्ट इन्सर्ट करें, जो श्रेणियों की साइड‑बाय‑साइड तुलना के लिए उपयोगी है।

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

### चरण 3: **अक्ष टिक मार्क्स बदलें** (change axis tick marks)
X‑ और Y‑अक्ष को कस्टमाइज़ करने से पठनीयता बढ़ती है। नीचे दिया गया कोड टिक मार्क्स बदलने, क्रम उलटने, और कस्टम क्रॉसिंग पॉइंट सेट करने का प्रदर्शन करता है।

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### चरण 4: **कस्टम नंबर फ़ॉर्मेट लागू करें** (apply custom number format)
आप Excel द्वारा समर्थित किसी भी पैटर्न से अक्ष नंबर या डेटा लेबल फ़ॉर्मेट कर सकते हैं। नीचे एक संक्षिप्त उदाहरण है जो Y‑अक्ष को हजार‑सेपरेटर पैटर्न से फ़ॉर्मेट करता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### चरण 5: अंतिम Word दस्तावेज़ जनरेट करें (generate chart word document)
सीरीज़, अक्ष और लेबल कॉन्फ़िगर करने के बाद, ऊपर दिखाए गए स्निपेट्स की तरह `doc.save(...)` को कॉल करें। परिणामी `.docx` फ़ाइल में पूरी तरह कार्यशील चार्ट होते हैं जिन्हें Microsoft Word में खोला और संपादित किया जा सकता है।

## सामान्य उपयोग मामलों
- **वित्तीय डैशबोर्ड** – राजस्व, खर्च और लाभ के लिए कई सीरीज़ वाले लाइन चार्ट।  
- **बिक्री रिपोर्ट** – क्षेत्रों के बीच त्रैमासिक बिक्री की तुलना करने वाले कॉलम चार्ट।  
- **प्रोजेक्ट ट्रैकिंग** – समय के साथ प्रगति दर्शाने वाले एरिया या स्कैटर चार्ट।  

## अतिरिक्त चार्ट कस्टमाइज़ेशन
बुनियादी बातों के अलावा, आप बाउंड्स समायोजित कर सकते हैं, अक्ष छिपा सकते हैं (`axis.setHidden(true)`), रंग बदल सकते हैं, लेजेंड जोड़ सकते हैं, आदि। पूरी विकल्प सूची के लिए Aspose.Words for Java API रेफ़रेंस देखें।

## निष्कर्ष
इस गाइड में हमने **कई सीरीज़ जोड़ना**, लाइन और कॉलम दोनों प्रकार के चार्ट बनाना, **अक्ष टिक मार्क्स बदलना**, **कस्टम नंबर फ़ॉर्मेट लागू करना**, और अंत में **चार्ट‑समृद्ध Word दस्तावेज़ जनरेट करना** कवर किया। Aspose.Words for Java के साथ आपके पास कोड‑फ़र्स्ट तरीका है जो पेशेवर डेटा विज़ुअलाइज़ेशन को सीधे आपके दस्तावेज़ों में एम्बेड करता है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: मैं चार्ट में कई सीरीज़ कैसे जोड़ूँ?**  
उत्तर: आप प्रदर्शित करने वाली प्रत्येक सीरीज़ के लिए `chart.getSeries().add()` कॉल करें। प्रत्येक कॉल एक नया डेटा सेट बनाता है जो अपनी स्वयं की लाइन, कॉलम या मार्कर समूह के रूप में दिखता है।

**प्रश्न: मैं डेटा लेबल को कस्टम नंबर फ़ॉर्मेट से कैसे फ़ॉर्मेट करूँ?**  
उत्तर: सीरीज़ के `DataLabels` ऑब्जेक्ट को एक्सेस करें और `getNumberFormat().setFormatCode("your pattern")` उपयोग करें। आप `isLinkedToSource(true)` के साथ फ़ॉर्मेट को स्रोत सेल से भी लिंक कर सकते हैं।

**प्रश्न: मैं अक्ष टिक मार्क्स कैसे बदलूँ?**  
उत्तर: `ChartAxis` पर `setMajorTickMark()` और `setMinorTickMark()` उपयोग करें। विकल्पों में `CROSS`, `INSIDE`, `OUTSIDE`, और `NONE` शामिल हैं।

**प्रश्न: क्या मैं स्कैटर या एरिया जैसे अन्य चार्ट प्रकार बना सकता हूँ?**  
उत्तर: हाँ – `builder.insertChart(...)` कॉल करते समय इच्छित `ChartType` (जैसे `ChartType.SCATTER`, `ChartType.AREA`) निर्दिष्ट करें।

**प्रश्न: मैं अनावश्यक अक्ष को कैसे छिपाऊँ?**  
उत्तर: जिस `ChartAxis` को आप छिपाना चाहते हैं, उस पर `axis.setHidden(true)` कॉल करें।

---

**अंतिम अपडेट:** 2026-02-16  
**परीक्षित संस्करण:** Aspose.Words for Java 24.11  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}