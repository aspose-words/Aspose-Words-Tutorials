---
category: general
date: 2026-02-28
description: C# का उपयोग करके Aspose.Words में फ़ॉन्ट चेतावनियों को संभालना और गायब
  फ़ॉन्ट्स का पता लगाना सीखें। पूर्ण कोड के साथ चरण‑दर‑चरण गाइड।
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: hi
og_description: Aspose.Words में फ़ॉन्ट चेतावनियों को संभालें और तैयार‑से‑चलाने वाले
  C# उदाहरण के साथ गायब फ़ॉन्ट्स का पता लगाएँ। चरणों का पालन करें और आउटपुट देखें।
og_title: Aspose.Words में फ़ॉन्ट चेतावनियों को संभालें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Document Loading
title: Aspose.Words में फ़ॉन्ट चेतावनियों को संभालें – गायब फ़ॉन्ट्स का पता लगाएँ
url: /hi/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में फ़ॉन्ट चेतावनियों को संभालें – लापता फ़ॉन्ट्स का पता लगाएँ

क्या आपको कभी Word दस्तावेज़ लोड करते समय **फ़ॉन्ट चेतावनियों** को संभालना पड़ा और आश्चर्य हुआ कि कुछ टेक्स्ट अजीब क्यों दिख रहा है? आप अकेले नहीं हैं। लापता फ़ॉन्ट्स प्रतिस्थापन चेतावनियों को ट्रिगर करते हैं जो चुपचाप विज़ुअल लेआउट को बिगाड़ सकते हैं, और यदि आप **लापता फ़ॉन्ट्स का पता नहीं लगाते** तो आपको कभी नहीं पता चलेगा कि क्या गलत हुआ।

इस ट्यूटोरियल में हम आपको Aspose.Words के `IWarningCallback` का उपयोग करके **फ़ॉन्ट चेतावनियों** को संभालने का व्यावहारिक तरीका दिखाएंगे। गाइड के अंत तक आप हर फ़ॉन्ट‑सबस्टीट्यूशन इवेंट को पहचान पाएँगे, उसे लॉग करेंगे, और यहाँ तक कि लोड को रोकने का निर्णय भी ले सकेंगे। कोई बाहरी दस्तावेज़ नहीं, सिर्फ एक ही, कॉपी‑पेस्ट‑तैयार उदाहरण।

## आप क्या सीखेंगे

- फ़ॉन्ट‑सबस्टीट्यूशन अलर्ट्स पर ही प्रतिक्रिया देने वाला कस्टम चेतावनी हैंडलर सेट करें।  
- `LoadOptions` में हैंडलर को अटैच करें ताकि हर दस्तावेज़ लोड इस पर चले।  
- कंसोल में आउटपुट को वेरिफ़ाई करें और समझें कि प्रत्येक चेतावनी का क्या मतलब है।  

**आवश्यकताएँ**

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.6+ के साथ भी काम करता है)।  
- NuGet (`Install-Package Aspose.Words`) के माध्यम से स्थापित Aspose.Words for .NET।  
- एक Word फ़ाइल जो आपके मशीन पर स्थापित नहीं होने वाले फ़ॉन्ट को रेफ़रेंस करती है (जैसे, एक कस्टम कॉरपोरेट फ़ॉन्ट)।  

यदि आपके पास इनमें से कोई भी नहीं है, तो अभी प्राप्त करें—अन्यथा, चलिए शुरू करते हैं।

## Aspose.Words में फ़ॉन्ट चेतावनियों को कैसे संभालें

नीचे पूरा, चलाने योग्य प्रोग्राम दिया गया है। इसमें `using` स्टेटमेंट्स से लेकर `Main` मेथड तक सब कुछ शामिल है, इसलिए आप इसे एक कंसोल ऐप में डालकर **F5** दबा सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **अपेक्षित कंसोल आउटपुट** (मान लेते हैं कि दस्तावेज़ में वह फ़ॉन्ट उपयोग किया गया है जो आपके पास स्थापित नहीं है):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

यदि दस्तावेज़ में **कोई लापता फ़ॉन्ट नहीं** है, तो चेतावनी लाइन कभी नहीं दिखती—इसलिए आपने प्रभावी रूप से केवल आवश्यकता पड़ने पर **लापता फ़ॉन्ट्स का पता लगाया** है।

### यह क्यों काम करता है

Aspose.Words फ़ाइल को पार्स करते समय मिलने वाले प्रत्येक गैर‑क्रिटिकल इश्यू के लिए एक `WarningInfo` थ्रो करता है। `IWarningCallback` को इम्प्लीमेंट करके आप उस पाइपलाइन में एक हुक प्राप्त करते हैं। `WarningType.FontSubstitution` फ़्लैग आपको सटीक रूप से बताता है कि लाइब्रेरी को अनुरोधित फ़ॉन्ट को फ़ॉलबैक से बदलना पड़ा। यह **फ़ॉन्ट चेतावनियों** को संभालने का सबसे भरोसेमंद तरीका है क्योंकि यह *लोडिंग के दौरान* चलता है, दस्तावेज़ ऑब्जेक्ट मॉडल को छूने से पहले।

