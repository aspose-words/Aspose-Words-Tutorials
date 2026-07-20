---
category: general
date: 2026-07-20
description: Aspose.Words के साथ Word में पाई चार्ट कैसे डालें। डेटा लेबल प्रतिशत
  जोड़ना सीखें और पेशेवर दस्तावेज़ों के लिए चार्ट पर प्रतिशत दिखाएँ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: hi
lastmod: 2026-07-20
og_description: Aspose.Words का उपयोग करके Word में पाई चार्ट कैसे डालें। यह गाइड
  दिखाता है कि डेटा लेबल प्रतिशत कैसे जोड़ें और चार्ट पर प्रतिशत केवल कुछ लाइनों में
  कैसे प्रदर्शित करें।
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: Word में पाई चार्ट कैसे डालें – त्वरित गाइड
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Word में पाई चार्ट कैसे डालें – डेटा लेबल प्रतिशत जोड़ें
url: /hi/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में पाई चार्ट कैसे डालें – डेटा लेबल प्रतिशत जोड़ें

क्या आपने कभी सोचा है कि UI से जूझे बिना Word दस्तावेज़ में **how to insert pie chart** कैसे डालें? आप अकेले नहीं हैं। कई रिपोर्टिंग परिदृश्यों में आपको *add pie chart to Word* करने की आवश्यकता होती है और, उससे भी महत्वपूर्ण, **show percent on pie chart** ताकि पाठक तुरंत डेटा वितरण को समझ सकें।

इस ट्यूटोरियल में हम Aspose.Words for Java का उपयोग करके पूरी प्रक्रिया को चरण-दर-चरण देखेंगे। अंत तक आप बिल्कुल जान जाएंगे कि **add data label percent**, **display percentages on chart** कैसे करें, और एक परिपूर्ण पाई चार्ट प्राप्त करेंगे जो पहली बार में ही सही दिखे। कोई अतिरिक्त प्लगइन्स नहीं, कोई मैनुअल ट्यूनिंग नहीं—सिर्फ साफ़ कोड जिसे आप किसी भी प्रोजेक्ट में डाल सकते हैं।

---

## आवश्यकताएँ

- Java 17 (या बाद का) – वह वर्तमान LTS संस्करण जिसे Aspose.Words समर्थन करता है।
- Aspose.Words for Java 24.x (लेखन के समय, जुलाई 2026 में नवीनतम)।
- लाइब्रेरी को प्राप्त करने के लिए एक बेसिक Maven या Gradle सेटअप।
- आपका पसंदीदा IDE (IntelliJ IDEA, Eclipse, VS Code… कोई भी चलेगा)।

यदि आपके पास ये पहले से हैं, तो बढ़िया—आइए शुरू करते हैं।

---

## चरण 1: प्रोजेक्ट सेट अप करें और लाइब्रेरी इम्पोर्ट करें

सबसे पहले, अपने `pom.xml` (Maven) या `build.gradle` (Gradle) में Aspose.Words निर्भरता जोड़ें। इससे आपको `Document`, `DocumentBuilder`, और चार्ट क्लासेज़ तक पहुँच मिलती है।

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** संस्करण संख्या को अद्यतित रखें; नए रिलीज़ अक्सर चार्ट‑संबंधी सुधार जोड़ते हैं जो **display percentages on chart** को अधिक विश्वसनीय बनाते हैं।

---

## चरण 2: नया Word दस्तावेज़ और बिल्डर बनाएं

बिल्डर आपके सामग्री डालने के लिए स्विस‑आर्मी चाकू जैसा है। यहाँ हम एक नया दस्तावेज़ बनाते हैं और उस पर `DocumentBuilder` संलग्न करते हैं।

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

हमें बिल्डर की क्यों जरूरत है? यह लो‑लेवल OpenXML संरचनाओं को एब्स्ट्रैक्ट करता है, जिससे हम *क्या* चाहते हैं—जैसे **add pie chart to word**—पर ध्यान दे सकते हैं, न कि *XML कैसे दिखता है*।

