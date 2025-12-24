---
date: '2025-12-10'
description: เรียนรู้วิธีสร้างบุ๊กมาร์กซ้อนและบันทึกบุ๊กมาร์ก PDF ของ Word ด้วย Aspose.Words
  for Java เพื่อจัดระเบียบการนำทาง PDF อย่างมีประสิทธิภาพ
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: สร้างบุ๊กมาร์กซ้อนใน PDF ด้วย Aspose.Words Java
url: /th/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สร้างบุ๊กมาร์กแบบซ้อนกันใน PDF ด้วย Aspose.Words Java

## บทนำ
หากคุณต้องการ **สร้างบุ๊กมาร์กแบบซ้อนกัน** ใน PDF ที่สร้างจากเอกสาร Word คุณมาถูกที่แล้ว ในบทแนะนำนี้เราจะเดินผ่านกระบวนการทั้งหมดโดยใช้ Aspose.Words for Java ตั้งแต่การตั้งค่าห้องสมุดไปจนถึงการกำหนดระดับโครงร่างของบุ๊กมาร์กและสุดท้าย **บันทึกบุ๊กมาร์ก Word PDF** เพื่อให้ PDF สุดท้ายนำทางได้ง่าย

**สิ่งที่คุณจะได้เรียนรู้**
- วิธีตั้งค่า Aspose.Words for Java
- วิธี **สร้างบุ๊กมาร์กแบบซ้อนกัน** ภายในเอกสาร Word
- วิธีกำหนดระดับโครงร่างเพื่อการนำทาง PDF ที่ชัดเจน
- วิธี **บันทึกบุ๊กมาร์ก Word PDF** ด้วย PdfSaveOptions

## คำตอบสั้น
- **เป้าหมายหลักคืออะไร?** เพื่อสร้างบุ๊กมาร์กแบบซ้อนกันและบันทึกบุ๊กมาร์ก Word PDF ในไฟล์ PDF เดียว  
- **ต้องใช้ไลบรารีอะไร?** Aspose.Words for Java (เวอร์ชัน 25.3 หรือใหม่กว่า)  
- **ต้องมีลิขสิทธิ์หรือไม่?** ทดลองใช้ฟรีได้สำหรับการทดสอบ; จำเป็นต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง  
- **สามารถควบคุมระดับโครงร่างได้หรือไม่?** ได้, โดยใช้ `PdfSaveOptions` และ `BookmarksOutlineLevelCollection`  
- **เหมาะกับเอกสารขนาดใหญ่หรือไม่?** ใช่, หากจัดการหน่วยความจำและการเพิ่มประสิทธิภาพทรัพยากรอย่างเหมาะสม

## “สร้างบุ๊กมาร์กแบบซ้อนกัน” คืออะไร?
การสร้างบุ๊กมาร์กแบบซ้อนกันหมายถึงการวางบุ๊กมาร์กหนึ่งภายในอีกบุ๊กมาร์กหนึ่ง, สร้างโครงสร้างแบบลำดับชั้นที่สะท้อนส่วนต่าง ๆ ของเอกสารของคุณ โครงสร้างนี้จะแสดงในแถบนำทางของ PDF, ทำให้ผู้อ่านสามารถกระโดดไปยังบทหรือส่วนย่อยที่ต้องการได้โดยตรง

## ทำไมต้องใช้ Aspose.Words for Java เพื่อบันทึกบุ๊กมาร์ก Word PDF?
Aspose.Words มี API ระดับสูงที่ทำให้คุณไม่ต้องจัดการกับการปรับแต่ง PDF ระดับล่าง, ทำให้คุณมุ่งเน้นที่โครงสร้างเนื้อหาแทนรายละเอียดรูปแบบไฟล์ นอกจากนี้ยังคงรักษาฟีเจอร์ทั้งหมดของ Word (สไตล์, รูปภาพ, ตาราง) พร้อมให้คุณควบคุมลำดับชั้นของบุ๊กมาร์กได้เต็มที่

