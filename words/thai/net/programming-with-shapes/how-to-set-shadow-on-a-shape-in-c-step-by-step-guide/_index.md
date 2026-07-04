---
category: general
date: 2026-04-10
description: วิธีตั้งค่าเงาบนรูปร่างใน C# – เรียนรู้วิธีใช้เงาตก, ปรับความโปร่งใส,
  ปรับเบลอ, และเพิ่มเงารูปร่างด้วย Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: th
og_description: วิธีตั้งเงาบนรูปทรงใน C# – บทเรียนนี้แสดงวิธีการใช้เงาตก, ปรับความโปร่งใส,
  ปรับเบลอ, และเพิ่มเงารูปทรงพร้อมตัวอย่างโค้ดที่ชัดเจน.
og_title: วิธีตั้งเงาบนรูปร่างใน C# – คู่มือเต็ม
tags:
- Aspose.Words
- C#
- Document Automation
title: วิธีตั้งเงาบนรูปทรงใน C# – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งเงาบนรูปร่างใน C# – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีตั้งเงา** บนรูปร่างเมื่อคุณสร้างเอกสาร Word ด้วยโค้ดหรือไม่? คุณไม่ได้อยู่คนเดียว นักพัฒนาหลายคนเจออุปสรรคเมื่อต้องการเงาลดระดับสำหรับกล่องข้อความ โลโก้ หรือกล่องอธิบาย และเอกสาร API ก็มักจะสั้นเกินไป  

ในบทเรียนนี้เราจะเดินผ่านกระบวนการทั้งหมด: ตั้งแต่การโหลดไฟล์ `.docx` การดึง `Shape` ตัวแรก ไปจนถึงการใส่เงา ปรับความโปร่งใส ปรับรัศมีเบลอ และสุดท้ายกำหนดตำแหน่งให้พอดี เมื่อเสร็จคุณจะได้โค้ดสั้น ๆ ที่ใช้ได้กับ Aspose.Words .NET 2023 หรือใหม่กว่า และคุณจะเข้าใจ *ทำไม* แต่ละคุณสมบัติจึงสำคัญ

## สิ่งที่คุณต้องเตรียม

- **Aspose.Words for .NET** (แพ็กเกจ NuGet `Aspose.Words`) – ไลบรารีที่ให้คลาส `Document`, `Shape` และ `ShadowFormat`  
- **.NET 6+** (หรือ .NET Framework 4.7.2) – เวอร์ชันรันไทม์ใดก็ได้ที่ทันสมัย  
- ไฟล์ Word ง่าย ๆ (`input.docx`) ที่มีรูปร่างอย่างน้อยหนึ่งรูป เช่น กล่องข้อความ  
- Visual Studio, VS Code หรือ IDE ที่คุณชื่นชอบ  

แค่นั้นเอง ไม่ต้องใช้เครื่องมือของบุคคลที่สามเพิ่มเติม ไม่ต้องใช้ COM interop เพียงแค่ C# ธรรมดา

![how to set shadow example](image-placeholder.png){:alt="วิธีตั้งเงาบนรูปร่างในเอกสาร Word"}

## วิธีตั้งเงา – ภาพรวม

แนวคิดหลักของ **วิธีตั้งเงา** คือการจัดการอ็อบเจกต์ `ShadowFormat` ที่อยู่บน `Shape` คิดว่า `ShadowFormat` เป็น “สไตล์ชีต” ขนาดเล็กสำหรับเงาเอง: มันบอกตัวเรนเดอร์ว่าเงาจะมองเห็นได้หรือไม่ สีของเงาเป็นอะไร ความโปร่งใสเท่าไหร่ เบลอแค่ไหน และตำแหน่งสัมพันธ์กับรูปร่างอย่างไร  

ด้านล่างเป็นโปรแกรมที่ *สมบูรณ์* สามารถรันได้เลย คัดลอก‑วางลงในแอปคอนโซล กด **F5** แล้วดูเงาที่ปรากฏในไฟล์ `output.docx` ที่บันทึกไว้

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### ทำไมการตั้งค่าเหล่านี้ถึงสำคัญ

- **Visible** – หากไม่เปิดฟลักนี้ คุณสมบัติอื่น ๆ ทั้งหมดจะถูกละเลย  
- **Color** – สีเทาเข้มจำลองเงา UI แบบทั่วไป; คุณสามารถเปลี่ยนเป็น `Color` ใดก็ได้  
- **Transparency** – ค่า 0.3 ให้ลุค *นุ่มนวล* แต่ยังทำให้รูปร่างอ่านได้ชัดเจน  
- **Size** – ควบคุมความเบลอ; ค่า 6 มักเพียงพอสำหรับความรู้สึกมืออาชีพ  
- **Distance & Angle** – ร่วมกันกำหนด *การเลื่อน*; 2 pts ที่ 45° ให้เงาแนวทแยงมุมอ่อน ๆ  

นี่คือสาระสำคัญของ **วิธีตั้งเงา** ต่อไปเราจะเจาะลึกแต่ละส่วนเพื่อให้คุณ **apply drop shadow**, **change transparency**, **adjust blur**, และ **add shape shadow** อย่างอิสระ

---

## Apply Drop Shadow to a Shape

เมื่อคนถามว่า “วิธี **apply drop shadow** ใน C# คืออะไร?” พวกเขามักต้องการแค่การเปิดการมองเห็นและสีเท่านั้น โค้ดสั้น ๆ ด้านล่างแยกสองบรรทัดนั้นออกมาให้คุณใช้ได้ทันที

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **เคล็ดลับ:** หากคุณกำหนดเป้าหมายเป็น Word รุ่นเก่า (2003‑2007) ควรใช้สีมาตรฐาน ค่าที่เป็น ARGB แปลก ๆ อาจถูกเรนเดอร์เวอร์ชันเก่าเพิกเฉย

---

## วิธีเปลี่ยนความโปร่งใสของเงา

ความโปร่งใสระบุเป็น **float ระหว่าง 0 ถึง 1** ค่า **0** หมายถึงเงาแน่นเต็มที่; **1** ทำให้เงาไม่มองเห็นได้ นักออกแบบส่วนใหญ่เลือกค่า **0.2‑0.4** เพื่อให้ดูเป็นธรรมชาติ

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### กรณีขอบ

- **ค่าติดลบ** – Aspose.Words จะบังคับให้เป็น 0 แต่ควรตรวจสอบอินพุตก่อน  
- **ค่ามากกว่า 1** – จะถูกบังคับให้เป็น 1 ทำให้เงาหายไป  

หากต้องการให้ผู้ใช้เลือกเป็นเปอร์เซ็นต์ ให้แปลงค่าก่อน:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## วิธีปรับเบลอ (Size) ของเงา

คุณสมบัติ **Size** ควบคุมรัศมีเบลอ ตัวเลขที่ใหญ่กว่าจะให้เงานุ่มและกระจายมากขึ้น วัดเป็นจุด (pt) ไม่ใช่พิกเซล

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### เมื่อใดควรใช้เบลอเล็ก vs. เบลอใหญ่

- **เบลอเล็ก (2‑4 pt)** – เหมาะกับคอล์อัพสไตล์ UI ที่ต้องการขอบคมชัด  
- **เบลอใหญ่ (8‑12 pt)** – เหมาะกับรายงานพิมพ์หรือเมื่อรูปร่างห่างจากพื้นหลังมาก

---

## Add Shape Shadow – การกำหนดตำแหน่งและทิศทาง

ส่วนสุดท้ายของ **add shape shadow** คือการเลื่อนตำแหน่ง มีสองคุณสมบัติทำงานร่วมกัน:

| คุณสมบัติ | ความหมาย |
|----------|-----------|
| **Distance** | ระยะที่เงาอยู่ห่างจากรูปร่าง (หน่วยเป็นจุด) |
| **Angle**    | ทิศทางของการเลื่อน (0° = ขวา, 90° = ลง, 180° = ซ้าย, 270° = ขึ้น) |

ตัวอย่างที่สร้างเงาแนวล่าง‑ขวาอ่อน ๆ:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

คุณสามารถทดลองเปลี่ยนมุมเพื่อจำลองแสงจากแหล่งต่าง ๆ เทคนิคทั่วไปคือให้ผู้ใช้เลือก “แหล่งกำเนิดแสง” จากดรอปดาวน์แล้วแมปเป็นค่ามุม

---

## ตัวอย่างทำงานเต็มรูปแบบ (รวมทุกขั้นตอน)

ด้านล่างเป็นโปรแกรมเดียวกันกับก่อนหน้า แต่เพิ่ม **คอมเมนต์พิเศษ** เพื่อให้ตรรกะชัดเจน คัดลอกไปวางใน `Program.cs` แล้วรัน; ไฟล์ผลลัพธ์จะมีกล่องข้อความพร้อมเงาที่ปรับแต่งอย่างสมบูรณ์

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `output.docx` กล่องข้อความแรกจะแสดงเงาเทาเข้ม โปร่งใส 30 % เบลอเล็กน้อย (size = 6) และเลื่อน 2 pt ที่มุม 45° เงานี้อ่อนแต่เห็นได้ชัด — พอดีกับสิ่งที่นักออกแบบ UI ส่วนใหญ่ต้องการ

---

## คำถามที่พบบ่อย & จุดต้องระวัง

- **“ทำงานกับรูปภาพได้หรือไม่?”**  
  ใช่. `Shape` ใด ๆ — ไม่ว่าจะเป็นกล่องข้อความ ภาพ หรือ auto‑shape — มี `ShadowFormat` อยู่ เพียงเปลี่ยนตรรกะการดึงรูปร่างให้ตรงกับดัชนีหรือชื่อที่ต้องการ

- **“ถ้าเอกสารมีหลายรูปร่างล่ะ?”**  
  วนลูป `doc.GetChildNodes(NodeType.Shape, true)` แล้วใส่ค่าตั้งค่าเดียวกันให้ทุกอัน คุณยังสามารถกรองด้วย `shape.Name` หรือ `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}