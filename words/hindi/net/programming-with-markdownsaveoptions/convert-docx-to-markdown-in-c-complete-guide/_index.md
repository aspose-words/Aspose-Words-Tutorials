---
category: general
date: 2026-03-25
description: Aspose.Words का उपयोग करके Word से चित्र निकालते हुए DOCX को जल्दी से
  Markdown में बदलें। पूर्ण कोड के साथ चरण‑दर‑चरण सीखें।
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: hi
og_description: Aspose.Words के साथ DOCX को Markdown में बदलें और Word से चित्र निकालें।
  तैयार‑से‑चलाने वाले समाधान के लिए इस पूर्ण ट्यूटोरियल का पालन करें।
og_title: C# में DOCX को Markdown में बदलें – चरण‑दर‑चरण गाइड
tags:
- Aspose.Words
- C#
- Markdown
title: C# में DOCX को Markdown में बदलें – पूर्ण गाइड
url: /hi/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert DOCX to Markdown with Aspose.Words

क्या आपको कभी **DOCX को markdown में बदलने** की ज़रूरत पड़ी है लेकिन एम्बेडेड चित्रों को कैसे रखें, समझ नहीं आया? आप अकेले नहीं हैं—कई डेवलपर्स को यह समस्या आती है जब वे Word कंटेंट को static‑site generator या डॉक्यूमेंटेशन रेपो में ले जाने की कोशिश करते हैं।  
अच्छी खबर यह है कि Aspose.Words for .NET यह काम आपके लिए कर सकता है, और एक छोटे कॉलबैक के साथ आप **Word फ़ाइलों से चित्र भी निकाल सकते** हैं।

इस ट्यूटोरियल में हम एक वास्तविक उदाहरण के माध्यम से दिखाएंगे कि कैसे एक `.docx` फ़ाइल को लोड करें, उसे Markdown फ़ाइल के रूप में सेव करें, और हर चित्र को एक समर्पित फ़ोल्डर में लिखें। अंत तक आपके पास एक तैयार‑to‑run कंसोल ऐप होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

> **प्रो टिप:** यदि आपको केवल टेक्स्ट चाहिए और चित्रों की परवाह नहीं है, तो आप `ResourceSavingCallback` को पूरी तरह छोड़ सकते हैं – कोड फिर भी साफ़ Markdown उत्पन्न करेगा।

## What You’ll Need

- **Aspose.Words for .NET** (नवीनतम संस्करण, उदाहरण के लिए, 24.12)। आप इसे NuGet से प्राप्त कर सकते हैं: `Install-Package Aspose.Words`।
- **.NET 6.0** या बाद का संस्करण (API .NET Framework पर भी काम करता है, लेकिन .NET 6 सबसे बेहतर प्रदर्शन देता है)।
- एक साधा कंसोल प्रोजेक्ट या कोई भी C# होस्ट जो आप पसंद करें।
- एक इनपुट Word फ़ाइल (`input.docx`) जिसमें कम से कम एक चित्र हो ताकि हम एक्सट्रैक्शन को देख सकें।

बस इतना ही—कोई अतिरिक्त लाइब्रेरी नहीं, कोई जटिल कमांड‑लाइन टूल नहीं। चलिए शुरू करते हैं।

![डॉक्‍स को मार्कडाउन में बदलने का उदाहरण](images/convert-docx-to-markdown.png)

*Image alt text: डॉक्‍स को मार्कडाउन में बदलने का उदाहरण*

## Step 1 – Set Up the Project and Add Aspose.Words

साफ‑सुथरा रखने के लिए, एक नया कंसोल ऐप बनाएं:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

`Program.cs` खोलें और ऑटो‑जनरेटेड कोड को हटा दें। हम बाद में पूरा समाधान पेस्ट करेंगे, लेकिन अभी के लिए सुनिश्चित करें कि प्रोजेक्ट बिल्ड हो रहा है।

## Step 2 – Load the Source DOCX

पहला कदम है Aspose.Words को Word फ़ाइल पढ़ने के लिए बताना। यह ऑपरेशन **तेज़** है—लाइब्रेरी दस्तावेज़ संरचना को पार्स करती है बिना Word को खोले।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

हम `Path.Combine` में पाथ को रैप क्यों करते हैं? यह कोड को Windows, macOS, और Linux पर पोर्टेबल बनाता है—जब आप प्रोजेक्ट को CI पाइपलाइन में ले जाते हैं तो यह बहुत काम आता है।

