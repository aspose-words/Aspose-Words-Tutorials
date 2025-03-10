---
title: वर्ड डॉक्यूमेंट में हेडर फूटर पर जाएँ
linktitle: वर्ड डॉक्यूमेंट में हेडर फूटर पर जाएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: हमारे चरण-दर-चरण गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में हेडर और फ़ुटर पर जाने का तरीका जानें। अपने दस्तावेज़ निर्माण कौशल को बढ़ाएँ।
weight: 10
url: /hi/net/add-content-using-documentbuilder/move-to-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड डॉक्यूमेंट में हेडर फूटर पर जाएँ

## परिचय

जब वर्ड डॉक्यूमेंट को प्रोग्रामेटिक रूप से बनाने और प्रबंधित करने की बात आती है, तो Aspose.Words for .NET एक शक्तिशाली उपकरण है जो आपका बहुत समय और प्रयास बचा सकता है। इस लेख में, हम Aspose.Words for .NET का उपयोग करके वर्ड डॉक्यूमेंट में हेडर और फ़ुटर पर जाने का तरीका जानेंगे। यह सुविधा तब ज़रूरी होती है जब आपको अपने डॉक्यूमेंट के हेडर या फ़ुटर सेक्शन में विशिष्ट सामग्री जोड़ने की ज़रूरत होती है। चाहे आप कोई रिपोर्ट, इनवॉइस या कोई ऐसा दस्तावेज़ बना रहे हों जिसके लिए पेशेवर स्पर्श की ज़रूरत हो, हेडर और फ़ुटर में हेरफेर करना समझना बहुत ज़रूरी है।

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, आइए सुनिश्चित करें कि आपने सब कुछ सेट कर लिया है:

