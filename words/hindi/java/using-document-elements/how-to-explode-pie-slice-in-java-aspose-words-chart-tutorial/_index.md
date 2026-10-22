---
category: general
date: 2026-08-07
description: Aspose.Words का उपयोग करके जावा में पाई स्लाइस को एक्सप्लोड कैसे करें।
  पाई में लीडर लाइन्स जोड़ना सीखें, वर्ड चार्ट बनाएं, और पाई चार्ट स्लाइस को कस्टमाइज़
  करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: hi
lastmod: 2026-08-07
og_description: Java में Aspose.Words के साथ पाई स्लाइस को एक्सप्लोड कैसे करें। यह
  गाइड दिखाता है कि पाई में लीडर लाइन्स कैसे जोड़ें, Word चार्ट बनाएं, और स्पष्ट दृश्य
  प्रभाव के लिए पाई चार्ट स्लाइस को कैसे कस्टमाइज़ करें।
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Java में पाई स्लाइस को कैसे विस्फोटित करें – Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Java में पाई स्लाइस को कैसे बाहर निकालें – Aspose.Words चार्ट ट्यूटोरियल
url: /hi/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में पाई स्लाइस को एक्सप्लोड कैसे करें – Aspose.Words चार्ट ट्यूटोरियल

यदि आपको Java का उपयोग करके Word दस्तावेज़ में **पाई स्लाइस को एक्सप्लोड करने** का तरीका जानना है, तो यह ट्यूटोरियल आपकी मदद करेगा। हम आपको **पाई चार्ट में लीडर लाइन्स जोड़ने** का तरीका, **java create word chart** ऑब्जेक्ट्स, और **पाई चार्ट स्लाइस को कस्टमाइज़ करने** के बारे में भी दिखाएंगे ताकि एक परिष्कृत परिणाम मिले। इस गाइड के अंत तक आपके पास एक पूर्ण, चलाने योग्य उदाहरण होगा जिसे आप किसी भी Java प्रोजेक्ट में डाल सकते हैं।

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## आवश्यकताएँ

* Java Development Kit (JDK) 8 या उससे ऊपर।
* निर्भरता प्रबंधन के लिए Maven या Gradle।
* Aspose.Words for Java लाइसेंस (नि:शुल्क मूल्यांकन सीखने के उद्देश्य से काम करता है)।
* Java सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड अवधारणाओं की बुनियादी परिचितता।

> **Pro tip:** यद्यपि Aspose.Words एक मुफ्त ट्रायल प्रदान करता है, लाइसेंस खरीदने से उत्पन्न दस्तावेज़ों से मूल्यांकन वाटरमार्क हट जाता है।

## इस ट्यूटोरियल में क्या कवर किया गया है

* शुरू से एक नया Word दस्तावेज़ बनाना।  
* `DocumentBuilder` का उपयोग करके **pie chart** सम्मिलित करना।  
* डेटा पॉइंट को उजागर करने के लिए **Exploding a pie slice**।  
* स्पष्ट लेबलिंग के लिए **Adding leader lines to pie**।  
* स्लाइस की उपस्थिति को कस्टमाइज़ करना, जैसे रंग और बॉर्डर।  
* दस्तावेज़ को डिस्क पर सहेजना और परिणाम की पुष्टि करना।

---

## Java में Aspose.Words के साथ पाई स्लाइस को एक्सप्लोड कैसे करें

पहला कदम चार्ट ऑब्जेक्ट को सेट अप करना और इच्छित स्लाइस को एक्सप्लोड करना है। Aspose.Words `Shape` क्लास के माध्यम से चार्ट को उजागर करता है, और प्रत्येक स्लाइस एक `ChartPoint` है। `Explosion` प्रॉपर्टी सेट करके आप नियंत्रित करते हैं कि स्लाइस कितनी दूरी तक बाहर की ओर जाता है।

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**यह क्यों काम करता है:**  
`setExplosion(20)` चार्ट इंजन को बताता है कि स्लाइस को चार्ट के केंद्र से 20 पॉइंट्स की दूरी पर ऑफसेट किया जाए। मान सापेक्ष है; बड़े नंबर अधिक नाटकीय प्रभाव बनाते हैं। आप इंडेक्स बदलकर (`get(1)`, `get(2)`, …) किसी भी स्लाइस को एक्सप्लोड कर सकते हैं।

