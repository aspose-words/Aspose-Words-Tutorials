---
"description": "เรียนรู้วิธีแทรก FieldIncludeText โดยไม่ใช้ DocumentBuilder ใน Aspose.Words สำหรับ .NET ด้วยคำแนะนำทีละขั้นตอนโดยละเอียดของเรา"
"linktitle": "แทรก FieldIncludeText โดยไม่ต้องใช้ตัวสร้างเอกสาร"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "แทรกฟิลด์รวมข้อความโดยไม่ต้องใช้ตัวสร้างเอกสาร"
"url": "/th/net/working-with-fields/insert-field-include-text-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกฟิลด์รวมข้อความโดยไม่ต้องใช้ตัวสร้างเอกสาร

## การแนะนำ

ในโลกของการจัดการและจัดการเอกสารอัตโนมัติ Aspose.Words สำหรับ .NET ถือเป็นเครื่องมือที่มีประสิทธิภาพ วันนี้ เราจะมาแนะนำรายละเอียดเกี่ยวกับวิธีการแทรก FieldIncludeText โดยไม่ใช้ DocumentBuilder บทช่วยสอนนี้จะแนะนำคุณทีละขั้นตอน เพื่อให้คุณเข้าใจแต่ละส่วนของโค้ดและวัตถุประสงค์ของโค้ด

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการแล้ว:

1. Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งเวอร์ชันล่าสุดแล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา .NET: IDE ที่เข้ากันได้กับ .NET เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะช่วยให้คุณทำตามได้

## นำเข้าเนมสเปซ

อันดับแรก เราต้องนำเข้าเนมสเปซที่จำเป็น เนมสเปซเหล่านี้ช่วยให้เข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการจัดการเอกสาร Word ได้

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

ตอนนี้เรามาแบ่งตัวอย่างออกเป็นหลายขั้นตอน แต่ละขั้นตอนจะได้รับการอธิบายอย่างละเอียดเพื่อให้เข้าใจชัดเจน

## ขั้นตอนที่ 1: ตั้งค่าเส้นทางไดเร็กทอรี

ขั้นตอนแรกคือการกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ ซึ่งเป็นที่ที่เอกสาร Word ของคุณจะถูกเก็บและเข้าถึง

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ขั้นตอนที่ 2: สร้างเอกสารและย่อหน้า

ขั้นต่อไป เราจะสร้างเอกสารใหม่และย่อหน้าภายในเอกสารนั้น ย่อหน้าจะประกอบด้วยฟิลด์ FieldIncludeText

```csharp
// สร้างเอกสารและย่อหน้า
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## ขั้นตอนที่ 3: แทรกฟิลด์ FieldIncludeText

ตอนนี้เราแทรกฟิลด์ FieldIncludeText ลงในย่อหน้า ฟิลด์นี้ช่วยให้คุณสามารถรวมข้อความจากเอกสารอื่นได้

```csharp
// แทรกฟิลด์ FieldIncludeText
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## ขั้นตอนที่ 4: ตั้งค่าคุณสมบัติฟิลด์

เราจำเป็นต้องระบุคุณสมบัติสำหรับฟิลด์ FieldIncludeText ซึ่งรวมถึงการตั้งชื่อบุ๊กมาร์กและเส้นทางเต็มของเอกสารต้นฉบับ

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## ขั้นตอนที่ 5: ผนวกย่อหน้าลงในเอกสาร

เมื่อตั้งค่าฟิลด์เรียบร้อยแล้ว เราจะผนวกย่อหน้าเข้าในเนื้อหาส่วนแรกของเอกสาร

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## ขั้นตอนที่ 6: อัปเดตฟิลด์

ก่อนที่จะบันทึกเอกสาร เราจำเป็นต้องอัปเดต FieldIncludeText เพื่อให้แน่ใจว่าดึงเนื้อหาที่ถูกต้องจากเอกสารต้นฉบับ

```csharp
fieldIncludeText.Update();
```

## ขั้นตอนที่ 7: บันทึกเอกสาร

สุดท้ายเราบันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้! ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถแทรก FieldIncludeText ได้อย่างง่ายดายโดยไม่ต้องใช้ DocumentBuilder ใน Aspose.Words สำหรับ .NET แนวทางนี้ช่วยให้รวมเนื้อหาจากเอกสารหนึ่งไปยังอีกเอกสารหนึ่งได้อย่างคล่องตัว ทำให้การทำงานอัตโนมัติของเอกสารของคุณง่ายขึ้นมาก

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?  
Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word ในแอปพลิเคชัน .NET ช่วยให้สามารถสร้าง แก้ไข และแปลงเอกสารด้วยโปรแกรมได้

### เหตุใดจึงต้องใช้ FieldIncludeText?  
FieldIncludeText มีประโยชน์สำหรับการรวมเนื้อหาจากเอกสารหนึ่งไปยังอีกเอกสารหนึ่งแบบไดนามิก ช่วยให้เอกสารมีความเป็นโมดูลและบำรุงรักษาได้มากขึ้น

### ฉันสามารถใช้วิธีนี้เพื่อรวมข้อความจากรูปแบบไฟล์อื่นได้หรือไม่  
FieldIncludeText ทำงานกับเอกสาร Word โดยเฉพาะ สำหรับรูปแบบอื่น คุณอาจต้องใช้วิธีการหรือคลาสอื่นที่ Aspose.Words จัดเตรียมไว้ให้

### Aspose.Words สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่  
ใช่ Aspose.Words สำหรับ .NET รองรับ .NET Framework, .NET Core และ .NET 5/6

### ฉันจะได้รับรุ่นทดลองใช้งาน Aspose.Words สำหรับ .NET ฟรีได้อย่างไร  
คุณสามารถรับการทดลองใช้ฟรีได้จาก [ที่นี่](https://releases-aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}