1. **Aspose.Words for .NET** : सुनिश्चित करें कि आपके पास .NET लाइब्रेरी के लिए Aspose.Words है। आप इसे यहाँ से डाउनलोड कर सकते हैं[Aspose रिलीज़ पेज](https://releases.aspose.com/words/net/).
2. **Development Environment**आपको Visual Studio जैसे विकास परिवेश की आवश्यकता है।
3. **Basic Knowledge of C#**C# प्रोग्रामिंग की मूल बातें समझने से आपको आगे बढ़ने में मदद मिलेगी।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको आवश्यक नामस्थानों को आयात करना होगा। यह चरण .NET के लिए Aspose.Words द्वारा प्रदान की गई कक्षाओं और विधियों तक पहुँचने के लिए महत्वपूर्ण है।

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System;
```

आइए इस प्रक्रिया को सरल चरणों में विभाजित करें। प्रत्येक चरण को स्पष्ट रूप से समझाया जाएगा ताकि आपको यह समझने में मदद मिले कि कोड क्या कर रहा है और क्यों कर रहा है।

## चरण 1: दस्तावेज़ को आरंभ करें

पहला कदम एक नया दस्तावेज़ और एक DocumentBuilder ऑब्जेक्ट आरंभ करना है। DocumentBuilder वर्ग आपको दस्तावेज़ का निर्माण और उसमें हेरफेर करने की अनुमति देता है।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 इस चरण में, आप एक नया उदाहरण बनाते हैं`Document` वर्ग और`DocumentBuilder` वर्ग.`dataDir` वेरिएबल का उपयोग उस निर्देशिका को निर्दिष्ट करने के लिए किया जाता है जहां आप दस्तावेज़ को सहेजना चाहते हैं।

## चरण 2: पेज सेटअप कॉन्फ़िगर करें

इसके बाद, हमें यह निर्दिष्ट करना होगा कि शीर्षलेख और पादलेख प्रथम, सम और विषम पृष्ठों के लिए अलग-अलग होने चाहिए।

```csharp
//निर्दिष्ट करें कि हम प्रथम, सम और विषम पृष्ठों के लिए शीर्षलेख और पादलेख अलग-अलग चाहते हैं।
builder.PageSetup.DifferentFirstPageHeaderFooter = true;
builder.PageSetup.OddAndEvenPagesHeaderFooter = true;
```

ये सेटिंग्स सुनिश्चित करती हैं कि आप विभिन्न प्रकार के पृष्ठों के लिए अद्वितीय शीर्षलेख और पादलेख रख सकें।

## चरण 3: हेडर/फुटर पर जाएं और सामग्री जोड़ें

अब, हेडर और फ़ुटर अनुभागों पर चलते हैं और कुछ सामग्री जोड़ते हैं।

```csharp
// हेडर बनाएं.
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.Write("Header for the first page");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderEven);
builder.Write("Header for even pages");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);
builder.Write("Header for all other pages");
```

 इस चरण में, हम उपयोग करते हैं`MoveToHeaderFooter` वांछित शीर्षलेख या पादलेख अनुभाग पर नेविगेट करने की विधि।`Write` फिर इन अनुभागों में पाठ जोड़ने के लिए .विधि का उपयोग किया जाता है।

## चरण 4: दस्तावेज़ के मुख्य भाग में सामग्री जोड़ें

शीर्षलेखों और पादलेखों को प्रदर्शित करने के लिए, आइए दस्तावेज़ के मुख्य भाग में कुछ सामग्री जोड़ें और कुछ पृष्ठ बनाएँ।

```csharp
// दस्तावेज़ में दो पृष्ठ बनाएँ.
builder.MoveToSection(0);
builder.Writeln("Page1");
builder.InsertBreak(BreakType.PageBreak);
builder.Writeln("Page2");
```

यहां, हम दस्तावेज़ में पाठ जोड़ते हैं और दूसरा पृष्ठ बनाने के लिए पृष्ठ विराम सम्मिलित करते हैं।

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें।

```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx");
```

कोड की यह पंक्ति निर्दिष्ट निर्देशिका में "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx" नाम से दस्तावेज़ को सहेजती है।

## निष्कर्ष

 इन चरणों का पालन करके, आप .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में हेडर और फ़ुटर को आसानी से बदल सकते हैं। इस ट्यूटोरियल में मूल बातें शामिल हैं, लेकिन Aspose.Words अधिक जटिल दस्तावेज़ हेरफेर के लिए कई प्रकार की कार्यक्षमता प्रदान करता है। इसे एक्सप्लोर करने में संकोच न करें[प्रलेखन](https://reference.aspose.com/words/net/) अधिक उन्नत सुविधाओं के लिए.

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET एक लाइब्रेरी है जो डेवलपर्स को C# का उपयोग करके प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने में सक्षम बनाती है।

### क्या मैं हेडर और फ़ुटर में छवियाँ जोड़ सकता हूँ?
 हां, आप हेडर और फ़ुटर में चित्र जोड़ सकते हैं`DocumentBuilder.InsertImage` तरीका।

### क्या प्रत्येक अनुभाग के लिए अलग-अलग शीर्षलेख और पादलेख रखना संभव है?
 बिल्कुल! आप अलग-अलग सेटिंग करके प्रत्येक अनुभाग के लिए अद्वितीय हेडर और फ़ुटर रख सकते हैं`HeaderFooterType` प्रत्येक अनुभाग के लिए.

### मैं हेडर और फ़ुटर में अधिक जटिल लेआउट कैसे बनाऊं?
आप जटिल लेआउट बनाने के लिए Aspose.Words द्वारा प्रदान की गई तालिकाओं, छवियों और विभिन्न स्वरूपण विकल्पों का उपयोग कर सकते हैं।

### मैं और अधिक उदाहरण और ट्यूटोरियल कहां पा सकता हूं?
 इसकी जाँच पड़ताल करो[प्रलेखन](https://reference.aspose.com/words/net/) और यह[सहयता मंच](https://forum.aspose.com/c/words/8) अधिक उदाहरणों और सामुदायिक समर्थन के लिए.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
