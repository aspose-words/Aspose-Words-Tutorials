---
category: general
date: 2026-09-27
description: जावा का उपयोग करके वर्ड दस्तावेज़ में पाई चार्ट कैसे डालें, वर्ड में
  पाई चार्ट बनाएं, और स्पष्ट डेटा अंतर्दृष्टि के लिए पाई चार्ट पर प्रतिशत दिखाएँ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: hi
lastmod: 2026-09-27
og_description: जावा के साथ वर्ड दस्तावेज़ में पाई चार्ट कैसे डालें। यह गाइड आपको
  दिखाता है कि वर्ड में पाई चार्ट कैसे बनाएं, पाई चार्ट पर प्रतिशत कैसे दिखाएं, और
  लीडर लाइन्स कैसे जोड़ें।
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: जावा का उपयोग करके वर्ड दस्तावेज़ में पाई चार्ट कैसे डालें
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: जावा का उपयोग करके वर्ड दस्तावेज़ में पाई चार्ट कैसे डालें
url: /hi/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java का उपयोग करके Word दस्तावेज़ में पाई चार्ट कैसे डालें

यदि आपको Word फ़ाइल में **how to insert pie chart** डालने की आवश्यकता है, तो यह गाइड आपको पूरी प्रक्रिया के माध्यम से ले जाता है। आप देखेंगे कि **create pie chart in Word** कैसे किया जाता है, प्रत्येक स्लाइस पर प्रतिशत कैसे दिखाए जाते हैं, और एक परिष्कृत लुक के लिए लीडर लाइन्स कैसे जोड़ी जाती हैं।

Word ऑटोमेशन अक्सर भारी महसूस होता है, लेकिन Aspose.Words for Java के साथ आप प्रोग्रामेटिक रूप से पूरी तरह फ़ॉर्मेटेड दस्तावेज़ बना सकते हैं। इस ट्यूटोरियल के अंत तक आपके पास एक चलाने योग्य Java स्निपेट होगा जो एक स्टाइल्ड पाई चार्ट वाला Word दस्तावेज़ उत्पन्न करता है।

## आवश्यकताएँ

- Java 17 या बाद का संस्करण स्थापित हो
- निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle
- Aspose.Words for Java (संस्करण 23.11 या नया) आपके प्रोजेक्ट में जोड़ा गया हो
- Java सिंटैक्स की बुनियादी समझ

आपको चार्ट API के साथ कोई पूर्व अनुभव की आवश्यकता नहीं है; नीचे दिए गए चरण प्रोजेक्ट सेटअप से लेकर अंतिम आउटपुट तक सब कुछ कवर करते हैं।

## चरण 1: Maven निर्भरता सेट करें

`pom.xml` में Aspose.Words लाइब्रेरी जोड़ें। यह एकल निर्भरता आपको `Document`, `DocumentBuilder`, और चार्ट क्लासेज़ तक पहुँच देती है।

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

यदि आप Gradle का उपयोग करते हैं, तो समकक्ष यह है:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** बग फिक्स और नई चार्ट सुविधाओं का लाभ उठाने के लिए नवीनतम स्थिर संस्करण का उपयोग करें।

## चरण 2: नया दस्तावेज़ और बिल्डर बनाएं

