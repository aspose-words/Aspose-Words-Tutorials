---
title: प्रत्येक अनुभाग पर सूची पुनः आरंभ करें
linktitle: प्रत्येक अनुभाग पर सूची पुनः आरंभ करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में प्रत्येक अनुभाग पर सूचियों को पुनः आरंभ करने का तरीका जानें। सूचियों को प्रभावी ढंग से प्रबंधित करने के लिए हमारे विस्तृत चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रत्येक अनुभाग पर सूची पुनः आरंभ करें

## परिचय

संरचित और सुव्यवस्थित दस्तावेज़ बनाना कभी-कभी एक जटिल पहेली को सुलझाने जैसा लग सकता है। उस पहेली का एक हिस्सा सूचियों को प्रभावी ढंग से प्रबंधित करना है, खासकर जब आप उन्हें प्रत्येक अनुभाग पर फिर से शुरू करना चाहते हैं। Aspose.Words for .NET के साथ, आप इसे सहजता से पूरा कर सकते हैं। आइए जानें कि आप Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में प्रत्येक अनुभाग पर सूचियों को कैसे फिर से शुरू कर सकते हैं।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  .NET के लिए Aspose.Words: नवीनतम संस्करण डाउनलोड करें और इंस्टॉल करें[एस्पोज रिलीज](https://releases.aspose.com/words/net/) पृष्ठ.
2. .NET वातावरण: .NET स्थापित करके अपना विकास वातावरण सेट करें।
3. C# की बुनियादी समझ: C# प्रोग्रामिंग भाषा से परिचित होना अनुशंसित है।
4.  Aspose लाइसेंस: आप एक का विकल्प चुन सकते हैं[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) यदि आपके पास नहीं है.

## नामस्थान आयात करें

कोड लिखने से पहले, सुनिश्चित करें कि आपने आवश्यक नेमस्पेस आयात कर लिए हैं:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

अब, आइए इस प्रक्रिया को कई चरणों में विभाजित करें ताकि इसका अनुसरण करना आसान हो जाए।

## चरण 1: दस्तावेज़ को आरंभ करें

सबसे पहले, आपको एक नया दस्तावेज़ इंस्टैंस बनाना होगा।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## चरण 2: क्रमांकित सूची जोड़ें

इसके बाद, दस्तावेज़ में क्रमांकित सूची जोड़ें। यह सूची डिफ़ॉल्ट क्रमांकन प्रारूप का पालन करेगी।

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## चरण 3: सूची तक पहुंचें और पुनः आरंभ संपत्ति सेट करें

आपके द्वारा अभी-अभी बनाई गई सूची को पुनः प्राप्त करें और उसका नाम सेट करें`IsRestartAtEachSection`संपत्ति को`true`यह सुनिश्चित करता है कि सूची प्रत्येक नए अनुभाग पर क्रमांकन पुनः आरंभ करे।

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## चरण 4: एक दस्तावेज़ बिल्डर बनाएं और सूची संबद्ध करें

 एक बनाने के`DocumentBuilder` दस्तावेज़ में सामग्री सम्मिलित करने और उसे सूची के साथ संबद्ध करने के लिए.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## चरण 5: सूची आइटम जोड़ें और अनुभाग विराम डालें

अब, सूची में आइटम जोड़ें। पुनः आरंभ करने की कार्यक्षमता को स्पष्ट करने के लिए, हम कुछ निश्चित संख्या में आइटम के बाद एक अनुभाग विराम डालेंगे।

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## चरण 6: दस्तावेज़ सहेजें

अंत में, अनुपालन सुनिश्चित करने के लिए दस्तावेज़ को उचित विकल्पों के साथ सहेजें।

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## निष्कर्ष

और अब यह आपके लिए है! इन चरणों का पालन करके, आप .NET के लिए Aspose.Words का उपयोग करके अपने Word दस्तावेज़ों में प्रत्येक अनुभाग पर सूचियों को आसानी से पुनः आरंभ कर सकते हैं। यह सुविधा अच्छी तरह से संरचित दस्तावेज़ बनाने के लिए अविश्वसनीय रूप से उपयोगी है, जिसके लिए अलग-अलग अनुभागों की आवश्यकता होती है, जिसमें उनकी अपनी सूची क्रमांकन होती है। Aspose.Words के साथ, ऐसे कार्यों को संभालना आसान हो जाता है, जिससे आप उच्च-गुणवत्ता वाली सामग्री तैयार करने पर ध्यान केंद्रित कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं विभिन्न सूची प्रकारों के लिए प्रत्येक अनुभाग पर सूचियों को पुनः आरंभ कर सकता हूँ?
हां, .NET के लिए Aspose.Words आपको बुलेट और क्रमांकित सूचियों सहित विभिन्न सूची प्रकारों को पुनः आरंभ करने की अनुमति देता है।

### यदि मैं नंबरिंग प्रारूप को अनुकूलित करना चाहूँ तो क्या होगा?
 आप संख्या प्रारूप को संशोधित करके अनुकूलित कर सकते हैं`ListTemplate` सूची बनाते समय संपत्ति का उपयोग करें।

### क्या सूची में आइटमों की संख्या की कोई सीमा होती है?
नहीं, .NET के लिए Aspose.Words का उपयोग करके सूची में आइटमों की संख्या की कोई विशिष्ट सीमा नहीं है।

### क्या मैं इस सुविधा का उपयोग पीडीएफ जैसे अन्य दस्तावेज़ प्रारूपों में कर सकता हूं?
हां, आप सूची संरचना को बनाए रखते हुए Word दस्तावेज़ों को PDF जैसे अन्य प्रारूपों में परिवर्तित करने के लिए Aspose.Words का उपयोग कर सकते हैं।

### मैं .NET के लिए Aspose.Words का निःशुल्क परीक्षण कैसे प्राप्त कर सकता हूँ?
 आप यहां से निःशुल्क परीक्षण प्राप्त कर सकते हैं[एस्पोज रिलीज](https://releases.aspose.com/) पृष्ठ.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
