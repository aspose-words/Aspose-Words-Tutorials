---
"description": "जावा के लिए Aspose.Words के साथ Word दस्तावेज़ों को Markdown में बदलने का तरीका जानें। यह चरण-दर-चरण मार्गदर्शिका तालिका संरेखण, छवि प्रबंधन, और बहुत कुछ को कवर करती है।"
"linktitle": "दस्तावेज़ों को मार्कडाउन के रूप में सहेजना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में मार्कडाउन के रूप में दस्तावेज़ सहेजना"
"url": "/hi/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में मार्कडाउन के रूप में दस्तावेज़ सहेजना


## जावा के लिए Aspose.Words में मार्कडाउन के रूप में दस्तावेज़ों को सहेजने का परिचय

इस चरण-दर-चरण मार्गदर्शिका में, हम प्रदर्शित करेंगे कि Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों को Markdown के रूप में कैसे सहेजा जाए। Markdown एक हल्की मार्कअप भाषा है जिसका उपयोग आमतौर पर टेक्स्ट दस्तावेज़ों को फ़ॉर्मेट करने के लिए किया जाता है। Java के लिए Aspose.Words के साथ, आप आसानी से अपने Word दस्तावेज़ों को Markdown फ़ॉर्मेट में बदल सकते हैं। हम Markdown फ़ाइलों को सहेजने के विभिन्न पहलुओं को कवर करेंगे, जिसमें टेबल सामग्री संरेखण और छवियों को संभालना शामिल है।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:

- आपके सिस्टम पर जावा डेवलपमेंट किट (JDK) स्थापित है।
- Aspose.Words for Java लाइब्रेरी। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

## चरण 1: वर्ड दस्तावेज़ बनाना

आइए एक वर्ड डॉक्यूमेंट बनाकर शुरू करें जिसे हम बाद में मार्कडाउन फॉर्मेट में बदल देंगे। आप इस डॉक्यूमेंट को अपनी ज़रूरतों के हिसाब से कस्टमाइज़ कर सकते हैं।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// दो कक्षों वाली तालिका सम्मिलित करें
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// दस्तावेज़ को मार्कडाउन के रूप में सहेजें
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

इस उदाहरण में, हम दो कक्षों वाली एक सरल तालिका बनाते हैं और इन कक्षों के भीतर पैराग्राफ़ का संरेखण सेट करते हैं। फिर, हम दस्तावेज़ को मार्कडाउन के रूप में सहेजते हैं `MarkdownSaveOptions`.

## चरण 2: तालिका सामग्री संरेखण अनुकूलित करें

जावा के लिए Aspose.Words आपको मार्कडाउन के रूप में सहेजते समय तालिका सामग्री के संरेखण को अनुकूलित करने की अनुमति देता है। आप तालिका सामग्री को बाएं, दाएं, केंद्र में संरेखित कर सकते हैं, या इसे प्रत्येक तालिका कॉलम में पहले पैराग्राफ के आधार पर स्वचालित रूप से निर्धारित कर सकते हैं।

तालिका सामग्री संरेखण को अनुकूलित करने का तरीका यहां दिया गया है:

```java
// तालिका सामग्री संरेखण को बाईं ओर सेट करें
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// तालिका सामग्री संरेखण को दाईं ओर सेट करें
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// तालिका सामग्री संरेखण को केंद्र में सेट करें
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// तालिका सामग्री संरेखण को स्वचालित पर सेट करें (पहले पैराग्राफ द्वारा निर्धारित)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

परिवर्तन करके `TableContentAlignment` प्रॉपर्टी का उपयोग करके, आप नियंत्रित कर सकते हैं कि मार्कडाउन में कनवर्ट करते समय तालिकाओं के अंदर की सामग्री कैसे संरेखित की जाए।

## चरण 3: छवियों को संभालना

अपने मार्कडाउन दस्तावेज़ में छवियों को शामिल करने के लिए, आपको उस फ़ोल्डर को निर्दिष्ट करना होगा जहाँ छवियाँ स्थित हैं। Aspose.Words for Java आपको छवियों फ़ोल्डर को सेट करने की अनुमति देता है `MarkdownSaveOptions`.

छवियाँ फ़ोल्डर सेट करने और दस्तावेज़ को छवियों के साथ सहेजने का तरीका यहां दिया गया है:

```java
// छवियाँ युक्त दस्तावेज़ लोड करें
Document doc = new Document("document_with_images.docx");

