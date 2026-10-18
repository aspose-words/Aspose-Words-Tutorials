---
category: general
date: 2026-02-13
description: แปลง PNG เป็น Base64 ใน C# อย่างรวดเร็ว – เรียนรู้วิธีเข้ารหัสภาพเป็น
  Base64, ฝังภาพใน HTML ด้วย Base64, และคัดลอกสตรีมไปยังหน่วยความจำสำหรับโครงการเว็บ.
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: th
og_description: แปลง PNG เป็น Base64 ใน C# อย่างรวดเร็ว บทเรียนนี้แสดงวิธีการเข้ารหัสภาพเป็น
  Base64, ฝังภาพใน HTML ด้วย Base64, และคัดลอกสตรีมไปยังหน่วยความจำ.
og_title: แปลง PNG เป็น Base64 ใน C# – คู่มือฉบับสมบูรณ์
tags:
- C#
- image-processing
- data-uri
title: แปลง PNG เป็น Base64 ใน C# – คู่มือฉบับสมบูรณ์
url: /th/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลง PNG เป็น Base64 ใน C# – คู่มือฉบับสมบูรณ์

เคยต้องการ **convert PNG to Base64** แต่ไม่แน่ใจว่าจะเริ่มต้นอย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว; นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อพยายามฝังรูปภาพโดยตรงลงใน HTML หรือ CSS. ข่าวดีคือวิธีแก้ไขค่อนข้างตรงไปตรงมาทันทีที่คุณรู้ขั้นตอนที่ถูกต้อง.

ในบทแนะนำนี้ เราจะเดินผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบที่ **base64 encode image** ข้อมูล, แสดงให้คุณเห็นวิธี **embed image html base64** ผ่าน data‑URI, และแม้กระทั่งอธิบายวิธีที่ดีที่สุดในการ **copy stream to memory** โดยไม่ทำให้ทรัพยากรรั่วไหล. เมื่อจบคุณจะมีโค้ดสั้นที่สามารถนำไปใช้ซ้ำได้ในโปรเจค .NET ใดก็ได้.

## สิ่งที่คุณจะได้เรียนรู้

- วิธีตรวจสอบส่วนขยายของไฟล์โดยไม่คำนึงถึงตัวพิมพ์ใหญ่/เล็ก.  
- รูปแบบที่ปลอดภัยที่สุดสำหรับการแปลง **image stream to base64** ด้วย `MemoryStream`.  
- สร้าง data‑URI ที่เหมาะสมซึ่งเบราว์เซอร์เข้าใจ.  
- ทำความสะอาดสตรีมต้นฉบับเพื่อให้แอปของคุณคงน้ำหนักเบา.  

ไม่จำเป็นต้องใช้ไลบรารีภายนอก—เพียงคลาส BCL ที่มาพร้อมกับ .NET. หากคุณคุ้นเคยกับพื้นฐานของ C# และมีโปรเจคที่จัดการการอัปโหลดไฟล์อยู่แล้ว คุณก็พร้อมใช้งาน.

---

