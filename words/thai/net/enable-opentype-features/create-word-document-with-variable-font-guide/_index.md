---
category: general
date: 2026-03-19
description: สร้างเอกสาร Word ด้วย Aspose.Words และฟอนต์แบบแปรผัน เรียนรู้วิธีเปลี่ยนน้ำหนักฟอนต์
  ตั้งความกว้างของฟอนต์ และกำหนดการแปรผันของฟอนต์ใน C#
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: th
og_description: สร้างเอกสาร Word ด้วยฟอนต์แบบแปรผันโดยใช้ Aspose.Words บทเรียนนี้จะแสดงวิธีโหลดฟอนต์,
  ปรับน้ำหนักฟอนต์, ตั้งความกว้างฟอนต์, และกำหนดการแปรผันของฟอนต์
og_title: สร้างเอกสาร Word ด้วยฟอนต์แบบแปรผัน – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Variable Font
title: สร้างเอกสาร Word ด้วยฟอนต์แบบแปรผัน – คู่มือ
url: /th/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ด้วยฟอนต์แบบตัวแปร – คู่มือ

เคยต้องการ **สร้างเอกสาร Word** ที่ใช้ฟอนต์แบบตัวแปรสมัยใหม่ แต่ไม่แน่ใจว่าจะเริ่มต้นอย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว ในหลายโครงการ—เช่นรายงานแบบไดนามิกหรือโบรชัวร์ที่สอดคล้องกับแบรนด์—การที่สามารถ **เปลี่ยนความหนาของฟอนต์** ได้ทันทีเป็นสิ่งที่เปลี่ยนเกมจริงๆ  

ในบทเรียนนี้เราจะพาคุณผ่านกระบวนการทั้งหมด: ตั้งแต่การโหลดฟอนต์แบบตัวแปรเข้าสู่ Aspose.Words, การตั้งค่าความหนาและความกว้างของฟอนต์, และสุดท้ายการบันทึกไฟล์ DOCX ที่ดูเหมือนกับที่คุณออกแบบไว้ ไม่ได้มีการอ้างอิงแบบคลุมเครือ เพียงโค้ดที่คุณสามารถคัดลอกไปใส่ในโปรเจกต์ C# ของคุณได้ทันที

## สิ่งที่คุณจะได้เรียนรู้

- วิธี **โหลดไฟล์ฟอนต์แบบตัวแปร** เข้าสู่ Aspose.Words ด้วย `FontSettings`
- ไวยากรณ์สำหรับ **กำหนดแกนการเปลี่ยนแปลงฟอนต์** เช่น `wght` (weight) และ `wdth` (width)
- วิธี **ตั้งค่าความกว้างของฟอนต์** และ **เปลี่ยนความหนาของฟอนต์** บน `Run` เดียว
- เคล็ดลับการแก้ไขปัญหาที่พบบ่อย (glyph หาย, เส้นทางโฟลเดอร์ไม่ถูกต้อง ฯลฯ)
- ตัวอย่างที่ทำงานได้ครบถ้วนที่คุณสามารถคัดลอก‑วางและทดสอบได้ทันที

> **Prerequisites**: .NET 6+ (หรือ .NET Framework 4.6+), Aspose.Words for .NET ที่ติดตั้งผ่าน NuGet, และไฟล์ฟอนต์แบบตัวแปรเช่น *RobotoFlex.ttf* ที่วางไว้ในโฟลเดอร์ *Fonts* ภายในเครื่อง

---

## ขั้นตอนที่ 1 – โหลดฟอนต์แบบตัวแปรเข้าสู่ Aspose.Words

ก่อนอื่นเราต้องบอก Aspose.Words ว่าจะมองหาไฟล์ฟอนต์ที่กำหนดเองของเราที่ไหน คลาส `FontSettings` จะทำหน้าที่หลักนี้ให้  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**ทำไมเรื่องนี้ถึงสำคัญ**: หากไม่ได้ลงทะเบียนโฟลเดอร์ Aspose.Words จะย้อนกลับไปใช้ฟอนต์ระบบและจะละเลยข้อมูลการเปลี่ยนแปลง OpenType ที่คุณพยายามนำไปใช้ในภายหลัง การชี้ไปที่ไดเรกทอรีเฉพาะจะทำให้มั่นใจว่า *RobotoFlex* (หรือฟอนต์แบบตัวแปรใด ๆ) จะถูกพบทุกครั้งที่โค้ดทำงาน

> **Pro tip**: ตั้งค่าพารามิเตอร์ตัวที่สองของ `SetFontsFolder` เป็น `true` หากคุณต้องการให้ Aspose ค้นหาในโฟลเดอร์ย่อยด้วย วิธีนี้ช่วยได้เมื่อคุณจัดระเบียบฟอนต์ตามสไตล์หรือความหนา

