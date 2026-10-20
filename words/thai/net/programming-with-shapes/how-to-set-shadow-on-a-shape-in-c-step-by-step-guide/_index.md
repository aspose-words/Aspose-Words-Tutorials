---
category: general
date: 2026-03-28
description: วิธีตั้งเงาบนรูปร่างใน C# ด้วย Aspose.Words – เพิ่มเงาให้กับรูปร่าง,
  ใช้เงา, และปรับแต่งลักษณะ.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: th
og_description: วิธีตั้งเงาบนรูปร่างใน C# อย่างรวดเร็ว เรียนรู้การเพิ่มเงาให้กับรูปร่าง
  ใช้เงา และปรับความเบลอ ระยะห่าง และมุม
og_title: วิธีตั้งเงาบนรูปทรงใน C# – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: วิธีตั้งเงาบนรูปร่างใน C# – คู่มือแบบทีละขั้นตอน
url: /th/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งเงาบนรูปร่างใน C# – คู่มือการเขียนโปรแกรมอย่างครบถ้วน

เคยสงสัย **วิธีตั้งเงา** บนรูปร่างเมื่อคุณสร้างเอกสาร Word ด้วยโปรแกรมหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลาย ๆ รายงาน การนำเสนอ หรือโบรชัวร์ เงาที่เบาบางสามารถทำให้กราฟิกดูโดดเด่นโดยไม่ดูหยาบกร้าน ข่าวดีคือ? ด้วย Aspose.Words for .NET คุณสามารถเพิ่มเงาให้กับรูปร่างได้เพียงไม่กี่บรรทัดของโค้ด

ในบทเรียนนี้เราจะเดินผ่านกระบวนการทั้งหมด: โหลดไฟล์ DOCX, ดึงรูปร่างแรก, แล้ว **apply shadow to shape** — รวมถึงสี, ความเบลอ, ระยะทาง, และมุม เมื่อเสร็จคุณจะได้สคริปต์ที่พร้อมรันซึ่งสามารถนำไปใส่ในโปรเจกต์ C# ใดก็ได้ ไม่ต้องใช้ไลบรารีเพิ่มเติม ไม่ต้องมีเวทมนตร์ลับใด ๆ

## สิ่งที่คุณต้องมี

- **Aspose.Words for .NET** (เวอร์ชัน 23.9 หรือใหม่กว่า) – ไลบรารีที่ทำให้การจัดการ Word ง่ายดาย  
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio 2022, Rider, หรือ CLI)  
- ตัวอย่างไฟล์ DOCX ที่มีรูปร่างอย่างน้อยหนึ่งรูป (เช่น สี่เหลี่ยม, รูปภาพ, หรือ SmartArt)  

หากคุณขาดส่วนใดส่วนหนึ่ง ให้ติดตั้งแพคเกจ NuGet ด้วย `Install-Package Aspose.Words` และสร้างไฟล์ Word ง่าย ๆ ที่มีการแทรกรูปร่างด้วยตนเอง – เพียงเพื่อการสาธิต

## ขั้นตอนที่ 1: โหลดเอกสาร (เตรียมเพิ่มเงา)

สิ่งแรกที่ต้องทำคือเปิดไฟล์ต้นฉบับ นี่คือจุดเริ่มต้นของการ **add shadow to shape**  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **ทำไมจึงสำคัญ:** การโหลดเอกสารทำให้คุณได้อ็อบเจ็กต์ `Document` ที่เป็นเจ้าของโหนดทั้งหมดรวมถึงรูปร่าง หากไม่มีมัน จะไม่มีอะไรให้แก้ไข

## ขั้นตอนที่ 2: ดึงรูปร่างเป้าหมาย (เลือกรูปร่างที่ต้องการ)

ต่อไปเราต้องหาตำแหน่งของรูปร่างที่ต้องการจัดรูปแบบ ในตัวอย่างนี้เราจะดึงรูปร่างแรกในย่อหน้าแรก แต่คุณสามารถปรับคิวรีให้เข้ากับคอลเลกชันโหนดใดก็ได้  

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **เคล็ดลับ:** `GetChildNodes(NodeType.Shape, true)` จะเดินสำรวจ subtree อย่างเป็นขั้นเป็นตอน ทำให้คุณไม่พลาดรูปร่างที่ซ้อนอยู่เช่น WordArt

## ขั้นตอนที่ 3: เข้าถึงอ็อบเจ็กต์ Shadow Formatting (ที่ซึ่งเวทมนตร์อยู่)

ทุก `Shape` จะเปิดเผยคุณสมบัติ `ShadowFormat` อ็อบเจ็กต์นี้ควบคุมการมองเห็น, สี, ความเบลอ, ระยะทาง, และมุม – ปุ่มทั้งหมดที่คุณต้องการเพื่อ **apply shadow to shape**  

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **ทำไมต้องใช้ `ShadowFormat`:** มันเป็นชั้นนามธรรมของการแสดงผล XML ด้านล่าง ทำให้คุณปรับเงาได้โดยไม่ต้องจัดการกับ OpenXML ดิบ

## ขั้นตอนที่ 4: ทำให้เงาแสดงและเลือกสี (Add Shadow to Shape)

เงาจะไม่ปรากฏจนกว่าคุณจะตั้งค่า `Visible` เป็น `true` หลังจากนั้นคุณสามารถเลือก `System.Drawing.Color` ใดก็ได้ ที่นี่เราใช้สีเทากลาง แต่คุณสามารถทดลองสีอื่นได้ตามต้องการ  

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **ข้อผิดพลาดทั่วไป:** ลืมเปิด `Visible` จะทำให้เกิดความล้มเหลวแบบเงียบ – รูปร่างของคุณจะดูเหมือนไม่เปลี่ยนแปลงแม้ว่าคุณจะตั้งค่าคุณสมบัติอื่นแล้วก็ตาม

