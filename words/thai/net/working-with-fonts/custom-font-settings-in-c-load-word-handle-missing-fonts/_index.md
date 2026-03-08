---
category: general
date: 2026-03-08
description: การตั้งค่าแบบอักษรที่กำหนดเองช่วยให้คุณตั้งค่าฟอนต์ โหลดเอกสาร Word อย่างปลอดภัย
  และจัดการฟอนต์ที่หายไปด้วย Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: th
og_description: การตั้งค่าแบบอักษรแบบกำหนดเองช่วยให้คุณตั้งค่าฟอนต์ โหลดเอกสาร Word
  อย่างปลอดภัย และจัดการกับฟอนต์ที่หายไปด้วย Aspose.Words.
og_title: การตั้งค่าแบบอักษรแบบกำหนดเองใน C# – โหลด Word และจัดการแบบอักษรที่หายไป
tags:
- Aspose.Words
- C#
- Font Management
title: การตั้งค่าแบบอักษรแบบกำหนดเองใน C# – โหลด Word และจัดการแบบอักษรที่หายไป
url: /th/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การตั้งค่าแบบอักษรแบบกำหนดเองใน C# – โหลด Word & จัดการแบบอักษรที่หายไป

เคยสงสัยไหมว่า **การตั้งค่าแบบอักษรแบบกำหนดเอง** ทำงานอย่างไรเมื่อไฟล์ Word อ้างอิงแบบอักษรที่คุณไม่ได้ติดตั้ง? นี่เป็นปัญหาที่พบบ่อย—เอกสารของคุณดูดีบนเครื่องหนึ่ง แล้วจู่ๆ ทุกย่อหน้าก็เปลี่ยนเป็นแบบอักษรสำรองบนเครื่องอื่น.  

ข่าวดีคืออะไร? ด้วย Aspose.Words คุณสามารถ **ตั้งค่าแบบอักษร**, **โหลดเนื้อหาเอกสาร Word** และ **จัดการแบบอักษรที่หายไป** ทั้งหมดในกระบวนการเดียวที่เรียบร้อย ด้านล่างคุณจะพบตัวอย่างที่สมบูรณ์พร้อมรันที่แสดงวิธีทำอย่างละเอียด พร้อมเหตุผลของแต่ละขั้นตอน.

## สิ่งที่คุณจะได้เรียนรู้

* สร้างอ็อบเจ็กต์ `LoadOptions` และแนบอินสแตนซ์ `FontSettings`.  
* ลงทะเบียน warning callback เพื่อให้คุณเห็นว่าแบบอักษรใดถูกแทนที่.  
* โหลดไฟล์ DOCX ที่อาจขาดแบบอักษร และพิมพ์รายละเอียดการแทนที่ไปยังคอนโซล.  

เมื่อจบคุณจะสามารถส่งมอบแอป C# ของคุณด้วยความมั่นใจ รู้ว่าทุกสถานการณ์ของแบบอักษรที่หายไปถูกบันทึกและสามารถจัดการได้ในภายหลัง.

> **ข้อกำหนดเบื้องต้น:** Aspose.Words for .NET (v23.12 หรือใหม่กว่า) ที่ติดตั้งผ่าน NuGet และความคุ้นเคยพื้นฐานกับแอปคอนโซล C#.

---

## การตั้งค่าแบบอักษรแบบกำหนดเอง – กำหนดค่า LoadOptions

สิ่งแรกที่คุณต้องการคืออ็อบเจ็กต์ `LoadOptions` ซึ่งบอก Aspose.Words ว่าจะจัดการไฟล์ที่เข้ามาอย่างไร โดยการกำหนดอินสแตนซ์ `FontSettings` ใหม่ เราจะให้ไลบรารีมีที่สำหรับค้นหาแบบอักษรแบบกำหนดเอง.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
หากคุณละเว้น `FontSettings` Aspose.Words จะย้อนกลับไปใช้คอลเลกชันแบบอักษรเริ่มต้นของระบบ ซึ่งหมายความว่าแบบอักษรที่หายไปจะถูกแทนที่โดยไม่แจ้งให้คุณทราบและคุณจะไม่รู้ว่าแบบอักษรใดถูกสลับ การสร้างคอนเทนเนอร์ `FontSettings` อย่างชัดเจนทำให้คุณควบคุมกระบวนการค้นหาได้เต็มที่.

---

## ตั้งค่า Font Settings บน LoadOptions

ตอนนี้เรามีอ็อบเจ็กต์ `FontSettings` แล้ว คุณอาจสงสัยว่าจะชี้ไปที่ไหน โดยทั่วไปคุณจะเพิ่มโฟลเดอร์ที่มีแบบอักษรที่คุณจัดส่งพร้อมแอปพลิเคชันของคุณ:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*หากคุณไม่มีโฟลเดอร์ส่วนตัว คุณสามารถละเว้นบล็อกนี้ได้—Aspose.Words จะยังคงรายงานแบบอักษรที่หายไปผ่าน warning callback.*

**เคล็ดลับ:** ใช้แฟล็ก `recursive: true` หากแบบอักษรของคุณกระจายอยู่ในโฟลเดอร์ย่อยต่างๆ จะช่วยคุณไม่ต้องเพิ่มแต่ละพาธด้วยตนเอง.

---

