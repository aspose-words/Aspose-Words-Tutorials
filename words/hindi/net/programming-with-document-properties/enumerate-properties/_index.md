---
title: गुण गिनाएँ
linktitle: गुण गिनाएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में गुणों की गणना करना सीखें। सभी कौशल स्तरों के डेवलपर्स के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# गुण गिनाएँ

## परिचय

क्या आप Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करना चाहते हैं? Aspose.Words for .NET एक शक्तिशाली उपकरण है जो आपको ऐसा करने में मदद कर सकता है। आज, मैं आपको Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के गुणों को सूचीबद्ध करने का तरीका बताऊंगा। चाहे आप शुरुआती हों या कुछ अनुभव रखते हों, यह मार्गदर्शिका इसे बातचीत के तरीके से और आसानी से समझने योग्य तरीके से चरण दर चरण समझाएगी।

## आवश्यक शर्तें

इससे पहले कि हम ट्यूटोरियल में आगे बढ़ें, आपको आरंभ करने के लिए कुछ चीजों की आवश्यकता होगी:

-  .NET के लिए Aspose.Words: आप कर सकते हैं[यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).
- विकास वातावरण: विजुअल स्टूडियो की अनुशंसा की जाती है, लेकिन आप कोई भी C# IDE उपयोग कर सकते हैं।
- C# का बुनियादी ज्ञान: C# की बुनियादी समझ आपको आगे बढ़ने में मदद करेगी।

अब, चलिए सीधे इसमें कूदते हैं!

## चरण 1: अपना प्रोजेक्ट सेट अप करना

सबसे पहले, आपको अपना प्रोजेक्ट विजुअल स्टूडियो में सेट करना होगा।

1. नया प्रोजेक्ट बनाएं: Visual Studio खोलें और एक नया कंसोल अनुप्रयोग प्रोजेक्ट बनाएं।
2. .NET के लिए Aspose.Words स्थापित करें: .NET के लिए Aspose.Words स्थापित करने के लिए NuGet पैकेज मैनेजर का उपयोग करें। समाधान एक्सप्लोरर में अपने प्रोजेक्ट पर राइट-क्लिक करें, "NuGet पैकेज प्रबंधित करें" चुनें और "Aspose.Words" खोजें। पैकेज स्थापित करें।

## चरण 2: नामस्थान आयात करें

Aspose.Words के साथ काम करने के लिए, आपको आवश्यक नामस्थान आयात करने की आवश्यकता है। अपनी Program.cs फ़ाइल के शीर्ष पर निम्न जोड़ें:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## चरण 3: अपना दस्तावेज़ लोड करें

इसके बाद, चलिए उस Word दस्तावेज़ को लोड करते हैं जिसके साथ आप काम करना चाहते हैं। इस उदाहरण के लिए, हम आपके प्रोजेक्ट डायरेक्टरी में स्थित "Properties.docx" नामक दस्तावेज़ का उपयोग करेंगे।

1. दस्तावेज़ पथ परिभाषित करें: अपने दस्तावेज़ का पथ निर्दिष्ट करें।
2.  दस्तावेज़ लोड करें: Aspose.Words का उपयोग करें`Document` दस्तावेज़ लोड करने के लिए क्लास का उपयोग करें.

कोड यह है:

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## चरण 4: दस्तावेज़ का नाम प्रदर्शित करें

एक बार आपका दस्तावेज़ लोड हो जाने के बाद, आप उसका नाम प्रदर्शित करना चाहेंगे। Aspose.Words इसके लिए एक प्रॉपर्टी प्रदान करता है:

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## चरण 5: अंतर्निहित गुणों की गणना करें

अंतर्निहित गुण Microsoft Word द्वारा पूर्वनिर्धारित मेटाडेटा गुण हैं। इनमें शीर्षक, लेखक और बहुत कुछ शामिल हैं।

1.  अंतर्निहित गुणों तक पहुंचें: का उपयोग करें`BuiltInDocumentProperties` संग्रह।
2. गुणों के माध्यम से लूप करें: गुणों के माध्यम से पुनरावृति करें और उनके नाम और मान प्रदर्शित करें।

कोड यह है:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## चरण 6: कस्टम गुण सूचीबद्ध करें

कस्टम गुण उपयोगकर्ता-परिभाषित मेटाडेटा गुण हैं। ये कुछ भी हो सकते हैं जिन्हें आप अपने दस्तावेज़ में जोड़ना चाहते हैं।

1.  कस्टम गुण तक पहुंचें: का उपयोग करें`CustomDocumentProperties` संग्रह।
2. गुणों के माध्यम से लूप करें: गुणों के माध्यम से पुनरावृति करें और उनके नाम और मान प्रदर्शित करें।

कोड यह है:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## निष्कर्ष

और अब आप यह कर सकते हैं! आपने .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ के बिल्ट-इन और कस्टम दोनों गुणों को सफलतापूर्वक सूचीबद्ध किया है। Aspose.Words के साथ आप क्या कर सकते हैं, यह सिर्फ़ शुरुआत है। चाहे आप दस्तावेज़ निर्माण को स्वचालित कर रहे हों या जटिल दस्तावेज़ों में हेरफेर कर रहे हों, Aspose.Words आपके जीवन को आसान बनाने के लिए सुविधाओं का एक समृद्ध सेट प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं किसी दस्तावेज़ में नए गुण जोड़ सकता हूँ?
 हां, आप इसका उपयोग करके नई कस्टम प्रॉपर्टी जोड़ सकते हैं`CustomDocumentProperties` संग्रह।

### क्या Aspose.Words का उपयोग निःशुल्क है?
 Aspose.Words प्रदान करता है एक[मुफ्त परीक्षण](https://releases.aspose.com/) और अलग[खरीद विकल्प](https://purchase.aspose.com/buy).

### मैं Aspose.Words के लिए समर्थन कैसे प्राप्त करूं?
 आप Aspose समुदाय से सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.aspose.com/c/words/8).

### क्या मैं अन्य .NET भाषाओं के साथ Aspose.Words का उपयोग कर सकता हूँ?
हां, Aspose.Words VB.NET सहित कई .NET भाषाओं का समर्थन करता है।

### मैं और अधिक उदाहरण कहां पा सकता हूं?
 इसकी जाँच पड़ताल करो[.NET दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/net/) अधिक उदाहरण और विस्तृत जानकारी के लिए.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