// छवियाँ फ़ोल्डर पथ सेट करें
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// दस्तावेज़ को छवियों के साथ सहेजें
doc.save("document_with_images.md", saveOptions);
```

प्रतिस्थापित करना सुनिश्चित करें `"document_with_images.docx"` आपके Word दस्तावेज़ के पथ के साथ जिसमें चित्र और `"images_folder/"` उस फ़ोल्डर का वास्तविक पथ जहाँ आपकी छवियाँ संग्रहीत हैं।

## जावा के लिए Aspose.Words में मार्कडाउन के रूप में दस्तावेज़ों को सहेजने के लिए पूर्ण स्रोत कोड

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// तालिका के अंदर सभी पैराग्राफों को संरेखित करता है।
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// इस मामले में संरेखण संबंधित तालिका कॉलम के पहले पैराग्राफ से लिया जाएगा।
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## निष्कर्ष

इस गाइड में, हमने जावा के लिए Aspose.Words का उपयोग करके मार्कडाउन के रूप में दस्तावेज़ों को सहेजने का तरीका खोजा है। हमने एक वर्ड दस्तावेज़ के निर्माण, तालिका सामग्री संरेखण को अनुकूलित करने और मार्कडाउन फ़ाइलों में छवियों को संभालने के बारे में बताया। अब आप अपने वर्ड दस्तावेज़ों को मार्कडाउन प्रारूप में कुशलतापूर्वक परिवर्तित कर सकते हैं, जिससे वे विभिन्न प्रकाशन प्लेटफ़ॉर्म और दस्तावेज़ीकरण आवश्यकताओं के लिए उपयुक्त बन जाते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Java के लिए Aspose.Words कैसे स्थापित करूं?

Aspose.Words for Java को आपके Java प्रोजेक्ट में लाइब्रेरी शामिल करके इंस्टॉल किया जा सकता है। आप लाइब्रेरी को यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/) और दस्तावेज़ में दिए गए स्थापना निर्देशों का पालन करें।

### क्या मैं तालिकाओं और छवियों वाले जटिल वर्ड दस्तावेज़ों को मार्कडाउन में परिवर्तित कर सकता हूँ?

हां, Aspose.Words for Java जटिल Word दस्तावेज़ों को तालिकाओं, छवियों और विभिन्न स्वरूपण तत्वों के साथ Markdown में बदलने का समर्थन करता है। आप अपने दस्तावेज़ की जटिलता के अनुसार Markdown आउटपुट को अनुकूलित कर सकते हैं।

### मैं मार्कडाउन फ़ाइलों में छवियों को कैसे संभाल सकता हूँ?

मार्कडाउन फ़ाइलों में छवियाँ शामिल करने के लिए, छवियाँ फ़ोल्डर पथ को सेट करने के लिए निम्न का उपयोग करें: `setImagesFolder` विधि में `MarkdownSaveOptions`सुनिश्चित करें कि छवि फ़ाइलें निर्दिष्ट फ़ोल्डर में संग्रहीत हैं, और Aspose.Words for Java छवि संदर्भों को तदनुसार संभालेगा।

### क्या Java के लिए Aspose.Words का कोई परीक्षण संस्करण उपलब्ध है?

हां, आप Aspose.Words for Java का ट्रायल संस्करण Aspose वेबसाइट से प्राप्त कर सकते हैं। ट्रायल संस्करण आपको लाइसेंस खरीदने से पहले लाइब्रेरी की क्षमताओं का मूल्यांकन करने की अनुमति देता है।

### मैं और अधिक उदाहरण और दस्तावेज कहां पा सकता हूं?

Java के लिए Aspose.Words पर अधिक उदाहरण, दस्तावेज़ीकरण और विस्तृत जानकारी के लिए, कृपया देखें [प्रलेखन](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}