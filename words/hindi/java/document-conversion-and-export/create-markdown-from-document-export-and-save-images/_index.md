---
category: general
date: 2026-02-18
description: दस्तावेज़ से मार्कडाउन बनाएं, आसान चरणों के साथ दस्तावेज़ को मार्कडाउन
  में निर्यात करें और छवियों को सबफ़ोल्डर में सहेजें। C# में दस्तावेज़ को मार्कडाउन
  के रूप में सहेजना सीखें।
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: hi
og_description: C# में दस्तावेज़ से मार्कडाउन बनाएं और सीखें कि कैसे दस्तावेज़ को
  मार्कडाउन में निर्यात करें जबकि छवियों को एक उपफ़ोल्डर में सहेजा जाए। चरण‑दर‑चरण
  मार्गदर्शिका का पालन करें।
og_title: दस्तावेज़ से मार्कडाउन बनाएं – छवियों को निर्यात और सहेजें
tags:
- C#
- Aspose.Words
- Markdown export
title: दस्तावेज़ से मार्कडाउन बनाएं – छवियों को निर्यात और सहेजें
url: /hi/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ से मार्कडाउन बनाएं – निर्यात और छवियों को सहेजें

क्या आपको कभी **दस्तावेज़ से मार्कडाउन बनाना** पड़ा है लेकिन एम्बेडेड तस्वीरों को व्यवस्थित रखने का तरीका नहीं पता था? आप अकेले नहीं हैं। कई प्रोजेक्ट्स में हम रिपोर्ट, मैनुअल या ब्लॉग ड्राफ्ट प्रोग्रामेटिकली जनरेट करते हैं, और आख़िरी चीज़ जो हम चाहते हैं वह आउटपुट फ़ोल्डर में बिखरी हुई छवि फ़ाइलों का गड़बड़ होना है।

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य समाधान के माध्यम से चलेंगे जो **दस्तावेज़ को मार्कडाउन में निर्यात करता है**, हर छवि को एक समर्पित *md‑resources* सब‑फ़ोल्डर में रखता है, और अंत में **Aspose.Words for .NET API** का उपयोग करके दस्तावेज़ को मार्कडाउन के रूप में सहेजता है। अंत तक आपके पास एक एकल मेथड होगा जिसे आप किसी भी C# कोडबेस में डाल सकते हैं, साथ ही किनारे के मामलों को संभालने के लिए कुछ टिप्स भी मिलेंगे।

> **त्वरित झलक:**  
> • `MarkdownSaveOptions` सेट अप करें  
> • एक `IResourceSavingCallback` प्रदान करें जो छवियों को सबफ़ोल्डर में रीडायरेक्ट करे  
> • कॉन्फ़िगर किए गए विकल्पों के साथ `Document.Save` को कॉल करें  

यदि आप यह जानने के लिए उत्सुक हैं कि हम पोस्ट‑प्रोसेसिंग के बजाय कॉलबैक क्यों चुनते हैं, तो पढ़ते रहें – कारण चरण‑दर‑चरण समझाए गए हैं।

---

## पूर्वापेक्षाएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)  
- Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)  
- एक स्रोत `Document` ऑब्जेक्ट (जैसे .docx, .pdf, .rtf, आदि)  

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है; कॉलबैक API Aspose.Words में ही निर्मित है।

---

## चरण 1: दस्तावेज़ से मार्कडाउन बनाएं – सेव विकल्प कॉन्फ़िगर करें

सबसे पहले हम `MarkdownSaveOptions` का एक इंस्टेंस बनाते हैं। यह ऑब्जेक्ट Aspose.Words को बताता है कि रूपांतरण कैसे व्यवहार करे, जैसे कौन सा Markdown फ़्लेवर उपयोग करना है, क्या छवियों को Base64 के रूप में एम्बेड करना है, और उत्पन्न फ़ाइलें कहाँ रखनी हैं।

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **यह क्यों महत्वपूर्ण है:**  
> `MarkdownSaveOptions` को स्पष्ट रूप से न बनाकर, लाइब्रेरी डिफ़ॉल्ट सेटिंग्स पर वापस चली जाती है जो छवियों को सीधे Markdown फ़ाइल में Base64 स्ट्रिंग्स के रूप में एम्बेड कर देती है। इससे फ़ाइल बहुत बड़ी हो जाती है और साफ़ *images* फ़ोल्डर रखने का उद्देश्य विफल हो जाता है।

---

## चरण 2: दस्तावेज़ को मार्कडाउन में निर्यात करें और रिसोर्स हैंडलिंग परिभाषित करें

अब हम सेव करने वाले को बताते हैं कि **हर छवि** कहाँ रखनी है। `IResourceSavingCallback` इंटरफ़ेस हमें एक हुक देता है जो निर्यात के दौरान खोजे गए प्रत्येक रिसोर्स (छवि, SVG, आदि) के लिए फायर होता है। कॉलबैक के भीतर हम:

1. लक्ष्य फ़ोल्डर (`md-resources/`) मौजूद है यह सुनिश्चित करें।  
2. `OutputFileName` को फ़ोल्डर पाथ प्लस मूल रिसोर्स नाम पर सेट करें।  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **सामान्य प्रश्न:** *अगर मैं छवियों को एम्बेड करना चाहूँ बजाय उन्हें सहेजे?*  
> बस कॉलबैक को स्किप करें या `args.OutputFileName = null;` सेट करें; सेव करने वाला स्वचालित रूप से छवि को Base64 स्ट्रिंग के रूप में एम्बेड कर देगा।

