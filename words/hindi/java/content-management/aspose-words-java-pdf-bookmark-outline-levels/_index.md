---
date: '2026-03-28'
description: Aspose.Words for Java का उपयोग करके PDF में बुकमार्क जोड़ना और नेस्टेड
  बुकमार्क प्रबंधित करना सीखें। स्पष्ट रूपरेखा स्तरों के साथ दस्तावेज़ नेविगेशन को
  बढ़ाएँ।
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words Java का उपयोग करके PDF बुकमार्क और रूपरेखा स्तर जोड़ें
url: /hi/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java का उपयोग करके PDF बुकमार्क और रूपरेखा स्तर जोड़ें

## परिचय
यदि आप Word दस्तावेज़ों को PDF में परिवर्तित करते समय व्यवस्थित रहने वाले **PDF बुकमार्क जोड़ने** में कठिनाई महसूस कर रहे हैं, तो आप सही जगह पर आए हैं। इस ट्यूटोरियल में हम बताएँगे कि Aspose.Words for Java का उपयोग करके **PDF में नेस्टेड बुकमार्क** कैसे बनाएँ, रूपरेखा स्तर निर्धारित करें, और एक साफ़, नेविगेबल PDF फ़ाइल उत्पन्न करें।

**आप क्या सीखेंगे**
- अपने प्रोजेक्ट में Aspose.Words for Java सेट अप करें  
- Word दस्तावेज़ से सीधे **PDF में नेस्टेड बुकमार्क** बनाएं  
- हायरार्किकल दृश्य के लिए बुकमार्क रूपरेखा स्तर कॉन्फ़िगर करें  
- सही ढंग से संरचित बुकमार्क के साथ अंतिम दस्तावेज़ को PDF के रूप में सहेजें  

### त्वरित उत्तर
- **PDF बुकमार्क जोड़ने का मुख्य लाभ क्या है?** बड़े दस्तावेज़ों में नेविगेशन और उपयोगकर्ता अनुभव को बेहतर बनाता है।  
- **Java में आसान PDF बुकमार्क निर्माण के लिए कौन सी लाइब्रेरी सक्षम करती है?** Aspose.Words for Java।  
- **क्या बुकमार्क फीचर्स उपयोग करने के लिए लाइसेंस आवश्यक है?** मूल्यांकन के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए लाइसेंस आवश्यक है।  
- **क्या मैं प्रत्येक बुकमार्क के लिए अलग-अलग रूपरेखा स्तर सेट कर सकता हूँ?** हाँ, `PdfSaveOptions` में `BookmarksOutlineLevelCollection` का उपयोग करके।  
- **क्या यह विधि नवीनतम Aspose.Words संस्करण के साथ संगत है?** बिल्कुल – संस्करण 25.3 और उसके बाद के साथ काम करता है।

## PDF बुकमार्क जोड़ना क्या है?
PDF बुकमार्क जोड़ना का अर्थ है PDF के नेविगेशन पेन में क्लिक करने योग्य प्रविष्टियाँ डालना जो दस्तावेज़ के विशिष्ट भागों की ओर संकेत करती हैं। जब इन्हें रूपरेखा स्तरों के साथ जोड़ा जाता है, तो ये बुकमार्क एक पेड़‑जैसी संरचना बनाते हैं जो आपके दस्तावेज़ की पदानुक्रम को प्रतिबिंबित करती है।

## PDF में नेस्टेड बुकमार्क क्यों उपयोग करें?
नेस्टेड बुकमार्क पाठकों को उच्च‑स्तरीय अनुभागों से विस्तृत उप‑अनुभागों तक बिना पृष्ठों को स्क्रॉल किए पहुँचने देते हैं। यह विशेष रूप से **कानूनी अनुबंध**, **तकनीकी रिपोर्ट**, और **ई‑लर्निंग मैनुअल** के लिए मूल्यवान है जहाँ त्वरित संदर्भ आवश्यक है।

## पूर्वापेक्षाएँ
- **लाइब्रेरी और निर्भरताएँ**: Aspose.Words for Java (संस्करण 25.3 या बाद का)।  
- **पर्यावरण**: JDK 8+ और IntelliJ IDEA या Eclipse जैसे IDE।  
- **ज्ञान**: बेसिक Java, Maven या Gradle की परिचितता।

## Aspose.Words सेट अप करना
शुरू करने के लिए, अपने प्रोजेक्ट में आवश्यक निर्भरताएँ शामिल करें। यहाँ Maven और Gradle के साथ इसे कैसे करें:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### लाइसेंस प्राप्ति
Aspose.Words एक व्यावसायिक उत्पाद है, लेकिन आप मुफ्त ट्रायल से शुरू कर सकते हैं:

