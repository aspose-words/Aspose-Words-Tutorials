---
"description": "เรียนรู้วิธีการตั้งค่าคอนฟิกูเรชันหน้าต่างๆ เมื่อรวมเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET มีคู่มือทีละขั้นตอนรวมอยู่ด้วย"
"linktitle": "การตั้งค่าหน้าที่แตกต่างกัน"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "การตั้งค่าหน้าที่แตกต่างกัน"
"url": "/th/net/join-and-append-documents/different-page-setup/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การตั้งค่าหน้าที่แตกต่างกัน

## การแนะนำ

สวัสดี! พร้อมที่จะดำดิ่งสู่โลกอันน่าหลงใหลของการจัดการเอกสารด้วย Aspose.Words สำหรับ .NET แล้วหรือยัง? วันนี้เราจะมาพูดถึงเรื่องดีๆ กัน: การตั้งค่าหน้าต่างๆ เมื่อรวมเอกสาร Word เข้าด้วยกัน ไม่ว่าคุณจะกำลังรวมรายงาน สร้างนวนิยาย หรือแค่เล่นกับเอกสารเพื่อความสนุกสนาน คู่มือนี้จะพาคุณผ่านขั้นตอนต่างๆ เหล่านี้ทีละขั้นตอน มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงมือทำ เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1. Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET แล้ว คุณสามารถ [ดาวน์โหลดได้ที่นี่](https://releases-aspose.com/words/net/).
2. .NET Framework: เวอร์ชันใดก็ตามที่รองรับ Aspose.Words สำหรับ .NET
3. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE อื่น ๆ ที่เข้ากันได้กับ .NET
4. ความรู้พื้นฐานเกี่ยวกับ C#: เพียงพื้นฐานในการทำความเข้าใจไวยากรณ์และโครงสร้าง

## นำเข้าเนมสเปซ

ขั้นแรก เรามาทำการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# กันก่อน เนมสเปซเหล่านี้มีความสำคัญต่อการเข้าถึงฟีเจอร์ของ Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Tables;
```

เอาล่ะ มาเข้าประเด็นกันเลยดีกว่า เราจะแบ่งกระบวนการทั้งหมดออกเป็นขั้นตอนที่ทำตามได้ง่าย

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

### ขั้นตอนที่ 1.1: สร้างโครงการใหม่

เปิด Visual Studio และสร้างแอปพลิเคชันคอนโซล C# ใหม่ ตั้งชื่อให้น่าสนใจ เช่น "DifferentPageSetupExample"

### ขั้นตอนที่ 1.2: เพิ่มการอ้างอิง Aspose.Words

หากต้องการใช้ Aspose.Words คุณต้องเพิ่มลงในโปรเจ็กต์ของคุณ หากคุณยังไม่ได้ดาวน์โหลดแพ็กเกจ Aspose.Words สำหรับ .NET คุณสามารถติดตั้งได้ผ่านตัวจัดการแพ็กเกจ NuGet โดยใช้คำสั่งต่อไปนี้:

```bash
Install-Package Aspose.Words
```

## ขั้นตอนที่ 2: โหลดเอกสาร

ตอนนี้เรามาโหลดเอกสารที่ต้องการรวมเข้าด้วยกัน สำหรับตัวอย่างนี้ คุณจะต้องมีเอกสาร Word สองฉบับ: `Document source.docx` และ `Northwind traders.docx`ตรวจสอบให้แน่ใจว่าไฟล์เหล่านี้อยู่ในไดเร็กทอรีโครงการของคุณ

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## ขั้นตอนที่ 3: กำหนดค่าการตั้งค่าหน้าสำหรับเอกสารต้นฉบับ

เราต้องแน่ใจว่าการตั้งค่าหน้าของเอกสารต้นฉบับตรงกับเอกสารปลายทาง ขั้นตอนนี้มีความสำคัญมากสำหรับการผสานที่ราบรื่น

### ขั้นตอนที่ 3.1: ดำเนินการต่อหลังจากเอกสารปลายทาง

ตั้งค่าเอกสารต้นฉบับให้ดำเนินการต่อทันทีหลังจากเอกสารปลายทาง

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

### ขั้นตอนที่ 3.2: เริ่มการกำหนดหมายเลขหน้าใหม่

เริ่มต้นการนับหน้าที่จุดเริ่มต้นของเอกสารต้นฉบับใหม่

```csharp
srcDoc.FirstSection.PageSetup.RestartPageNumbering = true;
srcDoc.FirstSection.PageSetup.PageStartingNumber = 1;
```

## ขั้นตอนที่ 4: จับคู่การตั้งค่าหน้า

เพื่อหลีกเลี่ยงความไม่สอดคล้องกันของเค้าโครง ตรวจสอบให้แน่ใจว่าการตั้งค่าหน้าของส่วนแรกของเอกสารต้นฉบับตรงกับการตั้งค่าของส่วนสุดท้ายของเอกสารปลายทาง

```csharp
srcDoc.FirstSection.PageSetup.PageWidth = dstDoc.LastSection.PageSetup.PageWidth;
srcDoc.FirstSection.PageSetup.PageHeight = dstDoc.LastSection.PageSetup.PageHeight;
srcDoc.FirstSection.PageSetup.Orientation = dstDoc.LastSection.PageSetup.Orientation;
```

## ขั้นตอนที่ 5: ปรับรูปแบบย่อหน้า

เพื่อให้แน่ใจว่าการไหลจะราบรื่น เราจำเป็นต้องปรับการจัดรูปแบบย่อหน้าในเอกสารต้นฉบับ

ทำซ้ำผ่านย่อหน้าทั้งหมดในเอกสารต้นฉบับและตั้งค่า `KeepWithNext` คุณสมบัติ.

```csharp
foreach (Paragraph para in srcDoc.GetChildNodes(NodeType.Paragraph, true))
{
    para.ParagraphFormat.KeepWithNext = true;
}
```

## ขั้นตอนที่ 6: ผนวกเอกสารต้นฉบับ

สุดท้าย ให้ผนวกเอกสารต้นฉบับเข้ากับเอกสารปลายทาง โดยต้องแน่ใจว่ารูปแบบดั้งเดิมได้รับการรักษาไว้

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## ขั้นตอนที่ 7: บันทึกเอกสารรวม

ตอนนี้บันทึกเอกสารที่ผสานสวยงามของคุณ

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.DifferentPageSetup.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้! คุณเพิ่งรวมเอกสาร Word สองฉบับที่มีการตั้งค่าหน้าที่แตกต่างกันโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การจัดการเอกสารด้วยโปรแกรมเป็นเรื่องง่ายมาก ไม่ว่าคุณจะกำลังสร้างรายงานที่ซับซ้อน รวบรวมหนังสือ หรือจัดการเอกสารหลายส่วน Aspose.Words ก็พร้อมช่วยเหลือคุณ

## คำถามที่พบบ่อย

### ฉันสามารถใช้วิธีนี้กับเอกสารมากกว่าสองฉบับได้ไหม?
แน่นอน! เพียงทำซ้ำขั้นตอนสำหรับเอกสารเพิ่มเติมแต่ละฉบับที่คุณต้องการรวมเข้าด้วยกัน

### จะเกิดอะไรขึ้นหากเอกสารของฉันมีระยะขอบต่างกัน?
คุณสามารถจับคู่การตั้งค่าระยะขอบได้ในลักษณะเดียวกับที่เราจับคู่ความกว้าง ความสูง และการวางแนวของหน้า

### Aspose.Words เข้ากันได้กับ .NET Core ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET สามารถเข้ากันได้อย่างสมบูรณ์กับ .NET Core

### ฉันสามารถรักษาสไตล์จากทั้งสองเอกสารได้ไหม
ใช่ครับ `ImportFormatMode.KeepSourceFormatting` ตัวเลือกนี้จะช่วยให้แน่ใจว่าสไตล์จากเอกสารต้นฉบับได้รับการรักษาไว้

### ฉันจะได้รับความช่วยเหลือเพิ่มเติมเกี่ยวกับ Aspose.Words ได้จากที่ไหน
ตรวจสอบออก [เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/) หรือเยี่ยมชมพวกเขา [ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8) เพื่อความช่วยเหลือเพิ่มเติม



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}