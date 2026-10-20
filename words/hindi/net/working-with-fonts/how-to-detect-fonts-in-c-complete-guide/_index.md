---
category: general
date: 2026-04-02
description: Aspose.Words का उपयोग करके C# दस्तावेज़ों में फ़ॉन्ट्स का पता कैसे लगाएँ।
  फ़ॉन्ट सेटिंग्स को कॉन्फ़िगर करना सीखें और अनुपलब्ध फ़ॉन्ट्स को प्रभावी ढंग से संभालें।
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: hi
og_description: Aspose.Words का उपयोग करके C# दस्तावेज़ों में फ़ॉन्ट कैसे पहचानें।
  यह गाइड आपको फ़ॉन्ट सेटिंग्स को कॉन्फ़िगर करने और गायब फ़ॉन्ट्स को संभालने का तरीका
  दिखाता है।
og_title: C# में फ़ॉन्ट्स कैसे पहचानें – पूर्ण गाइड
tags:
- C#
- Aspose.Words
- Document Processing
title: C# में फ़ॉन्ट कैसे पहचानें – पूर्ण गाइड
url: /hi/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में फ़ॉन्ट्स कैसे पहचानें – पूर्ण गाइड

क्या आपने कभी सोचा है **फ़ॉन्ट्स कैसे पहचानें** जब आप .NET में एक Word दस्तावेज़ लोड करते हैं और कुछ फ़ॉन्ट्स गायब या बदल दिए जाते हैं? आप अकेले नहीं हैं—डेवलपर्स अक्सर इस समस्या का सामना करते हैं जब दस्तावेज़ ऐसे फ़ॉन्ट का संदर्भ देता है जो सर्वर पर स्थापित नहीं है। अच्छी खबर यह है कि Aspose.Words आपको इन अंतरालों को पहचानने का एक साफ़, प्रोग्रामेटिक तरीका प्रदान करता है।

इस ट्यूटोरियल में हम एक व्यावहारिक उदाहरण के माध्यम से दिखाएंगे कि **फ़ॉन्ट्स कैसे पहचानें**, साथ ही **फ़ॉन्ट सेटिंग्स कैसे कॉन्फ़िगर करें** और **गायब फ़ॉन्ट्स को सुगमता से कैसे संभालें**। अंत तक आपके पास एक तैयार‑चलाने योग्य स्निपेट होगा जो हर फ़ॉन्ट प्रतिस्थापन चेतावनी को प्रिंट करेगा, ताकि आप आवश्यकता अनुसार लॉग, अलर्ट या फ़ॉन्ट बदल सकें।

---

## आपको क्या चाहिए

- **Aspose.Words for .NET** (नवीनतम संस्करण सबसे अच्छा है; नीचे दिया गया कोड .NET 6+ को लक्षित करता है)
- एक .NET विकास पर्यावरण (Visual Studio, Rider, या VS Code)
- एक नमूना `.docx` जो ऐसे फ़ॉन्ट का संदर्भ देता है जो आपके सिस्टम में स्थापित नहीं है (परीक्षण के लिए उत्तम)

Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है, और समाधान Windows, Linux, और macOS पर काम करता है।

---

## चरण 1: Aspose.Words स्थापित करें और संदर्भित करें

पहले, लाइब्रेरी को अपने प्रोजेक्ट में जोड़ें। NuGet कमांड सीधा‑सरल है:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** यदि आप CI सर्वर पर हैं, तो अनपेक्षित ब्रेकिंग बदलावों से बचने के लिए पैकेज संस्करण को पिन करें।

---

## चरण 2: फ़ॉन्ट सेटिंग्स कॉन्फ़िगर करें (और लोड विकल्प तैयार करें)

दस्तावेज़ खोलने से पहले, आप Aspose.Words को बता सकते हैं कि fallback फ़ॉन्ट्स कहाँ खोजे जाएँ। यह **फ़ॉन्ट सेटिंग्स कॉन्फ़िगर करने** वाला भाग है जो इंजन को चुपचाप अनचाहे फ़ॉन्ट्स बदलने से रोकता है।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

क्यों bother करें? यदि दस्तावेज़ *Comic Sans* का संदर्भ देता है लेकिन आपके सर्वर पर केवल *Calibri* है, तो Aspose.Words *Calibri* को प्रतिस्थापित करेगा और एक चेतावनी देगा। खोज पथ को कॉन्फ़िगर करके आप अनपेक्षित आश्चर्यों को कम कर सकते हैं।

---

## चरण 3: तैयार विकल्पों के साथ दस्तावेज़ लोड करें

अब हम वास्तव में फ़ाइल खोलते हैं। पिछले चरण में बनाए गए `LoadOptions` को सीधे `Document` कंस्ट्रक्टर में पास किया जाता है।

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

यदि फ़ाइल नहीं मिलती या भ्रष्ट है, तो एक अपवाद फेंका जाता है—इसलिए प्रोडक्शन कोड में इसे try/catch में लपेटना उचित रहेगा।

---

## चरण 4: फ़ॉन्ट प्रतिस्थापन के लिए दस्तावेज़ चेतावनियों को स्कैन करें

Aspose.Words पार्सिंग के दौरान चेतावनियों की एक सूची एकत्र करता है। इनमें से, `FontSubstitutionWarning` आपको ठीक‑ठीक बताता है कि कौन सा फ़ॉन्ट बदला गया।

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

