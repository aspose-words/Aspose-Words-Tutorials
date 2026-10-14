---
category: general
date: 2026-10-13
description: วิธีเปลี่ยนตัวคั่นเชิงอรรถในเอกสาร Word ด้วย Aspose.Words. เรียนรู้การเปลี่ยนสีตัวอักษรในเอกสาร
  Word อย่างโปรแกรมมิ่ง.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: th
lastmod: 2026-10-13
og_description: วิธีเปลี่ยนตัวคั่นเชิงอรรถในเอกสาร Word ด้วย Aspose.Words บทเรียนนี้จะแสดงวิธีเปลี่ยนสีตัวอักษรในเอกสาร
  Word ด้วย C#
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: วิธีเปลี่ยนตัวคั่นเชิงอรรถในเอกสาร Word – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: วิธีเปลี่ยนตัวคั่นเชิงอรรถและปรับแต่งสไตล์ของมันในเอกสาร Word
url: /th/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการเปลี่ยนตัวคั่นเชิงอรรถและปรับแต่งสไตล์ในเอกสาร Word

หากคุณต้องการ **how to change footnote separator** ในเอกสาร Word คำแนะนำนี้จะให้วิธีแก้ไขที่ครบถ้วนและพร้อมใช้งาน โดยใช้ Aspose.Words for .NET คุณยังสามารถ **change font color in Word document** ในส่วนต่าง ๆ เช่น ตัวคั่นเชิงอรรถและเชิงอรรถท้าย ทำให้ไฟล์ขั้นสุดท้ายตรงกับแบรนด์หรือคู่มือสไตล์ของคุณ

ผู้เขียนเอกสารมักถามว่า: *Why does the default footnote separator look plain, and how can I make it stand out?* คำตอบคือการเข้าถึงออบเจ็กต์ย่อหน้าตัวคั่นโดยตรง ปรับคุณสมบัติฟอนต์ของมัน แล้วบันทึกผลลัพธ์ บทแนะนำนี้จะพาคุณผ่านทุกขั้นตอน ตั้งแต่การโหลดไฟล์ .docx จนถึงการบันทึกผลลัพธ์ที่มีสไตล์

คุณจะได้เรียนรู้วิธี:

* โหลดไฟล์ Word ที่มีเชิงอรรถและเชิงอรรถท้ายอยู่แล้ว  
* ค้นหาย่อหน้าตัวคั่นเชิงอรรถและเชิงอรรถท้าย  
* เปลี่ยนสีฟอนต์ของแต่ละตัวคั่น (สีแดงสำหรับเชิงอรรถ, สีน้ำเงินสำหรับเชิงอรรถท้าย)  
* บันทึกเอกสารที่แก้ไขแล้วโดยไม่สูญเสียเนื้อหาเดิม  

ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจากไลบรารี Aspose.Words และสภาพแวดล้อมการพัฒนา .NET

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือรุ่นใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)  
* Visual Studio 2022, Rider หรือโปรแกรมแก้ไข C# ใด ๆ ที่คุณชอบ  
* แพคเกจ NuGet Aspose.Words for .NET (`Aspose.Words`)  
* ไฟล์ Word ตัวอย่าง (`Footnotes.docx`) ที่มีอย่างน้อยหนึ่งเชิงอรรถและหนึ่งเชิงอรรถท้าย  

> **Pro tip:** หากคุณไม่มีไฟล์ตัวอย่าง ให้สร้างเอกสาร Word ใหม่ แทรกเชิงอรรถ (`References → Insert Footnote`) และเชิงอรรถท้าย (`References → Insert Endnote`) แล้วบันทึกเป็น `Footnotes.docx` ในโฟลเดอร์ที่คุณสามารถอ้างอิงจากโค้ดได้

## วิธีการเปลี่ยนตัวคั่นเชิงอรรถด้วย Aspose.Words

