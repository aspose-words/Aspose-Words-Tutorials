---
category: general
date: 2026-10-10
description: Word फ़ाइल में चार्ट को घुमाना सीखें और Word में चार्ट को संशोधित करके
  डोनट चार्ट का आकार बदलें, एक पूर्ण Java उदाहरण के साथ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: hi
lastmod: 2026-10-10
og_description: Aspose.Words for Java का उपयोग करके Word फ़ाइल में चार्ट को कैसे घुमाएँ
  और Word में चार्ट को संशोधित करके डोनट चार्ट का आकार बदलें।
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Word दस्तावेज़ में चार्ट को घुमाने का तरीका – चरण‑दर‑चरण जावा गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words का उपयोग करके Word दस्तावेज़ में चार्ट को कैसे घुमाएँ
url: /hi/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words का उपयोग करके Word दस्तावेज़ में चार्ट को कैसे घुमाएँ

यदि आपको Microsoft Word फ़ाइल के भीतर **how to rotate chart** करने की आवश्यकता है, तो यह गाइड आपको सटीक चरण दिखाता है। आप यह भी सीखेंगे कि **modify chart in Word** कैसे करें ताकि **change doughnut chart size** को अपने Java कोड से बाहर निकले बिना किया जा सके।

Word ऑटोमेशन अक्सर असंबद्ध API कॉल्स की श्रृंखला जैसा महसूस होता है, लेकिन Aspose.Words के साथ आप चार्ट को किसी अन्य दस्तावेज़ नोड की तरह संभाल सकते हैं। इस ट्यूटोरियल के अंत तक आपके पास एक चलाने योग्य प्रोग्राम होगा जो मौजूदा `.docx` को लोड करता है, एक doughnut चार्ट को 45° घुमाता है, छेद को त्रिज्या के 50 % तक घटाता है, और परिणाम को नई फ़ाइल के रूप में सहेजता है।

## आवश्यकताएँ

* Java 17 या उससे नया स्थापित हो।
* निर्भरताओं को प्रबंधित करने के लिए Maven (या Gradle)।
* `input.docx` नामक इनपुट Word दस्तावेज़ जिसमें पहले से ही एक doughnut चार्ट हो।
* एक वैध Aspose.Words for Java लाइसेंस (या मूल्यांकन मोड का उपयोग करें)।

## चरण 1: Maven प्रोजेक्ट सेट अप करें

एक नया Maven प्रोजेक्ट बनाएं या निम्नलिखित निर्भरता को अपने मौजूदा `pom.xml` में जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

`mvn clean install` चलाने से लाइब्रेरी डाउनलोड होगी और क्लासेस आपके क्लासपाथ पर उपलब्ध हो जाएँगी।

## चरण 2: उस Word दस्तावेज़ को लोड करें जिसमें चार्ट हो

पहला ऑपरेशन मौजूदा दस्तावेज़ को खोलना है। `Document` क्लास पूरे फ़ाइल का प्रतिनिधित्व करती है।

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

फ़ाइल को लोड करने से यह **बदलती नहीं** है; यह केवल एक इन‑मेमोरी प्रतिनिधित्व बनाता है जिसे आप क्वेरी और संपादित कर सकते हैं।

## चरण 3: नेविगेशन के लिए DocumentBuilder बनाएं

`DocumentBuilder` आपको दस्तावेज़ ट्री में चलने के लिए कर्सर‑जैसा API देता है। हम इसका उपयोग पहले चार्ट शेप को खोजने के लिए करेंगे।

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर दस्तावेज़ की शुरुआत में शुरू होता है, लेकिन आवश्यकता पड़ने पर आप इसे बाद में किसी भी नोड पर ले जा सकते हैं।

## चरण 4: पहला चार्ट शेप प्राप्त करें

चार्ट `Shape` नोड्स के रूप में संग्रहीत होते हैं। `NodeType.SHAPE` प्रकार के चाइल्ड नोड्स को फ़िल्टर करके हम चार्ट ऑब्जेक्ट निकाल सकते हैं।

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

यदि दस्तावेज़ में कई चार्ट हैं, तो आप `getChildNodes` पर इटरेट कर सकते हैं और कास्ट करने से पहले प्रत्येक `Shape` के लिए `hasChart()` जांच सकते हैं।

## चरण 5: चार्ट को घुमाएँ (how to rotate chart)

