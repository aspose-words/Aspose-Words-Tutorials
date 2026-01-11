---
date: 2026-01-11
description: เรียนรู้วิธีแสดงและซ่อนบุ๊กมาร์กและสร้างบุ๊กมาร์กใน Java ด้วย Aspose.Words
  for Java เพื่อการนำทางและจัดการเอกสารอย่างมีประสิทธิภาพ.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: แสดงและซ่อนบุ๊กมาร์กด้วย Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แสดง/ซ่อนบุ๊กมาร์กด้วย Aspose.Words for Java

## แนะนำการใช้บุ๊กมาร์กใน Aspose.Words for Java

บุ๊กมาร์กเป็นฟีเจอร์ที่ทรงพลังใน Aspose.Words for Java ที่ช่วยให้คุณ **สร้าง bookmark java** , นำทางไปยังเนื้อหาเฉพาะ, และแม้กระทั่ง **show hide bookmarks** เมื่อคุณต้องการสร้างเวอร์ชันเอกสารที่แตกต่างกัน ในคู่มือขั้นตอนนี้เราจะอธิบายการสร้าง, การเข้าถึง, การอัปเดต, การคัดลอก, และการสลับการมองเห็นของบุ๊กมาร์ก เพื่อให้คุณควบคุมการจัดการเอกสารได้อย่างเต็มที่

## คำตอบสั้น
- **วัตถุประสงค์หลักของบุ๊กมาร์กคืออะไร?** เพื่อทำเครื่องหมายและดึงส่วนเฉพาะของเอกสารในภายหลัง  
- **ฉันสามารถซ่อนเครื่องหมายบุ๊กมาร์กในผลลัพธ์สุดท้ายได้หรือไม่?** ได้ — ใช้ API show/hide เพื่อสลับการมองเห็น  
- **ฉันจะสร้างบุ๊กมาร์กภายในเซลล์ตารางอย่างไร?** เริ่มและจบบุ๊กมาร์กด้วย `DocumentBuilder` ขณะที่เคอร์เซอร์อยู่ภายในเซลล์นั้น  
- **สามารถคัดลอกข้อความที่มีบุ๊กมาร์กไปยังเอกสารอื่นได้หรือไม่?** แน่นอน — ใช้ `NodeImporter` เพื่อรักษาการฟอร์แมต  
- **ต้องใช้เวอร์ชันใดของ Aspose.Words?** เวอร์ชันล่าสุดใดก็ได้; โค้ดทำงานกับบิลด์ 2026 ล่าสุด

## “show hide bookmarks” คืออะไร?

ฟีเจอร์ **show hide bookmarks** ช่วยให้คุณแสดงหรือซ่อนตัวแบ่งบุ๊กมาร์กในเอกสารที่บันทึกไว้โดยโปรแกรมได้ สิ่งนี้เป็นประโยชน์เมื่อคุณต้องการสร้างผลลัพธ์ที่สะอาดสำหรับผู้ใช้สุดท้าย แต่ยังคงเก็บข้อมูลบุ๊กมาร์กไว้สำหรับการประมวลผลภายใน

## ทำไมต้องใช้บุ๊กมาร์กในการอัตโนมัติเอกสารด้วย Java?

- **การนำทางที่มีประสิทธิภาพ** – กระโดดตรงไปยังส่วนต่าง ๆ โดยไม่ต้องสแกนไฟล์ทั้งหมด  
- **การสร้างเนื้อหาแบบไดนามิก** – แทรก, แทนที่, หรือเอาข้อความที่เชื่อมโยงกับบุ๊กมาร์กออก  
- **การมองเห็นแบบมีเงื่อนไข** – แสดงหรือซ่อนเครื่องหมายบุ๊กมาร์กตามการตั้งค่าผู้ใช้หรือรูปแบบผลลัพธ์  
- **การนำกลับมาใช้ใหม่** – คัดลอกส่วนที่มีบุ๊กมาร์กระหว่างเอกสารพร้อมคงสไตล์เดิม

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK) 8 หรือสูงกว่า  
- ไลบรารี Aspose.Words for Java ที่เพิ่มในโปรเจกต์ของคุณ (Maven/Gradle หรือ JAR)  
- ความคุ้นเคยพื้นฐานกับคลาส `Document` และ `DocumentBuilder`

## คู่มือขั้นตอน

### ขั้นตอนที่ 1: สร้างบุ๊กมาร์ก (create bookmark java)

เพื่อเพิ่มบุ๊กมาร์ก คุณต้องเริ่มต้น, เขียนเนื้อหา, แล้วจบการสร้าง ตัวอย่างนี้สร้างบุ๊กมาร์กง่าย ๆ ชื่อ **My Bookmark**  

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### ขั้นตอนที่ 2: เข้าถึงบุ๊กมาร์ก (access bookmarks java)

