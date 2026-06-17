---
category: general
date: 2026-04-28
description: एक आकृति पर शीघ्रता से छाया कैसे सेट करें। सीखें कि कैसे आकृति की छाया
  जोड़ें, छाया का रंग सेट करें, और Aspose.Words for .NET के साथ आकृति की छाया को अनुकूलित
  करें।
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: hi
og_description: C# में Aspose.Words के साथ किसी आकार पर शैडो कैसे सेट करें। चरण‑दर‑चरण
  गाइड जिसमें आकार पर शैडो जोड़ना, शैडो का रंग सेट करना, और आकार की शैडो को कस्टमाइज़
  करना शामिल है।
og_title: C# में किसी आकार पर शैडो कैसे सेट करें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Document Automation
title: C# में आकृति पर शैडो कैसे सेट करें – आसानी से आकृति का शैडो जोड़ें
url: /hi/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में किसी आकार पर शैडो कैसे सेट करें – आसानी से आकार की शैडो जोड़ें

क्या आपने कभी **शैडो कैसे सेट करें** यह सोचा है बिना अनगिनत API दस्तावेज़ों में खोए? आप अकेले नहीं हैं। कई डेवलपर्स को तब रुकावट आती है जब उन्हें एक सूक्ष्म ड्रॉप‑शैडो चाहिए जो डायग्राम को उभारे, लेकिन उन्हें ऐसा साफ़ उदाहरण नहीं मिलता जो *दोनों* “क्या” और “क्यों” दिखाए।

इस ट्यूटोरियल में हम आकार की शैडो जोड़ने, शैडो का रंग बदलने, और उसके ब्लर, ऑफ़सेट और ट्रांसपेरेंसी को फाइन‑ट्यून करने के चरणों से गुजरेंगे—सभी Aspose.Words for .NET का उपयोग करके। अंत तक आपके पास एक तैयार‑से‑चलाने वाला स्निपेट होगा जिसे आप किसी भी C# प्रोजेक्ट में डाल सकते हैं, साथ ही अधिक जटिल परिदृश्यों में आकार की शैडो को कस्टमाइज़ करने के कुछ टिप्स भी मिलेंगे।

> **Note:** यह कोड Aspose.Words 22.9 या बाद के संस्करणों के साथ काम करता है और .NET 6+ (या .NET Framework 4.7.2+) की आवश्यकता होती है।  

![कस्टम शैडो वाला आकार](shape-shadow.png "कस्टम शैडो वाला आकार")

## आप क्या सीखेंगे

- **प्रोग्रामेटिकली** पहले आकार में **शैडो जोड़ना**।  
- किसी भी `System.Drawing.Color` में **शैडो का रंग सेट करना**।  
- ब्लर रेडियस, ऑफ़सेट और ट्रांसपेरेंसी को समायोजित करके **आकार की शैडो को कस्टमाइज़ करना**।  
- कई आकारों को संभालना और आवश्यकता पड़ने पर शैडो सेटिंग्स को रीसेट करना।  

कोई बाहरी टूल नहीं, कोई Visual Basic मैक्रो नहीं—सिर्फ शुद्ध C#।

---

## आवश्यकताएँ

| Requirement | Why It Matters |
|-------------|----------------|
| **Aspose.Words for .NET** (NuGet पैकेज `Aspose.Words`) | वह `Document`, `Shape`, और `ShadowFormat` क्लासेज़ प्रदान करता है जो उदाहरण में उपयोग होते हैं। |
| **.NET 6 SDK** (या .NET Framework 4.7.2) | नवीनतम API सतह के साथ संगतता सुनिश्चित करता है। |
| **एक .docx फ़ाइल** जिसमें कम से कम एक आकार हो (जैसे, आयत या चित्र) | ट्यूटोरियल *पहले* आकार को बदलता है; यदि आपके पास नहीं है तो आप Word में एक बना सकते हैं। |

लाइब्रेरी को इस प्रकार इंस्टॉल करें:

```bash
dotnet add package Aspose.Words
```

---

## चरण‑दर‑चरण: आकार पर शैडो कैसे सेट करें

### 1. Word दस्तावेज़ लोड करें

हम `.docx` फ़ाइल को खोलकर शुरू करते हैं। `Document` कंस्ट्रक्टर फ़ाइल को मेमोरी में पढ़ता है, जिससे हमें उसके नोड्स तक पूर्ण पहुँच मिलती है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why?** दस्तावेज़ को लोड करना बुनियादी कदम है—इसके बिना आप आकार वृक्ष को ट्रैवर्स नहीं कर सकते।

### 2. पहला आकार प्राप्त करें (या कोई भी आवश्यक आकार)

Aspose.Words आकारों को `NodeType.SHAPE` प्रकार के नोड्स के रूप में संग्रहीत करता है। `GetChild` मेथड हमें *n‑th* आकार प्राप्त करने देता है; यहाँ हम इंडेक्स 0, यानी पहला आकार ले रहे हैं।

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **Pro tip:** यदि आपको किसी विशिष्ट आकार में **शैडो जोड़नी** है, तो इंडेक्स को उपयुक्त मान से बदलें या `doc.GetChildNodes(NodeType.Shape, true)` के माध्यम से इटररेट करें।

### 3. शैडो फ़ॉर्मेटिंग ऑब्जेक्ट तक पहुँचें

हर `Shape` में एक `ShadowFormat` प्रॉपर्टी होती है जो सभी शैडो‑संबंधित सेटिंग्स को उजागर करती है।

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

अब हम शैडो को ट्यून करना शुरू कर सकते हैं।

### 4. ब्लर रेडियस सेट करें – किनारों को नरम बनाना

