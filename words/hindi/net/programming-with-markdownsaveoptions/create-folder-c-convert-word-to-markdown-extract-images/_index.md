---
category: general
date: 2026-02-26
description: फ़ोल्डर बनाएं C# ट्यूटोरियल जो दिखाता है कि Word को markdown में कैसे
  बदलें, docx से चित्र निकालें, और स्ट्रीम को फ़ाइल में कैसे कॉपी करें—सभी एक ही चरण
  में।
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: hi
og_description: Create folder C# ट्यूटोरियल आपको वर्ड को मार्कडाउन में बदलने, docx
  से इमेज निकालने, और स्ट्रीम को फ़ाइल में कॉपी करने की प्रक्रिया स्पष्ट कोड उदाहरणों
  के साथ दिखाता है।
og_title: फ़ोल्डर बनाएं C# – वर्ड को मार्कडाउन में बदलें और इमेज निकालें
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: फ़ोल्डर बनाएं C# – वर्ड को मार्कडाउन में बदलें और इमेज निकालें
url: /hi/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ोल्डर बनाएं C# – Word को Markdown में बदलें और चित्र निकालें

क्या आपको कभी **create folder C#** करने की ज़रूरत पड़ी है जबकि साथ ही Word दस्तावेज़ को markdown में बदलना और हर चित्र को निकालना? आप अकेले नहीं हैं जो इस पर सिर खुजला रहे हैं। कई ऑटोमेशन पाइपलाइन में आपको फ़ाइल सिस्टम के काम, फ़ॉर्मेट रूपांतरण, और बाइनरी डेटा हैंडलिंग—सब एक साथ संभालना पड़ता है।  

इस गाइड में हम एक पूर्ण, चलाने योग्य समाधान के माध्यम से जाएंगे जो बिल्कुल यही करता है: यह एक लक्ष्य डायरेक्टरी बनाता है, एक `.docx` को markdown में बदलता है, प्रत्येक एम्बेडेड चित्र को निकालता है, और **copy stream to file** लॉजिक का उपयोग करता है ताकि चित्र वहीं रखे जाएँ जहाँ आप चाहते हैं। कोई बाहरी स्क्रिप्ट नहीं, कोई मैनुअल कदम नहीं। सिर्फ शुद्ध C# और Aspose.Words लाइब्रेरी।

> **आपको क्या मिलेगा**  
> * एक स्पष्ट फ़ोल्डर संरचना जो markdown और एसेट्स के लिए तैयार है  
> * एक markdown फ़ाइल जो निकाले गए चित्रों को सही ढंग से संदर्भित करती है  
> * पूरा स्रोत कोड जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं  

Before we dive, make sure you have:

* .NET 6.0 (या बाद का) SDK स्थापित हो – कोड आधुनिक भाषा सुविधाओं का उपयोग करता है।  
* **Aspose.Words for .NET** का लाइसेंस (फ़्री ट्रायल परीक्षण के लिए काम करता है)।  
* Visual Studio 2022 या आपका पसंदीदा एडिटर।  

यदि आप सोच रहे हैं *क्यों* आप चित्रों को एम्बेड करने के बजाय निकालना चाहेंगे, तो स्थैतिक साइट जेनरेटरों के बारे में सोचें: उन्हें रिलेटिव इमेज पाथ वाले markdown पसंद हैं, और एसेट्स को एक समर्पित फ़ोल्डर में रखना चीज़ों को व्यवस्थित और कैश‑फ्रेंडली बनाता है।

---

## फ़ोल्डर बनाएं C# और आउटपुट संरचना तैयार करें

सबसे पहले हमें डिस्क पर एक ऐसी जगह चाहिए जहाँ सब कुछ रहेगा। यह चरण वह है जहाँ **create folder C#** क्रिया होती है, और यह `Directory.CreateDirectory` की बदौलत आश्चर्यजनक रूप से सरल है। यह मेथड इडेम्पोटेंट है—यदि फ़ोल्डर पहले से मौजूद है तो यह त्रुटि नहीं फेंकेगा, जिससे अतिरिक्त जांचों की ज़रूरत नहीं पड़ेगी।

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**यह क्यों महत्वपूर्ण है:**  
फ़ोल्डर पहले से बनाकर यह सुनिश्चित किया जाता है कि बाद के सेविंग चरण `DirectoryNotFoundException` के साथ विफल न हों। यह आपको एक पूर्वानुमानित लेआउट भी देता है: `.md` फ़ाइल के लिए `output/markdown` और निकाले गए प्रत्येक चित्र के लिए `output/MyImages`।

> **प्रो टिप:** यदि आप प्रोग्राम को बार‑बार चलाते हैं, तो आप पहले इमेज फ़ोल्डर को साफ़ करना चाह सकते हैं (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) ताकि पुराने फ़ाइलों से बचा जा सके।