1. **Free Trial** – पूर्ण क्षमताओं का परीक्षण करने के लिए [Aspose's release page](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
2. **Temporary License** – यदि आपको अल्पकालिक कुंजी चाहिए तो [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) पर आवेदन करें।  
3. **Purchase** – [Aspose’s purchasing portal](https://purchase.aspose.com/buy) से स्थायी लाइसेंस प्राप्त करें।

लाइसेंस फ़ाइल प्राप्त करने के बाद, सभी सुविधाओं को अनलॉक करने के लिए इसे अपने कोड में लोड करें।

## कार्यान्वयन गाइड
आइए कार्यान्वयन को स्पष्ट, क्रमांकित चरणों में विभाजित करें।

### चरण 1: दस्तावेज़ और बिल्डर को प्रारंभ करें
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
यह एक नया Word दस्तावेज़ बनाता है जिसे हम सामग्री और बुकमार्क से भरेंगे।

### चरण 2: नेस्टेड बुकमार्क डालें
#### पहला (पैरेंट) बुकमार्क बनाएं
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### पैरेंट के अंदर एक चाइल्ड बुकमार्क नेस्ट करें
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### पैरेंट बुकमार्क बंद करें
```java
builder.endBookmark("Bookmark 1");
```

#### तीसरा, स्वतंत्र बुकमार्क जोड़ें
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### चरण 3: बुकमार्क रूपरेखा स्तर कॉन्फ़िगर करें
#### `PdfSaveOptions` सेट अप करें
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### हायरार्की स्तर असाइन करें
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### दस्तावेज़ को PDF के रूप में सहेजें
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### सामान्य समस्याएँ और समाधान
- **Missing bookmarks** – प्रत्येक `startBookmark` के लिए मिलते‑जुलते `endBookmark` की जाँच करें।  
- **Incorrect outline hierarchy** – स्तर संख्याओं को दोबारा जांचें; कम संख्या नेविगेशन पेन में उच्च स्तर दर्शाती है।  
- **Large documents** – मेमोरी उपयोग कम करने के लिए सहेजने से पहले `doc.optimizeResources()` कॉल करें।

## व्यावहारिक अनुप्रयोग
1. **Legal Documents** – धाराओं और उप‑धाराओं पर जल्दी से जाएँ।  
2. **Annual Reports** – अध्यायों, अनुभागों और सामग्री तालिकाओं के बीच नेविगेट करें।  
3. **Educational Material** – छात्रों को PDF के भीतर क्लिक करने योग्य सिलेबस प्रदान करें।

## प्रदर्शन संबंधी विचार
- परिवर्तन से पहले किसी भी अनावश्यक छवियों या छिपे हुए अनुभागों को हटाएँ।  
- बहुत बड़े फ़ाइलों के लिए मेमोरी उपयोग कम रखने हेतु स्ट्रीमिंग API का उपयोग करें।

## निष्कर्ष
अब आपके पास Aspose.Words for Java का उपयोग करके **PDF बुकमार्क जोड़ने**, उनके रूपरेखा स्तर कॉन्फ़िगर करने, और एक सुव्यवस्थित PDF उत्पन्न करने की पूर्ण, उत्पादन‑तैयार विधि है। यह तकनीक दस्तावेज़ उपयोगिता को नाटकीय रूप से सुधारती है और आपको PDF नेविगेशन पर सूक्ष्म नियंत्रण देती है।

**Next Steps** – इस विधि को Aspose.PDF for Java के साथ मिलाकर PDF बन जाने के बाद अतिरिक्त बुकमार्क संपादित या जोड़ने का प्रयास करें।

## FAQ अनुभाग
1. **मैं Aspose.Words for Java कैसे स्थापित करूँ?**  
   इसे Maven या Gradle निर्भरता के रूप में शामिल करें और रनटाइम पर अपना लाइसेंस फ़ाइल लोड करें।  
2. **क्या मैं बुकमार्क को बिना रूपरेखा स्तरों के उपयोग कर सकता हूँ?**  
   हाँ, लेकिन रूपरेखा स्तर एक पदानुक्रमित दृश्य प्रदान करते हैं जो नेविगेशन को बहुत आसान बनाता है।  
3. **बुकमार्क नेस्टिंग पर क्या सीमाएँ हैं?**  
   कोई कठोर सीमा नहीं है, लेकिन सर्वोत्तम उपयोगकर्ता अनुभव के लिए पदानुक्रम को तर्कसंगत रखें।  
4. **Aspose बड़े दस्तावेज़ों को कैसे संभालता है?**  
   यह संसाधनों को कुशलता से स्ट्रीम करता है; हालांकि, बहुत बड़े फ़ाइलों के लिए आपको `optimizeResources()` कॉल करना चाहिए।  
5. **क्या मैं PDF सहेजने के बाद बुकमार्क संशोधित कर सकता हूँ?**  
   बिल्कुल – परिवर्तन के बाद बुकमार्क संपादित करने के लिए Aspose.PDF for Java का उपयोग करें।

## अतिरिक्त अक्सर पूछे जाने वाले प्रश्न
**Q: क्या यह तकनीक DOCX को PDF में परिवर्तित करते समय काम करती है?**  
A: हाँ, स्रोत Word फ़ॉर्मेट चाहे जो भी हो, समान बुकमार्क निर्माण चरण लागू होते हैं।

**Q: क्या बुकमार्क के लिए कस्टम रंग या आइकन सेट करना संभव है?**  
A: बुकमार्क की उपस्थिति PDF व्यूअर द्वारा नियंत्रित होती है; Aspose.Words पदानुक्रम और नामकरण पर केंद्रित है।

**Q: क्या रूपरेखा स्तर सभी PDF रीडर्स में दिखेंगे?**  
A: अधिकांश आधुनिक रीडर्स (Adobe Acrobat, Foxit, Chrome) Aspose.Words द्वारा परिभाषित रूपरेखा पदानुक्रम का सम्मान करते हैं।

## संसाधन
- [Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/java/)  
- [नवीनतम रिलीज़ डाउनलोड करें](https://releases.aspose.com/words/java/)  
- [लाइसेंस खरीदें](https://purchase.aspose.com/buy)  
- [मुफ्त ट्रायल](https://releases.aspose.com/words/java/)  
- [अस्थायी लाइसेंस आवेदन](https://purchase.aspose.com/temporary-license/)  
- [Aspose सपोर्ट फ़ोरम](https://forum.aspose.com/c/words/10)

---

**Last Updated:** 2026-03-28  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}