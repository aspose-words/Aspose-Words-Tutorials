---
category: general
date: 2026-10-07
description: जावा का उपयोग करके वर्ड में पाई चार्ट बनाना, डेटा सीरीज़ जोड़ना और चार्ट
  को PNG के रूप में सहेजना सीखें। तेज़ परिणामों के लिए चरण‑दर‑चरण गाइड का पालन करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: hi
lastmod: 2026-10-07
og_description: 'Word में जल्दी पाई चार्ट बनाएं: यह ट्यूटोरियल दिखाता है कि डेटा सीरीज़
  कैसे जोड़ें, चार्ट कैसे जनरेट करें, और Word चार्ट को एक इमेज (PNG) के रूप में कैसे
  सहेजें। पूरी कोड उदाहरण का पालन करें।'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Word में पाई चार्ट बनाएं और PNG के रूप में निर्यात करें – गाइड
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Word में पाई चार्ट कैसे बनाएं और इसे PNG के रूप में सहेजें
url: /hi/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में पाई चार्ट कैसे बनाएं और उसे PNG के रूप में सहेजें

यदि आपको Microsoft Word फ़ाइल के अंदर **pie chart** ऑब्जेक्ट बनाने की आवश्यकता है, तो यह गाइड आपको Java के साथ इसे कैसे करें, बिल्कुल दिखाएगा। आप यह भी सीखेंगे कि चार्ट में **डेटा सीरीज़ जोड़ें** और **चार्ट को PNG के रूप में सहेजें** ताकि विज़ुअल को Word के बाहर पुन: उपयोग किया जा सके।

डॉक्यूमेंट में सीधे चार्ट जेनरेट करने से आपको डेटा को अलग ग्राफ़िक्स टूल में एक्सपोर्ट करने की जरूरत नहीं पड़ती। इस ट्यूटोरियल के अंत तक आपके पास एक पूरी तरह कार्यशील Word फ़ाइल होगी जिसमें पाई चार्ट और डिस्क पर एक मिलती-जुलती PNG इमेज होगी।

## आवश्यकताएँ

* Java 17 या बाद का संस्करण स्थापित हो।
* The **GroupDocs.Viewer for Java** (या कोई संगत लाइब्रेरी जो `Document`, `Chart`, `ChartType`, और `ImageSaveOptions` क्लासेज़ प्रदान करती हो)।
* एक Maven या Gradle प्रोजेक्ट जहाँ आप लाइब्रेरी डिपेंडेंसी जोड़ सकें।
* एक इनपुट Word डॉक्यूमेंट (`input.docx`) जो किसी फ़ोल्डर में स्थित हो जिसे आप कोड से रेफ़र कर सकें।

यदि आप Maven का उपयोग कर रहे हैं, तो डिपेंडेंसी जोड़ें ( `VERSION` को नवीनतम रिलीज़ से बदलें):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Word में पाई चार्ट कैसे बनाएं

समाधान का मूल तीन कार्यों पर आधारित है:

1. स्रोत `.docx` फ़ाइल लोड करें।
2. **डेटा सीरीज़** को `PIE` प्रकार के नए `Chart` ऑब्जेक्ट में जोड़ें।
3. **चार्ट को PNG के रूप में सहेजें** ताकि आपको Word डॉक्यूमेंट के बगल में एक इमेज फ़ाइल मिल सके।

नीचे प्रत्येक चरण का विस्तृत विवरण दिया गया है, जिसके बाद आपको आवश्यक सटीक Java कोड है।

### चरण 1: स्रोत डॉक्यूमेंट लोड करें

आपको वह Word फ़ाइल खोलनी होगी जिसमें चार्ट होस्ट किया जाएगा। `Document` क्लास `.docx` सामग्री को मेमोरी में पढ़ती है।

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters*: डॉक्यूमेंट लोड करने से एक mutable मॉडल बनता है। सभी बाद के चार्ट ऑपरेशन्स इस इन‑मेमोरी प्रतिनिधित्व को संशोधित करते हैं, जिसे आप बाद में डिस्क पर सहेजते हैं।

