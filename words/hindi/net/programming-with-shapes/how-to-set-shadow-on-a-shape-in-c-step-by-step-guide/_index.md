---
category: general
date: 2026-04-10
description: how to set shadow on a shape in C# – learn how to apply drop shadow,
  change transparency, adjust blur, and add shape shadow using Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: hi
og_description: C# में किसी आकार पर शैडो कैसे सेट करें – यह ट्यूटोरियल दिखाता है कि
  ड्रॉप शैडो कैसे लागू करें, पारदर्शिता कैसे बदलें, ब्लर कैसे समायोजित करें, और स्पष्ट
  कोड उदाहरणों के साथ आकार शैडो कैसे जोड़ें।
og_title: C# में किसी आकृति पर छाया कैसे सेट करें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Document Automation
title: C# में किसी आकार पर शैडो कैसे सेट करें – चरण‑दर‑चरण गाइड
url: /hi/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में आकार पर छाया सेट कैसे करें – पूर्ण गाइड

क्या आपने कभी **छाया सेट करने** के बारे में सोचा है जब आप प्रोग्रामेटिकली एक Word दस्तावेज़ बना रहे हों? आप अकेले नहीं हैं। कई डेवलपर्स को तब रुकावट आती है जब उन्हें टेक्स्टबॉक्स, लोगो या कॉल‑आउट बॉक्स के लिए सूक्ष्म ड्रॉप शैडो चाहिए होती है, और API दस्तावेज़ थोड़ा कम लगते हैं।  

इस ट्यूटोरियल में हम पूरी प्रक्रिया को चरण‑दर‑चरण देखेंगे: `.docx` फ़ाइल लोड करने से, पहले `Shape` को प्राप्त करने तक, ड्रॉप शैडो लागू करने, उसकी ट्रांसपेरेंसी समायोजित करने, ब्लर रेडियस बदलने, और अंत में सही पोज़िशनिंग करने तक। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जो Aspose.Words .NET 2023 या बाद के संस्करणों के साथ काम करता है, और आप समझेंगे कि *हर प्रॉपर्टी* क्यों महत्वपूर्ण है।

## आपको क्या चाहिए

- **Aspose.Words for .NET** (NuGet पैकेज `Aspose.Words`) – वह लाइब्रेरी जो हमें `Document`, `Shape`, और `ShadowFormat` क्लासेज़ देती है।  
- **.NET 6+** (या .NET Framework 4.7.2) – कोई भी नया रनटाइम चलेगा।  
- एक साधारण Word फ़ाइल (`input.docx`) जिसमें पहले से कम से कम एक आकार हो, जैसे कि टेक्स्टबॉक्स।  
- Visual Studio, VS Code, या आपका पसंदीदा IDE।

बस इतना ही। कोई अतिरिक्त थर्ड‑पार्टी टूल नहीं, कोई COM इंटरऑप नहीं, सिर्फ साधा C#।

![how to set shadow example](image-placeholder.png){:alt="Word दस्तावेज़ में एक आकार पर छाया सेट करना"}

## छाया सेट करने का अवलोकन

**छाया सेट करने** का मूल विचार यह है कि हम `Shape` पर मौजूद `ShadowFormat` ऑब्जेक्ट को बदलें। `ShadowFormat` को छाया के लिए एक छोटा “स्टाइल शीट” समझें: यह रेंडरर को बताता है कि छाया दिखनी चाहिए या नहीं, उसका रंग क्या होगा, वह कितनी ट्रांसपेरेंट है, ब्लर कितना है, और आकार के सापेक्ष वह कहाँ स्थित है।  

नीचे *पूरा* चलाने योग्य प्रोग्राम दिया गया है। इसे कॉपी‑पेस्ट करके एक कंसोल ऐप में रखें, **F5** दबाएँ, और देखें कि `output.docx` में छाया कैसे प्रकट होती है।

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### ये सेटिंग्स क्यों महत्वपूर्ण हैं

- **Visible** – इस फ़्लैग को ऑन किए बिना सभी अन्य प्रॉपर्टीज़ अनदेखी रह जाती हैं।  
- **Color** – डार्क ग्रे सामान्य UI ड्रॉप शैडो की नकल करता है; आप किसी भी `Color` से बदल सकते हैं।  
- **Transparency** – 0.3 एक *सॉफ्ट* लुक देता है जबकि आकार अभी भी पढ़ने योग्य रहता है।  
- **Size** – ब्लर को नियंत्रित करता है; 6 का मान आमतौर पर प्रोफ़ेशनल फ़ील देता है।  
- **Distance & Angle** – मिलकर *ऑफ़सेट* तय करते हैं; 2 pts पर 45° एक सूक्ष्म डायगोनल शैडो देता है।

यही है **छाया सेट करने** का सार। अब हम प्रत्येक भाग को अलग‑अलग समझेंगे ताकि आप **ड्रॉप शैडो लागू कर सकें**, **ट्रांसपेरेंसी बदल सकें**, **ब्लर समायोजित कर सकें**, और **आकार की छाया जोड़ सकें**।

---

## आकार पर ड्रॉप शैडो लागू करें