## โหลดเอกสาร Word ด้วยการตั้งค่าแบบอักษรแบบกำหนดเอง

เมื่อเตรียมตัวเลือกแล้ว การโหลดเอกสารก็ง่ายดาย คอนสตรัคเตอร์ `Document` รับพาธไฟล์และ `LoadOptions` ที่เราสร้างไว้.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**อะไรที่เกิดขึ้นเบื้องหลัง?**  
Aspose.Words จะทำการพาร์ส DOCX ตรวจสอบทุกการอ้างอิง `<w:font>` และปรึกษา `FontSettings` ที่คุณให้ไว้ หากไม่พบแบบอักษร จะสร้าง warning ประเภท `FontSubstitution` ตัวจัดการแบบกำหนดของเราที่จะแสดงต่อไปจะจับ warning เหล่านั้น.

---

## จัดการแบบอักษรที่หายไปด้วย Warning Callback

อินเทอร์เฟซ `IWarningCallback` ให้คุณตอบสนองต่อปัญหาใดๆ ที่เกิดขึ้นระหว่างการโหลด การนำไปใช้เป็นเรื่องง่าย:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

เมื่อเอกสารถูกโหลด ทุกแบบอักษรที่หายไปจะทำให้เกิดบรรทัดเช่น:

```
Font substituted: Arial -> Liberation Sans
```

**ทำไมคุณควรบันทึกสิ่งนี้:**  
ในสภาพแวดล้อมการผลิต คุณสามารถส่งต่อข้อความเหล่านี้ไปยังไฟล์หรือระบบ telemetry ทำให้ง่ายต่อการสังเกตว่าแบบอักษรใดที่คุณต้องบรรจุหรือขอใบอนุญาต.

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมคอนโซลที่รวมทุกอย่างไว้ด้วยกัน คัดลอกและวางลงในโปรเจกต์คอนโซล .NET Core ใหม่แล้วกด **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่า `input.docx` ใช้แบบอักษรที่คุณไม่มี):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

หากแบบอักษรทั้งหมดมีอยู่ คุณจะเห็นเพียงบรรทัดยืนยันสุดท้าย.

---

## คำถามทั่วไป & กรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าฉันต้องฝังแบบอักษรที่หายไปลงใน PDF?** | หลังจากโหลดแล้ว ให้เรียก `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` แล้วเปิดการฝังด้วย `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **ฉันสามารถปิดการแจ้งเตือนแทนการบันทึกได้หรือไม่?** | ได้—ตั้งค่า `loadOptions.WarningCallback = null;` หรือทำการนำ callback ไปใช้เพื่อเพิกเฉยต่อ warning ที่ไม่เกี่ยวกับแบบอักษร. |
| **วิธีนี้ทำงานกับไฟล์ `.doc` และ `.rtf` หรือไม่?** | แน่นอน. อ็อบเจ็กต์ `LoadOptions` เดียวกันใช้ได้กับทุกฟอร์แมตที่ Aspose.Words รองรับ. |
| **Callback นี้ปลอดภัยต่อการทำงานหลายเธรดหรือไม่?** | Callback ทำงานบนเธรดเดียวกับที่โหลดเอกสาร ดังนั้นคุณสามารถเขียนไปยังคอนโซลได้อย่างปลอดภัย สำหรับสถานการณ์หลายเธรด ให้ใช้คอลเลกชันแบบ concurrent หรือเฟรมเวิร์กการบันทึก. |

---

## เคล็ดลับระดับมืออาชีพ & สิ่งที่ควรระวัง

* **เคล็ดลับ:** หากคุณจัดส่งแบบอักษรที่ไม่ได้ติดตั้งบนเครื่องเป้าหมาย ให้เพิ่มมันลงในโฟลเดอร์ที่คุณส่งผ่านไปยัง `SetFontsFolder` สิ่งนี้รับประกันการเรนเดอร์ที่แน่นอน.  
* **ระวังเรื่องลิขสิทธิ์:** แบบอักษรบางตัวต้องการใบอนุญาตเชิงพาณิชย์สำหรับการฝัง ควรตรวจสอบ EULA ของแบบอักษรก่อนบรรจุ.  
* **หมายเหตุด้านประสิทธิภาพ:** การโหลดไลบรารีแบบอักษรขนาดใหญ่สามารถทำให้การพาร์สเอกสารช้าลง ควรรักษาโฟลเดอร์ให้เบา—รวมเฉพาะแบบอักษรที่คุณต้องการใช้จริง.  
* **กรณีขอบ:** เมื่อเอกสารอ้างอิงแบบอักษรด้วย *PostScript name* แทนชื่อครอบครัว Aspose.Words ยังสามารถแก้ไขได้ตราบใดที่ไฟล์แบบอักษรอยู่ในเส้นทางค้นหา.

---

## สรุป

ตอนนี้คุณมีรูปแบบที่ครบถ้วนและพร้อมใช้งานในระดับการผลิตสำหรับการใช้ **การตั้งค่าแบบอักษรแบบกำหนดเอง** ใน C# โดยการกำหนดค่า `LoadOptions` ลงทะเบียน warning callback และโดยอาจชี้ไปยังโฟลเดอร์แบบอักษรส่วนตัว คุณสามารถ **ตั้งค่าแบบอักษร**, **โหลดเนื้อหาเอกสาร Word** ได้อย่างเชื่อถือได้

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}