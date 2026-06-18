---
category: general
date: 2026-06-17
description: Aspose.Words में फ़ॉन्ट प्रतिस्थापन को संभालें और .NET डेवलपर्स के लिए
  इस चरण‑दर‑चरण ट्यूटोरियल के साथ गायब फ़ॉन्ट्स को जल्दी पहचानें।
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: hi
og_description: Aspose.Words में फ़ॉन्ट प्रतिस्थापन को संभालें और स्पष्ट कोड उदाहरणों
  के साथ अपने दस्तावेज़ों में गायब फ़ॉन्ट्स का पता लगाना सीखें।
og_title: Aspose.Words में फ़ॉन्ट प्रतिस्थापन को संभालें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Aspose.Words में फ़ॉन्ट प्रतिस्थापन को संभालें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में फ़ॉन्ट प्रतिस्थापन को संभालें – पूर्ण प्रोग्रामिंग गाइड

क्या आप कभी सोचते थे कि **फ़ॉन्ट प्रतिस्थापन को कैसे संभालें** जब कोई Word दस्तावेज़ सर्वर पर स्थापित नहीं किए गए फ़ॉन्ट को संदर्भित करता है? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया के ऐप्स—जैसे इनवॉइस जेनरेटर या स्वचालित रिपोर्ट सेवाएँ—में अनुपलब्ध फ़ॉन्ट्स चुपचाप फॉलबैक होते हैं जो लेआउट को बिगाड़ देते हैं।  

अच्छी खबर यह है कि Aspose.Words आपको एक बिल्ट‑इन चेतावनी प्रणाली देता है जो आपको **अनुपलब्ध फ़ॉन्ट्स का पता लगाने** और अपनी इच्छानुसार प्रतिक्रिया देने की अनुमति देती है। इस ट्यूटोरियल में हम एक चेतावनी हैंडलर को रजिस्टर करने, दस्तावेज़ लोड करने, और उन सटीक फ़ॉन्ट‑प्रतिस्थापन घटनाओं को निकालने की प्रक्रिया को चरण‑दर‑चरण देखेंगे जिनके बारे में आपको जानना आवश्यक है। अंत तक आप यह भी देखेंगे कि क्लासिक “**अनुपलब्ध फ़ॉन्ट्स का पता कैसे लगाएँ**?” प्रश्न का उत्तर साफ़, प्रोडक्शन‑रेडी कोड के साथ कैसे दिया जाता है।

## इस ट्यूटोरियल में क्या कवर किया गया है

* Aspose.Words को हर फ़ॉन्ट प्रतिस्थापन के लिए चेतावनी उत्पन्न करने के लिए सेट करना।
* उन चेतावनियों को एक कस्टम हैंडलर में कैप्चर करना ताकि आप लॉग, बदल या रोक सकें।
* कैप्चर किए गए डेटा का उपयोग करके **अनुपलब्ध फ़ॉन्ट्स का पता** लगाना, इससे पहले कि दस्तावेज़ सहेजा या रेंडर किया जाए।
* एज केसों के लिए ट्रबलशूटिंग टिप्स—जैसे जब फॉलबैक फ़ॉन्ट चुपचाप चुना जाता है।
* एक पूर्ण, चलाने योग्य उदाहरण जो आप किसी भी .NET कंसोल ऐप में डाल सकते हैं।

> **Prerequisites** – आपको एक हालिया .NET SDK (6.0+ ठीक काम करता है), एक वैध Aspose.Words for .NET लाइसेंस (या एक अस्थायी इवैल्यूएशन की), और एक सैंपल DOCX चाहिए जिसमें जानबूझकर ऐसा फ़ॉन्ट संदर्भित हो जो आपके सिस्टम में स्थापित न हो। अन्य कोई थर्ड‑पार्टी लाइब्रेरी आवश्यक नहीं है।

---

## ## कस्टम चेतावनी हैंडलर के साथ फ़ॉन्ट प्रतिस्थापन को संभालें

Aspose.Words हर बार जब वह अनुरोधित फ़ॉन्ट नहीं पा पाता है, एक `WarningInfo` ऑब्जेक्ट उठाता है। डिफ़ॉल्ट रूप से उन चेतावनियों को अनदेखा किया जाता है, इसलिए अक्सर आपको प्रतिस्थापन का पता नहीं चलता। **फ़ॉन्ट प्रतिस्थापन को संभालने** के लिए, आप डिफ़ॉल्ट चेतावनी हैंडलर को ऐसे हैंडलर से बदलते हैं जो वास्तव में कुछ करे।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### यह क्यों काम करता है

