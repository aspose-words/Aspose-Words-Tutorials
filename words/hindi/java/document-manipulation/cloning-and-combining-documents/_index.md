---
title: जावा के लिए Aspose.Words में दस्तावेज़ों की क्लोनिंग और संयोजन
linktitle: दस्तावेजों की क्लोनिंग और संयोजन
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Aspose.Words for Java में दस्तावेज़ों को क्लोन और संयोजित करना सीखें। स्रोत कोड उदाहरणों के साथ चरण-दर-चरण मार्गदर्शिका।
weight: 27
url: /hi/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में दस्तावेज़ों की क्लोनिंग और संयोजन


## जावा के लिए Aspose.Words में दस्तावेज़ों की क्लोनिंग और संयोजन का परिचय

इस ट्यूटोरियल में, हम जावा के लिए Aspose.Words का उपयोग करके दस्तावेज़ों को क्लोन और संयोजित करने का तरीका जानेंगे। हम विभिन्न परिदृश्यों को कवर करेंगे, जिसमें दस्तावेज़ को क्लोन करना, प्रतिस्थापन बिंदुओं, बुकमार्क और मेल मर्ज संचालन के दौरान दस्तावेज़ सम्मिलित करना शामिल है।

## चरण 1: दस्तावेज़ की क्लोनिंग

 Aspose.Words for Java में किसी दस्तावेज़ को क्लोन करने के लिए, आप इसका उपयोग कर सकते हैं`deepClone()` विधि। यहाँ एक सरल उदाहरण है:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

यह कोड मूल दस्तावेज़ का एक डीप क्लोन बनाएगा और उसे एक नई फ़ाइल के रूप में सहेज देगा।

## चरण 2: प्रतिस्थापन बिंदुओं पर दस्तावेज़ सम्मिलित करना

आप किसी दूसरे दस्तावेज़ में विशिष्ट प्रतिस्थापन बिंदुओं पर दस्तावेज़ सम्मिलित कर सकते हैं। यहाँ बताया गया है कि आप यह कैसे कर सकते हैं:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

 इस उदाहरण में, हम एक का उपयोग करते हैं`FindReplaceOptions` प्रतिस्थापन के लिए कॉलबैक हैंडलर निर्दिष्ट करने के लिए ऑब्जेक्ट।`InsertDocumentAtReplaceHandler` क्लास सम्मिलन तर्क को संभालता है.

## चरण 3: बुकमार्क में दस्तावेज़ सम्मिलित करना

किसी अन्य दस्तावेज़ में किसी विशिष्ट बुकमार्क पर दस्तावेज़ सम्मिलित करने के लिए, आप निम्नलिखित कोड का उपयोग कर सकते हैं:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

 यहाँ, हम नाम से बुकमार्क ढूंढते हैं और उपयोग करते हैं`insertDocument` सामग्री सम्मिलित करने की विधि`subDoc` दस्तावेज़ को बुकमार्क स्थान पर रखें.

## चरण 4: मेल मर्ज के दौरान दस्तावेज़ सम्मिलित करना

आप Aspose.Words for Java में मेल मर्ज ऑपरेशन के दौरान दस्तावेज़ सम्मिलित कर सकते हैं। यहाँ बताया गया है कि कैसे:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

 इस उदाहरण में, हमने फ़ील्ड मर्जिंग कॉलबैक सेट किया है`InsertDocumentAtMailMergeHandler` "Document_1" फ़ील्ड द्वारा निर्दिष्ट दस्तावेज़ के सम्मिलन को संभालने के लिए क्लास।

## निष्कर्ष

Aspose.Words for Java में दस्तावेज़ों की क्लोनिंग और संयोजन विभिन्न तकनीकों का उपयोग करके पूरा किया जा सकता है। चाहे आपको किसी दस्तावेज़ को क्लोन करना हो, प्रतिस्थापन बिंदुओं, बुकमार्क या मेल मर्ज के दौरान सामग्री सम्मिलित करनी हो, Aspose.Words दस्तावेज़ों को सहजता से हेरफेर करने के लिए शक्तिशाली सुविधाएँ प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Aspose.Words for Java में किसी दस्तावेज़ का क्लोन कैसे बनाऊं?

 आप Aspose.Words for Java में किसी दस्तावेज़ का क्लोन बना सकते हैं`deepClone()` विधि। यहाँ एक उदाहरण है:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### मैं किसी दस्तावेज़ को बुकमार्क में कैसे सम्मिलित कर सकता हूँ?

 Aspose.Words for Java में बुकमार्क पर एक दस्तावेज़ सम्मिलित करने के लिए, आप नाम से बुकमार्क ढूंढ सकते हैं और फिर इसका उपयोग कर सकते हैं`insertDocument` सामग्री डालने की विधि। यहाँ एक उदाहरण है:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### मैं Aspose.Words for Java में मेल मर्ज के दौरान दस्तावेज़ कैसे सम्मिलित करूँ?

आप Aspose.Words for Java में मेल मर्ज के दौरान फ़ील्ड मर्जिंग कॉलबैक सेट करके और डाले जाने वाले दस्तावेज़ को निर्दिष्ट करके दस्तावेज़ सम्मिलित कर सकते हैं। यहाँ एक उदाहरण दिया गया है:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

 इस उदाहरण में,`InsertDocumentAtMailMergeHandler`क्लास मेल मर्ज के दौरान "DocumentField" के लिए सम्मिलन तर्क को संभालता है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
