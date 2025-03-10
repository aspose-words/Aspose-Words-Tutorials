---
title: ตรวจสอบเอฟเฟกต์ข้อความ DrawingML
linktitle: ตรวจสอบเอฟเฟกต์ข้อความ DrawingML
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการตรวจสอบเอฟเฟกต์ข้อความ DrawingML ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคำแนะนำทีละขั้นตอนโดยละเอียดของเรา ปรับปรุงเอกสารของคุณได้อย่างง่ายดาย
weight: 10
url: /th/net/working-with-fonts/check-drawingml-text-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจสอบเอฟเฟกต์ข้อความ DrawingML

## การแนะนำ

ยินดีต้อนรับสู่บทช่วยสอนโดยละเอียดอีกบทหนึ่งเกี่ยวกับการทำงานกับ Aspose.Words สำหรับ .NET! วันนี้เราจะมาเจาะลึกในโลกอันน่าตื่นตาตื่นใจของเอฟเฟกต์ข้อความ DrawingML ไม่ว่าคุณจะต้องการปรับปรุงเอกสาร Word ของคุณด้วยเงา การสะท้อน หรือเอฟเฟกต์ 3 มิติ คู่มือนี้จะแสดงวิธีการตรวจสอบเอฟเฟกต์ข้อความเหล่านี้ในเอกสารของคุณโดยใช้ Aspose.Words สำหรับ .NET มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มบทช่วยสอน มีข้อกำหนดเบื้องต้นบางประการที่คุณจะต้องมี:

-  ไลบรารี Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: คุณควรมีการตั้งค่าสภาพแวดล้อมการพัฒนา เช่น Visual Studio
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# เล็กน้อยจะเป็นประโยชน์

## นำเข้าเนมสเปซ

ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็น เนมสเปซเหล่านี้จะช่วยให้คุณเข้าถึงคลาสและวิธีการที่จำเป็นในการจัดการเอกสาร Word และตรวจสอบเอฟเฟกต์ข้อความ DrawingML

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## คู่มือทีละขั้นตอนในการตรวจสอบเอฟเฟกต์ข้อความของ DrawingML

ตอนนี้มาแบ่งขั้นตอนออกเป็นหลายขั้นตอน เพื่อให้สามารถปฏิบัติตามได้ง่ายขึ้น

## ขั้นตอนที่ 1: โหลดเอกสาร

ขั้นตอนแรกคือโหลดเอกสาร Word ที่คุณต้องการตรวจสอบเอฟเฟกต์ข้อความ DrawingML 

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

โค้ดสั้นๆ นี้โหลดเอกสารชื่อ "DrawingML text effects.docx" จากไดเร็กทอรีที่คุณระบุ

## ขั้นตอนที่ 2: เข้าถึงคอลเลกชันการทำงาน

ต่อไป เราต้องเข้าถึงคอลเล็กชันการรันในย่อหน้าแรกของเอกสาร การรันคือส่วนของข้อความที่มีการจัดรูปแบบเดียวกัน

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

บรรทัดโค้ดนี้จะดึงข้อมูลการทำงานจากย่อหน้าแรกในส่วนแรกของเอกสาร

## ขั้นตอนที่ 3: รับแบบอักษรของการรันครั้งแรก

ตอนนี้ เราจะได้คุณสมบัติแบบอักษรของการเรียกใช้ครั้งแรกในคอลเล็กชันการเรียกใช้ ซึ่งจะช่วยให้เราตรวจสอบเอฟเฟกต์ข้อความ DrawingML ต่างๆ ที่ใช้กับข้อความได้

```csharp
Font runFont = runs[0].Font;
```

## ขั้นตอนที่ 4: ตรวจสอบเอฟเฟกต์ข้อความ DrawingML

ในที่สุด เราก็สามารถตรวจสอบเอฟเฟ็กต์ข้อความ DrawingML ต่างๆ เช่น เงา เอฟเฟกต์ 3D การสะท้อน โครงร่าง และเติม

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

 บรรทัดโค้ดเหล่านี้จะพิมพ์ออกมา`true` หรือ`false` ขึ้นอยู่กับว่าเอฟเฟกต์ข้อความ DrawingML เฉพาะแต่ละอันจะถูกนำไปใช้กับฟอนต์ของการรันหรือไม่

## บทสรุป

ขอแสดงความยินดี! คุณเพิ่งเรียนรู้วิธีการตรวจสอบเอฟเฟกต์ข้อความ DrawingML ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์อันทรงพลังนี้ช่วยให้คุณตรวจจับและจัดการการจัดรูปแบบข้อความที่ซับซ้อนด้วยโปรแกรม ทำให้คุณควบคุมงานประมวลผลเอกสารของคุณได้ดียิ่งขึ้น


## คำถามที่พบบ่อย

### เอฟเฟกต์ข้อความ DrawingML คืออะไร
เอฟเฟกต์ข้อความ DrawingML เป็นตัวเลือกการจัดรูปแบบข้อความขั้นสูงในเอกสาร Word รวมถึงเงา เอฟเฟกต์ 3 มิติ การสะท้อน โครงร่าง และการเติม

### ฉันสามารถใช้เอฟเฟ็กต์ข้อความ DrawingML โดยใช้ Aspose.Words สำหรับ .NET ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET ช่วยให้คุณตรวจสอบและใช้เอฟเฟ็กต์ข้อความ DrawingML ได้ด้วยโปรแกรม

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?
 ใช่ Aspose.Words สำหรับ .NET ต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ คุณสามารถขอรับใบอนุญาตได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อการประเมินผล

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) ทดลองใช้ Aspose.Words สำหรับ .NET ก่อนซื้อ

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 คุณสามารถค้นหาเอกสารรายละเอียดได้ที่[หน้าเอกสาร Aspose.Words สำหรับ .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
