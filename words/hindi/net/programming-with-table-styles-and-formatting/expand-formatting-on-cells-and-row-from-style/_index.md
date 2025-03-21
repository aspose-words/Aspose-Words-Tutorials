---
title: शैली से कक्षों और पंक्तियों पर स्वरूपण का विस्तार करें
linktitle: शैली से कक्षों और पंक्तियों पर स्वरूपण का विस्तार करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में शैलियों से कक्षों और पंक्तियों पर स्वरूपण का विस्तार करना सीखें। चरण-दर-चरण मार्गदर्शिका शामिल है।
weight: 10
url: /hi/net/programming-with-table-styles-and-formatting/expand-formatting-on-cells-and-row-from-style/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# शैली से कक्षों और पंक्तियों पर स्वरूपण का विस्तार करें

## परिचय

क्या आपको कभी अपने Word दस्तावेज़ों में तालिकाओं में एकसमान स्टाइलिंग लागू करने की ज़रूरत महसूस हुई है? प्रत्येक सेल को मैन्युअल रूप से समायोजित करना थकाऊ और त्रुटियों से भरा हो सकता है। यहीं पर Aspose.Words for .NET काम आता है। यह ट्यूटोरियल आपको टेबल स्टाइल से सेल और पंक्तियों पर फ़ॉर्मेटिंग का विस्तार करने की प्रक्रिया के माध्यम से मार्गदर्शन करेगा, यह सुनिश्चित करते हुए कि आपके दस्तावेज़ बिना किसी अतिरिक्त परेशानी के पॉलिश और पेशेवर दिखें।

## आवश्यक शर्तें

इससे पहले कि हम विस्तृत विवरण में जाएं, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें मौजूद हैं:

-  .NET के लिए Aspose.Words: आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).
- विजुअल स्टूडियो: कोई भी नवीनतम संस्करण काम करेगा।
- C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होना आवश्यक है।
- नमूना दस्तावेज़: एक तालिका सहित एक वर्ड दस्तावेज़ तैयार रखें, या आप कोड उदाहरण में दिए गए तालिका का उपयोग कर सकते हैं।

## नामस्थान आयात करें

सबसे पहले, आइए आवश्यक नेमस्पेस को आयात करें। यह सुनिश्चित करेगा कि हमारे कोड में उपयोग के लिए सभी आवश्यक क्लास और मेथड उपलब्ध हैं।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

अब, आइये इस प्रक्रिया को सरल एवं आसान चरणों में विभाजित करें।

## चरण 1: अपना दस्तावेज़ लोड करें

इस चरण में, हम उस Word दस्तावेज़ को लोड करेंगे जिसमें वह तालिका है जिसे आप फ़ॉर्मेट करना चाहते हैं। 

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

## चरण 2: टेबल तक पहुंचें

इसके बाद, हमें दस्तावेज़ में पहली तालिका तक पहुँचने की आवश्यकता है। यह तालिका हमारे स्वरूपण कार्यों का केंद्र होगी।

```csharp
// दस्तावेज़ में पहली तालिका प्राप्त करें.
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## चरण 3: पहला सेल पुनः प्राप्त करें

अब, आइए तालिका में पहली पंक्ति के पहले सेल को पुनः प्राप्त करें। इससे हमें यह प्रदर्शित करने में मदद मिलेगी कि जब शैलियाँ विस्तारित होती हैं तो सेल का स्वरूपण कैसे बदलता है।

```csharp
// तालिका में पहली पंक्ति का पहला कक्ष प्राप्त करें।
Cell firstCell = table.FirstRow.FirstCell;
```

## चरण 4: आरंभिक सेल शेडिंग की जाँच करें

किसी भी फ़ॉर्मेटिंग को लागू करने से पहले, आइए सेल के शुरुआती शेडिंग रंग की जाँच करें और उसे प्रिंट करें। यह हमें स्टाइल विस्तार के बाद तुलना करने के लिए एक आधार रेखा देगा।

```csharp
// प्रारंभिक सेल शेडिंग रंग प्रिंट करें.
Color cellShadingBefore = firstCell.CellFormat.Shading.BackgroundPatternColor;
Console.WriteLine("Cell shading before style expansion: " + cellShadingBefore);
```

## चरण 5: तालिका शैलियाँ विस्तृत करें

 यहीं पर जादू होता है। हम इसे कॉल करेंगे`ExpandTableStylesToDirectFormatting` तालिका शैलियों को सीधे कक्षों पर लागू करने की विधि।

```csharp
// तालिका शैलियों को प्रत्यक्ष स्वरूपण में विस्तारित करें.
doc.ExpandTableStylesToDirectFormatting();
```

## चरण 6: अंतिम सेल शेडिंग की जाँच करें

अंत में, हम स्टाइल्स को विस्तारित करने के बाद सेल के शेडिंग रंग की जांच करेंगे और उसे प्रिंट करेंगे। आपको टेबल स्टाइल से लागू अपडेटेड फ़ॉर्मेटिंग दिखनी चाहिए।

```csharp
// शैली विस्तार के बाद सेल शेडिंग रंग प्रिंट करें।
Color cellShadingAfter = firstCell.CellFormat.Shading.BackgroundPatternColor;
Console.WriteLine("Cell shading after style expansion: " + cellShadingAfter);
```

## निष्कर्ष

और अब यह हो गया! इन चरणों का पालन करके, आप आसानी से Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में शैलियों से कक्षों और पंक्तियों पर स्वरूपण का विस्तार कर सकते हैं। यह न केवल समय बचाता है बल्कि आपके दस्तावेज़ों में एकरूपता भी सुनिश्चित करता है। हैप्पी कोडिंग!

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
.NET के लिए Aspose.Words एक शक्तिशाली API है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ों को बनाने, संपादित करने, परिवर्तित करने और हेरफेर करने में सक्षम बनाता है।

### मुझे शैलियों से स्वरूपण का विस्तार करने की आवश्यकता क्यों होगी?
शैलियों से स्वरूपण का विस्तार करने से यह सुनिश्चित होता है कि स्टाइलिंग सीधे कोशिकाओं पर लागू होती है, जिससे दस्तावेज़ को बनाए रखना और अद्यतन करना आसान हो जाता है।

### क्या मैं इन चरणों को एक दस्तावेज़ में एकाधिक तालिकाओं पर लागू कर सकता हूँ?
बिल्कुल! आप अपने दस्तावेज़ में सभी तालिकाओं को लूप कर सकते हैं और प्रत्येक पर समान चरण लागू कर सकते हैं।

### क्या विस्तारित शैलियों को वापस लाने का कोई तरीका है?
एक बार जब शैलियाँ विस्तारित हो जाती हैं, तो वे सीधे कोशिकाओं पर लागू होती हैं। वापस लौटने के लिए, आपको दस्तावेज़ को फिर से लोड करना होगा या शैलियों को मैन्युअल रूप से फिर से लागू करना होगा।

### क्या यह विधि .NET के लिए Aspose.Words के सभी संस्करणों के साथ काम करती है?
 हां`ExpandTableStylesToDirectFormatting` विधि Aspose.Words for .NET के हाल के संस्करणों में उपलब्ध है। हमेशा जाँच करें[प्रलेखन](https://reference.aspose.com/words/net/) नवीनतम अपडेट के लिए.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
