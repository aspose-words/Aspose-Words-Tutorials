---
category: general
date: 2026-09-11
description: เรียนรู้วิธีสรุปข้อความใน C# โดยอ่านคีย์ API เรียกใช้ OpenAI และสร้างสรุปสั้นกระชับของเอกสาร
  Word
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: th
lastmod: 2026-09-11
og_description: วิธีสรุปข้อความใน C#? บทเรียนนี้จะแสดงวิธีอ่านคีย์ API, เรียกใช้ OpenAI,
  และสร้างสรุปของเอกสาร Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: วิธีสรุปข้อความใน C# ด้วย OpenAI – คู่มือขั้นตอนโดยละเอียด
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
title: วิธีสรุปข้อความใน C# ด้วย OpenAI
url: /th/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสรุปข้อความใน C# ด้วย OpenAI

หากคุณต้องการ **how to summarize text** ในไฟล์ .docx นี้ คู่มือจะแสดงวิธีแก้ไขที่สมบูรณ์และพร้อมใช้งาน คุณจะได้เรียนรู้วิธีอ่าน API key จากสภาพแวดล้อมของคุณ วิธีเรียกใช้ OpenAI (หรือ Google) จาก C# และวิธีสร้างสรุปสั้น ๆ ของเอกสาร Word

การสรุปเอกสาร Word เป็นความต้องการทั่วไปสำหรับการสร้างรายงาน, สรุปอีเมล, หรือการสกัดข้อมูลจากฐานความรู้. เมื่อจบบทเรียนนี้ คุณจะมีโปรแกรมบรรทัดคำสั่งที่พิมพ์สรุป 5 ประโยคของไฟล์ `.docx` ใด ๆ ที่คุณระบุ.

## ข้อกำหนดเบื้องต้น