## स्पष्ट लेबल के लिए पाई में लीडर लाइन्स जोड़ें

लीडर लाइन्स स्लाइस के लेबल को उसकी किनारे से जोड़ती हैं, जो विशेष रूप से तब उपयोगी होती हैं जब स्लाइस एक्सप्लोड किए गए हों या चार्ट में कई छोटे सेक्शन हों। `setLeaderLines(true)` कॉल इस फीचर को पूरी सीरीज़ के लिए सक्षम करती है।

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**आपको लीडर लाइन्स की आवश्यकता क्यों है:**  
जब कोई स्लाइस एक्सप्लोड किया जाता है, तो डिफ़ॉल्ट लेबल अन्य तत्वों के साथ ओवरलैप हो सकता है। लीडर लाइन्स स्लाइस से टेक्स्ट बॉक्स तक एक छोटी रेखा खींचकर लेबल को पठनीय बनाती हैं।

## Java में Word चार्ट बनाना – डेटा सीरीज़ सम्मिलित करना

डेटा के बिना चार्ट बहुत उपयोगी नहीं होता। आपको सीरीज़ को श्रेणियों और मानों से भरना होगा। नीचे हम बाजार हिस्सेदारी दर्शाने वाली तीन श्रेणियां जोड़ते हैं।

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**व्याख्या:**  
`ChartSeries` दोनों श्रेणियों (स्लाइस के नाम) और संख्यात्मक मानों को रखता है। `ShowCategoryName` और `ShowPercentage` को सक्षम करने से चार्ट स्वयं स्पष्ट बन जाता है, जो पहले जोड़ी गई लीडर लाइन्स के साथ अच्छी तरह मेल खाता है।

## एक्सप्लोजन से आगे पाई चार्ट स्लाइस को कस्टमाइज़ करें

स्लाइस को एक्सप्लोड करने के अलावा, आप अक्सर रंग, बॉर्डर को समायोजित करना या पूरी तरह से स्लाइस को छिपाना चाहते हैं। नीचे दिया गया स्निपेट तीन सामान्य कस्टमाइज़ेशन दिखाता है:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**स्लाइस को कस्टमाइज़ क्यों करें:**  
कस्टम रंग चार्ट को कॉरपोरेट ब्रांडिंग के साथ संरेखित करते हैं, जबकि बॉर्डर प्रिंटेड पेजों पर पठनीयता बढ़ाते हैं। स्लाइस को छिपाना तब उपयोगी होता है जब आप डेटा मॉडल को अपरिवर्तित रखना चाहते हैं लेकिन दृश्य आउटपुट से किसी श्रेणी को अस्थायी रूप से हटाना चाहते हैं।

## दस्तावेज़ सहेजें और परिणाम की पुष्टि करें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप उत्पन्न `.docx` को Microsoft Word, LibreOffice, या किसी भी व्यूअर में खोल सकते हैं जो इस फ़ॉर्मेट को सपोर्ट करता है।

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**अपेक्षित आउटपुट:**  
`PieChartDemo.docx` खोलने पर, आप एक पाई चार्ट देखेंगे जहाँ पहला स्लाइस (Product A) बाहर की ओर एक्सप्लोड किया गया है, लीडर लाइन्स प्रत्येक स्लाइस से उसके लेबल की ओर इशारा करती हैं, और स्लाइस कस्टम हरे, नीले और नारंगी रंगों में दिखते हैं। छिपा हुआ स्लाइस (Product C) दिखाई नहीं देगा, लेकिन प्रतिशत अभी भी 100 % का योग रहेगा क्योंकि डेटा चार्ट की सीरीज़ में बना रहता है।

---

## पूरा, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं, बशर्ते अपने प्रोजेक्ट में Aspose.Words निर्भरता जोड़ें।

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**निर्भरता (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## आप को आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Java के लिए Aspose.Words का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words Java के साथ Word दस्तावेज़ लोड करना: व्यापक गाइड](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फॉर्म फ़ील्ड बनाना और सामग्री जोड़ना](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}