---
title: การแทรกแผนภูมิคอลัมน์ในเอกสาร Word
linktitle: การแทรกแผนภูมิคอลัมน์ในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแทรกแผนภูมิคอลัมน์ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปรับปรุงการแสดงภาพข้อมูลในรายงานและการนำเสนอของคุณ
weight: 10
url: /th/net/programming-with-charts/insert-column-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การแทรกแผนภูมิคอลัมน์ในเอกสาร Word

## การแนะนำ

ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีปรับปรุงเอกสาร Word ของคุณด้วยการแทรกแผนภูมิคอลัมน์ที่ดึงดูดสายตาโดยใช้ Aspose.Words สำหรับ .NET แผนภูมิคอลัมน์มีประสิทธิภาพในการแสดงแนวโน้มข้อมูลและการเปรียบเทียบ ทำให้เอกสารของคุณมีข้อมูลและน่าสนใจมากขึ้น

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และสภาพแวดล้อม .NET
-  Aspose.Words สำหรับ .NET ติดตั้งอยู่ในสภาพแวดล้อมการพัฒนาของคุณแล้ว คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
- โปรแกรมแก้ไขข้อความหรือสภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น Visual Studio

## การนำเข้าเนมสเปซ

ก่อนที่คุณจะเริ่มเขียนโค้ด ให้ทำการนำเข้าเนมสเปซที่จำเป็น:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

ปฏิบัติตามขั้นตอนเหล่านี้เพื่อแทรกแผนภูมิคอลัมน์ลงในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET:

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

 ขั้นแรก ให้สร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน`DocumentBuilder` วัตถุ.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกแผนภูมิคอลัมน์

 ใช้`InsertChart` วิธีการของ`DocumentBuilder`ชั้นเรียนการแทรกแผนภูมิคอลัมน์

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## ขั้นตอนที่ 3: เพิ่มข้อมูลลงในแผนภูมิ

 เพิ่มชุดข้อมูลลงในแผนภูมิโดยใช้`Series` ทรัพย์สินของ`Chart` วัตถุ.

```csharp
chart.Series.Add("Aspose Series 1", new string[] { "Category 1", "Category 2" }, new double[] { 1, 2 });
```

## ขั้นตอนที่ 4: บันทึกเอกสาร

บันทึกเอกสารพร้อมแผนภูมิคอลัมน์ที่แทรกลงในตำแหน่งที่คุณต้องการ

```csharp
doc.Save(dataDir + "InsertColumnChart.docx");
```

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการแทรกแผนภูมิคอลัมน์ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว ทักษะนี้จะช่วยเพิ่มความน่าสนใจทางภาพและคุณค่าด้านข้อมูลของเอกสารของคุณได้อย่างมาก ทำให้การนำเสนอข้อมูลชัดเจนและมีประสิทธิภาพมากขึ้น

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะของแผนภูมิคอลัมน์ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET มีตัวเลือกมากมายในการปรับแต่งองค์ประกอบแผนภูมิ เช่น สี ป้ายชื่อ และแกน

### Aspose.Words สำหรับ .NET เข้ากันได้กับ Microsoft Word เวอร์ชันต่างๆ หรือไม่
ใช่ Aspose.Words สำหรับ .NET รองรับ Microsoft Word เวอร์ชันต่างๆ มากมาย ช่วยให้มั่นใจได้ว่าสามารถใช้งานร่วมกันได้ในสภาพแวดล้อมที่แตกต่างกัน

### ฉันจะรวมข้อมูลแบบไดนามิกลงในแผนภูมิคอลัมน์ได้อย่างไร
คุณสามารถเติมข้อมูลแบบไดนามิกลงในแผนภูมิคอลัมน์ได้โดยการดึงข้อมูลจากฐานข้อมูลหรือแหล่งภายนอกอื่นๆ ในแอปพลิเคชัน .NET ของคุณ

### ฉันสามารถส่งออกเอกสาร Word พร้อมแผนภูมิที่แทรกไปเป็น PDF หรือรูปแบบอื่นได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET ช่วยให้คุณบันทึกเอกสารพร้อมแผนภูมิในรูปแบบต่างๆ รวมถึง PDF, HTML และรูปภาพ

### ฉันจะได้รับการสนับสนุนหรือความช่วยเหลือเพิ่มเติมสำหรับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 หากต้องการความช่วยเหลือเพิ่มเติม โปรดไปที่[ฟอรั่ม Aspose.Words สำหรับ .NET](https://forum.aspose.com/c/words/8) หรือติดต่อฝ่ายสนับสนุน Aspose


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
