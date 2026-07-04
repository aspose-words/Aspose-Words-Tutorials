---
category: general
date: 2026-06-20
description: कस्टम इमेज फ़ोल्डर आपको मार्कडाउन को आसानी से इमेज के साथ निर्यात करने
  देता है। जानिए कैसे इमेज को विशिष्ट डायरेक्टरी में सहेँ और .NET में मार्कडाउन इमेज
  को सहेँ।
draft: false
keywords:
- custom image folder
- export markdown with images
- save images specific directory
- save markdown images
language: hi
og_description: कस्टम इमेज फ़ोल्डर मार्कडाउन को इमेजों के साथ निर्यात करना आसान बनाता
  है। इमेजों को विशिष्ट डायरेक्टरी में सहेजने और मार्कडाउन इमेजों को सहेजने के लिए
  इस चरण‑दर‑चरण गाइड का पालन करें।
og_title: कस्टम इमेज फ़ोल्डर – इमेज के साथ मार्कडाउन निर्यात
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  headline: custom image folder for export markdown with images – Complete Guide
  type: TechArticle
- description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  name: custom image folder for export markdown with images – Complete Guide
  steps:
  - name: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
    text: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
  - name: Eliminates a second file‑system scan, which can be costly for large docs.
    text: Eliminates a second file‑system scan, which can be costly for large docs.
  - name: Gives you the flexibility to rename or compress images on the fly.
    text: Gives you the flexibility to rename or compress images on the fly.
  type: HowTo
tags:
- Aspose.Words
- Markdown
- .NET
title: छवियों के साथ मार्कडाउन निर्यात के लिए कस्टम इमेज फ़ोल्डर – पूर्ण गाइड
url: /hi/net/programming-with-markdownsaveoptions/custom-image-folder-for-export-markdown-with-images-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# कस्टम इमेज फ़ोल्डर – .NET में इमेज के साथ मार्कडाउन निर्यात करें

क्या आपको कभी **कस्टम इमेज फ़ोल्डर** की जरूरत पड़ी है जब आप इमेज के साथ मार्कडाउन निर्यात करते हैं? आप अकेले नहीं हैं जो इस समस्या का सामना कर रहे हैं। चाहे आप डॉक्यूमेंटेशन, ब्लॉग पोस्ट, या API गाइड बना रहे हों, इमेज को एक समर्पित डायरेक्टरी में व्यवस्थित रखना बाद में गंदे फ़ाइल ट्री से बचाता है।

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य समाधान के माध्यम से चलेंगे जो आपको **कैसे इमेज को विशिष्ट डायरेक्टरी में सेव करें** दिखाता है जबकि आप एक मार्कडाउन फ़ाइल बना रहे हैं। आप देखेंगे कि कॉलबैक का उपयोग सबसे साफ़ तरीका क्यों है, और गाइड के अंत में आपको एक पूरा कोड नमूना मिलेगा जिसे आप किसी भी .NET प्रोजेक्ट में जोड़ सकते हैं।

## आप क्या सीखेंगे

- Aspose.Words (या कोई समान लाइब्रेरी) को इमेज सेव को रीडायरेक्ट करने के लिए कॉन्फ़िगर करें।
- एक कॉलबैक लागू करें जो प्रत्येक इमेज को **कस्टम इमेज फ़ोल्डर** में लिखे।
- `MarkdownSaveOptions` का उपयोग करके सब कुछ जोड़ें और **मार्कडाउन इमेज को सही ढंग से सेव** करें।
- डुप्लिकेट नाम या बड़े फ़ाइलों जैसी एज केसों को संभालने के लिए टिप्स।

### पूर्वापेक्षाएँ

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6+ (or .NET Framework 4.7+) | कोड `FileStream` और `Guid` का उपयोग करता है। |
| Aspose.Words for .NET (or a comparable markdown exporter) | `MarkdownSaveOptions` और कॉलबैक इंटरफ़ेस प्रदान करता है। |
| Basic C# knowledge | आपको क्लासेस और स्ट्रीम्स को समझना होगा। |
| An existing `Document` object (`doc`) | ट्यूटोरियल मानता है कि आपके पास पहले से एक पॉप्युलेटेड डॉक्यूमेंट है। |

इनके अलावा कोई बाहरी टूल्स आवश्यक नहीं हैं—सब कुछ स्थानीय रूप से चलता है।

## चरण 1: एक कॉलबैक परिभाषित करें जो प्रत्येक इमेज को कस्टम इमेज फ़ोल्डर में संग्रहीत करता है

समाधान का मुख्य भाग एक क्लास है जो `IResourceSavingCallback` को इम्प्लीमेंट करती है। `ResourceSaving` के अंदर हम एक यूनिक फ़ाइल नाम जेनरेट करते हैं, चुनी हुई फ़ोल्डर के अंदर पूरा पाथ बनाते हैं, और फिर लाइब्रेरी को इमेज वहाँ लिखने के लिए निर्देशित करते हैं।

