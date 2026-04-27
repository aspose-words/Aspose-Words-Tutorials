---
date: '2026-04-27'
description: Aspose.Words for Java का उपयोग करके बुकमार्क सेट करना और बुकमार्क के
  साथ PDF सहेजना सीखें। इस व्यापक गाइड के साथ पठनीयता और नेविगेशन को बढ़ाएँ।
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: Aspose.Words Java के साथ PDFs में बुकमार्क कैसे सेट करें
url: /hi/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java के साथ PDFs में बुकमार्क सेट करने का तरीका

## परिचय
यदि आप Word दस्तावेज़ों को PDFs में बदलते समय **बुकमार्क सेट करने** में कठिनाई महसूस कर रहे हैं, तो आप सही जगह पर हैं। इस ट्यूटोरियल में हम Aspose.Words for Java का उपयोग करके पूरी प्रक्रिया को समझेंगे, नेस्टेड बुकमार्क बनाने से लेकर उनके outline levels को कॉन्फ़िगर करने तक, ताकि अंतिम PDF साफ़, पेशेवर और नेविगेट करने में आसान हो।

**आप क्या सीखेंगे**
- अपने प्रोजेक्ट में Aspose.Words for Java सेट करें  
- **Create nested bookmarks** को Word दस्तावेज़ में बनाएं  
- **Configure bookmark outline levels** को संरचित PDF outline के लिए कॉन्फ़िगर करें  
- **Save PDF with bookmarks** को सहेजें जो आपके द्वारा परिभाषित हाइरार्की को दर्शाते हैं  

### त्वरित उत्तर
- **दस्तावेज़ बनाने के लिए मुख्य क्लास कौन सी है?** `DocumentBuilder`  
- **कौन सा विकल्प बुकमार्क हाइरार्की को नियंत्रित करता है?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **क्या मैं Maven या Gradle का उपयोग कर सकता हूँ?** हाँ, दोनों समर्थित हैं (कोड स्निपेट देखें)  
- **क्या मुझे लाइसेंस चाहिए?** मूल्यांकन के लिए ट्रायल काम करता है; उत्पादन के लिए स्थायी लाइसेंस आवश्यक है  
- **क्या PDF नेस्टेड बुकमार्क को बनाए रखेगा?** बिल्कुल, जब outline levels सही ढंग से सेट किए जाएँ  

## PDF में “बुकमार्क सेट करने” का क्या अर्थ है?
बुकमार्क सेट करने का मतलब है PDF के नेविगेशन पेन में क्लिक करने योग्य एंट्रीज़ बनाना जो दस्तावेज़ के विशिष्ट सेक्शन पर ले जाएँ। जब बुकमार्क नेस्टेड होते हैं और उन्हें outline levels सौंपे जाते हैं, तो वे एक कोलेप्सिबल ट्री के रूप में दिखते हैं, जिससे बड़े दस्तावेज़ों को आसानी से एक्सप्लोर किया जा सकता है।

## बुकमार्क outline levels के लिए Aspose.Words क्यों उपयोग करें?
Aspose.Words आपको Word‑to‑PDF रूपांतरण पर पूर्ण प्रोग्रामेटिक नियंत्रण देता है, जिसमें **बुकमार्क के साथ PDF जनरेट करने** की क्षमता शामिल है जो आपके दस्तावेज़ की संरचना को प्रतिबिंबित करता है। यह मैनुअल पोस्ट‑प्रोसेसिंग की आवश्यकता को समाप्त करता है और सभी जनरेटेड PDFs में एक सुसंगत उपयोगकर्ता अनुभव सुनिश्चित करता है।

## पूर्वापेक्षाएँ
- **लाइब्रेरीज़ और निर्भरताएँ**: Aspose.Words for Java (संस्करण 25.3 या बाद का)।  
- **पर्यावरण**: JDK 8 या नया, IDE जैसे IntelliJ IDEA या Eclipse।  
- **ज्ञान**: बेसिक Java, Maven या Gradle की परिचितता।  

## Aspose.Words सेट अप करना
अपने बिल्ड सिस्टम में आवश्यक लाइब्रेरी जोड़ें।

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### लाइसेंस प्राप्ति
Aspose.Words एक व्यावसायिक उत्पाद है, लेकिन आप फ़्री ट्रायल से शुरू कर सकते हैं।

