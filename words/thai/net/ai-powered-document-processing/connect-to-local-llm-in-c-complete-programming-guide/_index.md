---
category: general
date: 2026-04-28
description: เชื่อมต่อกับ LLM ภายในจาก C# และสั่งให้โมเดลภาษาขนาดใหญ่โหลดเอกสาร Word,
  เรียกใช้ LLM ภายในและเขียนข้อความใหม่โดยอัตโนมัติ. มีโค้ดขั้นตอนโดยละเอียดรวมอยู่.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: th
og_description: เชื่อมต่อกับ LLM ภายในจาก C# และดูวิธีการส่งพรอมต์ให้โมเดลภาษาขนาดใหญ่
  โหลดเอกสาร Word เรียกใช้ LLM ภายใน และเขียนข้อความใหม่โดยอัตโนมัติภายในไม่กี่นาที.
og_title: เชื่อมต่อกับ LLM ภายในเครื่องใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: เชื่อมต่อกับ LLM ภายในเครื่องใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์
url: /th/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เชื่อมต่อกับ Local LLM ใน C# – คู่มือการเขียนโปรแกรมฉบับเต็ม

เคยต้องการ **เชื่อมต่อกับ local llm** จากแอป .NET และสงสัยว่าจะทำให้มันสื่อสารกับไฟล์ Word ได้อย่างไรไหม? คุณไม่ได้เป็นคนเดียว ในคู่มือนี้เราจะพาคุณผ่านกระบวนการทั้งหมด—เชื่อมต่อกับ local llm, **prompt large language model**, โหลดเอกสาร Word, **call local llm**, และสุดท้าย **rewrite text automatically**. เมื่อเสร็จคุณจะได้ตัวอย่างที่สามารถรันได้ซึ่งจะแปลงย่อหน้าใด ๆ ให้เป็นโทนทางการโดยไม่ต้องใช้คีย์ API ภายนอก.

## สิ่งที่บทเรียนนี้ครอบคลุม

เราจะเริ่มด้วยการติดตั้งแพคเกจ NuGet ที่จำเป็น จากนั้นเปิด endpoint ของ Local LLM อย่างง่าย (เช่น Ollama ที่พอร์ต 11434) หลังจากนั้นเราจะโหลดไฟล์ `.docx` ด้วย Aspose.Words ส่งย่อหน้าไปยัง LLM รับเวอร์ชันที่เขียนใหม่และเขียนกลับไปยังเอกสารเดียวกัน คุณยังจะได้เห็นวิธีจัดการกับปัญหาที่พบบ่อย—ย่อหน้าเป็น null, การทำลายแบบ async, และปัญหา encoding—เพื่อให้โค้ดทำงานในสภาพแวดล้อมการผลิต ไม่ใช่แค่การสาธิต

### ข้อกำหนดเบื้องต้น

- .NET 6.0 SDK หรือใหม่กว่า (คุณสามารถใช้ .NET 8 ได้เช่นกัน)
- Visual Studio 2022 หรือ VS Code พร้อมส่วนขยาย C#
- **Aspose.Words for .NET** (รุ่นทดลองฟรีใช้งานได้)
- LLM ที่โฮสต์ในเครื่องซึ่งรองรับสัญญา `/api/generate` (เช่น Ollama, LMStudio)
- ความคุ้นเคยพื้นฐานกับ async/await ใน C#

> **เคล็ดลับมืออาชีพ:** หากคุณยังไม่ได้ติดตั้ง Ollama ให้รัน `ollama serve` และดึงโมเดลด้วย `ollama pull llama3` จุดเชื่อมต่อ HTTP เริ่มต้นจะเป็น `http://localhost:11434/api/generate`.

---

## ขั้นตอนที่ 1: ติดตั้งแพคเกจที่จำเป็น

ขั้นแรก ให้เพิ่มแพคเกจ NuGet ของ Aspose.Words และ Aspose.Words.AI ไปยังโปรเจกต์ของคุณ

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

ไลบรารีเหล่านี้ให้ความสามารถ **load word document** และ wrapper เบาที่ **call local llm** โดยไม่ต้องสร้างคำขอ HTTP ด้วยตนเอง

---

