---
title: तालिका सामग्री संरेखण के साथ मार्कडाउन में निर्यात करें
linktitle: तालिका सामग्री संरेखण के साथ मार्कडाउन में निर्यात करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके संरेखित तालिकाओं के साथ Word दस्तावेज़ों को Markdown में निर्यात करना सीखें। सही Markdown तालिकाओं के लिए हमारे चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# तालिका सामग्री संरेखण के साथ मार्कडाउन में निर्यात करें

## परिचय

नमस्ते! क्या आपने कभी सोचा है कि अपने वर्ड डॉक्यूमेंट को मार्कडाउन फॉर्मेट में कैसे एक्सपोर्ट करें, जिसमें टेबल्स पूरी तरह से अलाइन हों? चाहे आप डॉक्यूमेंटेशन पर काम करने वाले डेवलपर हों या फिर मार्कडाउन को पसंद करने वाले, यह गाइड आपके लिए है। हम इसे हासिल करने के लिए .NET के लिए Aspose.Words का इस्तेमाल करने की बारीकियों पर चर्चा करेंगे। क्या आप अपने वर्ड टेबल्स को मार्कडाउन टेबल्स में बदलने के लिए तैयार हैं? चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, कुछ चीजें हैं जिन्हें आपको ध्यान में रखना होगा:

1.  Aspose.Words for .NET लाइब्रेरी: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी है। आप इसे यहाँ से डाउनलोड कर सकते हैं।[Aspose रिलीज़ पेज](https://releases.aspose.com/words/net/).
2. विकास वातावरण: अपना विकास वातावरण सेट करें। .NET विकास के लिए Visual Studio एक लोकप्रिय विकल्प है।
3. C# का बुनियादी ज्ञान: C# को समझना आवश्यक है क्योंकि हम इस भाषा में कोड लिखेंगे।
4. नमूना वर्ड दस्तावेज़: एक वर्ड दस्तावेज़ रखें जिसका उपयोग आप परीक्षण के लिए कर सकते हैं।

## नामस्थान आयात करें

कोडिंग शुरू करने से पहले, आइए आवश्यक नेमस्पेस को आयात करें। ये हमें Aspose.Words क्लासेस और मेथड्स तक पहुँच प्रदान करेंगे जिनका हम उपयोग करेंगे।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

सबसे पहले, हमें एक नया वर्ड डॉक्यूमेंट बनाना होगा और एक नया वर्ड डॉक्यूमेंट इनिशियलाइज़ करना होगा।`DocumentBuilder` हमारे दस्तावेज़ का निर्माण शुरू करने के लिए ऑब्जेक्ट करें।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// एक नया दस्तावेज़ बनाएँ.
Document doc = new Document();

// डॉक्यूमेंटबिल्डर आरंभ करें.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: कक्ष सम्मिलित करें और सामग्री संरेखित करें

इसके बाद, हम अपने दस्तावेज़ में कुछ सेल डालेंगे और उनका संरेखण सेट करेंगे। यह सुनिश्चित करने के लिए महत्वपूर्ण है कि मार्कडाउन निर्यात सही संरेखण बनाए रखे।

```csharp
// एक सेल डालें और संरेखण को दाईं ओर सेट करें.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// एक अन्य सेल डालें और संरेखण को केंद्र पर सेट करें।
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## चरण 3: मार्कडाउन निर्यात के लिए तालिका सामग्री संरेखण सेट करें

 अब, इसे कॉन्फ़िगर करने का समय आ गया है`MarkdownSaveOptions` निर्यात की गई मार्कडाउन फ़ाइल में तालिका सामग्री के संरेखण को नियंत्रित करने के लिए। हम दस्तावेज़ को अलग-अलग संरेखण सेटिंग्स के साथ सहेजेंगे ताकि देख सकें कि यह कैसे काम करता है।

```csharp
// MarkdownSaveOptions ऑब्जेक्ट बनाएँ.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// दस्तावेज़ को बाएं संरेखण के साथ सहेजें.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// संरेखण को दाईं ओर बदलें और सहेजें.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// संरेखण को केंद्र में बदलें और सहेजें.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## चरण 4: ऑटो टेबल सामग्री संरेखण का उपयोग करें

`Auto`संरेखण विकल्प संबंधित तालिका कॉलम में पहले पैराग्राफ से संरेखण लेता है। यह तब उपयोगी हो सकता है जब आपके पास एक ही तालिका में मिश्रित संरेखण हों।

```csharp
// संरेखण को स्वचालित पर सेट करें.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// दस्तावेज़ को स्वतः संरेखण के साथ सहेजें.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## निष्कर्ष

और अब यह आपके लिए है! Aspose.Words for .NET का उपयोग करके संरेखित तालिकाओं के साथ Word दस्तावेज़ों को Markdown में निर्यात करना एक बार जब आप इसे करना जानते हैं तो यह बहुत आसान है। यह शक्तिशाली लाइब्रेरी आपके तालिकाओं के स्वरूपण और संरेखण को नियंत्रित करना आसान बनाती है, यह सुनिश्चित करती है कि आपके Markdown दस्तावेज़ बिल्कुल वैसे ही दिखें जैसे आप चाहते हैं। हैप्पी कोडिंग!

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
.NET के लिए Aspose.Words एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संशोधित करने, परिवर्तित करने और निर्यात करने में सक्षम बनाती है।

### क्या मैं एक ही तालिका में विभिन्न स्तंभों के लिए अलग-अलग संरेखण निर्धारित कर सकता हूँ?
 हाँ, का उपयोग करके`Auto` संरेखण विकल्प के अंतर्गत, आप प्रत्येक कॉलम में पहले पैराग्राफ के आधार पर अलग-अलग संरेखण रख सकते हैं।

### क्या मुझे .NET के लिए Aspose.Words का उपयोग करने के लिए लाइसेंस की आवश्यकता है?
 हां, .NET के लिए Aspose.Words को पूर्ण कार्यक्षमता के लिए लाइसेंस की आवश्यकता होती है। आप एक प्राप्त कर सकते हैं[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) मूल्यांकन हेतु.

### क्या Aspose.Words का उपयोग करके अन्य दस्तावेज़ तत्वों को मार्कडाउन में निर्यात करना संभव है?
हां, Aspose.Words शीर्षकों, सूचियों और छवियों जैसे विभिन्न तत्वों को मार्कडाउन प्रारूप में निर्यात करने का समर्थन करता है।

### यदि मुझे कोई समस्या आती है तो मुझे सहायता कहां से मिल सकती है?
 आप यहाँ से सहायता प्राप्त कर सकते हैं[Aspose.Words समर्थन फ़ोरम](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
