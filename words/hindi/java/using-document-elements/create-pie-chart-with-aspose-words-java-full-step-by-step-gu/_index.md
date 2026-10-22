---
category: general
date: 2026-07-16
description: Aspose.Words का उपयोग करके जावा में पाई चार्ट बनाएं। एक ही ट्यूटोरियल
  में लीडर लाइन्स जोड़ना, चार्ट लेजेंड दिखाना, और स्लाइस को एक्सप्लोड करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: hi
lastmod: 2026-07-16
og_description: Aspose.Words का उपयोग करके जावा में पाई चार्ट बनाएं। यह गाइड दिखाता
  है कि लीडर लाइन्स कैसे जोड़ें, चार्ट लेजेंड दिखाएँ, और स्लाइस को एक्सप्लोड करें,
  जिससे आप कुछ ही मिनटों में एक परिष्कृत विज़ुअल प्राप्त कर सकते हैं।
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Aspose.Words Java के साथ पाई चार्ट बनाएं – पूर्ण फ़ॉर्मेटिंग ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Aspose.Words Java के साथ पाई चार्ट बनाएं – पूर्ण चरण‑दर‑चरण मार्गदर्शिका
url: /hi/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java के साथ पाई चार्ट बनाएं – पूर्ण चरण‑दर‑चरण गाइड

क्या आपने कभी सोचा है कि **पाई चार्ट** को प्रोग्रामेटिकली Java में बिना लो‑लेवल ड्रॉइंग API के झंझट के कैसे बनाएं? आप अकेले नहीं हैं। कई डेवलपर्स को रिपोर्ट, डैशबोर्ड या ऑटोमेटेड डॉक्यूमेंट्स के लिए जल्दी से विज़ुअल चाहिए होता है, और वे Aspose.Words का उपयोग करते हैं क्योंकि यह भारी काम संभाल लेता है।  

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य उदाहरण के माध्यम से चलेंगे जो न केवल **पाई चार्ट** बनाता है बल्कि आपको **लीडर लाइन्स** जोड़ना, **चार्ट लेजेंड** दिखाना, और यहाँ तक कि **स्लाइस को एक्सप्लोड** करके ज़ोर देना भी सिखाता है। अंत में आपके पास एक `.docx` फ़ाइल होगी जो क्लाइंट को प्रभावित करने के लिए पर्याप्त परिष्कृत दिखेगी।

> **त्वरित लाभ:** नीचे दिया गया कोड स्निपेट Aspose.Words for Java 23.9 (या किसी भी नए संस्करण) के साथ बॉक्स से बाहर काम करता है। कोई अतिरिक्त डिपेंडेंसी नहीं, सिर्फ JAR।

## आप क्या सीखेंगे

- `DocumentBuilder` के साथ एक खाली Word डॉक्यूमेंट सेट अप करना।
- कस्टम आकार का **पाई चार्ट** इन्सर्ट करना।
- डेटा पॉइंट को हाईलाइट करने के लिए **एक्सप्लोड स्लाइस** फीचर का उपयोग करना।
- **लीडर लाइन्स** सक्षम करना ताकि एक्सप्लोडेड स्लाइस लेबल से जुड़ा रहे।
- **चार्ट लेजेंड** चालू करना ताकि पाठक तुरंत प्रत्येक स्लाइस की पहचान कर सकें।
- परिणाम को `.docx` फ़ाइल में सेव करना जिसे आप Microsoft Word या LibreOffice में खोल सकते हैं।

**पूर्वापेक्षाएँ** – आपको चाहिए:

1. Java 17 (या बाद का) स्थापित हो।
2. क्लासपाथ में Aspose.Words for Java JAR हो।
3. एक बेसिक IDE या टेक्स्ट एडिटर—IntelliJ IDEA, Eclipse, VS Code, जो भी आप पसंद करें।

अब, चलिए शुरू करते हैं।

## चरण 1: डॉक्यूमेंट और बिल्डर को इनिशियलाइज़ करें – **पाई चार्ट बनाने** की तैयारी