![แผนภาพแสดงการไหลจากไฟล์ PNG ไปยัง Base64 data‑URI – แปลง png เป็น base64](https://example.com/convert-png-to-base64-diagram.png "ตัวอย่างการแปลง png เป็น base64")

## แปลง PNG เป็น Base64 – ขั้นตอนโดยละเอียด

ด้านล่างเราจะแบ่งกระบวนการออกเป็นห้าขั้นตอนที่เป็นตรรกะ. แต่ละหัวข้อสะท้อนส่วนของปริศนา ทำให้คุณ (และผู้ช่วย AI) สามารถหาส่วนที่ต้องการได้อย่างง่ายดาย.

### ขั้นตอน 1: ตรวจสอบว่าแหล่งข้อมูลเป็น PNG (ไม่คำนึงถึงตัวพิมพ์ใหญ่/เล็ก)

ก่อนที่เราจะเสียหน่วยความจำ เราตรวจสอบว่าไฟล์ที่เข้ามาเป็น PNG จริงหรือไม่. ธง `StringComparison.OrdinalIgnoreCase` จัดการกับส่วนขยายที่ผสมตัวพิมพ์ใหญ่และเล็กได้ทั้งหมด.

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*ทำไมเรื่องนี้ถึงสำคัญ:* การพยายามเข้ารหัสไฟล์ที่ไม่ใช่รูปภาพ (หรือ JPEG) เป็น PNG อาจทำให้ผลลัพธ์เสียหายและทำให้ data‑URI ที่คุณฝังต่อมาขัดข้อง.

### ขั้นตอน 2: คัดลอกสตรีมไปยังหน่วยความจำ

สตรีม `Stream` ที่เข้ามา (อาจมาจากตัวจัดการอัปโหลด) จำเป็นต้องอ่านจนหมด. การใช้คำสั่ง `using var` รับประกันว่าบัฟเฟอร์จะถูกทำลายโดยอัตโนมัติ, ทำให้การ **copy stream to memory** สะอาด.

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*เคล็ดลับ:* หากคุณจัดการกับไฟล์ขนาดใหญ่มาก, พิจารณาใช้ `CopyToAsync` พร้อมขนาดบัฟเฟอร์ที่เหมาะสมเพื่อหลีกเลี่ยงการบล็อกเธรด.

### ขั้นตอน 3: เข้ารหัส Base64 รูปภาพ

ตอนนี้ไบต์ของรูปภาพอยู่ใน `memory` เราสามารถแปลงเป็นสตริง Base64 ได้. นี่คือหัวใจของ **base64 encode image**.

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*กำลังเกิดอะไรขึ้น?* `Convert.ToBase64String` รับอาร์เรย์ไบต์และคืนค่าการแสดงผลเป็นข้อความที่เบราว์เซอร์สามารถถอดรหัสกลับเป็นข้อมูลไบนารีได้.

### ขั้นตอน 4: สร้าง Data‑URI สำหรับ HTML/CSS

Data‑URI ช่วยให้คุณฝังรูปภาพโดยตรงในมาร์กอัป, ลดการร้องขอ HTTP เพิ่มเติม. รูปแบบคือ `data:[<mediatype>][;base64],<data>`.

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

เมื่อคุณแสดง `args.ResourceFilePath` ภายในแท็ก `<img src="...">` ภายหลัง, เบราว์เซอร์จะทำการแสดง PNG ทันที.

### ขั้นตอน 5: ปล่อยสตรีมต้นฉบับ

เนื่องจากรูปภาพตอนนี้แสดงด้วย data‑URI, `Stream` ดั้งเดิมจึงไม่จำเป็นอีกต่อไป. การตั้งค่าเป็น `null` ช่วยให้ตัวเก็บขยะเรียกคืนซ็อกเก็ตหรือไฟล์แฮนด์เดิลที่อยู่ด้านล่าง.

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*กรณีพิเศษ:* หากคุณต้องการไฟล์ต้นฉบับในภายหลัง (เช่น เพื่อเก็บบนดิสก์), ให้ข้ามขั้นตอนนี้และเก็บอ้างอิงไว้ที่อื่น.

---

## ตัวอย่างทำงานเต็มรูปแบบ

การรวมชิ้นส่วนทั้งหมดเข้าด้วยกันให้เมธอดกระชับที่คุณสามารถวางลงในคลาสใดก็ได้ที่ประมวลผลทรัพยากรที่อัปโหลด.

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากที่ `ProcessPng` ทำงาน, `args.ResourceFilePath` จะมีสตริงที่มีลักษณะเช่น:

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

คุณสามารถนำสตริงนั้นวางตรงลงในแท็ก `<img>` ได้เลย:

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

รูปภาพจะแสดงทันที, โดยไม่มีการจราจรเครือข่ายเพิ่มเติม.

---

## คำถามทั่วไป & กรณีพิเศษ

### ถ้า PNG มีขนาดใหญ่?

ภาพขนาดใหญ่สามารถทำให้การใช้หน่วยความจำพุ่งสูงเนื่องจากไฟล์ทั้งหมดอยู่ใน `MemoryStream`. สำหรับไฟล์ที่มีขนาดหลายเมกะไบต์, พิจารณาแปลง Base64 เป็นชิ้นส่วนหรือปรับขนาดภาพก่อนเข้ารหัส.

### ฉันสามารถทำให้เป็นแบบ async ได้หรือไม่?

แน่นอน. แทนที่ `CopyTo` ด้วย `CopyToAsync` และทำเครื่องหมายเมธอดเป็น `async Task`. สิ่งนี้ทำให้เธรดคำขอ ASP.NET ของคุณว่างขณะ I/O เสร็จ.

```csharp
await args.Stream.CopyToAsync(memory);
```

### โค้ดนี้ทำงานกับรูปแบบภาพอื่นหรือไม่?

โค้ดเองไม่มีการผูกกับรูปแบบ; คุณเพียงแค่ต้องปรับ MIME type ใน data‑URI (`image/jpeg`, `image/gif`, ฯลฯ) และเปลี่ยนการตรวจสอบส่วนขยายให้สอดคล้อง.

### ฉันจะจัดการข้อผิดพลาดอย่างราบรื่นได้อย่างไร?

ห่อบล็อกทั้งหมดด้วย `try/catch` และบันทึกข้อยกเว้น. หากคุณอยู่ในเว็บ API, ให้คืนค่า 400 Bad Request พร้อมข้อความที่เป็นประโยชน์.

---

## สรุป

ตอนนี้คุณรู้วิธี **convert PNG to Base64** ใน C# ตั้งแต่ต้นจนจบแล้ว. บทแนะนำได้ครอบคลุมการตรวจสอบประเภทไฟล์, การคัดลอกสตรีมเข้าสู่หน่วยความจำอย่างปลอดภัย, การทำ **base64 encode image**, การสร้าง **embed image html base64** data‑URI ที่เหมาะสม, และการทำความสะอาดทรัพยากร.  

จากนี้คุณอาจสำรวจการปรับขนาดภาพแบบเรียลไทม์, การแคช data‑URI ที่สร้างขึ้น, หรือแม้กระทั่งการสร้าง SVG placeholder. ไม่ว่าคุณจะเลือกอะไร, รูปแบบที่แสดงด้านบนจะเป็นพื้นฐานที่มั่นคงสำหรับทุกสถานการณ์ที่คุณต้องการแปลง **image stream to base64** และฝังโดยตรงในมาร์กอัป.

มีการปรับเปลี่ยนกระบวนการนี้หรือไม่? บางทีคุณอาจทำงานกับ WebAssembly หรือ Blazor—อย่าลังเลที่จะแบ่งปันการทดลองของคุณในคอมเมนต์. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}