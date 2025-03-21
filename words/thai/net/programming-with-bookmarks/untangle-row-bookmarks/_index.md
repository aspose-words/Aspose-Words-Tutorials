---
title: แก้ให้หายยุ่งที่คั่นหน้าแถวในเอกสาร Word
linktitle: แก้ให้หายยุ่งที่คั่นหน้าแถวในเอกสาร Word
second_title: Aspose.Words API การประมวลผลเอกสาร
description: แก้บุ๊กมาร์กแถวที่พันกันในเอกสาร Word ของคุณอย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET คู่มือนี้จะแนะนำคุณตลอดกระบวนการเพื่อการจัดการบุ๊กมาร์กที่สะอาดและปลอดภัยยิ่งขึ้น
weight: 10
url: /th/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แก้ให้หายยุ่งที่คั่นหน้าแถวในเอกสาร Word

## การแนะนำ

คุณเคยพบกับสถานการณ์ที่การลบแถวในเอกสาร Word ด้วยบุ๊กมาร์กทำให้บุ๊กมาร์กอื่น ๆ ในแถวที่อยู่ติดกันยุ่งเหยิงหรือไม่? สิ่งนี้น่าหงุดหงิดอย่างยิ่ง โดยเฉพาะอย่างยิ่งเมื่อต้องรับมือกับตารางที่ซับซ้อน โชคดีที่ Aspose.Words สำหรับ .NET นำเสนอโซลูชั่นอันทรงพลัง: การแยกบุ๊กมาร์กแถวที่พันกัน 

คู่มือนี้จะแนะนำคุณตลอดกระบวนการแกะที่คั่นแถวในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET เราจะแบ่งโค้ดออกเป็นขั้นตอนที่เข้าใจง่าย และอธิบายวัตถุประสงค์ของแต่ละฟังก์ชัน ซึ่งจะทำให้คุณสามารถจัดการกับปัญหาบุ๊กมาร์กที่น่ารำคาญเหล่านั้นได้อย่างมั่นใจ

## ข้อกำหนดเบื้องต้น

ก่อนที่จะดำน้ำ คุณจะต้องมีสิ่งต่อไปนี้:

