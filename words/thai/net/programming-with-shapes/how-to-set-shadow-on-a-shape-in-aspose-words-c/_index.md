---
category: general
date: 2026-04-02
description: เรียนรู้วิธีตั้งค่าเงาบนรูปทรงใน Aspose.Words ด้วย C# เราจะสาธิตวิธีเพิ่มเงาให้กับรูปทรง
  ปรับค่าความเบลอ ปรับแต่งเงา และบันทึกเอกสารพร้อมเงา
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to adjust blur
- how to customize shadow
- save document with shadow
language: th
og_description: วิธีตั้งเงาบนรูปร่างใน Aspose.Words ด้วย C# ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนเพื่อเพิ่มเงาให้กับรูปร่าง
  ปรับความเบลอ ปรับแต่งเงา และบันทึกเอกสารพร้อมเงา
og_title: วิธีตั้งเงาบนรูปร่างใน Aspose.Words (C#)
tags:
- Aspose.Words
- C#
- Document Automation
title: วิธีตั้งเงาบนรูปร่างใน Aspose.Words (C#)
url: /th/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งเงาบนรูปร่างใน Aspose.Words (C#)

เคยสงสัย **how to set shadow** บนรูปร่างเพื่อให้เอกสาร Word ของคุณดูเป็นมืออาชีพขึ้นบ้างไหม? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักถามวิธีเพิ่ม drop‑shadow ที่ละเอียดอ่อนซึ่งทำให้แผนภูมิเด่นขึ้นโดยไม่ทำลายการจัดวาง. ในบทเรียนนี้เราจะพาคุณผ่านขั้นตอนที่แม่นยำเพื่อ **how to set shadow** บนรูปร่างโดยใช้ Aspose.Words for .NET, และระหว่างทางเราจะครอบคลุม **add shadow to shape**, **how to adjust blur**, **how to customize shadow**, และสุดท้าย **save document with shadow**.

เราจะเริ่มด้วยข้อกำหนดเบื้องต้น, จากนั้นเจาะลึกแต่ละคุณสมบัติของคลาส `ShadowFormat`, และสรุปด้วยตัวอย่างที่ทำงานได้เต็มรูปแบบที่คุณสามารถคัดลอก‑วางลงใน Visual Studio. เมื่อจบคุณจะเข้าใจว่าทำไมแต่ละการตั้งค่าถึงสำคัญ, มีกรณีขอบเขตอะไรที่ควรระวัง, และวิธีตรวจสอบว่าเงานั้นทำให้รูปร่างดูดีขึ้นจริงหรือไม่.

---

## สิ่งที่คุณต้องการ

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ เวลาที่เขียน, 23.12). คุณสามารถรับได้ผ่าน NuGet: `Install-Package Aspose.Words`.
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio 2022 หรือ VS Code พร้อมส่วนขยาย C# ทำงานได้ดี)
- ไฟล์ DOCX ที่มีรูปร่างอย่างน้อยหนึ่งรูป (สี่เหลี่ยม, รูปภาพ, หรือ SmartArt). หากไม่มีไฟล์ดังกล่าว, สร้างไฟล์ Word อย่างเร็วและแทรกรูปร่างใดก็ได้—Aspose.Words จะอ่านได้เช่นเดียวกัน

ไม่มีไลบรารีของบุคคลที่สามอื่น ๆ ที่จำเป็น; ทุกอย่างอยู่ในเนมสเปซ `Aspose.Words`.

---

## วิธีตั้งเงาบนรูปร่าง

### Step 1 – Load the Document and Grab the Target Shape

ก่อนอื่นเราจะเปิดไฟล์ต้นฉบับและดึงรูปร่างแรกที่ต้องการจัดรูปแบบ. นี่เป็นรูปแบบเดียวกับที่คุณใช้สำหรับการจัดการรูปร่างใด ๆ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// The GetChild method walks the node tree recursively.
Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> `GetChild` กับ `true` ทำให้เราค้นหาทั้งต้นไม้ของเอกสาร, ดังนั้นแม้รูปร่างจะอยู่ในส่วนหัว, ส่วนท้าย, หรือกล่องข้อความ เราก็ยังพบได้. การข้ามขั้นตอนนี้จะทำให้คุณได้อ้างอิง `null` และเกิด `NullReferenceException`.

### Step 2 – Access the ShadowFormat Object

ทุก `Shape` มีคุณสมบัติ `ShadowFormat` ที่รวมการตั้งค่าที่เกี่ยวกับเงาทั้งหมด. คิดว่าเป็น “กล่องเครื่องมือเงา”.

```csharp
// Grab the ShadowFormat – this is where we configure colour, distance, blur, etc.
ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Pro tip:** หากรูปร่างมีเงาอยู่แล้ว, `ShadowFormat` จะมีค่าที่มีอยู่. คุณสามารถอ่านค่าก่อนเขียนทับได้หากต้องการเก็บค่าเริ่มต้นบางอย่างไว้.

### Step 3 – Add Shadow to Shape: Choose Colour and Distance

ตอนนี้เราจริง ๆ **add shadow to shape** โดยกำหนดสีและระยะการเลื่อน. สีถูกกำหนดด้วย ARGB ทำให้คุณควบคุมความโปร่งใสได้โดยตรง.

```csharp
// Semi‑transparent purple (alpha 128, red 0, green 0, blue 128)
shadow.Color = Color.FromArgb(128, 0, 0, 128);

// Distance from the shape to the shadow, measured in points.
shadow.Distance = 5.0;   // 5 points ≈ 1.75 mm
```

> **Why colour matters:** ช่องแอลฟา (ตัวเลขแรก) กำหนดความโปร่งใสของเงา. เงาแบบทึบเต็ม (alpha 255) อาจดูแข็งกระด้าง, ในขณะที่ค่าแอลฟาต่ำจะให้ผลลัพธ์ที่นุ่มนวลและเป็นธรรมชาติมากขึ้น.

### Step 4 – How to Adjust Blur for a Realistic Effect

เงาที่คมชัดและขอบแข็งมักไม่ดูดีในเอกสารธุรกิจ. ใช้คุณสมบัติ `BlurRadius` เพื่อทำให้ขอบนุ่มขึ้น.

```csharp
// Blur radius in points – larger values create a softer edge.
shadow.BlurRadius = 3.0;
```

> **Common mistake:** ตั้งค่า `BlurRadius` เป็น `0` จะทำให้เงาขรุขระและอาจทำลายการไหลของภาพในรายงาน. ค่าอยู่ระหว่าง `2` ถึง `5` ทำงานได้ดีสำหรับเอกสารที่ดูบนหน้าจอส่วนใหญ่.

### Step 5 – How to Customize Shadow Transparency and Style

นอกจากสีและการเบลอ, คุณยังสามารถปรับความโปร่งใสโดยรวมของเงาได้. ค่านี้แยกจากแอลฟาของสี.

```csharp
// Overall transparency (0 = opaque, 1 = fully transparent)
shadow.Transparency = 0.3;   // 30 % transparent
```

> **Edge case:** หากคุณตั้งค่าแอลฟาของสีและ `Transparency` ทั้งสองเป็นค่าสูง, เงาอาจกลายเป็นมองไม่เห็น. ทดสอบด้วยการพรีวิวเพื่อให้แน่ใจว่ามันยังเห็นได้.

### Step 6 – Save Document with Shadow

สุดท้ายบันทึกการเปลี่ยนแปลง. ขั้นตอนนี้แสดง **save document with shadow** เพื่อให้คุณเปิดไฟล์ใน Word และเห็นผลลัพธ์.

```csharp
// Save the updated document. Overwrite or use a new file name as you prefer.
doc.Save("YOUR_DIRECTORY/output.docx");
```

> **Verification tip:** เปิด `output.docx` ใน Microsoft Word, เลือกรูปร่าง, แล้วดูเมนูดรอปดาวน์ “Shadow” ใต้ “Shape Format”. คุณควรเห็นสี, ระยะ, เบลอ, และความโปร่งใสที่คุณตั้งค่าไว้.

---

## เพิ่มเงาให้รูปร่าง – การเลือกสีและระยะที่เหมาะสม

เมื่อคุณ **add shadow to shape**, ผลกระทบด้านภาพขึ้นอยู่กับความแตกต่างของสีกับพื้นหลังของหน้าอย่างมาก. เงาสีเข้มบนหน้ากระดาษสีอ่อนให้ความรู้สึกเป็นธรรมชาติ, ในขณะที่สีสว่างสามารถใช้เพื่อสร้างเอฟเฟกต์ศิลปะได้.

- **Dark grey (เช่น #808080)** ทำงานได้ดีสำหรับรายงานอย่างเป็นทางการ.  
- **Accent colours** (เช่นสีม่วงกึ่งโปร่งใสที่เราใช้) สามารถเน้นกล่องอธิบายในสื่อการตลาด

คุณยังสามารถเปลี่ยนคุณสมบัติ `ShadowFormat.Angle` เพื่อหมุนทิศทางของเงา, แต่ค่าเริ่มต้น (45°) มักให้การเลื่อนแบบทแยงมุมที่น่าพอใจ.

```csharp
shadow.Angle = 45.0;   // Default angle – feel free to experiment
```

---

## วิธีปรับ Blur สำหรับสื่อผลลัพธ์ที่แตกต่าง

หากเอกสารของคุณจะพิมพ์, คุณอาจต้องการเบลอที่ค่อนข้างคมขึ้นเนื่องจากเครื่องพิมพ์ความละเอียดสูงสามารถเรนเดอร์ไล่สีละเอียดได้. ในทางกลับกัน, สำหรับ PDF ที่ดูบนหน้าจอเท่านั้น, การเบลอที่ใหญ่ขึ้นช่วยหลีกเลี่ยงขอบขรุขระบนจอแสดงผล DPI ต่ำ.

```csharp
// Example: tighter blur for print
if (doc.PageCount > 0 && doc.FirstSection.PageSetup.PaperSize == PaperSize.A4)
{
    shadow.BlurRadius = 2.0;   // Slightly sharper for print
}
else
{
    shadow.BlurRadius = 4.0;   // Softer for screen
}
```

> **Why this conditional helps:** มันแสดง **how to adjust blur** ตามการตรวจสอบเงื่อนไขแบบเรียบง่ายใน runtime, แสดงให้คุณเห็นว่าคุณสามารถทำให้เงาตอบสนองต่อสื่อที่ใช้งานสุดท้ายได้อย่างไร.

---

## วิธีปรับความโปร่งใสและสีของเงาแบบไดนามิก

บางครั้งคุณต้องสร้างเอกสารตามแนวทางแบรนด์ที่แตกต่างกัน. เราจะทำให้สีและความโปร่งใสของเงาสามารถกำหนดค่าได้ผ่านพารามิเตอร์ของเมธอด.

```csharp
void ApplyCustomShadow(Shape shape, Color colour, double distance, double blur, double transparency)
{
    ShadowFormat sf = shape.ShadowFormat;
    sf.Color = colour;
    sf.Distance = distance;
    sf.BlurRadius = blur;
    sf.Transparency = transparency;
}
```

คุณสามารถเรียกใช้ได้ดังนี้:

```csharp
ApplyCustomShadow(targetShape, Color.FromArgb(200, 255, 0, 0), 4.0, 2.5, 0.2);
```

> **Real‑world use case:** ทีมการตลาดมักขอเงาสีแดงเฉพาะแบรนด์บนโบรชัวร์โปรโมชั่น. เมธอดช่วยเหลือนี้ทำให้คุณตอบสนองคำขอนั้นได้โดยไม่ต้องเขียนโค้ดหลักใหม่.

---

## บันทึกเอกสารพร้อมเงา – การบันทึกการเปลี่ยนแปลงของคุณ

คำถามที่พบบ่อยคือเงาจะคงอยู่หรือไม่เมื่อแปลงเอกสารเป็น PDF. คำตอบคือ **yes**, ตราบใดที่คุณใช้ `PdfSaveOptions` ที่รักษาวัตถุการวาดไว้.

```csharp
PdfSaveOptions pdfOpts = new PdfSaveOptions
{
    // Ensure all drawing effects, including shadows, are retained.
    EmbedFullFonts = true,
    Compliance = PdfCompliance.PdfA2b
};

doc.Save("YOUR_DIRECTORY/output.pdf", pdfOpts);
```

ตอนนี้คุณมีทั้งไฟล์ DOCX และ PDF ที่เงาของรูปร่างดูเหมือนกัน.

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่พร้อมคัดลอก‑วางครบชุดที่เชื่อมทุกส่วนเข้าด้วยกัน. แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงบนเครื่องของคุณ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (you could loop over all shapes if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Access the shadow format.
        ShadowFormat shadow = shape.ShadowFormat;

        // 4️⃣ Set colour, distance, blur and transparency.
        shadow.Color = Color.FromArgb(128, 0, 0, 128); // semi‑transparent purple
        shadow.Distance = 5.0;                        // offset in points
        shadow.BlurRadius = 3.0;                      // soft edge
        shadow.Transparency = 0.3;                    // 30 % transparent

        // Optional: tweak angle for a different light source.
        shadow.Angle = 45.0;

        // 5️⃣ Save the DOCX – this demonstrates save document with shadow.
        doc.Save("YOUR_DIRECTORY/output.docx");

        // 6️⃣ Also export to PDF to prove the shadow carries over.
        PdfSaveOptions pdfOpts = new PdfSaveOptions

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}