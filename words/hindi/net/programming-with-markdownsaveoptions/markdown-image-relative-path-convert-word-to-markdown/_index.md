---
category: general
date: 2026-04-28
description: जब आप Word को markdown में बदलते हैं, तो markdown इमेज का रिलेटिव पाथ
  कैसे सेट करें, Word से इमेज निकालें, और एक्सपोर्ट की गई इमेज के लिए रिसोर्सेज फ़ोल्डर
  बनाएं, यह सीखें।
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: hi
og_description: Word को markdown में बदलते समय markdown इमेज का रिलेटिव पाथ सेट करें,
  Word से इमेज निकालें, और एक्सपोर्ट की गई इमेज के लिए रिसोर्सेज फ़ोल्डर बनाएं।
og_title: मार्कडाउन छवि सापेक्ष पथ – वर्ड को मार्कडाउन में बदलें
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: मार्कडाउन छवि सापेक्ष पथ – वर्ड को मार्कडाउन में बदलें
url: /hi/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – Word को Markdown में बदलें

क्या आपको **markdown image relative path** की ज़रूरत कभी पड़ी है जब आप **Word को markdown में बदलते** हैं? आप अकेले नहीं हैं। अधिकांश डेवलपर्स को समस्या आती है जब उत्पन्न किया गया Markdown छवियों को एक फ्लैट फ़ोल्डर में इंगित करता है, जिससे स्थिर साइट या GitHub रेपो में आप जो सापेक्ष लिंक संरचना अपेक्षित करते हैं, वह टूट जाती है।

इस ट्यूटोरियल में हम एक पूर्ण, एंड‑टू‑एंड समाधान के माध्यम से चलेंगे जो **Word से छवियों को निकालता है**, **एक resources फ़ोल्डर बनाता है**, और छवि रेफ़रेंसेज़ को इस तरह पुनः लिखता है कि वे एक साफ़ *markdown image relative path* का उपयोग करें। अंत तक आपके पास एक तैयार‑से‑प्रकाशित `.md` फ़ाइल और एक सुव्यवस्थित `Resources` डायरेक्टरी होगी जिसमें मूल `.docx` से निकाली गई हर तस्वीर होगी।

> **आपको क्या मिलेगा:** एक एकल C# प्रोग्राम (कोई बाहरी स्क्रिप्ट नहीं), प्रत्येक भाग के *क्यों* महत्वपूर्ण होने की स्पष्ट व्याख्या, और कुछ व्यावहारिक टिप्स जिन्हें आप अपने प्रोजेक्ट्स में कॉपी‑पेस्ट कर सकते हैं।

---

## Prerequisites

कोड में डुबने से पहले सुनिश्चित करें कि आपके पास है:

- **.NET 6.0** या बाद का संस्करण स्थापित हो (आप .NET Framework 4.7+ को भी टार्गेट कर सकते हैं, लेकिन नए प्रोजेक्ट्स के लिए .NET 6 सबसे उपयुक्त है)।
- **Aspose.Words for .NET** (लेखन के समय उपलब्ध नवीनतम NuGet पैकेज, संस्करण 23.12)। इसे इस प्रकार स्थापित करें:
  ```bash
  dotnet add package Aspose.Words
  ```
- एक Word दस्तावेज़ जिसमें वास्तव में छवियां हों—इसे हम `WithImages.docx` कहेंगे।
- एक फ़ोल्डर जहाँ आप आउटपुट markdown और छवियों को रखना चाहते हैं, उदाहरण के लिए `C:\Projects\MarkdownExport`।

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है; बाकी सब Aspose.Words द्वारा संभाला जाता है।

---

## Step 1: Load the source Word document (the starting point for convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Why this matters:* दस्तावेज़ को लोड करने से हमें आंतरिक नोड ट्री तक पहुंच मिलती है, जिसमें वे इमेज पार्ट्स शामिल होते हैं जिन्हें बाद में **export images from docx** करने की आवश्यकता होती है। यदि लोड विफल हो जाता है, तो बाद के कोई भी चरण नहीं चलेंगे, इसलिए पथ और फ़ाइल अनुमतियों की दोबारा जाँच करें।

---

## Step 2: Configure `MarkdownSaveOptions` with a custom callback (the heart of create resources folder)

`ResourceSavingCallback` हमें प्रत्येक बार जब Aspose.Words कोई इमेज फ़ाइल लिखना चाहता है, हस्तक्षेप करने की अनुमति देता है। कॉलबैक के भीतर हम **Resources सब‑फ़ोल्डर** बनाएंगे और रेफ़रेंस को इस तरह समायोजित करेंगे कि उत्पन्न markdown एक *markdown image relative path* का उपयोग करे।

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

ध्यान दें कि हमने `resourcesFolder` को कॉलबैक के कन्स्ट्रक्टर में पास किया है—यह फ़ोल्डर पथ को लचीला रखता है और कोड में स्ट्रिंग्स को हार्ड‑कोड करने से बचाता है।

---