---

## ขั้นตอนที่ 2 – สร้างเอกสารใหม่และเพิ่มข้อความตัวอย่าง

ตอนนี้เอนจินฟอนต์รู้แล้วว่าต้องมองหาไฟล์ที่ไหน เราจึงสร้าง `Document` เปล่าและแทรกย่อหน้าที่มี `Run`  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**สิ่งที่เกิดขึ้น**: `Run` แทนส่วนข้อความต่อเนื่องที่มีการจัดรูปแบบเดียวกัน การสร้างมันก่อนทำให้ตรรกะการจัดรูปแบบแยกออกจากกัน—เหมาะสำหรับการนำแกนการเปลี่ยนแปลงต่าง ๆ ไปใช้กับ `Run` แยกกันในภายหลังหากต้องการ

---

## ขั้นตอนที่ 3 – กำหนดแกนการเปลี่ยนแปลงที่ต้องการ (Weight & Width)

ฟอนต์แบบตัวแปรเปิดเผย *แกน* ที่คุณสามารถปรับได้ขณะรัน แกนที่พบบ่อยที่สุดสองแกนคือ `wght` (ความหนาของฟอนต์) และ `wdth` (ความกว้างของฟอนต์) Aspose.Words จัดการสิ่งนี้ด้วยคอลเลกชัน `OpenTypeFontVariation`

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**ทำไมต้องใช้ตัวเลขเหล่านี้**: ตามสเปค OpenType, `wght` มีช่วงตั้งแต่น้ำหนักขั้นต่ำถึงสูงสุดของฟอนต์ (มักอยู่ที่ 100–900) ค่า **700** จะให้ลักษณะเป็นตัวหนา `wdth` ทำงานคล้ายกัน; **100** หมายถึงความกว้างเริ่มต้น (ปกติ) ส่วนค่าต่ำกว่า 100 จะทำให้ glyphs กระชับลง

> **Edge case**: ฟอนต์แบบตัวแปรบางตัวอาจไม่รองรับแกนที่ระบุ หากคุณส่งแท็กที่ไม่สนับสนุน Aspose จะละเลยโดยไม่มีข้อความเตือน ตรวจสอบสเปคของฟอนต์เสมอ (มักพบในเมตาดาต้าไฟล์ `.ttf` หรือ `.otf`)

---

## ขั้นตอนที่ 4 – นำการเปลี่ยนแปลงไปใช้กับ Run ด้วยชื่อฟอนต์

ตอนนี้เราจะผูกข้อมูลการเปลี่ยนแปลงกับข้อความจริง คลาส `FontInfo` จะเก็บชื่อฟอนต์และคอลเลกชันแกน

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**คำอธิบาย**: การตั้งค่า `FontInfo` ทำให้เราข้ามการใช้คุณสมบัติ `Font.Name` ปกติและส่งข้อมูลการกำหนดฟอนต์ที่ครบถ้วนให้กับเอนจิน นี่เป็นวิธีเดียวที่บอก Aspose.Words ให้ใช้ฟอนต์แบบตัวแปรพร้อมแกนที่กำหนดเอง

> **Common mistake**: ลืมใส่ชื่อฟอนต์ที่ตรงกับชื่อในไฟล์ฟอนต์ (`RobotoFlex` ในตัวอย่างนี้) การพิมพ์ผิดจะทำให้ Aspose ย้อนกลับไปใช้ฟอนต์เริ่มต้นและการเปลี่ยนแปลงของคุณจะหายไป

---

## ขั้นตอนที่ 5 – บันทึกเอกสารและตรวจสอบผลลัพธ์

สุดท้ายให้เขียนเอกสารลงดิสก์ ไฟล์ DOCX ที่สร้างขึ้นจะมีคำสั่งฟอนต์แบบตัวแปรซึ่ง Microsoft Word (2016+) สามารถแสดงผลได้อย่างถูกต้อง

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

เปิดไฟล์ที่ได้ใน Word, เลือกข้อความและดูที่กล่องโต้ตอบ **Font** คุณควรเห็น *Roboto Flex* ปรากฏอยู่และข้อความจะดูหนากว่าข้อความรอบข้าง—ตรงกับการตั้งค่า `wght = 700` ที่เรากำหนดไว้

> **Verification tip**: หากข้อความไม่เปลี่ยนแปลง ตรวจสอบอีกครั้งว่าฟอนต์ไฟล์จริง ๆ รองรับแกน `wght` หรือไม่ ฟอนต์ “แบบตัวแปร” บางตัวอาจเปิดเผยเฉพาะ `ital` (italic) หรือ `opsz` (optical size) เท่านั้น

---

## ตัวเลือก: เพิ่มการเปลี่ยนแปลงอื่น – ปรับความกว้างแบบไดนามิก

