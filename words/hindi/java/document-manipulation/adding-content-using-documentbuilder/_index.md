---
date: 2026-01-01
description: Aspose.Words for Java DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना
  और टेक्स्ट, टेबल, इमेज, हाइपरलिंक आदि जोड़ना सीखें। डेवलपर्स के लिए चरण-दर-चरण गाइड।
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड कैसे
  बनाएं और सामग्री जोड़ें
url: /hi/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में DocumentBuilder का उपयोग करके सामग्री जोड़ना

## Aspose.Words for Java में DocumentBuilder का उपयोग करके सामग्री जोड़ने का परिचय

इस चरण‑दर‑चरण गाइड में, आप **फ़ॉर्म फ़ील्ड्स** बनाएँगे और Aspose.Words for Java के साथ एक Word दस्तावेज़ में विभिन्न प्रकार की सामग्री—टेक्स्ट, टेबल, क्षैतिज रूल, HTML, हाइपरलिंक, इमेज़ और अधिक—जोड़ेंगे। चाहे आप रिपोर्ट, कॉन्ट्रैक्ट टेम्पलेट, या इंटरैक्टिव फ़ॉर्म बना रहे हों, `DocumentBuilder` क्लास आपको हर तत्व पर सूक्ष्म नियंत्रण देती है। चलिए शुरू करते हैं!

## त्वरित उत्तर
- **फ़ॉर्म फ़ील्ड्स कैसे बनाएं?** `DocumentBuilder` पर `insertTextInput`, `insertCheckBox`, या `insertComboBox` का उपयोग करें।
- **साधारण टेक्स्ट जोड़ने की विधि कौन सी है?** `builder.write("Your text")` या `builder.writeln("Your text")` कॉल करें।
- **क्या मैं क्षैतिज रूल डाल सकता हूँ?** हाँ—`builder.insertHorizontalRule()` एक लाइन सेपरेटर जोड़ता है।
- **HTML कैसे एम्बेड करें?** `builder.insertHtml("<p>HTML content</p>")` का उपयोग करें।
- **इनलाइन इमेज़ कैसे जोड़ें?** `builder.insertImage("path/to/image.png")` इमेज़ को टेक्स्ट प्रवाह में रखता है।

## `DocumentBuilder` क्या है और फ़ॉर्म फ़ील्ड्स बनाने के लिए इसका उपयोग क्यों करें?

`DocumentBuilder` Aspose.Words का फ्लुएंट API है जो प्रोग्रामेटिक रूप से Word दस्तावेज़ों को बनाने और संपादित करने के लिए उपयोग होता है। यह लो‑लेवल OpenXML संरचना को एब्स्ट्रैक्ट करता है, जिससे आप *क्या* जोड़ना चाहते हैं—जैसे **फ़ॉर्म फ़ील्ड्स**—पर ध्यान केंद्रित कर सकते हैं, न कि *XML कैसे दिखता है*। यह डायनामिक फ़ॉर्म, कॉन्ट्रैक्ट या किसी भी दस्तावेज़ के लिए आदर्श है जिसे उपयोगकर्ता इंटरैक्शन की आवश्यकता होती है।

## पूर्वापेक्षाएँ

