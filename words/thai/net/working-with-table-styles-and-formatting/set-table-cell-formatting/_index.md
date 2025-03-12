---
title: สร้างและจัดรูปตารางในเอกสาร Word ด้วย Aspose.Words
weight: 7700
limit: 
description: เรียนรู้วิธีการสร้างและฟอร์มตารางในเอกสาร Word โดยใช้คลาส Aspose.Words DocumentBuilder. รวมคําแนะนําขั้นตอนและรหัสตัวอย่าง
keywords: [Aspose.Words for .NET, create table in Word, format table cell, DocumentBuilder example, Word automation .NET, table formatting, Aspose.Words tutorial, .NET library for Word]
url: /th/net/working-with-table-styles-and-formatting/set-table-cell-formatting/
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างและจัดรูปตารางในเอกสาร Word ด้วย Aspose.Words

Aspose.Words สําหรับ .NET ทําให้การ thao tácเอกสาร Word ง่ายขึ้น ทําให้งานต่างๆ เช่น การสร้างและการฟอร์มเทปตารางง่ายขึ้น โดยใช้ `DocumentBuilder`คลาส, ผู้พัฒนาสามารถสร้างตารางได้อย่างง่ายดาย, ปรับการฟอร์มเมทเซลล์, และใส่เนื้อหาตามโปรแกรม. คู่มือนี้แสดงให้เห็นเป็นระยะทางการสร้างตาราง, ตั้งคุณสมบัติเซลล์ เช่น การใส่และความกว้าง, และเพิ่มเติมบทความในเซลล์. ไม่ว่าคุณกําลังอัตโนมัติรายงานหรือผลิตเอกสาร, คู่มือนี้จะช่วยให้คุณเปิด Aspose.Words ความสามารถเต็มที่ในการฟอร์มเมทเซลล์ของ Word. ลงและเพิ่มโปรเจคต์อัตโนมัติ Word ของคุณวันนี้!

---
{{< tutorial-widget sourcePath="words/net/working-with-table-styles-and-formatting/set-table-cell-formatting" >}}

{{< /blocks/products/pf/tutorial-page-section >}}
{{< blocks/products/pf/tutorial-page-section >}}
## คําแนะนําการติดตั้ง  
ติดตามขั้นตอนนี้เพื่อติดตั้งและใช้ Aspose.Words สําหรับ .NET ในโครงการของคุณ:  

1. ดาวน์โหลด Aspose.Words:  
   ไปเยี่ยม [Aspose.Words สําหรับหน้าดาวน์โหลด .NET](https://releases.aspose.com/words/net/)และดาวน์โหลดเวอร์ชั่นล่าสุดของห้องสมุด  

2. โครงการผ่าน NuGet:  
   เปิดโครงการ .NET ของคุณใน Visual Studio ไปยัง NuGet Package Manager (เครื่องมือ > NuGet Package Manager > การจัดการ NuGet Packages for Solution) ค้นหา "Aspose.Words", และติดตั้งแพ็คเกจ  

   แทนเช่นนั้น กรอกคําสั่งต่อไปนี้ใน คอนโซลผู้จัดการแพคเกจ  
   ```shell
   Install-Package Aspose.Words
   ```  

3. สมัครใบอนุญาต (เป็นทางเลือก)  
   เพื่อกําจัดข้อจํากัดการประเมิน, ใช้ใบอนุญาต ซื้อใบอนุญาตจาก [นี่](https://purchase.aspose.com/buy)หรือรับ[เอกสารชั่วคราว](https://purchase.aspose.com/temporary-license/)จากนั้น ใช้รหัสต่อไปนี้เพื่อใช้ใบอนุญาต  
   ```csharp
   License license = new License();
   license.SetLicense("Aspose.Words.lic");
   ```  

4. เพิ่มความหมาย:  
   รับรอง`"พูดคําพูด"`namespace นําเข้าในโครงการของคุณด้วย:  
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Tables;
   ```  

4. การสมัครใบอนุญาต (ทางเลือก):  
   เพื่อใช้ฉบับเต็ม[ใช้ใบอนุญาต](https://purchase.aspose.com/temporary-license/)หรือใช้ [ทดลองใช้ฟรี](https://releases.aspose.com/words/net/). .
   
## ดูอีกด้วย
[Aspose.Word สําหรับเอกสาร .NET](https://docs.aspose.com/words/net/)
[Aspose.Word สําหรับ .NET References](https://reference.aspose.com/words/net/) 
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