> **किनारा मामला:** कुछ पुराने दस्तावेज़ों में डुप्लिकेट छवि नाम होते हैं। ऊपर दिया गया कॉलबैक पहले की फ़ाइल को ओवरराइट कर देगा। इसे रोकने के लिए आप एक GUID जोड़ सकते हैं:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## चरण 3: दस्तावेज़ को मार्कडाउन के रूप में सहेजें और सहेजी गई छवियों की जाँच करें

विकल्प पूरी तरह कॉन्फ़िगर हो जाने के बाद, अंतिम कॉल एक‑लाइनर है जो Markdown फ़ाइल और संबंधित छवियों को डिस्क पर लिखता है।

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

यदि सब कुछ सही रहा तो आपको दिखेगा:

- `MyReport.md` – आपके स्रोत दस्तावेज़ का Markdown प्रतिनिधित्व।  
- `md-resources/` – `.md` फ़ाइल के बगल में एक फ़ोल्डर जिसमें प्रत्येक निकाली गई छवि होगी (जैसे `image001.png`, `image002.jpg`)।  

**उदाहरण Markdown स्निपेट** (Aspose.Words द्वारा ऑटो‑जनरेटेड):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **प्रो टिप:** उत्पन्न `.md` फ़ाइल को VS Code या किसी भी Markdown प्रीव्यूअर में खोलें; छवियों को तुरंत रेंडर होना चाहिए क्योंकि रिलेटिव पाथ फ़ोल्डर संरचना से मेल खाता है।

---

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक स्व-निहित कंसोल प्रोग्राम है जिसे आप नए .NET प्रोजेक्ट में पेस्ट करके चला सकते हैं। यह एक सरल Word दस्तावेज़ बनाता है, एक छवि जोड़ता है, और फिर **दस्तावेज़ से मार्कडाउन बनाते** हुए छवि को एक सबफ़ोल्डर में सहेजता है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**रन करने के बाद आपको जो दिखना चाहिए**:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

`ExportedDoc.md` खोलें – छवि रेफ़रेंस `md-resources/sample-image.png` की ओर इशारा करेगा, और चित्र किसी भी Markdown व्यूअर में सही ढंग से प्रदर्शित होगा।

---

## अक्सर पूछे जाने वाले विविधताएँ

| परिदृश्य | कोड को कैसे अनुकूलित करें |
|----------|---------------------------|
| **छवि निर्यात को छोड़ें** (Base64 के रूप में एम्बेड) | `ResourceSavingCallback` को पूरी तरह हटाएँ, या कॉलबैक के भीतर `args.OutputFileName = null;` सेट करें। |
| **छवि फ़ॉर्मेट बदलें** (जैसे सभी PNG) | कॉलबैक के भीतर `args.ResourceFileName` को संशोधित करें और वैकल्पिक रूप से स्ट्रीम को लिखने से पहले बदलें। |
| **कस्टम फ़ोल्डर नाम** | `"md-resources/"` को अपनी पसंद के किसी भी रिलेटिव या एब्सोल्यूट पाथ से बदलें। |
| **बैच में कई दस्तावेज़** | `Document` ऑब्जेक्ट्स के संग्रह पर लूप चलाएँ, वही `MarkdownSaveOptions` इंस्टेंस पुन: उपयोग करें (सिर्फ यह सुनिश्चित करें कि फ़ोल्डर साफ़ हो या प्रत्येक रन के लिए यूनिक नाम हो)। |

---

## निष्कर्ष

हमने अभी आपको **दस्तावेज़ से मार्कडाउन कैसे बनाएं**, **दस्तावेज़ को मार्कडाउन में निर्यात करें**, और **छवियों को सबफ़ोल्डर में सहेजें** एक साफ़, कॉलबैक‑ड्रिवेन दृष्टिकोण से दिखाया। मुख्य बिंदु हैं:

- `MarkdownSaveOptions` का उपयोग करके निर्यात पर सूक्ष्म नियंत्रण प्राप्त करें।  
- `IResourceSavingCallback` को लागू करके छवियों को समर्पित फ़ोल्डर में निर्देशित करें, जिससे आपका Markdown साफ़ रहे।  
- वही पैटर्न अन्य रिसोर्स प्रकारों (SVG, ऑडियो) के लिए भी काम करता है – बस `args.ResourceType` की जाँच करें।  

अगला कदम, आप **कस्टम हेडिंग स्टाइल्स** के साथ दस्तावेज़ को मार्कडाउन में सहेजने की खोज कर सकते हैं, या इस रूटीन को एक ASP.NET Web API में इंटीग्रेट कर सकते हैं जो `.md` फ़ाइल और उसकी रिसोर्सेज़ को ज़िप के रूप में रिटर्न करता है। चाहे जो भी हो, बिल्डिंग ब्लॉक्स अब आपके टूलबॉक्स में हैं।

कोई प्रश्न हैं, या कोई ऐसा किनारा मामला मिला जो हमने नहीं कवर किया? नीचे टिप्पणी छोड़ें, और कोडिंग का आनंद लें!

---

![दस्तावेज़ से मार्कडाउन बनाते हुए उदाहरण](placeholder.png "दस्तावेज़ से मार्कडाउन बनाते हुए उदाहरण")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}