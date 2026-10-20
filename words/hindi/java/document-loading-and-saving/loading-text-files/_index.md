---
date: 2025-12-27
description: Aspose.Words for Java का उपयोग करके दिशा सेट करना, txt फ़ाइलें लोड करना,
  स्पेस हटाना, और txt को docx में बदलना सीखें।
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java के साथ दिशा सेट करना और टेक्स्ट फ़ाइलें लोड करना
url: /hi/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ दिशा सेट करने और टेक्स्ट फ़ाइलें लोड करने का तरीका

## Aspose.Words for Java के साथ टेक्स्ट फ़ाइलें लोड करने का परिचय

इस गाइड में आप **टेक्स्ट लोड करते समय दिशा कैसे सेट करें** जानेंगे और व्यावहारिक तरीके देखेंगे कि **txt लोड करना**, **स्पेस ट्रिम करना**, और **txt को docx में बदलना** Aspose.Words for Java का उपयोग करके कैसे किया जाता है। चाहे आप एक डॉक्यूमेंट‑कन्वर्ज़न सर्विस बना रहे हों या लिस्ट डिटेक्शन पर सूक्ष्म नियंत्रण चाहिए, यह ट्यूटोरियल स्पष्ट व्याख्याओं और तैयार‑कोड के साथ हर कदम दिखाता है।

## त्वरित उत्तर
- **लोड की गई TXT फ़ाइल के लिए टेक्स्ट दिशा कैसे सेट करें?** `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` का उपयोग करें या `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT` निर्दिष्ट करें।
- **क्या Aspose.Words साधारण टेक्स्ट में क्रमांकित सूचियों का पता लगा सकता है?** हाँ – `TxtLoadOptions` में `DetectNumberingWithWhitespaces` को सक्षम करें।
- **लीडिंग और ट्रेलिंग स्पेस कैसे ट्रिम करें?** `TxtLeadingSpacesOptions.TRIM` और `TxtTrailingSpacesOptions.TRIM` सेट करें।
- **क्या एक लाइन में TXT फ़ाइल को DOCX में बदलना संभव है?** `TxtLoadOptions` के साथ TXT लोड करें और `Document.save("output.docx")` कॉल करें।
- **कौन सा Java संस्करण आवश्यक है?** Aspose.Words 24.x के लिए Java 8+ पर्याप्त है।

## Aspose.Words में “दिशा सेट करने” का क्या अर्थ है?
जब टेक्स्ट फ़ाइल में दाएँ‑से‑बाएँ स्क्रिप्ट (जैसे हिब्रू या अरबी) होते हैं, तो लाइब्रेरी को पढ़ने का क्रम पता होना चाहिए। `DocumentDirection` एन्‍यू आपको **दिशा सेट** करने की अनुमति देता है या Aspose को ऑटो‑डिटेक्ट करने देता है, जिससे लेआउट और बिडी फॉर्मेटिंग सही रहती है।

## TXT फ़ाइलें लोड करने के लिए Aspose.Words क्यों उपयोग करें?
- **सटीक सूची पहचान** – क्रमांकित, बुलेटेड और व्हाइटस्पेस‑डिलिमिटेड सूचियों को संभालता है।
- **सूक्ष्म स्पेस हैंडलिंग** – लीडिंग/ट्रेलिंग स्पेस को ट्रिम या संरक्षित करें।
- **ऑटोमैटिक टेक्स्ट‑दिशा पहचान** – बहुभाषी दस्तावेज़ों के लिए आदर्श।
- **एक‑स्टेप कन्वर्ज़न** – `.txt` लोड करें और `.docx`, `.pdf` या किसी भी समर्थित फ़ॉर्मेट में सेव करें।

## पूर्वापेक्षाएँ
- Java 8 या नया।
- Aspose.Words for Java लाइब्रेरी (Maven/Gradle डिपेंडेंसी जोड़ें या JAR को प्रोजेक्ट में शामिल करें)।
- Java I/O स्ट्रीम्स का बुनियादी ज्ञान।

## चरण‑दर‑चरण गाइड