`Warnings` संग्रह में अन्य आइटम भी हो सकते हैं (जैसे `DocumentStructureWarning`)। `FontSubstitutionWarning` के लिए फ़िल्टर करने से हम केवल **गायब फ़ॉन्ट्स को संभालने** वाले परिदृश्य की रिपोर्ट करते हैं।

---

## चरण 5: सब कुछ एक साथ रखें – एक पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है। इसे नई कंसोल ऐप में कॉपी‑पेस्ट करें और चलाएँ; आपको प्रत्येक गायब फ़ॉन्ट कंसोल में प्रिंट होते दिखेंगे।

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**अपेक्षित आउटपुट** (उदाहरण):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

यदि दस्तावेज़ केवल उन फ़ॉन्ट्स का उपयोग करता है जो मशीन पर मौजूद हैं, तो आपको “No font substitutions detected” लाइन दिखाई देगी।

---

## किनारे के मामलों और सामान्य प्रश्न

### यदि दस्तावेज़ में **कोई चेतावनी नहीं** है तो क्या होगा?

यह सिर्फ यह दर्शाता है कि सभी संदर्भित फ़ॉन्ट्स आपके द्वारा कॉन्फ़िगर किए गए खोज फ़ोल्डरों में मिल गए। उदाहरण में `anySubstitutions` फ़्लैग इस स्थिति को कवर करता है।

### क्या मैं चेतावनियों को कंसोल के बजाय फ़ाइल में **लॉग** कर सकता हूँ?

बिल्कुल। `Console.WriteLine` कॉल्स को अपनी पसंद के लॉगर (Serilog, NLog, आदि) से बदल दें। `WarningInfo` ऑब्जेक्ट `WarningType` और `WarningMessage` भी प्रदान करता है यदि आपको अधिक विवरण चाहिए।

### मैं कुछ फ़ॉन्ट्स को **अवहेलना** कैसे करूँ, जैसे कि एक कॉरपोरेट ब्रांड फ़ॉन्ट जो कभी नहीं बदलना चाहिए?

आप एक कस्टम प्रतिस्थापन नियम जोड़ सकते हैं:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

अब Aspose.Words केवल *MyBrandFont* को सूचीबद्ध विकल्पों से बदलेगा, और आपको फिर भी एक चेतावनी मिलेगी जिस पर आप कार्रवाई कर सकते हैं।

### क्या यह **Linux** कंटेनरों पर काम करता है?

हां—सिर्फ यह सुनिश्चित करें कि आप आवश्यक `.ttf`/`.otf` फ़ाइलों वाले फ़ोल्डर को माउंट करें और `SetFontsFolder` को उस दिशा में इंगित करें। Aspose.Words OS‑स्थापित फ़ॉन्ट्स पर निर्भर नहीं करता।

---

## दृश्य अवलोकन

![फ़ॉन्ट्स कैसे पहचानें फ्लोचार्ट](detect-fonts.png "दस्तावेज़ में फ़ॉन्ट्स पहचानने के चरण दिखाने वाला आरेख")

*छवि वैकल्पिक पाठ:* **फ़ॉन्ट्स कैसे पहचानें** फ्लोचार्ट जो कॉन्फ़िगरेशन, लोडिंग, और चेतावनी निरीक्षण को दर्शाता है।

---

## पुनरावलोकन – हमने क्या सीखा

- **फ़ॉन्ट्स कैसे पहचानें** जो गायब हैं या Aspose.Words चेतावनियों के माध्यम से प्रतिस्थापित हुए हैं।  
- **फ़ॉन्ट सेटिंग्स कैसे कॉन्फ़िगर करें** ताकि कस्टम फ़ॉन्ट फ़ोल्डरों की ओर इशारा हो और डिफ़ॉल्ट fallback सेट हो।  
- **गायब फ़ॉन्ट्स को संभालने** की रणनीतियाँ, लॉगिंग से लेकर कस्टम प्रतिस्थापन नियमों तक।

इन सब को एक कॉम्पैक्ट, स्व-निहित कंसोल ऐप में संकलित किया गया है जिसे आप किसी भी .NET समाधान में डाल सकते हैं।

---

## अगले कदम और संबंधित विषय

- **फ़ॉन्ट एम्बेडिंग** सीधे आउटपुट दस्तावेज़ में ताकि भविष्य में प्रतिस्थापन न हो (`SaveOptions` के साथ `EmbedFullFonts`)।  
- **प्रोग्रामेटिक फ़ॉन्ट प्रतिस्थापन** – सहेजने से पहले गायब फ़ॉन्ट्स को विशिष्ट विकल्प से बदलें।  
- **परफ़ॉर्मेंस ट्यूनिंग** – बैच में कई दस्तावेज़ प्रोसेस करते समय `FontSettings` को कैश करें।  

यदि आप इन विषयों में रुचि रखते हैं, तो *configure font settings* और *handle missing fonts* खोजें—वे आपको Aspose.Words के साथ फ़ॉन्ट प्रबंधन पर गहरी जानकारी तक ले जाएंगे।

कोडिंग का आनंद लें! कोई अजीब फ़ॉन्ट किनारा मामला है? टिप्पणी छोड़ें, हम साथ मिलकर समस्या का समाधान करेंगे।

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}