---
category: general
date: 2026-09-11
description: API कुंजी पढ़कर, OpenAI को कॉल करके, और एक Word दस्तावेज़ का संक्षिप्त
  सारांश बनाकर C# में टेक्स्ट को कैसे सारांशित करें, सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: hi
lastmod: 2026-09-11
og_description: C# में टेक्स्ट का सारांश कैसे बनाएं? यह ट्यूटोरियल आपको दिखाता है
  कि API कुंजी कैसे पढ़ें, OpenAI को कॉल करें, और एक Word दस्तावेज़ का सारांश कैसे
  बनाएं।
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: OpenAI के साथ C# में टेक्स्ट का सारांश कैसे बनाएं – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: OpenAI का उपयोग करके C# में टेक्स्ट का सारांश कैसे बनाएं
url: /hi/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में OpenAI का उपयोग करके पाठ का सारांश कैसे बनाएं

यदि आपको .docx फ़ाइल में **पाठ का सारांश कैसे बनाएं** की आवश्यकता है, तो यह गाइड आपको एक पूर्ण, तैयार‑चलाने योग्य समाधान दिखाता है। आप सीखेंगे कि अपने पर्यावरण से API कुंजी कैसे पढ़ें, C# से OpenAI (या Google) को कैसे कॉल करें, और Word दस्तावेज़ का संक्षिप्त सारांश कैसे बनाएं।

Word दस्तावेज़ का सारांश बनाना रिपोर्ट निर्माण, ईमेल डाइजेस्ट, या नॉलेज‑बेस एक्सट्रैक्शन के लिए एक सामान्य आवश्यकता है। इस ट्यूटोरियल के अंत तक आपके पास एक कमांड‑लाइन प्रोग्राम होगा जो आप द्वारा प्रदान की गई किसी भी `.docx` फ़ाइल का पाँच‑वाक्यीय सारांश प्रिंट करता है।

## Prerequisites