## Step 3: Implement the callback that **creates resources folder** and rewrites the path

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Why this works:* `args.Stream` में कच्चे इमेज बाइट्स होते हैं। इसे हमारे `Resources` फ़ोल्डर के अंदर किसी फ़ाइल में कॉपी करके हम **export images from docx** सुरक्षित रूप से कर लेते हैं। फिर हम `args.ResourceFileName` को एक सापेक्ष URL (`Resources/image.png`) से बदल देते हैं। जब Aspose.Words बाद में markdown लिखता है, तो वह ठीक वही स्ट्रिंग डालता है, जिससे हमें वांछित *markdown image relative path* मिल जाता है।

---

## Step 4: Verify the generated Markdown (what the final output looks like)

`Doc.md` को किसी भी टेक्स्ट एडिटर में खोलें। आपको कुछ इस तरह दिखना चाहिए:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

महत्वपूर्ण बात यह है कि प्रत्येक इमेज रेफ़रेंस `Resources/...` की ओर इशारा करता है – यही वह **markdown image relative path** है जिसकी हमें तलाश थी।

![markdown image relative path example](example.png "markdown image relative path example")

*Tip:* यदि आप markdown को ऐसे व्यूअर में खोलते हैं जो सापेक्ष लिंक को सपोर्ट करता है (VS Code प्रीव्यू, GitHub, या कोई स्थिर साइट जेनरेटर), तो तस्वीरें बिना किसी अतिरिक्त कॉन्फ़िगरेशन के सही ढंग से रेंडर होंगी।

---

## Step 5: Common pitfalls and pro‑tips

| Issue | Why it happens | How to fix it |
|-------|----------------|---------------|
| Images end up in the root folder instead of `Resources` | कॉलबैक संलग्न नहीं था या `args.ResourceFileName` को ओवरराइट नहीं किया गया। | सुनिश्चित करें कि `ResourceSavingCallback` को `doc.Save` कॉल करने **से पहले** सेट किया गया हो। |
| Filenames contain illegal characters | Word कभी‑कभी छवियों को स्पेस या यूनिकोड प्रतीकों के साथ नाम देता है। | कॉलबैक के भीतर `args.ResourceFileName` को साफ़ करने के लिए `Path.GetInvalidFileNameChars()` का उपयोग करें। |
| Large documents take a long time to process | प्रत्येक इमेज सिंक्रोनस रूप से लिखी जाती है। | यदि आप .NET 6+ पर हैं और प्रदर्शन की आवश्यकता है, तो असिंक्रोनस I/O (`await args.Stream.CopyToAsync(fileStream)`) पर स्विच करें। |
| Relative paths break when the markdown is moved | पथ markdown फ़ाइल के स्थान के सापेक्ष होता है। | `Doc.md` और `Resources` फ़ोल्डर को साथ रखें, या कॉलबैक को इस प्रकार समायोजित करें कि अलग सापेक्ष प्रीफ़िक्स (जैसे `../assets`) उपयोग हो। |

---

## Step 6: Extending the solution (what if you need more control?)

- **Multiple output formats:** `MarkdownSaveOptions` को `HtmlSaveOptions` या `PdfSaveOptions` से बदलें जबकि वही कॉलबैक रखें—Aspose.Words फ़ॉर्मेट चाहे जो भी हो, प्रत्येक इमेज के लिए इसे कॉल करेगा।
- **Custom image naming:** यदि आप छवियों का नाम बदलना चाहते हैं (उदा., `figure-01.png`), तो फ़ाइल लिखने से पहले `args.ResourceFileName` को संशोधित करें।
- **Embedding images as Base64:** `args.ResourceFileName` को एक डेटा URI (`data:image/png;base64,...`) सेट करें और फ़ाइल लिखना छोड़ दें। यह एकल‑फ़ाइल markdown निर्यात के लिए उपयोगी है।

---

## Conclusion

अब आपके पास एक पूरी तरह कार्यात्मक C# प्रोग्राम है जो **Word को markdown में बदलता है**, **word से छवियों को निकालता है**, **एक resources फ़ोल्डर बनाता है**, और हर तस्वीर के लिए साफ़ **markdown image relative path** सुनिश्चित करता है। कोड स्वयं‑समाहित है, नवीनतम Aspose.Words संस्करण के साथ काम करता है, और किसी भी .NET प्रोजेक्ट में न्यूनतम प्रयास से डाला जा सकता है।

अगले कदम? उत्पन्न markdown को Hugo या Jekyll जैसे स्थिर साइट जेनरेटर में फीड करें, या कॉलबैक को इस प्रकार प्रयोग करें कि छवियों को सीधे Base64 स्ट्रिंग्स के रूप में एम्बेड किया जाए। यदि आप किनारे के मामलों—जैसे SVG छवियां या अत्यधिक बड़ी फ़ाइलें—से मिलते हैं, तो “Common pitfalls” तालिका को देखें; एक छोटा सा बदलाव आमतौर पर समस्या हल कर देता है।

Happy coding, and may your markdown always point to the right folder!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}