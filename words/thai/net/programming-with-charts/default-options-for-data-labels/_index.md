---
title: ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ
linktitle: ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิโดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อสร้างและปรับแต่งแผนภูมิได้อย่างง่ายดาย
weight: 10
url: /th/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ

## การแนะนำ

สวัสดี! คุณตื่นเต้นที่จะได้ก้าวเข้าสู่โลกแห่งการทำงานอัตโนมัติของเอกสารหรือไม่ วันนี้ เราจะมาสำรวจวิธีการใช้ Aspose.Words สำหรับ .NET เพื่อสร้างเอกสารที่สวยงามด้วยโปรแกรม Aspose.Words เป็นไลบรารีอันทรงพลังที่ช่วยให้คุณสามารถจัดการเอกสาร Word ได้อย่างง่ายดาย และในบทช่วยสอนนี้ เราจะเน้นที่การตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือมือใหม่ คู่มือนี้จะแนะนำคุณในแต่ละขั้นตอนเพื่อให้คุณสามารถใช้งานได้อย่างรวดเร็ว

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม เรามาตรวจสอบกันก่อนว่าคุณมีทุกอย่างที่จำเป็นในการปฏิบัติตามบทช่วยสอนนี้แล้ว นี่คือรายการตรวจสอบโดยย่อ:

- Visual Studio หรือ IDE อื่นๆ ที่เข้ากันได้กับ .NET: นี่คือที่ที่คุณจะเขียนและรันโค้ดของคุณ
-  Aspose.Words สำหรับ .NET: คุณสามารถ[ดาวน์โหลดเวอร์ชั่นล่าสุด](https://releases.aspose.com/words/net/) และติดตั้งไว้ในโครงการของคุณ
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#: แม้ว่าคู่มือนี้เหมาะสำหรับผู้เริ่มต้น แต่ความคุ้นเคยกับ C# เล็กน้อยก็จะเป็นประโยชน์
- ติดตั้ง .NET Framework แล้ว: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องของคุณแล้ว
-  ใบอนุญาตชั่วคราวสำหรับ Aspose.Words: รับอันหนึ่ง[ที่นี่](https://purchase.aspose.com/temporary-license/) เพื่อปลดล็อคฟังก์ชั่นเต็มรูปแบบ

เมื่อคุณได้จัดเตรียมข้อกำหนดเบื้องต้นเหล่านี้เรียบร้อยแล้ว เราก็พร้อมที่จะเริ่มดำเนินการ!

## นำเข้าเนมสเปซ

ขั้นแรก ให้ตั้งค่าโครงการและนำเข้าเนมสเปซที่จำเป็นก่อน เนมสเปซเหล่านี้มีความสำคัญต่อการเข้าถึงฟังก์ชัน Aspose.Words

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## ขั้นตอนที่ 1: สร้างเอกสารใหม่


 การเดินทางเริ่มต้นด้วยการสร้างเอกสารใหม่และเริ่มต้นใช้งาน`DocumentBuilder` . การ`DocumentBuilder` คลาสนี้มีชุดวิธีการสำหรับจัดการเนื้อหาเอกสารได้อย่างง่ายดาย

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

// สร้างเอกสารใหม่
Document doc = new Document();

// เริ่มต้นใช้งาน DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### คำอธิบาย

 ในขั้นตอนนี้ เราได้ตั้งค่าเอกสารและโปรแกรมสร้างที่เราจะใช้ในการแทรกและจัดรูปแบบเนื้อหาของเรา`dataDir` ตัวแปรเก็บเส้นทางที่เราจะบันทึกเอกสารสุดท้ายของเรา

## ขั้นตอนที่ 2: แทรกแผนภูมิ

 ต่อไปเราจะเพิ่มแผนภูมิวงกลมลงในเอกสารของเรา`InsertChart` วิธีการของ`DocumentBuilder` คลาสนี้ทำให้เรื่องนี้ง่ายสุดๆ

```csharp
// แทรกแผนภูมิวงกลม
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// เข้าถึงวัตถุแผนภูมิ
Chart chart = shape.Chart;
```

### คำอธิบาย

ที่นี่ เรากำลังแทรกแผนภูมิวงกลมลงในเอกสารของเรา`InsertChart` วิธีการนี้ต้องการประเภทแผนภูมิ ความกว้าง และความสูงเป็นพารามิเตอร์ หลังจากแทรกแผนภูมิแล้ว เราจะเข้าถึงวัตถุแผนภูมิเพื่อจัดการเพิ่มเติม

## ขั้นตอนที่ 3: ปรับแต่งชุดแผนภูมิ

ตอนนี้ เราจะล้างชุดข้อมูลที่มีอยู่ทั้งหมดในแผนภูมิ และเพิ่มชุดข้อมูลที่กำหนดเอง ชุดข้อมูลนี้จะแสดงจุดข้อมูลของเรา

```csharp
// ล้างชุดแผนภูมิที่มีอยู่
chart.Series.Clear();

// เพิ่มซีรี่ส์ใหม่ลงในแผนภูมิ
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### คำอธิบาย

ในขั้นตอนนี้ เราจะตรวจสอบให้แน่ใจว่าแผนภูมิของเราว่างเปล่าโดยการล้างชุดข้อมูลที่มีอยู่ก่อนหน้านี้ จากนั้น เราจะเพิ่มชุดข้อมูลใหม่ที่มีหมวดหมู่และค่าที่กำหนดเอง ซึ่งจะแสดงในแผนภูมิวงกลมของเรา

## ขั้นตอนที่ 4: ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูล

ป้ายข้อมูลมีความสำคัญอย่างยิ่งในการทำให้แผนภูมิของคุณมีข้อมูลที่เป็นประโยชน์ เราจะตั้งค่าตัวเลือกเพื่อแสดงเปอร์เซ็นต์ ค่า และปรับแต่งตัวคั่น

```csharp
// เข้าถึงคอลเลกชันป้ายข้อมูล
ChartDataLabelCollection labels = series.DataLabels;

// ตั้งค่าตัวเลือกป้ายข้อมูล
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### คำอธิบาย

 ที่นี่เราจะเข้าถึง`DataLabels`คุณสมบัติของซีรีส์ของเราในการปรับแต่งลักษณะและข้อมูลที่แสดงบนป้ายข้อมูลแต่ละป้าย เราได้เลือกที่จะแสดงทั้งเปอร์เซ็นต์และค่า ซ่อนเส้นผู้นำ และตั้งค่าตัวคั่นแบบกำหนดเอง

## ขั้นตอนที่ 5: บันทึกเอกสาร

ในที่สุด เราจะบันทึกเอกสารของเราไปยังไดเร็กทอรีที่ระบุ ขั้นตอนนี้จะช่วยให้มั่นใจว่าการเปลี่ยนแปลงทั้งหมดของเราจะถูกเขียนลงในไฟล์

```csharp
// บันทึกเอกสาร
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### คำอธิบาย

 ในขั้นตอนสุดท้ายนี้ เราจะบันทึกเอกสารของเราโดยใช้`Save` วิธีการ เอกสารจะถูกบันทึกไว้ในไดเรกทอรีที่ระบุโดย`dataDir`โดยมีชื่อว่า "WorkingWithCharts.DefaultOptionsForDataLabels.docx"

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้สร้างเอกสาร Word ที่มีแผนภูมิวงกลมที่กำหนดเองได้สำเร็จโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การสร้างและจัดการเอกสารโดยอัตโนมัติเป็นเรื่องง่าย ช่วยประหยัดเวลาและความพยายามของคุณ ไม่ว่าคุณจะสร้างรายงาน ใบแจ้งหนี้ หรือเอกสารประเภทอื่นใด Aspose.Words ก็ช่วยคุณได้

 รู้สึกอิสระที่จะสำรวจ[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/) เพื่อดูคุณสมบัติและตัวอย่างเพิ่มเติม ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.Words ได้ฟรีหรือไม่?
คุณสามารถใช้ Aspose.Words ได้ฟรีด้วย[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หรือสำรวจคุณสมบัติต่างๆ โดยใช้[ทดลองใช้งานฟรี](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words ได้อย่างไร
 คุณสามารถรับการสนับสนุนได้ผ่านทาง[ฟอรั่มสนับสนุน Aspose.Words](https://forum.aspose.com/c/words/8).

### ฉันสามารถเพิ่มแผนภูมิประเภทอื่นได้หรือไม่
 ใช่ Aspose.Words รองรับแผนภูมิประเภทต่างๆ เช่น แผนภูมิแท่ง แผนภูมิเส้น และแผนภูมิคอลัมน์ ตรวจสอบ[เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับรายละเอียดเพิ่มเติม

### Aspose.Words เข้ากันได้กับ .NET Core ได้หรือไม่
 ใช่ Aspose.Words เข้ากันได้กับ .NET Core คุณสามารถค้นหาข้อมูลเพิ่มเติมได้ใน[เอกสารประกอบ](https://reference.aspose.com/words/net/).

### ฉันสามารถซื้อใบอนุญาตสำหรับ Aspose.Words ได้อย่างไร?
 คุณสามารถซื้อใบอนุญาตได้จาก[ร้านอาสโพเซ่](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