---

## चरण 3: पाई चार्ट डालें

अब **how to insert pie chart** का मुख्य भाग आता है। हम बिल्डर से एक विशिष्ट आकार का पाई चार्ट रखने को कहते हैं। आयाम पॉइंट्स में होते हैं (1 pt ≈ 1/72 in)।

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

इस बिंदु पर चार्ट खाली है, लेकिन प्लेसहोल्डर दस्तावेज़ में पहले से ही है। आपने अभी प्रोग्रामेटिकली **add pie chart to word** किया है।

---

## चरण 4: चार्ट को डेटा से भरें

एक पाई चार्ट को कम से कम एक वैल्यू सीरीज़ की जरूरत होती है। चलिए इसे कुछ सैंपल डेटा देते हैं जो मार्केट शेयर दर्शाता है।

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

यदि आपको कई सीरीज़ (स्टैक्ड पाई, डोनट आदि) चाहिए तो आप `pieChart.getSeries().add()` कॉल कर सकते हैं और चरण दोहरा सकते हैं। वही लॉजिक तब लागू होता है जब आप प्रत्येक स्लाइस के लिए **display percentages on chart** चाहते हैं।

---

## चरण 5: **add data label percent** – स्लाइस पर प्रतिशत दिखाएँ

यह वह भाग है जिसे अधिकांश डेवलपर भूल जाते हैं: डेटा लेबल्स को प्रतिशत दिखाने के लिए कॉन्फ़िगर करना। इसके बिना, चार्ट केवल कच्चे नंबर दिखाता है, जो अस्पष्ट हो सकता है।

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

`setShowPercent(true)` कॉल Aspose.Words को लेबल को “30 %”, “45 %” आदि के रूप में रेंडर करने के लिए बताता है। यही वह तरीका है जिससे आप **show percent on pie chart** बिना किसी अतिरिक्त फॉर्मेटिंग के कर सकते हैं।

---

## चरण 6: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप `.docx`, `.pdf`, या यहाँ तक कि `.html` चुन सकते हैं। इस गाइड के लिए हम आधुनिक `.docx` फ़ॉर्मेट का उपयोग करेंगे।

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

प्रोग्राम चलाएँ, `PieChartDemo.docx` खोलें, और आपको प्रत्येक स्लाइस पर प्रतिशत लेबल के साथ एक साफ़ रेंडर किया गया पाई चार्ट दिखेगा।

---

## अपेक्षित आउटपुट

नीचे जेनरेट किए गए Word फ़ाइल की स्क्रीनशॉट है। देखें कि प्रत्येक स्लाइस अपना शेयर प्रतिशत के रूप में कैसे दिखाता है—बिल्कुल वही जो हमने **add data label percent** सेट करने पर चाहा था।

![Word दस्तावेज़ का स्क्रीनशॉट जिसमें प्रतिशत लेबल वाला पाई चार्ट है](/images/pie-chart-percent.png){.center width=600px alt="Word में पाई चार्ट डालने और प्रतिशत लेबल जोड़ने का स्क्रीनशॉट"}

*Alt टेक्स्ट में मुख्य कीवर्ड शामिल है, जो SEO और एक्सेसिबिलिटी दोनों को संतुष्ट करता है।*

---

## आम प्रश्न और किनारे‑के‑मामले का समाधान

