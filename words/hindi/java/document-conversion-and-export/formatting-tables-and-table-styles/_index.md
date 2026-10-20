---
date: 2026-10-17
description: Aspose.Words for Java के साथ table cells में borders बदलना सीखें, जिसमें
  cell border styles सेट करना, first column style लागू करना, और table contents को
  auto‑fit करना शामिल है।
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: Aspose.Words for Java का उपयोग करके table cells में borders कैसे बदलें
og_description: Aspose.Words for Java का उपयोग करके table cells में borders कैसे बदलें।
  यह गाइड आपको दिखाता है कि cell border thickness कैसे सेट करें, first column style
  कैसे लागू करें, और पेशेवर दस्तावेज़ों के लिए tables को auto‑fit कैसे करें।
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: table cells में borders कैसे बदलें – Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  headline: How to change borders in table cells using Aspose.Words for Java
  type: TechArticle
- description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  name: How to change borders in table cells using Aspose.Words for Java
  steps:
  - name: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
    text: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
    text: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
  - name: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
    text: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
  type: HowTo
- questions:
  - answer: Yes, you can create and apply custom styles programmatically. See the
      [Aspose.Words documentation](https://reference.aspose.com/words/java/) for details.
    question: Can I use custom table styles not included in the default options?
  - answer: Use standard Java logic to inspect cell values, then call the appropriate
      formatting methods (e.g., change background colour if a value exceeds a threshold).
    question: How can I apply conditional formatting to cells?
  - answer: Absolutely. After merging cells, apply shading or borders using the same
      `CellFormat` APIs.
    question: Is it possible to format merged cells the same way as regular cells?
  - answer: Adjust column widths or call `autoFit` again after inserting new data
      to recalculate the layout.
    question: What if I need the table to resize dynamically based on user input?
  - answer: The official [Aspose.Words API documentation](https://reference.aspose.com/words/java/)
      contains a comprehensive set of samples.
    question: Where can I find more examples of table styling?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- Aspose.Words
- Java tables
- document formatting
- border styling
title: Aspose.Words for Java का उपयोग करके table cells में borders कैसे बदलें
url: /hi/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके तालिका कोशिकाओं में बॉर्डर कैसे बदलें

## परिचय

जब आपको डेटा को साफ़, पेशेवर लेआउट में प्रस्तुत करने की आवश्यकता होती है, **सेल बॉर्डर बदलना** उन पहले दृश्य समायोजनों में से एक है जिसे आप लागू करेंगे। जावा में, Aspose.Words आपको एक पूर्ण‑फ़ीचर API देता है जो तालिकाओं को स्टाइल करने, व्यक्तिगत सेल बॉर्डर को समायोजित करने, पहले‑कॉलम शैली को सक्षम करने, और सामग्री के अनुसार ऑटो‑फ़िट करने की अनुमति देता है ताकि तालिका कभी पेज से बाहर न हो। यह ट्यूटोरियल आपको दस्तावेज़ बनाने से लेकर प्रत्येक बॉर्डर को फाइन‑ट्यून करने तक के हर चरण के माध्यम से ले जाता है, और दिखाता है कि वास्तविक‑विश्व रिपोर्ट और इनवॉइस में ये सुविधाएँ क्यों महत्वपूर्ण हैं।

## त्वरित उत्तर
`DocumentBuilder` क्लास का उपयोग प्रोग्रामेटिक रूप से दस्तावेज़ और तालिकाएँ बनाने के लिए किया जाता है।  
- **टेबल बनाने के लिए मुख्य क्लास कौन सी है?** `DocumentBuilder` प्रोग्रामेटिक रूप से टेबल और सेल बनाता है।  
- **मैं एकल सेल की बॉर्डर मोटाई कैसे बदलूँ?** `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)` का उपयोग करें।  
- **क्या मैं पूर्वनिर्धारित तालिका शैली लागू कर सकता हूँ?** हाँ – `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` कॉल करें।  
- **कौन सा मेथड तालिका को उसकी सामग्री के अनुसार ऑटो‑फ़िट करता है?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`।  
- **उत्पादन के लिए क्या लाइसेंस की आवश्यकता है?** गैर‑ट्रायल उपयोग के लिए एक वैध Aspose.Words लाइसेंस आवश्यक है।

## Aspose.Words में “सेल बॉर्डर कैसे बदलें” क्या है?

सेल बॉर्डर बदलना का अर्थ है उन दृश्य रेखाओं को कस्टमाइज़ करना जो सेल्स को अलग करती हैं—रंग, चौड़ाई, और लाइन शैली। Aspose.Words for Java एक ग्रैन्युलर API प्रदान करता है जो आपको ये गुण तालिका, पंक्ति, या व्यक्तिगत‑सेल स्तर पर सेट करने देता है, जिससे आप अपने दस्तावेज़ों की दिखावट पर सटीक नियंत्रण रख सकते हैं।

## Aspose.Words for Java तालिका स्टाइलिंग का उपयोग क्यों करें?

Aspose.Words **35+ इनपुट और आउटपुट फॉर्मेट** (DOCX, PDF, HTML, ODT, आदि) का समर्थन करता है और सामान्य सर्वर हार्डवेयर पर **500‑पेज दस्तावेज़ 3 सेकंड से कम समय** में प्रोसेस कर सकता है, बिना Microsoft Word की आवश्यकता के। यह लाइब्रेरी Windows, Linux, और macOS पर लगातार काम करती है, जिससे आप सर्वर‑साइड पर दस्तावेज़ जनरेट या मॉडिफ़ाई कर सकते हैं, बिल्ट‑इन तालिका शैलियों जैसे *पहला कॉलम शैली* लागू कर सकते हैं, और एक ही मेथड कॉल से तालिकाओं को सामग्री के अनुसार ऑटो‑फ़िट कर सकते हैं।

## पूर्वापेक्षाएँ

1. **Java Development Kit (JDK) 8+** – सुनिश्चित करें `java` आपके PATH में है।  
2. **IDE** – IntelliJ IDEA, Eclipse, या कोई भी एडिटर जो आप पसंद करते हैं।  
3. **Aspose.Words for Java** – नवीनतम JAR [आधिकारिक साइट](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
4. **बुनियादी Java ज्ञान** – आपको Maven/Gradle प्रोजेक्ट बनाना और बाहरी JAR जोड़ना आना चाहिए।

## पैकेज आयात करें

`Document`, `DocumentBuilder`, `Table`, `StyleIdentifier`, और संबंधित क्लासेस `com.aspose.words` नेमस्पेस में स्थित हैं। इस एकल पैकेज को इम्पोर्ट करने से आपको पूरी तालिका‑स्टाइलिंग टूलकिट तक पहुँच मिलती है। `DocumentBuilder` क्लास प्रोग्रामेटिक रूप से दस्तावेज़ बनाने और संशोधित करने के मेथड प्रदान करती है।

```java
import com.aspose.words.*;
```

## सेल बॉर्डर कैसे बदलें

नीचे एक संक्षिप्त, चरण‑दर‑चरण गाइड है जो तालिका बनाता है, एक ग्लोबल बॉर्डर लागू करता है, और फिर एकल सेल के किनारों को कस्टमाइज़ करता है।

### प्रत्यक्ष उत्तर
`Document` Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` तालिकाओं जैसी सामग्री बनाता है। एक नया `Document` लोड करें, `DocumentBuilder` के साथ `Table` डालें, पूरी तालिका के लिए 2‑पॉइंट काली बॉर्डर सेट करें, और फिर तीसरे सेल के बाएँ, दाएँ, ऊपर और नीचे के बॉर्डर को 4 पॉइंट तक बढ़ाएँ। यह तरीका आपको किसी भी सेल को हाइलाइट करने की अनुमति देता है जबकि बाकी तालिका समान रूप से स्टाइलेड रहती है।

### चरण 1: नया दस्तावेज़ लोड करें

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### चरण 2: तालिका बनाएं और ग्लोबल बॉर्डर सेट करें

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### चरण 3: एकल सेल के बॉर्डर बदलें

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### कोड क्या करता है
- **ग्लोबल बॉर्डर** – `table.setBorders` पूरी तालिका को 2‑पॉइंट काली रेखा देता है।  
- **सेल शेडिंग** – व्यक्तिगत सेल्स को रंगने (लाल और हरा) का प्रदर्शन करता है।  
- **कस्टम सेल बॉर्डर** – तीसरे सेल को सभी पक्षों पर 4‑पॉइंट बॉर्डर मिलता है, जिससे वह अलग दिखता है।

## तालिका शैलियों को लागू करना (पहले कॉलम शैली सहित)

तालिका शैलियों से आप एक ही कॉल से सुसंगत लुक लागू कर सकते हैं। हम *पहले कॉलम शैली* को भी सक्षम करेंगे और तालिका को उसकी सामग्री के अनुसार ऑटो‑फ़िट करेंगे।

### प्रत्यक्ष उत्तर
`StyleIdentifier` बिल्ट‑इन तालिका शैलियों को एनेमरेट करता है, और `AutoFitBehavior` निर्धारित करता है कि तालिका अपनी सामग्री के अनुसार कैसे समायोजित होती है। एक नया `Document` बनाएं, `Table` बनाएं, उसका `StyleIdentifier` `MEDIUM_SHADING_1_ACCENT_1` सेट करें, `FirstColumn` और `RowBands` सक्षम करें, फिर `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` कॉल करें ताकि कॉलम स्वचालित रूप से डेटा के अनुसार सिकुड़ें या फैलें।

### चरण 4: स्टाइलिंग के लिए नया दस्तावेज़ बनाएं

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### चरण 5: पूर्वनिर्धारित शैली लागू करें और पहले‑कॉलम फ़ॉर्मेटिंग सक्षम करें

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### चरण 6: डेटा के साथ तालिका भरें

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### यह क्यों महत्वपूर्ण है
- **स्टाइल पहचानकर्ता** – `MEDIUM_SHADING_1_ACCENT_1` तालिका को साफ़, शेडेड लुक देता है।  
- **पहला कॉलम शैली** – पहले कॉलम को हाइलाइट करने से पढ़ने में आसानी बढ़ती है, विशेषकर रिपोर्ट में।  
- **रो बैंड्स** – वैकल्पिक पंक्तियों के रंग बड़े तालिकाओं को आँखों के लिए आसान बनाते हैं।  
- **ऑटो‑फ़िट** – तालिका की चौड़ाई को सामग्री के अनुसार अनुकूलित करता है, जिससे टेक्स्ट कट नहीं होता।

## सामान्य समस्याएँ और ट्रबलशूटिंग

| समस्या | सामान्य कारण | त्वरित समाधान |
|-------|----------------|-----------|
| बॉर्डर नहीं दिख रहे | बॉर्डर सेट करने के बाद `clearFormatting()` का उपयोग | फ़ॉर्मेटिंग साफ़ करने के बाद **बॉर्डर सेट** करें, या उन्हें फिर से लागू करें। |
| मर्ज किए गए सेल्स पर शेडिंग अनदेखी | मर्ज करने से पहले शेडिंग लागू की गई | सेल्स को मर्ज करने के बाद **शेडिंग लागू** करें। |
| तालिका की चौड़ाई पेज मार्जिन से अधिक | ऑटो‑फ़िट लागू नहीं किया गया | `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` कॉल करें या स्थिर चौड़ाई सेट करें। |
| शैली लागू नहीं हुई | गलत `StyleIdentifier` मान | जाँचें कि आप जिस Aspose.Words संस्करण का उपयोग कर रहे हैं, उसमें यह पहचानकर्ता मौजूद है। |

## अक्सर पूछे जाने वाले प्रश्न

**प्र: क्या मैं डिफ़ॉल्ट विकल्पों में नहीं शामिल कस्टम तालिका शैलियों का उपयोग कर सकता हूँ?**  
उ: हाँ, आप प्रोग्रामेटिक रूप से कस्टम शैलियों को बना और लागू कर सकते हैं। विवरण के लिए [Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/java/) देखें।

**प्र: मैं सेल्स पर कंडीशनल फ़ॉर्मेटिंग कैसे लागू करूँ?**  
उ: मानों की जाँच करने के लिए सामान्य Java लॉजिक का उपयोग करें, फिर उपयुक्त फ़ॉर्मेटिंग मेथड कॉल करें (जैसे, यदि मान सीमा से अधिक हो तो बैकग्राउंड रंग बदलें)।

**प्र: क्या मर्ज किए गए सेल्स को सामान्य सेल्स की तरह फ़ॉर्मेट किया जा सकता है?**  
उ: बिल्कुल। सेल्स को मर्ज करने के बाद वही `CellFormat` API का उपयोग करके शेडिंग या बॉर्डर लागू करें।

**प्र: यदि मुझे तालिका को उपयोगकर्ता इनपुट के आधार पर डायनामिक रूप से रिसाइज़ करना हो तो क्या करें?**  
उ: नई डेटा डालने के बाद कॉलम चौड़ाई समायोजित करें या `autoFit` फिर से कॉल करें ताकि लेआउट पुनः गणना हो सके।

**प्र: तालिका स्टाइलिंग के और उदाहरण कहाँ मिलेंगे?**  
उ: आधिकारिक [Aspose.Words API दस्तावेज़ीकरण](https://reference.aspose.com/words/java/) में व्यापक नमूने उपलब्ध हैं।

## निष्कर्ष

आपके पास अब **सेल बॉर्डर बदलने**, *पहले कॉलम शैली* लागू करने, और Aspose.Words for Java का उपयोग करके **तालिका सामग्री को ऑटो‑फ़िट** करने के लिए एक पूर्ण टूलबॉक्स है। इन तकनीकों में महारत हासिल करके आप ऐसे दस्तावेज़ बना सकते हैं जो डेटा‑समृद्ध और दृश्य‑पॉलिश्ड दोनों हों—रिपोर्ट, इनवॉइस, और किसी भी बिज़नेस‑क्रिटिकल आउटपुट के लिए आदर्श।

---

**अंतिम अपडेट:** 2026-10-17  
**परीक्षण किया गया:** Aspose.Words for Java 24.12 (लेखन के समय नवीनतम)  
**लेखक:** Aspose

## संबंधित ट्यूटोरियल

- [Aspose.Words Java फ़ॉर्मेटिंग और स्टाइल ट्यूटोरियल - अपने दस्तावेज़ों को बेहतर बनाएं](/words/java/formatting-styles/)
- [Aspose.Words for Java के साथ उन्नत दस्तावेज़ बॉर्डर: एक व्यापक गाइड](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [Aspose.Words for Java का उपयोग करके दस्तावेज़ में वॉटरमार्क जोड़ें](/words/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}