जब लोग पूछते हैं “C# में **ड्रॉप शैडो** कैसे **लागू करें**?”, तो आमतौर पर उन्हें केवल विज़िबिलिटी टॉगल और रंग चाहिए होता है। नीचे दिया गया स्निपेट उन दो लाइनों को अलग करता है:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **प्रो टिप:** यदि आप पुराने Word संस्करणों (2003‑2007) को टार्गेट कर रहे हैं, तो मानक रंगों का उपयोग करें। कुछ एक्सोटिक ARGB वैल्यूज़ को लेगेसी रेंडरर द्वारा अनदेखा किया जा सकता है।

---

## शैडो की ट्रांसपेरेंसी बदलें

ट्रांसपेरेंसी **0 और 1 के बीच के फ़्लोट** के रूप में व्यक्त की जाती है। **0** का मतलब पूरी तरह अपारदर्शी शैडो; **1** शैडो को अदृश्य बना देता है। अधिकांश डिज़ाइनर प्राकृतिक लुक के लिए **0.2‑0.4** के आसपास सेट करते हैं।

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### किनारे के मामलों

- **निगेटिव वैल्यू** – Aspose.Words उन्हें 0 पर क्लैंप कर देगा, लेकिन इनपुट को वैलिडेट करना बेहतर है।  
- **1 से बड़ी वैल्यू** – 1 पर क्लैंप हो जाती है, जिससे शैडो प्रभावी रूप से छिप जाता है।  

यदि आप उपयोगकर्ताओं को प्रतिशत चुनने देना चाहते हैं, तो पहले उसे कन्वर्ट करें:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## शैडो का ब्लर (Size) समायोजित करें

**Size** प्रॉपर्टी ब्लर रेडियस को नियंत्रित करती है। बड़े नंबर एक मुलायम, अधिक फैला हुआ शैडो बनाते हैं। यह पिक्सेल में नहीं, बल्कि पॉइंट्स (pt) में मापा जाता है।

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### कब छोटा बनाम बड़ा ब्लर उपयोग करें

- **छोटा ब्लर (2‑4 pt)** – UI‑स्टाइल कॉल‑आउट्स के लिए उपयुक्त जहाँ आप एक तेज़ किनारा चाहते हैं।  
- **बड़ा ब्लर (8‑12 pt)** – प्रिंटेड रिपोर्ट्स या जब आकार पृष्ठभूमि से दूर हो, तब अच्छा काम करता है।

---

## आकार की छाया जोड़ें – पोज़िशनिंग और दिशा

**आकार की छाया जोड़ने** का अंतिम भाग ऑफ़सेट है। दो प्रॉपर्टी मिलकर काम करती हैं:

| प्रॉपर्टी | अर्थ |
|----------|------|
| **Distance** | शैडो आकार से कितनी दूरी पर बैठती है (पॉइंट्स में)। |
| **Angle**    | ऑफ़सेट की दिशा (0° = दाएँ, 90° = नीचे, 180° = बाएँ, 270° = ऊपर)। |

नीचे दिया गया उदाहरण एक सूक्ष्म बॉटम‑राइट शैडो बनाता है:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

आप विभिन्न लाइट सोर्सेज़ को सिम्युलेट करने के लिए एंगल बदल सकते हैं। एक आम ट्रिक यह है कि उपयोगकर्ता को ड्रॉपडाउन से “लाइट सोर्स” चुनने दें और उसे एंगल वैल्यू से मैप करें।

---

## पूर्ण कार्यशील उदाहरण (सभी चरण एक साथ)

नीचे वही प्रोग्राम है जैसा पहले दिखाया गया था, लेकिन **अतिरिक्त टिप्पणियों** के साथ जो लॉजिक को स्पष्ट बनाती हैं। इसे `Program.cs` में कॉपी करें और चलाएँ; आउटपुट फ़ाइल में एक टेक्स्टबॉक्स के साथ बिल्कुल सही ट्यून की गई शैडो होगी।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**अपेक्षित परिणाम:** `output.docx` खोलें। पहला टेक्स्टबॉक्स डार्क ग्रे, 30 % ट्रांसपेरेंट शैडो दिखाएगा जो थोड़ा ब्लर (size = 6) और 2 pt पर 45° एंगल के साथ ऑफ़सेट होगा। प्रभाव सूक्ष्म लेकिन स्पष्ट है—बिल्कुल वही जो अधिकांश UI डिज़ाइनर चाहते हैं।

---

## सामान्य प्रश्न और ट्रिक्स

- **“क्या यह इमेजेज़ पर भी काम करता है?”**  
  हाँ। कोई भी `Shape`—चाहे वह टेक्स्टबॉक्स, पिक्चर, या ऑटो‑शेप हो—`ShadowFormat` को एक्सपोज़ करता है। बस शैडो प्राप्त करने की लॉजिक को उचित इंडेक्स या नाम से बदल दें।

- **“अगर दस्तावेज़ में कई आकार हों तो क्या करें?”**  
  `doc.GetChildNodes(NodeType.Shape, true)` पर लूप करें और प्रत्येक पर समान सेटिंग्स लागू करें। आप `shape.Name` या `shape` के अन्य एट्रिब्यूट्स के आधार पर फ़िल्टर भी कर सकते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}