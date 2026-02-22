---
category: general
date: 2026-02-21
description: Aspose.Words का उपयोग करके C# में चेतावनियों को सक्षम करना, लापता फ़ॉन्ट्स
  का पता लगाना और docx को सुरक्षित रूप से लोड करना सीखें। चरण‑दर‑चरण मार्गदर्शिका
  का पालन करें।
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: hi
og_description: Aspose.Words के साथ चेतावनियों को सक्षम करने, लापता फ़ॉन्ट्स का पता
  लगाने और docx फ़ाइलों को सही ढंग से लोड करने का तरीका। पूर्ण कोड उदाहरण शामिल है।
og_title: DOCX लोड करते समय चेतावनियाँ सक्षम करने और गायब फ़ॉन्ट्स का पता लगाने का
  तरीका
tags:
- C#
- Aspose.Words
- Document processing
title: DOCX फ़ाइलें लोड करते समय चेतावनियों को सक्षम कैसे करें और गायब फ़ॉन्ट्स का
  पता कैसे लगाएँ
url: /hi/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

, और आपके दस्तावेज़ हमेशा ठीक वैसा ही रेंडर हों जैसा आप चाहते हैं!"

Image line: keep unchanged.

Now closing shortcodes.

We must ensure we keep all shortcodes exactly.

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX फ़ाइलें लोड करते समय चेतावनियों को सक्षम करने और लापता फ़ॉन्ट्स का पता लगाने का तरीका

क्या आपने कभी लापता फ़ॉन्ट्स के लिए **how to enable warnings** को सक्षम करने के बारे में सोचा है, इससे पहले कि वे चुपचाप आपके दस्तावेज़ रेंडरिंग को बिगाड़ दें? आप अकेले नहीं हैं—अधिकांश डेवलपर्स मानते हैं कि लाइब्रेरी बस “सही काम” करेगी, लेकिन बाद में पता चलता है कि फ़ॉन्ट बिना किसी संकेत के बदल दिया गया था।  

इस ट्यूटोरियल में हम आपको बिल्कुल **how to enable warnings**, **detect missing fonts** करने का तरीका, और Aspose.Words for .NET का उपयोग करके **how to load docx** का सही तरीका दिखाएंगे। अंत तक आपके पास एक तैयार‑चलाने योग्य उदाहरण होगा जो प्रत्येक फ़ॉन्ट प्रतिस्थापन चेतावनी को कंसोल में प्रिंट करेगा, ताकि आपको फ़ाइल के अंदर क्या हुआ, इसका अनुमान न लगाना पड़े।

## आवश्यकताएँ

- .NET 6.0 या बाद का (कोड .NET Framework 4.7+ पर भी काम करता है)  
- Visual Studio 2022 या कोई भी पसंदीदा C# IDE  
- **Aspose.Words** NuGet पैकेज (`Install-Package Aspose.Words`)  
- एक DOCX फ़ाइल जिसमें आपके मशीन पर स्थापित नहीं किए गए फ़ॉन्ट्स हो सकते हैं (हम इसे `input.docx` कहेंगे)

> **Pro tip:** यदि आपके पास परीक्षण फ़ाइल नहीं है, तो बस एक Word दस्तावेज़ खोलें जो कस्टम कॉरपोरेट फ़ॉन्ट का उपयोग करता है और उसे `input.docx` के रूप में सहेजें। यह वह चेतावनी ट्रिगर करेगा जिसे हम कैप्चर करना चाहते हैं।

## समाधान का अवलोकन

1. **Create** एक `LoadOptions` ऑब्जेक्ट `FontSubstitutionWarnings` को चालू करके बनाएं।  
2. **Load** उन विकल्पों का उपयोग करके DOCX फ़ाइल लोड करें।  
3. **Inspect** `WarningCallback` संग्रह में किसी भी `FontSubstitution` एंट्री के लिए।  
4. **React** – आप लॉग कर सकते हैं, प्रदर्शित कर सकते हैं, या प्रोग्रामेटिक रूप से लापता फ़ॉन्ट को बदल भी सकते हैं।  

नीचे हम प्रत्येक चरण को विभाजित करते हैं, *क्यों* यह महत्वपूर्ण है समझाते हैं, और आपको एक पूर्ण, चलाने योग्य कोड स्निपेट देते हैं।

---

## चरण 1: Aspose.Words स्थापित करें और प्रोजेक्ट सेट अप करें

**how to enable warnings** करने से पहले, हमें वह लाइब्रेरी चाहिए जो वास्तव में इसे समर्थन देती है।

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

या, Visual Studio पैकेज मैनेजर कंसोल में:

```powershell
Install-Package Aspose.Words
```

> **Why this step?**  
> पैकेज के बिना, `LoadOptions`, `Document`, और चेतावनी इन्फ्रास्ट्रक्चर मौजूद नहीं होते। NuGet रेफ़रेंस जोड़ने से सुनिश्चित होता है कि आप नवीनतम स्थिर संस्करण (इस लेखन के समय, 24.5) प्राप्त कर रहे हैं।

---

## चरण 2: लोड विकल्प बनाएं जो फ़ॉन्ट‑सबस्टीट्यूशन चेतावनियों को सक्षम करते हैं

`**how to enable warnings**` का मूल `LoadOptions` क्लास में है। `FontSubstitutionWarnings` को `true` सेट करने से इंजन को हर बार जब उसे लापता फ़ॉन्ट को बदलना पड़े, रिकॉर्ड करने को कहा जाता है।

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Why enable this flag?**  
> डिफ़ॉल्ट रूप से Aspose.Words चुपचाप लापता फ़ॉन्ट्स को एक फॉलबैक (आमतौर पर Arial) से बदल देता है। इससे लेआउट शिफ्ट, अदृश्य अक्षर, या ब्रांडिंग उल्लंघन हो सकते हैं। इस फ़्लैग को ऑन करने से आपको पूरी दृश्यता मिलती है।

