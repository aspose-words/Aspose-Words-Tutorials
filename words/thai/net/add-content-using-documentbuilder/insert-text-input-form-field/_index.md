---
title: การแทรกช่องฟอร์มป้อนข้อความในเอกสาร Word
linktitle: การแทรกช่องฟอร์มป้อนข้อความในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีแทรกฟิลด์ฟอร์มป้อนข้อความในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยบทช่วยสอนแบบทีละขั้นตอนนี้ เหมาะอย่างยิ่งสำหรับการสร้างฟอร์มแบบโต้ตอบ
weight: 10
url: /th/net/add-content-using-documentbuilder/insert-text-input-form-field/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การแทรกช่องฟอร์มป้อนข้อความในเอกสาร Word

## การแนะนำ

ในบทช่วยสอนนี้ เราจะเจาะลึกเข้าไปในโลกของ Aspose.Words สำหรับ .NET เพื่อเรียนรู้วิธีการแทรกฟิลด์ฟอร์มสำหรับป้อนข้อความในเอกสาร Word เตรียมตัวไว้ให้ดี เพราะเรากำลังจะเริ่มต้นการเดินทางที่จะทำให้การทำงานอัตโนมัติในเอกสารของคุณเป็นเรื่องง่าย ไม่ว่าคุณจะกำลังสร้างฟอร์ม เทมเพลต หรือเอกสารแบบโต้ตอบ การเชี่ยวชาญทักษะนี้จะช่วยยกระดับแอปพลิเคชัน .NET ของคุณไปสู่อีกระดับ

### ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น มีบางสิ่งที่คุณจะต้องมี:

1.  ไลบรารี Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณมีไลบรารี Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น Visual Studio
3. ความเข้าใจพื้นฐานเกี่ยวกับ C#: มีความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และ .NET framework
4.  ใบอนุญาตชั่วคราว (ทางเลือก): หากคุณกำลังประเมิน Aspose.Words คุณอาจต้องการรับ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อหลีกเลี่ยงข้อจำกัดใดๆ

## นำเข้าเนมสเปซ

ก่อนอื่น ให้เตรียมการโดยนำเข้าเนมสเปซที่จำเป็น วิธีนี้จะช่วยให้สามารถใช้คลาสและเมธอด Aspose.Words ได้อย่างง่ายดาย

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

ตอนนี้เรามาแบ่งขั้นตอนออกเป็นขั้นตอนง่ายๆ ที่เข้าใจง่าย แต่ละขั้นตอนมีความสำคัญมาก ดังนั้นโปรดปฏิบัติตามอย่างใกล้ชิด

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ก่อนที่เราจะเริ่มเขียนโค้ด คุณต้องระบุเส้นทางไปยังไดเร็กทอรีเอกสารของคุณก่อน นี่คือที่ที่เอกสาร Word ที่คุณสร้างขึ้นจะถูกบันทึกไว้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ขั้นตอนที่ 2: สร้างเอกสารใหม่

 ต่อไปเราต้องสร้างอินสแตนซ์ใหม่ของ`Document` คลาส นี่คือเอกสาร Word ที่เราจะใช้ในการทำงาน

```csharp
Document doc = new Document();
```

## ขั้นตอนที่ 3: เริ่มต้น DocumentBuilder

 การ`DocumentBuilder` คลาสเป็นเครื่องมือหลักของเราสำหรับการเพิ่มเนื้อหาลงในเอกสาร ลองนึกภาพว่ามันเป็นปากกาที่เขียนบนผืนผ้าใบของเอกสาร Word

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 4: แทรกช่องป้อนข้อความในฟอร์ม

 นี่คือจุดที่เวทมนตร์เกิดขึ้น เราจะใช้`InsertTextInput` วิธีการของ`DocumentBuilder` คลาสสำหรับเพิ่มฟิลด์ฟอร์มสำหรับป้อนข้อความ ฟิลด์ฟอร์มนี้จะช่วยให้ผู้ใช้สามารถป้อนข้อความลงในเอกสารได้

```csharp
builder.InsertTextInput("TextInput", TextFormFieldType.Regular, "", "Hello", 0);
```

- ชื่อ: "TextInput" - นี่คือชื่อของฟิลด์แบบฟอร์ม
-  พิมพ์:`TextFormFieldType.Regular` ระบุว่าช่องฟอร์มนั้นเป็นช่องป้อนข้อความปกติ
- ข้อความเริ่มต้น: "" - นี่คือข้อความเริ่มต้นที่จะแสดงในฟิลด์ฟอร์ม (ว่างเปล่าในกรณีนี้)
- ค่า: “สวัสดี” - ค่าเริ่มต้นของฟิลด์ฟอร์ม
- ความยาวสูงสุด: 0 - ไม่มีการกำหนดขีดจำกัดความยาวของอินพุต

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายเราต้องบันทึกเอกสารไปยังไดเรกทอรีที่ระบุ ซึ่งจะสร้างไฟล์ .docx พร้อมช่องป้อนข้อความแบบแทรก

```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.InsertTextInputFormField.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้แทรกฟิลด์ฟอร์มป้อนข้อความลงในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET นี่เป็นเพียงส่วนเล็กๆ ของรายละเอียดทั้งหมด ด้วย Aspose.Words คุณสามารถทำให้กระบวนการประมวลผลเอกสารของคุณเป็นแบบอัตโนมัติและเพิ่มประสิทธิภาพได้หลายวิธี ตั้งแต่การสร้างเทมเพลตที่ซับซ้อนไปจนถึงการสร้างฟอร์มแบบโต้ตอบ ความเป็นไปได้นั้นไม่มีที่สิ้นสุด

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีการประมวลผลเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word ได้โดยการใช้โปรแกรม

### ฉันสามารถใช้ Aspose.Words ได้ฟรีหรือไม่?
Aspose.Words นำเสนอเวอร์ชันทดลองใช้งานฟรีพร้อมข้อจำกัดบางประการ หากต้องการฟังก์ชันครบถ้วน คุณสามารถซื้อใบอนุญาตหรือรับใบอนุญาตชั่วคราวเพื่อทดลองใช้งาน

### ฟิลด์ฟอร์มอินพุตข้อความใช้ทำอะไร?
ฟิลด์ฟอร์มป้อนข้อความใช้ในเอกสาร Word เพื่อให้ผู้ใช้สามารถป้อนข้อความลงในพื้นที่ที่กำหนดไว้ล่วงหน้า ทำให้เหมาะอย่างยิ่งสำหรับแบบฟอร์มและเทมเพลต

### ฉันจะปรับแต่งลักษณะที่ปรากฏของช่องฟอร์มได้อย่างไร?
 คุณสามารถปรับแต่งลักษณะของช่องฟอร์มได้โดยใช้คุณสมบัติต่างๆ ของ`DocumentBuilder` คลาส เช่น แบบอักษร ขนาด และการจัดตำแหน่ง

### ฉันสามารถหาบทช่วยสอนเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
 คุณสามารถค้นหาบทช่วยสอนและเอกสารเพิ่มเติมได้ที่[หน้าเอกสาร Aspose.Words สำหรับ .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
