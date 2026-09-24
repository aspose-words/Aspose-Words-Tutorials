---
date: 2025-12-20
description: Aspose.Words for Java के साथ HTML लोड करना और HTML को DOCX में बदलना
  सीखें। चरण-दर-चरण गाइड दिखाता है कि DOCX फ़ाइलें कैसे सहेजें और संरचित दस्तावेज़
  टैग्स का उपयोग कैसे करें।
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके HTML लोड करें और DOCX के रूप में सहेजें
url: /hi/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# HTML को लोड करना और Aspose.Words for Java का उपयोग करके DOCX के रूप में सहेजना

## Aspose.Words for Java के साथ HTML दस्तावेज़ों को लोड करने और सहेजने का परिचय

इस लेख में, हम **HTML को कैसे लोड करें** और इसे Aspose.Words for Java लाइब्रेरी का उपयोग करके DOCX फ़ाइल के रूप में सहेजने का पता लगाएंगे। Aspose.Words एक शक्तिशाली API है जो आपको प्रोग्रामेटिक रूप से Word दस्तावेज़ों को नियंत्रित करने देता है, और इसमें HTML आयात/निर्यात के लिए मजबूत समर्थन शामिल है। हम पूरी प्रक्रिया को कवर करेंगे, लोड विकल्पों को सेट करने से लेकर परिणाम को Word दस्तावेज़ के रूप में सहेजने तक।

## त्वरित उत्तर
- **HTML लोड करने के लिए मुख्य क्लास कौन सी है?** `Document` together with `HtmlLoadOptions`.
- **कौन सा विकल्प Structured Document Tags को सक्षम करता है?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **क्या मैं HTML को एक ही चरण में DOCX में बदल सकता हूँ?** Yes – load the HTML and call `doc.save(...".docx")`.
- **क्या विकास के लिए लाइसेंस चाहिए?** A free trial works for testing; a commercial license is required for production.
- **कौन सा Java संस्करण आवश्यक है?** Java 8 or higher is supported.

## Aspose.Words के संदर्भ में “HTML को कैसे लोड करें” क्या है?

HTML को लोड करना का अर्थ है HTML स्ट्रिंग या फ़ाइल को पढ़ना और उसे Aspose.Words `Document` ऑब्जेक्ट में परिवर्तित करना। इस ऑब्जेक्ट को फिर संपादित, फ़ॉर्मेट या API द्वारा समर्थित किसी भी फ़ॉर्मेट जैसे DOCX, PDF, या RTF में सहेजा जा सकता है।

## HTML‑to‑DOCX रूपांतरण के लिए Aspose.Words क्यों उपयोग करें?
- **लेआउट को संरक्षित करता है** – टेबल, सूची और छवियों को अपरिवर्तित रखा जाता है।
- **Structured Document Tags को सपोर्ट करता है** – Word में कंटेंट कंट्रोल बनाने के लिए आदर्श।
- **Microsoft Office की आवश्यकता नहीं** – किसी भी सर्वर या क्लाउड वातावरण में काम करता है।
- **उच्च प्रदर्शन** – बड़े HTML फ़ाइलों को तेज़ी से प्रोसेस करता है।

## पूर्वापेक्षाएँ