## ขั้นตอนที่ 2: เชื่อมต่อกับ Local LLM Endpoint

การเชื่อมต่อกับโมเดลที่โฮสต์ในเครื่องง่ายเพียงแค่สร้างอินสแตนซ์ของ `LocalLargeLanguageModel` ตัวสร้างคาดหวัง URL เต็มของ endpoint การสร้าง

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

ทำไมเราถึงห่อหุ้ม endpoint ไว้ในคลาส? `LocalLargeLanguageModel` จะจัดการการแปลงเป็น JSON, การลองใหม่, และการสตรีมผลตอบกลับให้คุณ—เพื่อให้คุณมุ่งเน้นที่ตรรกะของ prompt แทนการจัดการกับ `HttpClient`

---

## ขั้นตอนที่ 3: โหลดเอกสาร Word ต้นฉบับ

ต่อไป เรานำเอกสารเข้าสู่หน่วยความจำ Aspose.Words รองรับรูปแบบ Word เกือบทั้งหมด ดังนั้น `Document` จะทำการพาร์ส `input.docx` โดยไม่ต้องติดตั้ง Office

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

หากคุณต้องทำงานกับสตรีม (เช่นไฟล์ที่อัปโหลดผ่าน ASP.NET) เพียงแทนที่เส้นทางไฟล์ด้วย `MemoryStream` แล้วส่งให้กับตัวสร้าง `Document`

---

## ขั้นตอนที่ 4: ดึงข้อความย่อหน้าปัจจุบัน

เราจะใช้ `DocumentBuilder` เพื่อเดินทางในเอกสาร ในตัวอย่างนี้เราจะแก้ไข **ย่อหน้าแรก** แต่คุณสามารถวนลูปผ่าน `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` เพื่อประมวลผลหลายย่อหน้าได้

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

ตัวดำเนินการ `?.` ป้องกัน `NullReferenceException` หากเอกสารว่างเปล่า นี่เป็นหนึ่งใน **edge cases** ที่ทำให้ผู้เริ่มต้นหลง

---

## ขั้นตอนที่ 5: Prompt LLM เพื่อเขียนย่อหน้าใหม่

ตอนนี้เราจริง ๆ แล้ว **prompt large language model** คำสั่งเป็นภาษาอังกฤษธรรมดา; wrapper จะส่งเป็น JSON ไปยัง endpoint ในเครื่อง

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

ทำไมต้องวางรูปแบบคำขอแบบนี้? LLM จะตอบสนองดีที่สุดต่อคำสั่งที่ชัดเจนและทำงานเดียว การเพิ่มบรรทัดใหม่หลังเครื่องหมายโคลอนจะแยกคำสั่งออกจากเนื้อหา ลดความเป็นไปได้ที่โมเดลจะเอาคำสั่งกลับมา

**ผลลัพธ์ที่คาดหวัง** – หาก `originalParagraph` มีค่าเป็น `"Hey, what's up?"` LLM อาจคืนค่า:

> “Good day, how may I assist you?”

คุณสามารถตรวจสอบผลลัพธ์โดยการพิมพ์ออกมาดู:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## ขั้นตอนที่ 6: แทรกข้อความที่เขียนใหม่กลับเข้าไปในเอกสาร

เมื่อได้ข้อความใหม่แล้ว เราจะแทนที่ย่อหน้าเดิม `DocumentBuilder.Writeln` จะเขียนบรรทัดใหม่และเลื่อนเคอร์เซอร์ไปข้างหน้า ซึ่งเหมาะสำหรับการต่อท้าย หากคุณต้องการ *แทนที่* ย่อหน้าเดิมโดยตรง คุณสามารถใช้ `docBuilder.CurrentParagraph.RemoveAllChildren()` ก่อนเขียน

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

ทั้งสองวิธีถูกแสดงไว้เพื่อให้คุณเลือกตามกระบวนการทำงานของคุณ

---

## ขั้นตอนที่ 7: บันทึกเอกสารที่อัปเดต

สุดท้าย เราจะบันทึกการเปลี่ยนแปลงลงไฟล์ใหม่ Aspose.Words จะเลือกฟอร์แมตโดยอัตโนมัติตามส่วนขยายของไฟล์

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

