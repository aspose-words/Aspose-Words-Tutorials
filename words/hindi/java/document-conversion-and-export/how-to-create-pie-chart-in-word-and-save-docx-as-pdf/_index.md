---
category: general
date: 2026-11-15
description: जावा का उपयोग करके वर्ड दस्तावेज़ में पाई चार्ट बनाना और डॉक्स को पीडीएफ
  के रूप में सहेजना सीखें। यह गाइड वर्ड को पीडीएफ में बदलने और चार्ट जोड़ने के बारे
  में भी बताता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: hi
lastmod: 2026-11-15
og_description: Java का उपयोग करके Word फ़ाइल में पाई चार्ट बनाएं और docx को PDF के
  रूप में सहेजें। Word को PDF में बदलने और चार्ट जोड़ने के लिए इस चरण‑दर‑चरण ट्यूटोरियल
  का पालन करें।
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Word में पाई चार्ट बनाएं और docx को PDF के रूप में सहेजें – Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Word में पाई चार्ट कैसे बनाएं और docx को PDF के रूप में सहेजें
url: /hi/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में पाई चार्ट कैसे बनाएं और docx को PDF के रूप में सहेजें

यदि आपको **create pie chart** Word दस्तावेज़ के भीतर बनाना है और फिर **save docx as PDF** करना है, तो यह ट्यूटोरियल आपको बिल्कुल वही दिखाता है। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो .docx फ़ाइल को PDF में बदलता है जबकि पाई चार्ट को एम्बेड करता है, ताकि आप “how to add chart” का उत्तर बिखरे हुए स्निपेट्स की खोज किए बिना दे सकें।

इस गाइड में आप सीखेंगे:

* मौजूदा *.docx* लोड करें (या शून्य से शुरू करें)  
* Aspose.Words for Java का उपयोग करके **create pie chart** बनाएं और डेटा भरें  
* **Save docx as PDF** चार्ट को सही ढंग से रेंडर करते हुए सहेजें  
* जब चार्ट शामिल हों तो **convert word to pdf** के नुअन्सेज़ को समझें  

ये चरण Aspose.Words 2024‑x.x और Java 17 के साथ काम करते हैं, लेकिन अवधारणाएँ किसी भी लाइब्रेरी पर लागू होती हैं जो Word चार्ट मैनिपुलेशन को सपोर्ट करती है।

## आवश्यकताएँ

| आवश्यकता | क्यों महत्वपूर्ण है |
|-------------|----------------|
| Java 17 (or later) | Latest Aspose.Words JAR द्वारा आवश्यक |
| Maven or Gradle build tool | डिपेंडेंसी प्रबंधन को सरल बनाता है |
| Aspose.Words for Java (latest version) | `Document`, `Chart`, और `ChartType` क्लास प्रदान करता है |
| An input **.docx** file (or a blank document) | चार्ट इस फ़ाइल में डाला जाएगा |

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## चरण 1: Word दस्तावेज़ लोड करें (या नया बनाएं)

पहला कार्य `Document` इंस्टेंस प्राप्त करना है। यदि आपके पास पहले से टेम्पलेट है, तो उसका पाथ पास करें; अन्यथा एक खाली दस्तावेज़ बनाएं।

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* `Document` ऑब्जेक्ट सभी Word कंटेंट, जिसमें चार्ट भी शामिल हैं, का कंटेनर है। मौजूदा फ़ाइल लोड करने से आप आसपास के टेक्स्ट और स्टाइल को संरक्षित रख सकते हैं जबकि नया विज़ुअल एलिमेंट जोड़ते हैं।

## चरण 2: **Create pie chart** – “how to create chart” का मूल