หัวใจของงานคือการดึงย่อหน้าพิเศษที่ Aspose.Words เปิดเผยเป็นโหนด *separator* โหนดเหล่านี้เป็นประเภท `Paragraph` และสามารถจัดรูปแบบได้เช่นเดียวกับย่อหน้าอื่น ๆ  

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### ทำไมแต่ละบรรทัดจึงสำคัญ

* **Loading the document** (`new Document`) ให้คุณได้การแสดงผลในหน่วยความจำที่ Aspose.Words สามารถจัดการได้  
* **`GetChild` with `ParagraphNodeType.FootnoteSeparator`** คืนค่าย่อหน้าที่ซ่อนอยู่ที่ Word ใช้วาดเส้นแบ่งเชิงอรรถจากข้อความหลัก วิธีเดียวกันทำงานกับตัวคั่นเชิงอรรถท้าย  
* **Changing `Font.Color`** มีผลโดยตรงต่อการแสดงผลของเส้น เนื่องจาก Word แสดงตัวคั่นเป็นย่อหน้าที่มีอักขระ “‑” เพียงตัวเดียว การตั้งค่าสีเป็น `Color.Red` (หรือ `System.Drawing.Color` ใด ๆ) จะอัปเดตสไตล์ภาพ  
* **Saving** เขียนการเปลี่ยนแปลงกลับไปยังไฟล์ .docx ที่โปรแกรมประมวลผล Word ใด ๆ ก็สามารถเปิดได้  

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิดไฟล์ `FootnoteSeparatorsStyled.docx` ใน Microsoft Word:

* เส้นตัวคั่นเชิงอรรถปรากฏเป็นสี **red**  
* เส้นตัวคั่นเชิงอรรถท้ายปรากฏเป็นสี **blue**  

เนื้อหาเชิงอรรถและเชิงอรรถท้ายเดิมทั้งหมดยังคงอยู่โดยไม่ถูกแก้ไข  

## การเปลี่ยนสีฟอนต์ในเอกสาร Word ด้วย C#

การดำเนินการที่แสดงด้านบนเป็นกรณีเฉพาะของความสามารถที่กว้างกว่า: **change font color in Word document** อย่างโปรแกรมเมติก เมื่อคุณมี `Paragraph`, `Run` หรือ `Node` ใด ๆ ที่มีข้อความ คุณสามารถปรับคุณสมบัติ `Font.Color` ของมันได้  

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* สคริปต์นี้วนลูปผ่านทุกย่อหน้า ตรวจสอบว่ามีสไตล์ `Heading 1` หรือไม่ และตั้งค่าสีฟอนต์ของมัน  
* คุณสามารถปรับเงื่อนไขเพื่อกำหนดเป้าหมายที่เชิงอรรถ ตาราง หรือโหนดประเภทอื่นใดก็ได้  

## การแยกขั้นตอนทีละขั้นตอน

### 1. ติดตั้ง Aspose.Words

เปิดเทอร์มินัลในโฟลเดอร์โครงการของคุณและรันคำสั่ง:  

```bash
dotnet add package Aspose.Words
```

แพคเกจนี้รวมเอา assembly ทั้งหมดที่จำเป็นสำหรับโค้ดที่แสดงไว้ก่อนหน้านี้  

### 2. เตรียมไฟล์อินพุต

วางไฟล์ `Footnotes.docx` ไว้ในไดเรกทอรีที่รู้จัก (เช่น `C:\Docs`). ตรวจสอบว่าไฟล์มีอย่างน้อยหนึ่งเชิงอรรถและหนึ่งเชิงอรรถท้ายเพื่อให้โหนดตัวคั่นมีอยู่  

### 3. เขียนโปรแกรม C#

สร้างโปรเจกต์คอนโซลใหม่ (`dotnet new console -n FootnoteStyler`) แล้วแทนที่ไฟล์ `Program.cs` ที่สร้างขึ้นด้วยบล็อกโค้ดเต็มจากส่วน **How to change footnote separator** อย่าลืมปรับเส้นทางไฟล์ให้ตรงกับสภาพแวดล้อมของคุณ  

