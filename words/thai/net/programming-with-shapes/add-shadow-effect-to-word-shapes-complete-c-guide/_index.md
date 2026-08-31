---
category: general
date: 2026-02-10
description: เพิ่มเอฟเฟกต์เงาให้กับรูปทรงใน Word ด้วย C# เรียนรู้วิธีเปลี่ยนสีเงา
  ตั้งค่าความโปร่งแสง และใช้เงารูปทรงได้ในไม่กี่ขั้นตอน.
draft: false
keywords:
- add shadow effect
- change shadow color
- how to set transparency
- add shape shadow
- apply shadow color
language: th
og_description: เพิ่มเอฟเฟกต์เงาให้กับรูปทรงใน Word ด้วย C# เรียนรู้วิธีเปลี่ยนสีเงา
  ตั้งค่าความโปร่งแสง และใช้เงารูปทรงได้ในไม่กี่ขั้นตอน.
og_title: เพิ่มเอฟเฟกต์เงาให้กับรูปร่างใน Word – คู่มือ C# ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Automation
title: เพิ่มเอฟเฟกต์เงาให้กับรูปร่างใน Word – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มเอฟเฟกต์เงาให้กับรูปร่างใน Word – คู่มือ C# ฉบับสมบูรณ์

เคยต้องการ **add shadow effect** ให้กับรูปร่างใน Word แต่ไม่แน่ใจว่าจะเริ่มจากตรงไหนหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักถามว่า “จะทำให้รูปร่างดูมีมิติสาม‑มิติมากขึ้นได้อย่างไร?” ข่าวดีคือด้วยไม่กี่บรรทัดของ C# คุณสามารถเปลี่ยนสีเงา ตั้งค่าความโปร่งแสง และปรับแต่งรูปลักษณ์ของรูปร่างใดก็ได้ ในบทเรียนนี้เราจะพาคุณผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบ พร้อมเคล็ดลับหลายอย่างที่คุณอาจอยากรู้ตั้งแต่แรก

เราจะครอบคลุม:

* โหลดไฟล์ DOCX ที่มีรูปร่างอยู่แล้ว  
* ค้นหารูปร่าง (แม้จะซ้อนอยู่ในกลุ่ม)  
* ใช้เงา—ระยะ, เบลอ, สี, และความโปร่งแสง  
* ตรวจสอบผลลัพธ์โดยการบันทึกเอกสาร  

ไม่มีเอกสารภายนอกที่จำเป็น; ทุกอย่างที่คุณต้องการอยู่ที่นี่แล้ว สิ่งที่ต้องมีล่วงหน้าเพียงอย่างเดียวคือการอ้างอิงถึง **Aspose.Words for .NET** (หรือไลบรารีที่เข้ากันได้ซึ่งเปิดเผย `Shape.ShadowFormat`) หากคุณใช้ NuGet เพียงรัน `Install-Package Aspose.Words` พร้อมหรือยัง? ไปกันเลย

---

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 หรือใหม่กว่า | API สมัยใหม่, ประสิทธิภาพดีกว่า |
| Aspose.Words for .NET (หรือเทียบเท่า) | มีคลาส `Document`, `Shape`, และ `ShadowFormat` |
| ไฟล์ DOCX (`input.docx`) ที่มีอย่างน้อยหนึ่งรูปร่าง | บทเรียนนี้จัดการกับรูปร่างที่มีอยู่แล้ว; คุณสามารถสร้างรูปร่างใน Word ด้วยตนเองได้หากต้องการ |

> **Pro tip:** หากคุณไม่มีรูปร่างพร้อมใช้งาน ให้เปิด Word, แทรกสี่เหลี่ยมผืนผ้าง่าย ๆ, บันทึกไฟล์เป็น `input.docx` แล้ววางไว้ในโฟลเดอร์ `Resources` ของโปรเจกต์คุณ

## Step 1 – Load the Word Document and Locate the Shape {#add-shadow-effect-step1}

