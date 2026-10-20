---
category: general
date: 2026-09-11
description: Aspose.Words for Java के साथ डोनट चार्ट को संपादित करने के बाद Word दस्तावेज़
  को सहेजें। डोनट होल का आकार बदलना, डोनट चार्ट को घुमाना, और डोनट चार्ट की विशेषताओं
  को संपादित करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: hi
lastmod: 2026-09-11
og_description: Aspose.Words for Java का उपयोग करके डोनट चार्ट को संपादित करने के
  बाद Word दस्तावेज़ को सहेजें। यह ट्यूटोरियल दिखाता है कि डोनट होल का आकार कैसे बदलें,
  डोनट चार्ट को घुमाएँ, और चार्ट की उपस्थिति को कस्टमाइज़ करें।
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: डोनट चार्ट को संपादित करने के बाद वर्ड दस्तावेज़ सहेजें – जावा गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: जावा में डोनट चार्ट को संपादित करने के बाद वर्ड दस्तावेज़ को सहेजें
url: /hi/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में डोनट चार्ट को संपादित करने के बाद Word दस्तावेज़ को सहेजें

यदि आपको एक कस्टमाइज़्ड डोनट चार्ट वाला **Word दस्तावेज़ सहेजें** है, तो यह गाइड आपको बिल्कुल बताता है कैसे। केवल कुछ ही जावा लाइनों में आप डोनट होल बदल सकते हैं, डोनट चार्ट को घुमा सकते हैं, और फिर परिणाम को डिस्क पर लिख सकते हैं।

आपको एक पूर्ण, चलाने योग्य उदाहरण मिलेगा जो Aspose.Words for Java का उपयोग करता है, साथ ही कई चार्ट्स को संभालने, नोड प्रकारों की जाँच करने, और सामान्य समस्याओं से बचने के टिप्स भी मिलेंगे। कोई बाहरी संदर्भ आवश्यक नहीं है—जो कुछ भी चाहिए वह सब शामिल है।

## आवश्यकताएँ

- Java 17 या नया स्थापित हो
- निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle
- Aspose.Words for Java (संस्करण 23.9 या बाद का) आपके प्रोजेक्ट में जोड़ा गया  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- एक Word फ़ाइल (`input.docx`) जिसमें एकल डोनट चार्ट हो

## चरण 1: Word दस्तावेज़ लोड करें

पहला चरण स्रोत फ़ाइल को खोलना है। यह चरण आवश्यक है क्योंकि सभी बाद के ऑपरेशन इन‑मेमोरी `Document` ऑब्जेक्ट पर काम करते हैं।

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why?** दस्तावेज़ को लोड करने से एक DOM प्रतिनिधित्व बनता है जो आपको शैप्स, टेबल्स और चार्ट्स को ट्रैवर्स करने की अनुमति देता है। यदि फ़ाइल नहीं खुल पाती, तो Aspose.Words एक अपवाद फेंकता है, जिससे आपको तुरंत पता चल जाता है कि पथ गलत है।

## चरण 2: डोनट चार्ट आकार (shape) खोजें

एक चार्ट `Shape` नोड के अंदर संग्रहीत होता है। हम पहले उस शैप को प्राप्त करते हैं जो चार्ट होस्ट करता है और उसके रेंडरर को `Chart` में कास्ट करते हैं।

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Why?** `isChart()` की जाँच करने से `ClassCastException` से बचा जा सकता है जब दस्तावेज़ में चार्ट से पहले छवियाँ या अन्य शैप्स हों। यह मिश्रित सामग्री वाले दस्तावेज़ों के लिए कोड को मजबूत बनाता है।

## चरण 3: डोनट होल का आकार बदलें  

अब हम डोनट होल को संपादित करते हैं। `setHoleSize` मेथड चार्ट त्रिज्या का प्रतिशत (10 – 90) अपेक्षित करता है।

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Why?** डोनट होल (`change doughnut hole` / `change chart hole size`) बदलने से आप केंद्रीय क्षेत्र को ज़्यादा या कम प्रमुख बना सकते हैं। 10‑90 % के बाहर के मान API द्वारा अनदेखे रहेंगे।

## चरण 4: डोनट चार्ट को घुमाएँ  

पहले स्लाइस की शुरुआत को नियंत्रित करने के लिए, पहला‑स्लाइस एंगल सेट करें। यह प्रभावी रूप से **डोनट चार्ट घुमाएँ** करता है।

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Why?** चार्ट को घुमाना उपयोगी होता है जब आप चाहते हैं कि कोई विशेष स्लाइस शीर्ष पर दिखे या किसी डिज़ाइन स्पेसिफिकेशन से मेल खाए।

## चरण 5: अपडेटेड दस्तावेज़ सहेजें  

अंत में, बदलावों को नई फ़ाइल में लिखें। यही वह क्षण है जब आप **Word दस्तावेज़ सहेजें** करते हैं जिसमें संपादित चार्ट हो।

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Expected result:** `output.docx` में मूल सामग्री रहती है, लेकिन डोनट चार्ट का होल अब 30 % है और उसका पहला स्लाइस 45 ° पर शुरू होता है। Microsoft Word में फ़ाइल खोलने पर परिवर्तित चार्ट दिखेगा।

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी इम्पोर्ट्स और एरर हैंडलिंग शामिल है जो **डोनट चार्ट संपादित करें** और **Word दस्तावेज़ सहेजें** को सुरक्षित रूप से करने के लिए आवश्यक हैं।

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### अपेक्षित आउटपुट

जब आप `output.docx` खोलते हैं:

- डोनट चार्ट का केंद्रीय होल लगभग चार्ट त्रिज्या के एक‑तिहाई भाग को घेरता है।  
- पहला स्लाइस 45‑डिग्री स्थिति से शुरू होता है, जिससे पूरा चार्ट घड़ी की दिशा में शिफ्ट हो जाता है।  

दोनों दृश्य परिवर्तन तुरंत Word में परिलक्षित होते हैं।

## सामान्य विविधताएँ और किनारी मामलों

| स्थिति | कैसे संभालें |
|-----------|----------------|
| **एकाधिक चार्ट** | `doc.getChildNodes(NodeType.SHAPE, true)` पर इटररेट करें और `shape.isChart()` को फ़िल्टर करें; प्रत्येक `Chart` पर `setHoleSize` / `setFirstSliceAngle` लागू करें। |
| **चार्ट डोनट नहीं है** | `chart.getType()` जाँचें; केवल तभी `setHoleSize` कॉल करें जब `chart.getType() == ChartType.DOUGHNUT` हो। |
| **होल साइज को डायनामिक रूप से बदलने की आवश्यकता** | डेटा वैल्यूज़ के आधार पर इच्छित प्रतिशत गणना करें, फिर `setHoleSize(computedValue)` कॉल करें। |
| **स्ट्रीम में सहेजना** | Use |

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करेंगे।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java के साथ दस्तावेज़ को PDF के रूप में कैसे सहेजें](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java का उपयोग करके पासवर्ड के साथ Word सहेजें](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}