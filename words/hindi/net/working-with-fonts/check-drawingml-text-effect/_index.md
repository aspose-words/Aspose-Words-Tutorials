---
"description": "हमारे विस्तृत, चरण-दर-चरण गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में DrawingML टेक्स्ट प्रभाव की जाँच करना सीखें। अपने दस्तावेज़ों को आसानी से बेहतर बनाएँ।"
"linktitle": "DrawingML टेक्स्ट प्रभाव की जाँच करें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "DrawingML टेक्स्ट प्रभाव की जाँच करें"
"url": "/hi/net/working-with-fonts/check-drawingml-text-effect/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DrawingML टेक्स्ट प्रभाव की जाँच करें

## परिचय

Aspose.Words for .NET के साथ काम करने पर एक और विस्तृत ट्यूटोरियल में आपका स्वागत है! आज, हम DrawingML टेक्स्ट इफ़ेक्ट की आकर्षक दुनिया में गोता लगा रहे हैं। चाहे आप अपने Word दस्तावेज़ों को छाया, प्रतिबिंब या 3D इफ़ेक्ट के साथ बढ़ाना चाहते हों, यह गाइड आपको दिखाएगा कि Aspose.Words for .NET का उपयोग करके अपने दस्तावेज़ों में इन टेक्स्ट इफ़ेक्ट की जाँच कैसे करें। चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम ट्यूटोरियल में आगे बढ़ें, कुछ पूर्व-आवश्यकताएं हैं जो आपके पास होनी चाहिए:

- Aspose.Words for .NET लाइब्रेरी: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी स्थापित है। आप इसे यहाँ से डाउनलोड कर सकते हैं [Aspose रिलीज़ पेज](https://releases.aspose.com/words/net/).
- विकास परिवेश: आपके पास एक विकास परिवेश स्थापित होना चाहिए, जैसे कि विजुअल स्टूडियो।
- C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से कुछ परिचित होना उपयोगी होगा।

## नामस्थान आयात करें

सबसे पहले, आपको आवश्यक नेमस्पेस आयात करने की आवश्यकता है। ये नेमस्पेस आपको वर्ड दस्तावेज़ों में हेरफेर करने और DrawingML टेक्स्ट प्रभावों की जांच करने के लिए आवश्यक कक्षाओं और विधियों तक पहुंच प्रदान करेंगे।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## DrawingML टेक्स्ट प्रभाव की जांच करने के लिए चरण-दर-चरण मार्गदर्शिका

अब, आइए इस प्रक्रिया को कई चरणों में विभाजित करें, जिससे इसका अनुसरण करना आसान हो जाए।

## चरण 1: दस्तावेज़ लोड करें

पहला चरण उस वर्ड दस्तावेज़ को लोड करना है जिसे आप DrawingML टेक्स्ट प्रभावों के लिए जांचना चाहते हैं। 

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

यह कोड स्निपेट आपकी निर्दिष्ट निर्देशिका से "DrawingML text effects.docx" नामक दस्तावेज़ लोड करता है।

## चरण 2: रन संग्रह तक पहुंचें

इसके बाद, हमें दस्तावेज़ के पहले पैराग्राफ़ में रन के संग्रह तक पहुँचने की ज़रूरत है। रन एक ही फ़ॉर्मेटिंग वाले टेक्स्ट के हिस्से होते हैं।

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

कोड की यह पंक्ति दस्तावेज़ के प्रथम खंड के प्रथम पैराग्राफ से रन्स को पुनः प्राप्त करती है।

## चरण 3: पहले रन का फ़ॉन्ट प्राप्त करें

अब, हमें रन कलेक्शन में पहले रन के फ़ॉन्ट गुण मिलेंगे। यह हमें टेक्स्ट पर लागू विभिन्न DrawingML टेक्स्ट प्रभावों की जांच करने की अनुमति देता है।

```csharp
Font runFont = runs[0].Font;
```

## चरण 4: DrawingML टेक्स्ट प्रभाव की जाँच करें

अंत में, हम विभिन्न DrawingML टेक्स्ट प्रभावों जैसे छाया, 3D प्रभाव, प्रतिबिंब, रूपरेखा और भरण की जांच कर सकते हैं।

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

कोड की ये पंक्तियाँ प्रिंट होंगी `true` या `false` यह इस बात पर निर्भर करता है कि प्रत्येक विशिष्ट DrawingML पाठ प्रभाव रन के फ़ॉन्ट पर लागू किया गया है या नहीं।

## निष्कर्ष

बधाई हो! आपने अभी सीखा है कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में DrawingML टेक्स्ट प्रभावों की जाँच कैसे करें। यह शक्तिशाली सुविधा आपको प्रोग्रामेटिक रूप से परिष्कृत टेक्स्ट फ़ॉर्मेटिंग का पता लगाने और उसमें हेरफेर करने की अनुमति देती है, जिससे आपको अपने दस्तावेज़ प्रसंस्करण कार्यों पर अधिक नियंत्रण मिलता है।


## अक्सर पूछे जाने वाले प्रश्न

### DrawingML टेक्स्ट प्रभाव क्या है?
DrawingML टेक्स्ट प्रभाव, Word दस्तावेज़ों में उन्नत टेक्स्ट फ़ॉर्मेटिंग विकल्प हैं, जिनमें छाया, 3D प्रभाव, प्रतिबिंब, रूपरेखा और भरण शामिल हैं।

### क्या मैं .NET के लिए Aspose.Words का उपयोग करके DrawingML टेक्स्ट प्रभाव लागू कर सकता हूं?
हां, .NET के लिए Aspose.Words आपको DrawingML टेक्स्ट प्रभावों की जांच करने और उन्हें प्रोग्रामेटिक रूप से लागू करने की अनुमति देता है।

### क्या मुझे .NET के लिए Aspose.Words का उपयोग करने के लिए लाइसेंस की आवश्यकता है?
हां, Aspose.Words for .NET को पूर्ण कार्यक्षमता के लिए लाइसेंस की आवश्यकता है। आप एक प्राप्त कर सकते हैं [अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) मूल्यांकन हेतु.

### क्या .NET के लिए Aspose.Words का निःशुल्क परीक्षण उपलब्ध है?
हां, आप डाउनलोड कर सकते हैं [मुफ्त परीक्षण](https://releases.aspose.com/) खरीदने से पहले Aspose.Words for .NET को अवश्य आज़माएँ।

### मैं .NET के लिए Aspose.Words पर अधिक दस्तावेज़ कहां पा सकता हूं?
आप विस्तृत दस्तावेज यहाँ पा सकते हैं [.NET के लिए Aspose.Words प्रलेखन पृष्ठ](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}