1. **फ़्री ट्रायल**: पूर्ण क्षमताओं का परीक्षण करने के लिए [Aspose का रिलीज़ पेज](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
2. **अस्थायी लाइसेंस**: यदि आवश्यक हो तो [Aspose का अस्थायी लाइसेंस पेज](https://purchase.aspose.com/temporary-license/) पर अस्थायी लाइसेंस के लिए आवेदन करें।  
3. **खरीदें**: निरंतर उपयोग के लिए [Aspose का खरीद पोर्टल](https://purchase.aspose.com/buy) से लाइसेंस खरीदें।

अपने कोड में लाइसेंस फ़ाइल को इनिशियलाइज़ करें ताकि सभी फीचर्स अनलॉक हो जाएँ।

## कार्यान्वयन गाइड
नीचे एक चरण‑दर‑चरण walkthrough दिया गया है जो **नेस्टेड बुकमार्क बनाना**, उनके outline levels सेट करना, और अंत में **बुकमार्क के साथ PDF सहेजना** को कवर करता है।

### नेस्टेड बुकमार्क बनाना
**सारांश**: एक Word दस्तावेज़ बनाएं और बुकमार्क एम्बेड करें जो एक हाइरार्की को दर्शाते हैं।

#### चरण 1: दस्तावेज़ और बिल्डर को इनिशियलाइज़ करें
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
यह एक नया दस्तावेज़ बनाता है जो सामग्री सम्मिलित करने के लिए तैयार है।

#### चरण 2: नेस्टेड बुकमार्क डालें
पहले एक प्राइमरी बुकमार्क से शुरू करें, फिर उसके अंदर दूसरा बुकमार्क नेस्ट करें।

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

#### चरण 3: अतिरिक्त बुकमार्क जोड़ें
आप आवश्यकता अनुसार स्वतंत्र बुकमार्क जोड़ते रह सकते हैं।

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### बुकमार्क Outline Levels कॉन्फ़िगर करना
**सारांश**: outline levels असाइन करें ताकि PDF के बुकमार्क पेन में इच्छित हाइरार्की दर्शाई जाए।

#### चरण 1: PdfSaveOptions सेट अप करें
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
इन विकल्पों का उपयोग दस्तावेज़ को PDF के रूप में सहेजते समय किया जाएगा।

#### चरण 2: Outline Levels जोड़ें
प्रत्येक बुकमार्क नाम को एक outline level (1 = शीर्ष‑स्तर, 2 = चाइल्ड, आदि) से मैप करें।

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### चरण 3: दस्तावेज़ सहेजें
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
परिणामी PDF में अब एक संरचित बुकमार्क ट्री होगा।

## सामान्य समस्याएँ और समाधान
- **बुकमार्क गायब** – सुनिश्चित करें कि प्रत्येक `startBookmark` का मिलते‑जुलते `endBookmark` है।  
- **गलत हाइरार्की** – outline level नंबर जाँचें; चाइल्ड का नंबर पैरेंट से अधिक होना चाहिए।  
- **बड़े दस्तावेज़** – फ़ाइल आकार घटाने के लिए सहेजने से पहले `doc.removeUnusedResources()` कॉल करें।  

## व्यावहारिक अनुप्रयोग
1. **कानूनी अनुबंध** – क्लॉज़ और उप‑क्लॉज़ पर जल्दी से जाएँ।  
2. **वार्षिक रिपोर्ट** – सेक्शन, टेबल और चार्ट को आसानी से नेविगेट करें।  
3. **ई‑लर्निंग सामग्री** – छात्रों के लिए क्लिक करने योग्य टेबल ऑफ कंटेंट प्रदान करें।  

## प्रदर्शन संबंधी विचार
- रूपांतरण से पहले अनावश्यक नोड्स हटाएँ ताकि PDF हल्का रहे।  
- बहुत बड़े फ़ाइलों के लिए, मेमोरी उपयोग कम करने हेतु दस्तावेज़ को स्ट्रीम करने पर विचार करें।  

## निष्कर्ष
अब आप **बुकमार्क सेट करने**, उनके outline levels कॉन्फ़िगर करने, और Aspose.Words for Java का उपयोग करके **बुकमार्क के साथ PDF सहेजने** के बारे में जानते हैं। यह तकनीक PDF नेविगेशन को काफी सुधारती है और आपके दस्तावेज़ों को पेशेवर चमक देती है।

**अगले कदम**: बुकमार्क में कस्टम आइकन जोड़ने का प्रयास करें या इस वर्कफ़्लो को बैच‑प्रोसेसिंग सेवा में इंटीग्रेट करें।

## अक्सर पूछे जाने वाले प्रश्न

**प्र: मैं Aspose.Words for Java कैसे इंस्टॉल करूँ?**  
उ: ऊपर दिखाए गए Maven या Gradle डिपेंडेंसी को जोड़ें, फिर लाइसेंस फ़ाइल को प्रोजेक्ट के resources फ़ोल्डर में रखें।

**प्र: क्या मैं outline levels के बिना बुकमार्क बना सकता हूँ?**  
उ: हाँ, लेकिन outline levels के बिना PDF का नेविगेशन पेन सभी बुकमार्क को एक ही स्तर पर दिखाएगा, जिससे बड़े दस्तावेज़ों को ब्राउज़ करना कठिन हो जाएगा।

**प्र: बुकमार्क को कितनी गहराई तक नेस्ट किया जा सकता है, इसकी कोई सीमा है?**  
उ: तकनीकी रूप से कोई सीमा नहीं है, लेकिन उपयोगकर्ताओं के लिए हाइरार्की पढ़ने योग्य रखें—आमतौर पर 3‑4 स्तर पर्याप्त होते हैं।

**प्र: Aspose बहुत बड़े Word फ़ाइलों को कैसे संभालता है?**  
उ: यह कंटेंट को स्ट्रीम करता है और `Document.optimizeResources()` जैसी मेथड्स प्रदान करता है ताकि मेमोरी उपयोग कम रहे।

**प्र: क्या PDF जनरेट होने के बाद बुकमार्क को एडिट कर सकता हूँ?**  
उ: हाँ, आप Aspose.PDF for Java का उपयोग करके बुकमार्क शीर्षक, डेस्टिनेशन या हाइरार्की को पोस्ट‑कन्वर्ज़न में संशोधित कर सकते हैं।

---

**अंतिम अपडेट:** 2026-04-27  
**टेस्ट किया गया संस्करण:** Aspose.Words 25.3 for Java  
**लेखक:** Aspose  

## संसाधन
- [Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/java/)
- [नवीनतम रिलीज़ डाउनलोड करें](https://releases.aspose.com/words/java/)
- [लाइसेंस खरीदें](https://purchase.aspose.com/buy)
- [फ़्री ट्रायल](https://releases.aspose.com/words/java/)
- [अस्थायी लाइसेंस आवेदन](https://purchase.aspose.com/temporary-license/)
- [Aspose सपोर्ट फ़ोरम](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}