सबसे पहले, हमें एक साफ़ डॉक्यूमेंट कैनवास चाहिए। `Document` पूरे Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` वह सहायक है जो हमें कंटेंट जोड़ने देता है।

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **क्यों महत्वपूर्ण है:** एक नया `Document` शुरू करने से यह सुनिश्चित होता है कि कोई छिपी हुई स्टाइल या बचा हुआ ऑब्जेक्ट नहीं है जो चार्ट रेंडरिंग में बाधा डाल सके।

## चरण 2: **पाई चार्ट** इन्सर्ट करें – आकार मायने रखता है

Aspose.Words चार्ट इन्सर्शन को एक‑लाइनर बनाता है। यहाँ हम 400 × 300 पॉइंट्स का पाई चार्ट मांगते हैं—जो सामान्य स्क्रीन पर लगभग 5.5 × 4.2 इंच के बराबर है।

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **प्रो टिप:** अगर आपको अलग आकार चाहिए, तो बस दो संख्यात्मक आर्ग्यूमेंट बदल दें। API पॉइंट्स में काम करता है, जहाँ 72 पॉइंट = 1 इंच।

## चरण 3: **स्लाइस को एक्सप्लोड** कैसे करें – मुख्य डेटा पॉइंट को ज़ोर देना

एक स्लाइस को एक्सप्लोड करने से वह बाकी पाई से बाहर निकल जाता है, जिससे पाठक का ध्यान आकर्षित होता है। `setExplosion` मेथड एक इंटीजर लेता है जो दूरी को पॉइंट्स में दर्शाता है।

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **अगर आपके पास कई सीरीज़ हैं?** आप किसी भी सीरीज़ इंडेक्स (`get(1)`, `get(2)`, …) पर `setExplosion` कॉल कर सकते हैं ताकि विभिन्न स्लाइस को एक्सप्लोड किया जा सके।

## चरण 4: **लीडर लाइन्स** जोड़ें और **चार्ट लेजेंड** दिखाएँ – डॉट्स को कनेक्ट करना

जब कोई स्लाइस एक्सप्लोड होता है, तो लेबल दूर भटक सकता है। लीडर लाइन्स लेबल को टेथर रखती हैं, जिससे पठनीयता बनी रहती है। साथ ही, लेजेंड सभी स्लाइस के लिए एक त्वरित कुंजी प्रदान करता है।

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **लीडर लाइन्स क्यों सक्षम करें?** इनके बिना लेबल हवा में तैरता हुआ दिख सकता है, जिससे उपयोगकर्ता भ्रमित हो सकता है कि वह किस स्लाइस से संबंधित है।  
> **कस्टम लेजेंड पोज़िशन चाहिए?** `chart.getLegend().setPosition(LegendPosition.TOP)` या किसी अन्य enum वैल्यू का उपयोग करें।

## चरण 5: डॉक्यूमेंट को सेव करें – अंतिम **पाई चार्ट बनाने** का चरण

आखिर में, हम डॉक्यूमेंट को डिस्क पर लिखते हैं। उस फ़ोल्डर का पाथ बदलें जहाँ आपके पास लिखने की अनुमति हो।

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

प्रोग्राम चलाएँ, जेनरेटेड `PieChartDemo.docx` खोलें, और आपको एक सुंदर फॉर्मेटेड पाई चार्ट दिखेगा जिसमें पहला स्लाइस एक्सप्लोड किया गया है, लीडर लाइन्स हैं, और लेजेंड दिखाई दे रहा है।

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="एक्सप्लोडेड स्लाइस, लीडर लाइन्स और लेजेंड के साथ पाई चार्ट उदाहरण"}

### अपेक्षित आउटपुट

जब आप Word फ़ाइल खोलेंगे, तो चार्ट लगभग इस तरह दिखेगा:

- 400 × 300 pt पाई चार्ट।
- पहला स्लाइस 10 pt से ऑफ़सेट है।
- एक पतली लीडर लाइन एक्सप्लोडेड स्लाइस को उसके लेबल से जोड़ती है।
- चार्ट के नीचे एक लेजेंड प्रत्येक सीरीज़ का नाम सूचीबद्ध करता है।

अगर आपको लीडर लाइन नहीं दिख रही है, तो दोबारा जांचें कि `setLeaderLines(true)` **एक्सप्लोजन सेटिंग के बाद** कॉल किया गया है—क्रम महत्वपूर्ण है।

## सामान्य समस्याएँ और उनका समाधान

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| **लेजेंड नहीं दिख रहा** | `setShowLegend(true)` छोड़ दिया गया या गलत चार्ट ऑब्जेक्ट पर कॉल किया गया। | सुनिश्चित करें कि आप `chart.setShowLegend(true)` **चार्ट को शैप से प्राप्त करने के बाद** कॉल करें। |
| **लीडर लाइन गायब** | स्लाइस एक्सप्लोड नहीं हुआ, या चार्ट टाइप लीडर लाइन्स सपोर्ट नहीं करता। | केवल `ChartType.PIE` (या `PIE_3D`) लीडर लाइन्स सपोर्ट करता है। पहले `setExplosion` कॉल करें, फिर `setLeaderLines(true)`। |
| **स्लाइस नहीं हिल रहा** | एक्सप्लोजन वैल्यू बहुत कम (0‑2 pt)। | इंटीजर बढ़ाएँ, जैसे `setExplosion(10)` या अधिक, ताकि अधिक स्पष्ट प्रभाव मिले। |
| **चार्ट विकृत दिख रहा** | गैर‑स्क्वायर आकार (चौड़ाई ≠ ऊँचाई) पाई को स्क्वैश कर सकता है। | चौड़ाई और ऊँचाई को बराबर या करीब रखें; 400 × 300 काम करता है लेकिन 400 × 400 परफेक्ट सर्कल देगा। |

## उन्नत ट्यूनिंग (वैकल्पिक)

अगर आप बेसिक से आगे जाना चाहते हैं, तो विचार करें:

- **कस्टम रंग**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **डेटा लेबल**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D इफ़ेक्ट**: `ChartType.PIE` को `ChartType.PIE_3D` से बदलें।

इन विकल्पों से आप विज़ुअल को कॉर्पोरेट ब्रांडिंग गाइडलाइन के अनुसार फाइन‑ट्यून कर सकते हैं।

## सारांश – हमने क्या हासिल किया

हमने एक खाली Word डॉक्यूमेंट से शुरू किया, **पाई चार्ट बनाया**, **पहला स्लाइस एक्सप्लोड किया**, **लीडर लाइन्स जोड़ी**, और **चार्ट लेजेंड दिखाया**। पूरी प्रक्रिया एक संक्षिप्त `main` मेथड में फिट होती है, जिससे इसे बड़े रिपोर्टिंग पाइपलाइन में एम्बेड करना आसान हो जाता है।

## अगले कदम

- **और सीरीज़ जोड़ें**: डेटाबेस या CSV से वास्तविक डेटा के साथ चार्ट को पॉप्युलेट करें।
- **PDF में एक्सपोर्ट करें**: `doc.save("output.pdf", SaveFormat.PDF);` का उपयोग करके PDF संस्करण बनाएं।
- **अन्य शैप्स के साथ मिलाएँ**: टेबल, इमेज या अतिरिक्त चार्ट इन्सर्ट करके एक पूर्ण रिपोर्ट तैयार करें।

अगर आप अन्य चार्ट टाइप्स—कॉलम, बार, लाइन—में रुचि रखते हैं, तो बस `ChartType.PIE` को उपयुक्त enum से बदलें और वही फॉर्मेटिंग स्टेप्स फॉलो करें।

---

*हैप्पी चार्टिंग!* अगर कुछ अपेक्षित रूप से काम नहीं किया, तो कमेंट करें या बताएं कि आपने लेजेंड पोज़िशन कैसे कस्टमाइज़ किया। आपका फीडबैक हम सभी को बेहतर ऑटोमेटेड डॉक्यूमेंट्स बनाने में मदद करता है।


## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}