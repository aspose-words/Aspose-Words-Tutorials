---
category: general
date: 2026-02-24
description: สร้างรูปสี่เหลี่ยมผืนผ้าใน C# ด้วย Aspose.Words, เพิ่มเงาให้รูป, แล้วบันทึกเอกสารเป็น
  PDF. เรียนรู้วิธีเพิ่มเงาและวิธีบันทึก PDF ในไม่กี่นาที.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: th
og_description: สร้างรูปสี่เหลี่ยมใน C# ด้วย Aspose.Words จากนั้นเพิ่มเงาให้รูปและบันทึกเอกสารเป็น
  PDF – คู่มือครบถ้วนแบบขั้นตอนต่อขั้นตอน
og_title: สร้างรูปสี่เหลี่ยม, เพิ่มเงา & บันทึกเป็น PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: สร้างรูปสี่เหลี่ยม, เพิ่มเงาและบันทึกเป็น PDF
url: /th/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

## Conclusion" translate.

Then final paragraph.

Make sure to keep placeholders like {{< /blocks/... >}} unchanged.

Now produce final content.

Let's translate.

I'll write Thai translation.

Be careful with punctuation.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยม, เพิ่มเงา & บันทึกเป็น PDF

เคยต้อง **สร้างรูปสี่เหลี่ยม** ในเอกสาร Word แล้วอยากได้เงาที่ดูดีและบันทึกเป็น PDF หรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการการสร้างรายงานหรือใบแจ้งหนี้ การตกแต่งด้วยเงาเล็ก ๆ ทำให้เอกสารแตกต่างจาก “แค่ไฟล์ธรรมดา” ไปเป็น “เอกสารระดับมืออาชีพ”

ในบทเรียนนี้เราจะพาคุณทำตามขั้นตอนนั้นโดยใช้ **Aspose.Words for .NET** เพื่อสร้างรูปสี่เหลี่ยม, เพิ่มเงาให้รูป, และสุดท้าย **บันทึกเอกสารเป็น PDF**. เมื่อเสร็จคุณจะได้แอปคอนโซล C# ที่พร้อมรันและสร้าง PDF ที่มีสี่เหลี่ยมสีฟ้าอ่อนพร้อมเงา, พร้อมทั้งเข้าใจวิธีปรับเงาหรือเปลี่ยนตัวเลือกการส่งออกได้

## สิ่งที่คุณต้องมี

- .NET 6 SDK (หรือเวอร์ชัน .NET ล่าสุด) – API ทำงานเช่นเดียวกันบน .NET Framework 4.x  
- Aspose.Words for .NET NuGet package (`Aspose.Words`) – ติดตั้งด้วย `dotnet add package Aspose.Words`  
- โปรแกรมแก้ไขโค้ด – Visual Studio, VS Code หรือ Rider ก็ได้  

ไม่มีขั้นตอนการขอใบอนุญาตเพิ่มเติมสำหรับตัวอย่างนี้; โหมดประเมินผลฟรีเพียงพอที่จะดูผลลัพธ์ PDF

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespace

เริ่มแรกให้สร้างโปรเจกต์คอนโซลและนำเข้าคลาสที่เราต้องใช้

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*ทำไมสิ่งนี้สำคัญ:* `Document` และ `DocumentBuilder` ให้พื้นที่ทำงาน, ส่วน `Shape` และ `ShadowFormat` ช่วยให้เราวาดและจัดรูปแบบสี่เหลี่ยมได้ การนำเข้าล่วงหน้าช่วยให้โค้ดต่อมาดูเรียบร้อย

## ขั้นตอนที่ 2: **Create rectangle shape** ด้วยขนาดที่ต้องการ

ต่อไปเราจะสร้างเอกสารเปล่าและแทรกรูปสี่เหลี่ยม. สังเกตว่าเมธอด `InsertShape` จะคืนค่าเป็นอ็อบเจกต์ `Shape` ที่เราสามารถตั้งสไตล์ได้ทันที

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*คำอธิบาย*: ขนาดระบุเป็นจุด (1 pt = 1/72 in). ปรับตัวเลขให้เหมาะกับการจัดวางของคุณ เราให้รูปสี่เหลี่ยมเติมสีฟ้าอ่อนเพื่อให้เงาเด่นชัดขึ้น

## ขั้นตอนที่ 3: **Add shadow to shape** – ปรับแต่งเอฟเฟกต์ให้ละเอียด

เงาไม่ใช่แค่เปิด/ปิด. คุณสามารถควบคุมสี, ความเบลอ, ระยะ, ทิศทาง, และความโปร่งใสได้ นี่คือการตั้งค่าที่ใช้ได้ดีสำหรับรายงานส่วนใหญ่

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*เหตุผลที่คุณอาจเปลี่ยนค่าเหล่านี้:*  
- **BlurRadius** – เพิ่มเพื่อให้เงานุ่มขึ้น, ลดเพื่อให้ขอบคมชัด  
- **Direction** – 0° ชี้ไปทางขวา, 90° ลง, 180° ซ้าย ฯลฯ ปรับให้ตรงกับการจัดหน้า  
- **Transparency** – ตั้งเป็น `0` เพื่อให้เงาเต็มสี, `0.5` สำหรับครึ่งโปร่งใส, เป็นต้น

### วิธีเพิ่มเงา – แนวทางทางเลือก

