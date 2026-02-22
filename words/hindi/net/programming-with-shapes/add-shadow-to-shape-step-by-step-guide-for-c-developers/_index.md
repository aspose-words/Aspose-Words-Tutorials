---
category: general
date: 2026-02-21
description: C# में आकार पर छाया जोड़ें और सीखें कि छाया को कैसे अनुकूलित करें, छाया
  प्रभाव लागू करें, और पूर्ण, चलाने योग्य उदाहरण के साथ छाया की अपारदर्शिता सेट करें।
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: hi
og_description: इस गाइड के साथ C# में आकार पर शैडो जोड़ें। सीखें कि शैडो को कैसे कस्टमाइज़
  करें, शैडो इफ़ेक्ट लागू करें, और कुछ ही कोड लाइनों में शैडो की अपारदर्शिता सेट करें।
og_title: आकार में छाया जोड़ें – पूर्ण C# ट्यूटोरियल
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: आकार में छाया जोड़ें – C# डेवलपर्स के लिए चरण-दर-चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# आकार में छाया जोड़ें – पूर्ण C# ट्यूटोरियल

क्या आपको कभी **आकार में छाया जोड़ने** की ज़रूरत पड़ी है लेकिन शुरुआत नहीं पता थी? आप अकेले नहीं हैं—कई डेवलपर्स रिपोर्ट या मार्केटिंग फ़्लायर को पॉलिश करते समय इस समस्या से जूझते हैं। अच्छी ख़बर? कुछ ही चरणों में आप एक सपाट आयत को एक चमकदार, त्रि‑आयामी तत्व में बदल सकते हैं जो पेज से बाहर निकलता दिखे।

इस गाइड में हम एक **पूर्ण, चलाने योग्य उदाहरण** के माध्यम से दिखाएंगे कि कैसे छाया को कस्टमाइज़ करें, छाया इफ़ेक्ट लागू करें, और किसी भी आकार के लिए छाया की अपारदर्शिता सेट करें। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी Aspose.Words प्रोजेक्ट में डाल सकते हैं, बिना किसी रहस्यमय रेफ़रेंस के।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* **.NET 6.0** (या बाद का) स्थापित – कोड .NET Framework 4.6+ के साथ भी काम करता है।
* **Aspose.Words for .NET** NuGet पैकेज – संस्करण 23.9 या नया अनुशंसित है।
* C# और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी समझ।

यदि आपके पास NuGet पैकेज नहीं है, तो चलाएँ:

```bash
dotnet add package Aspose.Words
```

अब बुनियादी सेटअप हो गया है, चलिए काम शुरू करते हैं।

## चरण 1 – दस्तावेज़ लोड या बनाएं और पहला आकार प्राप्त करें

सबसे पहले हमें एक `Document` ऑब्जेक्ट चाहिए जिसमें वास्तव में कोई आकार हो। उदाहरण के लिए हम एक नया दस्तावेज़ बनाएँगे, एक साधारण आयत डालेंगे, और फिर उसे प्राप्त करेंगे।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**हम यह क्यों करते हैं:**  
`GetChild` के माध्यम से आकार प्राप्त करना वास्तविक‑दुनिया के परिदृश्यों की नकल करता है जहाँ आकार पहले से मौजूद होता है (जैसे टेम्पलेट से लोड किया गया)। यह यह भी सुनिश्चित करता है कि बाद वाला छाया कोड एक वैध ऑब्जेक्ट पर काम करे, जिससे null‑reference एक्सेप्शन से बचा जा सके।

> **प्रो टिप:** यदि आप कई आकारों से निपट रहे हैं, तो `GetChild(NodeType.Shape, index, true)` का उपयोग करें या `doc.GetChildNodes(NodeType.Shape, true)` के माध्यम से इटररेट करें।

## चरण 2 – छाया इफ़ेक्ट को सक्षम करें

एक आकार की छाया डिफ़ॉल्ट रूप से बंद होती है। इसे सक्षम करना आगे की किसी भी कस्टमाइज़ेशन की पहली पूर्वापेक्षा है।

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**यह क्यों महत्वपूर्ण है:**  
`Enabled = true` सेट किए बिना, बाद में किए गए किसी भी प्रॉपर्टी परिवर्तन (रंग, ब्लर, ऑफ़सेट) को नजरअंदाज़ किया जाता है। इसे लैंप की ब्राइटनेस समायोजित करने से पहले लाइट स्विच ऑन करने जैसा समझें।

## चरण 3 – छाया का रंग चुनें (और क्यों काला एक अच्छा शुरुआती बिंदु है)

रंग चयन गहराई की अनुभूति को काफी प्रभावित करता है। काला (या बहुत गहरा ग्रे) सबसे आम है क्योंकि यह किसी भी बैकग्राउंड पर काम करता है।

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**वैकल्पिक:**  
यदि आपके दस्तावेज़ का बैकग्राउंड गहरा है, तो एक हल्का शेड आज़माएँ:

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## चरण 4 – छाया की अपारदर्शिता सेट करें (Set Shadow Opacity)

अपारदर्शिता `0.0` (पूरी तरह पारदर्शी) से `1.0` (पूरी तरह अपारदर्शी) के बीच मान में व्यक्त की जाती है। 40 % पारदर्शी छाया अधिकांश UI डिज़ाइनों में स्वाभाविक लगती है।

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**कैसे कस्टमाइज़ करें:**  
- **और सूक्ष्म:** `0.2` (20 % पारदर्शी)  
- **बहुत हल्की:** `0.7` (70 % पारदर्शी)

