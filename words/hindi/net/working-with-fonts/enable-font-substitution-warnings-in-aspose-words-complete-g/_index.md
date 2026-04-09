---
category: general
date: 2026-01-11
description: फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें ताकि आपके .NET दस्तावेज़ों
  में गायब फ़ॉन्ट का पता लगाया जा सके। Aspose.Words के साथ गायब फ़ॉन्ट का नाम प्राप्त
  करने और गायब फ़ॉन्ट की सूची बनाने के तरीके जानें।
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: hi
og_description: Aspose.Words में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें ताकि
  लापता फ़ॉन्ट्स का पता लगाया जा सके, लापता फ़ॉन्ट का नाम प्राप्त किया जा सके, और
  आपके दस्तावेज़ों में लापता फ़ॉन्ट्स की सूची बनाई जा सके।
og_title: फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – चरण‑दर‑चरण C# ट्यूटोरियल
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – पूर्ण गाइड
url: /hi/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – पूर्ण गाइड

क्या आपने कभी सोचा है कि सर्वर पर वर्ड दस्तावेज़ लोड करने के बाद वह थोड़ा अलग क्यों दिखता है? संभवतः मूल लेखक द्वारा उपयोग किया गया फ़ॉन्ट आपके मशीन पर उपलब्ध नहीं है, और Aspose.Words चुपचाप इसे सबसे नज़दीकी मिलते-जुलते फ़ॉन्ट से बदल देता है। **फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें** और आपको तुरंत पता चल जाएगा कि कौन से फ़ॉन्ट गायब हैं, उन्हें किससे बदल दिया गया, और उस जानकारी के आधार पर क्या कार्रवाई करनी है।

इस ट्यूटोरियल में हम एक व्यावहारिक, अंत‑से‑अंत उदाहरण के माध्यम से चलेंगे जो दिखाता है कि कैसे **गायब फ़ॉन्ट्स का पता लगाएँ**, **गायब फ़ॉन्ट का नाम प्राप्त करें**, और रिपोर्टिंग के लिए **गायब फ़ॉन्ट्स की सूची बनाएँ**। कोई अतिरिक्त बात नहीं, बस एक स्पष्ट समाधान जिसे आप आज ही किसी भी .NET प्रोजेक्ट में उपयोग कर सकते हैं।

---

## आप क्या सीखेंगे

- `LoadOptions` को इस तरह कॉन्फ़िगर करना कि Aspose.Words विस्तृत चेतावनियाँ उत्पन्न करे।
- एक दस्तावेज़ लोड करने और फ़ॉन्ट‑संबंधित चेतावनियों को क्रमबद्ध करने के लिए आवश्यक सटीक कोड।
- गायब फ़ॉन्ट का नाम और उसकी प्रतिस्थापना निकालने के तरीके, फिर एक साफ़ रिपोर्ट आउटपुट करना।
- एज केस को संभालने के टिप्स, जैसे कई गायब फ़ॉन्ट वाले दस्तावेज़ या कस्टम फ़ॉन्ट फ़ोल्डर।

### आवश्यकताएँ

