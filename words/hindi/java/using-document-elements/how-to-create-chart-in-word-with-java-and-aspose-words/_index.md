---
category: general
date: 2026-09-24
description: Java का उपयोग करके Word में चार्ट बनाना सीखें, एक रेडियल चार्ट डालें,
  और Aspose.Words के साथ दस्तावेज़ को docx के रूप में सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: hi
lastmod: 2026-09-24
og_description: Java और Aspose.Words के साथ Word में चार्ट बनाएं। यह ट्यूटोरियल आपको
  दिखाता है कि रेडियल चार्ट कैसे जोड़ें, डेटा को कस्टमाइज़ करें, और दस्तावेज़ को docx
  के रूप में सहेजें।
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Java के साथ Word में चार्ट बनाएं – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: जावा और Aspose.Words के साथ Word में चार्ट कैसे बनाएं
url: /hi/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java और Aspose.Words के साथ Word में चार्ट कैसे बनाएं

यदि आपको Java एप्लिकेशन से **create chart in Word** बनाना है, तो यह गाइड आपको पूरी प्रक्रिया से गुज़राएगा। आप देखेंगे कि कैसे एक radial chart जोड़ें, वैकल्पिक रूप से उसकी series को populate करें, और अंत में Aspose.Words for Java लाइब्रेरी का उपयोग करके **save document as docx** करें।

Word फ़ाइल के अंदर विज़ुअल डेटा उत्पन्न करना रिपोर्टिंग, इनवॉइसिंग, या स्वचालित दस्तावेज़ निर्माण के लिए एक सामान्य आवश्यकता है। इस ट्यूटोरियल के अंत तक आप **create word document java** प्रोजेक्ट्स बना सकेंगे जो **add chart to Word** फ़ाइलों को बिना किसी मैनुअल एडिटिंग के जोड़ते हैं।

## आवश्यकताएँ

* Java Development Kit (JDK) 8 या नया।
* निर्भरता प्रबंधन के लिए Maven या Gradle।
* IntelliJ IDEA, Eclipse, या VS Code जैसे IDE।
* एक वैध Aspose.Words for Java लाइसेंस (फ्री ट्रायल विकास के लिए काम करता है)।

ये टूल्स आगे आने वाले कोड उदाहरणों के लिए आधार प्रदान करते हैं।

## चरण 1: Maven प्रोजेक्ट सेट अप करें

एक नया Maven प्रोजेक्ट बनाएं (या मौजूदा को अपडेट करें) और अपने `pom.xml` में Aspose.Words डिपेंडेंसी जोड़ें:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean install` चलाने से लाइब्रेरी डाउनलोड होती है और `Document`, `DocumentBuilder`, और `ChartType` जैसी क्लासेज़ क्लासपाथ पर उपलब्ध हो जाती हैं।

> **Pro tip:** लाइब्रेरी संस्करण को अद्यतित रखें। नई रिलीज़ में चार्ट प्रकार जोड़ते हैं और रेंडरिंग प्रदर्शन में सुधार करते हैं।

## चरण 2: नया Word दस्तावेज़ बनाएं

**create chart in Word** का पहला प्रोग्रामेटिक चरण एक खाली `Document` को इंस्टैंशिएट करना है। यह ऑब्जेक्ट पूरे `.docx` पैकेज का प्रतिनिधित्व करता है।

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` एक कर्सर की तरह काम करता है; यह वर्तमान इंसर्शन पॉइंट को जानता है और टेक्स्ट, टेबल, और चार्ट के लिए मेथड्स प्रदान करता है। इस बिंदु पर आपके पास **created word document java** शैली है – एक साफ़ कैनवास जो सामग्री के लिए तैयार है।

## चरण 3: एक radial chart डालें

Aspose.Words कई चार्ट प्रकारों का समर्थन करता है। **insert radial chart** करने के लिए, `insertChart` को `ChartType.RADIAL` के साथ कॉल करें। इस मेथड को चौड़ाई और ऊँचाई पॉइंट्स में भी चाहिए (1 point ≈ 1/72 inch)。

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

रिटर्न किया गया `Shape` ऑब्जेक्ट अंतर्निहित चार्ट ऑब्जेक्ट को रखता है। चार्ट स्वचालित रूप से 24.9° लेआउट के लिए ग्रेजुएशन रेंडर करता है, जो Word में radial charts का डिफ़ॉल्ट है।

### क्यों उपयोग करें radial chart?

एक radial chart डेटा को एक वृत्त के चारों ओर लपेटकर विज़ुअलाइज़ करता है, जिससे यह चक्रवाती पैटर्न (जैसे मासिक बिक्री, घड़ी‑मुख्य मीट्रिक) दिखाने के लिए आदर्श बनता है। वही API बार, पाई, या लाइन चार्ट भी डाल सकती है, लेकिन radial प्रकार अतिरिक्त स्टाइलिंग कोड के बिना एक विशिष्ट लुक जोड़ता है।

