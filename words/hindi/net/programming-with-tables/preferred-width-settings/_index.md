---
title: पसंदीदा चौड़ाई सेटिंग्स
linktitle: पसंदीदा चौड़ाई सेटिंग्स
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words में निरपेक्ष, सापेक्ष और स्वचालित चौड़ाई सेटिंग्स के साथ तालिकाएँ बनाना सीखें।
weight: 10
url: /hi/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# पसंदीदा चौड़ाई सेटिंग्स

## परिचय

टेबल आपके वर्ड दस्तावेज़ों में जानकारी को व्यवस्थित करने और प्रस्तुत करने का एक शक्तिशाली तरीका है। Aspose.Words for .NET में टेबल के साथ काम करते समय, आपके पास टेबल सेल की चौड़ाई सेट करने के लिए कई विकल्प होते हैं ताकि यह सुनिश्चित हो सके कि वे आपके दस्तावेज़ के लेआउट में पूरी तरह से फिट हों। यह गाइड आपको Aspose.Words for .NET का उपयोग करके पसंदीदा चौड़ाई सेटिंग्स के साथ टेबल बनाने की प्रक्रिया से गुजारेगी, जिसमें निरपेक्ष, सापेक्ष और स्वचालित आकार विकल्पों पर ध्यान केंद्रित किया जाएगा। 

## आवश्यक शर्तें

ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  Aspose.Words for .NET: सुनिश्चित करें कि आपके विकास परिवेश में Aspose.Words for .NET स्थापित है। आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).

2. .NET विकास वातावरण: Visual Studio जैसे .NET विकास वातावरण की स्थापना करें।

3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होने से आपको कोड स्निपेट और उदाहरणों को बेहतर ढंग से समझने में मदद मिलेगी।

4.  Aspose.Words दस्तावेज़ीकरण: देखें[Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/net/) विस्तृत API जानकारी और आगे पढ़ने के लिए.

## नामस्थान आयात करें

कोडिंग शुरू करने से पहले, आपको अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करने होंगे:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

ये नामस्थान Aspose.Words और टेबल ऑब्जेक्ट की मुख्य कार्यात्मकताओं तक पहुंच प्रदान करते हैं, जिससे आप दस्तावेज़ तालिकाओं में हेरफेर कर सकते हैं।

आइए विभिन्न पसंदीदा चौड़ाई सेटिंग्स के साथ तालिका बनाने की प्रक्रिया को स्पष्ट, प्रबंधनीय चरणों में विभाजित करें।

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

शीर्षक: नया दस्तावेज़ और दस्तावेज़बिल्डर बनाना

 स्पष्टीकरण: एक नया वर्ड दस्तावेज़ बनाकर शुरू करें और`DocumentBuilder` उदाहरण.`DocumentBuilder` क्लास आपके दस्तावेज़ में सामग्री जोड़ने का एक सरल तरीका प्रदान करता है।

```csharp
// दस्तावेज़ को सहेजने के लिए पथ निर्धारित करें.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// एक नया दस्तावेज़ बनाएँ.
Document doc = new Document();

// इस दस्तावेज़ के लिए एक दस्तावेज़बिल्डर बनाएँ.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 यहां, आप वह निर्देशिका निर्दिष्ट करते हैं जहां दस्तावेज़ सहेजा जाएगा और प्रारंभ किया जाएगा`Document` और`DocumentBuilder` वस्तुएं.

## चरण 2: पूर्ण चौड़ाई के साथ पहला टेबल सेल डालें

तालिका में पहले सेल को 40 पॉइंट की निश्चित चौड़ाई के साथ डालें। इससे यह सुनिश्चित होगा कि तालिका के आकार की परवाह किए बिना यह सेल हमेशा 40 पॉइंट की चौड़ाई बनाए रखेगा।

```csharp
// एक पूर्ण आकार का सेल डालें.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

इस चरण में, आप तालिका बनाना शुरू करते हैं और एक पूर्ण चौड़ाई वाला सेल सम्मिलित करते हैं।`PreferredWidth.FromPoints(40)` विधि सेल की चौड़ाई 40 पॉइंट पर सेट करती है, और`Shading.BackgroundPatternColor` एक हल्का पीला पृष्ठभूमि रंग लागू करता है.

## चरण 3: सापेक्ष आकार का सेल डालें

