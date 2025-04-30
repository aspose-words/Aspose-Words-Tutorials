---
"description": "เรียนรู้วิธีแทรกแผนภูมิแบบกระจายใน Word ด้วย Aspose.Words สำหรับ .NET ขั้นตอนง่ายๆ สำหรับการผสานการแสดงข้อมูลภาพลงในเอกสารของคุณ"
"linktitle": "การแทรกแผนภูมิกระจายในเอกสาร Word"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "การแทรกแผนภูมิกระจายในเอกสาร Word"
"url": "/th/net/programming-with-charts/insert-scatter-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การแทรกแผนภูมิกระจายในเอกสาร Word

## การแนะนำ

ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีใช้ Aspose.Words สำหรับ .NET เพื่อแทรกแผนภูมิแบบกระจายลงในเอกสาร Word ของคุณ แผนภูมิแบบกระจายเป็นเครื่องมือทางภาพที่มีประสิทธิภาพที่สามารถแสดงจุดข้อมูลตามตัวแปรสองตัวได้อย่างมีประสิทธิภาพ ทำให้เอกสารของคุณน่าสนใจและให้ข้อมูลมากขึ้น

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มสร้างแผนภูมิแบบกระจายด้วย Aspose.Words สำหรับ .NET โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. การติดตั้ง Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้ง Aspose.Words สำหรับ .NET จาก [ที่นี่](https://releases-aspose.com/words/net/).
   
2. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และ .NET framework จะเป็นประโยชน์

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

ตอนนี้ เรามาดูกระบวนการแทรกแผนภูมิแบบกระจายลงในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET กัน:

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

ขั้นแรก ให้เริ่มต้นอินสแตนซ์ใหม่ของ `Document` ชั้นเรียนและ `DocumentBuilder` ชั้นเรียนเพื่อเริ่มต้นสร้างเอกสารของคุณ

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกแผนภูมิกระจาย

ใช้ `InsertChart` วิธีการของ `DocumentBuilder` ชั้นเรียนที่จะแทรกแผนภูมิแบบกระจายเข้าไปในเอกสาร

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## ขั้นตอนที่ 3: เพิ่มชุดข้อมูลลงในแผนภูมิ

ตอนนี้ เพิ่มชุดข้อมูลลงในแผนภูมิแบบกระจายของคุณ ตัวอย่างนี้สาธิตการเพิ่มชุดข้อมูลที่มีจุดข้อมูลเฉพาะ

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## ขั้นตอนที่ 4: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารที่แก้ไขแล้วไปยังตำแหน่งที่คุณต้องการโดยใช้ `Save` วิธีการของ `Document` ระดับ.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการแทรกแผนภูมิแบบกระจายลงในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว แผนภูมิแบบกระจายเป็นเครื่องมือที่ยอดเยี่ยมสำหรับการแสดงภาพความสัมพันธ์ของข้อมูล และด้วย Aspose.Words คุณสามารถผสานรวมแผนภูมิเหล่านี้ลงในเอกสารของคุณได้อย่างง่ายดายเพื่อเพิ่มความชัดเจนและความเข้าใจ

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของแผนภูมิกระจายโดยใช้ Aspose.Words ได้หรือไม่
ใช่ Aspose.Words อนุญาตให้ปรับแต่งคุณสมบัติของแผนภูมิ เช่น สี แกน และป้ายกำกับ ได้อย่างกว้างขวาง

### Aspose.Words เข้ากันได้กับ Microsoft Word เวอร์ชันต่างๆ หรือไม่
Aspose.Words รองรับ Microsoft Word หลายเวอร์ชัน ช่วยให้มั่นใจได้ว่าสามารถใช้งานร่วมกันได้ในทุกแพลตฟอร์ม

### Aspose.Words รองรับแผนภูมิประเภทอื่นหรือไม่
ใช่ Aspose.Words รองรับแผนภูมิประเภทต่างๆ มากมาย เช่น แผนภูมิแท่ง แผนภูมิเส้น และแผนภูมิวงกลม

### ฉันสามารถอัปเดตข้อมูลแบบไดนามิกในแผนภูมิกระจายด้วยโปรแกรมได้หรือไม่
แน่นอน คุณสามารถอัปเดตข้อมูลแผนภูมิแบบไดนามิกได้โดยใช้การเรียก API ของ Aspose.Words

### ฉันจะได้รับความช่วยเหลือหรือการสนับสนุนเพิ่มเติมสำหรับ Aspose.Words ได้จากที่ใด
หากต้องการความช่วยเหลือเพิ่มเติม โปรดไปที่ [ฟอรั่มสนับสนุน Aspose.Words](https://forum-aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}