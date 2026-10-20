---
category: general
date: 2026-08-04
description: เปลี่ยนตัวคั่นเชิงอรรถใน C# ด้วย Aspose.Words – เรียนรู้วิธีแก้ไขตัวคั่นเชิงอรรถและเปลี่ยนตัวคั่นเชิงอรรถท้ายในเอกสาร
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: th
lastmod: 2026-08-04
og_description: เปลี่ยนตัวคั่นเชิงอรรถใน C# ด้วย Aspose.Words คู่มือนี้จะแสดงวิธีแก้ไขตัวคั่นเชิงอรรถ
  ปรับแต่งตัวคั่นบันทึกเชิงอรรถ และบันทึกเอกสารที่อัปเดต
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: เปลี่ยนตัวคั่นเชิงอรรถใน C# – คู่มือ Aspose.Words ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: เปลี่ยนตัวคั่นเชิงอรรถใน C# โดยใช้ Aspose.Words
url: /th/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปลี่ยนตัวคั่นเชิงอรรถใน C# ด้วย Aspose.Words

หากคุณต้องการ **เปลี่ยนตัวคั่นเชิงอรรถ** ในเอกสาร Word, บทแนะนำนี้จะพาคุณผ่านขั้นตอนที่แม่นยำด้วย Aspose.Words สำหรับ .NET ไม่ว่าคุณจะต้องการแทนที่เส้นเริ่มต้นด้วยสัญลักษณ์, หรือใช้สไตล์ที่แตกต่างสำหรับตัวคั่นเชิงอรรถท้าย, โค้ดด้านล่างครอบคลุมกระบวนการทั้งหมด

คุณจะได้เรียนรู้วิธี **แก้ไขตัวคั่นเชิงอรรถ** และการดำเนินการ **เปลี่ยนตัวคั่นเชิงอรรถท้าย** ที่เกี่ยวข้อง, เพื่อให้เอกสารเดียวกันมีสไตล์ที่สอดคล้องกันสำหรับเชิงอรรถและเชิงอรรถท้าย ไม่ต้องใช้เครื่องมือภายนอก—เพียงไม่กี่บรรทัดของ C# เท่านั้น

## สิ่งที่คุณจะได้ทำ

โดยตอนจบของคู่มือนี้คุณจะสามารถ:

* โหลดไฟล์ *.docx* ที่มีเชิงอรรถและเชิงอรรถท้ายอยู่แล้ว  
* เข้าถึงโหนดตัวคั่นสำหรับเชิงอรรถ, การต่อเนื่องของเชิงอรรถ, และเชิงอรรถท้าย  
* แทนที่อักขระตัวคั่น (เช่น เปลี่ยนเส้นเริ่มต้นเป็นเครื่องหมายดอกจัน)  
* บันทึกเอกสารที่แก้ไขแล้วโดยไม่สูญเสียเนื้อหาอื่นใด  

บทแนะนำนี้สมมติว่าคุณมีความเข้าใจพื้นฐานของ C# และได้ติดตั้งแพคเกจ **Aspose.Words** NuGet (เวอร์ชัน 24.9 หรือใหม่กว่า)  

---

## ข้อกำหนดเบื้องต้น

| ข้อกำหนด | เหตุผล |
|-------------|--------|
| .NET 6.0+ หรือ .NET Framework 4.7.2+ | จำเป็นต้องใช้รันไทม์สำหรับ Aspose.Words |
| Aspose.Words for .NET library | ให้ API `Document` และ `FootnoteOptions` |
| ไฟล์ Word เข้า (`input.docx`) ที่มีอย่างน้อยหนึ่งเชิงอรรถหรือเชิงอรรถท้าย | แสดงการเปลี่ยนตัวคั่น |

คุณสามารถเพิ่ม Aspose.Words ลงในโปรเจกต์ของคุณด้วยคำสั่ง CLI ต่อไปนี้:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## ขั้นตอนที่ 1: โหลดเอกสารที่มีเชิงอรรถ

