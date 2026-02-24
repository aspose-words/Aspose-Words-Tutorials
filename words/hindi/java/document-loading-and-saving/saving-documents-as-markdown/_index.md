---
date: 2026-02-24
description: Aspose.Words for Java का उपयोग करके वर्ड को मार्कडाउन में कैसे परिवर्तित
  करें, सीखें। यह गाइड टेबल अलाइनमेंट, इमेज हैंडलिंग, और दस्तावेज़ को मार्कडाउन के
  रूप में सहेजने को कवर करता है।
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java के साथ Word को Markdown में बदलें
url: /hi/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ Word को Markdown में बदलें

## Aspose.Words for Java के साथ Word को Markdown में बदलने का परिचय

इस चरण‑दर‑चरण ट्यूटोरियल में आप **Word को Markdown में कैसे बदलें** यह सीखेंगे, जो शक्तिशाली Aspose.Words for Java API का उपयोग करता है। Markdown एक हल्की मार्कअप भाषा है जिस पर कई डेवलपर और कंटेंट प्लेटफ़ॉर्म साफ़, पढ़ने योग्य दस्तावेज़ीकरण के लिए निर्भर करते हैं। इस गाइड के अंत तक आप किसी भी `.docx` फ़ाइल को ले सकेंगे, तालिकाएँ, चित्र और फ़ॉर्मेटिंग को संरक्षित रखते हुए, और उसे एक `.md` फ़ाइल के रूप में निर्यात कर सकेंगे जो स्थैतिक‑साइट जेनरेटर, GitHub READMEs, या किसी भी markdown‑अनुकूल कार्यप्रवाह के लिए तैयार है।

## त्वरित उत्तर
- **मुझे कौन सी लाइब्रेरी चाहिए?** Aspose.Words for Java (`aspose-words.jar`)।
- **क्या मैं तालिका संरेखण को कस्टमाइज़ कर सकता हूँ?** हाँ – `MarkdownSaveOptions` में `TableContentAlignment` का उपयोग करें।
- **चित्रों को कैसे संभाला जाता है?** `setImagesFolder()` के साथ एक इमेज फ़ोल्डर सेट करें; लाइब्रेरी सापेक्ष लिंक बनाती है।
- **उत्पादन के लिए लाइसेंस चाहिए?** गैर‑ट्रायल उपयोग के लिए एक व्यावसायिक लाइसेंस आवश्यक है।
- **क्या यह Java 17 के साथ संगत है?** हाँ, लाइब्रेरी Java 8 और उसके बाद के संस्करणों को सपोर्ट करती है।

## Word को Markdown में बदलना क्या है?

Word को Markdown में बदलना मतलब Microsoft Word दस्तावेज़ के समृद्ध फ़ॉर्मेटिंग को साधारण‑पाठ markdown सिंटैक्स में अनुवादित करना है। यह प्रक्रिया शीर्षक, सूचियाँ, तालिकाएँ और चित्र संदर्भों को बरकरार रखती है जबकि बाइनरी फ़ॉर्मेटिंग को हटाती है, जिससे सामग्री पोर्टेबल और संस्करण‑नियंत्रण‑अनुकूल बनती है।

## Aspose.Words for Java का उपयोग करके दस्तावेज़ को markdown के रूप में सहेजने के कारण

