---
title: รับระยะห่างระหว่างตารางกับข้อความโดยรอบ
linktitle: รับระยะห่างระหว่างตารางกับข้อความโดยรอบ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการดึงข้อมูลระยะห่างระหว่างตารางและข้อความโดยรอบในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปรับปรุงเค้าโครงเอกสารของคุณด้วยคู่มือนี้
weight: 10
url: /th/net/programming-with-table-styles-and-formatting/get-distance-between-table-surrounding-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# รับระยะห่างระหว่างตารางกับข้อความโดยรอบ

## การแนะนำ

ลองนึกภาพว่าคุณกำลังเตรียมรายงานที่สวยงามหรือเอกสารสำคัญ และคุณต้องการให้ตารางของคุณดูเหมาะสม คุณต้องแน่ใจว่ามีช่องว่างเพียงพอระหว่างตารางและข้อความรอบๆ ตาราง ซึ่งจะทำให้เอกสารอ่านง่ายและดูน่าสนใจ ด้วยการใช้ Aspose.Words สำหรับ .NET คุณสามารถเรียกค้นและปรับระยะห่างเหล่านี้ได้อย่างง่ายดายด้วยโปรแกรม บทช่วยสอนนี้จะแนะนำคุณตลอดขั้นตอนต่างๆ เพื่อให้บรรลุเป้าหมายนี้ ทำให้เอกสารของคุณโดดเด่นด้วยความเป็นมืออาชีพยิ่งขึ้น

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการแล้ว:

1.  ไลบรารี Aspose.Words สำหรับ .NET: คุณต้องติดตั้งไลบรารี Aspose.Words สำหรับ .NET หากคุณยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดจาก[การเปิดตัว Aspose](https://releases.aspose.com/words/net/) หน้าหนังสือ.
2. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนาที่ทำงานโดยมีการติดตั้ง .NET Framework Visual Studio เป็นตัวเลือกที่ดี
3. เอกสารตัวอย่าง: เอกสาร Word (.docx) ที่มีตารางอย่างน้อยหนึ่งตารางเพื่อทดสอบโค้ด

## นำเข้าเนมสเปซ

ขั้นแรก ให้เรานำเข้าเนมสเปซที่จำเป็นเข้าสู่โปรเจ็กต์ของคุณก่อน ซึ่งจะทำให้คุณสามารถเข้าถึงคลาสและวิธีการที่จำเป็นในการจัดการเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ได้

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

ตอนนี้เรามาแบ่งขั้นตอนออกเป็นขั้นตอนที่ทำตามได้ง่าย ๆ เราจะครอบคลุมทุกอย่างตั้งแต่การโหลดเอกสารไปจนถึงการดึงข้อมูลระยะทางรอบ ๆ โต๊ะของคุณ

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

 ขั้นตอนแรกคือโหลดเอกสาร Word ของคุณลงใน Aspose.Words`Document` วัตถุ วัตถุนี้แสดงถึงเอกสารทั้งหมด

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

// โหลดเอกสาร
Document doc = new Document(dataDir + "Tables.docx");
```

## ขั้นตอนที่ 2: เข้าถึงตาราง

 ขั้นต่อไป คุณต้องเข้าถึงตารางภายในเอกสารของคุณ`GetChild` วิธีการนี้ช่วยให้คุณดึงข้อมูลตารางแรกที่พบในเอกสารได้

```csharp
// รับตารางแรกในเอกสาร
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## ขั้นตอนที่ 3: ดึงค่าระยะทาง

ตอนนี้คุณมีตารางแล้ว ถึงเวลาหาค่าระยะห่าง ค่าเหล่านี้แสดงถึงช่องว่างระหว่างตารางและข้อความโดยรอบจากแต่ละด้าน ได้แก่ ด้านบน ด้านล่าง ด้านซ้าย และด้านขวา

```csharp
// รับระยะห่างระหว่างตารางและข้อความโดยรอบ
Console.WriteLine("\nGet distance between table left, right, bottom, top and the surrounding text.");
Console.WriteLine("Distance from Top: " + table.DistanceTop);
Console.WriteLine("Distance from Bottom: " + table.DistanceBottom);
Console.WriteLine("Distance from Right: " + table.DistanceRight);
Console.WriteLine("Distance from Left: " + table.DistanceLeft);
```

## ขั้นตอนที่ 4: แสดงระยะทาง

ในที่สุด คุณสามารถแสดงระยะทางได้ ซึ่งจะช่วยให้คุณตรวจสอบระยะห่างและปรับเปลี่ยนตามความจำเป็นเพื่อให้แน่ใจว่าตารางของคุณดูสมบูรณ์แบบในเอกสาร

```csharp
// แสดงระยะทาง
Console.WriteLine("Distance from Top: " + table.DistanceTop);
Console.WriteLine("Distance from Bottom: " + table.DistanceBottom);
Console.WriteLine("Distance from Right: " + table.DistanceRight);
Console.WriteLine("Distance from Left: " + table.DistanceLeft);
```

## บทสรุป

และแล้วคุณก็ทำได้! ด้วยการทำตามขั้นตอนเหล่านี้ คุณจะสามารถดึงข้อมูลระยะห่างระหว่างตารางและข้อความโดยรอบในเอกสาร Word ของคุณได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET เทคนิคที่เรียบง่ายแต่ทรงพลังนี้ช่วยให้คุณปรับแต่งเค้าโครงเอกสารของคุณให้อ่านง่ายขึ้นและดึงดูดสายตามากขึ้น ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถปรับระยะทางตามโปรแกรมได้หรือไม่
 ใช่ คุณสามารถปรับระยะทางโดยใช้โปรแกรม Aspose.Words โดยตั้งค่า`DistanceTop`, `DistanceBottom`, `DistanceRight` , และ`DistanceLeft` คุณสมบัติของ`Table` วัตถุ.

### จะเกิดอะไรขึ้นหากเอกสารของฉันมีตารางหลายตาราง?
 คุณสามารถวนซ้ำผ่านโหนดย่อยของเอกสารและใช้วิธีการเดียวกันกับแต่ละตารางได้ ใช้`GetChildNodes(NodeType.Table, true)` เพื่อรับตารางทั้งหมด

### ฉันสามารถใช้ Aspose.Words กับ .NET Core ได้หรือไม่
แน่นอน! Aspose.Words รองรับ .NET Core และคุณสามารถใช้โค้ดเดียวกันนี้กับโปรเจ็กต์ .NET Core ได้โดยมีการปรับเปลี่ยนเล็กน้อย

### ฉันจะติดตั้ง Aspose.Words สำหรับ .NET ได้อย่างไร?
คุณสามารถติดตั้ง Aspose.Words สำหรับ .NET ผ่านตัวจัดการแพ็กเกจ NuGet ใน Visual Studio เพียงค้นหา "Aspose.Words" และติดตั้งแพ็กเกจ

### มีข้อจำกัดใด ๆ เกี่ยวกับประเภทเอกสารที่รองรับโดย Aspose.Words หรือไม่
 Aspose.Words รองรับรูปแบบเอกสารหลากหลาย เช่น DOCX, DOC, PDF, HTML และอื่นๆ ตรวจสอบ[เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับรายการรูปแบบที่รองรับทั้งหมด
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