* `FontSettings.DefaultWarningHandler` एक ग्लोबल स्टैटिक प्रॉपर्टी है—एक बार सेट करने के बाद, **हर** Aspose.Words ऑपरेशन वर्तमान AppDomain में आपका डेलीगेट उपयोग करता है।
* `WarningInfoCollectionHandler` को एक `WarningInfo` ऑब्जेक्ट मिलता है जिसमें `WarningType` और एक मानव‑पठनीय `Description` होता है। `WarningType.FontSubstitution` पर फ़िल्टर करने से आप केवल उन घटनाओं को देख पाते हैं जिनमें आपकी रुचि है।
* `doc.Save` कॉल करने से लाइब्रेरी सभी फ़ॉन्ट्स को रिजॉल्व करती है, और उसी समय चेतावनियां फायर होती हैं। यदि आपको दस्तावेज़ को सहेजे बिना निरीक्षण करना है, तो आप `doc.UpdatePageLayout()` कॉल कर सकते हैं।

**अपेक्षित कंसोल आउटपुट** (मान लेते हैं कि अनुपलब्ध फ़ॉन्ट “Papyrus” है):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

यह लाइन यह प्रमाण है कि लाइब्रेरी **अनुपलब्ध फ़ॉन्ट्स का पता लगा** और एक फॉलबैक चुना।

---

## ## रेंडरिंग से पहले अनुपलब्ध फ़ॉन्ट्स का पता लगाएँ

कभी‑कभी आप पूरी प्रक्रिया को रोकना चाहते हैं यदि कोई आवश्यक फ़ॉन्ट अनुपलब्ध है—शायद क्योंकि ब्रांड गाइडलाइन सटीक टाइपोग्राफी की मांग करती हैं। चेतावनी हैंडलर को विस्तारित करके सभी अनुपलब्ध‑फ़ॉन्ट संदेशों को एक सूची में एकत्र किया जा सकता है, फिर आप निर्णय ले सकते हैं।

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### यह “अनुपलब्ध फ़ॉन्ट्स का पता कैसे लगाएँ” प्रश्न का उत्तर कैसे देता है

* `missingFonts` सूची प्रत्येक प्रतिस्थापन घटना की एक लेज़र की तरह काम करती है।
* `UpdatePageLayout` के बाद, आप सूची को निरीक्षण कर सकते हैं और तय कर सकते हैं कि आगे बढ़ना है, लॉग करना है या एक्सेप्शन उठाना है।
* यह पैटर्न किसी भी आउटपुट फ़ॉर्मेट (PDF, HTML, इमेज) के लिए काम करता है क्योंकि चेतावनी प्रणाली फ़ॉर्मेट‑अज्ञेय है।

---

## ## उन्नत टिप: अनुपलब्ध फ़ॉन्ट्स को एक विशिष्ट प्रतिस्थापन से बदलें

यदि आपके पास एक कॉरपोरेट फ़ॉन्ट है जिसे उपयोग करना अनिवार्य है, तो आप Aspose.Words को बता सकते हैं कि वह किसी भी अनुपलब्ध फ़ॉन्ट को स्वचालित रूप से आपके फॉलबैक से बदल दे। यह तब उपयोगी होता है जब आप चाहते हैं कि दस्तावेज़ *फिर भी* मैनुअल पोस्ट‑प्रोसेसिंग के बिना स्वीकार्य दिखे।

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

ऊपर दिया गया स्निपेट **दस्तावेज़ लोड करने से पहले** रखें। अब कोई भी अनुपलब्ध फ़ॉन्ट—भले ही उसका मूल नाम कुछ भी हो—“Calibri” (या यदि Calibri उपलब्ध नहीं है तो “Arial”) से बदल दिया जाएगा। आपको अभी भी चेतावनी मिलेगी, लेकिन दस्तावेज़ आपके नियंत्रित फ़ॉन्ट के साथ रेंडर होगा।

---

## ## सामान्य गलतियाँ और उन्हें कैसे टालें

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **पहली कॉल के बाद चेतावनियां गायब हो जाती हैं** | स्टैटिक `DefaultWarningHandler` बाद में ऐप में ओवरराइट हो जाता है। | हैंडलर को **एक बार** एप्लिकेशन स्टार्ट पर सेट करें, या रेफ़रेंस को स्टोर करके आवश्यकता पड़ने पर पुनः‑असाइन करें। |
| **केवल पहला अनुपलब्ध फ़ॉन्ट रिपोर्ट होता है** | कुछ API चेतावनियों को बैच में भेजते हैं; आपको `UpdatePageLayout` या `Save` कॉल करके कतार को फ्लश करना पड़ता है। | लेआउट अपडेट फोर्स करें या वह फ़ॉर्मेट सहेजें जिसे आप जनरेट करना चाहते हैं। |
| **अबॉर्ट करने के बाद भी प्रतिस्थापन जारी रहता है** | चेतावनी हैंडलर *फ़ॉन्ट प्रतिस्थापन के बाद* चलता है। | हैंडलर में **लॉग** करें और फिर एक्सेप्शन थ्रो करके आगे की प्रोसेसिंग रोकें। |
| **Linux कंटेनर में फ़ॉन्ट्स गायब हैं** | Linux में अक्सर Windows फ़ॉन्ट कैटलॉग नहीं होता, जिससे कई प्रतिस्थापन होते हैं। | आवश्यक फ़ॉन्ट्स को कंटेनर में माउंट करें या `FontSettings.SetFontsFolder` का उपयोग करके कस्टम फ़ॉन्ट डायरेक्टरी की ओर इशारा करें। |

