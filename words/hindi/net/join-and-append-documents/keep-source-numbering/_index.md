---
"description": ".NET के लिए Aspose.Words का उपयोग करके फ़ॉर्मेटिंग को संरक्षित करते हुए दस्तावेज़ों को आयात करना सीखें। कोड उदाहरणों के साथ चरण-दर-चरण मार्गदर्शिका।"
"linktitle": "स्रोत क्रमांकन रखें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "स्रोत क्रमांकन रखें"
"url": "/hi/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# स्रोत क्रमांकन रखें

## परिचय

.NET के लिए Aspose.Words के साथ काम करते समय, स्वरूपण को संरक्षित करते हुए दस्तावेज़ों को एक स्रोत से दूसरे में आयात करना कुशलतापूर्वक संभाला जा सकता है `NodeImporter` यह ट्यूटोरियल आपको चरण-दर-चरण प्रक्रिया के माध्यम से मार्गदर्शन करेगा।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके मशीन पर Visual Studio स्थापित है.
- Aspose.Words for .NET इंस्टॉल है। यदि नहीं, तो इसे यहाँ से डाउनलोड करें [यहाँ](https://releases.aspose.com/words/net/).
- C# और .NET प्रोग्रामिंग का बुनियादी ज्ञान।

## नामस्थान आयात करें

सबसे पहले, अपने प्रोजेक्ट में आवश्यक नामस्थान शामिल करें:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## चरण 1: अपना प्रोजेक्ट सेट करें

Visual Studio में एक नया C# प्रोजेक्ट बनाकर आरंभ करें और NuGet पैकेज मैनेजर के माध्यम से Aspose.Words स्थापित करें।

## चरण 2: दस्तावेज़ आरंभ करें
स्रोत के उदाहरण बनाएं (`srcDoc`) और गंतव्य (`dstDoc`) दस्तावेज़.

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## चरण 3: आयात विकल्प कॉन्फ़िगर करें
क्रमांकित पैराग्राफ़ सहित स्रोत स्वरूपण बनाए रखने के लिए आयात विकल्प सेट करें।

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## चरण 4: पैराग्राफ़ आयात करें
स्रोत दस्तावेज़ में पैराग्राफ़ों को पुनरावृत्त करें और उन्हें गंतव्य दस्तावेज़ में आयात करें।

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## चरण 5: दस्तावेज़ सहेजें
मर्ज किए गए दस्तावेज़ को अपने इच्छित स्थान पर सहेजें.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## निष्कर्ष

निष्कर्ष में, स्वरूपण को संरक्षित करते हुए दस्तावेज़ों को आयात करने के लिए .NET के लिए Aspose.Words का उपयोग करना सरल है `NodeImporter` यह विधि सुनिश्चित करती है कि आपके दस्तावेज़ अपनी मूल उपस्थिति और संरचना को निर्बाध रूप से बनाए रखें।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं भिन्न स्वरूपण शैलियों वाले दस्तावेज़ आयात कर सकता हूँ?
हां `NodeImporter` क्लास विभिन्न स्वरूपण शैलियों के साथ दस्तावेज़ों को आयात करने का समर्थन करता है।

### यदि मेरे दस्तावेज़ों में जटिल तालिकाएँ और चित्र हों तो क्या होगा?
.NET के लिए Aspose.Words आयात संचालन के दौरान तालिकाओं और छवियों जैसी जटिल संरचनाओं को संभालता है।

### क्या Aspose.Words .NET के सभी संस्करणों के साथ संगत है?
Aspose.Words निर्बाध एकीकरण के लिए .NET Framework और .NET Core संस्करणों का समर्थन करता है।

### मैं दस्तावेज़ आयात के दौरान त्रुटियों को कैसे संभाल सकता हूँ?
आयात प्रक्रिया के दौरान होने वाले अपवादों को संभालने के लिए try-catch ब्लॉक का उपयोग करें।

### मैं .NET के लिए Aspose.Words पर अधिक विस्तृत दस्तावेज़ कहां पा सकता हूं?
दौरा करना [प्रलेखन](https://reference.aspose.com/words/net/) व्यापक गाइड और एपीआई संदर्भ के लिए.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}