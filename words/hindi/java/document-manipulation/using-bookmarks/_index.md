---
date: 2026-01-11
description: Aspose.Words for Java का उपयोग करके बुकमार्क को दिखाने, छिपाने और जावा
  में बुकमार्क बनाने के बारे में सीखें, जिससे दस्तावेज़ नेविगेशन और हेरफेर अधिक कुशल
  हो सके।
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java के साथ बुकमार्क दिखाएँ/छिपाएँ
url: /hi/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ बुकमार्क दिखाएँ/छिपाएँ

## Aspose.Words for Java में बुकमार्क उपयोग का परिचय

बुकमार्क Aspose.Words for Java की एक शक्तिशाली सुविधा है जो आपको **create bookmark java** करने, विशिष्ट सामग्री पर नेविगेट करने और जब आप विभिन्न दस्तावेज़ संस्करण बनाना चाहते हैं तो **show hide bookmarks** करने की अनुमति देती है। इस चरण‑दर‑चरण गाइड में हम बुकमार्क बनाने, एक्सेस करने, अपडेट करने, कॉपी करने और उनकी दृश्यता टॉगल करने की प्रक्रिया को समझेंगे, जिससे दस्तावेज़ संचालन पर आपका पूरा नियंत्रण रहेगा।

## त्वरित उत्तर
- **बुकमार्क का मुख्य उद्देश्य क्या है?** दस्तावेज़ के विशिष्ट भागों को चिह्नित करना और बाद में उन्हें पुनः प्राप्त करना।  
- **क्या मैं अंतिम आउटपुट में बुकमार्क मार्कर को छिपा सकता हूँ?** हाँ—दृश्यता टॉगल करने के लिए शो/हाइड API का उपयोग करें।  
- **टेबल सेल के अंदर बुकमार्क कैसे बनाऊँ?** कर्सर को सेल के अंदर रखते हुए `DocumentBuilder` के साथ बुकमार्क की शुरुआत और अंत करें।  
- **क्या बुकमार्क किया गया टेक्स्ट किसी अन्य दस्तावेज़ में कॉपी किया जा सकता है?** बिल्कुल—फ़ॉर्मेटिंग बनाए रखने के लिए `NodeImporter` का उपयोग करें।  
- **Aspose.Words का कौन सा संस्करण आवश्यक है?** कोई भी हालिया रिलीज़; कोड नवीनतम 2026 बिल्ड के साथ काम करता है।

## “show hide bookmarks” क्या है?

**show hide bookmarks** सुविधा आपको प्रोग्रामेटिक रूप से सहेजे गए दस्तावेज़ में बुकमार्क डिलिमिटर को दिखाने या छिपाने की अनुमति देती है। यह तब उपयोगी होता है जब आप अंतिम उपयोगकर्ताओं के लिए साफ़ आउटपुट बनाना चाहते हैं, जबकि आंतरिक प्रोसेसिंग के लिए बुकमार्क डेटा बरकरार रहता है।

## जावा दस्तावेज़ ऑटोमेशन में बुकमार्क क्यों उपयोग करें?

- **कुशल नेविगेशन** – पूरे फ़ाइल को स्कैन किए बिना सीधे सेक्शन पर जाएँ।  
- **डायनामिक कंटेंट जेनरेशन** – बुकमार्क से जुड़े टेक्स्ट को इन्सर्ट, रिप्लेस या रिमूव करें।  
- **शर्तीय दृश्यता** – उपयोगकर्ता की पसंद या आउटपुट फ़ॉर्मेट के आधार पर बुकमार्क मार्कर दिखाएँ या छिपाएँ।  
- **पुन: उपयोगिता** – बुकमार्क किए गए फ्रैगमेंट को दस्तावेज़ों के बीच कॉपी करें और स्टाइल्स को संरक्षित रखें।

## पूर्वापेक्षाएँ
- Java Development Kit (JDK) 8 या उससे ऊपर।  
- आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी जोड़ी गई हो (Maven/Gradle या JAR)।  
- `Document` और `DocumentBuilder` क्लासेज़ की बुनियादी समझ।

## चरण‑दर‑चरण गाइड

### चरण 1: बुकमार्क बनाएँ (create bookmark java)

