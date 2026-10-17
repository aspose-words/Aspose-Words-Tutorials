---
category: general
date: 2026-01-03
description: C# के साथ Word में आयताकार आकार बनाएं और आकार में छाया जोड़ें। सीखें
  कि Word में आकार कैसे डालें, आकार में छाया कैसे जोड़ें, और प्रोग्रामेटिकली Word
  दस्तावेज़ बनाएं।
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: hi
og_description: C# का उपयोग करके Word में आयताकार आकार बनाएं और आकार में छाया जोड़ें।
  Word में आकार डालने, छायाओं को कॉन्फ़िगर करने और प्रोग्रामेटिक रूप से दस्तावेज़
  बनाने के लिए इस गाइड का पालन करें।
og_title: C# का उपयोग करके Word में आयताकार आकार बनाएं – पूर्ण ट्यूटोरियल
tags:
- C#
- Word Automation
- Aspose.Words
title: C# का उपयोग करके Word में आयताकार आकार बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# का उपयोग करके Word में आयताकार आकार बनाएं – पूर्ण ट्यूटोरियल

क्या आपको कभी Word दस्तावेज़ में **आयताकार आकार** बनाने की ज़रूरत पड़ी लेकिन शुरू करने का तरीका नहीं पता था? आप अकेले नहीं हैं—कई डेवलपर्स को वही समस्या आती है जब वे **आकार में छाया जोड़ना** चाहते हैं ताकि वह पेशेवर दिखे। इस ट्यूटोरियल में हम **Word में आकार डालना**, एक हल्की छाया लागू करना, और अंत में **c# generate word document** फ़ाइलें बनाना दिखाएंगे जिन्हें आप उपयोगकर्ताओं को भेज सकते हैं।

हम प्रोजेक्ट सेटअप से लेकर छाया गुणों को ट्यून करने तक सब कुछ कवर करेंगे, और एक तैयार‑से‑चलाने योग्य कोड उदाहरण के साथ समाप्त करेंगे। कोई फालतू बातें नहीं, सिर्फ वही व्यावहारिक हिस्से जो काम को पूरा करते हैं।

## आप क्या सीखेंगे

- C# में Aspose.Words (या Open XML) के साथ **आयताकार आकार** कैसे **create rectangle shape** करें  
- गहराई के लिए **आकार में छाया जोड़ना** के लिए आवश्यक सटीक गुण  
- `DocumentBuilder` का उपयोग करके आकार को कहाँ रखें  
- फ़ाइल को कैसे सहेजें ताकि वह Microsoft Word में सही ढंग से खुले  
- वास्तविक‑दुनिया के परिदृश्यों के लिए टिप्स, pitfalls, और विविधताएँ  

### पूर्वापेक्षाएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Core और .NET Framework पर भी काम करता है)  
- एक NuGet पैकेज जो Word फ़ाइलों को हेरफेर कर सके – हम **Aspose.Words for .NET** का उपयोग करेंगे क्योंकि इसका API संक्षिप्त है। यदि आप Open XML SDK पसंद करते हैं, तो अवधारणाएँ समान हैं, केवल क्लासेज़ अलग हैं।  
- Visual Studio, VS Code, या कोई भी C# IDE जो आपको पसंद हो  

> **Pro tip:** यदि आपका बजट सीमित है, तो Aspose एक मुफ्त ट्रायल देता है जो सीखने के लिए एकदम उपयुक्त है। परीक्षण के दौरान लाइसेंस लाइन को एक टिप्पणी से बदल दें।

## चरण 1: Word‑प्रोसेसिंग लाइब्रेरी स्थापित करें

पहले, लाइब्रेरी को अपने प्रोजेक्ट में जोड़ें। अपने सॉल्यूशन फ़ोल्डर में एक टर्मिनल खोलें और चलाएँ:

```bash
dotnet add package Aspose.Words
```

