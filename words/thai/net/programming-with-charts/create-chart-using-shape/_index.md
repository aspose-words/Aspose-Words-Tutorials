---
title: สร้างและปรับแต่งแผนภูมิโดยใช้รูปร่าง
linktitle: สร้างและปรับแต่งแผนภูมิโดยใช้รูปร่าง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีสร้างและปรับแต่งแผนภูมิในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้ เหมาะอย่างยิ่งสำหรับการแสดงภาพข้อมูล
weight: 10
url: /th/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างและปรับแต่งแผนภูมิโดยใช้รูปร่าง

## การแนะนำ

การสร้างและปรับแต่งแผนภูมิในเอกสารของคุณเป็นทักษะที่สำคัญในโลกปัจจุบันที่ข้อมูลถูกขับเคลื่อน แผนภูมิสามารถช่วยสร้างภาพข้อมูล ทำให้ข้อมูลที่ซับซ้อนเข้าใจง่ายขึ้น Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพที่ช่วยให้คุณสร้างและจัดการเอกสาร Word ได้ด้วยโปรแกรม ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการสร้างและปรับแต่งแผนภูมิเส้นโดยใช้ Aspose.Words สำหรับ .NET เมื่ออ่านคู่มือนี้จบ คุณจะสามารถสร้างแผนภูมิที่ดูเป็นมืออาชีพได้อย่างง่ายดาย

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Words สำหรับไลบรารี .NET: คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
- Visual Studio: เวอร์ชันใดก็ตามที่รองรับ .NET
- ความรู้พื้นฐานเกี่ยวกับ C#: การทำความเข้าใจพื้นฐานของ C# จะช่วยให้คุณทำตามบทช่วยสอนได้

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็น ขั้นตอนนี้มีความสำคัญเนื่องจากช่วยให้คุณสามารถใช้คลาสและวิธีการที่ Aspose.Words จัดเตรียมไว้สำหรับ .NET ได้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ขั้นแรก คุณต้องสร้างเอกสาร Word ใหม่ เอกสารนี้จะทำหน้าที่เป็นผืนผ้าใบสำหรับแผนภูมิของคุณ

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกแผนภูมิ

 ต่อไปคุณจะแทรกแผนภูมิเส้นลงในเอกสาร`DocumentBuilder.InsertChart` วิธีที่ใช้สำหรับจุดประสงค์นี้

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## ขั้นตอนที่ 3: ปรับแต่งชื่อแผนภูมิ

การปรับแต่งชื่อแผนภูมิจะช่วยให้แสดงข้อมูลได้อย่างเหมาะสม คุณสามารถแสดงชื่อแผนภูมิและตั้งค่าข้อความโดยใช้โค้ดต่อไปนี้:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// โปรดทราบว่าหากระบุค่าว่างหรือค่าว่างเป็นข้อความชื่อเรื่อง ระบบจะแสดงชื่อเรื่องที่สร้างขึ้นโดยอัตโนมัติ
```

## ขั้นตอนที่ 4: ปรับตำแหน่งตำนาน

คำอธิบายประกอบช่วยระบุชุดข้อมูลต่างๆ ในแผนภูมิของคุณ คุณสามารถปรับแต่งตำแหน่งและการตั้งค่าการซ้อนทับได้ดังนี้:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายคุณต้องบันทึกเอกสาร ขั้นตอนนี้จะช่วยให้แน่ใจว่าการเปลี่ยนแปลงทั้งหมดของคุณถูกเขียนลงในไฟล์

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการสร้างและปรับแต่งแผนภูมิเส้นในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เมื่อปฏิบัติตามคำแนะนำทีละขั้นตอนแล้ว คุณก็สามารถสร้างแผนภูมิที่สวยงามและสื่อสารข้อมูลของคุณได้อย่างมีประสิทธิภาพ Aspose.Words สำหรับ .NET มีตัวเลือกการปรับแต่งมากมาย ช่วยให้คุณปรับแต่งแผนภูมิให้เหมาะกับความต้องการเฉพาะของคุณได้

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET เพื่อสร้างแผนภูมิประเภทอื่นได้หรือไม่

 ใช่ Aspose.Words สำหรับ .NET รองรับแผนภูมิประเภทต่างๆ รวมถึงแผนภูมิแท่ง แผนภูมิวงกลม และอื่นๆ คุณสามารถศึกษาเอกสารประกอบได้[ที่นี่](https://reference.aspose.com/words/net/) สำหรับรายละเอียดเพิ่มเติม

### ฉันจะทดลองใช้ Aspose.Words สำหรับ .NET ก่อนซื้อได้อย่างไร

 คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีได้จาก[ที่นี่](https://releases.aspose.com/)ซึ่งจะทำให้คุณสามารถทดสอบไลบรารีและฟีเจอร์ต่างๆ ได้ก่อนตัดสินใจซื้อ

### มีวิธีรับการสนับสนุนหรือไม่หากฉันประสบปัญหา?

 แน่นอน คุณสามารถเข้าถึงการสนับสนุนผ่านฟอรัมชุมชน Aspose[ที่นี่](https://forum.aspose.com/c/words/8)ชุมชนและเจ้าหน้าที่ Aspose ตอบสนองได้ดีมาก

### ฉันจะซื้อใบอนุญาตสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร

 คุณสามารถซื้อใบอนุญาตโดยตรงจากเว็บไซต์ Aspose[ที่นี่](https://purchase.aspose.com/buy)มีตัวเลือกใบอนุญาตหลากหลายเพื่อให้ตรงกับความต้องการที่แตกต่างกัน

### จะเกิดอะไรขึ้นหากฉันต้องการใบอนุญาตชั่วคราวสำหรับโครงการระยะสั้น?

 Aspose เสนอใบอนุญาตชั่วคราวซึ่งคุณสามารถร้องขอได้[ที่นี่](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
