---
category: general
date: 2026-08-14
description: Aspose.Words का उपयोग करके जावा में वर्ड में पाई चार्ट बनाएं। चार्ट में
  सीरीज़ डेटा जोड़ना और केवल कुछ लाइनों में पाई चार्ट के स्लाइस को घुमाना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: hi
lastmod: 2026-08-14
og_description: Java का उपयोग करके Aspose.Words के साथ Word में पाई चार्ट बनाएं। यह
  ट्यूटोरियल दिखाता है कि चार्ट में सीरीज़ डेटा कैसे जोड़ें और पाई चार्ट के स्लाइस
  को जल्दी से कैसे घुमाएँ।
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: जावा के साथ वर्ड में पाई चार्ट बनाएं – पूर्ण कोडिंग गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: जावा के साथ वर्ड में पाई चार्ट बनाएं – चरण‑दर‑चरण गाइड
url: /hi/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के साथ Word में पाई चार्ट बनाएं – चरण‑दर‑चरण गाइड

यदि आपको प्रोग्रामेटिक रूप से **Word में पाई चार्ट बनाना** है, तो यह गाइड आपको Java और Aspose.Words के साथ इसे कैसे करना है, बिल्कुल दिखाता है। आप पूरी कार्यप्रवाह सीखेंगे, चार्ट डालने से लेकर डेटा पॉइंट जोड़ने और पहली स्लाइस को घुमाने तक।

`.docx` फ़ाइल में सीधे चार्ट जनरेट करने से मैन्युअल कॉपी‑पेस्ट चरण हट जाता है और आप रिपोर्ट, इनवॉइस या डैशबोर्ड को ऑटोमेट कर सकते हैं। इस दौरान हम **चार्ट में सीरीज़ डेटा कैसे जोड़ें** और **पाई चार्ट स्लाइस को कैसे घुमाएँ** को भी कवर करेंगे ताकि दृश्य प्रभाव बेहतर हो।

## Word में पाई चार्ट बनाना – अवलोकन

Aspose.Words for Java एक सहज `DocumentBuilder` API प्रदान करता है जो Word दस्तावेज़ में चार्ट ऑब्जेक्ट डाल सकता है। आप जो चार्ट प्रकार चुनते हैं, वह डिफ़ॉल्ट लेआउट निर्धारित करता है, और आप सीरीज़, रंग, कोण को कस्टमाइज़ कर सकते हैं, और एक ही मेथड कॉल से डोनट आकार में भी बदल सकते हैं।

### Aspose.Words क्यों उपयोग करें?

* **Microsoft Office की आवश्यकता नहीं** – लाइब्रेरी किसी भी सर्वर या CI वातावरण में काम करती है।  
* **पूर्ण .docx फ़िडेलिटी** – जनरेट किया गया चार्ट Word में मैन्युअल रूप से बनाए गए चार्ट जैसा ही दिखता है।  
* **सिंगल‑फ़ाइल डिपेंडेंसी** – बस JAR जोड़ें और आप तैयार हैं।

## चार्ट में सीरीज़ डेटा कैसे जोड़ें

डेटा के बिना चार्ट केवल एक प्लेसहोल्डर है। `Chart` ऑब्जेक्ट एक `Series` कलेक्शन प्रदान करता है; प्रत्येक सीरीज़ में संख्यात्मक मानों की सूची होती है जो स्लाइस (पाई के लिए) या पॉइंट (लाइन के लिए) से मैप होती है। डेटा जोड़ना सरल है:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**कोड क्या करता है:**  
* `chart.getSeries()` एक `List<ChartSeries>` लौटाता है।  
* `get(0)` पहली सीरीज़ चुनता है क्योंकि पाई चार्ट में परिभाषा अनुसार केवल एक ही सीरीज़ होती है।  
* `add(double)` एक डेटा पॉइंट जोड़ता है। मान स्वचालित रूप से प्रतिशत में बदल जाते हैं जो चार्ट रेंडर होने पर 100 % का योग बनाते हैं।

> **प्रो टिप:** यदि आपके डेटा स्रोत में तीन से अधिक श्रेणियां हैं, तो उसी तरह मान जोड़ते रहें। Aspose.Words स्वचालित रूप से अतिरिक्त स्लाइस बना देगा।

## पाई चार्ट स्लाइस को घुमाएँ

कभी-कभी आप चाहते हैं कि कोई विशेष स्लाइस एक विशिष्ट कोण से शुरू हो ताकि सबसे महत्वपूर्ण भाग दर्शक की ओर मुख़ातिब हो। `setFirstSliceAngle(double)` मेथड पूरे चार्ट को घुमाता है, प्रभावी रूप से पहली स्लाइस की शुरुआत को बदलता है:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

कोण को डिग्री में वर्टिकल एक्सिस से घड़ी की दिशा में मापा जाता है। इसे `0` (डिफ़ॉल्ट) पर सेट करने से पहली स्लाइस शीर्ष पर आती है। मान को समायोजित करके आप स्लाइस को हाइलाइट कर सकते हैं या डिज़ाइन गाइडलाइन से मेल करा सकते हैं।

