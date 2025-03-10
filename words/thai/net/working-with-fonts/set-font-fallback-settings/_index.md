---
title: ตั้งค่าฟอนต์สำรอง
linktitle: ตั้งค่าฟอนต์สำรอง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการตั้งค่า Font Fallback Settings ใน Aspose.Words สำหรับ .NET คำแนะนำที่ครอบคลุมนี้จะช่วยให้มั่นใจว่าอักขระทั้งหมดในเอกสารของคุณจะแสดงอย่างถูกต้อง
weight: 10
url: /th/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าฟอนต์สำรอง

## การแนะนำ

เมื่อทำงานกับเอกสารที่มีองค์ประกอบข้อความที่หลากหลาย เช่น ภาษาที่แตกต่างกันหรืออักขระพิเศษ สิ่งสำคัญคือต้องแน่ใจว่าองค์ประกอบเหล่านี้แสดงอย่างถูกต้อง Aspose.Words สำหรับ .NET นำเสนอฟีเจอร์อันทรงพลังที่เรียกว่า Font Fallback Settings ซึ่งช่วยในการกำหนดกฎสำหรับการแทนที่แบบอักษรเมื่อแบบอักษรดั้งเดิมไม่รองรับอักขระบางตัว ในคู่มือนี้ เราจะมาดูวิธีการตั้งค่า Font Fallback Settings โดยใช้ Aspose.Words สำหรับ .NET ในบทช่วยสอนแบบทีละขั้นตอน

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ โปรดแน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และ .NET framework
-  Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้งจาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: การตั้งค่าเช่น Visual Studio เพื่อเขียนและรันโค้ดของคุณ
-  เอกสารตัวอย่าง: มีเอกสารตัวอย่าง (เช่น`Rendering.docx`) พร้อมสำหรับการทดสอบแล้ว
- กฎการสำรองแบบอักษร XML: เตรียมไฟล์ XML ที่กำหนดกฎการสำรองแบบอักษร

## นำเข้าเนมสเปซ

ในการใช้ Aspose.Words คุณจำเป็นต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งจะทำให้สามารถเข้าถึงคลาสและวิธีการต่างๆ ที่จำเป็นสำหรับการประมวลผลเอกสารได้

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสาร

ขั้นแรก ให้กำหนดไดเรกทอรีที่จัดเก็บเอกสารของคุณ ซึ่งเป็นสิ่งสำคัญสำหรับการค้นหาและประมวลผลเอกสารของคุณ

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ขั้นตอนที่ 2: โหลดเอกสาร

 โหลดเอกสารของคุณลงใน Aspose.Words`Document` วัตถุ ขั้นตอนนี้ช่วยให้คุณสามารถทำงานกับเอกสารผ่านโปรแกรมได้

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ขั้นตอนที่ 3: กำหนดค่าการตั้งค่าแบบอักษร

 สร้างใหม่`FontSettings` วัตถุและโหลดการตั้งค่าแบบอักษรสำรองจากไฟล์ XML ไฟล์ XML นี้ประกอบด้วยกฎสำหรับแบบอักษรสำรอง

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## ขั้นตอนที่ 4: นำการตั้งค่าแบบอักษรไปใช้กับเอกสาร

 กำหนดค่าที่กำหนดไว้`FontSettings`ให้กับเอกสาร การดำเนินการนี้จะช่วยให้มั่นใจว่ากฎการสำรองแบบอักษรจะถูกนำไปใช้เมื่อแสดงผลเอกสาร

```csharp
doc.FontSettings = fontSettings;
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสาร การตั้งค่าแบบอักษรสำรองจะถูกใช้ในระหว่างการบันทึกเพื่อให้แน่ใจว่ามีการแทนที่แบบอักษรอย่างเหมาะสม

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## ไฟล์ XML: กฎการสำรองแบบอักษร

นี่คือตัวอย่างลักษณะของไฟล์ XML ของคุณที่กำหนดกฎการสำรองแบบอักษร:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## บทสรุป

หากทำตามขั้นตอนเหล่านี้ คุณจะสามารถตั้งค่าและใช้การตั้งค่า Font Fallback ใน Aspose.Words สำหรับ .NET ได้อย่างมีประสิทธิภาพ ซึ่งจะช่วยให้มั่นใจว่าเอกสารของคุณจะแสดงอักขระทั้งหมดได้อย่างถูกต้อง แม้ว่าแบบอักษรดั้งเดิมจะไม่รองรับอักขระบางตัวก็ตาม การนำการตั้งค่าเหล่านี้ไปใช้จะช่วยเพิ่มคุณภาพและความสามารถในการอ่านของเอกสารของคุณได้อย่างมาก

## คำถามที่พบบ่อย

### คำถามที่ 1: Font Fallback คืออะไร

Font Fallback เป็นคุณลักษณะที่ช่วยให้สามารถแทนที่แบบอักษรได้เมื่อแบบอักษรดั้งเดิมไม่รองรับอักขระบางตัว ช่วยให้แสดงองค์ประกอบข้อความทั้งหมดได้อย่างถูกต้อง

### คำถามที่ 2: ฉันสามารถระบุแบบอักษรสำรองหลายแบบได้หรือไม่

ใช่ คุณสามารถระบุแบบอักษรสำรองได้หลายแบบในกฎ XML Aspose.Words จะตรวจสอบแบบอักษรแต่ละตัวตามลำดับที่ระบุจนกว่าจะพบแบบอักษรที่รองรับอักขระนั้น

### คำถามที่ 3: ฉันสามารถดาวน์โหลด Aspose.Words สำหรับ .NET ได้ที่ไหน

 คุณสามารถดาวน์โหลดได้จาก[หน้าดาวน์โหลด Aspose](https://releases.aspose.com/words/net/).

### คำถามที่ 4: ฉันจะสร้างไฟล์ XML สำหรับกฎการสำรองแบบอักษรได้อย่างไร

คุณสามารถสร้างไฟล์ XML ได้โดยใช้โปรแกรมแก้ไขข้อความใดๆ ก็ได้ โดยควรใช้โครงสร้างตามที่แสดงไว้ในตัวอย่างที่ให้ไว้ในบทช่วยสอนนี้

### คำถามที่ 5: มีการรองรับ Aspose.Words หรือไม่

 ใช่ คุณสามารถหาการสนับสนุนได้ที่[ฟอรั่มสนับสนุน Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