คุณสามารถดึงบุ๊กมาร์กได้โดยใช้ดัชนีเริ่มจากศูนย์หรือโดยชื่อ โค้ดด้านล่างแสดงวิธีทั้งสองแบบ  

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### ขั้นตอนที่ 3: อัปเดตข้อมูลบุ๊กมาร์ก (update bookmark text)

คุณอาจเปลี่ยนชื่อบุ๊กมาร์กหรือแทนที่ข้อความของมันได้ ซึ่งเป็นประโยชน์เมื่อเอกสารพื้นฐานมีการเปลี่ยนแปลง  

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### ขั้นตอนที่ 4: ทำงานกับข้อความที่มีบุ๊กมาร์ก (copy bookmarked text)

การคัดลอกส่วนที่มีบุ๊กมาร์กไปยังเอกสารอื่นพร้อมคงฟอร์แมตเดิมทำได้ง่ายด้วย `NodeImporter`  

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### ขั้นตอนที่ 5: แสดงและซ่อนบุ๊กมาร์ก (show hide bookmarks)

ตัวอย่างโค้ดต่อไปนี้แสดงวิธีซ่อนเครื่องหมายบุ๊กมาร์กในไฟล์ที่บันทึกไว้ ส่งค่า `false` เพื่อซ่อน, `true` เพื่อแสดง  

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### ขั้นตอนที่ 6: แก้ไขบุ๊กมาร์กแถวตาราง (bookmark table cell)

เมื่อบุ๊กมาร์กข้ามหลายแถวตารางอาจเกิดการพันกัน วิธีการต่อไปนี้ช่วยแยกและให้คุณลบแถวเฉพาะโดยอ้างอิงบุ๊กมาร์กของมัน  

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## ปัญหาที่พบบ่อยและวิธีแก้

| ปัญหา | วิธีแก้ |
|-------|----------|
| **ไม่พบบุ๊กมาร์ก** | ตรวจสอบว่าชื่อบุ๊กมาร์กตรงกันอย่างแม่นยำ (แยกแยะตัวพิมพ์) และว่าเอกสารถูกบันทึกหลังจากสร้าง |
| **ข้อความที่คัดลอกสูญเสียฟอร์แมต** | ใช้ `ImportFormatMode.KEEP_SOURCE_FORMATTING` กับ `NodeImporter` ตามที่แสดงในขั้นตอน 4 |
| **การแสดง/ซ่อนไม่ส่งผลต่อผลลัพธ์** | ตรวจสอบว่าคุณเรียก `showHideBookmarkedContent` **ก่อน** บันทึกเอกสาร |
| **บุ๊กมาร์กภายในเซลล์ตารางถูกละเลย** | เรียกเมธอด start/end ขณะเคอร์เซอร์ของ builder อยู่ภายในเซลล์เป้าหมาย |

## คำถามที่พบบ่อย

**ถาม: จะสร้างบุ๊กมาร์กในเซลล์ตารางอย่างไร?**  
ตอบ: ใช้ `DocumentBuilder` ย้ายเคอร์เซอร์ไปยังเซลล์ที่ต้องการ แล้วเรียก `startBookmark` และ `endBookmark` รอบเนื้อหาในเซลล์นั้น  

**ถาม: สามารถคัดลอกบุ๊กมาร์กไปยังเอกสารอื่นได้หรือไม่?**  
ตอบ: ได้ — ใช้คลาส `NodeImporter` (ดูขั้นตอน 4) เพื่อนำเข้าน็อดที่มีบุ๊กมาร์กพร้อมคงฟอร์แมตต้นฉบับ  

**ถาม: จะลบแถวโดยอ้างอิงบุ๊กมาร์กได้อย่างไร?**  
ตอบ: ก่อนอื่นค้นหาแถวที่มีบุ๊กมาร์กนั้น แล้วเรียก `remove` บนโนดแถวนั้น (ตามที่แสดงในขั้นตอน 6)  

**ถาม: ตัวอย่างการใช้งานบุ๊กมาร์กที่พบบ่อยคืออะไร?**  
ตอบ: สร้างสารบัญ, ดึงส่วนเฉพาะสำหรับรายงาน, และอัตโนมัติการประกอบเอกสารตามการเลือกของผู้ใช้  

**ถาม: จะหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words for Java ได้จากที่ไหน?**  
ตอบ: สำหรับเอกสารรายละเอียดและการดาวน์โหลด, เยี่ยมชม [เอกสาร Aspose.Words for Java](https://reference.aspose.com/words/java/)  

---

**อัปเดตล่าสุด:** 2026-01-11  
**ทดสอบกับ:** Aspose.Words for Java 24.11 (2026)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}