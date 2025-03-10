---
title: वर्ड दस्तावेज़ में पैराग्राफ़ डालें
linktitle: वर्ड दस्तावेज़ में पैराग्राफ़ डालें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में पैराग्राफ़ सम्मिलित करना सीखें। दस्तावेज़ों में सहज हेरफेर के लिए हमारे विस्तृत ट्यूटोरियल का पालन करें।
weight: 10
url: /hi/net/add-content-using-documentbuilder/insert-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड दस्तावेज़ में पैराग्राफ़ डालें

## परिचय

Word दस्तावेज़ों में प्रोग्रामेटिक रूप से पैराग्राफ़ सम्मिलित करने के लिए .NET के लिए Aspose.Words का उपयोग करने पर हमारी विस्तृत मार्गदर्शिका में आपका स्वागत है। चाहे आप एक अनुभवी डेवलपर हों या .NET में दस्तावेज़ हेरफेर के साथ अभी शुरुआत कर रहे हों, यह ट्यूटोरियल आपको स्पष्ट, चरण-दर-चरण निर्देशों और उदाहरणों के साथ प्रक्रिया के माध्यम से ले जाएगा।

## आवश्यक शर्तें

ट्यूटोरियल में शामिल होने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- C# प्रोग्रामिंग और .NET फ्रेमवर्क का बुनियादी ज्ञान।
- आपके मशीन पर Visual Studio स्थापित है.
-  Aspose.Words for .NET लाइब्रेरी स्थापित है। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).

## नामस्थान आयात करें

सबसे पहले, आरंभ करने के लिए आवश्यक नामस्थानों को आयात करें:
```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using System.Drawing;
```

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

 अपना दस्तावेज़ सेट अप करके और प्रारंभ करके आरंभ करें`DocumentBuilder` वस्तु।
```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: फ़ॉन्ट और पैराग्राफ़ को फ़ॉर्मेट करें

इसके बाद, नए पैराग्राफ के लिए फ़ॉन्ट और पैराग्राफ फ़ॉर्मेटिंग को अनुकूलित करें।
```csharp
Font font = builder.Font;
font.Size = 16;
font.Bold = true;
font.Color = Color.Blue;
font.Name = "Arial";
font.Underline = Underline.Dash;

ParagraphFormat paragraphFormat = builder.ParagraphFormat;
paragraphFormat.FirstLineIndent = 8;
paragraphFormat.Alignment = ParagraphAlignment.Justify;
paragraphFormat.KeepTogether = true;
```

## चरण 3: पैराग्राफ़ डालें

 अब, का उपयोग करके अपनी इच्छित सामग्री जोड़ें`WriteLn` की विधि`DocumentBuilder`.
```csharp
builder.Writeln("A whole paragraph.");
```

## चरण 4: दस्तावेज़ सहेजें

अंत में, संशोधित दस्तावेज़ को अपने इच्छित स्थान पर सहेजें।
```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.InsertParagraph.docx");
```

## निष्कर्ष

बधाई हो! आपने .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में एक स्वरूपित पैराग्राफ सफलतापूर्वक डाला है। यह प्रक्रिया आपको अपने एप्लिकेशन की ज़रूरतों के अनुरूप समृद्ध सामग्री को गतिशील रूप से उत्पन्न करने की अनुमति देती है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं .NET कोर अनुप्रयोगों के साथ .NET के लिए Aspose.Words का उपयोग कर सकता हूं?
हां, .NET के लिए Aspose.Words .NET फ्रेमवर्क के साथ .NET कोर अनुप्रयोगों का समर्थन करता है।

### मैं .NET के लिए Aspose.Words हेतु अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### क्या Aspose.Words for .NET Microsoft Word संस्करणों के साथ संगत है?
हां, .NET के लिए Aspose.Words हालिया रिलीज़ सहित विभिन्न Microsoft Word संस्करणों के साथ संगतता सुनिश्चित करता है।

### क्या Aspose.Words for .NET दस्तावेज़ एन्क्रिप्शन का समर्थन करता है?
हां, आप .NET के लिए Aspose.Words का उपयोग करके अपने दस्तावेज़ों को प्रोग्रामेटिक रूप से एन्क्रिप्ट और सुरक्षित कर सकते हैं।

### मैं Aspose.Words for .NET के लिए और अधिक सहायता और समर्थन कहां पा सकता हूं?
 दौरा करना[Aspose.Words फ़ोरम](https://forum.aspose.com/c/words/8) सामुदायिक समर्थन और चर्चा के लिए।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