### चरण 2: चार्ट में डेटा सीरीज़ जोड़ें

एक **pie chart** बनाने के लिए पहले `Chart` इंस्टेंस बनाते हैं। कंस्ट्रक्टर पैरेंट `Document` और चार्ट टाइप (`ChartType.PIE`) को प्राप्त करता है। चार्ट ऑब्जेक्ट बनने के बाद, आप इसे संख्यात्मक मानों और वैकल्पिक लेबल्स से भरते हैं।

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Why this matters*: `add` मेथड **डेटा सीरीज़ जोड़ता है** चार्ट में। `values` में प्रत्येक एंट्री पाई का एक स्लाइस बनती है, जबकि `categories` लेजेंड लेबल प्रदान करती हैं। आप कोई भी संख्या में पॉइंट्स दे सकते हैं; लाइब्रेरी स्वचालित रूप से स्लाइस एंगल्स की गणना करेगी।

### चरण 3: चार्ट को PNG के रूप में सहेजें

एक बार चार्ट डॉक्यूमेंट का हिस्सा बन जाने पर, आप विज़ुअल प्रतिनिधित्व को एक्सपोर्ट कर सकते हैं। अंतर्निहित चार्ट ऑब्जेक्ट पर `save` मेथड PNG फ़ाइल को फ़ाइल सिस्टम में लिखती है।

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Why this matters*: चार्ट को PNG के रूप में सहेजने से आपको एक रास्टर इमेज मिलती है जिसे वेब पेज, ईमेल या रिपोर्ट में एम्बेड किया जा सकता है बिना मूल Word फ़ाइल की आवश्यकता के। `ImageSaveOptions` ऑब्जेक्ट आपको फ़ॉर्मेट, रिज़ॉल्यूशन और अन्य एक्सपोर्ट सेटिंग्स को नियंत्रित करने देता है।

## Word में पाई चार्ट जेनरेट करना – लुक को कस्टमाइज़ करना

बुनियादी चरणों के अलावा, आप रंग, शीर्षक या डेटा लेबल को कस्टमाइज़ करना चाह सकते हैं। अधिकांश लाइब्रेरीज़ `ChartOptions` या समान ऑब्जेक्ट प्रदान करती हैं। यहाँ एक त्वरित उदाहरण है जो शीर्षक जोड़ता है और स्लाइस रंग बदलता है:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

ये कस्टमाइज़ेशन वैकल्पिक हैं लेकिन दर्शाते हैं कि आप कैसे **Word में पाई चार्ट जेनरेट** कर सकते हैं जो आपके ब्रांडिंग से मेल खाता हो।

## Word चार्ट को इमेज के रूप में सहेजें – वैकल्पिक दृष्टिकोण

यदि आपको केवल इमेज चाहिए और डॉक्यूमेंट के अंदर चार्ट नहीं चाहिए, तो आप Word फ़ाइल में चार्ट शेप डालने को छोड़ सकते हैं और चार्ट बनाने के बाद सीधे `save` मेथड को कॉल कर सकते हैं। कोड वही रहता है; आप बस उन चरणों को छोड़ देते हैं जो चार्ट को डॉक्यूमेंट बॉडी में जोड़ते हैं।

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

यह तकनीक उपयोगी है जब आप बैच प्रोसेस में कई चार्ट बनाते हैं और केवल PNG आउटपुट में रुचि रखते हैं।

## पूर्ण चलाने योग्य उदाहरण

निम्नलिखित क्लास को अपने प्रोजेक्ट में कॉपी करें, फ़ाइल पाथ्स को समायोजित करें, और इसे चलाएँ। प्रोग्राम करेगा:

1. `input.docx` लोड करें।
2. **पाई चार्ट बनाएं**, **डेटा सीरीज़ जोड़ें**, और इसे डॉक्यूमेंट में एम्बेड करें।
3. **चार्ट को PNG के रूप में सहेजें** (`radial.png`)।
4. संशोधित Word फ़ाइल को `output.docx` के रूप में सहेजें।



## अब आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for .NET का उपयोग करके Word स्कैटर चार्ट बनाएं](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}