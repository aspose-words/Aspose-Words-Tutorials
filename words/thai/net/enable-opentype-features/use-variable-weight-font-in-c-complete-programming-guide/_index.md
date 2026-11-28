---
category: general
date: 2026-06-02
description: เรียนรู้วิธีใช้ฟอนต์น้ำหนักแปรผันใน C# และตั้งค่าน้ำหนักฟอนต์โดยโปรแกรมเมติกพร้อมเปลี่ยนโค้ดการยืดฟอนต์เพื่อการพิมพ์แบบไดนามิก
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: th
og_description: ใช้ฟอนต์แบบน้ำหนักแปรผันใน C# เพื่อกำหนดน้ำหนักฟอนต์โดยโปรแกรมและเปลี่ยนโค้ดการยืดฟอนต์
  ทำให้การพิมพ์แบบไดนามิกในเอกสารของคุณเป็นไปได้
og_title: ใช้ฟอนต์น้ำหนักแปรผันใน C# – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: ใช้ฟอนต์น้ำหนักแปรผันใน C# – คู่มือการเขียนโปรแกรมครบถ้วน
url: /th/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ใช้ฟอนต์น้ำหนักแปรผันใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์

เคยต้องการ **ใช้ฟอนต์น้ำหนักแปรผัน** ในโครงการ .NET แต่ไม่แน่ใจว่าจะทำให้ค่าน้ำหนักและการยืดขยายตอบสนองต่อการป้อนข้อมูลของผู้ใช้ได้อย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายสถานการณ์ UI หรือการรายงาน คุณอาจต้องการให้ข้อความปรับตัว—เช่นหัวเรื่องที่เบาแล้วกลายเป็นหนาเมื่อเมาส์ชี้, หรือย่อหน้าที่ขยายความกว้างเพื่อเน้นความสำคัญ ข่าวดีคือด้วย Aspose.Words คุณสามารถ **ตั้งค่าน้ำหนักฟอนต์โดยโปรแกรม** และแม้กระทั่ง **เปลี่ยนโค้ดการยืดขยายฟอนต์** ได้แบบเรียลไทม์

ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างเชิงปฏิบัติที่แสดงอย่างชัดเจนว่าจะแนบฟอนต์น้ำหนักแปรผัน, ใช้น้ำหนักที่กำหนดเอง, และปรับการตั้งค่าการยืดขยายอย่างไร—ทั้งหมดด้วยโค้ด C# ที่คัดลอก‑วางได้ง่าย ๆ เมื่อทำครบแล้วคุณจะได้แอปคอนโซลที่รันได้และสร้าง PDF แสดงผลลัพธ์

---

## สิ่งที่คุณต้องการ

- **Aspose.Words for .NET** (v23.12 หรือใหม่กว่า) ไลบรารีมาพร้อมการสนับสนุนเต็มรูปแบบสำหรับฟอนต์น้ำหนักแปรผัน
- โฟลเดอร์ที่มีไฟล์ฟอนต์น้ำหนักแปรผันอย่างน้อยหนึ่งไฟล์ เช่น *RobotoFlex‑Variable.ttf* คุณสามารถดาวน์โหลดได้จาก Google Fonts
- .NET 6 SDK (หรือเวอร์ชัน .NET ล่าสุดใดก็ได้) และ IDE ที่คุณชอบ
- ความรู้พื้นฐานของ C#—ไม่มีอะไรซับซ้อน เพียงไม่กี่บรรทัดของโค้ด

เท่านี้เอง ไม่ต้องมีแพ็กเกจ NuGet เพิ่มเติมนอกจาก Aspose.Words และไม่มีไฟล์การกำหนดค่าที่ซับซ้อน

