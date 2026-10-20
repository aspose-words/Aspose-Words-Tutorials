---
category: general
date: 2026-03-25
description: สร้างเอกสาร PDF ด้วย C# และเรียนรู้วิธีเพิ่มรูปสี่เหลี่ยม ตั้งค่าสีเติม
  ปรับขนาดรูป และตั้งค่าความโปร่งใสของรูปในไม่กี่ขั้นตอน.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: th
og_description: สร้างเอกสาร PDF ด้วย C# และดูวิธีเพิ่มสี่เหลี่ยม ตั้งค่าสีเติม ขนาด
  และความโปร่งใสเพื่อให้ได้ผลลัพธ์ PDF ที่เรียบหรู.
og_title: สร้างเอกสาร PDF พร้อมรูปสี่เหลี่ยม – บทเรียน C#
tags:
- C#
- PDF
- Aspose.Words
title: สร้างเอกสาร PDF ด้วยรูปสี่เหลี่ยม – คู่มือ C# เต็มรูปแบบ
url: /th/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร PDF พร้อมรูปสี่เหลี่ยม – คู่มือเต็ม C# 

เคยต้องการ **สร้างเอกสาร PDF** ที่มีรูปแบบที่กำหนดเองหรือไม่ แต่ไม่แน่ใจว่าจะเริ่มจากตรงไหน? คุณไม่ได้เป็นคนเดียว ไม่ว่าคุณจะสร้างเครื่องมือสร้างรายงานหรือโบรชัวร์การตลาด การที่สามารถวาดสี่เหลี่ยมโดยโปรแกรม ตั้งค่าสีเติม ปรับขนาด และแม้แต่ปรับความโปร่งใส จะทำให้ PDF ของคุณดูเป็นมืออาชีพมากขึ้น

> **เคล็ดลับ:** วิธีเดียวกันนี้ใช้ได้กับรูปแบบอื่น (วงรี, เส้น, ฯลฯ) — เพียงเปลี่ยน `ShapeType.RECTANGLE` เป็นประเภทที่คุณต้องการ

---

## สิ่งที่คุณต้องการ

| Prerequisite | Why it matters |
|--------------|----------------|
| **.NET 6+** (or .NET Framework 4.6+) | ไลบรารี Aspose.Words รองรับ runtime สมัยใหม่ |
| **Aspose.Words for .NET** NuGet package | ให้บริการคลาส `Document`, `Shape`, `ShadowEffect` และคลาสที่เกี่ยวข้อง |
| **A C# IDE** (Visual Studio, Rider, VS Code) | ทำให้การดีบักและรันตัวอย่างเป็นเรื่องง่าย |
| **Basic C# knowledge** | คุณจะเข้าใจไวยากรณ์โดยไม่ต้องศึกษาอย่างลึกซึ้ง |

คุณสามารถติดตั้งไลบรารีผ่านบรรทัดคำสั่ง:

```bash
dotnet add package Aspose.Words
```

แค่นั้น—ไม่มี DLL เพิ่มเติม ไม่มีการพึ่งพาเนทีฟ เมื่อแพคเกจพร้อม โค้ดด้านล่างจะคอมไพล์และรันได้

---

## การดำเนินการแบบขั้นตอน

ด้านล่างเราจะแบ่งกระบวนการเป็นห้าขั้นตอนที่เป็นตรรกะ แต่ละขั้นมีหัวข้อชัดเจน (เพื่อให้โมเดล AI สามารถจัดดัชนี) และบล็อกโค้ดสั้นที่คุณสามารถคัดลอก‑วางได้โดยตรง.

### ## 1. สร้างเอกสาร PDF และเตรียมผ้าใบ

สิ่งแรกที่เราทำคือสร้างอินสแตนซ์ของ `Document` คิดว่าเป็นผ้าใบเปล่าที่ในที่สุดจะกลายเป็นไฟล์ PDF ของคุณ

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **ทำไม?** `Document` เก็บส่วนต่าง ๆ, ย่อหน้า, และรูปทรงทั้งหมด การเริ่มต้นด้วยอ็อบเจกต์ที่สะอาดช่วยรับประกันว่าจะไม่มีศิลปะที่ซ่อนอยู่จากการรันก่อนหน้า

### ## 2. เพิ่มรูปสี่เหลี่ยม – ตั้งค่าสีเติมและขนาดรูป

ตอนนี้เราจะสร้างสี่เหลี่ยม, ให้สีเติมสีเหลืองสดใส, และกำหนดมิติของมัน ซึ่งครอบคลุมทั้ง **add rectangle shape** และ **set fill color** รวมถึง **set shape size**

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

หมายเหตุ: ความกว้าง/ความสูงวัดเป็นจุด (1 point = 1/72 นิ้ว) ปรับตัวเลขเหล่านี้ให้เหมาะกับการจัดวางของคุณ

### ## 3. ใช้เงานอกและตั้งค่าความโปร่งใสของรูป

เงาช่วยเพิ่มความลึก, การควบคุมความทึบของเงาเป็นหัวใจของ **set shape transparency** ด้านล่างเราตั้งค่าเงานอกสีเทาที่มีความโปร่งใส 30 %

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

