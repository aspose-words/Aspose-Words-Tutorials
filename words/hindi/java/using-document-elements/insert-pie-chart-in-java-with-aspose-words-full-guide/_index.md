---
category: general
date: 2026-07-29
description: Aspose.Words for Java का उपयोग करके पाई चार्ट डालें और डोनट चार्ट बनाना,
  पाई चार्ट को फॉर्मेट करना, चार्ट को Word में फॉर्मेट करना, तथा चार्ट का आकार कस्टमाइज़
  करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: hi
lastmod: 2026-07-29
og_description: Aspose.Words for Java के साथ पाई चार्ट डालें और जल्दी से डोनट चार्ट
  बनाना, पाई चार्ट फॉर्मेट करना, Word में चार्ट फॉर्मेट करना, तथा पेशेवर दस्तावेज़ों
  के लिए चार्ट का आकार अनुकूलित करना सीखें।
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: जावा में पाई चार्ट सम्मिलित करें – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Aspose.Words के साथ जावा में पाई चार्ट सम्मिलित करें – पूर्ण गाइड
url: /hi/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में Aspose.Words के साथ पाई चार्ट डालें – पूर्ण गाइड

क्या आपने कभी सोचा है कि जावा कोड से Word दस्तावेज़ में **insert pie chart** कैसे डालें? आप अकेले नहीं हैं—कई डेवलपर्स को डेटा को तेज़ी से प्रोग्रामेटिक रूप से विज़ुअलाइज़ करने की ज़रूरत पड़ने पर यह समस्या आती है। अच्छी खबर? Aspose.Words for Java के साथ आप इसे कुछ ही लाइनों में कर सकते हैं, और साथ ही आप **generate doughnut chart**, **format pie chart**, **format chart Word**, और **customize chart size** को अपने ब्रांडिंग के अनुसार अनुकूलित कर सकते हैं।

इस ट्यूटोरियल में हम एक वास्तविक उदाहरण के माध्यम से चलेंगे जो एक खाली दस्तावेज़ बनाकर शुरू होता है, उसमें पाई चार्ट डालता है, कुछ दृश्य गुणों को समायोजित करता है, और अंत में फ़ाइल को सहेजता है। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी जावा प्रोजेक्ट में पेस्ट कर सकते हैं जिसे चार्ट ऑटोमेशन की आवश्यकता है। कोई अतिरिक्त लाइब्रेरी नहीं, कोई मैन्युअल Office इंटरऑप नहीं—सिर्फ साफ़, कंपाइल्ड जावा।

## आपको क्या चाहिए

- **Java 17** (या कोई भी नवीनतम JDK; API पीछे की ओर संगत है)
- **Aspose.Words for Java** 22.12 या नया – आप Maven आर्टिफैक्ट या Aspose साइट से .jar प्राप्त कर सकते हैं।
- एक साधारण IDE (IntelliJ IDEA, Eclipse, VS Code…) – कुछ भी जो आपको `main` मेथड चलाने दे।
- वैकल्पिक: एक लाइसेंस फ़ाइल यदि आप इवैल्यूएशन वॉटरमार्क नहीं चाहते।

यदि आपके पास ये सब है, तो हम सीधे कोड में कूद सकते हैं।

## चरण 1: Aspose.Words के साथ पाई चार्ट डालें

