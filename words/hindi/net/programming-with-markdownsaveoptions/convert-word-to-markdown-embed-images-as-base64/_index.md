---
category: general
date: 2026-01-03
description: Word को Markdown में बदलें और एक ही बार में छवियों को base64 के रूप में
  एम्बेड करें। जानें कि Word को Markdown के रूप में कैसे सहेजें, Word से Markdown
  कैसे जनरेट करें, और base64 इमेज डेटा URI का उपयोग कैसे करें।
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: hi
og_description: वर्ड को मार्कडाउन में बदलें और छवियों को बेस64 डेटा यूआरआई के रूप
  में एम्बेड करें। यह चरण‑दर‑चरण ट्यूटोरियल दिखाता है कि वर्ड को मार्कडाउन के रूप
  में कैसे सहेजें और वर्ड से मार्कडाउन कैसे उत्पन्न करें।
og_title: वर्ड को मार्कडाउन में बदलें – बेस64 इमेज एम्बेडिंग गाइड
tags:
- Aspose.Words
- C#
- Markdown
title: वर्ड को मार्कडाउन में बदलें – इमेज को बेस64 के रूप में एम्बेड करें
url: /hi/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word को Markdown में बदलें – इमेजेज़ को Base64 के रूप में एम्बेड करें

क्या आपको कभी **Word को markdown में बदलने** की ज़रूरत पड़ी है लेकिन इमेजेज़ के कारण अटकते रहे हैं? आप अकेले नहीं हैं। Word तस्वीरों को अलग फ़ाइलों में संग्रहीत करना पसंद करता है, जबकि markdown उन छोटे `data:image/...;base64,` स्ट्रिंग्स को पसंद करता है जो सब कुछ एक ही फ़ाइल में व्यवस्थित रखती हैं।  

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य समाधान के माध्यम से चलेंगे जो **Word को markdown के रूप में सहेजता है**, **इमेजेज़ को base64 में एम्बेड करता है**, और यहाँ तक कि आपको दिखाता है कि **Word से markdown कैसे जेनरेट करें** Aspose.Words for .NET का उपयोग करके। अंत तक, आपके पास एक ही `.md` फ़ाइल होगी जो मूल दस्तावेज़ की तरह ही रेंडर होगी—कोई बाहरी इमेज फ़ोल्डर की आवश्यकता नहीं।

## आपको क्या चाहिए

- **.NET 6.0 या बाद का संस्करण** (जो भी NuGet पैकेज को रेफ़र कर सके)
- **Aspose.Words for .NET** (टेस्टिंग के लिए फ्री ट्रायल ठीक है)
- कुछ तस्वीरों वाली एक साधारण `.docx` फ़ाइल (हम इसे `input.docx` कहेंगे)
- आपका पसंदीदा IDE (Visual Studio, Rider, VS Code—जो भी आपको पसंद हो)

यदि आपके पास ये सब है, बढ़िया—चलते हैं आगे। यदि नहीं, तो NuGet पैकेज इंस्टॉल करना एक ही लाइन में हो जाता है:

```bash
dotnet add package Aspose.Words
```

## स्टेप 1: वर्ड डॉक्यूमेंट लोड करें—**वर्ड को मार्कडाउन में बदलने** के लिए शुरुआती पॉइंट

सबसे पहले हमें `.docx` को मेमोरी में लाना होगा। यहीं से रूपांतरण का जादू शुरू होता है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:**  
> डॉक्यूमेंट को लोड करने से Aspose को टेक्स्ट, स्टाइल्स और हर एम्बेडेड रिसोर्स तक पूरी पहुँच मिलती है। इस स्टेप के बिना, बदलने के लिए कुछ नहीं रहेगा।

## स्टेप 2: रिसोर्स-सेविंग कॉलबैक के साथ मार्कडाउनसेवऑप्शन सेट अप करें

Aspose आपको हर रिसोर्स (जैसे इमेजेज़) को इंटरसेप्ट करने की सुविधा देता है, जो सामान्यतः डिस्क पर लिखा जाता है। एक कस्टम `IResourceSavingCallback` प्रदान करके, हम डिफ़ॉल्ट फ़ाइल‑आधारित सेविंग को **base64 इमेज डेटा यूआरआई** से बदल सकते हैं।

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### कस्टम हैंडलर – इमेज को बेस64 में बदलना

नीचे पूरी इम्प्लीमेंटेशन दी गई है। ध्यान दें कि हम `args.ResourceType == ResourceType.Image` की जाँच करते हैं और फिर:

1. इमेज को `MemoryStream` में लिखते हैं।
2. बाइट एरे को Base64 स्ट्रिंग में बदलते हैं।
3. `data:image/jpeg;base64,` यूआरआई बनाते हैं और उसे `args.Uri` को असाइन करते हैं।

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Pro tip:** यदि आपके स्रोत Word में PNG उपयोग हो रहे हैं, तो `ImageSaveOptions.DefaultJpeg` को `ImageSaveOptions.DefaultPng` से बदलें और MIME टाइप को उसी अनुसार बदलें (`image/png`)।

## स्टेप 3: डॉक्यूमेंट को मार्कडाउन के तौर पर सेव करें – आखिरी **वर्ड को मार्कडाउन के तौर पर सेव करें** स्टेप