หากต้องการ **multiple‑layer shadow** (เช่น เงานอกสีเข้มและเงานในสีอ่อน) คุณสามารถสร้างรูปที่สอง, เลื่อนตำแหน่ง, แล้วตั้ง `ShadowFormat` ที่แตกต่างกันได้ หรือถ้าต้องการลุค “ไม่มีเบลอ” เพียงตั้ง `BlurRadius = 0`

## ขั้นตอนที่ 4: **Save document as PDF** – การส่งออกขั้นสุดท้าย

เมื่อสี่เหลี่ยมและเงาพร้อม, ขั้นตอนสุดท้ายคือบันทึกไฟล์เป็น PDF. Aspose.Words จัดการการแปลงภายใน; คุณแค่เรียก `Save` พร้อมระบุรูปแบบที่ต้องการ

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*เคล็ดลับ*: หากต้องการควบคุมความสอดคล้องของ PDF (PDF/A, PDF/X) หรือฝังฟอนต์, ใช้ overload:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

นี่คือส่วน **วิธีบันทึก pdf** อย่างสรุป

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอก‑วางลงใน `Program.cs`. มันคอมไพล์และรันได้ทันที (แค่ตรวจสอบให้โฟลเดอร์ปลายทางมีอยู่)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เปิดไฟล์ `ShadowRectangle.pdf` ที่สร้างขึ้น. คุณจะเห็นหน้าเดียวที่มีสี่เหลี่ยมสีฟ้าอ่อน, เงาสีเทานุ่มที่เลื่อนไป 45° ลง‑ขวา, และขอบที่คมชัด. PDF ควรเปิดได้ในโปรแกรมอ่านสมัยใหม่ใดก็ได้ (Adobe Acrobat, Edge, Chrome)

![สร้างรูปสี่เหลี่ยมพร้อมเงาใน PDF](/images/shadow-rectangle.png "สร้างรูปสี่เหลี่ยมพร้อมเงาใน PDF")

*(ข้อความ alt ของรูปรวมคีย์เวิร์ดหลักสำหรับ SEO.)*

## คำถามทั่วไป & การจัดการกรณีขอบ

**What if the shadow disappears in the PDF?**  
ตรวจสอบให้แน่ใจว่าคุณใช้ Aspose.Words เวอร์ชันล่าสุด (≥23.3). รุ่นเก่ามีบั๊กที่ทำให้บางคุณสมบัติเชิงเงาถูกละเว้นระหว่างการแปลงเป็น PDF

**Can I change the shadow colour to match my brand?**  
ได้เลย—เปลี่ยน `System.Drawing.Color.Gray` เป็น `Color` ใดก็ได้ที่คุณต้องการ, เช่น `Color.FromArgb(128, 0, 0, 255)` สำหรับสีน้ำเงินกึ่งโปร่งใส

**How do I add a shadow to other shapes (ellipse, star, etc.)?**  
`ShadowFormat` ใช้ได้กับอ็อบเจกต์ `Shape` ใดก็ได้ หลังจากสร้างรูปแล้วให้ดึง `ShadowFormat` ของมันและตั้งค่าต่าง ๆ

**What about DPI or scaling issues?**  
การเรนเดอร์ PDF เคารพขนาดจุดของรูป. หากต้องการความละเอียดสูงสำหรับการพิมพ์, ปรับขนาดรูปหรือกำหนด `PdfSaveOptions.ImageResolution`

**Can I export to other formats, like PNG?**  
ได้—แค่เรียก `document.Save("output.png", SaveFormat.Png)`. เงาจะถูกเรนเดอร์เช่นเดียวกัน

## เคล็ดลับระดับมืออาชีพ & แนวปฏิบัติที่ดีที่สุด

- **Reuse the builder**: หากต้องเพิ่มหลายรูป, ใช้ `DocumentBuilder` ตัวเดียว; จะประหยัดกว่าให้สร้างหลายตัว  
- **Batch saving**: เมื่อต้องสร้าง PDF จำนวนมากในลูป, ใช้ `PdfSaveOptions` ตัวเดียวซ้ำเพื่อหลีกเลี่ยงการจัดสรรซ้ำ ๆ  
- **Testing**: เปิด PDF หลังบันทึกทุกครั้งเพื่อยืนยันว่าเงาปรากฏตามที่คาด. โปรแกรมอ่านบางตัวอาจแสดงเงาแตกต่างกัน; Adobe Acrobat เป็นมาตรฐานที่เชื่อถือได้ที่สุด  
- **Performance**: สำหรับเอกสารขนาดใหญ่, ปิดการแบ่งหน้าอัตโนมัติของ `DocumentBuilder.InsertShape` โดยตั้ง `builder.PageSetup.DifferentFirstPageHeaderFooter = false` หากไม่ต้องการ

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **create rectangle shape**, **add shadow to shape**, และ **save document as PDF** ด้วย Aspose.Words for .NET. โค้ดกระชับ, แนวคิดอธิบายชัดเจน, และคุณมีพื้นฐานที่แข็งแรงเพื่อทดลองกับรูปแบบอื่น, สไตล์เงาต่าง ๆ, และตัวเลือกการส่งออกอื่น ๆ  

ขั้นตอนต่อไป? ลองเปลี่ยนสี่เหลี่ยมเป็นรูปแบบมุมโค้ง‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}