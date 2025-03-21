---
title: स्रोत स्वरूपण रखें
linktitle: स्रोत स्वरूपण रखें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके फ़ॉर्मेटिंग को संरक्षित करते हुए Word दस्तावेज़ों को मर्ज करना सीखें। दस्तावेज़ असेंबली कार्यों को स्वचालित करने की चाह रखने वाले डेवलपर्स के लिए आदर्श।
weight: 10
url: /hi/net/join-and-append-documents/keep-source-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# स्रोत स्वरूपण रखें

## परिचय

इस ट्यूटोरियल में, हम .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों को मर्ज और जोड़ने का तरीका जानेंगे। यह शक्तिशाली लाइब्रेरी डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ों में हेरफेर करने की व्यापक क्षमताएँ प्रदान करती है। हम दस्तावेज़ मर्जिंग के दौरान स्रोत स्वरूपण को बरकरार रखने की विधि पर ध्यान केंद्रित करेंगे, यह सुनिश्चित करते हुए कि मूल शैलियाँ और लेआउट निर्बाध रूप से संरक्षित हैं।

## आवश्यक शर्तें

ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:

- विकास वातावरण: विज़ुअल स्टूडियो या कोई भी IDE जो .NET विकास का समर्थन करता है।
-  .NET लाइब्रेरी के लिए Aspose.Words: लाइब्रेरी को यहां से डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.aspose.com/words/net/).
- C# प्रोग्रामिंग का बुनियादी ज्ञान: C# सिंटैक्स और ऑब्जेक्ट-ओरिएंटेड प्रोग्रामिंग अवधारणाओं से परिचित होना।

## नामस्थान आयात करें

अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को आयात करके प्रारंभ करें:

```csharp
using Aspose.Words;
```

## चरण 1: अपना प्रोजेक्ट सेट करें

Visual Studio में एक नया C# कंसोल एप्लिकेशन बनाएँ और Aspose.Words NuGet पैकेज स्थापित करें। इस पैकेज में आपके प्रोजेक्ट में Word दस्तावेज़ों के साथ काम करने के लिए आवश्यक लाइब्रेरीज़ शामिल हैं।

## चरण 2: Aspose.Words नामस्थान शामिल करें

Aspose.Words क्लासेस और विधियों तक पहुँचने के लिए सुनिश्चित करें कि आपने अपनी C# फ़ाइल के आरंभ में Aspose.Words नामस्थान शामिल किया है।

## चरण 3: दस्तावेज़ पथ आरंभ करें

अपनी दस्तावेज़ निर्देशिका का पथ निर्धारित करें जहाँ स्रोत और गंतव्य दस्तावेज़ स्थित हैं।

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## चरण 4: गंतव्य दस्तावेज़ बनाएँ

गंतव्य दस्तावेज़ बनाने के लिए दस्तावेज़ वर्ग का एक नया उदाहरण आरंभ करें जहां मर्ज की गई सामग्री संग्रहीत की जाएगी।

```csharp
Document dstDoc = new Document();
```

## चरण 5: स्रोत दस्तावेज़ लोड करें

इसी प्रकार, उस स्रोत दस्तावेज़ को लोड करने के लिए एक अन्य दस्तावेज़ ऑब्जेक्ट बनाएं जिसे आप गंतव्य दस्तावेज़ में जोड़ना चाहते हैं।

```csharp
Document srcDoc = new Document();
```

## चरण 6: फ़ॉर्मेटिंग को बनाए रखते हुए स्रोत दस्तावेज़ जोड़ें

स्रोत दस्तावेज़ को उसके मूल स्वरूपण को संरक्षित करते हुए गंतव्य दस्तावेज़ में विलय करने के लिए, ImportFormatMode को KeepSourceFormatting पर सेट करके AppendDocument विधि का उपयोग करें।

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## चरण 7: मर्ज किए गए दस्तावेज़ को सहेजें

अंत में, मर्ज किए गए दस्तावेज़ को Save विधि का उपयोग करके निर्दिष्ट निर्देशिका में सहेजें।

```csharp
dstDoc.Save(dataDir + "MergedDocument.docx");
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने बताया है कि .NET के लिए Aspose.Words का उपयोग करके मूल स्वरूपण को बनाए रखते हुए Word दस्तावेज़ों को कैसे मर्ज किया जाए। यह दृष्टिकोण सुनिश्चित करता है कि स्रोत दस्तावेज़ों से शैलियाँ, फ़ॉन्ट और लेआउट गंतव्य दस्तावेज़ में सहजता से एकीकृत होते हैं, जो दस्तावेज़ असेंबली कार्यों के लिए एक मजबूत समाधान प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं .NET के लिए Aspose.Words का उपयोग करके एक ही ऑपरेशन में कई दस्तावेज़ों को मर्ज कर सकता हूँ?
हां, आप प्रत्येक दस्तावेज़ को गंतव्य दस्तावेज़ में क्रमिक रूप से जोड़कर एकाधिक दस्तावेज़ों को मर्ज कर सकते हैं।

### क्या Aspose.Words दस्तावेज़ विलय के दौरान सभी स्वरूपण विशेषताओं को सुरक्षित रखता है?
Aspose.Words विभिन्न आयात मोडों का समर्थन करता है; KeepSourceFormatting मोड यह सुनिश्चित करता है कि अधिकांश स्वरूपण विशेषताएँ बरकरार रहें।

### क्या Aspose.Words .NET कोर अनुप्रयोगों के साथ संगत है?
हां, Aspose.Words .NET कोर का समर्थन करता है, जिससे आप इसे विभिन्न प्लेटफार्मों पर उपयोग कर सकते हैं।

### मैं Aspose.Words का उपयोग करके बड़े दस्तावेज़ों को कुशलतापूर्वक कैसे संभाल सकता हूँ?
Aspose.Words बड़े दस्तावेज़ों के साथ काम करने के लिए कुशल API प्रदान करता है, जिसमें पृष्ठांकन और मेमोरी प्रबंधन की सुविधाएं भी शामिल हैं।

### मैं Aspose.Words के लिए अधिक संसाधन और समर्थन कहां पा सकता हूं?
 दौरा करना[.NET दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/net/) विस्तृत API संदर्भ, उदाहरण और मार्गदर्शिका के लिए.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