## चरण 5 – ब्लर और किनारे की नरमी निर्धारित करें

ब्लर नियंत्रित करता है कि छाया के किनारे कितने मुलायम दिखें। `4.0` का मान मध्यम‑आकार के आकारों के लिए अच्छा काम करता है।

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**किनारे के मामले:**  
यदि आप `Blur` को `0` सेट करते हैं, तो छाया एक कठोर‑किनारी सिल्हूट बन जाती है, जो कठोर लग सकती है। इसके विपरीत, `10` से ऊपर के मान छाया को चमक (glow) जैसा बना सकते हैं।

## चरण 6 – आकार के सापेक्ष छाया की स्थिति निर्धारित करें

ऑफ़सेट मान छाया को क्षैतिज (`OffsetX`) और लंबवत (`OffsetY`) शिफ्ट करते हैं। सकारात्मक संख्याएँ छाया को नीचे और दाएँ ले जाती हैं।

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**प्रयोग:**  
- **ड्रॉप शैडो:** `OffsetX = 0`, `OffsetY = 10`  
- **उठी हुई प्रभाव:** `OffsetX = -5`, `OffsetY = -5`

## चरण 7 – सहेजें और परिणाम की पुष्टि करें

अंत में, दस्तावेज़ को डिस्क पर लिखें और Microsoft Word (या कोई संगत व्यूअर) में खोलें ताकि छाया को कार्यरत देखें।

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

जब आप **ShadowedShape.docx** खोलेंगे, तो आपको एक हल्के‑नीले आयत के साथ एक मुलायम, अर्ध‑पारदर्शी काली छाया पाँच पॉइंट्स द्वारा ऑफ़सेटेड दिखनी चाहिए। यदि छाया नहीं दिखती, तो दोबारा जांचें कि `firstShape.Shadow.Enabled` `true` है और आप Aspose.Words का नवीनतम संस्करण उपयोग कर रहे हैं।

### पूर्ण स्रोत कोड (कॉपी‑पेस्ट तैयार)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| **यदि आकार आयत के बजाय चित्र हो तो क्या करें?** | वही छाया प्रॉपर्टी लागू होती हैं; बस सुनिश्चित करें कि आकार का `ShapeType` `Picture` है। |
| **क्या मैं छाया को एनीमेट कर सकता हूँ?** | Aspose.Words एनीमेशन को सपोर्ट नहीं करता, लेकिन आप कई पेज़ बनाकर क्रमिक ऑफ़सेट्स जोड़ सकते हैं और एनीमेशन के लिए PowerPoint उपयोग कर सकते हैं। |
| **क्या छाया PDF निर्यात में काम करती है?** | हाँ। जब आप दस्तावेज़ को PDF (`doc.Save("out.pdf")`) के रूप में सहेजते हैं, तो Aspose.Words छाया इफ़ेक्ट को बरकरार रखता है। |
| **बाद में छाया कैसे हटाएँ?** | `firstShape.Shadow.Enabled = false;` सेट करें या बस `firstShape.Shadow = null;` कर दें। |
| **ब्लर मानों की कोई सीमा है?** | व्यावहारिक रूप से, `15` से ऊपर के मान छाया को हाला जैसा बना देते हैं और फ़ाइल आकार बढ़ा सकते हैं। |

## अगले कदम – गति बनाए रखें

अब जब आप **छाया कैसे जोड़ें** और **छाया की अपारदर्शिता कैसे सेट करें** जानते हैं, तो आगे खोजें:

* `Shadow.Distance` के साथ छाया को और अधिक प्रकट करने के लिए कस्टमाइज़ करें।
* टेक्स्ट फ्रेम या WordArt पर **छाया इफ़ेक्ट** लागू करें ताकि दस्तावेज़ डिज़ाइन समृद्ध हो।
* कई छायाओं (जैसे, inner + outer) को मिलाकर लेयरड लुक प्राप्त करें।
* **HTML में निर्यात** करें और देखें कि CSS `box‑shadow` समान सेटिंग्स को कैसे प्रतिबिंबित करता है।

यदि आप रिपोर्ट जेनरेटर बना रहे हैं, तो हेडर, चार्ट या कॉल‑आउट बॉक्स पर छाया डालें ताकि पाठक की नज़र आकर्षित हो। विभिन्न रंगों और पारदर्शिताओं के साथ प्रयोग करें—शायद कॉरपोरेट थीम के लिए एक सूक्ष्म नीली छाया।

---

### TL;DR

हमने एक **पूर्ण, स्व-निहित उदाहरण** के माध्यम से दिखाया कि कैसे **आकार में छाया जोड़ें**, **छाया को कस्टमाइज़ करें**, **छाया इफ़ेक्ट लागू करें**, और **छाया की अपारदर्शिता सेट करें** Aspose.Words के साथ C# में। कोड चलाने के लिए तैयार है, व्याख्याएँ *क्या* और *क्यों* दोनों को कवर करती हैं, और अब आपके पास किसी भी Word ऑटोमेशन प्रोजेक्ट में आकारों को स्टाइल करने की ठोस नींव है।

कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा वह अतिरिक्त‑आयामी पॉलिश रखें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}