---
category: general
date: 2026-04-07
description: एक कॉलबैक का उपयोग करके Word को Markdown के रूप में सहेजें और docx से
  छवियों को निकालें। जानें कि कॉलबैक का उपयोग करके मार्कडाउन इमेज फ़ोल्डर को प्रभावी
  ढंग से कैसे संग्रहीत किया जाए।
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: hi
og_description: Word को Markdown के रूप में सहेजें और callback का उपयोग करके docx
  से छवियों को निकालें। यह गाइड दिखाता है कि callback का उपयोग करके markdown इमेज
  फ़ोल्डर कैसे बनाएं।
og_title: वर्ड को मार्कडाउन के रूप में सहेजें – पूर्ण चरण‑दर‑चरण गाइड
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: कस्टम इमेज फ़ोल्डर के साथ वर्ड को मार्कडाउन में सहेजें – पूर्ण गाइड
url: /hi/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word को Markdown के रूप में सहेजें – पूर्ण चरण‑दर‑चरण गाइड

क्या आपको कभी **Word को Markdown के रूप में सहेजना** पड़ा, लेकिन एम्बेडेड तस्वीरों के साथ क्या करना है, समझ नहीं आया? आप अकेले नहीं हैं। कई प्रोजेक्ट्स में markdown आउटपुट शानदार दिखता है—*जब तक* आप यह नहीं देखते कि इमेज लिंक टूटे हुए हैं क्योंकि फ़ाइलें Word पैकेज से बाहर नहीं निकलीं।  

अच्छी खबर यह है कि Aspose.Words आपको **docx से इमेज निकालने** और उन्हें बिल्कुल वहीँ रखने का साफ़ तरीका देता है, एक **callback** के माध्यम से जो आपको markdown इमेज फ़ोल्डर को नियंत्रित करने की अनुमति देता है। इस ट्यूटोरियल में हम पूरी प्रक्रिया को समझेंगे, `.docx` फ़ाइल लोड करने से लेकर PNG (या आपके पास जो भी फ़ॉर्मेट हो) की एक व्यवस्थित फ़ोल्डर और उन पर पॉइंट करने वाली markdown फ़ाइल बनाने तक।

इस गाइड के अंत तक आप सक्षम होंगे:

* एक ही लाइन कोड से किसी भी Word डॉक्यूमेंट को Markdown में बदलना।  
* हर तस्वीर को एक समर्पित `images` सब‑फ़ोल्डर में स्वचालित रूप से डंप करना।  
* फ़ाइलनाम कस्टमाइज़ करना ताकि स्रोत में दर्जनों तस्वीरें हों तो भी नाम टकराएँ नहीं।  

कोई बाहरी स्क्रिप्ट नहीं, कोई मैन्युअल कॉपी‑पेस्ट नहीं—सिर्फ शुद्ध C# और Aspose.Words।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* **Aspose.Words for .NET** (सबसे नवीन स्थिर संस्करण; लेख लिखते समय यह 24.9 है)।  
* एक .NET डेवलपमेंट एनवायरनमेंट (Visual Studio, Rider, या `dotnet` CLI)।  
* एक Word डॉक्यूमेंट (`.docx`) जिसमें कम से कम एक इमेज हो—इसे `DocWithImages.docx` कहें।  

यदि आपने पहले कभी Aspose.Words नहीं इस्तेमाल किया है, तो चिंता न करें। यह लाइब्रेरी पूरी तरह मैनेज्ड है, कोई COM इंटरऑप की जरूरत नहीं, और .NET 6+ के साथ-साथ .NET Framework 4.8 पर भी काम करती है।

## Step 1 – Set Up the Project and Install the Package

पहले, एक नया console app बनाएं (या कोड को मौजूदा प्रोजेक्ट में जोड़ें)।

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **Pro tip:** यदि आप .NET 6 को टारगेट कर रहे हैं, तो डिफ़ॉल्ट `Program.cs` पहले से ही टॉप‑लेवल स्टेटमेंट्स का उपयोग करता है, जिससे सैंपल छोटा रहता है।

## Step 2 – Create a Callback to Control Image Saving

Aspose.Words हर बाहरी रिसोर्स (इमेज, CSS, आदि) को लिखने के लिए `IResourceSavingCallback.ResourceSaving` को कॉल करता है। इस इंटरफ़ेस को इम्प्लीमेंट करके हम **markdown इमेज फ़ोल्डर** को बनाने पर पूर्ण नियंत्रण प्राप्त करते हैं।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### Why use a callback?

