---
"description": "इस व्यापक गाइड के साथ Aspose.Words for Java में संरचित दस्तावेज़ टैग (SDT) का उपयोग करना सीखें। कस्टम XML डेटा के लिए SDTs बनाएँ, संशोधित करें और बाँधें।"
"linktitle": "संरचित दस्तावेज़ टैग (SDT) का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में संरचित दस्तावेज़ टैग (SDT) का उपयोग करना"
"url": "/hi/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में संरचित दस्तावेज़ टैग (SDT) का उपयोग करना


## जावा के लिए Aspose.Words में संरचित दस्तावेज़ टैग (SDT) का उपयोग करने का परिचय

संरचित दस्तावेज़ टैग (SDT) Aspose.Words for Java में एक शक्तिशाली विशेषता है जो आपको अपने दस्तावेज़ों में संरचित सामग्री बनाने और उसमें हेरफेर करने की अनुमति देता है। इस व्यापक गाइड में, हम आपको Aspose.Words for Java में SDTs के उपयोग के विभिन्न पहलुओं से परिचित कराएँगे। चाहे आप एक शुरुआती या एक अनुभवी डेवलपर हों, आपको इस लेख में मूल्यवान जानकारी और व्यावहारिक उदाहरण मिलेंगे।

## शुरू करना

इससे पहले कि हम विवरण में उतरें, आइए अपना परिवेश सेट करें और एक बुनियादी SDT बनाएँ। इस अनुभाग में, हम निम्नलिखित विषयों को कवर करेंगे:

- नया दस्तावेज़ बनाना
- संरचित दस्तावेज़ टैग जोड़ना
- दस्तावेज़ सहेजना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// CHECKBOX प्रकार का एक संरचित दस्तावेज़ टैग बनाएँ
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// दस्तावेज़ सहेजें
doc.save("WorkingWithSDT.docx");
```

## चेकबॉक्स SDT की वर्तमान स्थिति की जाँच करना

एक बार जब आप अपने दस्तावेज़ में चेकबॉक्स SDT जोड़ लेते हैं, तो आप इसकी वर्तमान स्थिति को प्रोग्रामेटिक रूप से जांचना चाह सकते हैं। यह तब उपयोगी हो सकता है जब आपको उपयोगकर्ता इनपुट को मान्य करने या चेकबॉक्स स्थिति के आधार पर विशिष्ट क्रियाएँ करने की आवश्यकता हो।

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // चेकबॉक्स चेक किया गया है
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## सामग्री नियंत्रण संशोधित करना

इस अनुभाग में, हम यह पता लगाएंगे कि आपके दस्तावेज़ में सामग्री नियंत्रणों को कैसे संशोधित किया जाए। हम तीन प्रकार के सामग्री नियंत्रणों को कवर करेंगे: सादा पाठ, ड्रॉप-डाउन सूची और चित्र।

### सादा पाठ सामग्री नियंत्रण को संशोधित करना

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // मौजूदा सामग्री साफ़ करें
    sdtPlainText.removeAllChildren();

    // नया पाठ जोड़ें
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### ड्रॉप-डाउन सूची सामग्री नियंत्रण को संशोधित करना

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // सूची से दूसरा आइटम चुनें
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### चित्र सामग्री नियंत्रण संशोधित करना

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // छवि को नई छवि से बदलें
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## कॉम्बोबॉक्स सामग्री नियंत्रण बनाना

कॉम्बोबॉक्स कंटेंट कंट्रोल उपयोगकर्ताओं को विकल्पों की पूर्वनिर्धारित सूची से चयन करने की अनुमति देता है। आइए अपने दस्तावेज़ में एक बनाएं।

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## रिच टेक्स्ट कंटेंट कंट्रोल के साथ कार्य करना

रिच टेक्स्ट कंटेंट कंट्रोल आपके दस्तावेज़ों में फ़ॉर्मेटेड टेक्स्ट जोड़ने के लिए एकदम सही हैं। आइए एक बनाएं और इसकी सामग्री सेट करें।

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

## सामग्री नियंत्रण शैलियाँ सेट करना

आप अपने दस्तावेज़ के दृश्य स्वरूप को बेहतर बनाने के लिए सामग्री नियंत्रणों पर शैलियाँ लागू कर सकते हैं। आइए देखें कि सामग्री नियंत्रण की शैली कैसे सेट करें।

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// कस्टम शैली लागू करें
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## SDT को कस्टम XML डेटा से बांधना

कुछ परिदृश्यों में, आपको गतिशील सामग्री निर्माण के लिए कस्टम XML डेटा से SDT को बांधने की आवश्यकता हो सकती है। आइए जानें कि इसे कैसे प्राप्त किया जाए।

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## कस्टम XML डेटा से मैप किए गए दोहराए जाने वाले अनुभागों के साथ एक तालिका बनाना

दोहराए जाने वाले अनुभागों वाली तालिकाएँ संरचित डेटा प्रस्तुत करने के लिए अत्यंत उपयोगी हो सकती हैं। आइए ऐसी तालिका बनाएँ और उसे कस्टम XML डेटा पर मैप करें।

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

## बहु-अनुभाग संरचित दस्तावेज़ टैग के साथ कार्य करना

संरचित दस्तावेज़ टैग एक दस्तावेज़ में कई अनुभागों में फैल सकते हैं। इस अनुभाग में, हम बहु-अनुभाग SDTs के साथ काम करने का तरीका जानेंगे।

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## निष्कर्ष

Aspose.Words for Java में संरचित दस्तावेज़ टैग आपके दस्तावेज़ों में सामग्री को प्रबंधित करने और प्रारूपित करने का एक बहुमुखी तरीका प्रदान करते हैं। चाहे आपको टेम्प्लेट, फ़ॉर्म या गतिशील दस्तावेज़ बनाने की आवश्यकता हो, SDTs आपको आवश्यक लचीलापन और नियंत्रण प्रदान करते हैं। इस लेख में दिए गए उदाहरणों और दिशानिर्देशों का पालन करके, आप अपने दस्तावेज़ प्रसंस्करण कार्यों को बढ़ाने के लिए SDTs की शक्ति का उपयोग कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### संरचित दस्तावेज़ टैग (एसडीटी) का उद्देश्य क्या है?

संरचित दस्तावेज़ टैग (एसडीटी) दस्तावेज़ों के भीतर सामग्री को व्यवस्थित और प्रारूपित करने के उद्देश्य से काम करते हैं, जिससे टेम्पलेट्स, फ़ॉर्म और संरचित दस्तावेज़ बनाना आसान हो जाता है।

### मैं चेकबॉक्स एसडीटी की वर्तमान स्थिति कैसे जांच सकता हूं?

आप चेकबॉक्स SDT की वर्तमान स्थिति की जांच कर सकते हैं `setChecked` विधि, जैसा कि लेख में दर्शाया गया है।

### क्या मैं सामग्री नियंत्रणों पर शैलियाँ लागू कर सकता हूँ?

हां, आप दस्तावेज़ में उनकी उपस्थिति को अनुकूलित करने के लिए सामग्री नियंत्रणों पर शैलियाँ लागू कर सकते हैं।

### क्या SDT को कस्टम XML डेटा से बांधना संभव है?

हां, आप SDT को कस्टम XML डेटा से जोड़ सकते हैं, जिससे गतिशील सामग्री निर्माण और डेटा मैपिंग की सुविधा मिलती है।

### एसडीटी में दोहराए जाने वाले अनुभाग क्या हैं?

एसडीटी में दोहराए जाने वाले अनुभाग आपको गतिशील डेटा के साथ तालिकाएं बनाने की अनुमति देते हैं, जहां मैप किए गए XML डेटा के आधार पर पंक्तियों को दोहराया जा सकता है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}