## ข้อกำหนดเบื้องต้น
- **ไลบรารี**: Aspose.Words for Java (v25.3+)  
- **สภาพแวดล้อมการพัฒนา**: JDK 8 หรือใหม่กว่า, IDE เช่น IntelliJ IDEA หรือ Eclipse  
- **เครื่องมือสร้าง**: Maven หรือ Gradle (ตามที่คุณชอบ)  
- **ความรู้พื้นฐาน**: การเขียนโปรแกรม Java, พื้นฐาน Maven/Gradle

## การตั้งค่า Aspose.Words
เพิ่มไลบรารีลงในโปรเจกต์ของคุณโดยใช้โค้ดสแนปหนึ่งต่อไปนี้

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### การรับลิขสิทธิ์
Aspose.Words เป็นผลิตภัณฑ์เชิงพาณิชย์, แต่คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรี:

1. **ทดลองใช้ฟรี** – ดาวน์โหลดจาก [หน้ารีลีสของ Aspose](https://releases.aspose.com/words/java/) เพื่อทดสอบความสามารถทั้งหมด  
2. **ลิขสิทธิ์ชั่วคราว** – ขอรับได้ที่ [หน้าลิขสิทธิ์ชั่วคราวของ Aspose](https://purchase.aspose.com/temporary-license/) หากต้องการคีย์ระยะสั้น  
3. **ซื้อ** – รับลิขสิทธิ์ถาวรจาก [พอร์ทัลการซื้อของ Aspose](https://purchase.aspose.com/buy)

เมื่อคุณมีไฟล์ `.lic` แล้ว, โหลดมันในขั้นตอนเริ่มต้นของแอปพลิเคชันเพื่อปลดล็อกฟีเจอร์ทั้งหมด

## คู่มือการทำงาน
ต่อไปนี้เป็นขั้นตอนแบบละเอียด แต่ละบล็อกโค้ดจะคงไว้ตามต้นฉบับเพื่อรักษาฟังก์ชันการทำงาน

### วิธีสร้างบุ๊กมาร์กแบบซ้อนกันในเอกสาร Word
#### ขั้นตอนที่ 1: เริ่มต้น และ Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
โค้ดนี้สร้างเอกสาร Word ว่างและอ็อบเจกต์ Builder สำหรับแทรกเนื้อหา

#### ขั้นตอนที่ 2: แทรกบุ๊กมาร์กแรก (พาเรนท์)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### ขั้นตอนที่ 3: ซ้อนบุ๊กมาร์กที่สองไว้ภายในแรก
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### ขั้นตอนที่ 4: ปิดบุ๊กมาร์กภายนอก
```java
builder.endBookmark("Bookmark 1");
```

#### ขั้นตอนที่ 5: เพิ่มบุ๊กมาร์กที่สามแยกออกมา
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### วิธีบันทึกบุ๊กมาร์ก Word PDF และกำหนดระดับโครงร่าง
#### ขั้นตอนที่ 1: ตั้งค่า PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### ขั้นตอนที่ 2: กำหนดระดับโครงร่างให้กับแต่ละบุ๊กมาร์ก
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### ขั้นตอนที่ 3: บันทึกเอกสารเป็น PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## ปัญหาที่พบบ่อยและวิธีแก้
- **บุ๊กมาร์กหาย** – ตรวจสอบว่าแต่ละ `startBookmark` มี `endBookmark` ที่ตรงกัน  
- **ลำดับชั้นไม่ถูกต้อง** – ตรวจสอบให้แน่ใจว่าตัวเลขระดับโครงร่างสอดคล้องกับความสัมพันธ์พาเรนท์‑ชิลด์ที่ต้องการ (เลขน้อย = ระดับสูง)  
- **ไฟล์ขนาดใหญ่** – ลบสไตล์หรือรูปภาพที่ไม่ได้ใช้ก่อนบันทึก, หรือเรียก `doc.optimizeResources()` หากจำเป็น

## การใช้งานในเชิงปฏิบัติ
| สถานการณ์ | ประโยชน์ของบุ๊กมาร์กแบบซ้อนกัน |
|----------|----------------------------|
| สัญญากฎหมาย | กระโดดไปยังข้อและข้อย่อยได้อย่างรวดเร็ว |
| รายงานเทคนิค | นำทางส่วนที่ซับซ้อนและภาคผนวก |
| สื่อการเรียนรู้ออนไลน์ | เข้าถึงบท, บทเรียน, และแบบทดสอบโดยตรง |

## พิจารณาด้านประสิทธิภาพ
- **การใช้หน่วยความจำ** – ประมวลผลเอกสารขนาดใหญ่เป็นชิ้น ๆ หรือใช้ `DocumentBuilder.insertDocument` เพื่อรวมส่วนย่อย  
- **ขนาดไฟล์** – บีบอัดรูปภาพและลบเนื้อหาที่ซ่อนอยู่ก่อนแปลงเป็น PDF

## สรุป
คุณได้เรียนรู้วิธี **สร้างบุ๊กมาร์กแบบซ้อนกัน**, ตั้งค่าระดับโครงร่าง, และ **บันทึกบุ๊กมาร์ก Word PDF** ด้วย Aspose.Words for Java เทคนิคนี้ช่วยปรับปรุงการนำทางใน PDF อย่างมาก ทำให้เอกสารของคุณดูเป็นมืออาชีพและเป็นมิตรต่อผู้ใช้

**ขั้นตอนต่อไป**: ทดลองสร้างลำดับชั้นบุ๊กมาร์กที่ลึกขึ้น, ผสานโลจิกนี้เข้ากับกระบวนการประมวลผลแบบแบตช์, หรือรวมกับ Aspose.PDF เพื่อแก้ไขบุ๊กมาร์กหลังการสร้าง

## คำถามที่พบบ่อย
**ถาม: ฉันจะติดตั้ง Aspose.Words for Java อย่างไร?**  
ตอบ: เพิ่ม dependency ของ Maven หรือ Gradle ตามที่แสดงด้านบน, แล้วโหลดไฟล์ลิขสิทธิ์ของคุณใน runtime

**ถาม: สามารถใช้บุ๊กมาร์กโดยไม่ตั้งค่าระดับโครงร่างได้หรือไม่?**  
ตอบ: ได้, แต่หากไม่มีระดับโครงร่าง แถบนำทางของ PDF จะรายการบุ๊กมาร์กทั้งหมดในระดับเดียวกัน ซึ่งอาจทำให้ผู้อ่านสับสน

**ถาม: มีขีดจำกัดความลึกของการซ้อนบุ๊กมาร์กหรือไม่?**  
ตอบ: ทางเทคนิคไม่มีข้อจำกัด, แต่เพื่อความใช้งานง่าย ควรจำกัดความลึกไว้ที่ประมาณ 3‑4 ระดับ

**ถาม: Aspose จัดการกับเอกสารขนาดใหญ่อย่างไร?**  
ตอบ: ไลบรารีสตรีมข้อมูลและมีเมธอด `optimizeResources()` เพื่อลดการใช้หน่วยความจำ; อย่างไรก็ตาม ควรตรวจสอบ heap ของ JVM อย่างสม่ำเสมอสำหรับไฟล์หลายร้อยหน้า

**ถาม: สามารถแก้ไขบุ๊กมาร์กหลังจากสร้าง PDF แล้วได้หรือไม่?**  
ตอบ: ได้, คุณสามารถใช้ Aspose.PDF for Java เพื่อแก้ไข, เพิ่ม, หรือเอาบุ๊กมาร์กออกจาก PDF ที่มีอยู่

---

**อัปเดตล่าสุด:** 2025-12-10  
**ทดสอบกับ:** Aspose.Words 25.3 for Java  
**ผู้เขียน:** Aspose  

**แหล่งข้อมูล**
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}