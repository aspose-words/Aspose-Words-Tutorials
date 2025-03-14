---
title: वर्ड में सरल टेक्स्ट खोजें और बदलें
linktitle: वर्ड में सरल टेक्स्ट खोजें और बदलें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में टेक्स्ट को आसानी से ढूँढ़ना और बदलना सीखें। चरण-दर-चरण मार्गदर्शिका शामिल है।
weight: 10
url: /hi/net/find-and-replace-text/simple-find-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड में सरल टेक्स्ट खोजें और बदलें

## परिचय

नमस्ते, महत्वाकांक्षी कोडर! क्या आपको कभी भी वर्ड डॉक्यूमेंट में किसी शब्द या वाक्यांश के कई उदाहरणों को अपडेट करने की ज़रूरत पड़ी है, बिना हर एक को मैन्युअल रूप से खोजने और बदलने के थकाऊ काम के? कल्पना करें कि आपके पास एक टेम्प्लेट है जो कहता है "_CustomerName_" और आपको इसके बजाय "जेम्स बॉन्ड" कहने की आवश्यकता है। आसान है, है ना? खैर, यह .NET के लिए Aspose.Words के साथ हो सकता है! इस ट्यूटोरियल में, हम आपको .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में टेक्स्ट खोजने और बदलने की प्रक्रिया के माध्यम से चलेंगे। बकसुआ और अपने पाठ हेरफेर कार्यों को सुव्यवस्थित करने के लिए तैयार हो जाओ!

## आवश्यक शर्तें

इससे पहले कि हम टेक्स्ट प्रतिस्थापन के जादू में उतरें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

