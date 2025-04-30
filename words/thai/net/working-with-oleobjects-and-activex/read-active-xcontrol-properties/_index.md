---
"description": "เรียนรู้วิธีการอ่านคุณสมบัติของตัวควบคุม ActiveX จากไฟล์ Word โดยใช้ Aspose.Words สำหรับ .NET ในคู่มือทีละขั้นตอน พัฒนาทักษะการจัดการเอกสารอัตโนมัติของคุณ"
"linktitle": "อ่านคุณสมบัติ Active XControl จากไฟล์ Word"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "อ่านคุณสมบัติ Active XControl จากไฟล์ Word"
"url": "/th/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# อ่านคุณสมบัติ Active XControl จากไฟล์ Word

## การแนะนำ

ในยุคดิจิทัลทุกวันนี้ การทำงานอัตโนมัติถือเป็นปัจจัยสำคัญในการเพิ่มประสิทธิภาพการทำงาน หากคุณทำงานกับเอกสาร Word ที่มีตัวควบคุม ActiveX คุณอาจต้องอ่านคุณสมบัติของตัวควบคุมเหล่านี้เพื่อวัตถุประสงค์ต่างๆ ตัวควบคุม ActiveX เช่น ช่องกาเครื่องหมายและปุ่มสามารถเก็บข้อมูลสำคัญได้ การใช้ Aspose.Words สำหรับ .NET ช่วยให้คุณสามารถแยกและจัดการข้อมูลนี้ด้วยโปรแกรมได้อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. Aspose.Words สำหรับไลบรารี .NET: คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/net/).
2. Visual Studio หรือ IDE C# ใดๆ: เพื่อเขียนและดำเนินการโค้ดของคุณ
3. เอกสาร Word ที่มีตัวควบคุม ActiveX: ตัวอย่างเช่น "ActiveX controls.docx"
4. ความรู้พื้นฐานเกี่ยวกับ C#: ต้องมีความคุ้นเคยกับการเขียนโปรแกรม C# เพื่อปฏิบัติตาม

## นำเข้าเนมสเปซ

ก่อนอื่นให้เรานำเข้าเนมสเปซที่จำเป็นสำหรับการใช้งาน Aspose.Words สำหรับ .NET

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## ขั้นตอนที่ 1: โหลดเอกสาร Word

ในการเริ่มต้น คุณจะต้องโหลดเอกสาร Word ที่มีตัวควบคุม ActiveX

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## ขั้นตอนที่ 2: สร้างสตริงเพื่อเก็บคุณสมบัติ

ขั้นตอนต่อไป คือการเริ่มต้นสตริงว่างเพื่อจัดเก็บคุณสมบัติของตัวควบคุม ActiveX

```csharp
string properties = "";
```

## ขั้นตอนที่ 3: ทำซ้ำผ่านรูปร่างในเอกสาร

เราจำเป็นต้องวนซ้ำผ่านรูปร่างทั้งหมดในเอกสารเพื่อค้นหาตัวควบคุม ActiveX

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // ประมวลผลการควบคุม ActiveX
    }
}
```

## ขั้นตอนที่ 4: แยกคุณสมบัติจากตัวควบคุม ActiveX

ตรวจสอบว่าตัวควบคุมเป็น Forms2OleControl ภายในลูปหรือไม่ หากใช่ ให้แคสต์และแยกคุณสมบัติออกมา

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## ขั้นตอนที่ 5: นับจำนวนตัวควบคุม ActiveX ทั้งหมด

หลังจากทำซ้ำผ่านรูปร่างทั้งหมดแล้ว ให้นับจำนวนตัวควบคุม ActiveX ทั้งหมดที่พบ

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## ขั้นตอนที่ 6: แสดงคุณสมบัติ

สุดท้ายให้พิมพ์คุณสมบัติที่แยกออกมาไปยังคอนโซล

```csharp
Console.WriteLine("\n" + properties);
```

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้เรียนรู้วิธีการอ่านคุณสมบัติของตัวควบคุม ActiveX จากเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว บทช่วยสอนนี้ครอบคลุมถึงการโหลดเอกสาร การวนซ้ำผ่านรูปร่าง และการดึงคุณสมบัติจากตัวควบคุม ActiveX เมื่อทำตามขั้นตอนเหล่านี้แล้ว คุณสามารถทำให้การดึงข้อมูลสำคัญจากเอกสาร Word ของคุณเป็นแบบอัตโนมัติ ซึ่งจะช่วยเพิ่มประสิทธิภาพเวิร์กโฟลว์ของคุณ

## คำถามที่พบบ่อย

### ตัวควบคุม ActiveX ในเอกสาร Word คืออะไร
ตัวควบคุม ActiveX เป็นวัตถุเชิงโต้ตอบที่ฝังอยู่ในเอกสาร Word เช่น ช่องกาเครื่องหมาย ปุ่ม และช่องข้อความ ซึ่งใช้ในการสร้างแบบฟอร์มและทำงานอัตโนมัติ

### ฉันสามารถปรับเปลี่ยนคุณสมบัติของตัวควบคุม ActiveX โดยใช้ Aspose.Words สำหรับ .NET ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET ช่วยให้คุณสามารถปรับเปลี่ยนคุณสมบัติของตัวควบคุม ActiveX ได้โดยทางโปรแกรม

### Aspose.Words สำหรับ .NET ใช้ได้ฟรีหรือไม่?
Aspose.Words for .NET เสนอให้ทดลองใช้งานฟรี แต่คุณจะต้องซื้อใบอนุญาตเพื่อใช้งานต่อ คุณสามารถทดลองใช้งานฟรีได้ [ที่นี่](https://releases-aspose.com/).

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET กับภาษา .NET อื่นๆ นอกเหนือจาก C# ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET สามารถใช้ได้กับภาษา .NET ใดๆ ก็ได้ รวมถึง VB.NET และ F#

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
คุณสามารถค้นหาเอกสารรายละเอียดได้ [ที่นี่](https://reference-aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}