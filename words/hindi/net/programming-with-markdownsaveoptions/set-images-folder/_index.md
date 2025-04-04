---
title: छवियाँ फ़ोल्डर सेट करें
linktitle: छवियाँ फ़ोल्डर सेट करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके उचित तालिका संरेखण के साथ Word दस्तावेज़ों को Markdown में बदलें। बेहतरीन परिणामों के लिए हमारी विस्तृत मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# छवियाँ फ़ोल्डर सेट करें

## परिचय

क्या आपने कभी अपने वर्ड डॉक्यूमेंट को मार्कडाउन फॉर्मेट में एक्सपोर्ट करना चाहा है, जबकि यह सुनिश्चित करना है कि टेबल और कंटेंट एकदम सही तरीके से संरेखित हों? इस कार्य के लिए Aspose.Words for .NET आपका सबसे अच्छा समाधान है। इस लेख में, हम आपको Aspose.Words को सेट अप करने, अपने डॉक्यूमेंट को तैयार करने और उचित टेबल कंटेंट संरेखण के साथ इसे मार्कडाउन में एक्सपोर्ट करने की प्रक्रिया से अवगत कराएँगे। हम प्रत्येक चरण को इस तरह से विभाजित करेंगे कि उसका पालन करना और समझना आसान हो जाए। तो, चलिए शुरू करते हैं और अपने वर्ड डॉक्यूमेंट को खूबसूरती से संरेखित मार्कडाउन फ़ाइलों में बदलते हैं!

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

-  .NET के लिए Aspose.Words: आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).
-  वैध लाइसेंस: निःशुल्क परीक्षण प्राप्त करें[यहाँ](https://releases.aspose.com/) या अस्थायी लाइसेंस[यहाँ](https://purchase.aspose.com/temporary-license/).
- विजुअल स्टूडियो: या कोई अन्य IDE जो .NET विकास का समर्थन करता है।
- C# का मूलभूत ज्ञान: C# प्रोग्रामिंग भाषा की समझ।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को आयात करना होगा। ये नामस्थान आपको Aspose.Words कार्यक्षमता तक पहुँचने की अनुमति देंगे।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## चरण 1: अपना प्रोजेक्ट सेट करें

सबसे पहले, अपने IDE में अपना .NET प्रोजेक्ट सेट करें। एक नया कंसोल एप्लिकेशन बनाएं और .NET के लिए Aspose.Words का संदर्भ जोड़ें।

### 1.1 नया प्रोजेक्ट बनाएं

Visual Studio खोलें और एक नया कंसोल एप्लिकेशन प्रोजेक्ट बनाएँ। इसे "MarkdownExporter" या कुछ ऐसा नाम दें।

### 1.2 Aspose.Words संदर्भ जोड़ें

 अपने प्रोजेक्ट में Aspose.Words जोड़ने के लिए, आप या तो DLL को यहाँ से डाउनलोड कर सकते हैं[Aspose वेबसाइट](https://releases.aspose.com/words/net/) और इसे मैन्युअल रूप से जोड़ें, या NuGet पैकेज मैनेजर का उपयोग करें:

```bash
Install-Package Aspose.Words
```

## चरण 2: मार्कडाउन के रूप में निर्यात करने के लिए कोड लिखें

अब, आइए वर्ड दस्तावेज़ को पढ़ने और उसे उचित तालिका संरेखण के साथ मार्कडाउन फ़ाइल के रूप में सहेजने के लिए कोड लिखें।

### 2.1 अपने दस्तावेज़ का पथ निर्धारित करें

अपने वर्ड दस्तावेज़ का पथ और वह फ़ोल्डर सेट करें जहाँ आप छवियाँ सहेजना चाहते हैं।

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 दस्तावेज़ लोड करें

Aspose.Words का उपयोग करके अपना Word दस्तावेज़ लोड करें।

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 मार्कडाउन सेव विकल्प कॉन्फ़िगर करें

 कॉन्फ़िगर करें`MarkdownSaveOptions` यह निर्दिष्ट करने के लिए कि छवियों को कहां संग्रहीत किया जाना चाहिए.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 दस्तावेज़ को मार्कडाउन के रूप में सहेजें

 का उपयोग करो`MemoryStream` दस्तावेज़ को मार्कडाउन प्रारूप में सहेजने के लिए.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## निष्कर्ष

Aspose.Words for .NET का उपयोग करके टेबल कंटेंट अलाइनमेंट के साथ Word डॉक्यूमेंट को Markdown में एक्सपोर्ट करना आसान है, जब आप इन चरणों का पालन करते हैं। कोड की कुछ पंक्तियों के साथ, आप रूपांतरण प्रक्रिया को स्वचालित कर सकते हैं और सुनिश्चित कर सकते हैं कि आपकी सामग्री अच्छी तरह से फ़ॉर्मेट की गई है। अब, आप अपने दस्तावेज़ों को Markdown फ़ॉर्मेट में आसानी से साझा कर सकते हैं, यह जानते हुए कि वे शानदार दिखेंगे और उनकी संरचना बनाए रखेंगे।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं अन्य प्रोग्रामिंग भाषाओं के साथ .NET के लिए Aspose.Words का उपयोग कर सकता हूँ?

हां, .NET के लिए Aspose.Words का उपयोग किसी भी .NET-संगत भाषा जैसे VB.NET, F#, आदि के साथ किया जा सकता है।

### मैं Aspose.Words के लिए अस्थायी लाइसेंस कैसे प्राप्त करूं?

आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### मैं किस प्रकार के दस्तावेज़ों को मार्कडाउन में परिवर्तित कर सकता हूँ?

आप .doc, .docx, .rtf, आदि सहित विभिन्न वर्ड दस्तावेज़ों को परिवर्तित कर सकते हैं।

### क्या Aspose.Words के परीक्षण संस्करण में कोई सीमाएँ हैं?

परीक्षण संस्करण में कुछ सीमाएँ हैं जैसे आउटपुट फ़ाइलों में वॉटरमार्क। आप निःशुल्क परीक्षण प्राप्त कर सकते हैं[यहाँ](https://releases.aspose.com/).

### मैं Aspose.Words के लिए और अधिक उदाहरण और दस्तावेज़ कहां पा सकता हूं?

 आप विस्तृत दस्तावेज और उदाहरण यहां पा सकते हैं[Aspose वेबसाइट](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