* **Granular control** – आप फ़ोल्डर स्ट्रक्चर और नेमिंग स्कीम तय करते हैं।  
* **Performance** – आप स्ट्रीम को एक बार लिखते हैं, लाइब्रेरी की डबल‑राइट फ़ॉलबैक से बचते हैं।  
* **Flexibility** – आप इस बिंदु पर लॉगिंग, इमेज‑ऑप्टिमाइज़ेशन, या क्लाउड स्टोरेज पर अपलोड जैसी चीज़ें जोड़ सकते हैं।

## Step 3 – Load the Word Document

अब जब callback तैयार है, हमें बस Aspose.Words को स्रोत फ़ाइल की ओर इंगित करना है।

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **What if the file isn’t found?**  
> `Document` एक `FileNotFoundException` फेंकेगा। यदि पाथ डायनामिक है तो `try/catch` में लोड करें।

## Step 4 – Wire Up the MarkdownSaveOptions

`MarkdownSaveOptions` क्लास हमें अभी बनाए हुए callback को प्लग‑इन करने की सुविधा देती है। हम वह फ़ोल्डर भी सेट करते हैं जहाँ इमेजेज़ markdown फ़ाइल के सापेक्ष रहेंगे।

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

`ImagesFolder` प्रॉपर्टी Aspose को `![Alt text](images/img_123.png)` जैसे markdown लिंक जनरेट करने के लिए बताती है। क्योंकि हमने callback के अंदर `ResourceFileName` भी सेट किया है, वास्तविक फ़ाइल ठीक उसी जगह पर रखी जाती है।

## Step 5 – Save as Markdown and Verify the Result

आखिरकार, हम markdown फ़ाइल लिखते हैं। callback ने पहले ही `images` सब‑फ़ोल्डर को भर दिया होगा।

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### Expected output

प्रोग्राम चलाने पर कुछ इस तरह का आउटपुट दिखना चाहिए:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

`Doc.md` को किसी भी markdown व्यूअर में खोलें; आपको इमेज लिंक सही तरीके से `images` फ़ोल्डर की ओर इशारा करते दिखेंगे।

---

## Frequently Asked Questions (FAQ)

### How to **extract images from docx** without converting to markdown?

आप वही `MyMarkdownResourceCallback` पुनः उपयोग कर सकते हैं, बस इसे `doc.Save("images.zip", SaveFormat.Zip)` में पास करें। callback अभी भी प्रत्येक इमेज के लिए फायर होगा, जिससे आप उन्हें अपनी इच्छानुसार रख सकेंगे।

### What if I need **different image formats**?

`args.FileName` में पहले से ही मूल एक्सटेंशन (`.png`, `.jpg`, आदि) मौजूद है। यदि सभी इमेज को एक ही फ़ॉर्मेट में बदलना है, तो `ResourceSaving` के अंदर एक कन्वर्ज़न स्टेप जोड़ें, फिर स्ट्रीम लिखें।

### Can I **customize the markdown images folder** per document?

बिल्कुल। callback अपने कंस्ट्रक्टर के माध्यम से फ़ोल्डर पाथ प्राप्त करता है, इसलिए आप बैच प्रोसेस में प्रत्येक डॉक्यूमेंट के लिए अलग फ़ोल्डर के साथ नया callback इंस्टैंस बना सकते हैं।

### Does this work with **large documents** (hundreds of images)?

हां। callback इमेज को सीधे डिस्क पर स्ट्रीम करता है, जिससे मेमोरी उपयोग कम रहता है। बस यह सुनिश्चित करें कि टार्गेट ड्राइव में पर्याप्त स्पेस हो और आप OS फ़ाइल‑हैंडल लिमिट को पार न करें।

---

## Full Working Example

नीचे पूरा, कॉपी‑एंड‑पेस्ट‑रेडी प्रोग्राम दिया गया है। `YOUR_DIRECTORY` को अपने वातावरण के अनुसार एक एब्सोल्यूट या रिलेटिव पाथ से बदलें।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

प्रोग्राम चलाएँ (`dotnet run`) और आपको एक नया `Doc.md` फ़ाइल के साथ एक `images` सब‑फ़ोल्डर मिलेगा जिसमें

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}