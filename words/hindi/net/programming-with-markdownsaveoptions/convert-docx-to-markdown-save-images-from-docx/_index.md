---
category: general
date: 2026-06-27
description: Aspose.Words का उपयोग करके docx को markdown में बदलें और docx से छवियों
  को सहेजें। जानें कि Word फ़ाइल से छवियों को कैसे निकालें और Word दस्तावेज़ को markdown
  के रूप में निर्यात करें।
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: hi
og_description: docx को markdown में बदलें और docx से छवियों को सहेजें। यह गाइड दिखाता
  है कि Word फ़ाइल से छवियों को कैसे निकालें और Word दस्तावेज़ को markdown के रूप
  में निर्यात करें।
og_title: DOCX को मार्कडाउन में बदलें और DOCX से इमेज़ सहेजें
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: docx को markdown में परिवर्तित करें और docx से छवियों को सहेजें
url: /hi/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert docx to markdown & save images from docx

क्या आपने कभी सोचा है कि **docx को markdown में कैसे बदलें** बिना आपके Word फ़ाइल में एम्बेड की गई तस्वीरों को खोए? आप अकेले नहीं हैं—डेवलपर्स अक्सर एक साफ़ Markdown संस्करण की आवश्यकता रखते हैं जबकि हर डायग्राम, लोगो, या स्क्रीनशॉट को बरकरार रखना चाहते हैं।

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य उदाहरण के माध्यम से दिखाएंगे कि **.docx को Markdown में कैसे बदलें**, **docx से तस्वीरें एक फ़ोल्डर में कैसे सहेजें** जिसे आप चुनें, और दिखाएंगे कि **Word फ़ाइल से तस्वीरें कैसे निकालें** Aspose.Words लाइब्रेरी की शक्ति से। अंत तक आप यह भी जानेंगे कि **Word दस्तावेज़ को markdown के रूप में कैसे निर्यात करें** एक ही लाइन कोड में।

## What you’ll need

- .NET 6+ (या .NET Framework 4.7.2+) आपके मशीन पर इंस्टॉल हो  
- `Aspose.Words` का NuGet रेफ़रेंस (फ़्री ट्रायल ठीक रहेगा)  
- एक नमूना `input.docx` जिसमें कम से कम एक तस्वीर हो  
- आपका पसंदीदा IDE—Visual Studio, Rider, या यहाँ तक कि VS Code भी चलेगा  

कोई अतिरिक्त थर्ड‑पार्टी टूल नहीं, कोई जटिल कमांड‑लाइन जिम्नास्टिक नहीं। सिर्फ़ सीधा C# कोड।

## Convert docx to markdown – Overview

मुख्य विचार सरल है:

1. स्रोत Word दस्तावेज़ को लोड करें।  
2. Aspose.Words को बताएं कि बाहरी संसाधनों (जैसे तस्वीरें) को कैसे हैंडल करना है।  
3. दस्तावेज़ को Markdown के रूप में सेव करें, लाइब्रेरी को बाकी काम करने दें।

नीचे **पूरा, चलाने‑योग्य प्रोग्राम** दिया गया है। इसे नई कंसोल प्रोजेक्ट में कॉपी‑पेस्ट करके `Ctrl+F5` दबाएँ।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### How the code works

- **Loading the document** (`new Document(inputPath)`) हमें Word फ़ाइल का इन‑मेमोरी प्रतिनिधित्व देता है, जिसमें सभी भाग—पैराग्राफ, टेबल, और **images**—शामिल होते हैं।  
- **`MarkdownSaveOptions`** वह जगह है जहाँ जादू होता है। `ResourceSavingCallback` को अटैच करके हम Aspose.Words द्वारा लिखी जाने वाली हर बाहरी रिसोर्स पर पूर्ण नियंत्रण प्राप्त करते हैं।  
- कॉलबैक के अंदर हम **extract images from Word file** करते हैं यह जाँच कर कि `args.ResourceType == ResourceType.Image` है या नहीं। कॉलबैक को इमेज बाइट्स, उसका मूल एक्सटेंशन, और एक `SavePath` प्रॉपर्टी मिलती है जिसे हम रन‑टाइम पर बनाते हुए फ़ोल्डर में सेट करते हैं। `Guid.NewGuid()` का उपयोग करने से फ़ाइलनाम यूनिक रहता है, इसलिए पिछली रन की फ़ाइलें ओवरराइट नहीं होंगी।  
- हम **CSS को स्किप** करते हैं (`ResourceType.CssStyleSheet`) क्योंकि साधारण Markdown को स्टाइलशीट की ज़रूरत नहीं होती। इससे आउटपुट साफ़ रहता है।  
- अंत में, `doc.Save(outputPath, mdOptions)` Markdown फ़ाइल लिखता है, Word की संरचनाओं को Markdown समकक्ष में बदल देता है (हेडिंग्स `#` बनती हैं, टेबल्स पाइप‑सेपरेटेड रोज़ बनते हैं, आदि)।

## Save images from docx – Custom folder strategy

कस्टम फ़ोल्डर की ज़रूरत क्यों? कल्पना करें कि आप CI पाइपलाइन के लिए डॉक्यूमेंटेशन जेनरेट कर रहे हैं। आप चाहते हैं कि Markdown फ़ाइल और उसकी एसेट्स साइड‑बाय‑साइड एक साफ़, पुनरुत्पादित लेआउट में हों।

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

कुछ **प्रो टिप्स**:

- **फ़ोल्डर पाथ को प्रोजेक्ट रूट के रिलेटिव रखें**। इस तरह Markdown फ़ाइल इमेजेज़ को रिलेटिव लिंक (`![Alt text](Images/abc123.png)`) से रेफ़र कर सकेगी, जो GitHub, GitLab, या किसी भी स्टैटिक‑साइट जेनरेटर पर काम करेगा।  
- **यदि आपको डिटरमिनिस्टिक नाम चाहिए** (जैसे, वही इमेज हमेशा वही फ़ाइलनाम पाए), तो GUID को इमेज बाइट्स के हैश से बदलें: `MD5.Create().ComputeHash(args.Data)`। यह छोटा बदलाव कैशिंग के लिए उपयोगी हो सकता है।

## Extract images from Word file – Edge cases

1. **Multiple image formats** – Aspose.Words PNG, JPEG, GIF, BMP, और यहाँ तक कि SVG को सपोर्ट करता है। `args.Extension` प्रॉपर्टी में सही फ़ाइल एक्सटेंशन पहले से ही होता है, इसलिए आपको अनुमान लगाने की ज़रूरत नहीं।  
2. **Very large images** – यदि आपके स्रोत दस्तावेज़ में हाई‑रेज़ोल्यूशन फ़ोटो हैं, तो जेनरेटेड फ़ाइलें बड़ी हो सकती हैं। कॉलबैक के बाद एक कम्प्रेशन स्टेप जोड़ने पर विचार करें, `System.Drawing` या `ImageSharp` का उपयोग करके।  
3. **Hidden images** – Word हेडर/फ़ूटर या टेक्स्ट बॉक्स में भी इमेजेज़ रख सकता है। कॉलबैक उन्हें सभी देखता है, इसलिए आप **हर** तस्वीर निकालेंगे, न कि केवल दिखने वाली। यदि आप केवल बॉडी इमेजेज़ चाहते हैं, तो `args.ImageIndex` पर फ़िल्टर लगाएँ या `args.ImageType` की जाँच करें।

## Export Word document as markdown – Verifying the result

प्रोग्राम चलाने के बाद, `output.md` को किसी भी Markdown व्यूअर में खोलें। आपको कुछ इस तरह दिखना चाहिए:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

ध्यान दें कि इमेज लिंक **Images** फ़ोल्डर की ओर इशारा कर रहा है जिसे हमने बनाया था। यही सफल **export Word document as markdown** ऑपरेशन की निशानी है।

### Quick sanity check

- क्या Markdown फ़ाइल VS Code के प्रीव्यू पेन में बिना त्रुटि खुलेगी? ✅  
- क्या सभी तस्वीरें GitHub पर फ़ाइल देखे जाने पर प्रदर्शित होंगी? ✅  
- क्या `Images` डायरेक्टरी में मूल `.docx` की हर तस्वीर के लिए एक फ़ाइल बनी है? ✅  

यदि इनमें से कोई भी चेक फेल हो, तो `ResourceSavingCallback` लॉजिक को दोबारा देखें और सुनिश्चित करें कि `YOUR_DIRECTORY` प्लेसहोल्डर एक राइटेबल लोकेशन की ओर इशारा कर रहा है।

## Common pitfalls and how to avoid them

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Images not appearing** | Callback never fired because `ResourceSavingCallback` wasn’t assigned. | Assign the callback **before** calling `doc.Save`. |
| **Empty Images folder** | `args.Cancel = true` was set for all resources inadvertently. | Only cancel CSS (`ResourceType.CssStyleSheet`), leave images untouched. |
| **File‑path too long on Windows** | Using deep nested folders plus GUIDs can exceed 260 characters. | Keep the folder shallow, or enable long‑path support in Windows 10+. |
| **Duplicate image names** | Using `DateTime.Now.Ticks` instead of GUID can collide on fast loops. | Stick with `Guid.NewGuid()` for uniqueness. |

## Wrap‑up

हमने अभी **docx को markdown में बदला**, **docx से तस्वीरें सहेजी**, और दिखाया कि **Word फ़ाइल से तस्वीरें कैसे निकाली जाएँ** जबकि **Word दस्तावेज़ को markdown के रूप में निर्यात किया जाए** एक साफ़, दोहराने योग्य तरीके से। पूरा प्रोसेस Aspose.Words के `ResourceSavingCallback` पर निर्भर करता है, जो आपको हर बाहरी एसेट पर ग्रैन्युलर कंट्रोल देता है।

### What’s next?

- **Style the Markdown** – Jekyll या Hugo के लिए एक फ्रंट‑मेटर ब्लॉक जोड़ें।  
- **Automate the pipeline** – इस कोड को Azure DevOps या GitHub Action स्टेप में एम्बेड करें।  
- **Handle tables and footnotes** – `MarkdownSaveOptions` के अन्य फ़्लैग्स जैसे `ExportTableBorderStyles` को एक्सप्लोर करें।  

फ़ोल्डर स्ट्रक्चर को कस्टमाइज़ करने, इमेज कम्प्रेशन जोड़ने, या आउटपुट फ़ॉर्मेट को HTML में बदलने के लिए `MarkdownSaveOptions` को `HtmlSaveOptions` से स्वैप करने में संकोच न करें। जब आपके पास **convert docx to markdown** के लिए एक ठोस बेस हो, तो संभावनाएँ असीमित हैं।

Happy coding, and may your documentation always stay both beautiful **and** machine‑readable!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}