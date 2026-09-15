---
date: 2026-01-01
description: Aspose.Words for Java का उपयोग करके टेक्स्ट निकालना सीखें। यह चरण‑दर‑चरण
  गाइड कई निकासी तकनीकों को तैयार‑चलाने योग्य कोड नमूनों के साथ दिखाता है।
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके टेक्स्ट कैसे निकालें
url: /hi/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके टेक्स्ट कैसे निकालें

## Aspose.Words for Java का उपयोग करके टेक्स्ट कैसे निकालें

दस्तावेज़ प्रोसेसिंग की दुनिया में, **Aspose.Words का उपयोग करके टेक्स्ट कैसे निकालें** Java डेवलपर्स के लिए एक अक्सर पूछा जाने वाला प्रश्न है। चाहे आपको साधारण टेक्स्ट, टेबल, इमेजेज़, या बुकमार्क्स या कमेंट्स जैसे विशिष्ट तत्व निकालने हों, Aspose.Words for Java एक समृद्ध API प्रदान करता है जो काम को सरल बनाता है। इस गाइड में हम कई निष्कर्षण परिदृश्यों को कवर करेंगे, प्रत्येक दृष्टिकोण क्यों महत्वपूर्ण है समझाएँगे, और तैयार‑से‑चलाने वाले कोड सैंपल प्रदान करेंगे जिन्हें आप अपने प्रोजेक्ट में जोड़ सकते हैं।

## त्वरित उत्तर
- **मुझे कौन सी लाइब्रेरी चाहिए?** Aspose.Words for Java (आधिकारिक साइट से डाउनलोड करें)।  
- **क्या मैं केवल साधारण टेक्स्ट निकाल सकता हूँ?** हाँ – `Document.getText()` या `DocumentBuilder` को फ़ील्ड्स के साथ उपयोग करें।  
- **क्या बुकमार्क्स के बीच टेक्स्ट निकालना संभव है?** बिल्कुल, `BookmarkStart`/`BookmarkEnd` को `ExtractContentHelper` के साथ उपयोग करें।  
- **क्या प्रोडक्शन के लिए लाइसेंस चाहिए?** गैर‑ट्रायल उपयोग के लिए एक वाणिज्यिक लाइसेंस आवश्यक है।  
- **कौन से Java संस्करण समर्थित हैं?** Java 8 और उसके बाद के संस्करण पूरी तरह संगत हैं।

## पूर्वापेक्षाएँ

1. **Aspose.Words for Java** – लाइब्रेरी स्थापित करें और इसे अपने प्रोजेक्ट में जोड़ें। आप इसे [here](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं।  
2. **एक नमूना दस्तावेज़** – उदाहरणों के लिए हम `Extract content.docx` नामक फ़ाइल का उपयोग करेंगे। इसे ऐसे फ़ोल्डर में रखें जिसे आप अपने कोड से संदर्भित कर सकें।

## ब्लॉक‑लेवल नोड्स के बीच सामग्री निकालना

```java
// Java code sample for extracting content between block-level nodes
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## बुकमार्क्स के बीच सामग्री निकालना

```java
// Java code sample for extracting content between bookmarks
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## टिप्पणी रेंज के बीच सामग्री निकालना

```java
// Java code sample for extracting content between comment ranges
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## पैराग्राफ़ के बीच सामग्री निकालना

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## पैराग्राफ़ स्टाइल्स के बीच सामग्री निकालना

```java
// Java code sample for extracting content between paragraph styles
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## रन के बीच सामग्री निकालना

```java
// Java code sample for extracting content between runs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## DocumentVisitor का उपयोग करके सामग्री निकालना

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## फ़ील्ड का उपयोग करके सामग्री निकालना

```java
// Java code sample for extracting content using Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## तालिका‑सामग्री (Table of Contents) निकालना

```java
// Java code sample for extracting table of contents
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## केवल टेक्स्ट निकालना

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## स्टाइल्स के आधार पर सामग्री निकालना

```java
// Java code sample for extracting content based on styles
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## टेक्स्ट निकालना और प्रिंट करना

```java
// Java code sample for extracting and printing text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## इमेजेज़ को फ़ाइलों में निकालना

```java
// Java code sample for extracting images to files
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## निष्कर्ष

बधाई हो! अब आपके पास Java में **Aspose.Words का उपयोग करके टेक्स्ट कैसे निकालें** के लिए एक मजबूत टूलबॉक्स है। ब्लॉक‑लेवल नोड्स से लेकर बुकमार्क्स, टिप्पणियाँ, स्टाइल्स और यहाँ तक कि इमेजेज़ तक, API आपको दस्तावेज़ से निकालने वाली सामग्री पर सूक्ष्म नियंत्रण देता है। इन स्निपेट्स को आधार के रूप में उपयोग करें, उन्हें अपनी फ़ाइल संरचनाओं के अनुसार अनुकूलित करें, और बड़े दस्तावेज़ सेटों में निष्कर्षण प्रक्रिया को स्वचालित करें।

## अक्सर पूछे जाने वाले प्रश्न

**Q: मैं पासवर्ड‑सुरक्षित दस्तावेज़ से सामग्री कैसे निकालूँ?**  
A: पासवर्ड कंस्ट्रक्टर के साथ दस्तावेज़ लोड करें: `new Document(path, new LoadOptions("password"))`, फिर ऊपर दिखाए गए किसी भी निष्कर्षण मेथड को चलाएँ।

**Q: क्या मैं एक ही रन में कई दस्तावेज़ों से सामग्री निकाल सकता हूँ?**  
A: हाँ। फ़ाइल पाथ की सूची पर लूप करें, प्रत्येक के लिए `Document` का एक उदाहरण बनाएं, और लूप के भीतर समान निष्कर्षण लॉजिक लागू करें।

**Q: क्या केवल दृश्यमान टेक्स्ट (छिपे हुए या फ़ील्ड कोड को अनदेखा करते हुए) निकालने का कोई तरीका है?**  
A: साधारण दृश्यमान टेक्स्ट के लिए `doc.getText()` का उपयोग करें। अधिक नियंत्रण के लिए, नोड्स पर इटररेट करें और `NodeType.RUN` तथा `Run.getFont().getHidden()` द्वारा फ़िल्टर करें।

**Q: मैं निकाली गई सामग्री को किन फ़ॉर्मेट्स में सहेज सकता हूँ?**  
A: निकालने के बाद, आप `Document` को DOCX, PDF, HTML, TXT, या Aspose.Words द्वारा समर्थित किसी भी फ़ॉर्मेट में `doc.save("output.pdf")` के माध्यम से सहेज सकते हैं।

**Q: क्या Aspose.Words बड़े (सैकड़ों MB) फ़ाइलों से सामग्री निकालने का समर्थन करता है?**  
A: हाँ, लेकिन मेमोरी उपयोग कम करने के लिए `LoadOptions` को `LoadFormat` और `MemoryOptimization` के साथ उपयोग करने पर विचार करें।

---

**अंतिम अपडेट:** 2026-01-01  
**परीक्षण किया गया:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}