---
category: general
date: 2026-01-14
description: C# में कॉलबैक का उपयोग करके DOCX को मार्कडाउन में बदलना, Word से इमेज
  निकालना, और अनोखे इमेज नाम बनाना सीखें।
draft: false
keywords:
- how to use callback
- convert docx to markdown
- extract images from word
- save word as markdown
- generate unique image names
language: hi
og_description: DOCX को मार्कडाउन में बदलने, इमेज निकालने और यूनिक इमेज नाम जेनरेट
  करने के लिए C# में कॉलबैक का उपयोग कैसे करें।
og_title: C# में कॉलबैक का उपयोग कैसे करें – DOCX को मार्कडाउन में बदलें
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: C# में कॉलबैक का उपयोग कैसे करें – DOCX को मार्कडाउन में बदलें
url: /hi/net/programming-with-markdownsaveoptions/how-to-use-callback-in-c-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में कॉलबैक का उपयोग कैसे करें – DOCX को Markdown में बदलें

क्या आपने कभी सोचा है **कॉलबैक का उपयोग कैसे करें** जब आपको एक Word दस्तावेज़ को साफ़ Markdown में बदलना हो? आप अकेले नहीं हैं। अधिकांश डेवलपर्स तब अटक जाते हैं जब रूपांतरण कई इमेज फ़ाइलें समान नामों के साथ उत्पन्न करता है या जब Markdown गलत फ़ोल्डर की ओर इशारा करता है। अच्छी खबर? एक छोटा कस्टम कॉलबैक के साथ आप यह नियंत्रित कर सकते हैं कि प्रत्येक रिसोर्स कहाँ सहेजा जाए, हर तस्वीर को एक अनोखा नाम दें, और अपना Markdown व्यवस्थित रखें।

इस गाइड में हम पूरी प्रक्रिया को देखेंगे: एक `.docx` लोड करना, एक कॉलबैक कॉन्फ़िगर करना जो तय करता है **कहाँ** और **कैसे** इमेज सेव हों, और अंत में परिणाम को Markdown के रूप में लिखना। अंत तक आप **docx को markdown में बदलना**, **Word से इमेज निकालना**, और **अनोखे इमेज नाम जेनरेट करना** बिना हर बार मैन्युअल हस्तक्षेप के कर पाएँगे। कोई बाहरी स्क्रिप्ट नहीं, सिर्फ शुद्ध C# और Aspose.Words।

> **Prerequisites**  
> • .NET 6+ (या .NET Framework 4.7+) स्थापित हो  
> • Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)  
> • C# क्लासेज़ और फ़ाइल I/O की बुनियादी समझ  

---

![how to use callback diagram](https://example.com/images/callback-diagram.png "कॉलबैक का उपयोग करके इमेज एक्सट्रैक्शन दिखाने वाला आरेख")

## How to Use Callback When Saving Resources

समाधान का मुख्य भाग एक क्लास में रहता है जो `IResourceSavingCallback` को इम्प्लीमेंट करता है। Aspose.Words हर बाहरी रिसोर्स (जैसे इमेज) को डिस्क पर लिखने के लिए इस इंटरफ़ेस को कॉल करता है। `ResourceSaving` को ओवरराइड करके हमें टार्गेट पाथ और फ़ाइल नाम पर पूर्ण नियंत्रण मिल जाता है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that decides where each image extracted from a Word document will be saved.
/// </summary>
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Choose the folder where images will be stored.
        string folder = @"YOUR_DIRECTORY/Images/";

        // 2️⃣ Create a unique name – Guid guarantees no collisions.
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Combine folder and file name, then tell Aspose to use it.
        args.SavePath = Path.Combine(folder, uniqueName);
        args.Cancel = false; // Let Aspose perform the actual write.
    }
}
```

**Why this matters:**  
- **Predictability** – सभी इमेज एक ही फ़ोल्डर में सहेजी जाती हैं, जिससे Markdown रेफ़रेंसेज़ विश्वसनीय बनती हैं।  
- **Collision‑free naming** – `Guid.NewGuid()` का उपयोग करने से आप कभी भी मौजूदा इमेज को ओवरराइट नहीं करेंगे, भले ही स्रोत दस्तावेज़ में डुप्लिकेट नाम हों।  
- **Flexibility** – `folder` या नामकरण योजना को बदलें बिना रूपांतरण लॉजिक को छुएँ।

## Configure Markdown Save Options (Save Word as Markdown)

अब हम कॉलबैक को `MarkdownSaveOptions` में जोड़ते हैं। यह ऑब्जेक्ट Aspose को बताता है कि रूपांतरण कैसे किया जाए और कौन सा कॉलबैक फ़ायर किया जाए।

```csharp
// Step 4: Hook our custom callback into the markdown options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

आप यहाँ अन्य विकल्प भी बदल सकते हैं, जैसे `ExportImagesAsBase64` (इसे `false` रखें क्योंकि हम अलग‑अलग इमेज फ़ाइलें चाहते हैं) या `ExportHeadersAsHtml` यदि आपको हेडिंग फ़ॉर्मेटिंग पर अधिक नियंत्रण चाहिए। डिफ़ॉल्ट सेटिंग्स पहले से ही अधिकांश स्टेटिक‑साइट जेनरेटर्स के लिए साफ़ Markdown उत्पन्न करती हैं।

## Load the Document and Perform the Conversion (Convert DOCX to Markdown)

विकल्प तैयार होने के बाद अंतिम कदम सीधा है: `.docx` लोड करें और Aspose को इसे Markdown के रूप में सहेजने को कहें।

```csharp
// Step 5: Load the source DOCX and save it as Markdown.
Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

// The output markdown will reference the images saved by MyResourceSaver.
doc.Save(@"YOUR_DIRECTORY/output.md", mdOptions);
```

