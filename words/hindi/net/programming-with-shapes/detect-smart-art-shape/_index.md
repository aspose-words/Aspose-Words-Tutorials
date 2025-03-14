---
title: स्मार्ट आर्ट आकार का पता लगाएं
linktitle: स्मार्ट आर्ट आकार का पता लगाएं
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस व्यापक गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में SmartArt आकृतियों का पता लगाना सीखें। आपके दस्तावेज़ वर्कफ़्लो को स्वचालित करने के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-shapes/detect-smart-art-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# स्मार्ट आर्ट आकार का पता लगाएं


## परिचय

नमस्ते! क्या आपको कभी Word दस्तावेज़ों में SmartArt के साथ प्रोग्रामेटिक रूप से काम करने की ज़रूरत पड़ी है? चाहे आप रिपोर्ट को स्वचालित कर रहे हों, गतिशील दस्तावेज़ बना रहे हों, या दस्तावेज़ प्रसंस्करण में गोता लगा रहे हों, Aspose.Words for .NET आपके लिए है। इस ट्यूटोरियल में, हम Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में SmartArt आकृतियों का पता लगाने का तरीका जानेंगे। हम प्रत्येक चरण को विस्तृत, आसानी से पालन करने वाली मार्गदर्शिका में विभाजित करेंगे। इस लेख के अंत तक, आप किसी भी Word दस्तावेज़ में SmartArt आकृतियों को आसानी से पहचान सकेंगे!

## आवश्यक शर्तें

इससे पहले कि हम विस्तार में जाएं, आइए सुनिश्चित करें कि आपने सब कुछ सेट कर लिया है:

1. C# का बुनियादी ज्ञान: आपको C# सिंटैक्स और अवधारणाओं से परिचित होना चाहिए।
2.  .NET के लिए Aspose.Words: इसे डाउनलोड करें[यहाँ](https://releases.aspose.com/words/net/) यदि आप सिर्फ खोज कर रहे हैं, तो आप एक से शुरू कर सकते हैं[मुफ्त परीक्षण](https://releases.aspose.com/).
3. विजुअल स्टूडियो: कोई भी नवीनतम संस्करण काम करेगा, लेकिन नवीनतम संस्करण अनुशंसित है।
4. .NET फ्रेमवर्क: सुनिश्चित करें कि यह आपके सिस्टम पर स्थापित है।

शुरू करने के लिए तैयार हैं? बहुत बढ़िया! चलिए शुरू करते हैं।

## नामस्थान आयात करें

शुरू करने के लिए, हमें आवश्यक नेमस्पेस को आयात करना होगा। यह कदम महत्वपूर्ण है क्योंकि यह उन क्लासेस और विधियों तक पहुँच प्रदान करता है जिनका हम उपयोग करेंगे।

```csharp
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

ये नामस्थान Word दस्तावेज़ों को बनाने, उनमें हेरफेर करने और उनका विश्लेषण करने के लिए आवश्यक हैं।

## चरण 1: दस्तावेज़ निर्देशिका सेट अप करना

सबसे पहले, हमें उस निर्देशिका को निर्दिष्ट करने की आवश्यकता है जहाँ हमारे दस्तावेज़ संग्रहीत हैं। इससे Aspose.Words को उन फ़ाइलों का पता लगाने में मदद मिलती है जिनका हम विश्लेषण करना चाहते हैं।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` आपके दस्तावेज़ों के वास्तविक पथ के साथ.

## चरण 2: दस्तावेज़ लोड करना

इसके बाद, हम Word दस्तावेज़ को लोड करेंगे जिसमें वे स्मार्टआर्ट आकृतियाँ होंगी जिन्हें हम पहचानना चाहते हैं।

```csharp
Document doc = new Document(dataDir + "Smart Art.docx");
```

 यहाँ, हम एक आरंभीकरण करते हैं`Document` ऑब्जेक्ट को हमारे वर्ड फ़ाइल के पथ के साथ जोड़ें।

## चरण 3: स्मार्टआर्ट आकृतियों का पता लगाना

अब रोमांचक हिस्सा आता है - दस्तावेज़ में स्मार्टआर्ट आकृतियों का पता लगाना। हम उन आकृतियों की संख्या गिनेंगे जिनमें स्मार्टआर्ट शामिल है।

```csharp
int count = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().Count(shape => shape.HasSmartArt);

Console.WriteLine("The document has {0} shapes with SmartArt.", count);
```

 इस चरण में, हम स्मार्टआर्ट वाले आकृतियों को फ़िल्टर करने और गिनने के लिए LINQ का उपयोग करते हैं।`GetChildNodes` विधि सभी आकृतियों को पुनः प्राप्त करती है, और`HasSmartArt` प्रॉपर्टी यह जांचती है कि आकृति में स्मार्टआर्ट है या नहीं।

## चरण 4: कोड चलाना

एक बार जब आप कोड लिख लें, तो उसे Visual Studio में चलाएँ। कंसोल दस्तावेज़ में पाए गए SmartArt आकृतियों की संख्या प्रदर्शित करेगा।

```plaintext
The document has X shapes with SmartArt.
```

अपने दस्तावेज़ में "X" को स्मार्टआर्ट आकृतियों की वास्तविक संख्या से प्रतिस्थापित करें।

## निष्कर्ष

और अब यह हो गया! आपने सफलतापूर्वक सीख लिया है कि .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में SmartArt आकृतियों का पता कैसे लगाया जाए। इस ट्यूटोरियल में आपके वातावरण को सेट करना, दस्तावेज़ लोड करना, SmartArt आकृतियों का पता लगाना और कोड चलाना शामिल है। Aspose.Words कई तरह की सुविधाएँ प्रदान करता है, इसलिए इसे अवश्य देखें[एपीआई दस्तावेज़ीकरण](https://reference.aspose.com/words/net/) इसकी पूरी क्षमता को अनलॉक करने के लिए।

## पूछे जाने वाले प्रश्न

### 1. .NET के लिए Aspose.Words क्या है?

Aspose.Words for .NET एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, हेरफेर करने और परिवर्तित करने की अनुमति देती है। यह दस्तावेज़-संबंधित कार्यों को स्वचालित करने के लिए आदर्श है।

### 2. क्या मैं .NET के लिए Aspose.Words का निःशुल्क उपयोग कर सकता हूँ?

 आप .NET के लिए Aspose.Words का उपयोग करके प्रयास कर सकते हैं[मुफ्त परीक्षण](https://releases.aspose.com/)दीर्घकालिक उपयोग के लिए, आपको लाइसेंस खरीदना होगा।

### 3. मैं किसी दस्तावेज़ में अन्य प्रकार की आकृतियों का पता कैसे लगा सकता हूँ?

 आप आकृतियों के अन्य गुणों या प्रकारों की जाँच करने के लिए LINQ क्वेरी को संशोधित कर सकते हैं।[प्रलेखन](https://reference.aspose.com/words/net/) अधिक जानकारी के लिए.

### 4. मैं .NET के लिए Aspose.Words का समर्थन कैसे प्राप्त करूं?

 आप यहां जाकर सहायता प्राप्त कर सकते हैं[Aspose समर्थन मंच](https://forum.aspose.com/c/words/8).

### 5. क्या मैं स्मार्टआर्ट आकृतियों को प्रोग्रामेटिक रूप से परिवर्तित कर सकता हूँ?

 हां, Aspose.Words आपको प्रोग्रामेटिक रूप से SmartArt आकृतियों में हेरफेर करने की अनुमति देता है।[प्रलेखन](https://reference.aspose.com/words/net/) विस्तृत निर्देशों के लिए कृपया देखें.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