## अपने ऐप को तोड़े बिना लापता फ़ॉन्ट्स का पता लगाएँ

कभी‑कभी आप लापता फ़ॉन्ट को फेटल एरर मानना चाह सकते हैं—शायद आपके ब्रांडिंग गाइडलाइन किसी भी प्रतिस्थापन को प्रतिबंधित करती हैं। आप हैंडलर को केवल लॉग करने के बजाय एक्सेप्शन थ्रो करने के लिए संशोधित कर सकते हैं:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

अब `new Document(...)` के चारों ओर का `try…catch` ब्लॉक समस्या को कैप्चर करेगा, जिससे आप तय कर सकेंगे कि लोड को रोकना है, फ़ॉलबैक करना है, या उपयोगकर्ता को प्रॉम्प्ट करना है।

## बोनस: UI एप्लिकेशन में चेतावनियों को विज़ुअलाइज़ करना

यदि आप WinForms या WPF ऐप बना रहे हैं, तो `Console.WriteLine` को एक UI‑फ़्रेंडली कॉल से बदलें:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

इस तरह, अंतिम‑उपयोगकर्ता तुरंत चेतावनी देखेंगे, और आप अभी भी सभी प्लेटफ़ॉर्म पर **फ़ॉन्ट चेतावनियों** को लगातार संभालेंगे।

## सामान्य जाल और प्रो टिप्स

- **Pitfall:** `WarningCallback` सेट करना भूल जाना। डिफ़ॉल्ट व्यवहार फ़ॉन्ट चेतावनियों को अनदेखा करना है, इसलिए आप उन्हें कभी नहीं देखेंगे।  
  **Pro tip:** चेतावनी हैंडलर की ज़रूरत हो तो भी हमेशा एक `LoadOptions` इंस्टेंस बनाएं। यह सस्ता और स्पष्ट है।  

- **Pitfall:** गैर‑Windows OS पर गलत पाथ सेपरेटर का उपयोग करना।  
  **Pro tip:** `Path.Combine` या रॉ स्ट्रिंग लिटरल (`@"C:\Docs\MissingFont.docx"` Windows पर काम करता है; Linux पर `"/home/user/docs/MissingFont.docx"` उपयोग करें) का प्रयोग करें।  

- **Pitfall:** यह मान लेना कि एम्बेडेड फ़ॉन्ट्स के लिए भी चेतावनी फायर होगी।  
  **Pro tip:** एम्बेडेड फ़ॉन्ट्स को मौजूद माना जाता है, इसलिए कोई सबस्टीट्यूशन चेतावनी नहीं आती। हैंडलर को सक्रिय देखना हो तो वास्तव में *लापता* फ़ॉन्ट्स के साथ टेस्ट करें।  

- **Pitfall:** हर चेतावनी प्रकार को अधिक लॉग करना।  
  **Pro tip:** जैसा दिखाया गया है, `WarningType.FontSubstitution` द्वारा फ़िल्टर करें—यह कंसोल को साफ़ रखता है और **लापता फ़ॉन्ट्स का पता लगाने** परिदृश्य पर ध्यान केंद्रित करता है।  

## पूर्ण कार्यशील उदाहरण का सारांश

यहाँ पूरा प्रोग्राम फिर से दिया गया है, इस बार बिना टिप्पणियों के, उन लोगों के लिए जो साफ़ दृश्य पसंद करते हैं:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

कॉपी, पेस्ट, रन—आपका कंसोल अब स्वचालित रूप से **फ़ॉन्ट चेतावनियों** को संभालेगा और **लापता फ़ॉन्ट्स** का पता लगाएगा।

## अगले कदम

- **Log to a file:** `Console.WriteLine` को एक लॉगर (जैसे, NLog) से बदलें ताकि प्रोडक्शन‑ग्रेड ट्रेसिंग हो सके।  
- **Batch processing:** दस्तावेज़ों के फ़ोल्डर पर लूप चलाएँ, सभी फ़ॉन्ट‑सबस्टीट्यूशन इवेंट्स को CSV रिपोर्ट में इकट्ठा करें।  
- **Automatic font installation:** लोडिंग जारी रखने से पहले लापता फ़ॉन्ट्स को कॉरपोरेट रिपॉजिटरी से डाउनलोड करने के लिए चेतावनी हैंडलर में हुक करें।  

इनमें से प्रत्येक विस्तार **फ़ॉन्ट चेतावनियों** को साफ़, पुन: उपयोग योग्य तरीके से संभालने के मूल विचार पर आधारित है।

---

*कोडिंग का आनंद लें! यदि आप **लापता फ़ॉन्ट्स** का पता लगाने की कोशिश में कोई अजीब समस्या का सामना करते हैं, तो नीचे टिप्पणी छोड़ें। मैं खुशी से आपकी समस्या हल करने में मदद करूंगा।*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}