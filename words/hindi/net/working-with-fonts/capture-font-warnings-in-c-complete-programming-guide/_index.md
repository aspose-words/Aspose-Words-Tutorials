---
category: general
date: 2026-02-18
description: Aspose.Words का उपयोग करके C# में फ़ॉन्ट चेतावनियों को पकड़ना और गायब
  फ़ॉन्ट्स का पता लगाना सीखें। गायब फ़ॉन्ट्स को प्रभावी ढंग से संभालने के लिए इस चरण‑दर‑चरण
  गाइड का पालन करें।
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: hi
og_description: C# में फ़ॉन्ट चेतावनियों को पकड़ें और सीखें कि कैसे गायब फ़ॉन्ट्स
  का पता लगाएँ, उन्हें संभालें, और पूर्ण कोड उदाहरण के साथ गायब फ़ॉन्ट्स की सूची बनाएँ।
og_title: C# में फ़ॉन्ट चेतावनियों को पकड़ें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Font Management
title: C# में फ़ॉन्ट चेतावनियों को कैप्चर करें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

inner text.

We must keep markdown formatting.

Let's produce final content.

Check for any URLs: none.

Now produce final translated content with same shortcodes.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Warnings in C# – Complete Programming Guide

क्या आपने कभी सोचा है कि **फ़ॉन्ट चेतावनियों को कैप्चर** कैसे किया जाए जब कोई दस्तावेज़ ऐसे फ़ॉन्ट का संदर्भ देता है जो सर्वर पर स्थापित नहीं है? आप अकेले नहीं हैं। कई एंटरप्राइज़ एप्लिकेशनों में, गायब फ़ॉन्ट लेआउट गड़बड़ियों का कारण बनते हैं, और इन्हें पहचानने का सबसे भरोसेमंद तरीका वह चेतावनियाँ सुनना है जो लाइब्रेरी फेंकती है।

इस ट्यूटोरियल में हम आपको एक तैयार‑चलाने‑योग्य समाधान दिखाएंगे जो न केवल **फ़ॉन्ट चेतावनियों को कैप्चर** करता है बल्कि **गायब फ़ॉन्ट्स का पता लगाता है**, **गायब फ़ॉन्ट्स को संभालता है**, और यहाँ तक कि **गायब फ़ॉन्ट्स की सूची बनाता है** ताकि आप तय कर सकें कि प्रतिस्थापन, एम्बेड करना या उपयोगकर्ता को सूचित करना है। कोई बाहरी दस्तावेज़ीकरण नहीं—सिर्फ कॉपी, पेस्ट और चलाएँ।

## What You’ll Learn

- `LoadOptions` को इस प्रकार कॉन्फ़िगर करना कि फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियाँ चालू हों।  
- DOCX लोड करने और हर चेतावनी निकालने के लिए आवश्यक सटीक कोड।  
- प्रत्येक चरण क्यों महत्वपूर्ण है, जिसमें प्रदर्शन संबंधी विचार शामिल हैं।  
- एज‑केस हैंडलिंग जैसे मिश्रित‑स्क्रिप्ट फ़ॉन्ट्स या कस्टम फ़ॉन्ट फ़ोल्डर वाले दस्तावेज़।  

**Prerequisites**: .NET 6+ (या .NET Framework 4.6+), **Aspose.Words** NuGet पैकेज का रेफ़रेंस, और C# की बुनियादी समझ। यदि आपने पहले Aspose.Words का उपयोग नहीं किया है, तो चिंता न करें—यह गाइड हर बारीकी से आपका मार्गदर्शन करेगा।

![Diagram showing capture font warnings flow](image.png){alt="फ़ॉन्ट चेतावनियों को कैप्चर करने का आरेख"}

## Capture Font Warnings – Why It Matters

जब Aspose.Words कोई दस्तावेज़ लोड करता है, तो यह चुपचाप किसी भी अनुपलब्ध फ़ॉन्ट को एक फ़ॉलबैक से बदल देता है। वह फ़ॉलबैक लोड ऑपरेशन को जीवित रखता है, लेकिन दृश्य परिणाम पूरी तरह से विकृत हो सकता है। **SubstitutionWarningLevel.All** फ़्लैग को चालू करके, लाइब्रेरी प्रत्येक गायब फ़ॉन्ट के लिए एक `WarningInfo` एंट्री जोड़ती है, जिससे आप दस्तावेज़ रेंडर या सेव करने से पहले **गायब फ़ॉन्ट्स का पता लगा** सकते हैं।

> **Pro tip:** यदि आप बैच जॉब में सैकड़ों फ़ाइलें प्रोसेस कर रहे हैं, तो इन चेतावनियों को एक केंद्रीय स्टोर में लॉग करना बाद में मैन्युअल QA में कई घंटे बचा सकता है।

## Step 1: Set Up Your Project

1. अपने पसंदीदा IDE (Visual Studio, Rider, VS Code) को खोलें।  
2. एक नया कंसोल प्रोजेक्ट बनाएं:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Aspose.Words पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

बस इतना ही—कोई अतिरिक्त DLLs नहीं, कोई COM इंटरऑप नहीं। लाइब्रेरी में वह सब कुछ है जो आपको **गायब फ़ॉन्ट्स को संभालने** के लिए चाहिए।