> **सामान्य प्रश्न:** *क्या घुमाने से डेटा क्रम प्रभावित होता है?*  
> नहीं। डेटा क्रम वही रहता है; केवल दृश्य प्रारंभिक स्थिति बदलती है।

## पूर्ण Java उदाहरण

नीचे एक पूर्ण, तैयार‑चलाने योग्य प्रोग्राम है जो पाई चार्ट के साथ Word दस्तावेज़ बनाता है, सीरीज़ डेटा जोड़ता है, स्लाइस को घुमाता है, और फ़ाइल को सहेजता है। सभी आवश्यक इम्पोर्ट्स सूचीबद्ध हैं, इसलिए आप कोड को किसी भी IDE में कॉपी कर सकते हैं।

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### अपेक्षित आउटपुट

* `output` फ़ोल्डर में **PieChart.docx** नाम की फ़ाइल बनती है।  
* Microsoft Word में फ़ाइल खोलने पर तीन स्लाइस (40 %, 30 %, 30 %) वाला रंगीन पाई चार्ट दिखता है।  
* चार्ट 45° घड़ी की दिशा में घुमाया गया है, इसलिए पहली स्लाइस वर्टिकल एक्सिस के थोड़ा दाईं ओर से शुरू होती है।

## सामान्य समस्याएँ और सर्वोत्तम प्रथाएँ

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| **चार्ट खाली दिख रहा है** | दस्तावेज़ को चार्ट पूरी तरह रेंडर होने से पहले सहेजा गया था। | सभी चार्ट संशोधनों **के बाद** `doc.save()` को कॉल करें। |
| **स्लाइस मान 100 % नहीं बनते** | ऐसे कच्चे नंबर जोड़ने से जो प्रतिशत नहीं दर्शाते, अप्रत्याशित स्केलिंग हो सकती है। | ऐसे मान प्रदान करें जो कुल का भाग दर्शाते हों, या Aspose.Words को स्वचालित रूप से प्रतिशत गणना करने दें। |
| **घुमाव का कोई प्रभाव नहीं** | `ChartType.DOUGHNUT` का उपयोग `holeSize` सेट किए बिना करने से घुमाव प्रभाव छिप सकता है। | चार्ट को `PIE` रखें या कोण सेट करने के बाद `holeSize` समायोजित करें। |
| **फ़ाइल पाथ त्रुटियाँ** | रिलेटिव पाथ Windows और Linux पर अलग-अलग रिजॉल्व हो सकते हैं। | `Paths.get("output", "PieChart.docx").toString()` या प्रोडक्शन कोड के लिए एब्सोल्यूट पाथ उपयोग करें। |

### प्रोडक्शन उपयोग के टिप्स

* **`DocumentBuilder` को पुनः उपयोग करें** – आप `insertChart` को बार‑बार कॉल करके एक ही दस्तावेज़ में कई चार्ट डाल सकते हैं।  
* **स्टाइलिंग** – प्रतिशत सीधे चार्ट पर दिखाने के लिए `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` उपयोग करें।  
* **परफॉर्मेंस** – चार्ट को एक बार जनरेट करें और यदि कई जगहों पर समान चार्ट चाहिए तो उसे क्लोन करें (`chart.deepClone()`)।

## पाई चार्ट स्लाइस को घुमाएँ – उन्नत परिदृश्य

* **डायनामिक कोण** – डेटा के आधार पर कोण की गणना करें (उदाहरण के लिए, सबसे बड़ा स्लाइस शीर्ष से शुरू करें)।  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **एकाधिक सीरीज़** – जबकि पाई चार्ट आमतौर पर एक सीरीज़ रखता है, Aspose.Words आपको स्टैक्ड पाई के लिए अधिक जोड़ने देता है। घुमाव केवल पहली सीरीज़ पर ही लागू होता है।

## निष्कर्ष

अब आप जानते हैं कि Java का उपयोग करके **Word में पाई चार्ट कैसे बनाएं**, **चार्ट में सीरीज़ डेटा कैसे जोड़ें**, और दृश्य प्रभाव के लिए **पाई चार्ट स्लाइस को कैसे घुमाएँ**। पूर्ण उदाहरण पूरे कार्यप्रवाह को दर्शाता है—दस्तावेज़ प्रारंभिकरण से लेकर अंतिम `.docx` फ़ाइल सहेजने तक—ताकि आप किसी भी ऑटोमेटेड रिपोर्टिंग पाइपलाइन में चार्ट जनरेशन को एकीकृत कर सकें।

### आगे क्या?

* अन्य चार्ट प्रकारों (`ChartType.BAR`, `ChartType.LINE`) का अन्वेषण करें ताकि आपका ऑटोमेशन टूलकिट विस्तृत हो।  
* चार्ट जनरेशन को **mail merge** के साथ मिलाकर प्रत्येक प्राप्तकर्ता के लिए व्यक्तिगत रिपोर्ट बनाएं।  
* अपने कॉरपोरेट ब्रांडिंग से मेल खाने के लिए **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) में गहराई से जाएँ।

विभिन्न डेटा सेट, कोण, और चार्ट स्टाइल के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड कैसे बनाएं और कंटेंट जोड़ें](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java का उपयोग करके Word को PDF में कैसे कनवर्ट करें](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}