สิ่งแรกที่ต้องทำคือเราต้องมีอ็อบเจกต์ `Document` ที่ชี้ไปยังไฟล์ต้นทางของเรา จากนั้นเราจะดึงรูปร่างแรกโดยใช้การค้นหาแบบเรียกซ้ำ เพื่อให้ทำงานได้แม้รูปร่างจะอยู่ภายในกลุ่มก็ตาม

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Step 1: Load the Word document that contains a shape
        Document doc = new Document("Resources/input.docx");

        // Step 2: Retrieve the first shape in the document (searches recursively)
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Continue with shadow settings...
```

**Why we do this:**  
* `Document` เป็นจุดเริ่มต้นสำหรับไฟล์ Word ใด ๆ  
* `GetChild(NodeType.Shape, 0, true)` จะเดินทางทั่วต้นไม้โหนดทั้งหมด, ทำให้เราไม่พลาดรูปร่างที่ซ้อนกัน  
* การตรวจสอบค่า null ป้องกัน `NullReferenceException` หากไฟล์ไม่มีรูปร่าง—กรณีขอบที่หลายคนเริ่มต้นมักมองข้าม

## Step 2 – Set the Shadow Distance and Blur {#add-shadow-effect-step2}

เงาไม่ใช่แค่สี; การเยื้องและความนุ่มของเงาก็สำคัญไม่แพ้กัน ให้เราย้ายเงาออกไปหลายจุดและเพิ่มความเบลอเล็กน้อย

```csharp
        // Step 3: Set how far the shadow is offset from the shape
        targetShape.ShadowFormat.Distance = 4.0;   // 4 points offset

        // Step 4: Define the softness of the shadow edges
        targetShape.ShadowFormat.BlurRadius = 2.0; // 2 points blur
```

**Explanation:**  
* **Distance** ควบคุมการเยื้อง X/Y ค่า `4.0` จะย้ายเงาลงและขวา, จำลองแหล่งแสงจากด้านบน‑ซ้าย  
* **BlurRadius** กำหนดความนุ่มของขอบ ค่าเล็กทำให้เงาคมชัด; ค่ามากทำให้ดูเหมือนแสงอ่อน ๆ  

หากต้องการทิศทางแสงต่างออกไป คุณสามารถปรับ `ShadowFormat.Angle` (ค่าเริ่มต้นคือ 45°) ได้เช่นกัน  

## Step 3 – Change Shadow Color and Set Transparency {#add-shadow-effect-step3}

ตอนนี้มาส่วนที่สนุก—เปลี่ยนสีและทำให้เงาโปร่งแสงบางส่วน นี่คือจุดที่คีย์เวิร์ดรอง **change shadow color** และ **how to set transparency** เข้ามาเกี่ยวข้อง

```csharp
        // Step 5: Choose a colour for the shadow
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color here

        // Step 6: Make the shadow partially transparent (30 % transparent)
        targetShape.ShadowFormat.Transparency = 0.3; // Value between 0 (opaque) and 1 (fully transparent)
```

**Why it matters:**  
* `Color.DarkGray` เป็นค่าเริ่มต้นที่ปลอดภัยและทำงานได้ทั้งพื้นหลังสว่างและมืด คุณสามารถเปลี่ยนเป็น `Color.FromArgb(255, 0, 0, 0)` เพื่อเป็นสีดำสนิทหรือค่า ARGB ใด ๆ ที่กำหนดเองได้  
* ตั้งค่า `Transparency` เป็น `0.3` จะให้เอฟเฟกต์โปร่งแสง 30 %—พอให้ความลึกโดยไม่บังรูปร่างด้านล่าง  

**Edge case:** เวอร์ชัน Word เก่าบางรุ่นอาจละเลยความโปร่งแสงบนประเภทรูปร่างบางอย่าง (เช่น WordArt) หากเงายังคงทึบเต็มที่ ลองแปลงรูปร่างเป็นรูปภาพก่อน

## Step 4 – Save and Verify the Result {#add-shadow-effect-step4}

หลังจากปรับเงาเสร็จ เราจะเขียนเอกสารกลับไปยังดิสก์ การเปิดไฟล์ใน Word ควรจะแสดงเงาที่สีอ่อน, โปร่งแสงบางส่วน รอบรูปร่าง

```csharp
        // Step 7: Save the modified document
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

**Verification checklist:**

1. เปิด `output_with_shadow.docx` ใน Microsoft Word  
2. คลิกรูปร่าง → Format → Shape Effects → Shadow  
3. คุณควรเห็นเงาสีเทาเข้ม, เยื้องประมาณ ~4 pt, เบลอ, และโปร่งแสง 30 %  

หากมีอะไรไม่ตรง ให้ตรวจสอบคุณสมบัติของ `ShadowFormat` โดยเฉพาะ `Distance` และ `Transparency`

## Common Variations and What‑If Scenarios {#add-shadow-effect-variations}

### Adding a Shadow to Multiple Shapes

หากต้องการ **add shape shadow** ให้กับทุกรูปร่างในเอกสาร ให้แทนที่การดึงรูปร่างเดียวด้วยลูป:

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Distance = 5.0;
            shp.ShadowFormat.BlurRadius = 3.0;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.4;
        }