- .NET 6.0 SDK या बाद का संस्करण (डाउनलोड करें [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- एक वैध OpenAI API कुंजी जो `OPENAI_API_KEY` नामक पर्यावरण चर में संग्रहीत है (आप **API कुंजी पढ़ें** क्रिया में देखेंगे)
- `.docx` फ़ाइलें पढ़ने के लिए `DocumentFormat.OpenXml` NuGet पैकेज
- `OpenAI` NuGet पैकेज (या यदि आप Google प्रदाता पसंद करते हैं तो `Google.AI`)

## Step 1: Set up the project and install dependencies

एक नया कंसोल प्रोजेक्ट बनाएं और आवश्यक पैकेज जोड़ें:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** यदि आप बाद में अधिक निर्भरताएँ जोड़ते हैं तो संबंधित पैकेजों को `<ItemGroup>` के तहत समूहित करके अपने `csproj` को साफ‑सुथरा रखें।

## Step 2: Read the API key securely

सीक्रेट्स को हार्ड‑कोड करना असुरक्षित है। ट्यूटोरियल पर्यावरण चर से **API कुंजी पढ़ें** का सही तरीका दर्शाता है।

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Step 3: Load the Word document you want to summarize

नीचे दिया गया कोड **Word दस्तावेज़ का सारांश कैसे बनाएं** सामग्री को OpenXML संरचना से सादा पाठ निकालकर दिखाता है।

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Step 4: Build a reusable summarizer class

यह क्लास **OpenAI को कैसे कॉल करें** (या Google) को समाहित करती है और **सारांश कैसे बनाएं** लॉजिक को लागू करती है। यह आपको एक ही enum मान के साथ प्रदाता बदलने की सुविधा भी देती है।

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### Why this structure matters

- **जिम्मेदारियों का विभाजन:** दस्तावेज़ लोड करना, API कुंजी पढ़ना, और AI सेवा को कॉल करना प्रत्येक अपने‑अपने मेथड में अलग किया गया है। इससे कोड का परीक्षण और विस्तार आसान हो जाता है।
- **प्रदाता लचीलापन:** एक enum का उपयोग करके आप OpenAI और Google के बीच बिना कॉलिंग कोड को बदले स्विच कर सकते हैं, जो सीधे **OpenAI को कैसे कॉल करें** और **सारांश कैसे बनाएं** का पुन: उपयोग योग्य उत्तर देता है।
- **त्रुटि संभालना:** अनुपस्थित API कुंजियों से स्पष्ट अपवाद फेंका जाता है, जिससे चुपचाप विफलता नहीं होती।

## Step 5: Put everything together in `Program.cs`

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### Expected output

सैंपल दस्तावेज़ के साथ प्रोग्राम चलाने पर:

```bash
dotnet run -- "sample/input.docx"
```

ऐसा परिणाम मिल सकता है:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Step 6: Common variations and edge cases

| स्थिति | सिफारिशित समायोजन |
|-----------|------------------------|
| **बड़े दस्तावेज़** ( > 10 KB ) | पाठ को हिस्सों में विभाजित करें और प्रत्येक हिस्से का सारांश बनाएं, फिर परिणामों को मिलाएँ। |
| **गैर‑अंग्रेज़ी सामग्री** | प्रॉम्प्ट में भाषा संकेत पास करें, जैसे “निम्नलिखित फ़्रेंच पाठ का सारांश बनाएं …”。 |
| **Google प्रदाता** | `SummarizeWithOpenAIAsync` कॉल को उपयुक्त Google API क्लाइंट से बदलें; वही enum इंटरफ़ेस रखें। |
| **कस्टम सारांश लंबाई** | `SummarizeAsync` कॉल करते समय `maxSentences` तर्क बदलें। |
| **API कुंजी अनुपलब्ध** | `GetOpenAIApiKey` मेथड पहले से ही स्पष्ट अपवाद फेंकता है; यदि आप अधिक मित्रवत संदेश चाहते हैं तो इसे `Main` में पकड़ें। |

## Pro tips for production use

1. **API कुंजी को कैश करें** – प्रत्येक कॉल पर पर्यावरण से पढ़ना नगण्य ओवरहेड जोड़ता है, लेकिन यदि आप एक प्रक्रिया में कई बार सारांशकर्ता को कॉल करते हैं तो इसे स्थिर readonly फ़ील्ड में संग्रहीत कर सकते हैं।
2. **रिक्वेस्ट रेट‑लिमिट** – OpenAI अनुरोध सीमाएँ लागू करता है; यदि आप `429 Too Many Requests` प्राप्त करते हैं तो एक्सपोनेंशियल बैक‑ऑफ़ लागू करें।
3. **इनपुट को साफ़ करें** – बाहरी AI सेवा को पाठ भेजने से पहले व्यक्तिगत पहचान योग्य जानकारी हटाएँ।
4. **एक्सट्रैक्शन लॉजिक का यूनिट टेस्ट** – विभिन्न दस्तावेज़ संरचनाओं के साथ `ExtractTextFromDocx` के काम करने की पुष्टि करने के लिए `WordprocessingDocument` को मॉक करें।

## Conclusion

अब आप C# में **पाठ का सारांश कैसे बनाएं** को सुरक्षित रूप से API कुंजी पढ़कर, OpenAI को कॉल करके, और Word दस्तावेज़ का संक्षिप्त सारांश उत्पन्न करके जानते हैं। यही पैटर्न आपको अन्य प्रदाताओं के साथ **OpenAI को कैसे कॉल करें**, विभिन्न सामग्री प्रकारों के लिए **सारांश कैसे बनाएं** लॉजिक, और पर्यावरण से सुरक्षित रूप से **API कुंजी पढ़ें** मानों की अनुमति देता है। अपने विशिष्ट डोमेन के अनुसार सारांश को अनुकूलित करने के लिए लंबे दस्तावेज़, विभिन्न प्रदाता, या कस्टम प्रॉम्प्ट के साथ प्रयोग करें।

---


## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words API के साथ C# में Word दस्तावेज़ का सारांश – पूर्ण AI‑संचालित गाइड](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Word से PDF कैसे बनाएं – पूर्ण C# गाइड](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word दस्तावेज़ - सामग्री कैसे हटाएँ](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}