### 4. รันและตรวจสอบ

เรียกใช้โปรแกรม:  

```bash
dotnet run
```

เมื่อการรันเสร็จสิ้น ให้เปิดไฟล์ `FootnoteSeparatorsStyled.docx` คุณควรเห็นเส้นตัวคั่นสีแดงและสีน้ำเงินตามที่อธิบาย  

### 5. ขยายโซลูชัน

* **Different colors:** ใช้ค่า `System.Drawing.Color` ใดก็ได้ เช่น `Color.FromArgb(255, 128, 0)` สำหรับสีส้ม  
* **Custom line style:** แทนการเปลี่ยนสี คุณสามารถแก้ไขคุณสมบัติ `ParagraphFormat` เช่น `LineSpacing`, `Shading` หรือแม้แต่แทนที่อักขระตัวคั่น  
* **Multiple documents:** ห่อหุ้มตรรกะในเมธอดที่รับพาธอินพุตและเอาต์พุต แล้วเรียกใช้ในลูปเพื่อประมวลผลหลายไฟล์  

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Symptom | Cause | Fix |
|---------|-------|-----|
| `GetChild` returns `null` | เอกสารต้นทางไม่มีตัวคั่นเชิงอรรถ/เชิงอรรถท้าย (เช่น ไม่มีเชิงอรรถ) | เพิ่มอย่างน้อยหนึ่งเชิงอรรถหรือเชิงอรรถท้าย หรือเช็ค `null` ก่อนเข้าถึง `Font` |
| Color change not visible | ตัวคั่นถูกแสดงเป็นเส้นแทนที่จะเป็นอักขระในบางเวอร์ชันของ Word | ตั้งค่า `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` และ `ParagraphFormat.LineSpacing = 1` เพื่อบังคับให้มีอักขระที่มองเห็นได้ |
| Runtime exception `FileNotFoundException` | เส้นทางไฟล์ไม่ถูกต้อง | ใช้เส้นทางแบบ absolute หรือ `Path.Combine` กับ `Environment.CurrentDirectory` |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปคอนโซลได้ รวมถึงการจัดการข้อผิดพลาดและคอมเมนต์ที่อธิบายแต่ละการดำเนินการ  

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

การรันโปรแกรมนี้จะสร้างไฟล์ Word ที่เส้นตัวคั่นเชิงอรรถเป็นสีแดงและเส้นตัวคั่นเชิงอรรถท้ายเป็นสีน้ำเงิน ทำให้ตรงตามความต้องการ **how to change footnote separator** พร้อมแสดงตัวอย่าง **change font color in word document**  

## สรุป

คุณตอนนี้รู้แล้วว่า **how to change footnote separator** ในเอกสาร Word ด้วย Aspose.Words for .NET และวิธี **change font color in Word document** อย่างโปรแกรมเมติก วิธีการคือ:

1. โหลดเอกสาร  
2. ดึงย่อหน้าตัวคั่นที่ซ่อนอยู่  
3. ตั้งค่าคุณสมบัติ `Font.Color` ของพวกมัน  
4. บันทึกไฟล์ที่แก้ไขแล้ว  

จากนี้คุณสามารถสำรวจการจัดรูปแบบขั้นสูงเพิ่มเติมได้ เช่น ปรับความหนาของเส้น ใช้ฟอนต์ต่าง ๆ หรืออัตโนมัติกระบวนการในหลายไฟล์ การเชี่ยวชาญเทคนิคเหล่านี้จะให้การควบคุมระดับละเอียดต่อการแสดงผลของเอกสาร Word โดยตรงจากโค้ด C#  

---

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ  

- [รับตัวคั่นสไตล์ย่อหน้าในเอกสาร Word](/words/english/net/document-formatting/get-paragraph-style-separator/)  
- [สร้างเอกสาร Word พร้อมส่วนหัวและส่วนท้ายโดยใช้ Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)  
- [เพิ่มเลขหน้าในส่วนท้ายของเอกสาร Word โดยใช้ Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}