बड़ा ब्लर रेडियस शैडो को अधिक फैला हुआ दिखाता है। मान पॉइंट्स में होता है (1 pt ≈ 1/72 इंच)।

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **When to adjust?** यदि आपका आकार छोटा है, तो 2–3 pt का ब्लर पर्याप्त हो सकता है; बड़े बैनर के लिए इसे 8–10 pt तक बढ़ाएँ।

### 5. क्षैतिज और लंबवत ऑफ़सेट निर्धारित करें

ऑफ़सेट तय करता है कि शैडो आकार से कितनी दूरी पर विस्थापित हो। सकारात्मक मान शैडो को दाएँ/नीचे ले जाते हैं; नकारात्मक मान बाएँ/ऊपर।

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. ट्रांसपेरेंसी (अपारदर्शिता) को ट्यून करें

`Transparency` का मान `0.0` (पूरी तरह अपारदर्शी) से `1.0` (पूरी तरह पारदर्शी) तक होता है। `0.3` के आसपास का मान एक सूक्ष्म, अर्ध‑पारदर्शी लुक देता है।

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. शैडो का रंग चुनें – **set shadow color** को किसी भी `System.Drawing.Color` में सेट करें

आप कोई भी प्री‑डिफाइंड रंग चुन सकते हैं या RGB मानों के साथ कस्टम रंग बना सकते हैं।

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

यदि आप क्लासिक काली शैडो पसंद करते हैं, तो बस `Color.Black` उपयोग करें।

### 8. संशोधित दस्तावेज़ सहेजें

अंत में, बदलावों को स्थायी बनाएँ। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई जगह पर लिख सकते हैं।

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## पूर्ण कार्यशील उदाहरण (सभी चरण एक ब्लॉक में)

निम्न कोड को कॉन्सोल ऐप के `Main` मेथड में कॉपी‑पेस्ट करें। यह जैसा है वैसा ही कम्पाइल हो जाएगा, बशर्ते NuGet पैकेज इंस्टॉल हो।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**Expected result:** `output_with_shadow.docx` को Word में खोलें; पहला आकार अब एक नरम नीली शैडो दिखाएगा, 3 pt के ऑफ़सेट के साथ, सूक्ष्म ब्लर और 30 % ट्रांसपेरेंसी के साथ।

---

## सामान्य विविधताएँ एवं किनारे के मामले

### सभी आकारों में शैडो जोड़ना

यदि आपके दस्तावेज़ में कई डायग्राम हैं, तो आप प्रत्येक आकार पर लूप लगाना चाहेंगे:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### शैडो रीसेट करना

कभी‑कभी किसी आकार में पहले से शैडो होती है जिसे हटाना आवश्यक होता है। `ShadowFormat.Visible` को `false` सेट करें:

```csharp
shape.ShadowFormat.Visible = false;
```

### अल्फा (अर्ध‑पारदर्शी) के साथ कस्टम रंग उपयोग करना

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### संगतता नोट

`ShadowFormat` API Aspose.Words के सभी संस्करणों में स्थिर है, लेकिन पुराने रिलीज़ (< 19.1) में `ShadowFormat` फ़ील्ड्स के नामकरण में थोड़ी भिन्नता थी। सर्वोत्तम परिणामों के लिए हमेशा नवीनतम NuGet पैकेज को टार्गेट करें।

---

## परिपूर्ण शैडो के लिए प्रो टिप्स

- **ब्लर और ऑफ़सेट का संतुलन:** भारी ब्लर के साथ छोटा ऑफ़सेट “ग्लोइ” जैसा दिख सकता है, असली ड्रॉप शैडो नहीं। `BlurRadius` × `DistanceX/Y` के साथ प्रयोग करें।  
- **दस्तावेज़ थीम से मेल:** यदि Word फ़ाइल डार्क थीम उपयोग करती है, तो हल्की शैडो (`Color.White`) एक सूक्ष्म लिफ्ट इफ़ेक्ट बना सकती है।  
- **परफ़ॉर्मेंस:** सैकड़ों आकारों पर शैडो बदलने से प्रत्येक आकार पर कुछ मिलीसेकंड अतिरिक्त लग सकते हैं। बड़े रिपोर्ट प्रोसेस करते समय ऑपरेशन को बैच करें।  
- **टेस्टिंग:** परिणामी `.docx` को Word डेस्कटॉप और Word Online दोनों में खोलें ताकि शैडो लगातार रेंडर हो।

---

## निष्कर्ष

हमने अभी-अभी C# का उपयोग करके आकार पर **शैडो कैसे सेट करें** को कवर किया। ऊपर बताए गए आठ चरणों का पालन करके आप **आकार की शैडो जोड़ सकते** हैं, **शैडो का रंग सेट कर सकते** हैं, और किसी भी डिज़ाइन भाषा के अनुसार **आकार की शैडो को पूरी तरह कस्टमाइज़** कर सकते हैं। यह उदाहरण स्व-समाहित है, तुरंत चलाने योग्य है, और आपको कई आकारों, डायनामिक रंगों, या यहाँ तक कि यूज़र‑डिफाइंड पैरामीटर तक लॉजिक को विस्तारित करने की ठोस नींव देता है।

अगली चुनौती के लिए तैयार हैं? इस तकनीक को **आकार घुमाव** के साथ मिलाएँ, या एक पूरी रिपोर्ट जेनरेट करें जहाँ प्रत्येक चार्ट को अपना ब्रांडेड शैडो मिले। संभावनाएँ अनंत हैं, और अभी-अभी सीखा कोड एक परिपूर्ण स्प्रिंगबोर्ड है।

यदि आपको यह गाइड उपयोगी लगा, तो कृपया रेपो को स्टार दें, टिप्पणी छोड़ें, या नीचे अपने शैडो‑ट्यूनिंग ट्रिक्स साझा करें। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}