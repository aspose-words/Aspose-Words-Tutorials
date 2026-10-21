---
category: general
date: 2026-08-20
description: Java में पाई चार्ट में लीडर लाइन्स जल्दी जोड़ें। चार्ट API का उपयोग करके
  स्लाइस को इन्सर्ट, एक्सप्लोड, रीकलर और लेबल करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: hi
lastmod: 2026-08-20
og_description: जावा में पाई चार्ट में लीडर लाइन्स जोड़ें एक संक्षिप्त उदाहरण के साथ।
  चार्ट API का उपयोग करके स्लाइस को इन्सर्ट, एक्सप्लोड, रीकलर और लेबल करने के लिए
  इस गाइड का पालन करें।
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: जावा में पाई चार्ट में लीडर लाइन्स जोड़ें – चरण‑दर‑चरण चार्ट API गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: जावा में चार्ट API का उपयोग करके पाई चार्ट में लीडर लाइन्स कैसे जोड़ें
url: /hi/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में Chart API के साथ पाई चार्ट में लीडर लाइन्स कैसे जोड़ें

यदि आपको जावा में **पाई चार्ट में लीडर लाइन्स जोड़ें** हैं, तो यह गाइड आपको पूरी प्रक्रिया से गुज़राएगा। आप देखेंगे कि पाई चार्ट कैसे डालें, ज़ोर देने के लिए एक स्लाइस को एक्सप्लोड करें, उसका रंग बदलें, और अंत में लीडर लाइन्स सक्षम करें जो एक्सप्लोड किए गए भाग को लेबल करती हैं। यह उदाहरण कई जावा रिपोर्टिंग लाइब्रेरीज़ में पाए जाने वाले मानक Chart API का उपयोग करता है। कोई बाहरी टूल आवश्यक नहीं है, और कोड किसी भी JDK 8+ वातावरण पर चलता है।

## आप क्या हासिल करेंगे

* कस्टम आकार के साथ `Chart` प्रकार `ChartType.PIE` बनाएं।  
* ध्यान आकर्षित करने के लिए पहले स्लाइस को एक्सप्लोड करें।  
* एक्सप्लोड किए गए स्लाइस का सेक्टर रंग नीला सेट करें।  
* **पाई चार्ट में लीडर लाइन्स जोड़ें** ताकि स्लाइस लेबल स्पष्ट रूप से जुड़ा रहे।

आपके पास पहले से ही क्लासपाथ में Chart लाइब्रेरी के साथ एक जावा प्रोजेक्ट होना चाहिए। यदि आप Maven का उपयोग कर रहे हैं, तो प्रीरेक्विज़िट सेक्शन में दिखाए गए डिपेंडेंसी को जोड़ें।

## पूर्वापेक्षाएँ

* JDK 8 या उससे नया स्थापित हो।  
* Chart लाइब्रेरी (उदाहरण के लिए `com.example.chart:chart-api:2.5.0`)।  
* जावा क्लासेस और मेथड कॉल्स की बुनियादी समझ।

---

## पाई चार्ट में लीडर लाइन्स कैसे जोड़ें

नीचे एक पूर्ण, चलाने योग्य प्रोग्राम दिया गया है जो हर कदम को दर्शाता है। कोड जानबूझकर स्व-निहित है ताकि आप इसे बिना किसी संशोधन के कॉपी, पेस्ट और चलाएं।

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### प्रत्येक चरण की व्याख्या

| चरण | कोड क्या करता है | क्यों महत्वपूर्ण है |
|------|-------------------|----------------|
| **1️⃣ पाई चार्ट डालें** | `builder.insertChart(ChartType.PIE, 400, 300)` 400 × 300 पिक्सेल पाई चार्ट बनाता है। | चार्ट कंटेनर स्थापित करता है और उसके आयाम निर्धारित करता है, जो लेबल प्लेसमेंट और लीडर लाइन की लंबाई को प्रभावित करते हैं। |
| **2️⃣ पहले स्लाइस को एक्सप्लोड करें** | `setExplosion(20)` स्लाइस को त्रिज्या के 20 % से ऑफसेट करता है। | एक एक्सप्लोड किया गया स्लाइस दर्शक की नजर आकर्षित करता है और लीडर लाइन को दृश्यमान बनाता है। |
| **3️⃣ सेक्टर रंग सेट करें** | `setSectorColor(Color.BLUE)` स्लाइस की भराव को नीला बदलता है। | रंग कंट्रास्ट पठनीयता बढ़ाता है, विशेषकर जब स्लाइस हाइलाइट किया गया हो। |
| **4️⃣ लीडर लाइन्स सक्षम करें** | `setLeaderLines(true)` कनेक्टर लाइन्स को चालू करता है जो स्लाइस को उसके लेबल से जोड़ती हैं। | लीडर लाइन्स सुनिश्चित करती हैं कि लेबल बाहर ले जाने पर भी पठनीय रहे। |