## Step 2: Prepare Load Options to Capture All Font Substitution Warnings

इंजन को **फ़ॉन्ट चेतावनियों को कैप्चर** करने के लिए, आपको उसे हर सब्स्टिट्यूशन रिकॉर्ड करने के लिए कहना होगा। नीचे दिया गया स्निपेट एक `LoadOptions` इंस्टेंस बनाता है, चेतावनी स्तर को सक्षम करता है, और (वैकल्पिक रूप से) इंजन को उस फ़ोल्डर की ओर इंगित करता है जिसमें कस्टम फ़ॉन्ट्स हो सकते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**यह क्यों महत्वपूर्ण है:**  
- `SubstitutionWarningLevel.All` सुनिश्चित करता है कि **हर** गायब‑फ़ॉन्ट इवेंट रिकॉर्ड हो, न कि केवल पहला।  
- इस फ़्लैग के बिना, Aspose.Words चुपचाप फ़ॉन्ट बदल देता है और आपको कभी पता नहीं चलता कि समस्या मौजूद है।

## Step 3: Load the Document Using the Configured Options

अब हम वास्तव में फ़ाइल खोलते हैं। `DocumentWithMissingFonts.docx` को अपने टेस्ट दस्तावेज़ के पाथ से बदलें।

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

यदि फ़ाइल में ऐसे फ़ॉन्ट रेफ़रेंसेज़ हैं जो मशीन पर (या आपने जो वैकल्पिक फ़ोल्डर दिया है) नहीं हैं, तो `document.WarningInfoCollection` भर जाएगा।

## Step 4: Find and Display Any Font Substitution Warnings

यह ट्यूटोरियल का मुख्य भाग है: `WarningInfoCollection` पर इटरेट करके **गायब फ़ॉन्ट्स की सूची** बनाना। हम `WarningType.FontSubstitution` द्वारा फ़िल्टर करेंगे और एक दोस्ताना संदेश प्रिंट करेंगे।

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

यदि दस्तावेज़ में केवल स्थापित फ़ॉन्ट्स ही हैं, तो आपको “✅ No missing fonts detected” लाइन दिखाई देगी।

## Step 5: Advanced – How to **Handle Missing Fonts** Programmatically

केवल सूची प्रिंट करना एक डायग्नोस्टिक टूल के लिए पर्याप्त हो सकता है, लेकिन कई प्रोडक्शन सिस्टम को **गायब फ़ॉन्ट्स को स्वचालित रूप से संभालना** पड़ता है। नीचे दो सामान्य रणनीतियाँ दी गई हैं:

### 5.1 Substitute with a Known Fallback

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Embed a Custom Font on the Fly

यदि आपके पास एक कॉर्पोरेट फ़ॉन्ट फ़ाइल (`MyBrand.ttf`) है, तो आप इसे तब एम्बेड कर सकते हैं जब कोई गायब फ़ॉन्ट पता चले:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note:** फ़ॉन्ट एम्बेड करने से आउटपुट फ़ाइल का आकार बढ़ सकता है, इसलिए फ़िडेलिटी और बैंडविड्थ के बीच समझौता तौलें।

## Common Pitfalls and How to Avoid Them

| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| कोई चेतावनी नहीं दिखती जबकि दस्तावेज़ गलत दिख रहा है | `SubstitutionWarningLevel` को `All` पर सेट नहीं किया गया | सुनिश्चित करें कि चरण 2 में फ़्लैग ठीक उसी तरह सेट किया गया है जैसा दिखाया गया है |
| चेतावनियों में एक ही फ़ॉन्ट कई बार सूचीबद्ध है | दस्तावेज़ में फ़ॉन्ट कई शैलियों में मौजूद है | यदि आपको केवल यूनिक सूची चाहिए तो डुप्लिकेट हटाएँ: `fontWarnings.Select(w => w.Description).Distinct()` |
| बड़े DOCX फ़ाइलों पर एप्लिकेशन क्रैश हो जाता है | डिफ़ॉल्ट मेमोरी सेटिंग्स के साथ लोड किया गया | मेमोरी प्रेशर कम करने के लिए `LoadOptions.LoadFormat` या स्ट्रीम का उपयोग करें |

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

प्रोग्राम को `dotnet run` के साथ चलाएँ। आपको कंसोल में गायब फ़ॉन्ट्स की सूची दिखाई देगी, जिससे पुष्टि होगी कि आपने सफलतापूर्वक **फ़ॉन्ट चेतावनियों को कैप्चर** कर लिया है।

## Conclusion

आपके पास अब एक पूर्ण, प्रोडक्शन‑रेडी पैटर्न है जो Aspose.Words को C# में उपयोग करके **फ़ॉन्ट चेतावनियों को कैप्चर**, **गायब फ़ॉन्ट्स का पता लगाना**, **गायब फ़ॉन्ट्स को संभालना**, और **गायब फ़ॉन्ट्स की सूची बनाना** सक्षम बनाता है। यह तरीका हल्का है, केवल कुछ लाइनों के कोड की आवश्यकता रखता है, और किसी भी मौजूदा पाइपलाइन में डाला जा सकता है—चाहे आप

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}