---
category: general
date: 2025-12-22
description: अपने C# आकारों में आसानी से शैडो इफ़ेक्ट जोड़ें। सीखें कि शैडो कैसे जोड़ें,
  ब्लर कैसे सेट करें, और शैप शैडो फ़ॉर्मेटिंग के साथ सॉफ्ट शैडो बनाएं।
draft: false
keywords:
- add shadow effect
- how to add shadow
- how to set blur
- create soft shadow
- add shape shadow
language: hi
og_description: अपने C# आकारों में छाया प्रभाव जोड़ें। यह ट्यूटोरियल दिखाता है कि
  छाया कैसे जोड़ें, ब्लर कैसे सेट करें, और स्पष्ट कोड उदाहरणों के साथ सॉफ्ट शैडो कैसे
  बनाएं।
og_title: C# में आकारों पर शैडो इफ़ेक्ट जोड़ें – पूर्ण गाइड
tags:
- C#
- graphics
- Aspose.Slides
- UI design
title: C# में आकृतियों पर शैडो इफ़ेक्ट जोड़ें – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/java/images-shapes/add-shadow-effect-to-shapes-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में आकारों पर शैडो इफ़ेक्ट जोड़ें – पूर्ण गाइड

क्या आपने कभी सोचा है कि **add shadow effect** को एक आकार पर बिना घंटों API दस्तावेज़ पढ़े कैसे जोड़ा जाए? आप अकेले नहीं हैं। कई डेवलपर्स को वह सूक्ष्म ड्रॉप‑शैडो चाहिए होता है जिससे UI तत्व उभर कर दिखें, और सामान्य “रेफ़रेंस देखें” वाला जवाब अक्सर निराशाजनक लगता है।

इस ट्यूटोरियल में हम आपको C# का उपयोग करके आकार पर **add shadow effect** जोड़ने के सभी चरणों से परिचित कराएंगे। हम *how to add shadow*, *how to set blur* को एक हल्की चमक के लिए कवर करेंगे, और यहाँ तक कि **create soft shadow** कैसे बनाते हैं जो किसी भी एप्लिकेशन में प्रोफेशनल दिखे। अंत तक आपके पास एक तैयार‑चलाने‑योग्य उदाहरण होगा जिसे आप अभी अपने प्रोजेक्ट में डाल सकते हैं।

## इस ट्यूटोरियल में क्या कवर किया गया है

- Aspose.Slides (या किसी समान लाइब्रेरी) में **add shape shadow** करने के लिए आवश्यक सटीक API कॉल्स।
- स्टेप‑बाय‑स्टेप कोड जिसे आप कॉपी‑पेस्ट कर सकते हैं।
- प्रत्येक सेटिंग क्यों महत्वपूर्ण है – केवल कमांड्स की सूची नहीं।
- ट्रांसपेरेंट शैप्स, मल्टिपल शैडोज़, और परफ़ॉर्मेंस टिप्स जैसे एज केस।
- एक पूर्ण, रन करने योग्य सैंपल जो एक आयत पर स्पष्ट सॉफ्ट शैडो उत्पन्न करता है।

शैडो APIs का कोई पूर्व अनुभव आवश्यक नहीं है; केवल C# और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी समझ चाहिए।

---

## Add Shadow Effect – Overview

शैडो मूलतः एक विज़ुअल ऑफ़सेट प्लस ब्लर होता है जो गहराई का सिमुलेशन करता है। अधिकांश ग्राफ़िक्स लाइब्रेरीज़ में प्रक्रिया इस प्रकार दिखती है:

1. **Retrieve** आकार के शैडो फ़ॉर्मेटिंग ऑब्जेक्ट को।
2. **Configure** प्रॉपर्टीज़ जैसे ऑफ़सेट, रंग, और ब्लर रेडियस।
3. **Apply** सेटिंग्स को वापस आकार पर लागू करें।

इन तीन चरणों का पालन करने पर आप तुरंत **soft shadow** देखेंगे। मुख्य बात ब्लर रेडियस है – यही वह नॉब है जो कठोर किनारे को एक हल्की धुंध में बदल देता है।

### Quick terminology cheat‑sheet

| शब्द | क्या करता है |
|------|--------------|
| **ShadowFormat** | सभी शैडो‑संबंधित प्रॉपर्टीज़ (ऑफ़सेट, रंग, ब्लर, आदि) को रखता है। |
| **BlurRadius** | शैडो किनारे की धुंधलापन को नियंत्रित करता है। उच्च मान = नरम शैडो। |
| **OffsetX / OffsetY** | शैडो को क्षैतिज/ऊर्ध्वाधर रूप से स्थानांतरित करता है। |
| **Transparency** | शैडो को अधिक या कम अपारदर्शी बनाता है। |

इनका समझना आपको **create soft shadow** प्रभाव बनाने में मदद करेगा जो स्वाभाविक महसूस हों।