पहला काम हम **insert pie chart** को एक नए दस्तावेज़ में डालना है। यह चरण बाकी सबके लिए मंच तैयार करता है, क्योंकि चार्ट ऑब्जेक्ट हमें सीरीज़, डेटा पॉइंट्स और विज़ुअल ट्यूनिंग तक पहुंच देता है।

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` न केवल चार्ट बनाता है बल्कि एक `Chart` ऑब्जेक्ट भी लौटाता है जिसे हम हेर-फेर कर सकते हैं। चौड़ाई और ऊँचाई के आर्ग्युमेंट आपको **customize chart size** निर्माण के समय ही करने देते हैं, इसलिए बाद में री‑साइज़ करने की ज़रूरत नहीं पड़ती।

## चरण 2: डोनट चार्ट बनाएं (वैकल्पिक)

यदि आपके डिज़ाइन में मध्य में एक छेद चाहिए—जैसे क्लासिक डोनट चार्ट—तो Aspose इसे एक‑लाइनर में बना देता है। वही `Chart` इंस्टेंस को नियमित पाई से डोनट में बदलने के लिए होल साइज को समायोजित किया जाता है।

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** होल साइज केवल `ChartType.DONUT` के लिए प्रभावी होता है। यदि आप टाइप को `PIE` रखते हैं, तो कॉल अनदेखा हो जाता है, इसलिए प्रयोग करने में संकोच न करें।

## चरण 3: पाई चार्ट स्लाइस को फ़ॉर्मेट करें

एक अच्छा विज़ुअल अक्सर किसी विशेष स्लाइस को हाइलाइट करता है। यहाँ हम **format pie chart** करके पहली स्लाइस को 20 पॉइंट बाहर की ओर एक्सप्लोड करते हैं। इससे सबसे महत्वपूर्ण डेटा पॉइंट की ओर पाठक की नजर जाती है।

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** यदि आपके पास कई सीरीज़ हैं तो आप `pieChart.getSeries()` पर लूप लगा सकते हैं और व्यक्तिगत रंग, बॉर्डर या डेटा लेबल सेट कर सकते हैं। यही तरीका है **format chart Word** दस्तावेज़ों को समृद्ध स्टाइलिंग देने का।

## चरण 4: चार्ट में डेटा जोड़ें

डेटा के बिना चार्ट केवल एक सजावटी आकृति है। चलिए इसे एक सरल डेटा सेट देते हैं—जैसे तिमाही बिक्री संख्याएँ।

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** स्पष्ट रूप से `ChartPoint` ऑब्जेक्ट जोड़कर हम सुनिश्चित करते हैं कि चार्ट हमारे बिज़नेस लॉजिक को दर्शाए। `setShowCategoryName` और `setShowValue` कॉल्स **formatting the pie chart** का हिस्सा हैं जो प्रत्येक स्लाइस पर लेबल और संख्या दोनों दिखाते हैं।

## चरण 5: उपस्थिति को फाइन‑ट्यून करें (customize chart size & style)

प्रारंभिक आयामों के अलावा, आप चार्ट की लेजेंड, टाइटल या डेटा लेबल के फ़ॉन्ट को भी समायोजित करना चाह सकते हैं। ये सभी **customize chart size** और समग्र फ़ॉर्मेटिंग के अंतर्गत आते हैं।

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** यदि बाद में आप दस्तावेज़ को PDF में एक्सपोर्ट करने का निर्णय लेते हैं, तो चार्ट का वेक्टर डेटा स्पष्ट रहता है क्योंकि आकार पॉइंट्स में परिभाषित होता है, पिक्सेल में नहीं। यह **format chart Word** और डाउनस्ट्रीम फ़ॉर्मेट्स के लिए एक जीत है।

## चरण 6: दस्तावेज़ को सहेजें और देखें

अंतिम चरण इतना सरल है जितना `doc.save` को कॉल करना। यह एक `.docx` फ़ाइल लिखता है जिसे आप Microsoft Word, LibreOffice, या किसी भी व्यूअर में खोल सकते हैं जो OpenXML फ़ॉर्मेट को सपोर्ट करता है।

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** `PieChart.docx` खोलें और आप एक ठीक‑से आकार का पाई (या डोनट) चार्ट देखेंगे जिसमें एक्सप्लोडेड स्लाइस, टाइटल और लेजेंड होगा—सभी बिना UI को छुए जेनरेट किया गया।

### अपेक्षित आउटपुट

| Element | What you’ll see |
|---------|-----------------|
| Chart type | Pie chart (or doughnut if `holeSize` > 0) |
| Slice explosion | First slice offset by 20 pts |
| Legend | Positioned on the right |
| Title | “Quarterly Sales Distribution” in bold 14 pt |
| Data labels | Category name and value shown on each slice |
| Document | A standard Word `.docx` file ready for sharing |

## सामान्य प्रश्न और समस्याएँ

- **Do I need a license?**  
  इवैल्यूएशन संस्करण परीक्षण के लिए ठीक काम करता है, लेकिन यह वॉटरमार्क जोड़ता है। साफ़ आउटपुट के लिए अपने `aspose.words.lic` फ़ाइल को क्लासपाथ में डालें।

- **Can I use this with Maven?**  
  बिल्कुल। अपने `pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  `pieChart.getSeries()` पर लूप लगाएँ और प्रत्येक सीरीज़ के लिए `setExplosion`, `setFillColor` या अन्य फ़ॉर्मेटिंग लागू करें। यही तरीका है **format pie chart** को मल्टी‑डायमेंशनल डेटा के लिए उपयोग करने का।

- **Is the chart editable in Word after generation?**  
  हाँ—एक बार सहेजने के बाद, आप दस्तावेज़ खोलकर रंग, फ़ॉन्ट या यहाँ तक कि पाई को बार चार्ट में भी बदल सकते हैं यदि आवश्यकता हो।

## निष्कर्ष

हमने अभी-अभी Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में **inserted pie chart** किया, **generate doughnut chart** दिखाया, **format pie chart** के कई तरीके प्रदर्शित किए, **format chart Word** की सर्वोत्तम प्रथाएँ कवर कीं, और एक पॉलिश्ड लुक के लिए **customize chart size** सीखें। ऊपर दिया गया पूर्ण, रन‑एबल उदाहरण किसी भी जावा प्रोजेक्ट में डाला जा सकता है, जिससे आपको COM इंटरऑप या Office इंस्टॉलेशन की ओवरहेड के बिना तुरंत चार्ट ऑटोमेशन मिल जाता है।

अब आगे क्या? डेटा स्रोत को लाइव डेटाबेस से बदलें, थ्रेशहोल्ड के आधार पर कंडीशनल रंग जोड़ें, या समान दस्तावेज़ को PDF में एक्सपोर्ट करके प्रिंट‑रेडी रिपोर्ट बनाएं। इन सभी चरणों का आधार हमने पहले ही रख दिया है, इसलिए ट्रांज़िशन सहज रहेगा।

यदि आपको कोई समस्या आती है या आगे के सुधारों के लिए विचार हैं—शायद स्टैक्ड बार या लाइन चार्ट—तो नीचे टिप्पणी करें। हैप्पी चार्टिंग!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}