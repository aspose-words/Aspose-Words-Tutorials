---
date: '2025-11-27'
description: Aspose.Words का उपयोग करके जावा में बुकमार्क बनाना, बुकमार्क के साथ PDF
  जनरेट करना, और Word को PDF में बदलना सीखें। यह गाइड नेस्टेड बुकमार्क और आउटलाइन
  लेवल्स को कवर करता है।
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: hi
title: Aspose.Words Java का उपयोग करके PDFs में बुकमार्क बनाना और आउटलाइन लेवल सेट
  करना
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java का उपयोग करके PDFs में बुकमार्क कैसे बनाएं और आउटलाइन लेवल सेट करें

## परिचय
यदि आप कभी Word दस्तावेज़ को PDF में बदलते समय व्यवस्थित बुकमार्क बनाने में कठिनाई महसूस कर चुके हैं, तो आप सही जगह पर हैं। इस ट्यूटोरियल में हम बुकमार्क के साथ PDF बनाने, उन्हें नेस्ट करने, और आउटलाइन लेवल असाइन करने की पूरी प्रक्रिया को समझेंगे ताकि अंतिम PDF को नेविगेट करना आसान हो। अंत तक आप **convert Word PDF Java**‑स्टाइल में एक साफ़ बुकमार्क हाइरार्की के साथ PDF बना सकेंगे जो किसी भी PDF व्यूअर में काम करती है।

### आप क्या सीखेंगे
- अपने विकास पर्यावरण में Aspose.Words for Java सेट अप करें।  
- **बुकमार्क कैसे बनाएं** प्रोग्रामेटिकली और उन्हें नेस्ट करें।  
- बुकमार्क आउटलाइन लेवल कॉन्फ़िगर करें ताकि PDF में बुकमार्क दस्तावेज़ संरचना को दर्शाएँ।  
- बुकमार्क हाइरार्की को बरकरार रखते हुए Word फ़ाइल को PDF के रूप में सहेजें।

## त्वरित उत्तर
- **दस्तावेज़ बनाने के लिए मुख्य क्लास कौन सी है?** `DocumentBuilder`।  
- **बुकमार्क हाइरार्की को नियंत्रित करने वाला विकल्प कौन सा है?** `BookmarksOutlineLevelCollection` `PdfSaveOptions` के अंदर।  
- **क्या मैं Maven या Gradle का उपयोग कर सकता हूँ?** हाँ – दोनों नीचे दिखाए गए हैं।  
- **क्या मुझे लाइसेंस चाहिए?** परीक्षण के लिए मुफ्त ट्रायल काम करता है; उत्पादन के लिए स्थायी लाइसेंस आवश्यक है।  
- **क्या यह तरीका बड़े दस्तावेज़ों के लिए उपयुक्त है?** हाँ, लेकिन मेमोरी‑ऑप्टिमाइज़ेशन तकनीकों पर विचार करें (जैसे, अनउपयोगी संसाधनों को हटाना)।

### पूर्वापेक्षाएँ
शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:

- **लाइब्रेरीज़ और निर्भरताएँ** – Aspose.Words for Java (25.3 या बाद का)।  
- **पर्यावरण** – JDK 8 या नया, और IntelliJ IDEA या Eclipse जैसे IDE।  
- **बुनियादी ज्ञान** – Java प्रोग्रामिंग मूल बातें और Maven या Gradle की परिचितता।

## Aspose.Words सेट अप करना
शुरू करने के लिए, अपने प्रोजेक्ट में आवश्यक निर्भरताएँ शामिल करें। यहाँ Maven या Gradle का उपयोग करके Aspose.Words जोड़ने का तरीका है:

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
Aspose.Words एक व्यावसायिक लाइब्रेरी है, लेकिन आप मुफ्त ट्रायल से शुरू कर सकते हैं:

1. **Free Trial** – [Aspose रिलीज़ पेज](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
2. **Temporary License** – यदि आपको अल्पकालिक कुंजी चाहिए तो [temporary‑license पेज](https://purchase.aspose.com/temporary-license/) पर आवेदन करें।  
3. **Full License** – उत्पादन उपयोग के लिए [Aspose खरीद पोर्टल](https://purchase.aspose.com/buy) से खरीदें।

लाइसेंस फ़ाइल प्राप्त करने के बाद, सभी सुविधाओं को अनलॉक करने के लिए इसे एप्लिकेशन स्टार्ट‑अप पर लोड करें।

## Aspose.Words Java के साथ PDFs में बुकमार्क कैसे बनाएं
नीचे हम कार्यान्वयन को स्पष्ट, क्रमांकित चरणों में विभाजित करते हैं। प्रत्येक चरण में एक संक्षिप्त व्याख्या और उसके बाद मूल कोड ब्लॉक (अपरिवर्तित) शामिल है।

### चरण 1: एक Document और DocumentBuilder को इनिशियलाइज़ करें
हम एक नई `Document` इंस्टेंस और `DocumentBuilder` से शुरू करते हैं जो हमें कंटेंट और बुकमार्क डालने की अनुमति देता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### चरण 2: पहला (पैरेंट) बुकमार्क डालें
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### चरण 3: पैरेंट के अंदर चाइल्ड बुकमार्क नेस्ट करें
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### चरण 4: पैरेंट बुकमार्क बंद करें
```java
builder.endBookmark("Bookmark 1");
```

### चरण 5: एक स्वतंत्र तीसरा बुकमार्क जोड़ें
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## बुकमार्क आउटलाइन लेवल कॉन्फ़िगर करना
बुकमार्क स्थापित होने के बाद, हम Aspose.Words को बताते हैं कि ये बुकमार्क PDF के आउटलाइन (बाएँ‑हाथ नेविगेशन पेन) में कैसे दिखेंगे।

### चरण 6: PdfSaveOptions तैयार करें
`PdfSaveOptions` हमें आउटलाइन सेटिंग्स तक पहुँच देता है।

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### चरण 7: हाइरार्की लेवल असाइन करें
प्रत्येक बुकमार्क को एक पूर्णांक लेवल मिलता है; छोटे नंबर हाइरार्की में ऊँचे होते हैं।

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### चरण 8: दस्तावेज़ को PDF के रूप में सहेजें
अंत में, बुकमार्क आउटलाइन को बरकरार रखते हुए Word दस्तावेज़ को PDF में निर्यात करें।

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## बुकमार्क के साथ PDF जनरेट करने के लिए इस दृष्टिकोण का उपयोग क्यों करें?
- **Professional Navigation** – पाठक सीधे सेक्शन पर जा सकते हैं, जिससे बड़े रिपोर्ट या कानूनी अनुबंधों की उपयोगिता बढ़ती है।  
- **Full Control** – आप हाइरार्की तय करते हैं, PDF व्यूअर नहीं।  
- **Cross‑Platform** – यह Windows, Linux, और macOS पर समान रूप से काम करता है क्योंकि यह शुद्ध Java है।  

## सामान्य समस्याएँ और समाधान
| लक्षण | संभावित कारण | समाधान |
|---|---|---|
| PDF में बुकमार्क नहीं दिख रहे हैं | `startBookmark` का मेल नहीं खाने वाला `endBookmark` | सुनिश्चित करें कि प्रत्येक `startBookmark` का संबंधित `endBookmark` है। |
| हाइरार्की गलत | आउटलाइन लेवल क्रम से बाहर असाइन किए गए | सुनिश्चित करें कि पैरेंट बुकमार्क के लेवल नंबर उनके चाइल्ड से कम हों। |
| लाइसेंस लागू नहीं हुआ | दस्तावेज़ निर्माण से पहले लाइसेंस फ़ाइल लोड नहीं हुई | अपनी एप्लिकेशन की शुरुआत में लाइसेंस लोड करें (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## व्यावहारिक अनुप्रयोग
1. **Legal Documents** – खंड, परिशिष्ट और अनुबंधों को जल्दी नेविगेट करें।  
2. **Financial Reports** – आय विवरण, बैलेंस शीट, और नोट्स जैसे सेक्शन के बीच कूदें।  
3. **E‑Learning Materials** – एक सामग्री-सूची प्रदान करें जो PDF आउटलाइन को दर्शाती हो।  

## प्रदर्शन संबंधी विचार
- **Memory Management** – बहुत बड़े Word फ़ाइलों के लिए, सहेजने से पहले `doc.cleanup()` कॉल करने पर विचार करें।  
- **Resource Optimization** – अनउपयोगी इमेज या स्टाइल हटाकर PDF आकार छोटा रखें।  

## अक्सर पूछे जाने वाले प्रश्न

**Q: मैं Aspose.Words for Java कैसे इंस्टॉल करूँ?**  
A: पहले दिखाए गए Maven या Gradle निर्भरता जोड़ें, फिर लाइसेंस फ़ाइल को क्लासपाथ में रखें और रनटाइम पर लोड करें।

**Q: क्या मैं आउटलाइन लेवल सेट किए बिना बुकमार्क बना सकता हूँ?**  
A: हाँ, लेकिन PDF व्यूअर उन्हें एक फ्लैट सूची के रूप में दिखाएगा, जिससे जटिल दस्तावेज़ों में नेविगेट करना कठिन हो सकता है।

**Q: बुकमार्क कितनी गहराई तक नेस्ट किए जा सकते हैं, इसकी कोई सीमा है?**  
A: तकनीकी रूप से कोई सीमा नहीं है, लेकिन अधिकांश PDF व्यूअर आराम से 9 लेवल तक सपोर्ट करते हैं। पाठकों के लिए हाइरार्की को तर्कसंगत रखें।

**Q: Aspose बहुत बड़े Word फ़ाइलों को कैसे संभालता है?**  
A: लाइब्रेरी कंटेंट को स्ट्रीम करती है और `Document.optimizeResources()` जैसे मेथड प्रदान करती है जिससे मेमोरी फुटप्रिंट कम हो।

**Q: क्या मैं PDF जनरेट होने के बाद बुकमार्क को एडिट कर सकता हूँ?**  
A: बिल्कुल – आप Aspose.PDF for Java का उपयोग करके मौजूदा PDF में बुकमार्क जोड़, हट या नाम बदल सकते हैं।

## संसाधन
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)  
- [Download Latest Releases](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2025-11-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose