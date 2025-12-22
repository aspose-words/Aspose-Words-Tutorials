---
category: general
date: 2025-12-22
description: เพิ่มเอฟเฟกต์เงาให้กับรูปร่าง C# ของคุณได้อย่างง่ายดาย เรียนรู้วิธีเพิ่มเงา
  วิธีตั้งค่าความเบลอ และสร้างเงานุ่มด้วยการจัดรูปแบบเงารูปร่าง
draft: false
keywords:
- add shadow effect
- how to add shadow
- how to set blur
- create soft shadow
- add shape shadow
language: th
og_description: เพิ่มเอฟเฟกต์เงาให้กับรูปทรง C# ของคุณ บทเรียนนี้จะแสดงวิธีเพิ่มเงา
  ตั้งค่าความเบลอ และสร้างเงานุ่มด้วยตัวอย่างโค้ดที่ชัดเจน
og_title: เพิ่มเอฟเฟกต์เงาให้กับรูปร่างใน C# – คู่มือฉบับสมบูรณ์
tags:
- C#
- graphics
- Aspose.Slides
- UI design
title: เพิ่มเอฟเฟกต์เงาให้กับรูปทรงใน C# – คู่มือขั้นตอนโดยละเอียด
url: /th/java/images-shapes/add-shadow-effect-to-shapes-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มเอฟเฟกต์เงาให้กับรูปร่างใน C# – คู่มือเต็ม

เคยสงสัยไหมว่าจะแนบ **add shadow effect** ให้กับรูปร่างอย่างไรโดยไม่ต้องใช้เวลาหลายชั่วโมงค้นหาในเอกสาร API? คุณไม่ได้เป็นคนเดียว นักพัฒนาหลายคนเจออุปสรรคเมื่อพวกเขาต้องการเงาที่ละเอียดเพื่อทำให้องค์ประกอบ UI โดดเด่น, และคำตอบแบบ “ดูที่อ้างอิง” ปกติก็เหมือนกับทางตัน.

ในบทแนะนำนี้ เราจะอธิบายทุกอย่างที่คุณต้องการเพื่อ **add shadow effect** ให้กับรูปร่างโดยใช้ C#. เราจะครอบคลุม *how to add shadow*, *how to set blur* สำหรับแสงอ่อน ๆ, และแม้กระทั่งวิธี **create soft shadow** ที่ดูเป็นมืออาชีพในแอปพลิเคชันใด ๆ. เมื่อจบคุณจะมีตัวอย่างที่พร้อมรันที่คุณสามารถนำไปใส่ในโปรเจคของคุณได้ทันที.

## สิ่งที่บทแนะนำนี้ครอบคลุม

- คำสั่ง API ที่แม่นยำที่จำเป็นสำหรับ **add shape shadow** ใน Aspose.Slides (หรือไลบรารีที่คล้ายกัน).
- โค้ดแบบขั้นตอน‑ต่อ‑ขั้นตอนที่คุณสามารถคัดลอก‑วางได้.
- เหตุผลว่าการตั้งค่าแต่ละอย่างสำคัญอย่างไร – ไม่ใช่แค่รายการคำสั่ง.
- กรณีขอบเขตเช่นรูปร่างโปร่งแสง, เงาหลายชั้น, และเคล็ดลับประสิทธิภาพ.
- ตัวอย่างเต็มที่สามารถรันได้ซึ่งสร้างเงานุ่มที่มองเห็นได้บนสี่เหลี่ยม.

ไม่จำเป็นต้องมีประสบการณ์กับ shadow APIs มาก่อน; เพียงแค่ความเข้าใจพื้นฐานของ C# และการเขียนโปรแกรมเชิงวัตถุ.

---

## Add Shadow Effect – ภาพรวม

เงาเป็นการเลื่อนตำแหน่งภาพพร้อมกับการเบลอที่จำลองความลึก. ในไลบรารีกราฟิกส่วนใหญ่ กระบวนการจะเป็นดังนี้:

1. **Retrieve** วัตถุการจัดรูปแบบเงาของรูปร่าง.
2. **Configure** คุณสมบัติต่าง ๆ เช่น offset, color, และ blur radius.
3. **Apply** การตั้งค่ากลับไปยังรูปร่าง.

เมื่อคุณทำตามสามขั้นตอนนี้ คุณจะเห็น **soft shadow** ปรากฏทันที. กุญแจคือ blur radius – นั่นคือปุ่มที่ทำให้ขอบแข็งกลายเป็นหมอกอ่อน.

### ตารางสรุปคำศัพท์อย่างรวดเร็ว

| Term | What it does |
|------|--------------|
| **ShadowFormat** | เก็บคุณสมบัติทั้งหมดที่เกี่ยวกับเงา (offset, color, blur, ฯลฯ). |
| **BlurRadius** | ควบคุมความเบลอของขอบเงา ค่าที่สูงขึ้น = เงานุ่มขึ้น. |
| **OffsetX / OffsetY** | ย้ายเงาในแนวนอน/แนวตั้ง. |
| **Transparency** | ทำให้เงามีความทึบหรือโปร่งใสมากขึ้น. |