| Question | Answer |
|----------|--------|
| **क्या मैं प्रतिशत लेबल्स के फ़ॉन्ट को बदल सकता हूँ?** | हाँ। `setShowPercent(true)` सक्षम करने के बाद, `DataLabel` ऑब्जेक्ट प्राप्त करें और उसकी `Font` प्रॉपर्टी को समायोजित करें (`dataLabel.getFont().setSize(10);`). |
| **अगर मुझे पाई के बजाय डोनट चार्ट चाहिए तो क्या करें?** | `insertChart` कॉल में `ChartType.PIE` को `ChartType.DOUGHNUT` से बदलें। वही **add data label percent** लॉजिक काम करता है। |
| **क्या पुराने Word संस्करण (2007‑2010) प्रतिशत सही ढंग से दिखाते हैं?** | Aspose.Words अंतर्निहित XML को संस्करण‑निर्पेक्ष तरीके से लिखता है, इसलिए प्रतिशत किसी भी Word में दिखते हैं जो चार्ट सपोर्ट करता है (2007+). |
| **चार्ट में शीर्षक कैसे जोड़ें?** | सहेजने से पहले `pieChart.getTitle().setText("Market Share");` का उपयोग करें। |
| **क्या मैं चार्ट को किसी विशिष्ट पैराग्राफ या टेबल सेल में डाल सकता हूँ?** | बिल्कुल। `insertChart` कॉल करने से पहले `DocumentBuilder` को इच्छित स्थान पर ले जाएँ (`builder.moveToParagraph(index, true);` या `builder.moveToCell(table, row, column, true);`). |

---

## फ़ील्ड से टिप्स और ट्रिक्स

- **Pro tip:** यदि आप लूप में कई चार्ट जनरेट करने की योजना बना रहे हैं, तो एक ही `DocumentBuilder` इंस्टेंस को पुन: उपयोग करें; यह मेमोरी उपयोग को कम करता है।
- **Watch out for:** बहुत छोटे स्लाइस (< 2 %). Aspose.Words अव्यवस्था से बचने के लिए लेबल को छोड़ सकता है; आप इसे `dataLabel.setShowLabel(true);` से मजबूर कर सकते हैं।
- **Performance note:** चार्ट रेंडरिंग CPU‑गहन है। बड़े पैमाने पर रिपोर्ट जनरेशन के लिए मल्टी‑थ्रेडिंग पर विचार करें लेकिन सुनिश्चित करें कि प्रत्येक थ्रेड अपने स्वयं के `Document` इंस्टेंस पर काम करे।
- **Version check:** मेथड `setShowPercent` Aspose.Words 22.8 में पेश किया गया था। यदि आप पुराने संस्करण पर हैं, तो अपग्रेड करें या मैन्युअली प्रतिशत गणना करके उन्हें कस्टम लेबल के रूप में सेट करें।

---

## सारांश

हमने Aspose.Words का उपयोग करके Word दस्तावेज़ में **how to insert pie chart** को कवर किया, आपको **add data label percent** कैसे करें दिखाया, और **display percentages on chart** का सबसे आसान तरीका प्रदर्शित किया। केवल कुछ Java लाइनों से आप **add pie chart to word** और **show percent on pie chart** कर सकते हैं, जिससे कच्चे नंबर तुरंत पढ़ने योग्य विज़ुअल्स में बदल जाते हैं।

---

## आगे क्या?

- अन्य चार्ट प्रकारों (`BAR`, `LINE`, `AREA`) के साथ प्रयोग करें और देखें कि वही **add data label percent** लॉजिक कैसे लागू होता है।
- चार्ट को टेबल के साथ मिलाकर अधिक समृद्ध रिपोर्ट बनाएं—Aspose.Words के साथ चार्ट को डेटा टेबल के बगल में रखना बहुत आसान है।
- समान दस्तावेज़ को PDF या HTML में एक्सपोर्ट करके देखें कि विभिन्न फ़ॉर्मेट में प्रतिशत कैसे रेंडर होते हैं।

डायमेंशन, रंग, या डेटा स्रोत (जैसे, डेटाबेस क्वेरी) को बदलने में संकोच न करें और देखें कि आपके Word रिपोर्ट जीवंत हो जाते हैं। यदि आपको कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें—हैप्पी चार्टिंग!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके Word में कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)
- [Word दस्तावेज़ में एरिया चार्ट डालें | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में बबल चार्ट डालें](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}