ทำไมต้องตั้งค่าความโปร่งใส? เงาโปร่งใส 30 % ให้ความละเอียดอ่อน ป้องกันไม่ให้สี่เหลี่ยมดู “แบน” บนหน้า

### ## 4. แทรกรูปเข้าไปในเนื้อหาเอกสาร

ตอนนี้เราจะวางสี่เหลี่ยมลงในย่อหน้าแรกของส่วนแรกของเอกสาร ขั้นตอนนี้ทำให้ทุกอย่างเชื่อมต่อกัน

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

กรณีขอบ: หากคุณต้องการให้รูปอยู่บนหน้ใหม่ ให้เพิ่ม `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` ก่อนการเพิ่มรูป

### ## 5. บันทึกเอกสารเป็นไฟล์ PDF

สุดท้าย เราจะบันทึกโครงสร้างในหน่วยความจำเป็นไฟล์ PDF จริง ไฟล์จะถูกเขียนไปยังโฟลเดอร์ที่คุณระบุ

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

เมื่อคุณรันโปรแกรม จะปรากฏไฟล์ชื่อ `shadow.pdf` การเปิดไฟล์จะแสดงสี่เหลี่ยมสีเหลืองพร้อมเงาสีเทานุ่มที่เลื่อนออก 4 จุด — ตรงกับที่โค้ดของเราบรรยาย

ผลลัพธ์ที่คาดหวัง: PDF หนึ่งหน้า ที่สี่เหลี่ยมอยู่ใกล้มุมบน‑ซ้ายของหน้า, เติมสีเหลือง, ขนาด 200 × 100 points, และมีเงานอกกึ่งโปร่งใส

---

## ตัวอย่างทำงานเต็ม (พร้อมคัดลอก‑วาง)

ด้านล่างเป็นไฟล์ซอร์สทั้งหมด พร้อมให้คุณวางลงในโปรเจกต์คอนโซลใหม่

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

เคล็ดลับ: แทนที่ `YOUR_DIRECTORY` ด้วยพาธแบบเต็ม เช่น `C:\Temp` หรือพาธสัมพันธ์เช่น `.\output` โปรแกรมจะสร้างโฟลเดอร์หากยังไม่มี

---

## คำถามที่พบบ่อย (FAQ)

**Q: ฉันสามารถเปลี่ยนตำแหน่งของสี่เหลี่ยมบนหน้าได้หรือไม่?**  
A: แน่นอน ตั้งค่า `rectangle.Left` และ `rectangle.Top` (ทั้งสองวัดเป็นจุด) ก่อนเพิ่มลงในย่อหน้า

**Q: ถ้าฉันต้องการสีเติมโปร่งใสแทนเงาโปร่งใสจะทำอย่างไร?**  
A: ใช้ `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – อาร์กิวเมนต์แรกคือช่องอัลฟ่า (0‑255) โดยค่า 128 ให้ความโปร่งใสประมาณ 50 %

**Q: โค้ดนี้ทำงานกับ .NET Core หรือไม่?**  
A: ใช่ Aspose.Words รองรับ .NET Standard 2.0+ ดังนั้นคุณสามารถรันโค้ดเดียวกันบน .NET 6, .NET 7 หรือ .NET Framework 4.6+ ได้

**Q: ฉันจะเพิ่มหลายรูปได้อย่างไร?**  
A: เพียงทำซ้ำขั้นตอน 2‑4 สำหรับแต่ละรูป อาจแทรกลงในย่อหน้าหรือส่วนที่ต่างกัน

---

## สรุป

เราเพิ่ง **สร้างเอกสาร PDF** ตั้งแต่ต้น, **เพิ่มรูปสี่เหลี่ยม**, **ตั้งค่าสีเติม**, **กำหนดขนาด**, และ **ปรับความโปร่งใสของรูป** เพื่อให้ได้เอฟเฟกต์เงาที่เรียบหรู ตัวอย่างโค้ดเป็นอิสระ ทำงานภายในไม่ถึงหนึ่งนาที และแสดงแนวคิดหลักที่คุณจะต้องใช้สำหรับการจัดวาง PDF ที่ซับซ้อนยิ่งขึ้น

พร้อมสำหรับความท้าทายต่อไปหรือยัง? ลองเปลี่ยนสี่เหลี่ยมเป็นรูปมุมโค้ง, ฝังภาพภายในรูป, หรือสร้างสารบัญอัตโนมัติ API เดียวกันช่วยให้คุณวางชั้นข้อความ, ภาพ, และเวกเตอร์—ไม่มีขีดจำกัด

หากคุณพบว่าคู่มือนี้มีประโยชน์ ให้กดดาวบน GitHub, แชร์ให้เพื่อนร่วมทีม, หรือแสดงความคิดเห็นพร้อมตัวอย่างของคุณเอง ขอให้เขียนโค้ดอย่างสนุก!

![สร้างเอกสาร pdf ด้วยรูปสี่เหลี่ยมตัวอย่าง](/images/rectangle-shadow.png "ภาพหน้าจอแสดง PDF ที่สร้างขึ้นพร้อมสี่เหลี่ยมสีเหลืองและเงานอกสีเทา")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}