1.  .NET लाइब्रेरी के लिए Aspose.Words: आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/) यदि आपने अभी तक ऐसा नहीं किया है, तो निःशुल्क परीक्षण का लाभ उठाएँ[यहाँ](https://releases.aspose.com/).

2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके मशीन पर .NET फ्रेमवर्क स्थापित है। यदि आवश्यक हो तो आप इसे Microsoft वेबसाइट से डाउनलोड कर सकते हैं।

3. C# का बुनियादी ज्ञान: C# से थोड़ी परिचितता इस ट्यूटोरियल को समझने में काफी मददगार होगी।

4. एक पाठ संपादक: विजुअल स्टूडियो या कोई अन्य C# संगत IDE.

## नामस्थान आयात करें

इससे पहले कि हम बारीकियों में जाएं, आपको अपने प्रोजेक्ट में आवश्यक नेमस्पेस को आयात करना होगा। यहां बताया गया है कि आप इसे कैसे करते हैं:

```csharp
using Aspose.Words;
using Aspose.Words.Replacing;
```

अब, आइए वर्ड डॉक्यूमेंट में टेक्स्ट को खोजने और बदलने की प्रक्रिया को चरण दर चरण समझते हैं। प्रत्येक चरण सरल और अनुसरण करने में आसान होगा।

## चरण 1: अपनी दस्तावेज़ निर्देशिका सेट करना

सबसे पहले, आइए अपने दस्तावेज़ निर्देशिका का पथ सेट करें। यह वह जगह है जहाँ आपका वर्ड दस्तावेज़ टेक्स्ट प्रतिस्थापन के बाद सहेजा जाएगा।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## चरण 2: नया दस्तावेज़ बनाना

इसके बाद, आप Aspose.Words का उपयोग करके एक नया Word दस्तावेज़ बनाएंगे। इस दस्तावेज़ को खोजने और बदलने की कार्यक्षमता दिखाने के लिए हेरफेर किया जाएगा।

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 यहाँ, हम एक बनाते हैं`Document` वस्तु और एक`DocumentBuilder` वस्तु.`DocumentBuilder` यह हमें अपने दस्तावेज़ में पाठ लिखने में मदद करता है।

## चरण 3: प्रारंभिक पाठ लिखना

 अब, आइए दस्तावेज़ में कुछ पाठ लिखें जिसे हम बाद में बदल देंगे।`DocumentBuilder` "हैलो" टेक्स्ट डालने के लिए_CustomerName_,".

```csharp
builder.Writeln("Hello _CustomerName_,");
```

यह सुनिश्चित करने के लिए कि अब तक सब कुछ सही ढंग से काम कर रहा है, हम मूल दस्तावेज़ पाठ को कंसोल पर प्रिंट करते हैं।

```csharp
Console.WriteLine("Original document text: " + doc.Range.Text);
```

## चरण 4: पाठ बदलना

यहीं पर जादू होता है! हम "_CustomerName_ "जेम्स बॉन्ड" का उपयोग करते हुए`Replace` तरीका। 

```csharp
doc.Range.Replace("_CustomerName_", "James Bond", new FindReplaceOptions(FindReplaceDirection.Forward));
```

 यहाँ,`FindReplaceOptions`हमें खोजने और बदलने की प्रक्रिया की दिशा निर्दिष्ट करने की अनुमति देता है। हम उपयोग कर रहे हैं`FindReplaceDirection.Forward` दस्तावेज़ के आरंभ से अंत तक पाठ को प्रतिस्थापित करने के लिए।

## चरण 5: प्रतिस्थापन का सत्यापन

यह सत्यापित करने के लिए कि प्रतिस्थापन काम कर रहा है, संशोधित दस्तावेज़ पाठ को कंसोल पर प्रिंट करें।

```csharp
Console.WriteLine("Document text after replace: " + doc.Range.Text);
```

आपको यह देखना चाहिए कि "_CustomerName_" को "जेम्स बॉण्ड" से प्रतिस्थापित कर दिया गया है।

## चरण 6: दस्तावेज़ को सहेजना

अंत में, संशोधित दस्तावेज़ को अपनी निर्दिष्ट निर्देशिका में सहेजें।

```csharp
doc.Save(dataDir + "FindAndReplace.SimpleFindReplace.docx");
```

## निष्कर्ष

और अब यह हो गया! आपने Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में टेक्स्ट ढूँढने और बदलने की प्रक्रिया को स्वचालित कर दिया है। अब कोई मैन्युअल अपडेट नहीं और कोई त्रुटि नहीं। चाहे आप रिपोर्ट तैयार कर रहे हों, व्यक्तिगत पत्र बना रहे हों या बस दस्तावेज़ सामग्री का प्रबंधन कर रहे हों, यह सरल लेकिन शक्तिशाली तकनीक आपका बहुत सारा समय बचा सकती है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं एक साथ कई अलग-अलग टेक्स्ट को प्रतिस्थापित कर सकता हूँ?
 हाँ, आप कर सकते हैं। बस फ़ोन करें`Replace` प्रत्येक पाठ के लिए विधि जिसे आप प्रतिस्थापित करना चाहते हैं।

### क्या Aspose.Words for .NET निःशुल्क है?
Aspose.Words for .NET एक निःशुल्क परीक्षण प्रदान करता है, लेकिन पूर्ण कार्यक्षमता के लिए, आपको लाइसेंस खरीदना होगा। उनकी जाँच करें[मूल्य निर्धारण](https://purchase.aspose.com/buy) अधिक जानकारी के लिए.

### क्या मैं टेक्स्ट को फ़ॉर्मेटिंग से बदल सकता हूँ?
 बिल्कुल! आप टेक्स्ट को बदल सकते हैं और फ़ॉर्मेटिंग लागू कर सकते हैं`FindReplaceOptions` कक्षा।

### यदि मैं जिस पाठ को प्रतिस्थापित करना चाहता हूँ वह एकाधिक दस्तावेज़ों में है तो क्या होगा?
आप एकाधिक दस्तावेज़ों में लूप कर सकते हैं और प्रोग्रामेटिक रूप से प्रत्येक पर खोज और प्रतिस्थापन कार्यक्षमता लागू कर सकते हैं।

### क्या Aspose.Words अन्य पाठ हेरफेर सुविधाओं का समर्थन करता है?
हां, Aspose.Words एक शक्तिशाली लाइब्रेरी है जो विभिन्न टेक्स्ट हेरफेर और दस्तावेज़ प्रसंस्करण सुविधाओं का समर्थन करती है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