## चरण 4: (वैकल्पिक) चार्ट की series डेटा भरें

यदि आप चाहते हैं कि चार्ट वास्तविक मान दिखाए, तो आपको series और points जोड़ने होंगे। निम्नलिखित स्निपेट एक सिंगल series को तीन डेटा पॉइंट्स के साथ जोड़ता है:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

आप आवश्यकतानुसार `add` कॉल्स को दोहरा सकते हैं। Aspose.Words स्वचालित रूप से विज़ुअल प्रतिनिधित्व को अपडेट करता है, इसलिए आप देखेंगे कि radial slices नई मानों के अनुसार समायोजित होते हैं।

> **Common question:** *यदि मुझे डेटाबेस से डेटा बाइंड करना हो तो क्या करें?*  
> पंक्तियों को प्राप्त करें, उन पर लूप चलाएँ, और लूप के भीतर `series.getDataPoints().add(value, label)` कॉल करें। API थ्रेड‑सेफ़ है और आपके द्वारा प्रदान किए गए किसी भी `ResultSet` के साथ काम करता है।

## चरण 5: दस्तावेज़ को DOCX के रूप में सहेजें

जब चार्ट तैयार हो जाए, तो अंतिम चरण **save document as docx** है। `save` मेथड फ़ाइल एक्सटेंशन से आउटपुट फ़ॉर्मेट निर्धारित करता है।

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

जनरेट किया गया फ़ाइल एक पूरी तरह कार्यशील radial chart रखती है जिसे Microsoft Word, LibreOffice, या किसी भी व्यूअर में खोला जा सकता है जो DOCX फ़ॉर्मेट को सपोर्ट करता है। क्योंकि हमने `.docx` एक्सटेंशन का उपयोग किया, Word फ़ाइल को Open XML फ़ॉर्मेट में सहेजता है, जो Word दस्तावेज़ों का आधुनिक मानक है।

### परिणाम की पुष्टि

Word में `RadialChartDemo.docx` खोलें:

1. आपको एक सिंगल पेज दिखना चाहिए जिसमें केंद्रित radial chart हो।
2. यदि आपने series डेटा जोड़ा है, तो चार्ट चार स्लाइस दिखाता है जिनके लेबल Q1‑Q4 हैं।
3. चार्ट पर राइट‑क्लिक करें → **Edit Data** ताकि अंतर्निहित डेटा टेबल की पुष्टि हो सके।

यदि चार्ट खाली दिखे, तो दोबारा जांचें कि आपने series जोड़ने से पहले `chart.getChart()` कॉल किया है, और सुनिश्चित करें कि document builder का कर्सर उस स्थान पर स्थित है जहाँ आप चार्ट चाहते हैं।

## चरण 6: चार्ट के साथ काम करने के उन्नत टिप्स

| टिप | क्यों महत्वपूर्ण है |
|-----|-------------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | प्रत्येक तत्व को मैन्युअली फॉर्मेट किए बिना विज़ुअल कंसिस्टेंसी को सुधारता है। |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | पेज लेआउट के आधार पर चार्ट आकार को फाइन‑ट्यून करने की अनुमति देता है। |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | उन पाठकों को संदर्भ देता है जो दस्तावेज़ को बिना आसपास के टेक्स्ट के देखते हैं। |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | वितरण के लिए एक नॉन‑एडिटेबल संस्करण की आवश्यकता होने पर उपयोगी है। |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | प्रोडक्शन बिल्ड्स में इवैल्यूएशन वाटरमार्क को रोकता है। |

ये सुधार वैकल्पिक हैं लेकिन यह दर्शाते हैं कि आप **add chart to Word** सीखने के बाद चार्ट को और कैसे कस्टमाइज़ कर सकते हैं।

## निष्कर्ष

अब आपके पास एक पूर्ण, स्व-निहित उदाहरण है जो दिखाता है कि Java का उपयोग करके **create chart in Word** कैसे करें, **insert radial chart**, वैकल्पिक रूप से डेटा से भरें, और **save document as docx**। वही पैटर्न अन्य चार्ट प्रकारों के लिए भी काम करता है, इसलिए आप इस ट्यूटोरियल को आवश्यकता अनुसार बार, लाइन, या पाई चार्ट तक विस्तारित कर सकते हैं।

अगले आप खोज सकते हैं:

* **create word document java** प्रोजेक्ट्स जो टेबल, इमेज, और कई चार्ट को संयोजित करते हैं।
* **save document as docx** को **save document as pdf** के साथ मिलाकर मल्टी‑फ़ॉर्मेट रिपोर्टिंग के लिए उपयोग करना।
* अपने चार्ट्स में REST APIs या डेटाबेस से डायनामिक डेटा जोड़ना।

स्टाइलिंग विकल्पों, चार्ट डायमेंशन, और डेटा स्रोतों के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Word दस्तावेज़ Java बनाएं – शैडो इफ़ेक्ट के साथ रेक्टैंगल शेप जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}