### चरण 1: सूचियों का पता लगाना (txt कैसे लोड करें)
टेक्स्ट दस्तावेज़ लोड करने और स्वचालित रूप से सूचियों का पता लगाने के लिए, एक `TxtLoadOptions` इंस्टेंस बनाएं और सूची पहचान सक्षम करें। नीचे का कोड कई सूची शैलियों को दिखाता है और व्हाइटस्पेस‑सचेत नंबरिंग को सक्षम करता है।

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **प्रो टिप:** यदि आपको केवल बुनियादी सूची पहचान चाहिए, तो आप व्हाइटस्पेस विकल्प को छोड़ सकते हैं – Aspose अभी भी मानक `1.` और `1)` पैटर्न को पहचान लेगा।

### चरण 2: स्पेस विकल्पों को संभालना (स्पेस कैसे ट्रिम करें)
लीडिंग और ट्रेलिंग स्पेस अक्सर फ़ॉर्मेटिंग गड़बड़ी का कारण बनते हैं। इस व्यवहार को नियंत्रित करने के लिए `TxtLeadingSpacesOptions` और `TxtTrailingSpacesOptions` का उपयोग करें।

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **यह क्यों महत्वपूर्ण है:** स्पेस ट्रिम करने से परिणामी DOCX में अनचाहा इंडेंटेशन नहीं रहता, जिससे दस्तावेज़ साफ़ दिखता है और मैन्युअल पोस्ट‑प्रोसेसिंग की आवश्यकता नहीं पड़ती।

### चरण 3: टेक्स्ट दिशा नियंत्रित करना (दिशा कैसे सेट करें)
दाएँ‑से‑बाएँ भाषाओं के लिए, लोड करने से पहले दस्तावेज़ दिशा सेट करें। नीचे का उदाहरण एक हिब्रू टेक्स्ट फ़ाइल लोड करता है और दिशा की पुष्टि के लिए बिडी फ़्लैग प्रिंट करता है।

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **सामान्य गलती:** `DocumentDirection` सेट करना भूल जाना, जिससे अरबी/हिब्रू टेक्स्ट उल्टा दिखता है और अक्षर गलत क्रम में आते हैं।

### Aspose.Words for Java के साथ टेक्स्ट फ़ाइलें लोड करने का पूर्ण स्रोत कोड
नीचे पूरा, तैयार‑चलाने‑योग्य स्रोत दिया गया है जो सूची पहचान, स्पेस हैंडलिंग और दिशा नियंत्रण को मिलाता है। आप इसे एक ही क्लास में कॉपी‑पेस्ट कर तीन टेस्ट मेथड्स को अलग‑अलग चला सकते हैं।

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## सामान्य समस्याएँ और समाधान
| समस्या | कारण | समाधान |
|-------|-------|-----|
| सूचियाँ पहचान नहीं रही हैं | व्हाइटस्पेस‑डिलिमिटेड सूचियों के लिए `DetectNumberingWithWhitespaces` `false` रहा | `loadOptions.setDetectNumberingWithWhitespaces(true)` सक्षम करें |
| लोड करने के बाद अतिरिक्त इंडेंटेशन | लीडिंग स्पेस संरक्षित रहे | `TxtLeadingSpacesOptions.TRIM` सेट करें |
| हिब्रू टेक्स्ट उल्टा दिख रहा है | दस्तावेज़ दिशा सेट नहीं की गई या `LEFT_TO_RIGHT` पर सेट थी | `DocumentDirection.AUTO` या `RIGHT_TO_LEFT` उपयोग करें |
| आउटपुट DOCX खाली है | दूसरे लोड से पहले इनपुट स्ट्रीम रीसेट नहीं हुई | प्रत्येक लोड कॉल के लिए नया `ByteArrayInputStream` बनाएं |

## अक्सर पूछे जाने वाले प्रश्न

### प्रश्न: Aspose.Words for Java क्या है?
**उत्तर:** Aspose.Words for Java एक शक्तिशाली दस्तावेज़ प्रोसेसिंग लाइब्रेरी है जो डेवलपर्स को Java एप्लिकेशन में प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाना, संशोधित करना और कन्वर्ट करना सक्षम करती है। यह सरल टेक्स्ट लोडिंग से लेकर जटिल फ़ॉर्मेटिंग और कन्वर्ज़न तक की विस्तृत सुविधाएँ प्रदान करती है।