---

## चरण 3: कॉन्फ़िगर किए गए विकल्पों का उपयोग करके DOCX फ़ाइल लोड करें

अब जब हमें पता है **how to load docx** चेतावनियों के साथ, हम वास्तव में लोड करते हैं।

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **What happens under the hood?**  
> DOCX को पार्स करते समय, Aspose.Words हर `<w:rFonts>` तत्व की जांच करता है। यदि निर्दिष्ट फ़ॉन्ट स्थापित नहीं है, तो यह एक `FontSubstitution` चेतावनी रिकॉर्ड करता है और डिफ़ॉल्ट फ़ॉन्ट पर फॉलबैक करता है। क्योंकि हमने चेतावनियों को सक्षम किया है, ये एंट्रीज़ `document.WarningCallback.Warnings` में आ जाती हैं।

---

## चरण 4: फ़ॉन्ट सबस्टीट्यूशन चेतावनियों को प्राप्त करें और प्रदर्शित करें

`WarningCallback` प्रॉपर्टी में एक `WarningInfoCollection` होता है। इसे लूप करें, `WarningType.FontSubstitution` के लिए फ़िल्टर करें, और संदेश आउटपुट करें।

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**अपेक्षित आउटपुट** (उदाहरण):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **What to do with these messages?**  
> आप उन्हें फ़ाइल में लॉग कर सकते हैं, UI में दिखा सकते हैं, या एक कस्टम फ़ॉन्ट‑फॉलबैक रूटीन को ट्रिगर कर सकते हैं। मुख्य बात यह है कि अब आप *detect missing fonts* कर रहे हैं, बजाय बाद में अनुमान लगाने के।

---

## चरण 5: (वैकल्पिक) लापता फ़ॉन्ट्स को एक विशिष्ट फॉलबैक से बदलें

यदि आपके पास एक कॉरपोरेट फ़ॉन्ट है जिसे आप लागू करना चाहते हैं, तो आप चेतावनियों को संभाल सकते हैं और उन्हें तुरंत बदल सकते हैं।

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Why consider this?**  
> यह सभी उत्पन्न दस्तावेज़ों में दृश्य स्थिरता सुनिश्चित करता है, जो ब्रांड अनुपालन के लिए महत्वपूर्ण है।

---

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक एकल C# फ़ाइल है जिसे आप कॉपी‑पेस्ट करके एक कंसोल ऐप में उपयोग कर सकते हैं। यह सब कुछ कवर करता है—पैकेज स्थापित करने से लेकर चेतावनियों को प्रिंट करने तक।

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Run it**: प्रोजेक्ट फ़ोल्डर से `dotnet run` चलाएँ। यदि कोई फ़ॉन्ट लापता है, तो आप चेतावनियों को प्रिंट होते देखेंगे, और वैकल्पिक प्रतिस्थापन फ़ाइल सहेजने से पहले लागू हो जाएगा।

---

## अक्सर पूछे जाने वाले प्रश्न

### क्या यह PDF रूपांतरण के साथ भी काम करता है?

हाँ। चेतावनियों को संभालने के बाद, आप `doc.Save("output.pdf")` कॉल कर सकते हैं और प्रतिस्थापित फ़ॉन्ट्स PDF में उसी तरह दिखाई देंगे जैसे DOCX में होते हैं।

### यदि मुझे किसी विशिष्ट फ़ॉन्ट के लिए चेतावनियों को दबाना हो तो क्या करें?

आप उन्हें लूप में फ़िल्टर कर सकते हैं—सिर्फ उस `WarningInfo` को स्किप करें जिसका `Message` उस फ़ॉन्ट नाम को शामिल करता है जिसे आप अनदेखा करना चाहते हैं।

### क्या `FontSubstitutionWarnings` पुराने Aspose.Words संस्करणों में उपलब्ध है?

यह संस्करण 20.5 में पेश किया गया था। यदि आप पुराने रिलीज़ पर फंसे हैं, तो NuGet के माध्यम से अपग्रेड करें; API परिवर्तन बैकवर्ड‑कम्पैटिबल है।

---

## निष्कर्ष

हमने **how to enable warnings** की प्रक्रिया को समझाया, आपको **detect missing fonts** दिखाया, और Aspose.Words के साथ **how to load docx** का सही तरीका प्रदर्शित किया, जबकि फ़ॉन्ट सबस्टीट्यूशन पर पूरी दृश्यता रखी। `document.WarningCallback.Warnings` की जांच करके आपको एक विश्वसनीय ऑडिट ट्रेल मिलता है—अब कोई चुपचाप फॉलबैक नहीं।

अगले कदम? चेतावनी लॉजिक को Serilog जैसे लॉगिंग फ्रेमवर्क में जोड़ने का प्रयास करें, या एक UI बनाएं जो उपयोगकर्ताओं को दस्तावेज़ भेजने से पहले लापता फ़ॉन्ट्स को हाइलाइट करे। आप `FontSettings` क्लास को भी एक्सप्लोर कर सकते हैं ताकि फ़ॉन्ट सबस्टीट्यूशन नीतियों पर अधिक सूक्ष्म नियंत्रण मिल सके।

कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा ठीक वैसा ही रेंडर हों जैसा आप चाहते हैं!

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}