## How to Add Shadow to a Shape

सबसे पहले – आपको एक shape इंस्टेंस चाहिए। नीचे Aspose.Slides का उपयोग करके एक न्यूनतम सेटअप दिया गया है, लेकिन यही पैटर्न अधिकांश .NET ग्राफ़िक्स लाइब्रेरीज़ में काम करता है।

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System.Drawing;

// Create a new presentation and add a blank slide
Presentation pres = new Presentation();
ISlide slide = pres.Slides[0];

// Add a rectangle shape (our canvas for the shadow)
IShape rect = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 100, 100, 300, 150);
rect.FillFormat.FillType = FillType.Solid;
rect.FillFormat.SolidFillColor = Color.LightBlue;
rect.LineFormat.Width = 2;
rect.LineFormat.FillFormat.SolidFillColor = Color.DarkBlue;
```

> **Pro tip:** ऐसा shape चुनें जिसका फ़िल स्पष्ट दिखे; अन्यथा शैडो पारदर्शी बैकग्राउंड के पीछे छिप सकता है।

अब जब हमारे पास `rect` है, हम उसके `ShadowFormat` को एक्सेस करके **add shape shadow** कर सकते हैं:

```csharp
// Step 1: Obtain the shape you want to modify (already done above)
// Step 2: Access the shape's shadow formatting object
ShadowFormat shadow = rect.ShadowFormat;

// Step 3: Enable the shadow and set basic properties
shadow.Visible = true;                 // Turn the shadow on
shadow.Type = ShadowType.Inner;        // You can also use Outer, Perspective, etc.
shadow.Color = Color.Black;           // Classic black shadow
shadow.OffsetX = 5;                    // 5 points to the right
shadow.OffsetY = 5;                    // 5 points down
```

इस बिंदु पर आयत में एक स्पष्ट, कठोर‑किनारा वाला शैडो होगा। यदि आप प्रेजेंटेशन चलाते हैं, तो आपको एक **add shadow effect** दिखाई देगा जो फैंसी होने से अधिक कार्यात्मक है।

## How to Set Blur for a Soft Shadow

कठोर किनारा सस्ता दिख सकता है, विशेषकर हाई‑DPI डिस्प्ले पर। यहाँ **how to set blur** काम आता है। `BlurRadius` प्रॉपर्टी एक `float` लेती है जो पॉइंट्स में रेडियस दर्शाता है।

```csharp
// Step 4: Set the blur radius to create a soft shadow
shadow.BlurRadius = 5.0f;   // 5 points gives a subtle, soft look
```

क्यों `5.0f`? व्यावहारिक रूप से, `3.0f` से `8.0f` के बीच के मान अधिकांश UI तत्वों के लिए एक प्राकृतिक सॉफ्ट शैडो उत्पन्न करते हैं। इससे अधिक मान शैडो की बजाय एक ग्लो जैसा दिखना शुरू कर देता है।

आप ट्रांसपेरेंसी को भी समायोजित कर सकते हैं ताकि शैडो कम कठोर लगे:

```csharp
shadow.Transparency = 0.4f; // 40% transparent – looks lighter
```

अब आपने **added shadow effect** बना लिया है जो दिखने में स्पष्ट और कोमल दोनों है। परिणाम देखने के लिए फ़ाइल को सहेजें:

```csharp
pres.Save("AddShadowEffect.pptx", SaveFormat.Pptx);
```

`AddShadowEffect.pptx` को PowerPoint या किसी भी व्यूअर में खोलें, और आपको एक आयत दिखाई देगा जिसमें सुगमता से ब्लर किया हुआ ऑफ़सेट है – एक textbook **create soft shadow** उदाहरण।

## Create Soft Shadow with Custom Settings

कभी‑कभी आपको अधिक कलात्मक नियंत्रण चाहिए होता है। नीचे एक हेल्पर मेथड दिया गया है जो सामान्य सेटिंग्स को एक ही कॉल में बंडल करता है। इसे अपनी यूटिलिटीज़ क्लास में कॉपी करने में संकोच न करें।

```csharp
/// <summary>
/// Applies a customizable soft shadow to any IShape.
/// </summary>
public static void ApplySoftShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                   float blur = 6f, Color? color = null, float transparency = 0.35f)
{
    if (shape == null) throw new ArgumentNullException(nameof(shape));

    ShadowFormat sf = shape.ShadowFormat;
    sf.Visible = true;
    sf.Type = ShadowType.Outer;
    sf.OffsetX = offsetX;
    sf.OffsetY = offsetY;
    sf.BlurRadius = blur;
    sf.Color = color ?? Color.Black;
    sf.Transparency = transparency;
}
```

इसे इस तरह उपयोग करें:

```csharp
ApplySoftShadow(rect, offsetX: 8, offsetY: 8, blur: 7, color: Color.DarkSlateGray);
```

यह मेथड आपको एक ही लाइन में **add shape shadow** करने देता है, जिससे आपका मुख्य कोड साफ़ रहता है। यह *how to add shadow* को पुन: उपयोग योग्य तरीके से दर्शाता है – एक प्रैक्टिस जो जब आपके पास दर्जनों शैप्स हों तो बहुत फायदेमंद होती है।

## Add Shape Shadow – Full Working Example

नीचे एक स्व-निहित प्रोग्राम है जिसे आप कंपाइल और रन कर सकते हैं। यह एक प्रेजेंटेशन बनाता है, तीन आयतें जोड़ता है, प्रत्येक में अलग‑अलग शैडो कॉन्फ़िगरेशन होता है, और फ़ाइल को सहेजता है।

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System;
using System.Drawing;

namespace ShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Initialize presentation
            Presentation pres = new Presentation();
            ISlide slide = pres.Slides[0];

            // Rectangle 1 – basic shadow
            IShape rect1 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 50, 50, 200, 100);
            rect1.FillFormat.SolidFillColor = Color.LightCoral;
            ApplyShadow(rect1, blur: 3f, offsetX: 4, offsetY: 4, transparency: 0.2f);

            // Rectangle 2 – soft shadow (our main focus)
            IShape rect2 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 50, 200, 100);
            rect2.FillFormat.SolidFillColor = Color.LightGreen;
            ApplyShadow(rect2, blur: 6f, offsetX: 6, offsetY: 6, transparency: 0.4f);

            // Rectangle 3 – heavy blur for a glow effect
            IShape rect3 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 550, 50, 200, 100);
            rect3.FillFormat.SolidFillColor = Color.LightSkyBlue;
            ApplyShadow(rect3, blur: 12f, offsetX: 0, offsetY: 0, transparency: 0.6f, color: Color.DarkBlue);

            // Save the result
            pres.Save("ShadowDemo.pptx", SaveFormat.Pptx);
            Console.WriteLine("Presentation created – open ShadowDemo.pptx to see the add shadow effect.");
        }

        // Reusable helper (same as earlier)
        public static void ApplyShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                       float blur = 5f, Color? color = null, float transparency = 0.35f)
        {
            ShadowFormat sf = shape.ShadowFormat;
            sf.Visible = true;
            sf.Type = ShadowType.Outer;
            sf.OffsetX = offsetX;
            sf.OffsetY = offsetY;
            sf.BlurRadius = blur;
            sf.Color = color ?? Color.Black;
            sf.Transparency = transparency;
        }
    }
}
```