शुरू करने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी स्थापित है। आप इसे [यहाँ](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं।

## टेक्स्ट जोड़ना (टेक्स्ट कैसे जोड़ें)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## टेबल जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## क्षैतिज रूल जोड़ना (होरिज़ॉन्टल रूल जोड़ें)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## फ़ॉर्म फ़ील्ड्स जोड़ना (फ़ॉर्म फ़ील्ड्स बनाएं)

### टेक्स्ट इनपुट फ़ॉर्म फ़ील्ड

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### चेक बॉक्स फ़ॉर्म फ़ील्ड

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### कॉम्बो बॉक्स फ़ॉर्म फ़ील्ड

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## HTML जोड़ना (HTML इन्सर्ट शब्द)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## हाइपरलिंक जोड़ना (हाइपरलिंक कैसे जोड़ें)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## सामग्री तालिका (Table of Contents) जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## इमेज़ जोड़ना

### इनलाइन इमेज़ (इनलाइन इमेज़ इन्सर्ट करें)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### फ़्लोटिंग इमेज़

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## पैराग्राफ जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## कर्सर को मूव करना (स्टेप 10)

आप `moveToParagraph`, `moveToCell` आदि जैसी मेथड्स का उपयोग करके दस्तावेज़ में कर्सर की स्थिति को नियंत्रित कर सकते हैं।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

ये कुछ सामान्य ऑपरेशन्स हैं जिन्हें आप Aspose.Words for Java के `DocumentBuilder` का उपयोग करके कर सकते हैं। अधिक उन्नत फीचर्स और कस्टमाइज़ेशन विकल्पों के लिए लाइब्रेरी की डॉक्यूमेंटेशन देखें। दस्तावेज़ निर्माण का आनंद लें!

## निष्कर्ष

इस व्यापक गाइड में, हमने दिखाया है कि कैसे **फ़ॉर्म फ़ील्ड्स** बनाएँ और विभिन्न प्रकार की सामग्री—टेक्स्ट, टेबल, क्षैतिज रूल, HTML, हाइपरलिंक, सामग्री तालिका, इमेज़, फ़ॉर्मेटेड पैराग्राफ, और कर्सर नेविगेशन—Aspose.Words for Java के `DocumentBuilder` का उपयोग करके जोड़ें। अब आपके पास प्रोग्रामेटिक रूप से डायनामिक, इंटरैक्टिव Word दस्तावेज़ बनाने की ठोस नींव है।

## अक्सर पूछे जाने वाले प्रश्न

### Q: Aspose.Words for Java क्या है?

A: Aspose.Words for Java एक Java लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Microsoft Word दस्तावेज़ बनाने, संशोधित करने और मैनिपुलेट करने की सुविधा देती है। यह दस्तावेज़ जनरेशन, फ़ॉर्मेटिंग और कंटेंट इन्सर्शन के लिए विस्तृत फीचर्स प्रदान करती है।

### Q: मैं अपने दस्तावेज़ में सामग्री तालिका कैसे जोड़ सकता हूँ?

A: सामग्री तालिका जोड़ने के लिए, `DocumentBuilder` का उपयोग करके एक TOC फ़ील्ड इन्सर्ट करें और अपनी सामग्री जोड़ने के बाद `doc.updateFields()` कॉल करें।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Aspose.Words for Java का उपयोग करके दस्तावेज़ में इमेज़ कैसे इन्सर्ट करें?

A: आप `DocumentBuilder` का उपयोग करके इमेज़, इनलाइन और फ़्लोटिंग दोनों, इन्सर्ट कर सकते हैं।

#### इनलाइन इमेज़:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### फ़्लोटिंग इमेज़:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: क्या मैं सामग्री जोड़ते समय टेक्स्ट और पैराग्राफ को फ़ॉर्मेट कर सकता हूँ?

A: हाँ, आप `DocumentBuilder` का उपयोग करके टेक्स्ट और पैराग्राफ को फ़ॉर्मेट कर सकते हैं। कंटेंट लिखने से पहले फ़ॉन्ट प्रॉपर्टीज़, पैराग्राफ अलाइनमेंट, इंडेंटेशन आदि सेट करें।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: मैं दस्तावेज़ में किसी विशिष्ट स्थान पर कर्सर कैसे ले जा सकता हूँ?

A: नई सामग्री इन्सर्ट करने से पहले कर्सर को पोजिशन करने के लिए `moveToParagraph`, `moveToCell` आदि मेथड्स का उपयोग करें।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

ये उत्तर Aspose.Words for Java के `DocumentBuilder` के साथ काम करते समय सबसे सामान्य परिदृश्यों को कवर करते हैं। अधिक विस्तृत जानकारी के लिए [लाइब्रेरी की डॉक्यूमेंटेशन](https://reference.aspose.com/words/java/) देखें या समर्थन के लिए Aspose.Words समुदाय में शामिल हों।

**अंतिम अपडेट:** 2026-01-01  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}