## Aspose.Words का उपयोग करके Word को Markdown में बदलें

अब जब डायरेक्टरी ट्री तैयार है, चलिए Word दस्तावेज़ को markdown में बदलते हैं। Aspose.Words भारी काम करता है—OpenXML या थर्ड‑पार्टी कन्वर्टर्स के साथ झंझट नहीं।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**आंतरिक रूप से क्या हो रहा है?**  
`MarkdownSaveOptions` Aspose को markdown सिंटैक्स उत्पन्न करने के लिए बताता है। डिफ़ॉल्ट रूप से, लाइब्रेरी चित्रों को markdown फ़ाइल के समान फ़ोल्डर में ऑटो‑जेनरेटेड नामों के साथ रख देती है। `ResourceSavingCallback` प्रदान करके, हम उस व्यवहार को इंटरसेप्ट करते हैं और **copy stream to file** को अपनी पसंद के स्थान पर रखते हैं।

## DOCX से चित्र निकालें और सहेजें

कॉलबैक क्लास `IResourceSavingCallback` को इम्प्लीमेंट करता है। अंदर हम एक `ResourceSavingArgs` ऑब्जेक्ट प्राप्त करते हैं जिसमें मूल इमेज स्ट्रीम और सुझाया गया फ़ाइल नाम होता है। फिर हम उस स्ट्रीम को डिस्क पर लिखते हैं, यदि चाहें तो फ़ाइल का नाम बदलते हैं, और Aspose को बताते हैं कि हमने इसे संभाल लिया है।

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### markdown कैसा दिखेगा

कन्वर्ज़न के बाद, उत्पन्न `output.md` में इस प्रकार की पंक्तियाँ होंगी:

```markdown
![Image 1](MyImages/img_picture1.png)
```

क्योंकि हमने `args.ResourceFileName` को रिलेटिव पाथ में बदल दिया, markdown सीधे उस फ़ोल्डर की ओर इशारा करता है जिसे हमने बनाया था। यह वही है जो स्थैतिक साइट जेनरेटर अपेक्षा करते हैं।

**एज केस हैंडलिंग:**  
*यदि दस्तावेज़ में डुप्लिकेट इमेज नाम हैं*, तो `img_` प्रीफ़िक्स मूल नाम के साथ आमतौर पर टकराव से बचाता है, लेकिन आप पूर्ण यूनिकनेस के लिए GUID (`Guid.NewGuid()`) भी जोड़ सकते हैं।

## Copy stream to file – इमेज डेटा को संभालना

आप सोच सकते हैं कि हम सिर्फ `File.WriteAllBytes` क्यों नहीं कॉल करते। उत्तर **stream flexibility** में है। `args.Stream` मेमोरी स्ट्रीम, नेटवर्क स्ट्रीम, या कोई अन्य इम्प्लीमेंटेशन हो सकता है। `CopyTo` का उपयोग करके, हम निरपेक्ष रहते हैं और .NET को बफ़र साइजिंग को कुशलता से संभालने देते हैं।

यदि आपको कभी किसी सामान्य स्ट्रीम को कहीं और कॉपी करने की ज़रूरत पड़े, तो यहाँ एक कॉम्पैक्ट यूटिलिटी मेथड है:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

यदि आप सिंगल‑रेस्पॉन्सिबिलिटी अप्रोच पसंद करते हैं, तो आप `ImageSavingCallback` में इनलाइन कॉपी को `CopyStreamToFile` कॉल से बदल सकते हैं।

## पूर्ण चलाने योग्य उदाहरण

सभी हिस्सों को मिलाकर आपको एक स्व-निहित प्रोग्राम मिलता है जिसे आप कमांड लाइन से चला सकते हैं:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**अपेक्षित परिणाम**

* `output/markdown/output.md` – एक markdown फ़ाइल जिसकी इमेज रेफ़रेंसेज़ `![Alt text](MyImages/img_picture1.png)` जैसी दिखती हैं।  
* `output/MyImages/` – प्रत्येक चित्र के लिए एक PNG/JPEG फ़ाइल जो मूल रूप से `input.docx` के अंदर थी।  

markdown को किसी भी व्यूअर (VS Code, GitHub, या स्थैतिक‑साइट जेनरेटर) में खोलें और आप चित्रों को ठीक उसी जगह रेंडर होते देखेंगे जहाँ वे मूल Word फ़ाइल में थे।

## अक्सर पूछे जाने वाले प्रश्न & ट्रबलशूटिंग

| प्रश्न | उत्तर |
|----------|--------|
| **यदि लक्ष्य फ़ोल्डर में पहले से फ़ाइलें हैं तो क्या होगा?** | `Directory.CreateDirectory` ओवरराइट नहीं करेगा। यदि आपको साफ़ रन चाहिए, तो डिलीट करें |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}