एक doughnut चार्ट मूलतः एक पाई चार्ट है जिसमें छेद होता है। इसे घुमाने से पहले स्लाइस का प्रारंभिक कोण बदलता है।

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle` मेथड डिग्री दर्शाने वाले डबल मान की अपेक्षा करता है। सकारात्मक मान घड़ी की दिशा में घुमाते हैं, जबकि नकारात्मक मान विपरीत दिशा में।

## चरण 6: doughnut छेद का आकार बदलें (change doughnut chart size)

छेद का आकार चार्ट की त्रिज्या के अंश के रूप में व्यक्त किया जाता है। `0.5` मान का अर्थ है कि छेद कुल त्रिज्या का 50 % लेता है।

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tip:** वैध सीमा `0.0` (कोई छेद नहीं, अर्थात सामान्य पाई) से `0.9` (बहुत पतली रिंग) तक है। इस सीमा से बाहर के मान `IllegalArgumentException` उत्पन्न करेंगे।

## चरण 7: संशोधित दस्तावेज़ को सहेजें

अंत में, परिवर्तन को डिस्क पर वापस लिखें।

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

जब आप Microsoft Word में `DoughnutFormatted.docx` खोलेंगे, तो आप देखेंगे कि doughnut चार्ट 45° घुमाया गया है और छेद अपने मूल आकार का आधा रह गया है।

## पूरा, चलाने योग्य उदाहरण

सभी भागों को मिलाकर, यहाँ पूरा प्रोग्राम है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### अपेक्षित आउटपुट

प्रोग्राम चलाने पर यह प्रिंट करता है:

```
Chart rotated and doughnut size changed successfully.
```

`DoughnutFormatted.docx` खोलने पर एक doughnut चार्ट दिखेगा जिसका पहला स्लाइस 45° स्थिति से शुरू होता है और जिसकी आंतरिक त्रिज्या बाहरी त्रिज्या का आधा है।

## सामान्य विविधताएँ और किनारी मामलों

| Situation | What to adjust | Why it matters |
|-----------|----------------|----------------|
| **एकाधिक चार्ट** | `getChildNodes(NodeType.SHAPE, true)` पर लूप करें और प्रत्येक के लिए `shape.hasChart()` जांचें | सुनिश्चित करता है कि आप पहले वाले के बजाय इच्छित चार्ट को संशोधित करें |
| **बार या लाइन चार्ट** | `setStartAngle` लागू नहीं होता; अन्य दृश्य समायोजनों के लिए `chart.getSeries().get(0).setFillFormat(...)` उपयोग करें | सभी चार्ट प्रकार घुमाव का समर्थन नहीं करते; doughnut/पाई चार्ट ही एक प्रारंभिक कोण रखते हैं |
| **छेद के बिना चार्ट** | `setDoughnutHoleSize` को छोड़ें या पहले `chart.setChartType(ChartType.DONUT)` के माध्यम से चार्ट प्रकार को doughnut में बदलें | non‑doughnut चार्ट पर छेद का आकार बदलने से अपवाद उत्पन्न होता है |
| **बड़े दस्तावेज़** | लक्षित नेविगेशन के लिए `DocumentBuilder.moveToDocumentStart()` और `builder.moveToNode(chartShape)` का उपयोग करें | असंबंधित नोड्स की पूरी यात्रा से बचकर प्रदर्शन में सुधार करता है |

## विश्वसनीय चार्ट हेरफेर के लिए प्रो टिप्स

* **Cache the chart reference** – यदि आप कई गुणों को संशोधित करने की योजना बनाते हैं, तो `chartShape.getChart()` को बार‑बार कॉल करने के बजाय एक स्थानीय `Chart` वेरिएबल रखें।
* **Validate input values** – `setStartAngle` या `setDoughnutHoleSize` को कॉल करने से पहले, रेंज सत्यापित करें ताकि रन‑टाइम त्रुटियों से बचा जा सके।
* **Use a license** – मूल्यांकन मोड पहली पृष्ठ पर वॉटरमार्क डालता है। लाइसेंस लागू करने से (`License license = new License(); license.setLicense("Aspose.Words.lic");`) यह हट जाता है।

## अगले कदम

अब जब आप **how to rotate chart** और **change doughnut chart size** जानते हैं, तो आप अन्य **modify chart in Word** परिदृश्यों का अन्वेषण कर सकते हैं:

* `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())` का उपयोग करके स्लाइस के रंग बदलें।
* `chart.getSeries().get(0).setHasDataLabel(true)` कॉल करके डेटा लेबल जोड़ें।
* `chart.toImage(300, 300, ImageType.PNG)` का उपयोग करके चार्ट को इमेज के रूप में एक्सपोर्ट करें।

इनमें से प्रत्येक विस्तार समान पैटर्न का पालन करता है: `Chart` ऑब्जेक्ट प्राप्त करें, उपयुक्त सेट्टर को कॉल करें, और दस्तावेज़ को सहेजें।

**आपने अभी Java का उपयोग करके Word में doughnut चार्ट को घुमाने और आकार बदलने में महारत हासिल कर ली है।** कोड को अन्य चार्ट प्रकारों के लिए अनुकूलित करने, इसे बड़े दस्तावेज़‑जनरेशन पाइपलाइन में एकीकृत करने, या PowerPoint ऑटोमेशन के लिए Aspose.Slides के साथ संयोजित करने में संकोच न करें। कोडिंग का आनंद लें!

## अगले क्या सीखें?

निम्नलिखित ट्यूटोरियल उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}