- .NET 6.0 SDK หรือใหม่กว่า (ดาวน์โหลดจาก [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- คีย์ API ของ OpenAI ที่ถูกต้องซึ่งเก็บไว้ในตัวแปรสภาพแวดล้อมชื่อ `OPENAI_API_KEY` (คุณจะเห็น **read api key** ในการทำงาน)
- แพคเกจ NuGet `DocumentFormat.OpenXml` สำหรับอ่านไฟล์ `.docx`
- แพคเกจ NuGet `OpenAI` (หรือ `Google.AI` หากคุณต้องการใช้ผู้ให้บริการของ Google)

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และติดตั้ง dependencies

สร้างโปรเจกต์คอนโซลใหม่และเพิ่มแพคเกจที่จำเป็น:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** รักษาไฟล์ `csproj` ของคุณให้เป็นระเบียบโดยการจัดกลุ่มแพคเกจที่เกี่ยวข้องภายใต้ `<ItemGroup>` หากคุณเพิ่ม dependencies เพิ่มเติมในภายหลัง

## ขั้นตอนที่ 2: อ่าน API key อย่างปลอดภัย

การเขียนค่าลับแบบ hard‑coding ไม่ปลอดภัย บทเรียนนี้แสดงวิธีที่ถูกต้องในการ **read api key** จากตัวแปรสภาพแวดล้อม

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

## ขั้นตอนที่ 3: โหลดเอกสาร Word ที่คุณต้องการสรุป

โค้ดด้านล่างแสดง **how to summarize word document** โดยการดึงข้อความธรรมดาจากโครงสร้าง OpenXML

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

## ขั้นตอนที่ 4: สร้างคลาส summarizer ที่นำกลับมาใช้ได้

คลาสนี้บรรจุ **how to call openai** (หรือ Google) และทำงานตามตรรกะของ **how to create summary** นอกจากนี้ยังให้คุณสลับผู้ให้บริการด้วยค่า enum เพียงค่าเดียว

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

### ทำไมโครงสร้างนี้ถึงสำคัญ

- **Separation of concerns:** การโหลดเอกสาร, การอ่าน API key, และการเรียกใช้บริการ AI ถูกแยกออกเป็นเมธอดของตนเอง ทำให้โค้ดง่ายต่อการทดสอบและขยาย
- **Provider flexibility:** ด้วยการใช้ enum คุณสามารถสลับระหว่าง OpenAI และ Google ได้โดยไม่ต้องแก้ไขโค้ดที่เรียกใช้ ซึ่งตอบตรงกับ **how to call openai** และ **how to create summary** ในรูปแบบที่นำกลับมาใช้ได้
- **Error handling:** หากไม่มี API key จะโยนข้อยกเว้นที่ชัดเจน ป้องกันการล้มเหลวแบบเงียบ

## ขั้นตอนที่ 5: รวมทุกอย่างเข้าด้วยกันใน `Program.cs`

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

### ผลลัพธ์ที่คาดหวัง

รันโปรแกรมด้วยเอกสารตัวอย่าง:

```bash
dotnet run -- "sample/input.docx"
```

อาจได้ผลลัพธ์ดังนี้:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## ขั้นตอนที่ 6: ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับแนะนำ |
|-----------|------------------------|
| **Large documents** ( > 10 KB ) | แยกข้อความเป็นส่วนย่อยและสรุปแต่ละส่วน แล้วรวมผลลัพธ์เข้าด้วยกัน |
| **Non‑English content** | ส่งคำบ่งชี้ภาษาในพรอมต์ เช่น “Summarize the following French text …”. |
| **Google provider** | แทนที่การเรียก `SummarizeWithOpenAIAsync` ด้วยไคลเอนต์ Google API ที่เหมาะสม; รักษาอินเทอร์เฟซ enum เดิม |
| **Custom summary length** | เปลี่ยนค่าอาร์กิวเมนต์ `maxSentences` เมื่อเรียก `SummarizeAsync` |
| **Missing API key** | `GetOpenAIApiKey` method มีการโยนข้อยกเว้นที่ชัดเจนแล้ว; ให้จับใน `Main` หากต้องการข้อความที่เป็นมิตรกว่า |

## เคล็ดลับระดับมืออาชีพสำหรับการใช้งานในโปรดักชัน

1. **Cache the API key** – อ่านจากสภาพแวดล้อมในแต่ละครั้งเพิ่มภาระที่น้อยมาก แต่คุณสามารถเก็บไว้ในฟิลด์ static readonly หากเรียกใช้ summarizer หลายครั้งในกระบวนการเดียว
2. **Rate‑limit requests** – OpenAI กำหนดขีดจำกัดการร้องขอ; ให้ทำการ back‑off แบบเอ็กซ์โพเนนเชียลหากเจอ `429 Too Many Requests`
3. **Sanitize input** – ลบข้อมูลส่วนบุคคลที่สามารถระบุตัวตนได้ก่อนส่งข้อความไปยังบริการ AI ภายนอก
4. **Unit test the extraction logic** – mock `WordprocessingDocument` เพื่อตรวจสอบว่า `ExtractTextFromDocx` ทำงานกับโครงสร้างเอกสารที่ต่างกันได้

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to summarize text** ใน C# ด้วยการอ่าน API key อย่างปลอดภัย, เรียก OpenAI, และสร้างสรุปสั้น ๆ ของเอกสาร Word รูปแบบเดียวกันนี้ทำให้คุณสามารถ **how to call openai** กับผู้ให้บริการอื่น, **how to create summary** สำหรับประเภทเนื้อหาต่าง ๆ, และอ่านค่า **read api key** จากสภาพแวดล้อมได้อย่างปลอดภัย ทดลองกับเอกสารที่ยาวขึ้น, ผู้ให้บริการที่ต่างกัน, หรือพรอมต์ที่กำหนดเองเพื่อปรับการสรุปให้เหมาะกับโดเมนของคุณ

---

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [สรุปเอกสาร Word ใน C# ด้วย Aspose.Words API – คู่มือ AI‑Powered ฉบับเต็ม](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [วิธีสร้าง PDF จาก Word – คู่มือ C# ฉบับเต็ม](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [เอกสาร Word - วิธีลบเนื้อหา](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}