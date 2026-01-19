---
date: 2026-01-19
description: Aspose.Words for Java में Structured Document Tags (SDT) का उपयोग करके
  चेकबॉक्स की स्थिति सेट करना और ड्रॉपडाउन कंटेंट कंट्रोल बनाना सीखें।
linktitle: Using Structured Document Tags (SDT)
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words में Structured Document Tags (SDT) के साथ Java में चेकबॉक्स की
  स्थिति कैसे सेट करें
url: /hi/java/document-manipulation/using-structured-document-tags/
weight: 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में Structured Document Tags (SDT) का उपयोग

## Aspose.Words for Java में Structured Document Tags (SDT) के उपयोग का परिचय

Structured Document Tags (SDT) Aspose.Words for Java की एक शक्तिशाली सुविधा है जो आपको दस्तावेज़ों के भीतर संरचित सामग्री बनाने और उसे नियंत्रित करने की अनुमति देती है। इस गाइड में आप **set checkbox state java**, **create dropdown content control**, और कस्टम XML डेटा से SDT को बाइंड करने के बारे में स्पष्ट, चलाने योग्य कोड उदाहरणों के साथ सीखेंगे।

## त्वरित उत्तर
- **जावा में स्थिति सेट करने का मुख्य तरीका क्या है?** Use a `StructuredDocumentTag objects.
- **क्या इन उदाहरणों को चलाने के लिए लाइसेंस चाहिए?** A free trial works for evaluation; a commercial license is required for production.
- **कौन सा Aspose.Words संस्करण समर्थित है?** The examples work with the latest Aspose.Words for Java release.
- **क्या कस्टम XML बाइंडिंग संभव है?** Absolutely—use `CustomXmlPart` and `XmlMapping` to link data to an SDT.

## “set checkbox state java” क्या है?

जावा में चेकबॉक्स की स्थिति सेट करना मतलब प्रोग्रामेटिक रूप से एक कंटेंट कंट्रोल (SDT) को चेक या अनचेक करना है, जो Word दस्तावेज़ के भीतर एक चेकबॉक्स का प्रतिनिधित्व करता है। यह तब आवश्यक होता है जब आप फॉर्म, टेम्प्लेट या रिपोर्ट बनाते हैं जिन्हें उपयोगकर्ता की चयनित विकल्पों को स्वचालित रूप से दर्शाना होता है।

## इस कार्य के लिए Structured Document Tags क्यों उपयोग करें?

- **सूक्ष्म नियंत्रण** – SDT आपको कच्चा XML पार्स किए बिना व्यक्तिगत तत्वों को लक्षित करने साथ मिलाकर डायनेमिक दस्तावेज़ निर्माण संभव- **स्टाइलिंग और पुनरावृत्ति** – स्टाइल लागू करें, सेक्शन दोहराएँ, या डेटा के अनुसार टेबल बनाएं।

## आवश्यकताएँ
- Java 17+ (या संगत JDK)  
- Asposeिस्तृत विवरण में जाने से पहले, अपने वातावरण को सेट करें और एक बेसिक SDT बनाएं। इस सेक्शन में हम निम्नलिखित विषयों को कवर करेंगे:

- नया दस्तावेज़ बनाना  
- Structured Document Tag जोड़ना  
- दस्तावेज़ सहेजना  

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a Structured Document Tag of type CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Save the document
doc.save("WorkingWithSDT.docx");
```

## Checkbox SDT का उपयोग करके set checkbox state java कैसे सेट करें

जब आप अपने दस्तावबॉक्स SDT जोड़ देते हैं, तो आप प्रोग्रामेटिक रूप से उसकी वर्तमान स्थिति पढ़ना या बदलना चाह सकते हैं। यह उपयोगकर्ता इनपुट को वैध करने या चेकबॉक्स की स्थिति के आधार पर विशिष्ट कार्य करने में सहायक होता है।

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Checkbox is checked
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## कंटेंट कंट्रोल्स को संशोधित करना

इस सेक्शन में हम आपके दस्तावेज़ के भीतर कंटेंट कंट्रोल्स को संशोधित करने के तरीकों का अन्वेषण करेंगे। हम तीन प्रकार के कंटेंट कंट्रोल्स को कवर करेंगे: Plain Text, **create dropdown content control**, और Picture।