## Step 3 – Configure Markdown Save Options with a Resource Callback

जब आप Aspose.Words को Markdown में सेव करने को कहते हैं, तो यह सामान्यतः चित्रों को Base64 स्ट्रिंग्स के रूप में एम्बेड करता है। छोटे आइकन के लिए यह ठीक है, लेकिन बड़े फ़ोटो के लिए फ़ाइल साइज बहुत बढ़ जाता है। इसके बजाय, हम **resource‑saving callback** जोड़ते हैं जो प्रत्येक चित्र को डिस्क पर लिखता है और Markdown लिंक को अपडेट करता है।

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

ध्यान दें कि हम `resourcesDir` को कॉलबैक के कन्स्ट्रक्टर में पास कर रहे हैं—यह पाथ लॉजिक को कॉलबैक से बाहर रखता है और क्लास को पुन: उपयोग योग्य बनाता है।

## Step 4 – Implement the Resource‑Saving Callback

कॉलबैक `IResourceSavingCallback` को इम्प्लीमेंट करता है। प्रत्येक चित्र के लिए जिसे Aspose.Words लिखना चाहता है, वह हमें एक `ResourceSavingArgs` ऑब्जेक्ट देता है। हम तय करते हैं **कहाँ** फ़ाइल को स्टोर करना है, उसे एक यूनिक नाम देते हैं, और फिर इंजन को उसके डिफ़ॉल्ट सेविंग बिहेवियर को स्किप करने के लिए कहते हैं।

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**यह क्यों महत्वपूर्ण है:** `args.Uri` सेट करके हम यह नियंत्रित करते हैं कि परिणामी `.md` फ़ाइल में चित्र कैसे रेफ़र किया जाएगा। रिलेटिव पाथ `Resources/img_0.png` VS Code, GitHub, या किसी static‑site generator में Markdown खोलने पर भी काम करता है।

## Step 5 – Save the Document as Markdown

अब अंतिम चरण: Aspose.Words को Markdown फ़ाइल लिखने को कहें। हमने जो कॉलबैक सेट किया है, वह प्रत्येक चित्र के लिए स्वचालित रूप से फायर होगा।

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

जब यह लाइन समाप्त होगी, आपके पास होगा:

- `output.md` – मूल Word कंटेंट का एक साफ़ Markdown प्रतिनिधित्व।
- `Resources/` फ़ोल्डर – जिसमें DOCX से निकाले गए सभी चित्र होंगे।

## Full Working Example

नीचे **पूरा, कॉपी‑पेस्ट‑रेडी** प्रोग्राम दिया गया है। `YOUR_DIRECTORY` को उस एब्सोल्यूट या रिलेटिव पाथ से बदलें जहाँ आपका `input.docx` स्थित है।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### Expected Output

`Output/output.md` को किसी भी Markdown व्यूअर में खोलें और आपको कुछ इस तरह दिखना चाहिए:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

`Resources` फ़ोल्डर में `img_0.png`, `img_1.jpg` आदि होंगे, जो मूल रूप से `input.docx` में एम्बेड किए गए चित्रों से मेल खाते हैं।

## Frequently Asked Questions (FAQ)

**क्या यह .doc फ़ाइलों के साथ काम करता है?**  
हां। Aspose.Words `.doc`, `.docx`, `.rtf`, और कई अन्य फॉर्मैट लोड कर सकता है। बस `inputPath` में फ़ाइल एक्सटेंशन बदल दें।

**यदि मुझे चित्रों के लिए एब्सोल्यूट URLs चाहिए तो क्या करें?**  
`args.Uri = $"Resources/{fileName}";` को बदलकर कुछ इस तरह रखें: `args.Uri = $"https://mycdn.com/docs/{fileName}";`। तब Markdown रिमोट लोकेशन को रेफ़र करेगा।

**क्या मैं चित्र की क्वालिटी या फॉर्मैट को नियंत्रित कर सकता हूँ?**  
कॉलबैक मूल इमेज स्ट्रीम प्राप्त करता है। यदि आप PNG को JPEG में बदलना चाहते हैं, तो आप स्ट्रीम को `System.Drawing.Image` में लोड करके री‑एन्कोड कर सकते हैं और नए बाइट्स को `args.Uri` सेट करने से पहले लिख सकते हैं।

**क्या `ResourceSavingCallback` थ्रेड‑सेफ़ है?**  
Aspose.Words प्रत्येक रिसोर्स के लिए कॉलबैक को क्रमिक (sequential) रूप से कॉल करता है, इसलिए  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}