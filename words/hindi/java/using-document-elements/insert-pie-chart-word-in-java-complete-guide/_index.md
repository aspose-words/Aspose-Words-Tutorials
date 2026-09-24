---
category: general
date: 2026-09-24
description: Aspose.Words for Java का उपयोग करके DOCX में पाई चार्ट डालें। होल का
  आकार सेट करना, पाई स्लाइस को एक्सप्लोड करना, पाई चार्ट स्लाइस को हाइलाइट करना, और
  आसानी से DOCX चार्ट बनाना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: hi
lastmod: 2026-09-24
og_description: Aspose.Words for Java का उपयोग करके DOCX में पाई चार्ट शब्द डालें।
  छेद का आकार सेट करें, पाई स्लाइस को एक्सप्लोड करें, पाई चार्ट स्लाइस को हाइलाइट
  करें, और मिनटों में DOCX चार्ट बनाएं।
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: जावा में पाई चार्ट शब्द सम्मिलित करें – चरण‑दर‑चरण ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Java में पाई चार्ट शब्द डालें – पूर्ण गाइड
url: /hi/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में पाई चार्ट शब्द सम्मिलित करें – पूर्ण गाइड

यदि आपको DOCX फ़ाइल में **insert pie chart word** सम्मिलित करने की आवश्यकता है, तो यह ट्यूटोरियल आपको Aspose.Words for Java के साथ इसे कैसे किया जाए, बिल्कुल दिखाता है। आप दस्तावेज़ बनाने से लेकर चार्ट को कस्टमाइज़ करने तक का पूरा वर्कफ़्लो देखेंगे, जिसमें स्लाइस को एक्सप्लोड किया जाता है, होल साइज को शून्य सेट किया जाता है, और स्लाइस को हाइलाइट किया जाता है।

Word दस्तावेज़ों में चार्ट के साथ काम करना अक्सर नियमित टेक्स्ट प्रोसेसिंग से अलग लग सकता है, लेकिन Aspose.Words दोनों को एकीकृत करता है। नीचे दिए गए चरणों में आप यह भी सीखेंगे कि कैसे **create docx chart** फ़ाइलें बनाई जाएँ जो Microsoft Word, Google Docs, या किसी अन्य DOCX‑compatible व्यूअर में खोली जा सकें।

## आप क्या हासिल करेंगे

* **Insert pie chart word** को एक खाली दस्तावेज़ में सम्मिलित करें  
* **Set hole size** को सेट करके चार्ट को पूर्ण पाई (डोनट नहीं) बनाएं  
* **Explode pie slice** को किसी विशिष्ट खंड पर ध्यान आकर्षित करने के लिए उपयोग करें  
* **Highlight pie chart slice** को कस्टम फ़ॉर्मेटिंग के साथ हाइलाइट करें  
* **Create docx chart** जिसे साझा किया जा सके या आगे संपादित किया जा सके  

### आवश्यकताएँ

* Java 17 या बाद का संस्करण (कोड Java 8 के साथ भी कंपाइल होता है)  
* Aspose.Words for Java लाइब्रेरी (संस्करण 23.9 या नया)  
* एक IDE या बिल्ड टूल (Maven/Gradle) जो Aspose.Words डिपेंडेंसी को रिजॉल्व कर सके  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Aspose.Words का उपयोग करके DOCX में pie chart शब्द कैसे सम्मिलित करें

पहला कदम एक नया खाली दस्तावेज़ बनाना और `DocumentBuilder` प्राप्त करना है। बिल्डर आपको दस्तावेज़ की कंटेंट स्ट्रीम तक सीधा एक्सेस देता है, जिससे **insert pie chart word** करना बहुत आसान हो जाता है।

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### यह क्यों महत्वपूर्ण है
`Document` पूरे Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक हाई‑लेवल API है जो आपको पैराग्राफ, टेबल, और चार्ट सम्मिलित करने देता है बिना लो‑लेवल XML से निपटे। एक साफ़ दस्तावेज़ से शुरू करने से यह सुनिश्चित होता है कि आप जो चार्ट जोड़ते हैं वह एकमात्र कंटेंट है, जो सीखने या टेम्पलेट‑आधारित रिपोर्ट जेनरेट करने के लिए उत्तम है।

## पूर्ण पाई बनाने के लिए होल साइज सेट करें

डिफ़ॉल्ट रूप से, जब आप पाई चार्ट का अनुरोध करते हैं तो Aspose.Words एक डोनट चार्ट बनाता है। चार्ट को वास्तविक सर्कल बनाने के लिए आपको **set hole size** को `0` पर सेट करना होगा। इससे अंदर का होल हट जाता है और क्लासिक पाई रूप मिलता है।

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### व्यावहारिक टिप
यदि बाद में आप डोनट चार्ट पर स्विच करना चाहते हैं, तो बस `holeSize` मान को प्रतिशत में बदलें (जैसे, `30`)। वही API दोनों चार्ट प्रकारों के लिए काम करता है।

## स्लाइस को एक्सप्लोड करके एक खंड को हाइलाइट करें