```

### Using a Custom Colour with Alpha

บางครั้งคุณอาจต้องการให้สีเงาเองก็มีความโปร่งแสงผสมอยู่ ใช้ `Color.FromArgb` ร่วมกับ `Transparency` เพื่อสร้างเอฟเฟกต์ชั้นหลายระดับ:

```csharp
        // Semi‑transparent blue shadow
        targetShape.ShadowFormat.Color = Color.FromArgb(180, 0, 0, 255); // 180/255 ≈ 70% opacity
        targetShape.ShadowFormat.Transparency = 0.2; // Additional 20% transparency
```

### Handling Shapes Inside a Group

รูปร่างที่จัดกลุ่มจะถูกเก็บเป็นโหนด `GroupShape` การค้นหาแบบเรียกซ้ำที่เราใช้ (`true` flag) จะดำดิ่งเข้าไปในกลุ่มแล้วอยู่แล้ว แต่หากต้องการจัดการกลุ่มเป็นเอกเทศ ให้แคสต์เป็น `GroupShape` แล้ววนลูป `ChildNodes` ของมัน

```csharp
        GroupShape group = targetShape.ParentNode as GroupShape;
        if (group != null)
        {
            foreach (Shape inner in group.GetChildNodes(NodeType.Shape, true))
            {
                // Apply same shadow settings to each inner shape
                inner.ShadowFormat = targetShape.ShadowFormat.Clone();
            }
        }
```

## Pro Tips & Pitfalls {#add-shadow-effect-tips}

* **Pro tip:** ขณะทดลอง ให้ตั้งค่า `ShadowFormat.Visible = true` อย่างชัดเจน บาง API จะซ่อนเงาจนกว่าจะมีการเปลี่ยนแปลงคุณสมบัติ  
* **Watch out for:** การตั้งค่า “No Outline” ของ Word สามารถทำให้เงาดูแยกออกจากรูปร่าง ตรวจสอบให้แน่ใจว่าเส้นขอบของรูปร่างเปิดใช้งานหากต้องการให้เงาเชื่อมต่อกับมัน  
* **Performance note:** การอัปเดตรูปหลายพันรูปในเอกสารขนาดใหญ่อาจช้า ให้ทำการเปลี่ยนแปลงเป็นชุดและเรียก `doc.UpdatePageLayout()` ครั้งเดียวตอนจบ  
* **Compatibility:** Aspose.Words 23.10+ รองรับคุณสมบัติเงาเต็มรูปแบบสำหรับ DOCX, แต่เวอร์ชันเก่าอาจละเลย `BlurRadius` ตรวจสอบกับเวอร์ชันไลบรารีที่คุณใช้งานเสมอ  

## Full Working Example {#add-shadow-effect-complete}

ด้านล่างเป็นโปรแกรมที่พร้อมคัดลอก‑วางใช้งานครบถ้วน รวมถึง `using` ทั้งหมด, การจัดการข้อผิดพลาด, และคอมเมนต์

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the document that already contains a shape.
        Document doc = new Document("Resources/input.docx");

        // Retrieve the first shape (recursively searches groups).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Apply shadow distance and blur.
        targetShape.ShadowFormat.Distance = 4.0;      // Offset from shape
        targetShape.ShadowFormat.BlurRadius = 2.0;   // Soft edges

        // Change shadow color and set transparency.
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;     // How to set transparency (30%)

        // Save the modified document.
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

การรันโปรแกรมนี้จะสร้าง `output_with_shadow.docx` พร้อม **add shadow effect** ที่คุณต้องการ เปิดไฟล์แล้วคุณจะเห็นเงาสีเทาเข้มที่เบลออย่างสวยงามและโปร่งแสง 30 %—ลักษณะที่คุณคาดหวังจากการนำเสนอระดับมืออาชีพ

## Conclusion

เราได้สาธิตวิธี **add shadow effect** ให้กับรูปร่างใน Word ด้วย C# โดยการโหลดเอกสาร, ค้นหารูปร่าง, ปรับคุณสมบัติ `ShadowFormat`, และบันทึกไฟล์ คุณจึงควบคุม **change shadow color**, **how to set transparency**, และ **add shape shadow** ได้ภายในไม่กี่นาที  

ต่อไปคุณอาจต้องการ **apply shadow color** อย่างมีเงื่อนไข—เช่นเงาเข้มขึ้นสำหรับรูปร่างใหญ่หรือสีต่างกันตามอินพุตของผู้ใช้ หรือสำรวจการปรับปรุงภาพอื่น ๆ เช่น glow, reflection, หรือ 3‑D bevels รูปแบบ `ShadowFormat` เดียวกันใช้ได้กับฟีเจอร์เหล่านั้น ทำให้คุณพร้อมขยายบทเรียนนี้ต่อไป

มีคำถามหรือเจอกรณีขอบแปลก ๆ? แสดงความคิดเห็นด้านล่างและมาช่วยกันแก้ไขกันเถอะ Happy coding, and may your documents always have that extra pop of depth!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}