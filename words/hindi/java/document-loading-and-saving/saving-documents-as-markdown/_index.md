---
date: 2025-12-22
description: Aspose.Words for Java के साथ Word दस्तावेज़ों को Markdown में बदलकर मार्कडाउन
  निर्यात करना सीखें। यह चरण-दर-चरण गाइड तालिका संरेखण, छवि संभालना और अधिक को कवर
  करता है।
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java के साथ मार्कडाउन निर्यात कैसे करें
url: /hi/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ Markdown निर्यात कैसे करें

## Aspose.Words for Java में Markdown निर्यात का परिचय

इस चरण‑दर‑चरण ट्यूटोरियल में, **आप सीखेंगे कि Word दस्तावेज़ों से Markdown कैसे निर्यात किया जाए** Aspose.Words for Java का उपयोग करके। Markdown एक हल्की मार्कअप भाषा है जो दस्तावेज़ीकरण, स्थैतिक साइट जेनरेटर और कई प्रकाशन प्लेटफ़ॉर्म के लिए उपयुक्त है। इस गाइड के अंत तक आप **Word को Markdown में बदलना**, तालिका संरेखण को अनुकूलित करना, और **Markdown में छवियों को संभालना** आसानी से कर पाएँगे।

## त्वरित उत्तर
- **Markdown के रूप में सहेजने के लिए प्रमुख क्लास कौन सी है?** `MarkdownSaveOptions`
- **क्या छवियों को स्वचालित रूप से एम्बेड किया जा सकता है?** हाँ – `setImagesFolder` के माध्यम से छवि फ़ोल्डर सेट करें।
- **मैं तालिका संरेखण को कैसे नियंत्रित करूँ?** `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO) का उपयोग करें।
- **न्यूनतम आवश्यकताएँ क्या हैं?** JDK 8+ और Aspose.Words for Java लाइब्रेरी।
- **क्या ट्रायल संस्करण उपलब्ध है?** हाँ, इसे Aspose वेबसाइट से डाउनलोड करें।

## “Markdown निर्यात कैसे करें” क्या है?
Markdown निर्यात का अर्थ है एक समृद्ध‑पाठ Word दस्तावेज़ (`.docx`) को एक साधारण‑पाठ `.md` फ़ाइल में बदलना, जिसमें शीर्षक, तालिकाएँ और छवियाँ Markdown सिंटैक्स में संरक्षित रहती हैं।

## छवियों के साथ docx को बदलने के लिए Aspose.Words for Java क्यों उपयोग करें?
Aspose.Words जटिल लेआउट, एम्बेडेड चित्र और तालिका संरचनाओं को बिना गुणवत्ता खोए संभालता है। यह आपको Markdown आउटपुट पर सूक्ष्म नियंत्रण भी देता है, जैसे तालिका संरेखण और छवि फ़ोल्डर प्रबंधन।

## पूर्वापेक्षाएँ

- आपके सिस्टम पर Java Development Kit (JDK) स्थापित हो।
- Aspose.Words for Java लाइब्रेरी। आप इसे [यहाँ](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं।

## चरण 1: एक साधारण Word दस्तावेज़ बनाएँ

पहले, हम एक छोटा दस्तावेज़ बनाएँगे जिसमें एक तालिका होगी। इससे हम बाद में **तालिका संरेखण को अनुकूलित** कर सकेंगे।

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

ऊपर के स्निपेट में हमने किया:

1. एक नया `Document` बनाया।
2. `DocumentBuilder` का उपयोग करके दो‑सेल वाली तालिका डाली।
3. प्रत्येक सेल के भीतर **दाएँ** और **केंद्र** पैराग्राफ संरेखण लागू किया।
4. `MarkdownSaveOptions` का उपयोग करके फ़ाइल को Markdown के रूप में सहेजा।

## चरण 2: तालिका सामग्री संरेखण को अनुकूलित करें

Aspose.Words आपको अंतिम Markdown में तालिका कोशिकाओं के रेंडरिंग को निर्धारित करने की सुविधा देता है। आप बाएँ, दाएँ, केंद्र संरेखण को मजबूर कर सकते हैं, या प्रत्येक कॉलम के पहले पैराग्राफ के आधार पर लाइब्रेरी को स्वचालित रूप से निर्णय लेने दे सकते हैं।

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

`TableContentAlignment` प्रॉपर्टी को बदलकर आप **Markdown आउटपुट के लिए तालिका संरेखण** को अनुकूलित कर सकते हैं।

## चरण 3: Markdown निर्यात करते समय छवियों को संभालें

जब दस्तावेज़ में चित्र होते हैं, तो आप चाहते हैं कि ये छवियाँ उत्पन्न `.md` फ़ाइल में सही ढंग से दिखें। वह फ़ोल्डर सेट करें जहाँ Aspose.Words निकाली गई छवियों को रखेगा।

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"` को अपने स्रोत फ़ाइल के पथ से बदलें और `"images_folder/"` को उस स्थान से जहाँ आप छवियों को संग्रहित करना चाहते हैं। परिणामी Markdown में ऐसे छवि लिंक होंगे जो इस फ़ोल्डर की ओर इशारा करेंगे, जिससे आप **Markdown में छवियों को सहजता से संभाल** सकेंगे।

