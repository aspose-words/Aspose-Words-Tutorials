---
"description": "เรียนรู้วิธีปรับเปลี่ยนแท็กเอกสารที่มีโครงสร้างใน Word โดยใช้ Aspose.Words สำหรับ .NET อัปเดตข้อความ เมนูแบบดรอปดาวน์ และรูปภาพทีละขั้นตอน"
"linktitle": "ปรับเปลี่ยนการควบคุมเนื้อหา"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "ปรับเปลี่ยนการควบคุมเนื้อหา"
"url": "/th/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ปรับเปลี่ยนการควบคุมเนื้อหา

## การแนะนำ

หากคุณเคยทำงานกับเอกสาร Word และจำเป็นต้องปรับเปลี่ยนการควบคุมเนื้อหาที่มีโครงสร้าง เช่น ข้อความธรรมดา รายการแบบดรอปดาวน์ หรือรูปภาพ การใช้ Aspose.Words สำหรับ .NET คุณมาถูกที่แล้ว! แท็กเอกสารที่มีโครงสร้าง (SDT) เป็นเครื่องมือที่มีประสิทธิภาพที่ช่วยให้การจัดการเอกสารอัตโนมัติง่ายขึ้นและยืดหยุ่นมากขึ้น ในบทช่วยสอนนี้ เราจะเจาะลึกว่าคุณสามารถปรับเปลี่ยน SDT เหล่านี้ให้เหมาะกับความต้องการของคุณได้อย่างไร ไม่ว่าคุณจะอัปเดตข้อความ เปลี่ยนการเลือกแบบดรอปดาวน์ หรือสลับรูปภาพ คู่มือนี้จะแนะนำคุณทีละขั้นตอนในกระบวนการนี้

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงรายละเอียดในการปรับเปลี่ยนการควบคุมเนื้อหา โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. ติดตั้ง Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words แล้ว หากยังไม่ได้ติดตั้ง คุณสามารถ [ดาวน์โหลดได้ที่นี่](https://releases-aspose.com/words/net/).

2. ความรู้พื้นฐานเกี่ยวกับ C#: บทช่วยสอนนี้ถือว่าคุณมีความคุ้นเคยกับแนวคิดการเขียนโปรแกรม C# ขั้นพื้นฐาน

3. สภาพแวดล้อมการพัฒนา .NET: คุณควรมี IDE เช่น Visual Studio ที่ตั้งค่าไว้สำหรับการรันแอปพลิเคชัน .NET

4. เอกสารตัวอย่าง: เราจะใช้เอกสาร Word ตัวอย่างที่มี SDT หลายประเภท คุณสามารถใช้เอกสารตัวอย่างหรือสร้างเอกสารของคุณเองก็ได้

5. การเข้าถึงเอกสาร Aspose: สำหรับข้อมูลโดยละเอียดเพิ่มเติม โปรดดูที่ [เอกสารประกอบ Aspose.Words](https://reference-aspose.com/words/net/).

## นำเข้าเนมสเปซ

หากต้องการเริ่มทำงานกับ Aspose.Words คุณต้องนำเข้าเนมสเปซที่เกี่ยวข้องเข้าสู่โปรเจ็กต์ C# ของคุณ โดยดำเนินการได้ดังนี้:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

เนมสเปซเหล่านี้จะทำให้คุณสามารถเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการจัดการแท็กเอกสารที่มีโครงสร้างในเอกสาร Word ของคุณได้

## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอกสารของคุณ

ก่อนที่จะทำการเปลี่ยนแปลงใด ๆ คุณต้องระบุเส้นทางไปยังเอกสารของคุณ แทนที่ `"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่คุณเก็บเอกสารไว้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## ขั้นตอนที่ 2: วนซ้ำผ่านแท็กเอกสารที่มีโครงสร้าง

หากต้องการปรับเปลี่ยน SDT ก่อนอื่นคุณต้องวนซ้ำผ่าน SDT ทั้งหมดในเอกสาร ซึ่งทำได้โดยใช้ `GetChildNodes` วิธีการรับโหนดทุกประเภท `StructuredDocumentTag`-

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // ปรับเปลี่ยน SDT ตามประเภท
}
```

## ขั้นตอนที่ 3: แก้ไข SDT แบบข้อความธรรมดา

หาก SDT เป็นประเภทข้อความธรรมดา คุณสามารถแทนที่เนื้อหาได้ ขั้นแรก ให้ล้างเนื้อหาที่มีอยู่ จากนั้นจึงเพิ่มข้อความใหม่

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

คำอธิบาย: ที่นี่ `RemoveAllChildren()` ล้างเนื้อหาที่มีอยู่ของ SDT จากนั้นเราจะสร้างใหม่ `Paragraph` และ `Run` วัตถุที่จะแทรกข้อความใหม่

## ขั้นตอนที่ 4: แก้ไขรายการดรอปดาวน์ SDT

สำหรับ SDT แบบรายการดรอปดาวน์ คุณสามารถเปลี่ยนรายการที่เลือกได้โดยเข้าถึง `ListItems` คอลเลกชัน ที่นี่เราเลือกรายการที่สามในรายการ

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

คำอธิบาย: โค้ดสั้นๆ นี้จะเลือกไอเท็มที่ดัชนี 2 (ไอเท็มที่สาม) จากรายการดร็อปดาวน์ ปรับแต่งดัชนีตามความต้องการของคุณ

## ขั้นตอนที่ 5: ปรับเปลี่ยนรูปภาพ SDT

หากต้องการอัปเดตรูปภาพภายใน SDT รูปภาพ คุณสามารถแทนที่รูปภาพที่มีอยู่ด้วยรูปภาพใหม่ได้

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

คำอธิบาย: โค้ดนี้จะตรวจสอบว่ารูปร่างมีรูปภาพหรือไม่ จากนั้นแทนที่ด้วยรูปภาพใหม่ที่อยู่ที่ `ImagesDir`-

## ขั้นตอนที่ 6: บันทึกเอกสารที่คุณแก้ไข

หลังจากทำการเปลี่ยนแปลงที่จำเป็นทั้งหมดแล้ว ให้บันทึกเอกสารที่แก้ไขด้วยชื่อใหม่เพื่อรักษาเอกสารต้นฉบับของคุณไว้

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

คำอธิบาย: การดำเนินการนี้จะบันทึกเอกสารด้วยชื่อไฟล์ใหม่ เพื่อให้คุณสามารถแยกความแตกต่างจากเอกสารต้นฉบับได้ง่าย

## บทสรุป

การแก้ไขตัวควบคุมเนื้อหาในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายเมื่อคุณเข้าใจขั้นตอนที่เกี่ยวข้อง ไม่ว่าคุณจะอัปเดตข้อความ เปลี่ยนการเลือกแบบดรอปดาวน์ หรือสลับรูปภาพ Aspose.Words ก็มี API ที่แข็งแกร่งสำหรับงานเหล่านี้ เมื่อทำตามบทช่วยสอนนี้ คุณจะสามารถจัดการและปรับแต่งตัวควบคุมเนื้อหาที่มีโครงสร้างของเอกสารได้อย่างมีประสิทธิภาพ ทำให้เอกสารของคุณมีความไดนามิกมากขึ้นและเหมาะกับความต้องการของคุณ

## คำถามที่พบบ่อย

1. แท็กเอกสารที่มีโครงสร้าง (SDT) คืออะไร?

SDT เป็นองค์ประกอบในเอกสาร Word ที่ช่วยจัดการและจัดรูปแบบเนื้อหาเอกสาร เช่น กล่องข้อความ รายการดรอปดาวน์ หรือรูปภาพ

2. ฉันจะเพิ่มรายการดรอปดาวน์ใหม่ลงใน SDT ได้อย่างไร

หากต้องการเพิ่มรายการใหม่ ให้ใช้ `ListItems` ทรัพย์สินและผนวกใหม่ `SdtListItem` ไปที่คอลเลกชัน

3. ฉันสามารถใช้ Aspose.Words เพื่อลบ SDT ออกจากเอกสารได้หรือไม่

ใช่ คุณสามารถลบ SDT ได้โดยเข้าถึงโหนดของเอกสารและลบ SDT ที่ต้องการ

4. ฉันจะจัดการ SDT ที่ซ้อนกันอยู่ในองค์ประกอบอื่นได้อย่างไร

ใช้ `GetChildNodes` วิธีการที่มีพารามิเตอร์ที่เหมาะสมในการเข้าถึง SDT ที่ซ้อนกัน

5. ฉันควรทำอย่างไรหาก SDT ที่ฉันต้องการแก้ไขไม่ปรากฏในเอกสาร?

ตรวจสอบให้แน่ใจว่า SDT ไม่ถูกซ่อนหรือป้องกัน ตรวจสอบการตั้งค่าเอกสารและให้แน่ใจว่าโค้ดของคุณกำหนดเป้าหมายไปที่ประเภท SDT อย่างถูกต้อง


### ตัวอย่างโค้ดต้นฉบับสำหรับการปรับเปลี่ยนการควบคุมเนื้อหาโดยใช้ Aspose.Words สำหรับ .NET 

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

เสร็จเรียบร้อย! คุณได้ปรับเปลี่ยนตัวควบคุมเนื้อหาประเภทต่างๆ ในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}