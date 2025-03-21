---
title: รวมแถว
linktitle: รวมแถว
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการรวมแถวจากหลายตารางเป็นหนึ่งโดยใช้ Aspose.Words สำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนของเรา
weight: 10
url: /th/net/programming-with-tables/combine-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# รวมแถว

## การแนะนำ

การรวมแถวจากหลายตารางเข้าเป็นตารางเดียวที่เชื่อมโยงกันอาจเป็นงานที่น่าปวดหัว แต่ด้วย Aspose.Words สำหรับ .NET จะทำให้ทุกอย่างเป็นเรื่องง่าย! คู่มือนี้จะแนะนำคุณตลอดกระบวนการ ทำให้คุณผสานตารางได้อย่างราบรื่น ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น คุณจะพบว่าบทช่วยสอนนี้มีประโยชน์อย่างยิ่ง มาเริ่มกันเลยและเปลี่ยนแถวที่กระจัดกระจายเหล่านี้ให้กลายเป็นตารางรวม

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1.  Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE อื่น ๆ ที่เข้ากันได้กับ .NET
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับ C# จะเป็นประโยชน์

 หากคุณยังไม่มี Aspose.Words สำหรับ .NET คุณสามารถรับได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือซื้อมัน[ที่นี่](https://purchase.aspose.com/buy) . หากมีคำถามใด ๆ[ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8) เป็นจุดเริ่มต้นที่ดี

## นำเข้าเนมสเปซ

ขั้นแรก คุณจะต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งจะช่วยให้คุณสามารถเข้าถึงคลาสและวิธีการ Aspose.Words ได้ โดยทำได้ดังนี้:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

ตอนนี้เราได้ตั้งค่าทุกอย่างเรียบร้อยแล้ว มาแบ่งกระบวนการออกเป็นขั้นตอนที่ทำตามได้ง่ายกัน

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

ขั้นตอนแรกคือโหลดเอกสาร Word ของคุณ เอกสารนี้ควรมีตารางที่คุณต้องการรวมเข้าด้วยกัน นี่คือโค้ดสำหรับโหลดเอกสาร:

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

 ในตัวอย่างนี้ให้แทนที่`"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางไปยังเอกสารของคุณ

## ขั้นตอนที่ 2: ระบุตาราง

 ขั้นต่อไป คุณต้องระบุตารางที่คุณต้องการรวมเข้าด้วยกัน Aspose.Words ช่วยให้คุณสามารถรับตารางจากเอกสารโดยใช้`GetChild` วิธีการมีดังนี้:

```csharp
Table firstTable = (Table) doc.GetChild(NodeType.Table, 0, true);
Table secondTable = (Table) doc.GetChild(NodeType.Table, 1, true);
```

ในโค้ดนี้ เราจะดึงตารางแรกและตารางที่สองจากเอกสาร

## ขั้นตอนที่ 3: ผนวกแถวจากตารางที่สองไปยังตารางแรก

ตอนนี้ถึงเวลาที่จะรวมแถวแล้ว เราจะผนวกแถวทั้งหมดจากตารางที่สองเข้ากับตารางแรก ซึ่งทำได้โดยใช้ลูป while ง่ายๆ:

```csharp
// ผนวกแถวทั้งหมดจากตารางที่สองไปยังตารางแรก
while (secondTable.HasChildNodes)
    firstTable.Rows.Add(secondTable.FirstRow);
```

ลูปนี้จะดำเนินต่อไปจนกระทั่งแถวทั้งหมดจากตารางที่สองจะถูกเพิ่มลงในตารางแรก

## ขั้นตอนที่ 4: ถอดโต๊ะตัวที่สองออก

 หลังจากผนวกแถวแล้ว ตารางที่สองจะไม่จำเป็นอีกต่อไป คุณสามารถลบออกได้โดยใช้`Remove` วิธี:

```csharp
secondTable.Remove();
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารที่แก้ไขแล้ว ขั้นตอนนี้จะช่วยให้แน่ใจว่าการเปลี่ยนแปลงของคุณถูกเขียนลงในไฟล์:

```csharp
doc.Save(dataDir + "WorkingWithTables.CombineRows.docx");
```

และเสร็จเรียบร้อย! คุณได้รวมแถวจากสองตารางเป็นหนึ่งเดียวสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET

## บทสรุป

การรวมแถวจากหลายตารางเป็นหนึ่งเดียวสามารถช่วยลดความซับซ้อนของงานประมวลผลเอกสารของคุณได้อย่างมาก ด้วย Aspose.Words สำหรับ .NET งานนี้จะกลายเป็นเรื่องง่ายและมีประสิทธิภาพ ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณสามารถรวมตารางและปรับปรุงเวิร์กโฟลว์ของคุณได้อย่างง่ายดาย

หากคุณต้องการข้อมูลเพิ่มเติมหรือมีคำถามใดๆ[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/) เป็นแหล่งข้อมูลที่ยอดเยี่ยม คุณยังสามารถสำรวจตัวเลือกการซื้อได้อีกด้วย[ที่นี่](https://purchase.aspose.com/buy) หรือรับ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อการทดสอบ

## คำถามที่พบบ่อย

### ฉันสามารถรวมตารางที่มีจำนวนคอลัมน์ต่างกันได้หรือไม่

ใช่ Aspose.Words ช่วยให้คุณรวมตารางเข้าด้วยกันได้แม้ว่าจะมีจำนวนคอลัมน์และความกว้างต่างกันก็ตาม

### เมื่อรวมการจัดรูปแบบของแถวเข้าด้วยกันจะเกิดอะไรขึ้น?

การจัดรูปแบบของแถวจะยังคงอยู่เมื่อมีการผนวกเข้ากับตารางแรก

### สามารถรวมตารางมากกว่าสองตารางเข้าด้วยกันได้หรือไม่

ใช่ คุณสามารถรวมตารางหลายตารางเข้าด้วยกันได้โดยทำซ้ำขั้นตอนสำหรับตารางเพิ่มเติมแต่ละตาราง

### ฉันสามารถทำให้กระบวนการนี้เป็นแบบอัตโนมัติสำหรับเอกสารหลายฉบับได้ไหม

แน่นอน! คุณสามารถสร้างสคริปต์เพื่อทำให้กระบวนการนี้เป็นแบบอัตโนมัติสำหรับเอกสารหลายฉบับได้

### ฉันจะได้รับความช่วยเหลือหากประสบปัญหาได้ที่ไหน?

 การ[ฟอรั่มสนับสนุน Aspose.Words](https://forum.aspose.com/c/words/8) เป็นสถานที่ที่ยอดเยี่ยมในการขอความช่วยเหลือและค้นหาวิธีแก้ไขปัญหาทั่วไป
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