### प्रश्न: मैं Aspose.Words for Java के साथ कैसे शुरू करूँ?
**उत्तर:** 1. Aspose.Words for Java लाइब्रेरी डाउनलोड और इंस्टॉल करें। 2. विस्तृत जानकारी और उदाहरणों के लिए [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) पर दस्तावेज़ देखें। 3. नमूना कोड और ट्यूटोरियल्स को एक्सप्लोर करें ताकि लाइब्रेरी का प्रभावी उपयोग सीख सकें।

### प्रश्न: Aspose.Words for Java का उपयोग करके टेक्स्ट दस्तावेज़ कैसे लोड करूँ?
**उत्तर:** `TxtLoadOptions` क्लास को `Document` कंस्ट्रक्टर के साथ उपयोग करें। सूची पहचान, स्पेस हैंडलिंग या टेक्स्ट दिशा जैसे विकल्पों को चरण‑दर‑चरण सेक्शन में दिखाए अनुसार सेट करें।

### प्रश्न: क्या मैं लोड किए गए टेक्स्ट दस्तावेज़ को अन्य फ़ॉर्मेट में बदल सकता हूँ?
**उत्तर:** हाँ। TXT फ़ाइल को `Document` ऑब्जेक्ट में लोड करने के बाद `doc.save("output.pdf")`, `doc.save("output.docx")` या किसी भी समर्थित फ़ॉर्मेट को कॉल करें।

### प्रश्न: लोड किए गए टेक्स्ट दस्तावेज़ में स्पेस कैसे संभालूँ?
**उत्तर:** `TxtLeadingSpacesOptions` और `TxtTrailingSpacesOptions` के साथ लीडिंग और ट्रेलिंग स्पेस को नियंत्रित करें। अनचाहे व्हाइटस्पेस हटाने के लिए `TRIM` सेट करें, या मूल स्पेस रखने के लिए `PRESERVE` सेट करें।

### प्रश्न: Aspose.Words for Java में टेक्स्ट दिशा का महत्व क्या है?
**उत्तर:** टेक्स्ट दिशा दाएँ‑से‑बाएँ स्क्रिप्ट (हिब्रू, अरबी आदि) के सही रेंडरिंग को सुनिश्चित करती है। `DocumentDirection` सेट करके आप बिडी टेक्स्ट को परिणामी दस्तावेज़ में सही ढंग से प्रदर्शित कर सकते हैं।

### प्रश्न: Aspose.Words for Java के लिए अतिरिक्त संसाधन और समर्थन कहाँ मिलेंगे?
**उत्तर:** API रेफ़रेंसेज़, कोड सैंपल और विस्तृत गाइड के लिए [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) देखें। आप Aspose कम्युनिटी फ़ोरम में शामिल हो सकते हैं या विशिष्ट प्रश्नों के लिए Aspose सपोर्ट से संपर्क कर सकते हैं।

### प्रश्न: क्या Aspose.Words for Java व्यावसायिक प्रोजेक्ट्स के लिए उपयुक्त है?
**उत्तर:** हाँ। यह व्यक्तिगत और व्यावसायिक दोनों उपयोग के लिए लाइसेंस विकल्प प्रदान करता है। अपने प्रोजेक्ट के लिए उपयुक्त योजना चुनने हेतु Aspose वेबसाइट पर लाइसेंस शर्तें देखें।

## निष्कर्ष
अब आपके पास **txt फ़ाइलें लोड करने**, **सूचियों का पता लगाने**, **स्पेस ट्रिम करने**, और **दिशा सेट करने** के लिए एक पूर्ण टूलकिट है, जिससे आप Aspose.Words for Java के साथ साधारण टेक्स्ट को समृद्ध Word दस्तावेज़ों में बदल सकते हैं। इन पैटर्न को अपनाकर दस्तावेज़ वर्कफ़्लो को स्वचालित करें, बहुभाषी समर्थन को बेहतर बनाएं, और हर बार साफ़, पेशेवर आउटपुट सुनिश्चित करें।

---

**अंतिम अपडेट:** 2025-12-27  
**परिक्षण किया गया:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}