- .NET 6+ (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET 23.10 या नया (आप इसे NuGet से प्राप्त कर सकते हैं)
- एक नमूना DOCX जो ऐसे फ़ॉन्ट को संदर्भित करता है जो आपके सिस्टम में स्थापित नहीं है (हम इसे `MissingFont.docx` कहेंगे)

यदि आपके पास ये बुनियादी चीज़ें हैं, तो चलिए शुरू करते हैं।

---

## चरण 1: फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करने के लिए LoadOptions सेट करें  

सबसे पहले आपको Aspose.Words को यह बताना है कि आप गायब फ़ॉन्ट्स की परवाह करते हैं। डिफ़ॉल्ट रूप से लाइब्रेरी केवल आंतरिक रूप से चेतावनियाँ लॉग करती है। `SubstitutionWarningLevel` को `Typical` (या सबसे विस्तृत आउटपुट के लिए `All`) पर सेट करने से यह स्विच सक्रिय हो जाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**यह क्यों महत्वपूर्ण है:**  

जब `SubstitutionWarningLevel` सेट किया जाता है, तो हर बार जब Aspose.Words किसी संदर्भित फ़ॉन्ट को नहीं ढूँढ़ पाता है, वह दस्तावेज़ के `Warnings` संग्रह में एक `FontSubstitutionWarning` जोड़ देता है। यह संग्रह दस्तावेज़ को मैन्युअल रूप से पार्स किए बिना **गायब फ़ॉन्ट्स का पता लगाने** का एकमात्र विश्वसनीय तरीका है।

> **प्रो टिप:** यदि आप दस्तावेज़ों के एक बैच से निपट रहे हैं और पूरी तरह सुनिश्चित करना चाहते हैं कि आप हर प्रतिस्थापन को पकड़ें, तो `FontSubstitutionWarningLevel.All` का उपयोग करें। यह थोड़ा अधिक शोरयुक्त हो सकता है लेकिन यह सुनिश्चित करता है कि कोई चेतावनी छूट न जाए।

---

## चरण 2: कॉन्फ़िगर किए गए विकल्पों का उपयोग करके दस्तावेज़ लोड करें  

अब जबकि चेतावनी प्रणाली तैयार है, अपने DOCX को उन `LoadOptions` के साथ लोड करें जो हमने अभी तैयार किए हैं। पाथ पूर्ण (absolute) या सापेक्ष (relative) हो सकता है; बस यह सुनिश्चित करें कि फ़ाइल मौजूद है।

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**आंतरिक रूप से क्या हो रहा है?**  

Aspose.Words दस्तावेज़ के XML को पार्स करता है, प्रत्येक `<w:font>` तत्व को हल करता है, और सिस्टम के फ़ॉन्ट कैटलॉग (और किसी भी कस्टम फ़ोल्डर को जो आपने `FontSettings` में जोड़ा हो) की जाँच करता है। जब यह किसी फ़ॉन्ट को नहीं ढूँढ़ पाता, तो यह एक चेतावनी रिकॉर्ड करता है—बिल्कुल वही जो हमें बाद में **गायब फ़ॉन्ट्स की सूची** बनाने की आवश्यकता है।

---

## चरण 3: चेतावनियों पर इटररेट करें और गायब फ़ॉन्ट विवरण निकालें  

दस्तावेज़ मेमोरी में होने पर, `Warnings` संग्रह में हर `FontSubstitutionWarning` रहता है। हम इस पर लूप करेंगे, सही प्रकार के लिए फ़िल्टर करेंगे, और एक उपयोगकर्ता‑मित्र रिपोर्ट प्रिंट करेंगे।

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**अपेक्षित आउटपुट** (मान लेते हैं कि स्रोत दस्तावेज़ `MyCustomFont` को संदर्भित करता है जो स्थापित नहीं है):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

ध्यान दें कि प्रत्येक प्रविष्टि आपको दोनों **गायब फ़ॉन्ट का नाम प्राप्त करें** (`MyCustomFont`) और फ़ॉलबैक (`Arial`) देती है। यही वह जानकारी है जिसकी आपको यह तय करने के लिए आवश्यकता है कि मूल फ़ॉन्ट को एम्बेड करें, लेखक से प्रतिस्थापन माँगें, या बस प्रतिस्थापन को स्वीकार करें।

---

## चरण 4: वैकल्पिक – आगे की प्रोसेसिंग के लिए डेटा को सूची में एकत्रित करें  

यदि आपको रिपोर्ट को CSV में निर्यात करना है, API के माध्यम से भेजना है, या बस बाद में मेमोरी में रखना है, तो आप चेतावनियों को एक स्ट्रॉन्ग‑टाइप्ड सूची में रख सकते हैं।

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

अब आपके पास **गायब फ़ॉन्ट्स की सूची** एक ऐसे फ़ॉर्मेट में है जिसे कोई भी डाउनस्ट्रीम सिस्टम उपयोग कर सकता है। चाहे आप डैशबोर्ड को फ़ीड कर रहे हों या ऑडिट लॉग बना रहे हों, डेटा तैयार है।

---

## चरण 5: एज केस और सामान्य समस्याओं को संभालना  

### एक ही रन में कई गायब फ़ॉन्ट्स  

बड़े कॉरपोरेट टेम्पलेट्स अक्सर दर्जनों कस्टम फ़ॉन्ट्स को संदर्भित करते हैं। चेतावनी संग्रह बड़ा हो सकता है, लेकिन ऊपर दिखाया गया इटररेशन पैटर्न रैखिक रूप से स्केल करता है, इसलिए प्रदर्शन की चिंता नहीं है। बस यह याद रखें कि आउटपुट को पठनीय रखें—यदि आपको गहरी विश्लेषण की आवश्यकता है तो पेज या स्टाइल के अनुसार समूह बनाना मददगार हो सकता है।

### कस्टम फ़ॉन्ट फ़ोल्डर  

यदि आप फ़ॉन्ट्स को गैर‑मानक डायरेक्टरी (जैसे, एक साझा नेटवर्क शेयर) में रखते हैं, तो Aspose.Words को बताएं कि कहां देखना है:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

दस्तावेज़ लोड करने से *पहले* यह सेट करने से लाइब्रेरी को फ़ॉन्ट्स खोजने का मौका मिलता है, जिससे कुछ चेतावनियों को पूरी तरह समाप्त किया जा सकता है।

### विशिष्ट चेतावनियों को दबाना  

कभी‑कभी आप जानते हैं कि कोई विशेष प्रतिस्थापन स्वीकार्य है (जैसे, एक सजावटी फ़ॉन्ट जिसे आप बदलने में कोई आपत्ति नहीं रखते)। आप बाद में उन्हें फ़िल्टर कर सकते हैं:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### संस्करण संगतता  

`FontSubstitutionWarningLevel` एन्नुम Aspose.Words 20.12 से स्थिर है। यदि आप पुराने संस्करण पर हैं, तो आपको चेतावनी‑लेवल फीचर का उपयोग करने के लिए अपग्रेड करना पड़ सकता है।

---

## पूर्ण कार्यशील उदाहरण  

नीचे वह पूर्ण, तैयार‑चलाने योग्य प्रोग्राम है जो ऊपर बताए गए सभी चरणों को सम्मिलित करता है। इसे एक नए कंसोल प्रोजेक्ट में पेस्ट करें, Aspose.Words NuGet पैकेज जोड़ें, और `docPath` को ऐसे दस्तावेज़ की ओर इंगित करें जो एक गायब फ़ॉन्ट को संदर्भित करता हो।

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

इस प्रोग्राम को चलाने से **फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम किया जाएगा**, **गायब फ़ॉन्ट्स का पता लगाया जाएगा**, **गायब फ़ॉन्ट का नाम प्राप्त किया जाएगा**, और **गायब फ़ॉन्ट्स की सूची** दोनों कंसोल और CSV फ़ाइल में बनाई जाएगी।

---

## निष्कर्ष  

हमने अभी-अभी वह सब कुछ कवर किया है जो आपको Aspose.Words में **फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करने** के लिए चाहिए, प्रारंभिक कॉन्फ़िगरेशन से लेकर गायब फ़ॉन्ट्स की साफ़ सूची निकालने तक। ऊपर बताए गए चरणों का पालन करके आप अपने दस्तावेज़ों का ऑडिट कर सकेंगे, दृश्य सटीकता सुनिश्चित कर सकेंगे, और सर्वर पर रेंडरिंग के समय अप्रिय आश्चर्यों से बच सकेंगे।

अगला, आप निम्नलिखित को एक्सप्लोर करना चाहेंगे:

- **गायब फ़ॉन्ट्स को एम्बेड करना** सीधे आउटपुट PDF या DOCX में (`FontSettings.EmbeddedFonts` का उपयोग करें)।
- **रिपोर्ट के आधार पर बिल्ड एजेंट्स पर फ़ॉन्ट इंस्टॉलेशन को स्वचालित करना**।
- **CI पाइपलाइन के साथ इंटीग्रेट करना** ताकि महत्वपूर्ण फ़ॉन्ट्स की अनुपस्थिति में बिल्ड फेल हो जाए।

इनको आज़माएँ, और आप एक साधारण चेतावनी प्रणाली को एक पूर्ण फ़ॉन्ट‑मैनेजमेंट वर्कफ़्लो में बदल देंगे।

कोडिंग का आनंद लें, और आपके सभी फ़ॉन्ट्स मिलें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}