यदि आप Open XML SDK का उपयोग कर रहे हैं, तो कमांड `dotnet add package DocumentFormat.OpenXml` होगी। इस गाइड का बाकी हिस्सा Aspose.Words मानता है, लेकिन API कॉल्स को बदलना सीधा है।

## चरण 2: नया खाली दस्तावेज़ बनाएं

अब लाइब्रेरी तैयार है, हम एक साफ़ `Document` ऑब्जेक्ट से **आयताकार आकार** बना सकते हैं। इसे एक नई कैनवास की तरह सोचें।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` हमें लो‑लेवल नोड ट्री में गहराई में जाए बिना सामग्री डालने का उच्च‑स्तरीय तरीका देता है।

## चरण 3: आयताकार आकार डालें

बिल्डर हाथ में होने पर, हम **Word में आकार डालना** कर सकते हैं। `InsertShape` मेथड आकार का प्रकार और उसके आयाम (चौड़ाई, ऊँचाई) पॉइंट्स में लेता है।

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

इस बिंदु पर आयत दस्तावेज़ में दिखाई देती है, लेकिन यह थोड़ा सपाट दिखता है। अगला चरण यही सुधार लाएगा।

## चरण 4: आकार में छाया जोड़ें

छाया आकार को गहराई का एहसास देती है। `Shadow` ऑब्जेक्ट हमें ब्लर, दूरी, कोण, रंग, और ट्रांसपेरेंसी को बारीकी से ट्यून करने देता है। नीचे एक पूरी कॉन्फ़िगरेशन है जो अधिकांश रिपोर्टों के लिए अच्छी तरह काम करती है।

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**इन मानों का कारण क्या है?**  
- `BlurRadius` **5.0** किनारा को स्मूद रखता है बिना धुंधला दिखाए।  
- `Distance` **4.0** छाया को पर्याप्त रूप से ऑफ़सेट करता है ताकि वह दिखाई दे।  
- `Angle` **45** ऊपर‑बाएँ से प्राकृतिक प्रकाश की नकल करता है, जो सामान्य UI परम्परा है।  
- `Transparency` **0.3** छाया को आकार के फ़िल को हावी होने से रोकता है।

यदि आपको अधिक नाटकीय प्रभाव चाहिए, तो `BlurRadius` बढ़ाएँ और `Transparency` घटाएँ। हल्के, लगभग‑अदृश्य लिफ्ट के लिए उन संख्याओं को उलट दें।

## चरण 5: दस्तावेज़ सहेजें

अंत में, फ़ाइल को डिस्क पर लिखें। `Save` मेथड फ़ाइल एक्सटेंशन से फ़ॉर्मेट पहचान लेता है, इसलिए `.docx` आपको आधुनिक Word फ़ॉर्मेट देता है।

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

`ShadowRectangle.docx` को Microsoft Word में खोलें, और आपको एक स्पष्ट आयताकार आकार के साथ एक नरम छाया दिखाई देगी—बिल्कुल वही जो आप “**how to add shape**” पूछते समय चाहते थे, पेशेवर फ़िनिश के साथ।

![Word में छाया के साथ आयताकार आकार बनाएं](placeholder-image.png "Word में छाया के साथ आयताकार आकार बनाएं")

*छवि वैकल्पिक पाठ: Word में छाया के साथ आयताकार आकार बनाएं*

## पूर्ण कार्यशील उदाहरण

सब कुछ एक साथ रखते हुए, यहाँ पूरा, तैयार‑से‑चलाने वाला प्रोग्राम है। इसे कॉपी‑पेस्ट करके एक कंसोल ऐप में रखें और **F5** दबाएँ।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### अपेक्षित परिणाम

- उत्पन्न `ShadowRectangle.docx` में **एक आयताकार आकार** केंद्रित होगा जहाँ कर्सर स्थित था।  
- आयत **30 % पारदर्शी काली छाया** के साथ 45° कोण पर ऑफ़सेट दिखाएगा।  
- अन्य कोई सामग्री नहीं जोड़ी गई, जिससे फ़ाइल हल्की और बड़े रिपोर्टों में एम्बेड करने में आसान रहेगी।

## सामान्य प्रश्न और किनारे के मामलों

### यदि मुझे अलग आकार चाहिए तो क्या करें?

`ShapeType.Rectangle` को किसी भी अन्य `ShapeType` enum मान (जैसे `Ellipse`, `Triangle`) से बदलें। छाया API समान रहती है, इसलिए आप वही कॉन्फ़िगरेशन पुन: उपयोग कर सकते हैं।

### फ़िल रंग कैसे बदलें?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### क्या मैं आकार को किसी विशिष्ट पैराग्राफ़ में जोड़ सकता हूँ?

हाँ। `InsertShape` कॉल करने से पहले `builder.MoveToParagraph(index)` के साथ `DocumentBuilder` को लक्ष्य पैराग्राफ़ पर ले जाएँ। इससे आकार ठीक उसी जगह दिखाई देगा जहाँ आपको चाहिए।

### पुराने Word फ़ॉर्मेट (.doc) के बारे में क्या?

सिर्फ एक्सटेंशन बदलें:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

छाया सुविधा Word 2003 और बाद के संस्करणों में समर्थित है, इसलिए आप प्रभाव देख पाएँगे।

### Aspose के बजाय Open XML SDK का उपयोग?

कदम वही हैं: एक `WordprocessingDocument` बनाएं, एक `Drawing` तत्व जोड़ें, `<a:shadow>` गुण सेट करें। XML अधिक विस्तृत होता है, लेकिन वही अवधारणाएँ (आकार, ब्लर, दूरी, कोण) लागू होती हैं।

## pitfalls से बचने के टिप्स

- **लाइसेंस भूल न जाएँ** यदि आप Aspose का पेड संस्करण उपयोग कर रहे हैं; नहीं तो वॉटरमार्क दिखेगा।  
- **इकाइयाँ पॉइंट्स हैं**, पिक्सेल नहीं। एक सामान्य स्क्रीन पिक्सेल ≈ 0.75 pt होता है, इसलिए आयाम उसी अनुसार समायोजित करें।  
- **यदि shape का `WrapType` `Inline` है तो छाया गुण अनदेखे रहेंगे**। फ़्लोटिंग शैप्स के लिए `WrapType = WrapType.Square` उपयोग करें ताकि छाया रेंडर हो।  
- **नेटवर्क शेयर पर सहेजते समय** उचित अनुमतियों की आवश्यकता हो सकती है; हमेशा पथ को पहले टेस्ट करें।

## निष्कर्ष

अब आप जानते हैं कि C# का उपयोग करके Word दस्तावेज़ में **आयताकार आकार** कैसे बनाएं, **आकार में छाया जोड़ें**, और **c# generate word document** फ़ाइलें कैसे तैयार करें जो बॉक्स से बाहर ही परिपूर्ण दिखें। मुख्य कदम—लाइब्रेरी स्थापित करना, `Document` बनाना, आकार डालना, छाया कॉन्फ़िगर करना, और सहेजना—याद रखने में आसान हैं और अन्य आकारों, रंगों, या गतिशील डेटा के लिए अनुकूलित किए जा सकते हैं।

अब आगे क्या? कई आकारों को लेयर करें, इमेज एम्बेड करें, या तालिकाओं और चार्ट्स के साथ पूर्ण रिपोर्ट जनरेट करें। आप शर्तीय फ़ॉर्मेटिंग भी एक्सप्लोर कर सकते हैं—डेटा मानों के आधार पर छाया की तीव्रता बदलें—ताकि आपके दस्तावेज़ न केवल कार्यात्मक हों बल्कि दृश्य रूप से आकर्षक भी हों।

बिना झिझक प्रयोग करें, और यदि कोई अजीब व्यवहार मिले तो नीचे टिप्पणी छोड़ें। कोडिंग का आनंद लें, और आपके Word दस्तावेज़ हमेशा वह परिपूर्ण ड्रॉप शैडो रखें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}