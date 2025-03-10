---
title: ปรับแต่งป้ายข้อมูลแผนภูมิ
linktitle: ปรับแต่งป้ายข้อมูลแผนภูมิ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีปรับแต่งป้ายข้อมูลแผนภูมิโดยใช้ Aspose.Words สำหรับ .NET ในคู่มือทีละขั้นตอน เหมาะสำหรับนักพัฒนา .NET
weight: 10
url: /th/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ปรับแต่งป้ายข้อมูลแผนภูมิ

## การแนะนำ

คุณกำลังมองหาวิธีปรับปรุงแอปพลิเคชัน .NET ของคุณด้วยความสามารถในการประมวลผลเอกสารแบบไดนามิกและกำหนดเองหรือไม่ Aspose.Words สำหรับ .NET อาจเป็นคำตอบของคุณ! ในคู่มือนี้ เราจะเจาะลึกการปรับแต่งป้ายข้อมูลแผนภูมิโดยใช้ Aspose.Words สำหรับ .NET ซึ่งเป็นไลบรารีอันทรงพลังสำหรับการสร้าง แก้ไข และแปลงเอกสาร Word ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น บทช่วยสอนนี้จะแนะนำคุณในแต่ละขั้นตอน เพื่อให้คุณเข้าใจวิธีใช้เครื่องมือนี้ได้อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. Visual Studio: ติดตั้ง Visual Studio 2019 หรือใหม่กว่า
2. .NET Framework: ตรวจสอบว่าคุณมี .NET Framework 4.0 หรือใหม่กว่า
3.  Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้ง Aspose.Words สำหรับ .NET จาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/).
4. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# เป็นสิ่งจำเป็น
5.  ใบอนุญาตที่ถูกต้อง: รับ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หรือซื้อหนึ่งจาก[ลิงค์ซื้อ](https://purchase.aspose.com/buy).

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ ขั้นตอนนี้มีความสำคัญมาก เนื่องจากขั้นตอนนี้จะช่วยให้คุณสามารถเข้าถึงคลาสและเมธอดทั้งหมดที่ Aspose.Words จัดเตรียมไว้ได้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

ในการสร้างและจัดการเอกสาร Word ก่อนอื่นเราต้องสร้างอินสแตนซ์ของ`Document` ชั้นเรียนและก`DocumentBuilder` วัตถุ.

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### คำอธิบาย

- เอกสารเอกสาร: สร้างอินสแตนซ์ใหม่ของคลาสเอกสาร
- ตัวสร้าง DocumentBuilder: DocumentBuilder ช่วยในการแทรกเนื้อหาลงในวัตถุเอกสาร

## ขั้นตอนที่ 2: แทรกแผนภูมิ

 ต่อไปเราจะแทรกแผนภูมิแท่งเข้าไปในเอกสารโดยใช้`DocumentBuilder` วัตถุ.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### คำอธิบาย

- รูปทรงรูปร่าง: แสดงแผนภูมิเป็นรูปร่างในเอกสาร
- builder.InsertChart(ChartType.Bar, 432, 252): แทรกแผนภูมิแท่งที่มีมิติที่ระบุ

## ขั้นตอนที่ 3: เข้าถึงชุดแผนภูมิ

เพื่อปรับแต่งป้ายข้อมูล เราต้องเข้าถึงชุดข้อมูลในแผนภูมิก่อน

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### คำอธิบาย

- ChartSeries series0: ดึงข้อมูลชุดแรกของแผนภูมิซึ่งเราจะปรับแต่ง

## ขั้นตอนที่ 4: ปรับแต่งป้ายข้อมูล

สามารถปรับแต่งป้ายข้อมูลเพื่อแสดงข้อมูลต่างๆ ได้ เราจะกำหนดค่าป้ายข้อมูลเพื่อแสดงคีย์คำอธิบาย ชื่อซีรีส์ และค่า ในขณะที่ซ่อนชื่อหมวดหมู่และเปอร์เซ็นต์

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### คำอธิบาย

- ป้ายชื่อ ChartDataLabelCollection: เข้าถึงป้ายชื่อข้อมูลของชุดข้อมูล
- labels.ShowLegendKey: แสดงคีย์คำอธิบาย
- labels.ShowLeaderLines: แสดงเส้นผู้นำสำหรับป้ายข้อมูลที่วางไว้ด้านนอกจุดข้อมูล
- labels.ShowCategoryName: ซ่อนชื่อหมวดหมู่
- labels.ShowPercentage: ซ่อนค่าเปอร์เซ็นต์
- labels.ShowSeriesName: แสดงชื่อชุด
- labels.ShowValue: แสดงค่าของจุดข้อมูล
- labels.Separator: กำหนดตัวคั่นสำหรับป้ายข้อมูล

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### คำอธิบาย

- doc.Save: บันทึกเอกสารที่มีชื่อที่ระบุในไดเร็กทอรีที่ให้ไว้

## บทสรุป

 ขอแสดงความยินดี! คุณปรับแต่งป้ายข้อมูลแผนภูมิสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีนี้นำเสนอโซลูชันที่แข็งแกร่งสำหรับการจัดการเอกสาร Word ด้วยโปรแกรม ทำให้ผู้พัฒนาสามารถสร้างแอปพลิเคชันการประมวลผลเอกสารที่ซับซ้อนและไดนามิกได้ง่ายขึ้น เจาะลึก[เอกสารประกอบ](https://reference.aspose.com/words/net/) เพื่อสำรวจคุณลักษณะและความสามารถเพิ่มเติม

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีการประมวลผลเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word ได้โดยการใช้โปรแกรม

### ฉันจะติดตั้ง Aspose.Words สำหรับ .NET ได้อย่างไร?
 คุณสามารถดาวน์โหลดและติดตั้งได้จาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/). ปฏิบัติตามคำแนะนำในการติดตั้งที่ให้มา

### ฉันสามารถทดลองใช้ Aspose.Words สำหรับ .NET ได้ฟรีหรือไม่?
 ใช่ คุณสามารถรับได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/)เพื่อประเมินผลิตภัณฑ์

### Aspose.Words สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ Aspose.Words สำหรับ .NET เข้ากันได้กับ .NET Core, .NET Standard และ .NET Framework

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
 คุณสามารถเยี่ยมชม[ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8) เพื่อขอความช่วยเหลือและการสนับสนุนจากชุมชน Aspose และผู้เชี่ยวชาญ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