तालिका की कुल चौड़ाई का 20% चौड़ाई वाला एक और सेल डालें। यह सापेक्ष आकार सुनिश्चित करता है कि सेल तालिका की चौड़ाई के अनुपात में समायोजित हो।

```csharp
// सापेक्ष (प्रतिशत) आकार का सेल डालें.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

इस सेल की चौड़ाई तालिका की कुल चौड़ाई की 20% होगी, जिससे इसे विभिन्न स्क्रीन आकारों या दस्तावेज़ लेआउट के अनुकूल बनाया जा सकेगा।

### चरण 4: एक ऑटो आकार सेल डालें

अंत में, एक सेल डालें जो तालिका में शेष उपलब्ध स्थान के आधार पर अपने आप अपना आकार निर्धारित कर ले।

```csharp
// एक स्वतः आकारित सेल डालें.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

`PreferredWidth.Auto` सेटिंग इस सेल को अन्य सेल के हिसाब से बची हुई जगह के आधार पर विस्तार या संकुचन करने की अनुमति देती है। यह सुनिश्चित करता है कि टेबल लेआउट संतुलित और पेशेवर दिखे।

## चरण 5: दस्तावेज़ को अंतिम रूप दें और सहेजें

एक बार जब आप अपनी सभी कोशिकाएं सम्मिलित कर लें, तो तालिका को पूरा करें और दस्तावेज़ को अपने निर्दिष्ट पथ पर सहेजें।

```csharp
// दस्तावेज़ सहेजें.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

यह चरण तालिका को अंतिम रूप देता है और दस्तावेज़ को "WorkingWithTables.PreferredWidthSettings.docx" फ़ाइल नाम के साथ आपकी निर्दिष्ट निर्देशिका में सहेजता है।

## निष्कर्ष

Aspose.Words for .NET में पसंदीदा चौड़ाई सेटिंग के साथ टेबल बनाना एक बार जब आप उपलब्ध विभिन्न आकार विकल्पों को समझ लेते हैं तो यह बहुत आसान हो जाता है। चाहे आपको निश्चित, सापेक्ष या स्वचालित सेल चौड़ाई की आवश्यकता हो, Aspose.Words विभिन्न टेबल लेआउट परिदृश्यों को कुशलतापूर्वक संभालने के लिए लचीलापन प्रदान करता है। इस गाइड में बताए गए चरणों का पालन करके, आप यह सुनिश्चित कर सकते हैं कि आपकी टेबल आपके Word दस्तावेज़ों में अच्छी तरह से संरचित और दिखने में आकर्षक हों।

## अक्सर पूछे जाने वाले प्रश्न

### निरपेक्ष और सापेक्ष सेल चौड़ाई के बीच क्या अंतर है?
पूर्ण कक्ष चौड़ाई निश्चित होती है और बदलती नहीं है, जबकि सापेक्ष चौड़ाई तालिका की कुल चौड़ाई के आधार पर समायोजित होती है।

### क्या मैं सापेक्ष चौड़ाई के लिए ऋणात्मक प्रतिशत का उपयोग कर सकता हूँ?
नहीं, सेल की चौड़ाई के लिए नकारात्मक प्रतिशत मान्य नहीं हैं। केवल सकारात्मक प्रतिशत की अनुमति है।

### ऑटो साइज़िंग सुविधा कैसे काम करती है?
स्वचालित आकार निर्धारण, अन्य कक्षों के आकार निर्धारण के बाद तालिका में शेष बचे स्थान को भरने के लिए कक्ष की चौड़ाई को समायोजित करता है।

### क्या मैं अलग-अलग चौड़ाई सेटिंग वाले कक्षों पर अलग-अलग शैलियाँ लागू कर सकता हूँ?
हां, आप कक्षों पर उनकी चौड़ाई सेटिंग की परवाह किए बिना विभिन्न शैलियाँ और स्वरूपण लागू कर सकते हैं।

### यदि तालिका की कुल चौड़ाई सभी कक्षों की चौड़ाई के योग से कम है तो क्या होगा?
तालिका उपलब्ध स्थान में फिट होने के लिए कोशिकाओं की चौड़ाई को स्वचालित रूप से समायोजित कर देगी, जिसके कारण कुछ कोशिकाएं छोटी हो सकती हैं।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