การดำเนินการแรกคือการอ่านไฟล์ต้นทางเข้าสู่วัตถุ `Document` วัตถุนี้เป็นตัวแทนของไฟล์ Word ทั้งหมดในหน่วยความจำและให้คุณเข้าถึงโหนดทั้งหมดของมัน

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**ทำไมเรื่องนี้สำคัญ:** การโหลดเอกสารเป็นจุดเริ่มต้นของการปรับแต่งใด ๆ หากไฟล์ไม่พบ Aspose.Words จะโยน `FileNotFoundException`, ดังนั้นให้ตรวจสอบเส้นทางให้ถูกต้องก่อนดำเนินการต่อ

---

## ขั้นตอนที่ 2: เข้าถึงโหนดตัวคั่นของเชิงอรรถและเชิงอรรถท้าย

`Document.FootnoteOptions` เปิดเผยโหนดตัวคั่นสามประเภท:

* `Separator` – เส้นที่ปรากฏหลังชุดเชิงอรรถในหน้าที่หนึ่ง  
* `ContinuationSeparator` – เส้นที่ใช้เมื่อเชิงอรรถต่อเนื่องไปยังหน้าถัดไป  
* `EndnoteSeparator` – เส้นที่แยกข้อความหลักจากรายการเชิงอรรถท้าย  

คุณจะดึงโหนดเหล่านี้เป็นอ็อบเจ็กต์ `Node` ทั่วไป, แล้วแคสต์เป็น `Run` เพื่อแก้ไขข้อความ

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**ทำไมเรื่องนี้สำคัญ:** โหนดเหล่านี้เป็นที่เดียวที่อักขระตัวคั่นที่มองเห็นได้ถูกเก็บไว้ การเปลี่ยนโหนดอื่น (เช่น ย่อหน้าปกติ) จะไม่ส่งผลต่อการจัดรูปแบบของเชิงอรรถ

---

## ขั้นตอนที่ 3: เปลี่ยนอักขระตัวคั่นของเชิงอรรถ

ความต้องการที่พบบ่อยที่สุดคือการแทนที่เส้นเริ่มต้นด้วยสัญลักษณ์เช่นเครื่องหมายดอกจัน (`*`). เนื่องจากตัวคั่นถูกเก็บเป็น `Run`, คุณจึงสามารถแก้ไขคุณสมบัติ `Text` ได้อย่างปลอดภัย

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**ทำไมเรื่องนี้สำคัญ:** การแก้ไข `Run.Text` โดยตรงจะอัปเดตการแสดงผลในเอกสารสุดท้ายโดยไม่กระทบเนื้อหาเชิงอรรถอื่น ๆ รูปแบบเดียวกันสามารถใช้กับสตริงใดก็ได้ รวมถึงสัญลักษณ์ Unicode

---

## ขั้นตอนที่ 4: เปลี่ยนตัวคั่นเชิงอรรถท้าย (ไม่บังคับ)

หากคุณต้องการ **เปลี่ยนตัวคั่นเชิงอรรถท้าย** ด้วย, กระบวนการจะคล้ายกับการเปลี่ยนเชิงอรรถ เพียงแทนที่ข้อความของ `endnoteSeparator` ด้วยอักขระที่คุณต้องการ

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**ทำไมเรื่องนี้สำคัญ:** เชิงอรรถท้ายมักมีสไตล์ที่แตกต่างจากเชิงอรรถ การให้ตัวคั่นแยกต่างหากช่วยให้คุณรักษาความสอดคล้องตามแนวทางการออกแบบของเอกสารได้

---

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากทำการปรับเปลี่ยนทั้งหมดแล้ว ให้บันทึกการเปลี่ยนแปลงโดยใช้ `Document.Save`. คุณสามารถเขียนทับไฟล์เดิมหรือบันทึกไปยังตำแหน่งใหม่ได้

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**ทำไมเรื่องนี้สำคัญ:** `Save` จะเขียนข้อมูลในหน่วยความจำลงดิสก์, รักษาองค์ประกอบอื่น ๆ (สไตล์, รูปภาพ, ตาราง) ไว้โดยไม่เปลี่ยนแปลง

---

## ตัวอย่างเต็มที่สามารถรันได้