การเข้าใจสิ่งเหล่านี้จะช่วยให้คุณ **create soft shadow** ที่รู้สึกเป็นธรรมชาติ.

## วิธีเพิ่มเงาให้กับรูปร่าง

สิ่งแรกที่ต้องทำ – คุณต้องมีอินสแตนซ์ของรูปร่าง. ด้านล่างเป็นการตั้งค่าขั้นต่ำโดยใช้ Aspose.Slides, แต่รูปแบบเดียวกันทำงานกับไลบรารีกราฟิก .NET ส่วนใหญ่.

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System.Drawing;

// Create a new presentation and add a blank slide
Presentation pres = new Presentation();
ISlide slide = pres.Slides[0];

// Add a rectangle shape (our canvas for the shadow)
IShape rect = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 100, 100, 300, 150);
rect.FillFormat.FillType = FillType.Solid;
rect.FillFormat.SolidFillColor = Color.LightBlue;
rect.LineFormat.Width = 2;
rect.LineFormat.FillFormat.SolidFillColor = Color.DarkBlue;
```

> **Pro tip:** เลือกรูปร่างที่มีการเติมสีที่มองเห็นได้; มิฉะนั้นเงาอาจถูกซ่อนอยู่หลังพื้นหลังโปร่งแสง.

ตอนนี้เรามี `rect` แล้ว, เราสามารถ **add shape shadow** ได้โดยเข้าถึง `ShadowFormat` ของมัน:

```csharp
// Step 1: Obtain the shape you want to modify (already done above)
// Step 2: Access the shape's shadow formatting object
ShadowFormat shadow = rect.ShadowFormat;