बुकमार्क जोड़ने के लिए आप इसे शुरू करते हैं, सामग्री लिखते हैं, फिर इसे समाप्त करते हैं। यह उदाहरण **My Bookmark** नामक एक सरल बुकमार्क बनाता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### चरण 2: बुकमार्क एक्सेस करें (access bookmarks java)

बुकमार्क को या तो शून्य‑आधारित इंडेक्स या नाम से प्राप्त किया जा सकता है। नीचे दिया गया कोड दोनों तरीकों को दर्शाता है।

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### चरण 3: बुकमार्क डेटा अपडेट करें (update bookmark text)

आप बुकमार्क का नाम बदल सकते हैं या उसका टेक्स्ट कंटेंट बदल सकते हैं। यह तब उपयोगी होता है जब मूल दस्तावेज़ में बदलाव होते हैं।

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### चरण 4: बुकमार्क किया हुआ टेक्स्ट के साथ काम करें (copy bookmarked text)

`NodeImporter` के साथ बुकमार्क किए हुए हिस्से को किसी अन्य दस्तावेज़ में कॉपी करना और मूल फ़ॉर्मेटिंग बनाए रखना सरल है।

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### चरण 5: बुकमार्क दिखाएँ और छिपाएँ (show hide bookmarks)

निम्न स्निपेट दिखाता है कि सहेजे गए फ़ाइल में बुकमार्क के मार्कर को कैसे छिपाएँ। छिपाने के लिए `false` पास करें, दिखाने के लिए `true`।

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### चरण 6: रो बुकमार्क अनटैंगल करें (bookmark table cell)

जब बुकमार्क टेबल की पंक्तियों में फैले होते हैं, तो वे उलझ सकते हैं। नीचे दी गई यूटिलिटी मेथड्स उन्हें अनटैंगल करती हैं और आपको बुकमार्क द्वारा किसी विशिष्ट पंक्ति को डिलीट करने की अनुमति देती हैं।

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## सामान्य समस्याएँ और समाधान

| समस्या | समाधान |
|-------|----------|
| **Bookmark not found** | बुकमार्क नाम को बिल्कुल सही (केस‑सेंसिटिव) मिलाएँ और सुनिश्चित करें कि निर्माण के बाद दस्तावेज़ सहेजा गया है। |
| **Copied text loses formatting** | Step 4 में दिखाए अनुसार `NodeImporter` के साथ `ImportFormatMode.KEEP_SOURCE_FORMATTING` का उपयोग करें। |
| **Show/hide does not affect output** | दस्तावेज़ सहेजने से **पहले** `showHideBookmarkedContent` को कॉल करना सुनिश्चित करें। |
| **Bookmark inside a table cell is ignored** | बिल्डर कर्सर को लक्ष्य सेल के अंदर रखते हुए शुरू/समाप्त कॉल करें। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: टेबल सेल में बुकमार्क कैसे बनाऊँ?**  
उत्तर: `DocumentBuilder` का उपयोग करके कर्सर को इच्छित सेल में ले जाएँ, फिर सेल सामग्री के चारों ओर `startBookmark` और `endBookmark` कॉल करें।

**प्रश्न: क्या मैं बुकमार्क को किसी अन्य दस्तावेज़ में कॉपी कर सकता हूँ?**  
उत्तर: हाँ—Step 4 देखें, `NodeImporter` क्लास का उपयोग करके बुकमार्क्ड नोड को इम्पोर्ट करें और मूल फ़ॉर्मेटिंग बनाए रखें।

**प्रश्न: बुकमार्क द्वारा पंक्ति को कैसे डिलीट करूँ?**  
उत्तर: पहले उस पंक्ति को खोजें जिसमें बुकमार्क है, फिर Step 6 में दिखाए अनुसार पंक्ति नोड पर `remove` कॉल करें।

**प्रश्न: बुकमार्क के सामान्य उपयोग केस क्या हैं?**  
उत्तर: टेबल ऑफ कंटेंट बनाना, रिपोर्टिंग के लिए विशिष्ट सेक्शन निकालना, और उपयोगकर्ता चयन के आधार पर दस्तावेज़ असेंबली को ऑटोमेट करना।

**प्रश्न: Aspose.Words for Java के बारे में अधिक जानकारी कहाँ मिल सकती है?**  
उत्तर: विस्तृत दस्तावेज़ीकरण और डाउनलोड के लिए देखें [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)।

---

**Last Updated:** 2026-01-11  
**Tested With:** Aspose.Words for Java 24.11 (2026)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}