1.  Aspose.Words สำหรับ .NET: ไลบรารีเชิงพาณิชย์นี้มีฟังก์ชันการทำงานสำหรับการทำงานกับเอกสาร Word โดยทางโปรแกรม 2. คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/) หรือซื้อใบอนุญาตจาก[ซื้อ](https://purchase.aspose.com/buy).
3. สภาพแวดล้อมการพัฒนา AC#: Visual Studio หรือ C# IDE อื่น ๆ จะทำงานได้อย่างสมบูรณ์
4. เอกสาร Word ที่มีบุ๊กมาร์กแถว: เราจะใช้เอกสารตัวอย่างชื่อ "บุ๊กมาร์กคอลัมน์ตาราง.docx" เพื่อวัตถุประสงค์ในการสาธิต

## นำเข้าเนมสเปซ

ขั้นตอนแรกเกี่ยวข้องกับการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ เนมสเปซเหล่านี้ให้การเข้าถึงคลาสและฟังก์ชันการทำงานที่เราจะใช้จาก Aspose.Words สำหรับ .NET:

```csharp
using Aspose.Words;
using System;
```

## ขั้นตอนที่ 1: โหลดเอกสาร Word

 เราเริ่มต้นด้วยการโหลดเอกสาร Word ที่มีบุ๊กมาร์กแถวที่พันกัน ที่`Document` คลาสจัดการการจัดการเอกสารใน Aspose.Words ต่อไปนี้เป็นวิธีโหลดเอกสาร:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // แทนที่ด้วยตำแหน่งเอกสารของคุณ
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 อย่าลืมเปลี่ยน`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงไปยังไฟล์ "คอลัมน์ตาราง bookmarks.docx" ของคุณ

## ขั้นตอนที่ 2: แก้ให้หายยุ่งที่คั่นหน้าแถว

 นี่คือจุดที่ความมหัศจรรย์เกิดขึ้น! ที่`Untangle` ฟังก์ชั่นดูแลการคลี่บุ๊กมาร์กแถว มาดูรายละเอียดการทำงานของมันกัน:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // รับแถวพาเรนต์ของทั้งบุ๊กมาร์กและส่วนท้ายของบุ๊กมาร์ก
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // ตรวจสอบว่าแถวถูกต้องและอยู่ติดกัน
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //ย้ายส่วนท้ายของบุ๊กมาร์กไปยังย่อหน้าสุดท้ายของเซลล์สุดท้ายของแถวบนสุด
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

ต่อไปนี้เป็นคำอธิบายทีละขั้นตอนว่าโค้ดทำอะไรได้บ้าง:

 เราวนซ้ำบุ๊กมาร์กทั้งหมดในเอกสารโดยใช้`foreach` วนซ้ำ
สำหรับแต่ละบุ๊กมาร์ก เราจะดึงข้อมูลแถวพาเรนต์ของทั้งจุดเริ่มต้นบุ๊กมาร์ก (`bookmark.BookmarkStart`) และส่วนท้ายของบุ๊กมาร์ก (`bookmark.BookmarkEnd` ) โดยใช้`GetAncestor` วิธี.
จากนั้นเราตรวจสอบว่าพบทั้งสองแถวหรือไม่ (`row1 != null`และ`row2 != null`) และหากเป็นแถวที่อยู่ติดกัน (`row1.NextSibling == row2`- เพื่อให้แน่ใจว่าเราจะแก้ไขเฉพาะบุ๊กมาร์กที่ขยายข้ามแถวที่อยู่ติดกันเท่านั้น
หากตรงตามเงื่อนไข เราจะย้ายโหนดสิ้นสุดบุ๊กมาร์กไปยังจุดสิ้นสุดของย่อหน้าสุดท้ายในเซลล์สุดท้ายของแถวบนสุด (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) แกะพวกมันออกได้อย่างมีประสิทธิภาพ

## ขั้นตอนที่ 3: ลบแถวด้วยบุ๊กมาร์ก

 ตอนนี้บุ๊กมาร์กไม่พันกันแล้ว เราสามารถลบแถวได้อย่างปลอดภัยโดยใช้ชื่อบุ๊กมาร์ก ที่`DeleteRowByBookmark` ฟังก์ชั่นจัดการงานนี้:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

นี่คือรายละเอียดของฟังก์ชันนี้:

เราใช้ชื่อบุ๊กมาร์ก (`bookmarkName`) เป็นอินพุต
 เราดึงข้อมูลวัตถุบุ๊กมาร์กที่เกี่ยวข้องโดยใช้`doc.Range.Bookmarks[bookmarkName]`.
จากนั้นเราจะเริ่มใช้แถวพาเรนต์ของบุ๊กมาร์ก`GetAncestor` (คล้ายกับ`Untangle` การทำงาน).
สุดท้าย เราจะตรวจสอบว่ามีบุ๊กมาร์กและแถวอยู่หรือไม่ (`bookmark != null` และ

## ขั้นตอนที่ 4: ตรวจสอบการแกะออก

 ในขณะที่`Untangle` ฟังก์ชั่นควรมั่นใจในความปลอดภัยของบุ๊กมาร์กอื่น ๆ ถือเป็นแนวปฏิบัติที่ดีในการตรวจสอบ ต่อไปนี้คือวิธีที่เราสามารถตรวจสอบได้ว่ากระบวนการแกะออกไม่ได้ลบจุดสิ้นสุดของบุ๊กมาร์กอื่นโดยไม่ได้ตั้งใจหรือไม่:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

ข้อมูลโค้ดนี้จะตรวจสอบว่าส่วนท้ายของบุ๊กมาร์กชื่อ "ROW1" ยังคงมีอยู่หรือไม่หลังจากลบแถวที่มีบุ๊กมาร์ก "ROW2" แล้ว หากเป็นโมฆะ จะมีข้อยกเว้นเกิดขึ้น ซึ่งบ่งชี้ถึงปัญหากับกระบวนการที่ไม่พันกัน 

## ขั้นตอนที่ 5: บันทึกเอกสาร

 สุดท้ายนี้ หลังจากที่คลี่บุ๊กมาร์กออกและอาจลบแถวแล้ว ให้บันทึกเอกสารที่แก้ไขโดยใช้`Save` วิธี:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

วิธีนี้จะบันทึกเอกสารพร้อมกับบุ๊กมาร์กที่ไม่พันกันและแถวที่ถูกลบภายใต้ชื่อไฟล์ใหม่ "WorkingWithBookmarks.UntangleRowBookmarks.docx" 

## บทสรุป

 โดยทำตามขั้นตอนเหล่านี้และใช้งาน`Untangle`คุณสามารถแก้ให้หายยุ่งบุ๊กมาร์กแถวในเอกสาร Word ของคุณได้อย่างมีประสิทธิภาพด้วย Aspose.Words สำหรับ .NET เพื่อให้แน่ใจว่าการลบแถวด้วยบุ๊กมาร์กจะไม่ทำให้เกิดผลลัพธ์ที่ไม่ได้ตั้งใจกับบุ๊กมาร์กอื่นๆ ในแถวที่อยู่ติดกัน อย่าลืมแทนที่ตัวยึดตำแหน่งเช่น`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางและชื่อไฟล์ที่แท้จริงของคุณ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET ฟรีหรือไม่

 Aspose.Words สำหรับ .NET เป็นไลบรารีเชิงพาณิชย์พร้อมให้ทดลองใช้ฟรี คุณสามารถดาวน์โหลดได้จาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/).