เปิด `output.docx` ด้วย Word แล้วคุณจะเห็นย่อหน้าตอนนี้อ่านในโทนทางการ

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็น **โปรแกรมที่สมบูรณ์และเป็นอิสระ** คัดลอกและวางลงในโปรเจกต์คอนโซล, รีสโตร์แพคเกจ NuGet, แล้วรัน—ไม่ต้องตั้งค่าเพิ่มเติมนอกจากต้องมี Local LLM ที่ทำงานอยู่

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### สิ่งที่คาดว่าจะเกิดขึ้นเมื่อคุณรัน

1. คอนโซลจะแสดงย่อดั้งเดิมและย่อหน้าใหม่ที่เขียนใหม่  
2. `output.docx` ปรากฏข้าง `input.docx`  
3. การเปิดไฟล์จะแสดงย่อหน้าใหม่ในโทนทางการที่แทรกหลังย่อดั้งเดิม (หรือแทนที่ หากคุณเปลี่ยนเป็นโค้ดทางเลือก)

---

## การจัดการ Edge Cases ที่พบบ่อย

| Situation | Solution |
|-----------|----------|
| **ย่อหน้าเป็นค่าว่างหรือมีเพียงช่องว่าง** | ตรวจสอบ `string.IsNullOrWhiteSpace` ก่อนทำ prompt (ดูขั้นตอน 3) |
| **LLM ส่งคืนข้อผิดพลาดหรือสตริงว่าง** | ห่อ `PromptAsync` ด้วย `try/catch` แล้วใช้ข้อความเดิมเป็นสำรอง |
| **หลายย่อหน้าต้องการการเขียนใหม่** | วนลูปผ่าน `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` และใช้ตรรกะ prompt เดียวกัน |
| **เอกสารขนาดใหญ่ทำให้เกิดความล่าช้า** | จัดกลุ่มย่อหน้าและส่งในคำขอเดียว (prompt สูงสุด 4 KB ต่อการเรียก) |
| **อักขระที่ไม่ใช่ ASCII เกิดการบิดเบือน** | ตรวจสอบให้ endpoint ของ LLM ใช้ UTF-8 (โมเดลสมัยใหม่ส่วนใหญ่ทำเช่นนั้น) |

---

## ขั้นตอนต่อไปและหัวข้อที่เกี่ยวข้อง

- **Prompt large language model** ด้วยคำสั่งที่ละเอียดขึ้น (เช่น คู่มือสไตล์, ขีดจำกัดความยาว).  
- ใช้ **call local llm** ใน Web API เพื่อเปิดเผยการทำงานอัตโนมัติของเอกสารเป็นบริการ.  
- สำรวจ **load word document** ในสตรีมแบบขนานสำหรับสถานการณ์ที่ต้องการ throughput สูง.  
- รวมวิธีนี้กับ **rewrite text automatically** เพื่อสร้างอีเมลจำนวนมากหรือมาตรฐานรายงาน.

หากคุณต้องการเจาะลึกเพิ่มเติม ให้ดูเอกสารของ Aspose เกี่ยวกับ **document merging** และอ้างอิง API ของ Ollama สำหรับพารามิเตอร์การสุ่มแบบกำหนดเอง

---

## สรุป

เราได้แสดงให้คุณเห็นวิธี **connect to local llm** จาก C#, **prompt large language model**, **load word document**, **call local llm**, และ **rewrite text automatically**—ทั้งหมดในแอปคอนโซลที่สามารถรันได้หนึ่งเดียว รูปแบบนี้สามารถขยายได้: เปลี่ยน prompt, วนลูปผ่านย่อหน้า, หรือเปิดเผยตรรกะผ่าน endpoint ของ ASP.NET สิ่งที่สำคัญคือโมเดล AI ในเครื่องสามารถบูรณาการอย่างแน่นหนากับไลบรารีการประมวลผลเอกสารแบบคลาสสิก ทำให้คุณได้อัตโนมัติที่ทรงพลังโดยไม่ต้องออกจากสภาพแวดล้อม on‑prem ที่คุณเชื่อถือ

มีคำถามเกี่ยวกับ threading หรือไม่,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}