หากคุณต้องการ *ตั้งค่าความกว้างของฟอนต์* แตกต่างกันสำหรับย่อหน้าอื่น เพียงทำซ้ำขั้นตอน 3‑4 ด้วยคอลเลกชัน `OpenTypeFontVariation` ใหม่

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

ตอนนี้คุณมีสอง `Run`—หนึ่งเป็นตัวหนา อีกหนึ่งกว้างเล็กน้อย—แสดงให้เห็นทั้ง **การเปลี่ยนความหนาของฟอนต์** และ **การตั้งค่าความกว้างของฟอนต์** ในเอกสารเดียวกัน

---

## ตัวอย่างทำงานเต็มรูปแบบ

คัดลอกโค้ดด้านล่างไปวางในแอปคอนโซลใหม่ (`Program.cs`) แล้วรัน ตรวจสอบให้แน่ใจว่าโฟลเดอร์ `Fonts` มีไฟล์ `RobotoFlex.ttf` (หรือฟอนต์แบบตัวแปรอื่นที่คุณต้องการ)

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง**: ไฟล์ `VariableFont.docx` ที่คำว่า “Variable‑weight text” ปรากฏเป็นตัวหนา เนื่องจากแกน `wght = 700` พร้อมยังคงความกว้างเริ่มต้นไว้

---

## คำถามที่พบบ่อย & กรณีขอบเขต

| Question | Answer |
|----------|--------|
| *What if the font isn’t found?* | ตรวจสอบเส้นทางโฟลเดอร์, ให้แน่ใจว่าไฟล์มีชื่อตรงกันและกระบวนการมีสิทธิ์อ่าน คุณยังสามารถเรียก `fontSettings.GetFonts()` เพื่อแสดงรายการฟอนต์ที่ตรวจพบ |
| *Can I combine multiple runs with different variations?* | ได้เลย แต่ละ `Run` สามารถมี `FontInfo` ของตนเอง เพียงทำซ้ำขั้นตอน 3‑4 สำหรับแต่ละ run |
| *Do older versions of Word support variable fonts?* | Word 2016 (Build 16.0.8001) เริ่มรองรับพื้นฐาน หากคุณตั้งเป้าหมายเวอร์ชันเก่าเอกสารจะย้อนกลับไปใช้ฟอนต์สถิตที่ใกล้เคียงที่สุด |
| *Is there a limit to how many axes I can set?* | คุณสามารถตั้งค่าแกนได้ตามจำนวนที่ฟอนต์กำหนด แท็กที่พบบ่อยคือ `wght`, `wdth`, `ital`, `opsz`, `GRAD` การส่งแท็กที่ไม่สนับสนุนจะไม่มีผล |
| *How do I debug missing glyphs?* | ใช้ `FontSettings.GetFontSources()` เพื่อตรวจสอบฟอนต์ที่โหลด และ `FontInfo.HasGlyph(char)` เพื่อตรวจสอบ glyph ของอักขระแต่ละตัว |

---

## สรุป

ในไม่กี่ขั้นตอน เราได้แสดง **วิธีสร้างเอกสาร Word** ที่ใช้พลังของฟอนต์แบบตัวแปร ทำให้คุณ **เปลี่ยนความหนาของฟอนต์**, **ตั้งค่าความกว้างของฟอนต์**, **โหลดไฟล์ฟอนต์แบบตัวแปร**, และ **กำหนดแกนการเปลี่ยนแปลงฟอนต์** ทั้งหมดนี้ด้วย Aspose.Words for .NET  

แนวคิดหลักง่าย ๆ: ลงทะเบียนโฟลเดอร์ฟอนต์, กำหนดแกนที่ต้องการ, ผูกกับ `Run`, แล้วบันทึก จากนั้นคุณสามารถขยายเทคนิคนี้ไปยังส่วนต่าง ๆ ทั้งส่วนหัว, ตาราง, หรือแม้กระทั่งสร้างรายงานที่สอดคล้องกับแบรนด์โดยอัตโนมัติ

**Next steps**: ลองสลับ `RobotoFlex` กับฟอนต์แบบตัวแปรอื่น, ทดลองแกน `ital` (italic), หรือสร้างไฟล์ PDF ของเอกสารเดียวกันโดยใช้ Aspose.PDF รูปแบบเดียวกัน—โหลด, กำหนด, นำไปใช้, บันทึก

ขอให้โค้ดของคุณสนุกและเพลิดเพลินกับความยืดหยุ่นที่ฟอนต์แบบตัวแปรนำมาสู่โครงการอัตโนมัติของ Word!  

<img src="variable-font-demo.png" alt="สร้างเอกสาร Word ด้วยฟอนต์แบบตัวแปร ตัวอย่าง">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}