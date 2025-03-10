---
title: वर्ड दस्तावेज़ में क्षैतिज नियम प्रारूप
linktitle: वर्ड दस्तावेज़ में क्षैतिज नियम प्रारूप
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में अनुकूलन योग्य क्षैतिज नियम सम्मिलित करना सीखें। अपने दस्तावेज़ स्वचालन को बढ़ाएँ।
weight: 10
url: /hi/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड दस्तावेज़ में क्षैतिज नियम प्रारूप

## परिचय

.NET विकास के क्षेत्र में, Word दस्तावेज़ों को प्रोग्रामेटिक रूप से हेरफेर करना और फ़ॉर्मेट करना एक कठिन काम हो सकता है। सौभाग्य से, .NET के लिए Aspose.Words एक मजबूत समाधान प्रदान करता है, जो डेवलपर्स को दस्तावेज़ निर्माण, संपादन और प्रबंधन को आसानी से स्वचालित करने में सक्षम बनाता है। यह लेख आवश्यक विशेषताओं में से एक पर गहराई से चर्चा करता है: Word दस्तावेज़ों में क्षैतिज नियम सम्मिलित करना। चाहे आप एक अनुभवी डेवलपर हों या Aspose.Words के साथ अभी शुरुआत कर रहे हों, इस क्षमता में महारत हासिल करने से आपकी दस्तावेज़ निर्माण प्रक्रिया में वृद्धि होगी।

## आवश्यक शर्तें

.NET के लिए Aspose.Words का उपयोग करके क्षैतिज नियमों को लागू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:

- विज़ुअल स्टूडियो: .NET विकास के लिए विज़ुअल स्टूडियो IDE स्थापित करें।
- Aspose.Words for .NET: Aspose.Words for .NET को यहाँ से डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.aspose.com/words/net/).
- बुनियादी C# ज्ञान: C# प्रोग्रामिंग भाषा की मूल बातों से परिचित होना।
-  डॉक्यूमेंटबिल्डर क्लास: की समझ`DocumentBuilder` दस्तावेज़ हेरफेर के लिए Aspose.Words में वर्ग।

## नामस्थान आयात करें

आरंभ करने के लिए, अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करें:

```csharp
using Aspose.Words;
using System.Drawing;
```

ये नामस्थान दस्तावेज़ हेरफेर के लिए Aspose.Words क्लासों और रंगों को संभालने के लिए मानक .NET क्लासों तक पहुंच प्रदान करते हैं।

आइए Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में क्षैतिज नियम जोड़ने की प्रक्रिया को व्यापक चरणों में विभाजित करें:

## चरण 1: डॉक्यूमेंटबिल्डर आरंभ करें और निर्देशिका सेट करें

 सबसे पहले, एक आरंभ करें`DocumentBuilder` ऑब्जेक्ट चुनें और निर्देशिका पथ सेट करें जहां दस्तावेज़ सहेजा जाएगा।

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## चरण 2: क्षैतिज नियम डालें

 उपयोग`InsertHorizontalRule()` की विधि`DocumentBuilder` वर्ग में क्षैतिज नियम जोड़ें।

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## चरण 3: क्षैतिज नियम प्रारूप को अनुकूलित करें

 तक पहुंच`HorizontalRuleFormat` क्षैतिज नियम के स्वरूप को अनुकूलित करने के लिए सम्मिलित आकृति की संपत्ति का उपयोग करें।

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- संरेखण: क्षैतिज नियम के संरेखण को निर्दिष्ट करता है (`HorizontalRuleAlignment.Center` (इस उदाहरण में)
- WidthPercent: क्षैतिज नियम की चौड़ाई को पृष्ठ की चौड़ाई के प्रतिशत के रूप में सेट करता है (इस उदाहरण में 70%).
- ऊँचाई: क्षैतिज नियम की ऊँचाई को बिन्दुओं में परिभाषित करता है (इस उदाहरण में 3 बिन्दु)।
- रंग: क्षैतिज नियम का रंग सेट करता है (`Color.Blue` (इस उदाहरण में)
- NoShade: निर्दिष्ट करता है कि क्षैतिज नियम में छाया होनी चाहिए या नहीं (`true` (इस उदाहरण में)

## चरण 4: दस्तावेज़ सहेजें

 अंत में, संशोधित दस्तावेज़ को सहेजें`Save` की विधि`Document` वस्तु।

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## निष्कर्ष

.NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में क्षैतिज नियमों को सम्मिलित करने में महारत हासिल करने से आपकी दस्तावेज़ स्वचालन क्षमताएँ बढ़ जाती हैं। Aspose.Words की लचीलेपन और शक्ति का लाभ उठाकर, डेवलपर्स दस्तावेज़ निर्माण और फ़ॉर्मेटिंग प्रक्रियाओं को कुशलतापूर्वक सुव्यवस्थित कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET, .NET अनुप्रयोगों में Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने के लिए एक शक्तिशाली लाइब्रेरी है।

### मैं .NET के लिए Aspose.Words कैसे डाउनलोड कर सकता हूँ?
 आप .NET के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).

### क्या मैं Aspose.Words में क्षैतिज नियमों की उपस्थिति को अनुकूलित कर सकता हूं?
हां, आप Aspose.Words का उपयोग करके क्षैतिज नियमों के संरेखण, चौड़ाई, ऊंचाई, रंग और छायांकन जैसे विभिन्न पहलुओं को अनुकूलित कर सकते हैं।

### क्या Aspose.Words एंटरप्राइज़-स्तरीय दस्तावेज़ प्रसंस्करण के लिए उपयुक्त है?
हां, Aspose.Words को इसके मजबूत दस्तावेज़ हेरफेर क्षमताओं के लिए उद्यम वातावरण में व्यापक रूप से उपयोग किया जाता है।

### मुझे .NET के लिए Aspose.Words का समर्थन कहां मिल सकता है?
 समर्थन और सामुदायिक सहभागिता के लिए, यहां जाएं[Aspose.Words फ़ोरम](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
