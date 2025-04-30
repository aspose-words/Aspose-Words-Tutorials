---
"description": ".NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में फ़ेंस्ड कोड और जानकारी स्ट्रिंग जोड़ना सीखें। चरण-दर-चरण मार्गदर्शिका शामिल है। अपने दस्तावेज़ स्वरूपण कौशल को बढ़ाएँ।"
"linktitle": "फेंस्ड कोड"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "फेंस्ड कोड"
"url": "/hi/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# फेंस्ड कोड

## परिचय

नमस्ते, साथी कोडर! आज, हम .NET के लिए Aspose.Words की दुनिया में गोता लगा रहे हैं ताकि आपके Word दस्तावेज़ों में फ़ेंस्ड कोड और फ़ेंस्ड कोड को जानकारी स्ट्रिंग के साथ जोड़ने की कला में महारत हासिल की जा सके। अपने Word दस्तावेज़ को एक कैनवास के रूप में कल्पना करें, और आप, कलाकार, एक अनुभवी डेवलपर की सटीकता के साथ पेंट करने वाले हैं। Aspose.Words के साथ, आपको संरचित, स्वरूपित कोड ब्लॉक के साथ अपने दस्तावेज़ों को प्रोग्रामेटिक रूप से बढ़ाने की शक्ति मिलती है, जिससे आपके तकनीकी दस्तावेज़ व्यावसायिकता और स्पष्टता के साथ चमकते हैं।

## आवश्यक शर्तें

ट्यूटोरियल में जाने से पहले, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

- C# का बुनियादी ज्ञान: C# की सामान्य समझ आपको अवधारणाओं को शीघ्रता से समझने में मदद करेगी।
- Aspose.Words for .NET: आपके पास Aspose.Words for .NET इंस्टॉल होना चाहिए। अगर आपके पास अभी तक यह नहीं है, तो इसे ले लें [यहाँ](https://releases.aspose.com/words/net/).
- विकास वातावरण: विजुअल स्टूडियो या कोई अन्य C# IDE जिससे आप सहज हों।

## नामस्थान आयात करें

सबसे पहले, आपको आवश्यक नेमस्पेस आयात करने की आवश्यकता है। यह किसी प्रोजेक्ट को शुरू करने से पहले अपने सभी उपकरण इकट्ठा करने जैसा है।

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

अब, आइये इस प्रक्रिया को चरण दर चरण समझें।

## चरण 1: अपना प्रोजेक्ट सेट अप करना

इससे पहले कि हम अपने वर्ड दस्तावेज़ में सुंदर, प्रारूपित कोड ब्लॉक बना सकें, हमें विजुअल स्टूडियो में एक नया प्रोजेक्ट सेट अप करना होगा।

1. नया प्रोजेक्ट बनाएं: Visual Studio खोलें और एक नया C# कंसोल अनुप्रयोग बनाएं।
2. Aspose.Words संदर्भ जोड़ें: NuGet पैकेज मैनेजर के माध्यम से Aspose.Words स्थापित करें। आप समाधान एक्सप्लोरर में अपने प्रोजेक्ट पर राइट-क्लिक करके, "Manage NuGet Packages" का चयन करके और Aspose.Words खोज कर ऐसा कर सकते हैं।

## चरण 2: डॉक्यूमेंटबिल्डर को आरंभ करें

अब जब आपका प्रोजेक्ट सेट हो गया है, तो चलिए डॉक्यूमेंटबिल्डर को आरंभ करते हैं, जो वर्ड डॉक्यूमेंट में सामग्री जोड़ने के लिए हमारा मुख्य उपकरण होगा।

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## चरण 3: फेंस्ड कोड के लिए एक शैली बनाएं

फेंस्ड कोड जोड़ने के लिए, हमें सबसे पहले एक स्टाइल बनाना होगा। इसे हमारे कोड ब्लॉक के लिए थीम सेट करने के रूप में सोचें।

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## चरण 4: दस्तावेज़ में फ़ेंस्ड कोड जोड़ें

हमारी शैली तैयार होने के साथ, अब हम दस्तावेज़ में एक फेंस्ड कोड ब्लॉक जोड़ सकते हैं।

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## चरण 5: जानकारी स्ट्रिंग के साथ फेंस्ड कोड के लिए एक शैली बनाएं

कभी-कभी, आप प्रोग्रामिंग भाषा निर्दिष्ट करना चाहते हैं या अपने कोड ब्लॉक में अतिरिक्त जानकारी जोड़ना चाहते हैं। आइए इसके लिए एक शैली बनाएं।

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## चरण 6: दस्तावेज़ में जानकारी स्ट्रिंग के साथ फ़ेंस्ड कोड जोड़ें

अब, आइए एक फेंस्ड कोड ब्लॉक को एक सूचना स्ट्रिंग के साथ जोड़ें जो यह इंगित करे कि यह C# कोड है।

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## निष्कर्ष

बधाई हो! आपने अभी-अभी Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में फ़ेंस्ड कोड ब्लॉक और फ़ेंस्ड कोड विद इन्फो स्ट्रिंग्स जोड़े हैं। यह तो बस शुरुआत है। Aspose.Words के साथ, आप अपने दस्तावेज़ प्रसंस्करण को नई ऊंचाइयों तक स्वचालित और उन्नत कर सकते हैं। खोज करते रहें और कोडिंग का आनंद लें!

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
.NET के लिए Aspose.Words एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ों को बनाने, हेरफेर करने और परिवर्तित करने की अनुमति देती है।

### क्या मैं अन्य प्रोग्रामिंग भाषाओं के साथ Aspose.Words का उपयोग कर सकता हूँ?
Aspose.Words मुख्यतः .NET भाषाओं का समर्थन करता है, लेकिन Java, Python और अन्य भाषाओं के लिए भी इसके संस्करण उपलब्ध हैं।

### क्या Aspose.Words का उपयोग निःशुल्क है?
Aspose.Words एक वाणिज्यिक उत्पाद है, लेकिन आप एक निःशुल्क परीक्षण डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/) इसकी विशेषताओं का पता लगाने के लिए।

### मैं Aspose.Words के लिए समर्थन कैसे प्राप्त कर सकता हूं?
आप Aspose समुदाय और डेवलपर्स से सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.aspose.com/c/words/8).

### Aspose.Words क्या अन्य सुविधाएँ प्रदान करता है?
Aspose.Words दस्तावेज़ रूपांतरण, टेम्पलेट-आधारित दस्तावेज़ निर्माण, रिपोर्टिंग और बहुत कुछ सहित सुविधाओं की एक विस्तृत श्रृंखला प्रदान करता है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}