```csharp
// Step 1: Define a callback that stores each image in a custom folder
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique file name for the image
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Build the full path inside the desired resources directory
        var fullPath = Path.Combine("YOUR_DIRECTORY", fileName);

        // Redirect the saving stream to the new location
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;   // close after save

        // Update the markdown reference to point to the new file name
        args.ResourceFileName = fileName;
    }
}
```

**यह क्यों काम करता है:**  
- `Guid.NewGuid()` एक यूनिक नाम सुनिश्चित करता है, जिससे स्रोत डॉक्यूमेंट में समान मूल फ़ाइलनाम वाली कई इमेज होने पर टकराव नहीं होता।  
- `args.Stream` को बदलकर हम एक्सपोर्टर को ठीक वही जगह बताते हैं जहाँ बाइनरी डेटा लिखना है।  
- `args.ResourceFileName` को अपडेट करने से मार्कडाउन रेफ़रेंस (`![](img_…​)`) आपके **कस्टम इमेज फ़ोल्डर** में मौजूद फ़ाइल की ओर इशारा करता है।

> **प्रो टिप:** यदि आप चाहते हैं कि फ़ोल्डर आपके मार्कडाउन फ़ाइल के बगल में स्वतः बन जाए, तो `"YOUR_DIRECTORY"` को `Path.Combine(Environment.CurrentDirectory, "Images")` से बना पाथ से बदलें।

## चरण 2: कॉलबैक को मार्कडाउन सेव ऑप्शन्स में जोड़ें

अब हम एक `MarkdownSaveOptions` इंस्टेंस बनाते हैं और अपने कॉलबैक को असाइन करते हैं। यह एक्सपोर्टर को हर एम्बेडेड रिसोर्स पर `ImageSavingCallback` को कॉल करने के लिए बताता है।

```csharp
// Step 2: Configure Markdown save options to use the callback
var markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback()
};
```

**आंतरिक रूप से क्या हो रहा है?**  
`doc.Save` चलने पर, Aspose.Words डॉक्यूमेंट के नोड ट्री को ट्रैवर्स करता है। हर बार जब यह किसी इमेज से मिलता है, तो यह `ResourceSaving` को फायर करता है। हमारा कॉलबैक उस इवेंट को इंटरसेप्ट करता है, इमेज स्ट्रीम को रीडायरेक्ट करता है, और मार्कडाउन लिंक को अपडेट करता है। परिणामस्वरूप, सभी इमेज आपके द्वारा निर्दिष्ट फ़ोल्डर में सेव हो जाती हैं, और मार्कडाउन फ़ाइल उन्हें सही ढंग से रेफ़र करती है।

## चरण 3: डॉक्यूमेंट को मार्कडाउन के रूप में सेव करें – इमेजेज कॉलबैक के माध्यम से सेव होती हैं

अंत में, हम `Save` को विकल्प ऑब्जेक्ट के साथ कॉल करते हैं। लाइब्रेरी भारी काम करती है; हमारा कॉलबैक फ़ाइल प्लेसमेंट करता है।

```csharp
// Step 3: Save the document as Markdown; images are saved via the callback
doc.Save("YOUR_DIRECTORY/DocWithImages.md", markdownOptions);
```

यदि `"YOUR_DIRECTORY"` `C:\Docs\MyProject` है, तो आप देखेंगे:

```
C:\Docs\MyProject\DocWithImages.md
C:\Docs\MyProject\img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png
C:\Docs\MyProject\img_7e8f9a0b‑c1d2‑3e4f‑5g6h‑7i8j9k0l1m2n.jpg
```

मार्कडाउन फ़ाइल में इस तरह की लाइन्स होंगी:

```markdown
![Image](img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png)
```

यही वह है जो आपको एक पूर्वानुमेय स्थान में **मार्कडाउन इमेजेज को सेव** करने के लिए चाहिए।

## पूर्ण कार्यशील उदाहरण

नीचे एक स्व-निहित कंसोल ऐप है जिसे आप Visual Studio में कॉपी‑पेस्ट कर सकते हैं। यह एक इमेज के साथ एक साधारण डॉक्यूमेंट बनाता है, फिर कस्टम फ़ोल्डर दृष्टिकोण का उपयोग करके इसे एक्सपोर्ट करता है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, markdown with images!");
        builder.InsertImage("sample.jpg"); // Ensure sample.jpg exists next to the exe

        // 2️⃣ Define the callback (same as earlier)
        var options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback()
        };

        // 3️⃣ Choose output folder (feel free to change)
        string outputDir = Path.Combine(Environment.CurrentDirectory, "Exported");
        Directory.CreateDirectory(outputDir); // creates if missing

        // 4️⃣ Save markdown and images
        string mdPath = Path.Combine(outputDir, "Document.md");
        doc.Save(mdPath, options);

        Console.WriteLine($"Markdown saved to: {mdPath}");
        Console.WriteLine("Images stored in the same folder.");
    }
}

