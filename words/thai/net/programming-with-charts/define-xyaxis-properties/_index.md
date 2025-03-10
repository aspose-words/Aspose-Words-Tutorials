---
title: กำหนดคุณสมบัติของแกน XY ในแผนภูมิ
linktitle: กำหนดคุณสมบัติของแกน XY ในแผนภูมิ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีกำหนดคุณสมบัติแกน XY ในแผนภูมิโดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้ เหมาะสำหรับนักพัฒนา .NET
weight: 10
url: /th/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กำหนดคุณสมบัติของแกน XY ในแผนภูมิ

## การแนะนำ

แผนภูมิเป็นเครื่องมือที่มีประสิทธิภาพสำหรับการแสดงภาพข้อมูล เมื่อคุณจำเป็นต้องสร้างเอกสารระดับมืออาชีพด้วยแผนภูมิแบบไดนามิก Aspose.Words สำหรับ .NET เป็นไลบรารีที่ทรงคุณค่า บทความนี้จะแนะนำคุณเกี่ยวกับกระบวนการกำหนดคุณสมบัติแกน XY ในแผนภูมิโดยใช้ Aspose.Words สำหรับ .NET โดยจะแบ่งขั้นตอนต่างๆ ออกเป็นส่วนๆ เพื่อให้แน่ใจว่ามีความชัดเจนและเข้าใจง่าย

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด มีข้อกำหนดเบื้องต้นบางประการที่คุณต้องมี:

1. Aspose.Words สำหรับ .NET: ตรวจสอบว่าคุณมีไลบรารี Aspose.Words สำหรับ .NET แล้ว คุณสามารถ[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: คุณต้องมีสภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น Visual Studio
3. .NET Framework: ตรวจสอบให้แน่ใจว่าสภาพแวดล้อมการพัฒนาของคุณได้รับการตั้งค่าสำหรับการพัฒนา .NET
4. ความรู้พื้นฐานเกี่ยวกับ C#: คู่มือนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ของคุณ ซึ่งจะช่วยให้คุณสามารถเข้าถึงคลาสและวิธีการทั้งหมดที่จำเป็นสำหรับการสร้างและจัดการเอกสารและแผนภูมิได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

เราจะแบ่งกระบวนการออกเป็นขั้นตอนง่ายๆ โดยแต่ละขั้นตอนมุ่งเน้นไปที่ส่วนเฉพาะของการกำหนดคุณสมบัติของแกน XY ในแผนภูมิ

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

 ขั้นแรกคุณต้องสร้างเอกสารใหม่และ`DocumentBuilder` วัตถุ.`DocumentBuilder` ช่วยในการแทรกเนื้อหาเข้าไปในเอกสาร

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกแผนภูมิ

ขั้นต่อไป คุณจะแทรกแผนภูมิลงในเอกสาร ในตัวอย่างนี้ เราจะใช้แผนภูมิพื้นที่ คุณสามารถปรับแต่งขนาดของแผนภูมิได้ตามต้องการ

```csharp
// แทรกแผนภูมิ
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## ขั้นตอนที่ 3: ล้างชุดเริ่มต้นและเพิ่มข้อมูลที่กำหนดเอง

โดยค่าเริ่มต้น แผนภูมิจะมีชุดข้อมูลที่กำหนดไว้ล่วงหน้า เราจะล้างข้อมูลเหล่านี้และเพิ่มชุดข้อมูลที่กำหนดเอง

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## ขั้นตอนที่ 4: กำหนดคุณสมบัติของแกน X

ตอนนี้ถึงเวลาที่จะกำหนดคุณสมบัติของแกน X แล้ว ซึ่งรวมถึงการตั้งค่าประเภทหมวดหมู่ ปรับแต่งการข้ามแกน และปรับเครื่องหมายและป้ายกำกับ

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; //วัดเป็นหน่วยแสดงผลของแกน Y (ร้อย)
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## ขั้นตอนที่ 5: กำหนดคุณสมบัติของแกน Y

ในทำนองเดียวกัน คุณจะตั้งค่าคุณสมบัติสำหรับแกน Y ซึ่งรวมถึงการตั้งค่าตำแหน่งป้ายกำกับเครื่องหมาย หน่วยหลักและหน่วยรอง หน่วยแสดงผล และการปรับขนาด

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารลงในไดเร็กทอรีที่คุณระบุ ซึ่งจะสร้างเอกสาร Word ที่มีแผนภูมิที่กำหนดเอง

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## บทสรุป

การสร้างและปรับแต่งแผนภูมิในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายเมื่อคุณเข้าใจขั้นตอนที่เกี่ยวข้อง คู่มือนี้จะแนะนำคุณตลอดกระบวนการกำหนดคุณสมบัติแกน XY ในแผนภูมิ ตั้งแต่การเริ่มต้นเอกสารจนถึงการบันทึกผลิตภัณฑ์ขั้นสุดท้าย ด้วยทักษะเหล่านี้ คุณสามารถสร้างแผนภูมิที่มีรายละเอียดและดูเป็นมืออาชีพซึ่งจะช่วยเสริมเอกสารของคุณได้

## คำถามที่พบบ่อย

### ฉันสามารถสร้างแผนภูมิประเภทใดได้บ้างโดยใช้ Aspose.Words สำหรับ .NET
คุณสามารถสร้างแผนภูมิได้หลากหลายประเภท เช่น แผนภูมิพื้นที่ แผนภูมิแท่ง แผนภูมิเส้น แผนภูมิวงกลม และอื่นๆ อีกมากมาย

### ฉันจะติดตั้ง Aspose.Words สำหรับ .NET ได้อย่างไร?
 คุณสามารถดาวน์โหลด Aspose.Words สำหรับ .NET ได้จาก[ที่นี่](https://releases.aspose.com/words/net/)และปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้

### ฉันสามารถปรับแต่งลักษณะของแผนภูมิของฉันได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET อนุญาตให้ปรับแต่งแผนภูมิได้มากมาย รวมถึงสี แบบอักษร และคุณสมบัติของแกน

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถรับการทดลองใช้ฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถหาบทช่วยสอนและเอกสารเพิ่มเติมได้ที่ไหน
 คุณสามารถค้นหาบทช่วยสอนและเอกสารรายละเอียดเพิ่มเติมได้ที่[หน้าเอกสาร Aspose.Words สำหรับ .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