* **पूर्ण सटीकता** – तालिकाएँ, चित्र, और जटिल लेआउट संरक्षित रहते हैं।
* **सूक्ष्म नियंत्रण** – आप तालिका संरेखण, चित्र पथ, और अधिक को कस्टमाइज़ कर सकते हैं।
* **कोई बाहरी निर्भरताएँ नहीं** – लाइब्रेरी बॉक्स से बाहर काम करती है और Office स्थापित होने की आवश्यकता नहीं होती।
* **क्रॉस‑प्लेटफ़ॉर्म** – Windows, Linux, और macOS पर किसी भी Java रनटाइम के साथ काम करती है।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- आपके सिस्टम पर स्थापित Java Development Kit (JDK)।
- Aspose.Words for Java लाइब्रेरी। आप इसे [here](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं।

## चरण‑दर‑चरण गाइड

### चरण 1: वह Word दस्तावेज़ बनाएँ जिसे बदला जाएगा

पहले, हम एक सरल Word दस्तावेज़ बनाते हैं जिसमें दो‑सेल वाली तालिका होती है। यह उदाहरण दर्शाता है कि तालिका कोशिकाओं के भीतर पैराग्राफ संरेखण को बाद में **दस्तावेज़ को markdown के रूप में सहेजते** समय कैसे सम्मानित किया जाता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

### चरण 2: तालिका सामग्री संरेखण को कस्टमाइज़ करें

Aspose.Words for Java आपको उत्पन्न markdown में तालिका कोशिकाओं के संरेखण को नियंत्रित करने की अनुमति देता है। `TableContentAlignment` प्रॉपर्टी का उपयोग करके **तालिका संरेखण को कस्टमाइज़** करें – बाएँ, दाएँ, केंद्र, या प्रत्येक कॉलम के पहले पैराग्राफ के आधार पर लाइब्रेरी को स्वचालित रूप से निर्णय लेने दें।

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

इस सेटिंग को टॉगल करके आप **word तालिकाओं को markdown में निर्यात** कर सकते हैं, वह सटीक संरेखण जिसके आप नीचे के रेंडरिंग इंजन में आवश्यकता रखते हैं।

### चरण 3: परिवर्तन के दौरान चित्रों को संभालें

जब आपके स्रोत Word दस्तावेज़ में चित्र होते हैं, तो आपको Aspose.Words को बताना होगा कि निर्यातित चित्र फ़ाइलें कहाँ रखी जाएँ। `MarkdownSaveOptions` पर `setImagesFolder` मेथड वह फ़ोल्डर निर्धारित करता है जो चित्र एसेट्स को रखेगा, और markdown उन फ़ाइलों के सापेक्ष लिंक शामिल करेगा।

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"` को अपने स्रोत फ़ाइल के पथ से बदलें और `"images_folder/"` को चित्रों के इच्छित आउटपुट फ़ोल्डर से बदलें।

### सभी परिदृश्यों के लिए पूर्ण स्रोत कोड

नीचे एक समेकित उदाहरण है जो दिखाता है कि कैसे **स्वचालित तालिका संरेखण**, **संरेखण को कस्टमाइज़**, और **एक चित्र फ़ोल्डर सेट** एक ही मेथड में किया जाता है। यह स्निपेट मूल ट्यूटोरियल कोड को प्रतिबिंबित करता है और बिना बदलाव के काम करता है।

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## सामान्य समस्याएँ और समाधान

| समस्या | कारण | समाधान |
|-------|--------|-----|
| चित्र टूटे हुए लिंक के रूप में दिखते हैं | `setImagesFolder` सेट नहीं है या फ़ोल्डर पथ गलत है | फ़ोल्डर पथ सही है और फ़ोल्डर लिखने योग्य है, यह सुनिश्चित करें |
| तालिका संरेखण गलत दिख रहा है | गलत `TableContentAlignment` मान | `TableContentAlignment.AUTO` का उपयोग करें ताकि पहला पैराग्राफ निर्णय ले, या स्पष्ट रूप से LEFT/RIGHT/CENTER सेट करें |
| आउटपुट फ़ाइल खाली है | `doc.save()` में Save Options पास नहीं किए गए | `save` मेथड में `MarkdownSaveOptions` इंस्टेंस पास करना सुनिश्चित करें |
| असमर्थित Word फीचर (जैसे, SmartArt) | Markdown कुछ जटिल ऑब्जेक्ट्स को दर्शा नहीं सकता | उन तत्वों को चित्रों में बदलें या स्रोत दस्तावेज़ को सरल बनाएं |

## अक्सर पूछे जाने वाले प्रश्न

**Q: Aspose.Words for Java को कैसे इंस्टॉल करूँ?**  
A: Aspose.Words for Java को अपने Java प्रोजेक्ट में लाइब्रेरी शामिल करके इंस्टॉल किया जा सकता है। आप लाइब्रेरी को [here](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं और दस्तावेज़ीकरण में प्रदान किए गए इंस्टॉलेशन निर्देशों का पालन कर सकते हैं।

**Q: क्या मैं जटिल Word दस्तावेज़ों को तालिकाओं और चित्रों के साथ Markdown में बदल सकता हूँ?**  
A: हाँ, Aspose.Words for Java जटिल Word दस्तावेज़ों को तालिकाओं, चित्रों और विभिन्न फ़ॉर्मेटिंग तत्वों के साथ Markdown में बदलने का समर्थन करता है। आप अपने दस्तावेज़ की जटिलता के अनुसार Markdown आउटपुट को कस्टमाइज़ कर सकते हैं।

**Q: मैं Markdown फ़ाइलों में चित्रों को कैसे संभालूँ?**  
A: Markdown फ़ाइलों में चित्र शामिल करने के लिए `MarkdownSaveOptions` में `setImagesFolder` मेथड का उपयोग करके चित्र फ़ोल्डर पथ सेट करें। सुनिश्चित करें कि चित्र फ़ाइलें निर्दिष्ट फ़ोल्डर में संग्रहीत हैं, और Aspose.Words for Java स्वचालित रूप से चित्र संदर्भों को संभालेगा।

**Q: क्या Aspose.Words for Java का ट्रायल संस्करण उपलब्ध है?**  
A: हाँ, आप Aspose वेबसाइट से Aspose.Words for Java का ट्रायल संस्करण प्राप्त कर सकते हैं। ट्रायल संस्करण आपको लाइसेंस खरीदने से पहले लाइब्रेरी की क्षमताओं का मूल्यांकन करने की अनुमति देता है।

**Q: अधिक उदाहरण और दस्तावेज़ीकरण कहाँ मिल सकते हैं?**  
A: अधिक उदाहरण, दस्तावेज़ीकरण, और Aspose.Words for Java पर विस्तृत जानकारी के लिए कृपया [documentation](https://reference.aspose.com/words/java/) देखें।

## निष्कर्ष

इस गाइड में हमने Aspose.Words for Java का उपयोग करके **Word को Markdown में बदलने** के सभी आवश्यक पहलुओं को कवर किया: स्रोत दस्तावेज़ बनाना, **तालिका संरेखण को कस्टमाइज़** करना, और उचित फ़ोल्डर कॉन्फ़िगरेशन के साथ चित्रों को संभालना। इन तकनीकों के साथ आप Word सामग्री को विश्वसनीय रूप से Markdown में निर्यात कर सकते हैं, चाहे वह ब्लॉग, दस्तावेज़ीकरण साइट, या कोई भी प्लेटफ़ॉर्म हो जो Markdown को उपभोग करता है।

---

**अंतिम अद्यतन:** 2026-02-24  
**परीक्षण किया गया:** Aspose.Words for Java 24.12 (लेखन के समय नवीनतम)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}