**What you’ll see:**  
- `output.md` में Markdown सिंटैक्स (`![Alt text](Images/img_…png)`) होगा जो आपके द्वारा निर्दिष्ट इमेज फ़ोल्डर की ओर इशारा करता है।  
- `input.docx` से निकाली गई हर इमेज `YOUR_DIRECTORY/Images/` के तहत एक अनोखे GUID‑आधारित नाम के साथ रखी जाएगी।  

---

## Common Variations & Edge Cases

### 1️⃣ Changing the Naming Scheme
यदि आप GUID के बजाय पढ़ने योग्य नाम (जैसे `figure_1.png`) पसंद करते हैं, तो `uniqueName` लाइन को इस तरह बदलें:

```csharp
int counter = 0;
string uniqueName = $"figure_{++counter}{Path.GetExtension(args.ResourceFileName)}";
```

सिर्फ यह याद रखें कि `counter` को एक static फ़ील्ड बनाएं या कॉलबैक कंस्ट्रक्टर के माध्यम से पास करें ताकि यह कॉल्स के बीच बना रहे।

### 2️⃣ Handling Sub‑folders
कुछ प्रोजेक्ट्स इमेज को चैप्टर के अनुसार व्यवस्थित करते हैं। आप `args.ResourceFileName` या आसपास के पैराग्राफ़ टेक्स्ट को देख कर तय कर सकते हैं कि इमेज किस सब‑फ़ोल्डर में रखनी है:

```csharp
string chapterFolder = Path.Combine(folder, $"Chapter_{args.ResourceFileName.Substring(0,1)}");
Directory.CreateDirectory(chapterFolder);
args.SavePath = Path.Combine(chapterFolder, uniqueName);
```

### 3️⃣ Skipping Certain Images
यदि आप केवल PNG इमेज निकालना चाहते हैं, तो एक गार्ड जोड़ें:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase))
{
    args.Cancel = true; // Skip non‑PNG images.
    return;
}
```

### 4️⃣ Verifying the Output
रूपांतरण के बाद आप प्रोग्रामेटिकली यह जांच सकते हैं कि Markdown में रेफ़र की गई हर इमेज वास्तव में मौजूद है या नहीं:

```csharp
string markdown = File.ReadAllText(@"YOUR_DIRECTORY/output.md");
var matches = System.Text.RegularExpressions.Regex.Matches(markdown, @"!\[.*?\]\((.*?)\)");
foreach (System.Text.RegularExpressions.Match m in matches)
{
    string imgPath = Path.Combine(@"YOUR_DIRECTORY", m.Groups[1].Value);
    Console.WriteLine(File.Exists(imgPath) ? "OK" : $"Missing: {imgPath}");
}
```

---

## Pro Tips for a Smooth Experience

- **Images फ़ोल्डर को पहले से बना लें।** Aspose इसे ऑटोमैटिकली बना देगा, लेकिन प्री‑क्रिएशन मल्टी‑थ्रेडेड परिदृश्यों में रेस कंडीशन से बचाता है।  
- **`Path.GetInvalidFileNameChars()`** का उपयोग करें यदि आपको मूल दस्तावेज़ से आने वाले नामों को साफ़ करना पड़े।  
- **`Document` को डिस्पोज़ करें** जब काम पूरा हो जाए (इसे `using` ब्लॉक में रखें) ताकि नेटिव रिसोर्सेज़ तुरंत मुक्त हो सकें।  
- **SVG वाली फ़ाइलों के साथ टेस्ट करें।** Aspose डिफ़ॉल्ट रूप से उन्हें PNG में बदल देता है; यदि आपको मूल फ़ॉर्मेट चाहिए, तो कॉलबैक को उसी अनुसार एडजस्ट करें।

---

## Expected Result

एक नमूना `input.docx` जिसमें दो तस्वीरें हैं, पर स्क्रिप्ट चलाने पर मिलेगा:

**`output.md` (excerpt)**
```markdown
# Sample Document

Here is the first image:

![Image 1](Images/img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png)

And here is the second one:

![Image 2](Images/img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg)
```

**Folder structure**
```
YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ Images/
   ├─ img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png
   └─ img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg
```

सभी इमेज रेफ़रेंसेज़ सही ढंग से हल हो जाती हैं, और आपने सफलतापूर्वक **word को markdown में सहेजा** जबकि **Word से इमेज निकाली** और **अनोखे इमेज नाम जेनरेट किए**।

---

## Conclusion

हमने **कॉलबैक का उपयोग कैसे करें** Aspose.Words में दिखाया, जिससे DOCX को Markdown में बदला जा सके, हर एम्बेडेड तस्वीर निकाली जा सके, और प्रत्येक फ़ाइल को एक अनोखा, टकराव‑रहित नाम दिया जा सके। यह तरीका हल्का, पूरी तरह कस्टमाइज़ेबल, और किसी भी .NET संस्करण के साथ काम करता है जो Aspose.Words को सपोर्ट करता है।

अगला कदम? इस प्रक्रिया को Hugo या Jekyll जैसे स्टेटिक‑साइट जेनरेटर के साथ जोड़ें, या पूरे फ़ोल्डर के दस्तावेज़ों के लिए बैच रूपांतरण ऑटोमेट करें। आप टेबल को Markdown में एक्सपोर्ट करने या कॉलबैक को इस तरह बदलने के साथ प्रयोग कर सकते हैं कि इमेज को Base64 में एम्बेड किया जाए जब आकार समस्या न हो।

कोई नया प्रयोग है जिसमें आप रुचि रखते हैं? कमेंट करें, और हम साथ में इसे एक्सप्लोर करेंगे। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}