**Expected output:** जब आप *ShadowDemo.pptx* खोलेंगे, तो आपको तीन आयतें दिखेंगी। मध्य वाली आयत क्लासिक **create soft shadow** तकनीक को मध्यम ब्लर और ऑफ़सेट के साथ दर्शाती है, जबकि बाकी हल्की और भारी वैरिएशन दिखाती हैं।

![शैडो इफ़ेक्ट उदाहरण](shadow-example.png "शैडो इफ़ेक्ट उदाहरण")

*छवि वैकल्पिक पाठ:* शैडो इफ़ेक्ट उदाहरण

## Common Pitfalls and Tips

- **Shadow not showing?** सुनिश्चित करें कि `ShadowFormat.Visible` `true` पर सेट है। कुछ लाइब्रेरीज़ डिफ़ॉल्ट रूप से अदृश्य रहती हैं।
- **Blur looks too harsh.** `BlurRadius` को कम करें या `Transparency` बढ़ाएँ। ट्रांसपेरेंसी के लिए `0.4f` का मान आमतौर पर लुक को नरम करता है।
- **Performance concerns.** कई शैडोज़ रेंडर करने से UI री‑ड्रॉ में धीमी गति आ सकती है। यदि आप लूप में ड्रॉ कर रहे हैं तो परिणाम को कैश करें।
- **Multiple shadows.** अधिकांश APIs प्रति shape केवल एक शैडो सपोर्ट करती हैं। कई शैडोज़ का सिमुलेशन करने के लिए shape को डुप्लिकेट करें, प्रत्येक कॉपी को अलग‑अलग ऑफ़सेट दें, और सही क्रम में रेंडर करें।
- **Cross‑platform quirks.** यदि आप Xamarin या MAUI को टार्गेट कर रहे हैं, तो सुनिश्चित करें कि शैडो API लक्ष्य प्लेटफ़ॉर्म पर उपलब्ध है; अन्यथा आपको कस्टम रेंडरर की आवश्यकता हो सकती है।

## Conclusion

अब आप बिल्कुल जानते हैं कि C# में शैप्स पर **add shadow effect** कैसे किया जाता है। `ShadowFormat` ऑब्जेक्ट को प्राप्त करने से लेकर ब्लर को फाइन‑ट्यून करने तक के बुनियादी चरणों को समझने के बाद, आप अपने UI में पेशेवर‑स्तर के सॉफ्ट शैडोज़ जोड़ सकते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}