`Document` ऑब्जेक्ट Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` आपको सामग्री डालने की अनुमति देता है। यह **add chart to word document** का आधार है।

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

अब बिल्डर दस्तावेज़ में कहीं भी ऑब्जेक्ट्स रखने के लिए तैयार है।

## चरण 3: पाई चार्ट डालें

Aspose.Words कई चार्ट प्रकारों का समर्थन करता है; हम `ChartType.PIE` चुनते हैं। आकार पॉइंट्स में व्यक्त किया जाता है (1 पॉइंट = 1/72 इंच)।

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

इस चरण में चार्ट में डिफ़ॉल्ट डेटा सीरीज़ प्लेसहोल्डर मानों के साथ होती है। यदि आवश्यक हो तो आप बाद में उन मानों को बदल सकते हैं।

## चरण 4: चार्ट सीरीज़ तक पहुँचें

पाई चार्ट में एक ही सीरीज़ होती है जो स्लाइस मानों को रखती है। फ़ॉर्मेटिंग लागू करने के लिए इसे प्राप्त करें।

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## चरण 5: पहली स्लाइस को एक्सप्लोड करें

स्लाइस को एक्सप्लोड करने से किसी विशेष डेटा पॉइंट पर ध्यान आकर्षित होता है। यह एक सामान्य विज़ुअल संकेत है जब आप किसी प्रमुख मीट्रिक को हाइलाइट करना चाहते हैं।

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## चरण 6: प्रत्येक स्लाइस पर प्रतिशत दिखाएँ

चार्ट पर सीधे प्रतिशत दिखाने से डेटा अंतर्दृष्टि बेहतर होती है। यह **show percentages on pie chart** आवश्यकता को पूरा करता है।

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## चरण 7: स्पष्ट लेबल के लिए लीडर लाइन्स जोड़ें

लीडर लाइन्स स्लाइस लेबल को उनके संबंधित सेक्शन से जोड़ती हैं, जिससे अस्पष्टता समाप्त होती है। यह **how to add leader lines** को पूरा करती हैं।

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## चरण 8: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप किसी भी फ़ोल्डर को चुन सकते हैं जहाँ आपके पास लिखने की अनुमति हो।

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

प्रोग्राम चलाने से `output/PieFormatted.docx` बनता है। फ़ाइल को Microsoft Word में खोलें, और आप एक पाई चार्ट देखेंगे जहाँ:

- पहली स्लाइस एक्सप्लोड की गई है।
- प्रत्येक स्लाइस अपना प्रतिशत मान दिखाती है।
- लीडर लाइन्स प्रतिशत से संबंधित स्लाइस की ओर इंगित करती हैं।

### अपेक्षित आउटपुट

![Word में फ़ॉर्मेटेड पाई चार्ट](/images/pie-formatted.png){: .center-image alt="Word दस्तावेज़ में डाला गया फ़ॉर्मेटेड पाई चार्ट"}

स्क्रीनशॉट (alt टेक्स्ट मुख्य कीवर्ड का उपयोग करता है) अंतिम रूप को दर्शाता है: एक साफ़, डेटा‑ड्रिवेन पाई चार्ट जो रिपोर्ट, प्रस्ताव या डैशबोर्ड के लिए तैयार है।

## सामान्य विविधताएँ और किनारी मामलों

### स्लाइस मान बदलना

यदि आपको कस्टम डेटा चाहिए, तो डिफ़ॉल्ट सीरीज़ मानों को बदलें:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### कई सीरीज़ (डोनट चार्ट)

जबकि एक साधा पाई चार्ट एक सीरीज़ रखता है, Aspose.Words कई सीरीज़ वाले डोनट चार्ट का भी समर्थन करता है। `ChartType.PIE` को `ChartType.DONUT` में बदलें और सीरीज़‑कॉन्फ़िगरेशन चरणों को दोहराएँ।

### PDF में निर्यात करना

यदि आपके डाउनस्ट्रीम वर्कफ़्लो को PDF चाहिए, तो चार्ट बन जाने के बाद `doc.save("output/PieFormatted.pdf");` कॉल करें। विज़ुअल लेआउट समान रहता है।

## पूर्ण स्रोत सूची

नीचे पूर्ण, स्वतंत्र Java फ़ाइल है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं।

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

`mvn compile exec:java -Dexec.mainClass=PieChartExample` (या समकक्ष Gradle कमांड) के साथ प्रोग्राम को कंपाइल और चलाएँ। उत्पन्न Word फ़ाइल में पूरी तरह फ़ॉर्मेटेड पाई चार्ट होगा।

## निष्कर्ष

अब आप जानते हैं कि Java का उपयोग करके Word दस्तावेज़ में **how to insert pie chart** कैसे डालें, **create pie chart in Word** कैसे बनाएं, **show percentages on pie chart** कैसे दिखाएँ, और लीडर लाइन्स के साथ **add chart to word document** कैसे जोड़ें। पूरा उदाहरण प्रत्येक चरण को दर्शाता है, बताता है कि कोड इस तरह लिखा गया है, और अनुकूलन के लिए टिप्स प्रदान करता है।

अगले चरण में, आप देख सकते हैं:

- कस्टम फ़ॉन्ट के साथ डेटा लेबल जोड़ना (**show percentages on pie chart** विविधताएँ)
- एक ही दस्तावेज़ में कई चार्ट संयोजित करना (**add chart to word document** उपयोग केस)
- टेबल और चार्ट के साथ रिपोर्ट जनरेशन को स्वचालित करना

रंगों, स्लाइस क्रम, या PDF में निर्यात के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Word दस्तावेज़ में चार्ट एक्सिस छिपाएँ](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Aspose.Words for .NET का उपयोग करके Word में लाइन चार्ट बनाएं](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}