अब हम `Chart` ऑब्जेक्ट को `ChartType.PIE` के साथ इंस्टैंशिएट करते हैं। यह स्वचालित रूप से एक पाई चार्ट प्लेसहोल्डर बनाता है जिसे बाद में डेटा से भरा जा सकता है।

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` Aspose.Words को पाई‑चार्ट टेम्पलेट उपयोग करने के लिए बताता है। चार्ट को दस्तावेज़ के बॉडी में जोड़ा जाता है, इसलिए यह वहीँ दिखाई देगा जहाँ आपको चाहिए। यह एक ही कॉल में “how to add chart” की आवश्यकता को पूरा करता है।

## चरण 3: चार्ट को डेटा से भरें – “how to add chart” का उत्तर डेटा के साथ

पाई चार्ट का कोई मतलब नहीं होता जब तक उसमें सीरीज़ डेटा न हो। `Series` कलेक्शन का उपयोग करके श्रेणियाँ और मान जोड़ें।

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: `add` के प्रत्येक कॉल से पाई का एक स्लाइस बनता है। पहला आर्ग्युमेंट लेबल है, दूसरा न्यूमेरिक वैल्यू। आप इन्हें डेटाबेस या CSV फ़ाइल से डायनामिक डेटा से बदल सकते हैं।

### वैकल्पिक: रूप को अनुकूलित करें (आवश्यक नहीं लेकिन उपयोगी)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

ये ट्यूनिंग दिखाती हैं कि आप **how to create chart** को प्रोफेशनल लुक के साथ कैसे बना सकते हैं, बिना Java कोड छोड़े।

## चरण 4: **Save docx as PDF** – “convert word to pdf” का अंतिम भाग

एक बार चार्ट एम्बेड हो जाने पर, दस्तावेज़ को PDF में एक्सपोर्ट करें। Aspose.Words चार्ट को वेक्टर ग्राफिक के रूप में रेंडर करता है, जिससे क्वालिटी बनी रहती है।

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: `save` मेथड स्वचालित रूप से Word फ़ाइल को PDF में बदल देता है, चार्ट रास्टराइज़ेशन, फ़ॉन्ट एम्बेडिंग, और पेज लेआउट को संभालते हुए। यह **save docx as pdf** लक्ष्य को पूरा करता है और चार्ट मौजूद होने पर **convert word to pdf** का विश्वसनीय तरीका दर्शाता है।

### अपेक्षित आउटपुट

प्रोग्राम चलाने से `output.pdf` बनता है जिसमें शामिल है:

* `input.docx` की मूल सामग्री (यदि कोई हो)  
* *Sales Distribution Q1* शीर्षक वाला पूरी तरह रेंडर किया गया पाई चार्ट  
* डेटा से मेल खाने वाले सटीक स्लाइस प्रतिशत (40 %, 30 %, 30 %)

PDF को किसी भी व्यूअर में खोलें और आपको एक स्पष्ट पाई चार्ट दिखना चाहिए, जो Word फ़ाइल में जैसा दिखता है वैसा ही होगा।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | कारण | समाधान |
|-------|-------|-----|
| Chart appears blank in PDF | फ़ॉन्ट या चार्ट रेंडरिंग सेटिंग्स गायब | सुनिश्चित करें कि आप नवीनतम Aspose.Words संस्करण उपयोग कर रहे हैं; यह आवश्यक रेंडरिंग लाइब्रेरीज़ को बंडल करता है। |
| Data values are rounded incorrectly | बड़े नंबरों के साथ इंटीजर वैल्यू उपयोग करना | `double` वैल्यू प्रदान करें या सीरीज़ में जोड़ने से पहले नंबरों को स्केल करें। |
| Output PDF is huge | हाई DPI पर इमेजेज एम्बेडेड | यदि आप इमेजेज भी एम्बेड कर रहे हैं तो `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` सेट करें। |
| “convert word to pdf” throws `UnsupportedOperationException` | पुराना Java संस्करण (< 11) उपयोग करना | Java 17 या बाद के संस्करण में अपग्रेड करें, जो Aspose.Words 24.x की आवश्यकता है। |

## प्रो टिप: चार्ट निर्माण लॉजिक को पुन: उपयोग करें

यदि आपको एक ही दस्तावेज़ में कई चार्ट जोड़ने हैं, तो चार्ट‑बिल्डिंग कोड को एक हेल्पर मेथड में निकालें:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

अब आप प्रत्येक डेटा सेट के लिए `doc.getFirstSection().getBody().appendChild(createPieChart(...));` कॉल कर सकते हैं, जिससे आपका कोड DRY (Don’t Repeat Yourself) बना रहे।

## निष्कर्ष

आप अब जानते हैं कि Java का उपयोग करके Word दस्तावेज़ के भीतर **create pie chart** कैसे बनाएं, उसे डेटा से भरें, और **save docx as PDF** कैसे करें। यह एंड‑टू‑एंड उदाहरण पूरे **convert word to pdf** वर्कफ़्लो को कवर करता है, **how to add chart** का उत्तर देता है, और प्रोग्रामेटिक रूप से **how to create chart** को दर्शाता है।  

अब आप आगे खोज सकते हैं:

* बार या लाइन चार्ट जोड़ना (`ChartType.BAR`, `ChartType.LINE`) – एक और **how to create chart** परिदृश्य।  
* PNG या HTML जैसे अन्य फ़ॉर्मैट में एक्सपोर्ट करना (`SaveFormat.PNG`, `SaveFormat.HTML`)।  
* चार्ट डालने से पहले टेबल या प्लेसहोल्डर के साथ इनपुट दस्तावेज़ को डायनामिक रूप से जनरेट करना।

विभिन्न डेटा सेट, स्टाइलिंग विकल्प, या यहाँ तक कि प्रति पेज कई चार्ट एम्बेड करने के साथ प्रयोग करने में संकोच न करें। Happy coding!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Java का उपयोग करके Word दस्तावेज़ में पाई चार्ट कैसे डालें](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Java में Word को PDF के रूप में सहेजें और एक्सेसिबल PDF बनाएं](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Java और Aspose.Words के साथ Word में चार्ट कैसे बनाएं](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}