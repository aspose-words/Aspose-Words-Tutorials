---
"description": "เรียนรู้วิธีแทรกวัตถุ OLE เป็นไอคอนในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อปรับปรุงเอกสารของคุณ"
"linktitle": "แทรกวัตถุ Ole ในเอกสาร Word เป็นไอคอน"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "แทรกวัตถุ Ole ในเอกสาร Word เป็นไอคอน"
"url": "/th/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกวัตถุ Ole ในเอกสาร Word เป็นไอคอน

## การแนะนำ

คุณเคยจำเป็นต้องฝังวัตถุ OLE เช่น งานนำเสนอ PowerPoint หรือสเปรดชีต Excel ลงในเอกสาร Word หรือไม่ แต่ต้องการให้ปรากฏเป็นไอคอนเล็กๆ ที่สวยงามแทนที่จะเป็นวัตถุแบบเต็มๆ ใช่แล้ว คุณมาถูกที่แล้ว! ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับวิธีการแทรกวัตถุ OLE เป็นไอคอนในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เมื่ออ่านคู่มือนี้จบ คุณจะสามารถผสานวัตถุ OLE ลงในเอกสารได้อย่างราบรื่น ทำให้เอกสารโต้ตอบได้และดึงดูดสายตามากขึ้น

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกรายละเอียด มาดูสิ่งที่คุณต้องการกันก่อน:

1. Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET แล้ว หากคุณยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดได้จาก [หน้าวางจำหน่าย Aspose](https://releases-aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: คุณต้องมีสภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# จะเป็นประโยชน์

## นำเข้าเนมสเปซ

ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งถือเป็นสิ่งสำคัญสำหรับการเข้าถึงฟังก์ชันไลบรารี Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ในการเริ่มต้น คุณต้องสร้างอินสแตนซ์เอกสาร Word ใหม่

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

โค้ดชิ้นนี้จะเริ่มต้นเอกสาร Word ใหม่และวัตถุ DocumentBuilder ซึ่งใช้เพื่อสร้างเนื้อหาของเอกสาร

## ขั้นตอนที่ 2: แทรกวัตถุ OLE เป็นไอคอน

ตอนนี้เรามาแทรกวัตถุ OLE เป็นไอคอนกัน `InsertOleObjectAsIcon` วิธีการของคลาส DocumentBuilder ถูกใช้เพื่อจุดประสงค์นี้

```csharp
builder.InsertOleObjectAsIcon("path_to_your_presentation.pptx", false, "path_to_your_icon.ico", "My embedded file");
```

มาแยกวิธีการนี้กัน:
- `"path_to_your_presentation.pptx"`:นี่คือเส้นทางไปยังวัตถุ OLE ที่คุณต้องการฝัง
- `false`:พารามิเตอร์บูลีนนี้ระบุว่าจะแสดงวัตถุ OLE เป็นไอคอนหรือไม่ เนื่องจากเราต้องการไอคอน เราจึงตั้งค่าเป็น `false`-
- `"path_to_your_icon.ico"`:นี่คือเส้นทางไปยังไฟล์ไอคอนที่คุณต้องการใช้สำหรับอ็อบเจ็กต์ OLE
- `"My embedded file"`:นี่คือป้ายกำกับที่จะปรากฏอยู่ใต้ไอคอน

## ขั้นตอนที่ 3: บันทึกเอกสาร

สุดท้ายคุณต้องบันทึกเอกสาร เลือกไดเรกทอรีที่คุณต้องการบันทึกไฟล์

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
```

บรรทัดโค้ดนี้จะบันทึกเอกสารไปยังเส้นทางที่ระบุ

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการแทรกวัตถุ OLE เป็นไอคอนในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว เทคนิคนี้ไม่เพียงแต่ช่วยในการฝังวัตถุที่ซับซ้อนเท่านั้น แต่ยังช่วยให้เอกสารของคุณดูเป็นระเบียบเรียบร้อยและเป็นมืออาชีพอีกด้วย

## คำถามที่พบบ่อย

### ฉันสามารถใช้ประเภทของวัตถุ OLE ที่แตกต่างกันกับวิธีนี้ได้หรือไม่

ใช่ คุณสามารถฝังวัตถุ OLE ประเภทต่างๆ เช่น สเปรดชีต Excel, งานนำเสนอ PowerPoint และแม้แต่ PDF

### ฉันจะได้รับรุ่นทดลองใช้งาน Aspose.Words สำหรับ .NET ฟรีได้อย่างไร

คุณสามารถรับการทดลองใช้ฟรีได้จาก [หน้าวางจำหน่าย Aspose](https://releases-aspose.com/).

### OLE Object คืออะไร?

OLE (Object Linking and Embedding) เป็นเทคโนโลยีที่พัฒนาโดย Microsoft ซึ่งช่วยให้สามารถฝังและเชื่อมโยงกับเอกสารและวัตถุอื่นๆ ได้

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?

ใช่ Aspose.Words สำหรับ .NET ต้องมีใบอนุญาต คุณสามารถซื้อได้จาก [หน้าสั่งซื้อ Aspose](https://purchase.aspose.com/buy) หรือรับ [ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อการประเมินผล

### ฉันสามารถหาบทช่วยสอนเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน

คุณสามารถค้นหาบทช่วยสอนและเอกสารเพิ่มเติมได้ที่ [หน้าเอกสาร Aspose](https://reference-aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}