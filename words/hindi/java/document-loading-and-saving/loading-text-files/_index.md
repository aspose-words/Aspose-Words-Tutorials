---
"description": "जावा के लिए Aspose.Words की शक्ति अनलॉक करें। टेक्स्ट डॉक्यूमेंट लोड करना, सूचियाँ प्रबंधित करना, स्पेस को संभालना और टेक्स्ट दिशा को नियंत्रित करना सीखें।"
"linktitle": "टेक्स्ट फ़ाइलें लोड करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words के साथ टेक्स्ट फ़ाइलें लोड करना"
"url": "/hi/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words के साथ टेक्स्ट फ़ाइलें लोड करना


## जावा के लिए Aspose.Words के साथ टेक्स्ट फ़ाइलें लोड करने का परिचय

इस गाइड में, हम जावा के लिए Aspose.Words का उपयोग करके टेक्स्ट फ़ाइलों को लोड करने और उन्हें Word दस्तावेज़ों के रूप में हेरफेर करने का तरीका जानेंगे। हम सूचियों का पता लगाने, रिक्त स्थान को संभालने और टेक्स्ट दिशा को नियंत्रित करने जैसे विभिन्न पहलुओं को कवर करेंगे।

## चरण 1: सूचियों का पता लगाना

किसी टेक्स्ट दस्तावेज़ को लोड करने और सूचियों का पता लगाने के लिए, आप इन चरणों का पालन कर सकते हैं:

```java
// स्ट्रिंग के रूप में एक सादा पाठ दस्तावेज़ बनाएं, जिसके कुछ भागों को सूचियों के रूप में समझा जा सके।
// लोड होने पर, पहली तीन सूचियाँ हमेशा Aspose.Words द्वारा पहचानी जाएंगी,
// और लोड होने के बाद उनके लिए सूची ऑब्जेक्ट बनाए जाएंगे।
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
// चौथी सूची, जिसमें सूची संख्या और सूची आइटम सामग्री के बीच रिक्त स्थान होता है,
// केवल तभी सूची के रूप में पहचाना जाएगा जब LoadOptions ऑब्जेक्ट में "DetectNumberingWithWhitespaces" को true पर सेट किया गया हो,
// ताकि संख्याओं से शुरू होने वाले पैराग्राफ को गलती से सूची समझे जाने से बचाया जा सके।
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// LoadOptions को पैरामीटर के रूप में लागू करते हुए दस्तावेज़ लोड करें और परिणाम सत्यापित करें।
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

यह कोड दर्शाता है कि विभिन्न सूची प्रारूपों के साथ एक पाठ दस्तावेज़ को कैसे लोड किया जाए और इसका उपयोग कैसे किया जाए `DetectNumberingWithWhitespaces` सूचियों का सही ढंग से पता लगाने का विकल्प।

## चरण 2: स्पेस विकल्पों को संभालना

किसी टेक्स्ट दस्तावेज़ को लोड करते समय आरंभिक और अंतिम रिक्त स्थान को नियंत्रित करने के लिए आप निम्नलिखित कोड का उपयोग कर सकते हैं:

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

इस उदाहरण में, हम एक टेक्स्ट दस्तावेज़ लोड करते हैं और इसका उपयोग करके प्रारंभिक और अंतिम रिक्त स्थान को ट्रिम करते हैं `TxtLeadingSpacesOptions.TRIM` और `TxtTrailingSpacesOptions.TRIM`.

## चरण 3: पाठ की दिशा नियंत्रित करना

टेक्स्ट दस्तावेज़ लोड करते समय टेक्स्ट दिशा निर्दिष्ट करने के लिए, आप निम्नलिखित कोड का उपयोग कर सकते हैं:

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

यह कोड दस्तावेज़ की दिशा को स्वतः पहचान पर सेट करता है (`DocumentDirection.AUTO`) और हिब्रू टेक्स्ट के साथ एक टेक्स्ट दस्तावेज़ लोड करता है। आप आवश्यकतानुसार दस्तावेज़ की दिशा समायोजित कर सकते हैं।

## जावा के लिए Aspose.Words के साथ टेक्स्ट फ़ाइलें लोड करने के लिए पूर्ण स्रोत कोड

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// स्ट्रिंग के रूप में एक सादा पाठ दस्तावेज़ बनाएं, जिसके कुछ भागों को सूचियों के रूप में समझा जा सके।
	// लोड होने पर, पहली तीन सूचियाँ हमेशा Aspose.Words द्वारा पहचानी जाएंगी,
	// और लोड होने के बाद उनके लिए सूची ऑब्जेक्ट बनाए जाएंगे।
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
	// चौथी सूची, सूची संख्या और सूची आइटम सामग्री के बीच रिक्त स्थान के साथ,
	// केवल तभी सूची के रूप में पहचाना जाएगा जब LoadOptions ऑब्जेक्ट में "DetectNumberingWithWhitespaces" को true पर सेट किया गया हो,
	// ताकि संख्याओं से शुरू होने वाले पैराग्राफ को गलती से सूची समझे जाने से बचाया जा सके।
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// LoadOptions को पैरामीटर के रूप में लागू करते हुए दस्तावेज़ लोड करें और परिणाम सत्यापित करें।
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

## निष्कर्ष

इस गाइड में, हमने जावा के लिए Aspose.Words का उपयोग करके टेक्स्ट फ़ाइलों को लोड करने, सूचियों का पता लगाने, रिक्त स्थान को संभालने और टेक्स्ट दिशा को नियंत्रित करने के तरीकों के बारे में पता लगाया है। ये तकनीकें आपको अपने जावा अनुप्रयोगों में टेक्स्ट दस्तावेज़ों को प्रभावी ढंग से हेरफेर करने की अनुमति देती हैं।

## अक्सर पूछे जाने वाले प्रश्न

### Java के लिए Aspose.Words क्या है?

Aspose.Words for Java एक शक्तिशाली दस्तावेज़ प्रसंस्करण लाइब्रेरी है जो डेवलपर्स को जावा अनुप्रयोगों में प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, हेरफेर करने और परिवर्तित करने की अनुमति देती है। यह टेक्स्ट, टेबल, इमेज और अन्य दस्तावेज़ तत्वों के साथ काम करने के लिए कई तरह की सुविधाएँ प्रदान करता है।

### मैं Java के लिए Aspose.Words के साथ कैसे शुरुआत कर सकता हूँ?

Java के लिए Aspose.Words के साथ आरंभ करने के लिए, इन चरणों का पालन करें:
1. Aspose.Words for Java लाइब्रेरी को डाउनलोड और इंस्टॉल करें।
2. दस्तावेज़ देखें [Aspose.Words for Java API संदर्भ](https://reference.aspose.com/words/java/) विस्तृत जानकारी और उदाहरण के लिए.
3. लाइब्रेरी का प्रभावी ढंग से उपयोग करने का तरीका जानने के लिए नमूना कोड और ट्यूटोरियल देखें।

### मैं Java के लिए Aspose.Words का उपयोग करके टेक्स्ट दस्तावेज़ कैसे लोड करूं?

Java के लिए Aspose.Words का उपयोग करके एक टेक्स्ट दस्तावेज़ लोड करने के लिए, आप इसका उपयोग कर सकते हैं `TxtLoadOptions` वर्ग और `Document` क्लास। सुनिश्चित करें कि आप आवश्यकतानुसार रिक्त स्थान और पाठ दिशा को संभालने के लिए उचित विकल्प निर्दिष्ट करते हैं। विस्तृत उदाहरण के लिए इस लेख में चरण-दर-चरण मार्गदर्शिका देखें।

### क्या मैं लोड किए गए टेक्स्ट दस्तावेज़ को अन्य प्रारूपों में परिवर्तित कर सकता हूँ?

हां, Aspose.Words for Java आपको लोड किए गए टेक्स्ट डॉक्यूमेंट को विभिन्न फॉर्मेट में बदलने की अनुमति देता है, जिसमें DOCX, PDF और बहुत कुछ शामिल है। आप इसका उपयोग कर सकते हैं `Document` रूपांतरण करने के लिए क्लास का उपयोग करें। विशिष्ट रूपांतरण उदाहरणों के लिए दस्तावेज़ देखें।

### मैं लोड किए गए टेक्स्ट दस्तावेज़ों में रिक्त स्थानों को कैसे संभालूँ?

आप लोड किए गए टेक्स्ट दस्तावेज़ों में अग्रणी और अंतिम रिक्त स्थानों को कैसे प्रबंधित किया जाए, इसे नियंत्रित कर सकते हैं `TxtLoadOptions`. जैसे विकल्प `TxtLeadingSpacesOptions` और `TxtTrailingSpacesOptions` आपको आवश्यकतानुसार रिक्त स्थान को ट्रिम या संरक्षित करने की अनुमति देता है। उदाहरण के लिए इस गाइड में "रिक्त स्थान को संभालने के विकल्प" अनुभाग देखें।

### Java के लिए Aspose.Words में पाठ दिशा का क्या महत्व है?

मिश्रित लिपियों या भाषाओं, जैसे हिब्रू या अरबी वाले दस्तावेज़ों के लिए पाठ दिशा आवश्यक है। जावा के लिए Aspose.Words पाठ दिशा निर्दिष्ट करने के लिए विकल्प प्रदान करता है, जिससे इन भाषाओं में पाठ का उचित प्रतिपादन और स्वरूपण सुनिश्चित होता है। इस गाइड में "टेक्स्ट दिशा नियंत्रित करना" अनुभाग दर्शाता है कि पाठ दिशा कैसे सेट करें।

### मैं Java के लिए Aspose.Words के लिए अधिक संसाधन और समर्थन कहां पा सकता हूं?

अतिरिक्त संसाधनों, दस्तावेज़ीकरण और सहायता के लिए, यहां जाएं [जावा दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/java/)आप Aspose.Words सामुदायिक मंचों में भी भाग ले सकते हैं या विशिष्ट मुद्दों या पूछताछ के लिए सहायता के लिए Aspose समर्थन से संपर्क कर सकते हैं।

### क्या Aspose.Words for Java व्यावसायिक परियोजनाओं के लिए उपयुक्त है?

हां, Aspose.Words for Java व्यक्तिगत और व्यावसायिक दोनों तरह की परियोजनाओं के लिए उपयुक्त है। यह विभिन्न उपयोग परिदृश्यों को समायोजित करने के लिए लाइसेंसिंग विकल्प प्रदान करता है। अपनी परियोजना के लिए उपयुक्त लाइसेंस चुनने के लिए Aspose वेबसाइट पर लाइसेंसिंग शर्तों और मूल्य निर्धारण की समीक्षा करना सुनिश्चित करें।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}