1. **Aspose.Words for Java Library** – इसे [here](https://releases.aspose.com/words/java/) से डाउनलोड करें।
2. **Java Development Environment** – JDK 8+ स्थापित और कॉन्फ़िगर किया हुआ।
3. **Java I/O की बुनियादी परिचितता** – हम `ByteArrayInputStream` का उपयोग करके HTML स्ट्रिंग प्रदान करेंगे।

## HTML दस्तावेज़ों को कैसे लोड करें

नीचे एक संक्षिप्त उदाहरण है जो **structured document tag** सुविधा को सक्षम करते हुए HTML स्निपेट को लोड करने को दर्शाता है।

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**व्याख्या**

- हम एक `HTML` स्ट्रिंग बनाते हैं जिसमें एक सरल `<select>` कंट्रोल होता है।
- `HtmlLoadOptions` हमें यह निर्दिष्ट करने देता है कि HTML को कैसे व्याख्यायित किया जाए। पसंदीदा कंट्रोल प्रकार को `STRUCTURED_DOCUMENT_TAG` सेट करने से Aspose.Words HTML फ़ॉर्म कंट्रोल को Word कंटेंट कंट्रोल में बदल देता है।
- `Document` कन्स्ट्रक्टर UTF‑8 एन्कोडिंग का उपयोग करके `ByteArrayInputStream` से HTML पढ़ता है।

## DOCX के रूप में सहेजें (HTML को DOCX में बदलें)

एक बार HTML `Document` में लोड हो जाने पर, इसे DOCX फ़ाइल के रूप में सहेजना सरल है:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

`"Your Directory Path"` को उस वास्तविक फ़ोल्डर से बदलें जहाँ आप आउटपुट फ़ाइल चाहते हैं।

## HTML दस्तावेज़ों को लोड और सहेजने के लिए पूर्ण स्रोत कोड

नीचे पूर्ण, तैयार‑चलाने‑योग्य उदाहरण है जो लोड और सहेजने के चरणों को मिलाता है। इसे अपने IDE में कॉपी‑पेस्ट करने के लिए स्वतंत्र महसूस करें।

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## सामान्य समस्याएँ एवं सुझाव

| Issue | Why it Happens | How to Fix |
|-------|----------------|------------|
| **फ़ॉन्ट गायब** | HTML उन फ़ॉन्ट्स का उल्लेख करता है जो सर्वर पर स्थापित नहीं हैं। | `FontSettings` का उपयोग करके फ़ॉन्ट्स को DOCX में एम्बेड करें या सुनिश्चित करें कि आवश्यक फ़ॉन्ट्स उपलब्ध हों। |
| **छवियाँ नहीं दिख रही हैं** | रिलेटिव इमेज पाथ को हल नहीं किया जा सकता। | एब्सोल्यूट URLs का उपयोग करें या छवियों को `MemoryStream` में लोड करें और `HtmlLoadOptions.setImageSavingCallback` सेट करें। |
| **कंट्रोल प्रकार परिवर्तित नहीं हुआ** | `setPreferredControlType` सेट नहीं है या गलत enum पर सेट है। | सुनिश्चित करें कि आप `HtmlControlType.STRUCTURED_DOCUMENT_TAG` का उपयोग कर रहे हैं। |
| **एन्कोडिंग समस्याएँ** | HTML स्ट्रिंग अलग charset में एन्कोडेड है। | स्ट्रिंग को बाइट्स में बदलते समय हमेशा `StandardCharsets.UTF_8` का उपयोग करें। |

## अक्सर पूछे जाने वाले प्रश्न

### Aspose.Words for Java कैसे स्थापित करें?
Aspose.Words for Java को [here](https://releases.aspose.com/words/java/) से डाउनलोड किया जा सकता है। डाउनलोड पेज पर इंस्टॉलेशन गाइड का पालन करके JAR फ़ाइलों को अपने प्रोजेक्ट की classpath में जोड़ें।

### क्या मैं Aspose.Words का उपयोग करके जटिल HTML दस्तावेज़ लोड कर सकता हूँ?
हाँ, Aspose.Words for Java जटिल HTML को संभाल सकता है, जिसमें नेस्टेड टेबल, CSS स्टाइलिंग, और JavaScript‑मुक्त इंटरैक्टिव एलिमेंट्स शामिल हैं। आयात को बेहतर बनाने के लिए `HtmlLoadOptions` (जैसे, `setLoadImages` या `setCssStyleSheetFileName`) को समायोजित करें।

### Aspose.Words कौन से अन्य दस्तावेज़ फ़ॉर्मेट सपोर्ट करता है?
Aspose.Words DOC, DOCX, RTF, HTML, PDF, EPUB, XPS, और कई अन्य फ़ॉर्मेट को सपोर्ट करता है। API इन सभी फ़ॉर्मेट में एक‑लाइन सहेजने की सुविधा देता है।

### क्या Aspose.Words एंटरप्राइज़‑स्तर के दस्तावेज़ ऑटोमेशन के लिए उपयुक्त है?
बिल्कुल। यह बड़े एंटरप्राइज़ द्वारा स्वचालित रिपोर्ट जेनरेशन, बड़े पैमाने पर दस्तावेज़ रूपांतरण, और Microsoft Office निर्भरताओं के बिना सर्वर‑साइड दस्तावेज़ प्रोसेसिंग के लिए उपयोग किया जाता है।

### Aspose.Words for Java के लिए अधिक दस्तावेज़ीकरण और उदाहरण कहाँ मिलेंगे?
आप पूरी API रेफ़रेंस और अतिरिक्त ट्यूटोरियल Aspose.Words for Java दस्तावेज़ीकरण साइट पर देख सकते हैं: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**अंतिम अपडेट:** 2025-12-20  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12 (लेखन के समय नवीनतम)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}