अब जब कॉलबैक तैयार है, असली सेविंग एक‑लाइनर है।

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

जब आप `output.md` को किसी भी markdown व्यूअर (VS Code प्रीव्यू, GitHub, आदि) में खोलेंगे, तो आपको टेक्स्ट बिल्कुल मूल Word फ़ाइल जैसा दिखेगा, और तस्वीरें इनलाइन बिना किसी अलग इमेज फ़ाइल के दिखाई देंगी।

## उम्मीद का आउटपुट

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]` लाइन एक **base64 इमेज डेटा यूआरआई** है—पूरा इमेज वहीं एन्कोडेड है। कोई अतिरिक्त फ़ोल्डर नहीं, कोई टूटे लिंक नहीं।

## एज केस और उन्हें कैसे हैंडल करें

| सिचुएशन | क्या करें |
|-----------|------------|
| **Large Images** – Base64 आकार को ~33% बढ़ा देता है | रूपांतरण से पहले रीसाइज़ करने पर विचार करें: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Non‑JPEG Images** (PNG, GIF) | मूल फ़ॉर्मेट को `args.ResourceData.ImageType` से पहचानें और सही MIME टाइप सेट करें (`image/png`, `image/gif`). |
| **Very Long Documents** (सैकड़ों इमेजेज़) | मेमोरी उपयोग पर नज़र रखें; यदि RAM खत्म हो जाए तो प्रत्येक इमेज को अस्थायी रूप से डिस्क पर स्ट्रीम कर सकते हैं। |
| **Need Separate Image Files** (जैसे static साइट के लिए) | उन इमेजेज़ के लिए कॉलबैक से `false` रिटर्न करें जिन्हें आप फ़ाइलों के रूप में रखना चाहते हैं, और Aspose को फ़ोल्डर में लिखने दें। |

## आम सवाल (जिनके जवाब पहले ही दे दिए गए हैं)

- **क्या यह .doc फ़ाइलों के साथ काम करता है?** हाँ—Aspose.Words लेगेसी `.doc` फ़ाइलों को भी उसी तरह लोड कर सकता है जैसे आप `.docx` लोड करते हैं। बस `new Document("myfile.doc")` को पॉइंट करें।
- **टेबल्स और फुटनोट्स का क्या?** ये Markdown एक्सपोर्टर द्वारा पूरी तरह सपोर्टेड हैं। टेबल्स markdown टेबल्स बन जाते हैं; फुटनोट्स इनलाइन रेफ़रेंसेज़ बन जाते हैं।
- **क्या मैं markdown फ्लेवर बदल सकता हूँ?** `MarkdownSaveOptions` में `MarkdownVersion` प्रॉपर्टी है (CommonMark, GitHub, आदि)। यदि आपको कोई विशेष सिंटैक्स चाहिए तो सेव करने से पहले इसे सेट करें।

## पूरा, रेडी-टू-रन सैंपल

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉन्सोल ऐप में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी `using` स्टेटमेंट्स, हैंडलर क्लास, और एरर हैंडलिंग शामिल है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

प्रोग्राम चलाएँ, जेनरेट हुई `output.md` खोलें, और आपको अपने Word फ़ाइल की एक परफेक्ट markdown प्रतिलिपि दिखेगी—**convert word to markdown** अब पहले से कहीं आसान है।

## रीकैप

हमने **convert word to markdown** की समस्या को इमेजेज़ को इनलाइन रखते हुए शुरू किया। डॉक्यूमेंट को लोड करके, `MarkdownSaveOptions` कॉलबैक कॉन्फ़िगर करके, और फ़ाइल को सेव करके, हमने एक साफ़ **save word as markdown** समाधान हासिल किया जो **base64 इमेज डेटा यूआरआई** स्ट्रिंग्स उत्पन्न करता है। अब आप जानते हैं कि **इमेजेज़ को base64 में एम्बेड कैसे करें**, एज केस कैसे हैंडल करें, और विभिन्न इमेज टाइप्स के लिए प्रोसेस को कैसे ट्यून करें।

## आगे क्या?

- **HTML जेनरेट करें markdown की बजाय** – `MarkdownSaveOptions` को `HtmlSaveOptions` से बदलें और वही कॉलबैक पुनः उपयोग करें।
- **कई फ़ाइलों को बैच में बदलें** – लॉजिक को फ़ोल्डर के ऊपर `foreach` लूप में रैप करें।
- **CI पाइपलाइन में इंटीग्रेट करें** – स्टैटिक साइट के लिए डॉक्यूमेंटेशन जेनरेशन को ऑटोमेट करें।

बिल्कुल प्रयोग करें, इमेज क्वालिटी को ट्यून करें, या अपना खुद का कस्टम रिसोर्स हैंडलिंग जोड़ें (जैसे इमेजेज़ को CDN पर अपलोड करके URL डालना)। Aspose.Words को थोड़ी C# चतुराई के साथ मिलाकर आप जो भी चाहें, कर सकते हैं।

Happy coding, and may your markdown always render perfectly! 

![Diagram showing convert word to markdown flow – embed images as base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "Word को Markdown में बदलने की प्रक्रिया – इमेजेज़ को Base64 के रूप में एम्बेड करने का डायग्राम")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}