รวมทุกส่วนเข้าด้วยกัน, นี่คือตัวอย่างแอปพลิเคชันคอนโซลที่แสดงกระบวนการทั้งหมด:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด *ModifiedSeparators.docx* ด้วย Microsoft Word. เส้นตัวคั่นของเชิงอรรถที่ด้านล่างของหน้าที่หนึ่งจะกลายเป็นดอกจัน (`*`). หากเอกสารมีเชิงอรรถท้าย, เส้นที่แยกข้อความหลักจากรายการเชิงอรรถท้ายจะปรากฏเป็นเครื่องหมายขีด (`-`). เนื้อหาอื่น ๆ (ข้อความ, รูปภาพ, ตาราง) จะไม่ถูกแก้ไข

---

## คำถามทั่วไป & การจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าเอกสารไม่มีเชิงอรรถ?** | `FootnoteOptions.Separator` ยังคืนค่าโหนด `Run` อยู่, แต่ข้อความอาจว่างเปล่า โค้ดจะตรวจสอบประเภทของโหนดอย่างปลอดภัยก่อนทำการแก้ไข |
| **ฉันสามารถใช้สตริงหลายอักขระ (เช่น "***") ได้หรือไม่?** | ได้. คุณสมบัติ `Run.Text` ยอมรับสตริงใดก็ได้, รวมถึงอักขระ Unicode |
| **การเปลี่ยนตัวคั่นจะส่งผลต่อการนับเลขเชิงอรรถที่มีอยู่หรือไม่?** | ไม่. ตัวคั่นทำงานแยกจากระบบการนับเลข |
| **ฉันต้องทำการ dispose วัตถุ `Document` หรือไม่?** | `Document` มีการทำงาน `IDisposable` อย่างไม่ชัดเจนผ่าน `Node`. ในแอปคอนโซลสั้น ๆ สามารถละได้, แต่สำหรับบริการที่ทำงานต่อเนื่องควรใช้ `using` เพื่อจัดการทรัพยากร |
| **วิธีการทำงานนี้กับ .NET Core เทียบกับ .NET Framework เป็นอย่างไร?** | API เหมือนกันในทุก runtime; เพียงต้องใช้เวอร์ชันเฟรมเวิร์กที่รองรับโดยแพคเกจ Aspose.Words |

**เคล็ดลับ:** หากต้องการใช้ตัวคั่นที่แตกต่างสำหรับส่วนต่าง ๆ, คุณสามารถวนลูปผ่าน `doc.GetChildNodes(NodeType.Footnote, true)` และปรับคุณสมบัติ `Separator` ของแต่ละเชิงอรรถแยกกันได้ วิธีนี้ค่อนข้างขั้นสูงแต่มีประโยชน์สำหรับเอกสารที่ซับซ้อน

---

## สรุป

คุณได้เรียนรู้วิธี **เปลี่ยนตัวคั่นเชิงอรรถ** และ **เปลี่ยนตัวคั่นเชิงอรรถท้าย** ในไฟล์ Word ด้วย Aspose.Words สำหรับ C#. คู่มือนี้ครอบคลุมการโหลดเอกสาร, การเข้าถึงโหนดตัวคั่นที่เกี่ยวข้อง, การแก้ไขข้อความของมัน, และการบันทึกผลลัพธ์—ทั้งหมดในโปรแกรมเดียวที่ทำงานได้อย่างสมบูรณ์

จากนี้คุณสามารถสำรวจหัวข้อที่เกี่ยวข้องเช่น **แก้ไขสไตล์ตัวคั่นเชิงอรรถ**, การปรับแต่งการนับเลขเชิงอรรถ, หรือการใช้การจัดรูปแบบตามเงื่อนไขตามการจัดหน้า รูปแบบเดียวกัน (ดึงโหนด, แคสต์เป็น `Run`, แก้ไข `Text`) สามารถใช้ได้กับหลายสถานการณ์การประมวลผล Word อื่น ๆ

ขอให้สนุกกับการเขียนโค้ด, และอย่ากลัวที่จะทดลองใช้สัญลักษณ์ต่าง ๆ หรือแม้กระทั่งฝังรูปภาพเป็นตัวคั่นเพื่อสร้างเลย์เอาต์เอกสารที่เป็นเอกลักษณ์จริง ๆ!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [การประมวลผลคำด้วยเชิงอรรถและเชิงอรรถท้าย](/words/english/net/working-with-footnote-and-endnote/)
- [รับตัวคั่นสไตล์ย่อหน้าในเอกสาร Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [แทรกตัวคั่นสไตล์เอกสารใน Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}