// Callback class – identical to the earlier snippet
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        var fullPath = Path.Combine("Exported", fileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;
        args.ResourceFileName = fileName;
    }
}
```

**अपेक्षित आउटपुट**

प्रोग्राम चलाने पर कुछ इस तरह का आउटपुट मिलेगा:

```
Markdown saved to: C:\MyApp\Exported\Document.md
Images stored in the same folder.
```

`Document.md` खोलें और आप देखेंगे कि मार्कडाउन इमेज रेफ़रेंस `img_…​` की ओर इशारा कर रहा है। इमेज फ़ाइल मार्कडाउन फ़ाइल के बगल में ही रहती है, बिल्कुल जैसा कि **कस्टम इमेज फ़ोल्डर** डिज़ाइन बताता है।

## सामान्य एज केसों को संभालना

| Situation | Solution |
|-----------|----------|
| **Duplicate filenames** | `Guid` का उपयोग पहले से ही डुप्लिकेट को रोकता है; यदि आप पढ़ने योग्य नाम चाहते हैं, तो एक काउंटर जोड़ें (`img_001.png`, `img_002.png`)। |
| **Large image sets** | जैसा दिखाया गया है, सीधे डिस्क पर स्ट्रीम करें; पूरी इमेज को मेमोरी में लोड करने से बचें। |
| **Different output directories per run** | `ImageSavingCallback` को कंस्ट्रक्टर आर्ग्यूमेंट के रूप में टार्गेट फ़ोल्डर पास करें बजाय हार्ड‑कोडिंग `"Exported"` के। |
| **Missing write permissions** | सुनिश्चित करें कि एप्लिकेशन पर्याप्त अधिकारों के साथ चल रहा है या `%TEMP%` जैसी यूज़र‑राइटेबल फ़ोल्डर चुनें। |
| **Non‑image resources (e.g., CSS)** | कॉलबैक किसी भी रिसोर्स के लिए फायर होता है; आप `args.ResourceType` को जांच सकते हैं और केवल इमेज को ही हैंडल करें। |

## पोस्ट‑प्रोसेसिंग के बजाय कॉलबैक क्यों उपयोग करें?

आप सोच सकते हैं, “पहले मार्कडाउन जेनरेट करें, फिर इमेजेज को बाद में मूव करें?” कॉलबैक दृष्टिकोण:

1. **एटॉमिकिटी** सुनिश्चित करता है – इमेज और मार्कडाउन साथ में लिखे जाते हैं, जिससे टूटे लिंक नहीं होते।  
2. दूसरी फ़ाइल‑सिस्टम स्कैन को हटाता है, जो बड़े डॉक्यूमेंट्स के लिए महंगा हो सकता है।  
3. आपको इमेजेज को ऑन‑द‑फ़्लाई रीनेम या कम्प्रेस करने की लचीलापन देता है।

संक्षेप में, यह **इमेजेज के साथ मार्कडाउन एक्सपोर्ट करने का सबसे मजबूत तरीका** है, जबकि सब कुछ **कस्टम इमेज फ़ोल्डर** में रखा जाता है।

## निष्कर्ष

हमने वह सब कवर किया जो आपको **इमेज को विशिष्ट डायरेक्टरी में सेव** करने और **मार्कडाउन इमेजेज को सेव** करने के लिए **कस्टम इमेज फ़ोल्डर** रणनीति के साथ चाहिए। `IResourceSavingCallback` को इम्प्लीमेंट करके, `MarkdownSaveOptions` को कॉन्फ़िगर करके, और `doc.Save` को कॉल करके, आप एक साफ़ फ़ोल्डर लेआउट और भरोसेमंद मार्कडाउन रेफ़रेंसेज़ प्राप्त करते हैं—सिर्फ कुछ दर्जन लाइनों के कोड में।

अगले चरण में, आप खोज सकते हैं:

- कॉलबैक के अंदर इमेज कम्प्रेशन जोड़ना।  
- एक `README.md` जनरेट करना जो स्वचालित रूप से फ़ोल्डर से लिंक करे।  
- कॉलबैक को विस्तारित करके CSS या स्क्रिप्ट्स जैसे अन्य रिसोर्स टाइप्स को हैंडल करना।

इसे अपने अगले डॉक्यूमेंटेशन पाइपलाइन में आज़माएँ—आपका भविष्य का आप साफ़ फ़ोल्डर संरचना के लिए आपका धन्यवाद करेगा।

कोडिंग का आनंद लें!

## अगले में आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं ताकि आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर कर सकें।

- [वर्ड इमेजेज सेव करें – Aspose के साथ वर्ड को मार्कडाउन में कनवर्ट करें](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [DOCX को मार्कडाउन में कनवर्ट करते समय इमेजेज को कैसे रीनेम करें](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [docx को मार्कडाउन के रूप में सेव करें – इमेज एक्सट्रैक्शन के साथ पूर्ण C# गाइड](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}