---

## ## वेब API परिदृश्य में फ़ॉन्ट प्रतिस्थापन का पता लगाएँ

यदि आप ASP.NET Core के माध्यम से दस्तावेज़ सर्व कर रहे हैं, तो संभवतः आप कंसोल राइट्स नहीं चाहते। इसके बजाय, चेतावनियों को इकट्ठा करें और उन्हें HTTP रिस्पॉन्स का हिस्सा बनाकर लौटाएँ।

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

अब API **अनुपलब्ध फ़ॉन्ट्स का पता लगाता** है और कोई भी PDF जनरेट होने से पहले एक स्पष्ट JSON पेलोड लौटाता है। यह “अनुपलब्ध फ़ॉन्ट्स का पता कैसे लगाएँ” प्रश्न का एक व्यावहारिक उदाहरण है जो प्रोडक्शन‑ग्रेड सर्विस में लागू होता है।

---

## ## अपनी इम्प्लीमेंटेशन का परीक्षण करें

1. **एक टेस्ट DOCX बनाएँ** जिसमें ऐसा फ़ॉन्ट संदर्भित हो जो मशीन पर नहीं है (उदाहरण: न्यूनतम Docker इमेज पर “Comic Sans MS”)।  
2. कंसोल ऐप या API एंडपॉइंट चलाएँ।  
3. सत्यापित करें कि कंसोल (या HTTP रिस्पॉन्स) में प्रतिस्थापन चेतावनी सूचीबद्ध है।  
4. वैकल्पिक रूप से, उत्पन्न PDF खोलें और फ़ॉन्ट प्रॉपर्टीज़ जांचें—Aspose.Words को आपके कॉन्फ़िगर किए गए फॉलबैक फ़ॉन्ट को दिखाना चाहिए।

यदि आपको चेतावनी मिलती है लेकिन PDF अभी भी अप्रत्याशित फ़ॉन्ट उपयोग करता है, तो `SubstitutionSettings` क्रम को दोबारा जाँचें; पहला मिलान जीतता है।

---

## ## निष्कर्ष

हमने Aspose.Words में **फ़ॉन्ट प्रतिस्थापन को संभालने** के लिए आवश्यक सभी पहलुओं को कवर किया है, चेतावनी हैंडलर को रजिस्टर करने से लेकर प्रोग्रामेटिक रूप से **अनुपलब्ध फ़ॉन्ट्स का पता लगाने** और उन्हें कॉरपोरेट टाइपफ़ेस से बदलने तक। बिल्ट‑इन चेतावनी प्रणाली का उपयोग करके आप हर “फ़ॉन्ट नहीं मिला” घटना पर पूरी दृश्यता प्राप्त करते हैं, जो सीधे “**अनुपलब्ध फ़ॉन्ट्स का पता कैसे लगाएँ**?” प्रश्न का उत्तर देता है, जिसे हर डेवलपर दस्तावेज़ जनरेशन ऑटोमेशन में पूछता है।

अगला क्या? इस लॉजिक को **डायनामिक फ़ॉन्ट लोडिंग** (`FontSettings.SetFontsFolder`) के साथ मिलाकर उपयोगकर्ता‑अपलोडेड फ़ॉन्ट्स को ऑन‑द‑फ़्लाई सपोर्ट करने की कोशिश करें, या चेतावनी हैंडलर को विस्तारित करके Serilog जैसी सेंट्रल लॉगिंग सर्विस में एंट्री लिखें। जितना अधिक आप फ़ॉन्ट हैंडलिंग को इंस्ट्रूमेंट करेंगे, आपका डॉक्यूमेंट पाइपलाइन उतना ही भरोसेमंद बन जाएगा।

क्या आपके पास कोई जटिल फ़ॉन्ट‑प्रतिस्थापन परिदृश्य है जिस पर आप संघर्ष कर रहे हैं? नीचे कमेंट करें, और चलिए साथ मिलकर ट्रबलशूट करते हैं। हैप्पी कोडिंग!

## आगे आप क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Aspose.Words में फ़ॉन्ट्स का पता कैसे लगाएँ – चेतावनियों और सेटिंग्स को संभालें](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – पूर्ण गाइड](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [DOCX को लोड करें और अनुपलब्ध फ़ॉन्ट्स का पता लगाएँ – पूर्ण C# गाइड](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}