![Use variable weight font example](https://example.com/variable-weight-sample.png "Use variable weight font demonstration")

ข้อความแทนภาพ: ภาพหน้าจอที่แสดงการใช้ฟอนต์น้ำหนักแปรผันในเอกสาร PDF ที่สร้างขึ้น

---

## ขั้นตอนที่ 1: ตั้งค่า FontSettings และชี้ไปยังโฟลเดอร์ฟอนต์ของคุณ  

ก่อนอื่น—Aspose.Words ต้องรู้ว่าฟอนต์น้ำหนักแปรผันของคุณอยู่ที่ไหน คุณทำได้โดยสร้างอ็อบเจ็กต์ `FontSettings` แล้วแนบ `FolderFontSource` ธง `true` บอกให้เครื่องมือค้นหาไดเรกทอรีย่อยด้วย ซึ่งสะดวกถ้าคุณเก็บหลายครอบครัวฟอนต์ไว้ด้วยกัน

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**ทำไมขั้นตอนนี้สำคัญ:** หากไม่ได้ลงทะเบียนโฟลเดอร์ Aspose.Words จะย้อนกลับไปใช้ฟอนต์ระบบและจะละเลยข้อมูลน้ำหนักแปรผันที่ฝังอยู่ในไฟล์ฟอนต์ของคุณ ขั้นตอนนี้เป็นพื้นฐานสำหรับทุกอย่างที่ตามมา

---

## ขั้นตอนที่ 2: แนบ FontSettings ไปยัง Document  

ต่อไปเราจะสร้าง `Document` ใหม่ (หรือโหลดที่มีอยู่) แล้วบอกให้ใช้ `FontSettings` ที่เตรียมไว้ การผูกนี้ทำให้ข้อมูลน้ำหนักแปรผันพร้อมใช้งานกับทุก `Run` ที่เราจะเพิ่มต่อไป

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

ถ้าคุณมีเทมเพลตอยู่แล้ว—เช่นไฟล์ Word ที่มีตัวแปรที่ต้องแทนที่—คุณสามารถเปลี่ยน `new Document()` เป็น `new Document("Template.docx")` ได้ `FontSettings` เดิมจะยังคงใช้ได้

---

## ขั้นตอนที่ 3: เพิ่ม Run ของข้อความที่จะใช้ฟอนต์น้ำหนักแปรผัน  

**Run** คือหน่วยย่อยที่สุดของการจัดรูปแบบข้อความใน Aspose.Words เราจะสร้างหนึ่งอัน, แทรกลงในย่อหน้าที่ใหม่, แล้วต่อมาจะเปลี่ยนแอตทริบิวต์ฟอนต์ของมัน

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

ในขั้นตอนนี้ข้อความจะถูกเรนเดอร์ด้วยฟอนต์เริ่มต้น (โดยทั่วไปคือ Times New Roman) เวทมนต์จะเกิดขึ้นเมื่อเรากำหนดครอบครัวฟอนต์น้ำหนักแปรผัน

---

## ขั้นตอนที่ 4: เลือกฟอนต์ครอบครัวน้ำหนักแปรผัน  

นี่คือจุดที่เราจริง ๆ **ใช้ฟอนต์น้ำหนักแปรผัน** ตั้งค่า `Font.Name` ให้ตรงกับชื่อครอบครัวที่กำหนดในไฟล์ฟอนต์แปรผัน สำหรับ Roboto Flex ชื่อคือ `"Roboto Flex"`

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

หากคุณไม่แน่ใจชื่อครอบครัว ให้เปิดไฟล์ `.ttf` ด้วยโปรแกรมดูฟอนต์หรือใช้เมธอด `fontSettings.GetFonts()` เพื่อแสดงรายการครอบครัวที่พบ

---

## ขั้นตอนที่ 5: ตั้งค่าน้ำหนักและการยืดขยายฟอนต์โดยโปรแกรม  

ตอนนี้เป็นหัวใจของบทแนะนำ: เรา **ตั้งค่าน้ำหนักฟอนต์โดยโปรแกรม** และ **เปลี่ยนโค้ดการยืดขยายฟอนต์** ทั้งสองคุณสมบัติกำหนดค่าเป็นจำนวนเต็มที่สอดคล้องกับสเปค OpenType

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). เลือกค่าที่ฟอนต์แปรผันรองรับ  
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). ค่าเริ่มต้นคือ 100 (Normal)

> **เคล็ดลับ:** ฟอนต์แปรผันทุกตัวไม่ได้เปิดเผยช่วงเต็ม หากคุณตั้งค่าที่ไม่รองรับ เครื่องมือจะปรับให้เป็นค่าน้ำหนักหรือการยืดขยายที่ใกล้ที่สุดที่มีอยู่

---

## ขั้นตอนที่ 6: บันทึกเอกสารและตรวจสอบผลลัพธ์  

สุดท้ายให้เขียนเอกสารออกเป็น PDF (หรือ DOCX) แล้วเปิดดูเพื่อดูผลลัพธ์ PDF เป็นรูปแบบที่ดีสำหรับการตรวจสอบภาพ เนื่องจากการเรนเดอร์สม่ำเสมอข้ามแพลตฟอร์ม

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

เมื่อคุณเปิด *VariableWeightDemo.pdf* คุณควรเห็นวลี “Variable‑weight text demo” แสดงด้วยสไตล์เบาและขยายเล็กน้อยของ Roboto Flex เปลี่ยน `FontWeight` เป็น `700` และ `FontStretch` เป็น `80` แล้วรันใหม่—สังเกตว่าข้อความกลายเป็นหนาและกระชับมากขึ้น

---

## คำถามทั่วไป & กรณีขอบ

