---
title: स्टाइल के साथ टेबल बनाएं
linktitle: स्टाइल के साथ टेबल बनाएं
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस व्यापक चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में तालिकाओं को बनाने और स्टाइल करने का तरीका जानें।
weight: 10
url: /hi/net/programming-with-table-styles-and-formatting/build-table-with-style/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# स्टाइल के साथ टेबल बनाएं

## परिचय

स्टाइलिश, पेशेवर दस्तावेज़ बनाने के लिए अक्सर सादे टेक्स्ट से ज़्यादा की ज़रूरत होती है। टेबल डेटा को व्यवस्थित करने का एक शानदार तरीका है, लेकिन उन्हें आकर्षक बनाना एक पूरी तरह से अलग चुनौती है। .NET के लिए Aspose.Words दर्ज करें! इस ट्यूटोरियल में, हम स्टाइल के साथ टेबल बनाने के तरीके के बारे में जानेंगे, जिससे आपके वर्ड दस्तावेज़ पॉलिश और पेशेवर दिखेंगे।

## आवश्यक शर्तें

इससे पहले कि हम चरण-दर-चरण मार्गदर्शिका में आगे बढ़ें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

1.  .NET के लिए Aspose.Words: यदि आपने पहले से ऐसा नहीं किया है, तो डाउनलोड करें और इंस्टॉल करें[.NET के लिए Aspose.Words](https://releases.aspose.com/words/net/).
2. विकास पर्यावरण: आपके पास एक विकास पर्यावरण स्थापित होना चाहिए। इस ट्यूटोरियल के लिए विज़ुअल स्टूडियो एक बढ़िया विकल्प है।
3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होने से आपको अधिक आसानी से अनुसरण करने में मदद मिलेगी।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको आवश्यक नामस्थान आयात करने की आवश्यकता है। इससे आपको Word दस्तावेज़ों में हेरफेर करने के लिए आवश्यक क्लास और विधियों तक पहुँच मिलेगी।

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## चरण 1: नया दस्तावेज़ और दस्तावेज़बिल्डर बनाएँ

 सबसे पहली बात, आपको एक नया दस्तावेज़ बनाना होगा और`DocumentBuilder` वस्तु. यह`DocumentBuilder` आपके दस्तावेज़ में तालिका बनाने में आपकी सहायता करेगा.

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: तालिका बनाना शुरू करें

अब जबकि हमारा दस्तावेज़ और बिल्डर तैयार है, तो चलिए तालिका बनाना शुरू करते हैं।

```csharp
Table table = builder.StartTable();
```

## चरण 3: पहली पंक्ति डालें

पंक्तियों के बिना एक तालिका बस एक खाली संरचना है। किसी भी तालिका स्वरूपण को सेट करने से पहले हमें कम से कम एक पंक्ति सम्मिलित करने की आवश्यकता है।

```csharp
builder.InsertCell();
```

## चरण 4: तालिका शैली सेट करें

 पहला सेल डालने के बाद, अब हमारी टेबल में कुछ स्टाइल जोड़ने का समय आ गया है। हम इसका इस्तेमाल करेंगे`StyleIdentifier` पूर्वनिर्धारित शैली लागू करने के लिए.

```csharp
// अद्वितीय शैली पहचानकर्ता के आधार पर प्रयुक्त तालिका शैली सेट करें
table.StyleIdentifier = StyleIdentifier.MediumShading1Accent1;
```

## चरण 5: शैली विकल्प परिभाषित करें

टेबल स्टाइल विकल्प यह निर्धारित करते हैं कि टेबल के किन भागों को स्टाइल किया जाएगा। उदाहरण के लिए, हम पहले कॉलम, पंक्ति बैंड और पहली पंक्ति को स्टाइल करना चुन सकते हैं।

```csharp
// कौन सी सुविधाएँ शैली के अनुसार प्रारूपित की जानी चाहिए, इसे लागू करें
table.StyleOptions = TableStyleOptions.FirstColumn | TableStyleOptions.RowBands | TableStyleOptions.FirstRow;
```

## चरण 6: सामग्री को फिट करने के लिए तालिका समायोजित करें

यह सुनिश्चित करने के लिए कि हमारी मेज साफ और सुव्यवस्थित दिखे, हम इसका उपयोग कर सकते हैं`AutoFit` तालिका को उसकी सामग्री के अनुरूप समायोजित करने की विधि।

```csharp
table.AutoFit(AutoFitBehavior.AutoFitToContents);
```

## चरण 7: तालिका में डेटा डालें

अब समय आ गया है कि हम अपनी तालिका को कुछ डेटा से भरें। हम हेडर पंक्ति से शुरू करेंगे और फिर कुछ नमूना डेटा जोड़ेंगे।

### शीर्ष पंक्ति सम्मिलित करना

```csharp
builder.Writeln("Item");
builder.CellFormat.RightPadding = 40;
builder.InsertCell();
builder.Writeln("Quantity (kg)");
builder.EndRow();
```

#### डेटा पंक्तियाँ सम्मिलित करना

```csharp
builder.InsertCell();
builder.Writeln("Apples");
builder.InsertCell();
builder.Writeln("20");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Bananas");
builder.InsertCell();
builder.Writeln("40");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Carrots");
builder.InsertCell();
builder.Writeln("50");
builder.EndRow();
```

## चरण 8: दस्तावेज़ सहेजें

सभी डेटा डालने के बाद, अंतिम चरण दस्तावेज़ को सहेजना है।

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.BuildTableWithStyle.docx");
```

## निष्कर्ष

और अब यह हो गया! आपने .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में एक स्टाइलिश टेबल सफलतापूर्वक बना ली है। यह शक्तिशाली लाइब्रेरी आपकी सटीक आवश्यकताओं को पूरा करने के लिए Word दस्तावेज़ों को स्वचालित और अनुकूलित करना आसान बनाती है। चाहे आप रिपोर्ट, चालान या किसी अन्य प्रकार का दस्तावेज़ बना रहे हों, Aspose.Words आपके लिए है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को C# का उपयोग करके प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संपादित करने और हेरफेर करने की अनुमति देती है।

### क्या मैं मौजूदा तालिकाओं को स्टाइल करने के लिए Aspose.Words for .NET का उपयोग कर सकता हूँ?
हां, .NET के लिए Aspose.Words का उपयोग आपके Word दस्तावेज़ों में नई और मौजूदा दोनों तालिकाओं को स्टाइल करने के लिए किया जा सकता है।

### क्या मुझे .NET के लिए Aspose.Words का उपयोग करने के लिए लाइसेंस की आवश्यकता है?
 हां, .NET के लिए Aspose.Words को पूर्ण कार्यक्षमता के लिए लाइसेंस की आवश्यकता होती है। आप एक प्राप्त कर सकते हैं[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) या पूरा खरीदें[यहाँ](https://purchase.aspose.com/buy).

### क्या मैं .NET के लिए Aspose.Words के साथ अन्य दस्तावेज़ प्रकारों को स्वचालित कर सकता हूँ?
बिल्कुल! .NET के लिए Aspose.Words विभिन्न दस्तावेज़ प्रकारों का समर्थन करता है, जिसमें DOCX, PDF, HTML, और बहुत कुछ शामिल है।

### मैं और अधिक उदाहरण और दस्तावेज कहां पा सकता हूं?
 आप यहाँ पर विस्तृत दस्तावेज और उदाहरण पा सकते हैं।[.NET के लिए Aspose.Words दस्तावेज़न पृष्ठ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