## Aspose.Words for Java में दस्तावेज़ों को Markdown के रूप में सहेजने के लिए पूर्ण स्रोत कोड

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

| समस्या | समाधान |
|--------|--------|
| `.md` फ़ाइल में छवियाँ नहीं दिख रही हैं | सुनिश्चित करें कि `setImagesFolder` एक लिखने योग्य निर्देशिका की ओर इशारा कर रहा है और फ़ोल्डर को उत्पन्न Markdown में सही ढंग से संदर्भित किया गया है। |
| तालिका संरेखण गलत दिख रहा है | `TableContentAlignment.AUTO` का उपयोग करें ताकि Aspose.Words प्रत्येक कॉलम के पहले पैराग्राफ के आधार पर सर्वोत्तम संरेखण निर्धारित कर सके। |
| आउटपुट फ़ाइल खाली है | `Document` ऑब्जेक्ट में वास्तव में सामग्री है या नहीं, यह जाँचें, फिर `save` कॉल करें। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: Aspose.Words for Java कैसे स्थापित करें?**  
**उत्तर:** Aspose.Words for Java को अपने Java प्रोजेक्ट में लाइब्रेरी शामिल करके स्थापित किया जा सकता है। आप लाइब्रेरी को [यहाँ](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं और दस्तावेज़ीकरण में दी गई स्थापना निर्देशों का पालन कर सकते हैं।

**प्रश्न: क्या मैं जटिल Word दस्तावेज़ों को तालिकाओं और छवियों के साथ Markdown में बदल सकता हूँ?**  
**उत्तर:** हाँ, Aspose.Words for Java जटिल Word दस्तावेज़ों को तालिकाओं, छवियों और विभिन्न फ़ॉर्मेटिंग तत्वों के साथ Markdown में बदलने का समर्थन करता है। आप अपने दस्तावेज़ की जटिलता के अनुसार Markdown आउटपुट को अनुकूलित कर सकते हैं।

**प्रश्न: मैं Markdown फ़ाइलों में छवियों को कैसे संभालूँ?**  
**उत्तर:** `MarkdownSaveOptions` में `setImagesFolder` मेथड का उपयोग करके छवि फ़ोल्डर पथ सेट करें। सुनिश्चित करें कि छवि फ़ाइलें निर्दिष्ट फ़ोल्डर में संग्रहीत हैं; Aspose.Words उपयुक्त Markdown छवि लिंक उत्पन्न करेगा।

**प्रश्न: क्या Aspose.Words for Java का ट्रायल संस्करण उपलब्ध है?**  
**उत्तर:** हाँ, आप Aspose वेबसाइट से Aspose.Words for Java का ट्रायल संस्करण प्राप्त कर सकते हैं। ट्रायल संस्करण आपको लाइब्रेरी की क्षमताओं का मूल्यांकन करने की अनुमति देता है, इससे पहले कि आप लाइसेंस खरीदें।

**प्रश्न: अधिक उदाहरण और दस्तावेज़ीकरण कहाँ मिल सकता है?**  
**उत्तर:** अधिक उदाहरण, दस्तावेज़ीकरण और विस्तृत जानकारी के लिए कृपया [दस्तावेज़ीकरण](https://reference.aspose.com/words/java/) देखें।

---

**अंतिम अपडेट:** 2025-12-22  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12 (लेखन समय पर नवीनतम)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}