### ฉันสามารถแก้ให้หายยุ่งบุ๊กมาร์กแถวด้วยตนเองใน Word ได้หรือไม่

แม้ว่าในทางเทคนิคจะเป็นไปได้ แต่การแกะบุ๊กมาร์กใน Word ด้วยตนเองอาจเป็นเรื่องที่น่าเบื่อและเกิดข้อผิดพลาดได้ง่าย Aspose.Words สำหรับ .NET จะทำให้กระบวนการนี้เป็นไปโดยอัตโนมัติ ซึ่งช่วยประหยัดเวลาและความพยายามของคุณ

###  จะเกิดอะไรขึ้นถ้า`Untangle` function encounters an error?

รหัสนี้มีตัวจัดการข้อยกเว้นที่ส่งข้อยกเว้นหากกระบวนการแกะออกโดยบังเอิญลบจุดสิ้นสุดของบุ๊กมาร์กอื่น คุณสามารถปรับแต่งการจัดการข้อผิดพลาดนี้ให้เหมาะกับความต้องการเฉพาะของคุณได้

### ฉันสามารถใช้รหัสนี้เพื่อแก้ให้หายยุ่งบุ๊กมาร์กในแถวที่ไม่อยู่ติดกันได้หรือไม่

ขณะนี้โค้ดมุ่งเน้นไปที่บุ๊กมาร์กที่ไม่พันกันซึ่งครอบคลุมแถวที่อยู่ติดกัน การแก้ไขโค้ดเพื่อจัดการแถวที่ไม่อยู่ติดกันจะต้องใช้ตรรกะเพิ่มเติมเพื่อระบุและจัดการสถานการณ์เหล่านั้น

### มีข้อจำกัดในการใช้แนวทางนี้หรือไม่?

วิธีการนี้จะถือว่าบุ๊กมาร์กมีการกำหนดไว้อย่างดีภายในเซลล์ตาราง หากวางที่คั่นหน้าไว้นอกเซลล์หรือในตำแหน่งที่ไม่คาดคิด กระบวนการแยกส่วนที่พันกันอาจไม่ทำงานตามที่ตั้งใจไว้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