### ถ้าฟอนต์ไม่ปรากฏเลย?

- **Missing FontSettings**: ตรวจสอบให้แน่ใจว่า `doc.FontSettings = fontSettings;` ถูกเรียก **ก่อน** เพิ่มข้อความใด ๆ  
- **Incorrect family name**: ใช้ `fontSettings.GetFonts()` เพื่อแสดงรายการครอบครัวทั้งหมด; คัดลอกสตริงที่ตรงกันอย่างแม่นยำ  
- **Unsupported weight/stretch**: ฟอนต์แปรผันบางตัวรองรับช่วงน้ำหนัก 100‑900 เพียงบางส่วน ใช้ `run.Font.FontWeight = 400;` เป็นค่าปลอดภัย

### ฉันสามารถเปลี่ยนค่าน้ำหนักหลังจากบันทึกเอกสารได้หรือไม่?

ได้. อ็อบเจ็กต์ `Run` สามารถแก้ไขได้ ดังนั้นคุณสามารถปรับ `FontWeight` หรือ `FontStretch` ได้ทุกจุดก่อน `Save` สุดท้าย หากต้องการสลับน้ำหนักแบบไดนามิก (เช่นตามการโต้ตอบของผู้ใช้) ให้พิจารณาสร้าง Run แยกสำหรับแต่ละสถานะ

### ฟังก์ชันนี้ทำงานกับการส่งออกเป็น DOCX หรือไม่?

แน่นอน. ข้อมูลเมตาดาต้าน้ำหนักแปรผันจะถูกเก็บใน OpenXML ด้านล่างและเวอร์ชัน Word สมัยใหม่สามารถตีความได้ อย่างไรก็ตาม Word รุ่นเก่าอาจละเลยการตั้งค่าการยืดขยาย

---

## ตัวอย่างการทำงานเต็มรูปแบบ  

ด้านล่างเป็นโปรแกรมคอนโซลที่สมบูรณ์ คุณสามารถคอมไพล์และรันได้ทันที รวมถึง `using` directives ที่จำเป็น, การจัดการข้อผิดพลาด, และคอมเมนต์

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** คอนโซลจะแสดงเส้นทางการบันทึก และ PDF ที่สร้างขึ้นจะแสดงข้อความในสไตล์เบาและขยาย—ตรงกับที่เราตั้งค่าไว้

---

## สรุป  

เราได้อธิบายวิธี **ใช้ฟอนต์น้ำหนักแปรผัน** ใน C# ด้วย Aspose.Words, แสดงวิธี **ตั้งค่าน้ำหนักฟอนต์โดยโปรแกรม**, และให้โค้ด **เปลี่ยนการยืดขยายฟอนต์** ที่จำเป็นเพื่อขยายหรือบีบอักษร ขั้นตอนง่าย ๆ คือ: ตั้งค่า `FontSettings`, แนบให้กับ `Document`, สร้าง `Run`, เลือกครอบครัวฟอนต์แปรผัน, แล้วปรับ `FontWeight` และ `FontStretch` ตามต้องการ

---

## สิ่งต่อไปที่ควรทำ  

- **การผสาน UI แบบไดนามิก**: นำตรรกะเดียวกันไปใช้ในแอป WinForms หรือ WPF เพื่อให้ผู้ใช้เลือกน้ำหนัก/การยืดขยายด้วยสไลเดอร์  
- **หลาย Run**: ผสานหลาย Run ที่มีน้ำหนักต่างกันในย่อหน้าเดียวเพื่อสร้างลำดับชั้นการพิมพ์ที่หลากหลาย  
- **แกนขั้นสูง**: ฟอนต์แปรผันบางตัวมีแกนเพิ่มเติม (เช่น slant, optical size) ใช้ `run.Font.FontStyle` หรือสำรวจ `FontVariationSettings` เพื่อควบคุมละเอียดยิ่งขึ้น  
- **เคล็ดลับประสิทธิภาพ**: แคชอ็อบเจ็กต์ `FontSettings` เมื่อประมวลผลหลายเอกสารเพื่อหลีกเลี่ยงการสแกนโฟลเดอร์ซ้ำ ๆ  

ลองเปลี่ยน *Roboto Flex* เป็น *Inter Variable* หรือฟอนต์ OpenType แปรผันอื่น ๆ แล้วดูว่าเอกสารของคุณได้รับความยืดหยุ่นด้านภาพใหม่ระดับไหน ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอน‑ต่อ‑ขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [ใช้ฟอนต์จากเครื่องเป้าหมาย](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [ใช้ฟอนต์จากเครื่องเป้าหมาย](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [ใช้ฟอนต์จากเครื่องเป้าหมาย](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}