स्लाइस को एक्सप्लोड करने से वह दृश्य रूप से उभर कर दिखता है। **explode pie slice** ऑपरेशन चुने हुए स्लाइस को चार्ट की रेडियस के प्रतिशत के अनुसार बाहर की ओर ले जाता है।

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### एक्सप्लोड क्यों?
एक एक्सप्लोडेड स्लाइस पाठक की नजर सबसे महत्वपूर्ण डेटा पॉइंट की ओर आकर्षित करता है—डैशबोर्ड या एग्जीक्यूटिव समरी के लिए उत्तम। मान `20` का अर्थ है रेडियस का 20 %; आप इसे `0` (कोई एक्सप्लोजन नहीं) और `100` (पूरी तरह से अलग) के बीच समायोजित कर सकते हैं।

## कस्टम फ़ॉर्मेटिंग के साथ पाई चार्ट स्लाइस को हाइलाइट करें

एक्सप्लोड करने के अलावा, आप **highlight pie chart slice** को उसके फ़िल कलर या बॉर्डर को बदलकर हाइलाइट करना चाह सकते हैं। जबकि डेमो कोड एक्सप्लोजन पर केंद्रित है, आप इसे इस प्रकार विस्तारित कर सकते हैं:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### विशेषज्ञ नोट
किसी विशिष्ट स्लाइस का फ़िल कलर बदलने के लिए `DataPoint` ऑब्जेक्ट तक पहुंच आवश्यक है। यदि आपके पास कई सीरीज़ हैं, तो `series.getDataPoints()` पर इटररेट करें और शर्तानुसार स्टाइल लागू करें।

## बनाए गए docx चार्ट को सेव करें और सत्यापित करें

अंत में, आप `Document` को सेव करके **create docx chart** बनाते हैं। परिणामी फ़ाइल को Microsoft Word में खोलकर फ़ॉर्मेटेड पाई चार्ट देखा जा सकता है।

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### अपेक्षित आउटपुट
`PieChartFormatted.docx` खोलने पर एक एकल पाई चार्ट दिखता है:

* चार्ट 400 × 300 pt क्षेत्र को घेरता है।  
* होल साइज `0` है, इसलिए चार्ट एक पूर्ण पाई है।  
* पहला स्लाइस 20 % द्वारा एक्सप्लोड किया गया है और लाल रंग में रंगा गया है (यदि आपने वैकल्पिक फ़ॉर्मेटिंग जोड़ी है)।  

अब आपके पास एक **create docx chart** है जिसे वितरित किया जा सकता है, ईमेल में एम्बेड किया जा सकता है, या प्रोग्रामेटिक रूप से आगे संपादित किया जा सकता है।

---

## सामान्य विविधताएँ और किनारे के मामले

| परिदृश्य | कोड को कैसे अनुकूलित करें |
|----------|----------------------|
| **Multiple series** | `pieChart.getChart().getSeries()` पर लूप करें और प्रत्येक सीरीज़ के लिए `Explosion` या `FillColor` सेट करें। |
| **Dynamic data** | `setExplosion` कॉल करने से पहले डेटाबेस या CSV से मान लेकर सीरीज़ को भरें। |
| **Different chart size** | `insertChart(ChartType.PIE, width, height)` में चौड़ाई/ऊँचाई के आर्ग्युमेंट बदलें। |
| **Export to PDF** | DOCX को सेव करने के बाद, `doc.save("output.pdf")` कॉल करके उसी चार्ट का PDF संस्करण बनाएं। |
| **Localization** | लेबल्स के लिए locale‑specific नंबर फ़ॉर्मेट के साथ `DocumentBuilder.insertChart` का उपयोग करें। |

### प्रो टिप
हमेशा `insertChart` के **बाद** `setHoleSize(0)` कॉल करें। यदि आप इसे इन्सर्शन से पहले सेट करते हैं, तो चार्ट बनते ही Aspose.Words डिफ़ॉल्ट डोनट साइज पर वापस आ जाएगा।

---

## पुनरावलोकन

अब आप जानते हैं कि Java का उपयोग करके Word दस्तावेज़ में **insert pie chart word** कैसे डालें, पूर्ण‑पाई लुक के लिए **set hole size** कैसे सेट करें, ध्यान आकर्षित करने के लिए **explode pie slice** कैसे करें, और कस्टम रंगों के साथ **highlight pie chart slice** कैसे करें। पूर्ण उदाहरण यह भी दर्शाता है कि **create docx chart** फ़ाइलें कैसे बनाएं जो वितरण के लिए तैयार हों।

---

## अगले कदम

* `ChartType` के साथ अन्य चार्ट प्रकारों (`BAR`, `LINE`, `SCATTER`) का अन्वेषण करें।  
* चार्ट जेनरेशन को मेल मर्ज के साथ मिलाकर व्यक्तिगत रिपोर्ट बनाएं।  
* जनरेटेड DOCX को वेब सर्विस में इंटीग्रेट करें जो मांग पर फ़ाइल लौटाए।  

यदि आपको समस्याएँ आती हैं, तो यह याद रखें कि आप Aspose.Words का संगत संस्करण उपयोग कर रहे हैं और आउटपुट डायरेक्टरी मौजूद है और लिखने योग्य है।

कोडिंग का आनंद लें!

## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}