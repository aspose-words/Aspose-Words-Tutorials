---
date: 2025-11-28
description: Aspose.Words for Java का उपयोग करके सेल बॉर्डर बदलना और टेबल को फॉर्मेट
  करना सीखें। यह चरण‑दर‑चरण गाइड बॉर्डर सेट करने, पहले कॉलम की शैली लागू करने, टेबल
  सामग्री को ऑटो‑फ़िट करने, और टेबल शैलियों को लागू करने को कवर करता है।
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: टेबल में सेल बॉर्डर कैसे बदलें – Aspose.Words for Java
url: /hi/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# टेबल में सेल बॉर्डर बदलने का तरीका – Aspose.Words for Java

## परिचय

डॉक्यूमेंट फ़ॉर्मेटिंग की बात आए तो टेबल्स एक महत्वपूर्ण भूमिका निभाते हैं, और **सेल बॉर्डर कैसे बदलें** यह जानना स्पष्ट, पेशेवर लेआउट बनाने के लिए आवश्यक है। यदि आप Java और Aspose.Words के साथ विकास कर रहे हैं, तो आपके पास पहले से ही एक शक्तिशाली टूलकिट है। इस ट्यूटोरियल में हम टेबल फ़ॉर्मेटिंग, सेल बॉर्डर बदलने, *पहले कॉलम स्टाइल* लागू करने, और *ऑटो‑फ़िट टेबल कंटेंट्स* का उपयोग करके आपके डॉक्यूमेंट को परिपूर्ण बनाने की पूरी प्रक्रिया को समझेंगे।