// Step 3: Enable the shadow and set basic properties
shadow.Visible = true;                 // Turn the shadow on
shadow.Type = ShadowType.Inner;        // You can also use Outer, Perspective, etc.
shadow.Color = Color.Black;           // Classic black shadow
shadow.OffsetX = 5;                    // 5 points to the right
shadow.OffsetY = 5;                    // 5 points down
```

ในขั้นตอนนี้สี่เหลี่ยมจะมีเงาที่คมชัดและขอบแข็ง. หากคุณรันพรีเซนเทชัน, คุณจะเห็น **add shadow effect** ที่มีประโยชน์มากกว่าการตกแต่ง.

## วิธีตั้งค่า Blur สำหรับ Soft Shadow

ขอบที่แข็งอาจดูราคาถูก, โดยเฉพาะบนหน้าจอ high‑DPI. นั่นคือจุดที่ **how to set blur** เข้ามา. คุณสมบัติ `BlurRadius` รับค่า `float` ที่เป็นรัศมีในหน่วย points.

```csharp
// Step 4: Set the blur radius to create a soft shadow
shadow.BlurRadius = 5.0f;   // 5 points gives a subtle, soft look
```

ทำไมถึงเป็น `5.0f`? ในการใช้งานจริง, ค่ารหว่าง `3.0f` ถึง `8.0f` ให้เงานุ่มธรรมชาติสำหรับส่วน UI ส่วนใหญ่. ค่าที่สูงกว่่านั้นจะดูเหมือนแสงเรืองแสงมากกว่าเงา.

คุณยังสามารถปรับค่า transparency เพื่อทำให้เงานุ่มลง:

```csharp
shadow.Transparency = 0.4f; // 40% transparent – looks lighter
```

ตอนนี้คุณได้ **added shadow effect** ที่มองเห็นได้และอ่อนโยน. บันทึกไฟล์เพื่อดูผลลัพธ์:

```csharp
pres.Save("AddShadowEffect.pptx", SaveFormat.Pptx);
```

เปิด `AddShadowEffect.pptx` ใน PowerPoint หรือโปรแกรมดูไฟล์ใด ๆ, แล้วคุณจะเห็นสี่เหลี่ยมที่มีการเลื่อนตำแหน่งเบลออย่างสวยงาม – ตัวอย่าง **create soft shadow** ที่เป็นมาตรฐาน.

## สร้าง Soft Shadow ด้วยการตั้งค่าแบบกำหนดเอง

บางครั้งคุณต้องการการควบคุมเชิงศิลปะมากขึ้น. ด้านล่างเป็นเมธอดช่วยเหลือที่รวมการตั้งค่าทั่วไปไว้ในคำเรียกเดียว. สามารถคัดลอกไปใส่ในคลาส utilities ได้ตามต้องการ.

```csharp
/// <summary>
/// Applies a customizable soft shadow to any IShape.
/// </summary>
public static void ApplySoftShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                   float blur = 6f, Color? color = null, float transparency = 0.35f)
{
    if (shape == null) throw new ArgumentNullException(nameof(shape));

    ShadowFormat sf = shape.ShadowFormat;
    sf.Visible = true;
    sf.Type = ShadowType.Outer;
    sf.OffsetX = offsetX;
    sf.OffsetY = offsetY;
    sf.BlurRadius = blur;
    sf.Color = color ?? Color.Black;
    sf.Transparency = transparency;
}
```

ใช้มันแบบนี้:

```csharp
ApplySoftShadow(rect, offsetX: 8, offsetY: 8, blur: 7, color: Color.DarkSlateGray);
```

เมธอดนี้ทำให้คุณ **add shape shadow** ด้วยบรรทัดเดียว, ทำให้โค้ดหลักของคุณเป็นระเบียบ. มันยังแสดงวิธี *how to add shadow* แบบที่สามารถนำกลับมาใช้ใหม่ได้ – วิธีการที่ขยายได้ดีเมื่อคุณมีหลายสิบรูปทรง.

## Add Shape Shadow – ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่ทำงานอิสระที่คุณสามารถคอมไพล์และรันได้. มันสร้างพรีเซนเทชัน, เพิ่มสามสี่เหลี่ยม, แต่ละอันมีการตั้งค่าเงาที่แตกต่างกัน, และบันทึกไฟล์.

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System;
using System.Drawing;

namespace ShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Initialize presentation
            Presentation pres = new Presentation();
            ISlide slide = pres.Slides[0];

            // Rectangle 1 – basic shadow
            IShape rect1 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 50, 50, 200, 100);
            rect1.FillFormat.SolidFillColor = Color.LightCoral;
            ApplyShadow(rect1, blur: 3f, offsetX: 4, offsetY: 4, transparency: 0.2f);

            // Rectangle 2 – soft shadow (our main focus)
            IShape rect2 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 50, 200, 100);
            rect2.FillFormat.SolidFillColor = Color.LightGreen;
            ApplyShadow(rect2, blur: 6f, offsetX: 6, offsetY: 6, transparency: 0.4f);

            // Rectangle 3 – heavy blur for a glow effect
            IShape rect3 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 550, 50, 200, 100);
            rect3.FillFormat.SolidFillColor = Color.LightSkyBlue;
            ApplyShadow(rect3, blur: 12f, offsetX: 0, offsetY: 0, transparency: 0.6f, color: Color.DarkBlue);

            // Save the result
            pres.Save("ShadowDemo.pptx", SaveFormat.Pptx);
            Console.WriteLine("Presentation created – open ShadowDemo.pptx to see the add shadow effect.");
        }

        // Reusable helper (same as earlier)
        public static void ApplyShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                       float blur = 5f, Color? color = null, float transparency = 0.35f)
        {
            ShadowFormat sf = shape.ShadowFormat;
            sf.Visible = true;
            sf.Type = ShadowType.Outer;
            sf.OffsetX = offsetX;
            sf.OffsetY = offsetY;
            sf.BlurRadius = blur;
            sf.Color = color ?? Color.Black;
            sf.Transparency = transparency;
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เมื่อคุณเปิด *ShadowDemo.pptx*, คุณจะเห็นสามสี่เหลี่ยม. ตัวกลางแสดงเทคนิค **create soft shadow** แบบคลาสสิกด้วยการเบลอและเลื่อนตำแหน่งระดับปานกลาง, ส่วนอื่น ๆ แสดงความแตกต่างที่เบาและหนักกว่า.

![ตัวอย่างการเพิ่มเอฟเฟกต์เงา](shadow-example.png "ตัวอย่างการเพิ่มเอฟเฟกต์เงา")

*ข้อความแทนภาพ:* ตัวอย่างการเพิ่มเอฟเฟกต์เงา

## ข้อผิดพลาดทั่วไปและเคล็ดลับ

- **Shadow not showing?** ตรวจสอบให้แน่ใจว่า `ShadowFormat.Visible` ถูกตั้งค่าเป็น `true`. ไลบรารีบางตัวมีค่าเริ่มต้นเป็น invisible.
- **Blur looks too harsh.** ลดค่า `BlurRadius` หรือเพิ่มค่า `Transparency`. ค่า `0.4f` สำหรับ transparency มักทำให้ลักษณะดูนุ่มขึ้น.
- **Performance concerns.** การเรนเดอร์เงาจำนวนมากอาจทำให้การรีดรอว์ UI ช้าลง. แคชผลลัพธ์หากคุณวาดในลูป.
- **Multiple shadows.** API ส่วนใหญ่รองรับเงาเพียงหนึ่งเงาต่อรูปร่าง. เพื่อจำลองหลายเงา, ทำสำเนารูปร่าง, เลื่อนตำแหน่งแต่ละสำเนา, และเรนเดอร์ตามลำดับที่ถูกต้อง.
- **Cross‑platform quirks.** หากคุณกำหนดเป้าหมายเป็น Xamarin หรือ MAUI, ตรวจสอบว่า shadow API มีให้ใช้บนแพลตฟอร์มเป้าหมายหรือไม่; หากไม่อาจต้องใช้ custom renderer.

## สรุป

ตอนนี้คุณรู้วิธี **add shadow effect** ให้กับรูปร่างใน C# อย่างแม่นยำแล้ว. ตั้งแต่ขั้นตอนพื้นฐานของการดึงวัตถุ `ShadowFormat` ไปจนถึงการปรับแต่ง blur อย่างละเอียด

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}