### Plain Text कंटेंट कंट्रोल को संशोधित करना

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Clear the existing content
    sdtPlainText.removeAllChildren();

    // Add new text
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### ड्रॉपडाउन कंटेंट कंट्रोल कैसे बनाएं

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Select the second item from the list
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Picture कंटेंट कंट्रोल को संशोधित करना

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Replace the image with a new one
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## ComboBox कंटेंट कंट्रोल बनाना

ComboBox कंटेंट कंट्रोल उपयोगकर्ताओं को पूर्वनिर्धारित विकल्पों की सूची से चयन करने की सुविधा देता है। चलिए अपने दस्तावेज़ में एक बनाते हैं।

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Rich Text कंटेंट कंट्रोल के साथ काम करना

Rich Text कंटेंट कंट्रोल्स दस्तावेज़ में फॉर्मेटेड टेक्स्ट जोड़ने के लिए आदर्श हैं। चलिए एक बनाते हैं और उसकी सामग्री सेट करते हैं।

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## कंटेंट कंट्रोल स्टाइल्स सेट करना

आप कंटेंट कंट्रोल्स पर स्टाइल लागू करके अपने दस्तावेज़ की दृश्य उपस्थिति को बेहतर बना सकते हैं। चलिए देखते हैं कि कंटेंट कंट्रोल की स्टाइल कैसे सेट करें।

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Apply a custom style
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## SDT को कस्टम XML डेटा से बाइंड करना

कुछ परिदृश्यों में आपको डायनेमिक कंटेंट जेनरेशन के लिए SDT को कस्टम XML डेटा से बाइंड करने की आवश्यकता हो सकती है। आइए देखें कि इसे कैसे हासिल किया जाए।

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## कस्टम XML डेटा से मैप्ड रिपीटिंग सेक्शन वाले टेबल बनाना

रिपीटिंग सेक्शन वाले टेबल संरचित डेटा प्रस्तुत करने में अत्यंत उपयोगी होते हैं। चलिए ऐसा टेबल बनाते हैं और उसे कस्टम XML डेटा से मैप करते हैं।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## मल्टी‑सेक्शन Structured Document Tags के साथ काम करना

Structured Document Tags दस्तावेज़ में कई सेक्शन तक फैला हो सकता है। इस सेक्शन में हम मल्टी‑सेक्शन SDT के साथ काम करने के तरीकों का अन्वेषण करेंगे।

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## निष्कर्ष

Aspose.Words for Java में Structured Document Tags दस्तावेज़ों के भीतर सामग्री को प्रबंधित और फॉर्मेट करने का एक बहुमुखी तरीका प्रदान करते हैं। चाहे आप टेम्प्लेट, और। इस लेख में प्रदान किए गए उदाहरणों और दिशानिर्देशों का पालन करके आप अपने भीतर सामग्री को व्यव फॉर्म और संरचित दस्तावेज़ बनाना आसान हो जाता है।

**प्रश्न: मैं Checkbox SDT की वर्तमान स्थिति कैसे जांच सकता हूँ?**  
उत्तर: आप लेख में दर्शाए अनुसार `setChecked` मेथड का उपयोग करके Checkbox SDT की वर्तमान स्थिति जांच सकते हैं।

**प्रश्न: क्या मैं कंटेंट कंट्रोल्स पर हूँ?**  
उत्तर: हाँ, आप कंटेंट कंट्रोल्स पर स्टाइल लागू करके दस्तावेज़ में उनकी उपस्थिति को कस्टमाइज़ कर सकते हैं।

**प्रश**  
peatingंक्तियों को दोहराते हुए टेबल बनाने की अनुमति देते हैं।

**प्रश्न: मैं ड्रॉपडाउन कंटेंट कंट्रोल कैसे बनाऊँ?**  
उत्तर: `SdtType.DROP_DOWN_LIST` का उपयोग करें और `SdtListItem` ऑब्जेक्ट्स से कंटउत्तर: बिल्कुल—`StructuredDocumentTag` को प्राप्त करें और `setChecked(true)` या `setChecked(false)` कॉल करें।

---

**Last Updated:** 2026-01-19  
**Tested With:** Aspose.Words for Java 24.11 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}