## ขั้นตอนที่ 5: ปรับลักษณะ – ความเบลอ, ระยะทาง, และมุม (Fine‑Tune the Look)

ตอนนี้เราจะกำหนดผลกระทบทางสายตา `BlurRadius` ทำให้ขอบเงานุ่มขึ้น, `Distance` ผลักเงาออกจากรูปร่าง, และ `Angle` กำหนดทิศทางของแหล่งแสง  

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **กรณีขอบ:** หากคุณตั้งค่าระยะทางเป็นค่าลบ เงาจะปรากฏ *ภายใน* รูปร่าง ซึ่งอาจใช้เพื่อสร้างเอฟเฟกต์แบบอิมบอสได้

## ขั้นตอนที่ 6: บันทึกเอกสารที่อัปเดต (ดูผลลัพธ์)

สุดท้ายให้เขียนการเปลี่ยนแปลงกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างไฟล์ใหม่ได้  

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

เมื่อรันโปรแกรมจะได้ไฟล์ `output-with-shadow.docx` เปิดไฟล์นี้ใน Microsoft Word คุณจะเห็นรูปร่างที่เลือกตอนนี้มีเงาเทานุ่มที่มุม 45°, เบลอ 5 pts และเลื่อน 3 pts  

![Diagram showing shadow applied to a shape](https://example.com/images/shadow-diagram.png "Diagram showing shadow applied to a shape")

*ข้อความแทนภาพ: แผนภาพแสดงการใช้เงาบนรูปร่าง* – ภาพนี้แสดงผลก่อน/หลังของเอฟเฟกต์

## วิธีเพิ่มเงา – ตัวแปรทั่วไปและกรณีขอบ

แม้ขั้นตอนหลักจะตรงไปตรงมา แต่สถานการณ์จริงมักต้องการการปรับแต่ง ด้านล่างเป็นสถานการณ์ “ถ้าอย่างไร” ที่คุณอาจเจอ

### 1. หลายรูปร่าง, เงาต่างกัน

หากเอกสารของคุณมีกราฟิกหลายรายการ ให้วนลูปผ่านคอลเลกชันรูปร่างและกำหนดค่าการตั้งค่าเงาที่ไม่ซ้ำกันสำหรับแต่ละรูปร่าง  

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. เงาโปร่งแสง

Aspose.Words ให้คุณตั้งค่าแชนแนลอัลฟาโดยใช้ `Color.FromArgb(alpha, r, g, b)` ใช้ค่าอัลฟาต่ำ (เช่น 50) เพื่อให้ได้เอฟเฟกต์โปร่งแสงแบบนุ่มนวล  

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. ลบเงา

บางครั้งคุณอาจต้องปิดเงาหลังจากที่ได้ตั้งค่าไว้ เพียงตั้งค่า `Visible` เป็น `false`  

```csharp
        shadow.Visible = false;
```

### 4. ความกังวลเรื่องความเข้ากันได้

คุณลักษณะเงาที่ใช้ในที่นี้รองรับใน Word 2007 + (รูปแบบ DOCX) หากคุณกำหนดเป้าหมายเป็นรูปแบบไบนารี `.doc` เก่า เงาอาจถูกละเว้นเนื่องจากรูปแบบนั้นไม่มีองค์ประกอบ XML ที่จำเป็น ในกรณีเช่นนี้ ควรบันทึกเป็น DOCX หรือใช้สัญญาณภาพสำรองอื่น  

## สรุป: สิ่งที่เราทำสำเร็จ

- **โหลด** DOCX ด้วย Aspose.Words  
- **ดึง** รูปร่างแรกจากเอกสาร  
- **เข้าถึง** อ็อบเจ็กต์ `ShadowFormat` ของมัน  
- **เปิดใช้งาน** เงา, ตั้งสี, ความเบลอ, ระยะทาง, และมุม  
- **บันทึก** ไฟล์ใหม่ที่แสดงผลเงาอย่างชัดเจน  

ขั้นตอนทั้งหมดนี้ตอบ **how to set shadow** บนรูปร่าง พร้อมแสดงวิธี **add shadow to shape**, **apply shadow to shape**, และแม้กระทั่ง **how to add shadow** ในสถานการณ์ที่ซับซ้อนยิ่งขึ้น

## ขั้นตอนต่อไปและหัวข้อที่เกี่ยวข้อง

เมื่อคุณเชี่ยวชาญการจัดรูปแบบเงาแล้ว คุณอาจอยากสำรวจต่อ:

- **การเติมสีไล่ระดับ** สำหรับรูปร่าง (`Shape.FillFormat.GradientFill`)  
- **เอฟเฟกต์ข้อความ** เช่น แสงเรืองหรือการสะท้อน (`TextEffect`)  
- **การแทรกรูปร่างใหม่โดยโปรแกรม** (`doc.FirstSection.Body.AppendChild(new Shape(...))`)  
- **การส่งออกเป็น PDF** พร้อมรักษาเงา (`doc.Save("output.pdf")`)  

หัวข้อเหล่านี้ทั้งหมดอิงตามหลักการของอ็อบเจ็กต์โมเดลเดียวกันที่เราใช้ในที่นี้ ทำให้คุณรู้สึกคุ้นเคยได้อย่างรวดเร็ว

---

*ขอให้สนุกกับการเขียนโค้ด! หากพบปัญหาใด ๆ คอมเมนต์ด้านล่างหรือดูเอกสาร API ของ Aspose.Words เพื่อข้อมูลเชิงลึกเพิ่มเติม*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}