## त्वरित उत्तर
- **टेबल बनाने के लिए मुख्य क्लास कौन सी है?** `DocumentBuilder` प्रोग्रामेटिक रूप से टेबल और सेल बनाता है।  
- **एकल सेल की बॉर्डर मोटाई कैसे बदलें?** `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)` का उपयोग करें।  
- **क्या मैं प्री‑डिफाइंड टेबल स्टाइल लागू कर सकता हूँ?** हाँ – `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` को कॉल करें।  
- **कौन सा मेथड टेबल को उसकी सामग्री के अनुसार ऑटो‑फ़िट करता है?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`।  
- **प्रोडक्शन के लिए लाइसेंस की आवश्यकता है क्या?** गैर‑ट्रायल उपयोग के लिए एक वैध Aspose.Words लाइसेंस आवश्यक है।

## Aspose.Words में “सेल बॉर्डर कैसे बदलें” क्या है?

सेल बॉर्डर बदलना का अर्थ है उन दृश्य रेखाओं को कस्टमाइज़ करना जो सेल्स को अलग करती हैं—रंग, चौड़ाई, और लाइन स्टाइल। Aspose.Words एक समृद्ध API प्रदान करता है जिससे आप टेबल, रो, या व्यक्तिगत‑सेल स्तर पर इन गुणों को समायोजित कर सकते हैं, जिससे आपके डॉक्यूमेंट की उपस्थिति पर सूक्ष्म नियंत्रण मिलता है।

## Java टेबल स्टाइलिंग के लिए Aspose.Words क्यों उपयोग करें?

- **प्लैटफ़ॉर्म पर समान लुक** – वही स्टाइलिंग कोड Windows, Linux, और macOS पर काम करता है।  
- **Microsoft Word पर निर्भरता नहीं** – सर्वर‑साइड पर डॉक्यूमेंट जनरेट या मॉडिफ़ाई करें।  
- **समृद्ध स्टाइल लाइब्रेरी** – बिल्ट‑इन टेबल स्टाइल्स (जैसे *first column style*) और पूर्ण ऑटो‑फ़िट क्षमताएँ।  

## पूर्वापेक्षाएँ

1. **Java Development Kit (JDK) 8+** – सुनिश्चित करें `java` आपके PATH में है।  
2. **IDE** – IntelliJ IDEA, Eclipse, या कोई भी एडिटर जो आप पसंद करते हैं।  
3. **Aspose.Words for Java** – नवीनतम JAR [आधिकारिक साइट](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
4. **बुनियादी Java ज्ञान** – आपको Maven/Gradle प्रोजेक्ट बनाना और बाहरी JAR जोड़ना आता होना चाहिए।

## पैकेज इम्पोर्ट करें

टेबल्स के साथ काम शुरू करने के लिए आपको कोर Aspose.Words क्लासेज़ की आवश्यकता होगी:

```java
import com.aspose.words.*;
```

यह एकल इम्पोर्ट आपको `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier`, और कई अन्य यूटिलिटीज़ तक पहुंच देता है।

## सेल बॉर्डर कैसे बदलें

नीचे हम एक साधारण टेबल बनाएँगे, उसकी समग्र बॉर्डर बदलेंगे, फिर व्यक्तिगत सेल्स को कस्टमाइज़ करेंगे।

### चरण 1: नया डॉक्यूमेंट लोड करें

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### चरण 2: टेबल बनाएं और ग्लोबल बॉर्डर सेट करें

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

### चरण 3: एकल सेल की बॉर्डर बदलें

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
- **ग्लोबल बॉर्डर** – `table.setBorders` पूरे टेबल को 2‑पॉइंट काली लाइन देता है।  
- **सेल शेडिंग** – व्यक्तिगत सेल्स (लाल और हरा) को रंगने का उदाहरण दिखाता है।  
- **कस्टम सेल बॉर्डर** – तीसरे सेल को सभी पक्षों पर 4‑पॉइंट बॉर्डर मिलता है, जिससे वह प्रमुख दिखता है।

## टेबल स्टाइल्स लागू करना (पहले कॉलम स्टाइल सहित)

टेबल स्टाइल्स आपको एक ही कॉल से सुसंगत लुक देने की अनुमति देते हैं। हम यह भी दिखाएंगे कि *पहले कॉलम स्टाइल* कैसे सक्षम करें और टेबल को उसकी सामग्री के अनुसार ऑटो‑फ़िट करें।

### चरण 4: स्टाइलिंग के लिए नया डॉक्यूमेंट बनाएं

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### चरण 5: प्री‑डिफाइंड स्टाइल लागू करें और पहले कॉलम फॉर्मेटिंग सक्षम करें

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### चरण 6: टेबल में डेटा भरें

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
- **स्टाइल आइडेंटिफायर** – `MEDIUM_SHADING_1_ACCENT_1` टेबल को साफ़, शेडेड लुक देता है।  
- **पहले कॉलम स्टाइल** – पहले कॉलम को हाइलाइट करने से पठनीयता बढ़ती है, विशेषकर रिपोर्ट्स में।  
- **रो बैंड्स** – वैकल्पिक रो रंग बड़े टेबल्स को आँखों के लिए आसान बनाते हैं।  
- **ऑटो‑फ़िट** – टेबल की चौड़ाई को सामग्री के अनुसार अनुकूलित करता है, जिससे टेक्स्ट कट नहीं होता।

## सामान्य समस्याएँ एवं ट्रबलशूटिंग

| समस्या | सामान्य कारण | त्वरित समाधान |
|-------|----------------|-----------|
| बॉर्डर नहीं दिख रहे | बॉर्डर सेट करने के बाद `clearFormatting()` का उपयोग | **बॉर्डर को क्लियर फ़ॉर्मेटिंग के बाद** सेट करें, या फिर से लागू करें। |
| मर्ज्ड सेल्स पर शेडिंग अनदेखी | मर्ज करने से पहले शेडिंग लागू की | **सेल्स को मर्ज करने के बाद** शेडिंग लागू करें। |
| टेबल की चौड़ाई पेज मार्जिन से अधिक | ऑटो‑फ़िट नहीं लागू किया गया | `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` कॉल करें या फिक्स्ड विड्थ सेट करें। |
| स्टाइल लागू नहीं हो रहा | गलत `StyleIdentifier` वैल्यू | सुनिश्चित करें कि वह आइडेंटिफायर आपके उपयोग किए जा रहे Aspose.Words संस्करण में मौजूद है। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं डिफॉल्ट विकल्पों में नहीं मौजूद कस्टम टेबल स्टाइल्स का उपयोग कर सकता हूँ?**  
उत्तर: हाँ, आप प्रोग्रामेटिक रूप से कस्टम स्टाइल बना और लागू कर सकते हैं। विवरण के लिए [Aspose.Words डॉक्यूमेंटेशन](https://reference.aspose.com/words/java/) देखें।

**प्रश्न: मैं सेल्स पर कंडीशनल फ़ॉर्मेटिंग कैसे लागू करूँ?**  
उत्तर: सेल वैल्यूज़ की जाँच करने के लिए सामान्य Java लॉजिक उपयोग करें, फिर उपयुक्त फ़ॉर्मेटिंग मेथड्स कॉल करें (जैसे, यदि मान सीमा से अधिक हो तो बैकग्राउंड रंग बदलें)।

**प्रश्न: क्या मर्ज्ड सेल्स को सामान्य सेल्स की तरह फ़ॉर्मेट किया जा सकता है?**  
उत्तर: बिल्कुल। सेल्स को मर्ज करने के बाद वही `CellFormat` API का उपयोग करके शेडिंग या बॉर्डर लागू करें।

**प्रश्न: यदि मुझे टेबल को उपयोगकर्ता इनपुट के आधार पर डायनामिक रूप से रिसाइज़ करना हो तो?**  
उत्तर: कॉलम चौड़ाई समायोजित करें या नया डेटा डालने के बाद `autoFit` फिर से कॉल करें ताकि लेआउट पुनः गणना हो सके।

**प्रश्न: टेबल स्टाइलिंग के और उदाहरण कहाँ मिल सकते हैं?**  
उत्तर: आधिकारिक [Aspose.Words API डॉक्यूमेंटेशन](https://reference.aspose.com/words/java/) में व्यापक सैंपल सेट उपलब्ध है।

## निष्कर्ष

अब आपके पास **सेल बॉर्डर बदलने**, *पहले कॉलम स्टाइल* लागू करने, और Aspose.Words for Java के साथ **ऑटो‑फ़िट टेबल कंटेंट्स** करने के लिए पूर्ण टूलबॉक्स है। इन तकनीकों में महारत हासिल करके आप ऐसे डॉक्यूमेंट बना सकते हैं जो डेटा‑समृद्ध और दृश्य‑आकर्षक दोनों हों—रिपोर्ट्स, इनवॉइस, और किसी भी बिज़नेस‑क्रिटिकल आउटपुट के लिए एकदम उपयुक्त।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**अंतिम अपडेट:** 2025-11-28  
**परीक्षण किया गया:** Aspose.Words for Java 24.12 (लेखन के समय नवीनतम)  
**लेखक:** Aspose