`saveAsPng` कॉल वैकल्पिक है लेकिन दृश्य परिणाम की पुष्टि के लिए उपयोगी है। प्रोग्राम चलाने के बाद, आपको नीचे दिखाए गए समान एक छवि दिखनी चाहिए।

![पाई चार्ट में लीडर लाइन्स जोड़ें](https://example.com/assets/pie-leader-lines.png "पाई चार्ट में लीडर लाइन्स जोड़ें – एक्सप्लोड स्लाइस नीले रंग और लीडर लाइन्स के साथ")

*चित्र: एक पाई चार्ट जहाँ पहला स्लाइस एक्सप्लोड किया गया है, नीला रंग दिया गया है, और लीडर लाइन द्वारा उसके लेबल से जुड़ा है।*

## लीडर लाइन्स को अनुकूलित करना (उन्नत)

बेसिक `setLeaderLines(true)` कॉल लाइब्रेरी की डिफ़ॉल्ट शैली का उपयोग करता है। आप दिखावट को आगे नियंत्रित कर सकते हैं:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

ये विकल्प उपयोगी होते हैं जब आपको कॉरपोरेट ब्रांडिंग से मेल खाना हो या एक्सेसिबिलिटी सुधारनी हो।

### कई सीरीज़ को संभालना

यदि आपके पाई चार्ट में एक से अधिक सीरीज़ हैं, तो आप केवल किसी विशिष्ट स्लाइस के लिए लीडर लाइन्स चाहते हैं। सही तत्व को लक्षित करने के लिए सीरीज़ इंडेक्स का उपयोग करें:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

जब स्लाइस एक्सप्लोड नहीं किया गया हो, तो लीडर लाइन आमतौर पर स्वतः छिप जाती है, लेकिन आप इसे `setLeaderLineEnabled(true)` से मजबूर कर सकते हैं।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | लक्षण | समाधान |
|--------|---------|-----|
| **लीडर लाइन्स नहीं दिख रही** | चार्ट कनेक्टर्स के बिना रेंडर होता है। | सुनिश्चित करें कि स्लाइस एक्सप्लोड किया गया है (`setExplosion` > 0) या स्लाइस पर स्पष्ट रूप से लीडर लाइन्स सक्षम करें। |
| **लेबल ओवरलैप** | लेबल एक-दूसरे से टकराते हैं। | चार्ट का आकार बढ़ाएँ या `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)` सेट करें। |
| **रंग लागू नहीं हुआ** | स्लाइस डिफ़ॉल्ट रंग में रहता है। | जाँचें कि आप सही सीरीज़ इंडेक्स को लक्षित कर रहे हैं (`getSeries().get(0)`)। |
| **इमेज सेव नहीं हुई** | `saveAsPng` अपवाद फेंकता है। | आउटपुट डायरेक्टरी की लिखने की अनुमति जाँचें और सुनिश्चित करें कि लाइब्रेरी PNG एक्सपोर्ट को सपोर्ट करती है। |

## पूर्ण स्रोत सूची

सुविधा के लिए, यहाँ फिर से पूरा स्रोत फ़ाइल दिया गया है, जिसमें इम्पोर्ट्स और टिप्पणियाँ शामिल हैं:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

इस प्रोग्राम को चलाने से `pie-with-leader-lines.png` बनता है, जो एक पाई चार्ट दिखाता है जिसमें एक्सप्लोड किया गया नीला स्लाइस और स्पष्ट लीडर लाइन्स स्लाइस लेबल की ओर इशारा करती हैं।

## निष्कर्ष

अब आप जावा में Chart API का उपयोग करके **पाई चार्ट में लीडर लाइन्स जोड़ना** जानते हैं। प्रक्रिया में `ChartType.PIE` डालना, इच्छित स्लाइस को एक्सप्लोड करना, उसका रंग अनुकूलित करना, और लीडर लाइन्स सक्षम करना शामिल है। वैकल्पिक स्टाइलिंग विकल्पों के साथ आप लाइन का रंग, मोटाई, और लेबल प्लेसमेंट को किसी भी दृश्य आवश्यकता के अनुसार फाइन‑ट्यून कर सकते हैं।

अगला, संबंधित विषयों जैसे **pie chart explosion Java**, **set sector color Chart API**, और **builder.insertChart usage** का अन्वेषण करें ताकि डोनट चार्ट, स्टैक्ड पाईज़, या इंटरैक्टिव डैशबोर्ड जैसे अधिक परिष्कृत विज़ुअलाइज़ेशन बना सकें।

विभिन्न स्लाइस इंडेक्स, रंग, और लीडर‑लाइन शैलियों के साथ प्रयोग करने में संकोच न करें—आपके चार्ट प्रत्येक बदलाव के साथ अधिक सूचनात्मक और दृश्य रूप से आकर्षक बनेंगे। कोडिंग का आनंद लें!

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [चार्ट की एक्सिस में डेट टाइम वैल्यूज जोड़ें](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Aspose.Words for .NET का उपयोग करके वर्ड में कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}