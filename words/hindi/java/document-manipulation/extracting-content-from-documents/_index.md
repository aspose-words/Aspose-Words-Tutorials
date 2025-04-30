---
"description": "Java के लिए Aspose.Words का उपयोग करके आसानी से दस्तावेज़ों से सामग्री निकालना सीखें। हमारी चरण-दर-चरण मार्गदर्शिका और कोड नमूने प्रक्रिया को सरल बनाते हैं।"
"linktitle": "दस्तावेज़ों से सामग्री निकालना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में दस्तावेज़ों से सामग्री निकालना"
"url": "/hi/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों से सामग्री निकालना


## जावा के लिए Aspose.Words में दस्तावेज़ों से सामग्री निकालने का परिचय

दस्तावेज़ प्रसंस्करण की दुनिया में, दस्तावेज़ों से सामग्री निकालना एक सामान्य आवश्यकता है। चाहे आपको टेक्स्ट, टेबल, इमेज या विशिष्ट दस्तावेज़ तत्वों को निकालने की आवश्यकता हो, Aspose.Words for Java इस कार्य को आसान बनाने के लिए शक्तिशाली उपकरण प्रदान करता है। इस व्यापक गाइड में, हम आपको Aspose.Words for Java का उपयोग करके दस्तावेज़ों से सामग्री निकालने की प्रक्रिया के बारे में बताएँगे। 

## आवश्यक शर्तें

इससे पहले कि हम निष्कर्षण प्रक्रिया में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

1. Aspose.Words for Java: आपके पास Aspose.Words for Java इंस्टॉल होना चाहिए और आपके Java डेवलपमेंट एनवायरनमेंट में सेट अप होना चाहिए। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

2. सामग्री निकालने के लिए एक दस्तावेज़: इस गाइड के लिए, हम "Extract content.docx" नामक एक नमूना दस्तावेज़ का उपयोग करेंगे। सुनिश्चित करें कि आपके पास निष्कर्षण के लिए एक समान दस्तावेज़ तैयार है।

## ब्लॉक-स्तरीय नोड्स के बीच सामग्री निकालना

```java
// ब्लॉक-स्तरीय नोड्स के बीच सामग्री निकालने के लिए जावा कोड नमूना
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
// बुकमार्क के बीच सामग्री निकालने के लिए जावा कोड नमूना
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

## टिप्पणी श्रेणियों के बीच सामग्री निकालना

```java
// टिप्पणी श्रेणियों के बीच सामग्री निकालने के लिए जावा कोड नमूना
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
// पैराग्राफ़ के बीच सामग्री निकालने के लिए जावा कोड नमूना
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## पैराग्राफ़ शैलियों के बीच सामग्री निकालना

```java
// पैराग्राफ़ शैलियों के बीच सामग्री निकालने के लिए जावा कोड नमूना
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
// रन के बीच सामग्री निकालने के लिए जावा कोड नमूना
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## डॉक्यूमेंटविजिटर का उपयोग करके सामग्री निकालना

```java
// डॉक्यूमेंटविजिटर का उपयोग करके सामग्री निकालने के लिए जावा कोड नमूना
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## फ़ील्ड का उपयोग करके सामग्री निकालना

```java
// फ़ील्ड का उपयोग करके सामग्री निकालने के लिए जावा कोड नमूना
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## विषय-सूची निकालना

```java
// सामग्री तालिका निकालने के लिए जावा कोड नमूना
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

## केवल पाठ निकालना

```java
// केवल पाठ निकालने के लिए जावा कोड नमूना
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## शैलियों के आधार पर सामग्री निकालना

```java
// शैलियों के आधार पर सामग्री निकालने के लिए जावा कोड नमूना
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

## पाठ निकालना और प्रिंट करना

```java
// पाठ निकालने और प्रिंट करने के लिए जावा कोड नमूना
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## छवियों को फ़ाइलों में निकालना

```java
// छवियों को फ़ाइलों में निकालने के लिए जावा कोड नमूना
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

बधाई हो! आपने Aspose.Words for Java का उपयोग करके दस्तावेज़ों से सामग्री निकालना सीख लिया है। इस गाइड में ब्लॉक-स्तरीय नोड्स, बुकमार्क, टिप्पणी रेंज, पैराग्राफ और बहुत कुछ के बीच सामग्री सहित विभिन्न निष्कर्षण तकनीकों को शामिल किया गया है। अब आप अपने Java अनुप्रयोगों में दस्तावेज़ सामग्री निष्कर्षण को कुशलतापूर्वक संभालने के लिए सुसज्जित हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं विशिष्ट दस्तावेज़ अनुभागों से सामग्री कैसे निकालूँ?

विशिष्ट दस्तावेज़ अनुभागों से सामग्री निकालने के लिए, आप अनुभागों के आरंभिक और अंतिम बिंदुओं की पहचान कर सकते हैं और उनके बीच सामग्री निकालने के लिए उपयुक्त Aspose.Words for Java विधियों का उपयोग कर सकते हैं।

### क्या मैं पासवर्ड-संरक्षित दस्तावेज़ों से सामग्री निकाल सकता हूँ?

हां, Aspose.Words for Java पासवर्ड-संरक्षित दस्तावेज़ों से सामग्री निकालने की कार्यक्षमता प्रदान करता है। आप दस्तावेज़ खोलते समय पासवर्ड प्रदान कर सकते हैं `Document` क्लास निर्माता.

### मैं सामग्री को कैसे निकाल सकता हूं और इसे विभिन्न प्रारूपों में कैसे सहेज सकता हूं, जैसे सादा पाठ या HTML?

आप Aspose.Words for Java का उपयोग करके किसी दस्तावेज़ से सामग्री निकाल सकते हैं और उसे विभिन्न प्रारूपों में सहेज सकते हैं। सामग्री निकालने के बाद, आप इसका उपयोग कर सकते हैं `Document` क्लास विधियों का उपयोग करके इसे सादे पाठ, HTML या अन्य प्रारूपों में सहेजा जा सकता है।

### क्या विशिष्ट दस्तावेज़ तत्वों, जैसे तालिकाओं या छवियों से सामग्री निकालने का कोई तरीका है?

हां, आप Java के लिए Aspose.Words का उपयोग करके तालिकाओं या छवियों जैसे विशिष्ट दस्तावेज़ तत्वों से सामग्री निकाल सकते हैं। उन तत्वों की पहचान करें जिन्हें आप निकालना चाहते हैं, और फिर उनकी सामग्री निकालने के लिए उपयुक्त विधियों का उपयोग करें।

### मैं अपने जावा अनुप्रयोग में सामग्री निष्कर्षण प्रक्रिया को स्वचालित कैसे कर सकता हूँ?

अपने जावा एप्लिकेशन में सामग्री निष्कर्षण प्रक्रिया को स्वचालित करने के लिए, आप इस गाइड में वर्णित तकनीकों के आधार पर कस्टम कोड बना सकते हैं। आप कई दस्तावेज़ों के माध्यम से पुनरावृत्ति करने और आवश्यकतानुसार सामग्री निकालने के लिए तर्क भी लागू कर सकते हैं।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}