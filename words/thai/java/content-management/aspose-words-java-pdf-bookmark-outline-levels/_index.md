---
date: '2026-03-15'
description: เรียนรู้วิธีเพิ่มบุ๊กมาร์ก PDF และตั้งระดับโครงร่างด้วย Aspose.Words
  for Java เพื่อเพิ่มการนำทางและความอ่านง่ายของ PDF
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: เพิ่มบุ๊กมาร์ก PDF และระดับโครงร่างด้วย Aspose.Words Java
url: /th/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มบุ๊กมาร์ค PDF และระดับโครงร่างด้วย Aspose.Words Java

## บทนำ
ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีเพิ่มบุ๊กมาร์ค PDF** และกำหนดระดับโครงร่างของมันโดยใช้ **Aspose.Words for Java** บุ๊กมาร์คที่จัดระเบียบอย่างดีทำให้การนำทางไฟล์ PDF ขนาดใหญ่เป็นเรื่องง่าย ไม่ว่าจะเป็นสัญญากฎหมาย รายงานละเอียด หรือสื่อการเรียนรู้ออนไลน์

**สิ่งที่คุณจะได้เรียน**
- ตั้งค่าและใช้ **Aspose.Words for Java**
- **สร้างบุ๊กมาร์คซ้อนกัน** ในเอกสาร Word
- **วิธีตั้งค่าระดับโครงร่างของบุ๊กมาร์ค** เพื่อให้มีโครงสร้างชัดเจน
- **บันทึกเอกสารเป็น PDF** พร้อมต้นไม้บุ๊กมาร์คที่จัดโครงสร้าง

ให้แน่ใจว่าคุณมีทุกอย่างที่ต้องการก่อนเริ่มทำตามขั้นตอน

### ข้อกำหนดเบื้องต้น
ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:
- **ไลบรารีและการพึ่งพา**: Aspose.Words for Java (เวอร์ชัน 25.3 หรือใหม่กว่า)  
- **การตั้งค่าสภาพแวดล้อม**: ติดตั้ง JDK และ IDE เช่น IntelliJ IDEA หรือ Eclipse  
- **ความรู้พื้นฐาน**: ทักษะการเขียนโปรแกรม Java เบื้องต้นและความคุ้นเคยกับ Maven หรือ Gradle

## คำตอบสั้น
- **เป้าหมายหลักคืออะไร?** เพิ่มบุ๊กมาร์ค PDF และกำหนดระดับโครงร่าง  
- **ต้องใช้ไลบรารีใด?** Aspose.Words for Java (v25.3+)  
- **ต้องมีลิขสิทธิ์หรือไม่?** สามารถใช้รุ่นทดลองฟรีสำหรับการทดสอบ; ต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง  
- **สามารถสร้าง PDF พร้อมบุ๊กมาร์คได้ในขั้นตอนเดียวหรือไม่?** ใช่ — ตั้งค่า `PdfSaveOptions` แล้วเรียก `doc.save`  
- **รองรับการซ้อนกันหรือไม่?** แน่นอน คุณสามารถสร้างระดับบุ๊กมาร์คซ้อนกันได้ไม่จำกัด

## การตั้งค่า Aspose.Words
เริ่มต้นโดยเพิ่มการพึ่งพาที่จำเป็นในโปรเจกต์ของคุณ ตัวอย่างต่อไปนี้แสดงวิธีทำด้วย Maven และ Gradle:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### การรับลิขสิทธิ์
Aspose.Words เป็นผลิตภัณฑ์เชิงพาณิชย์ แต่คุณสามารถเริ่มต้นด้วยรุ่นทดลองฟรีเพื่อสำรวจคุณสมบัติต่าง ๆ

1. **รุ่นทดลองฟรี**: ดาวน์โหลดจาก [หน้าเผยแพร่ของ Aspose](https://releases.aspose.com/words/java/) เพื่อทดสอบความสามารถทั้งหมด  
2. **ลิขสิทธิ์ชั่วคราว**: ขอรับลิขสิทธิ์ชั่วคราวได้ที่ [หน้าลิขสิทธิ์ชั่วคราวของ Aspose](https://purchase.aspose.com/temporary-license/) หากต้องการเวลาประเมินผลเพิ่ม  
3. **ซื้อ**: สำหรับการใช้งานต่อเนื่อง ให้ซื้อลิขสิทธิ์จาก [พอร์ทัลการซื้อของ Aspose](https://purchase.aspose.com/buy)

เมื่อคุณมีไฟล์ลิขสิทธิ์แล้ว ให้ทำการเริ่มต้นในโปรเจกต์เพื่อเปิดใช้งานคุณสมบัติทั้งหมด

## คู่มือการใช้งาน
เราจะเดินผ่านขั้นตอนการทำงานทีละส่วนโดยแบ่งเป็นชิ้นย่อย ๆ

### การสร้างบุ๊กมาร์คซ้อนกัน
**ภาพรวม**: เรียนรู้วิธี **สร้างบุ๊กมาร์คซ้อนกัน** ภายในเอกสาร Word ด้วย Aspose.Words for Java

#### ขั้นตอนที่ 1: เริ่มต้น Document และ Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
โค้ดนี้จะสร้างเอกสาร Word ใหม่และออบเจกต์ Builder ที่ช่วยให้คุณแทรกเนื้อหาและบุ๊กมาร์คได้

#### ขั้นตอนที่ 2: แทรกบุ๊กมาร์คซ้อนกัน
เริ่มด้วยการสร้างบุ๊กมาร์คหลัก:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
จากนั้นให้ซ้อนบุ๊กมาร์คอีกอันหนึ่งไว้ภายใน:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
และปิดบุ๊กมาร์คภายนอกให้เสร็จ:
```java
builder.endBookmark("Bookmark 1");
```

#### ขั้นตอนที่ 3: เพิ่มบุ๊กมาร์คเพิ่มเติม
คุณสามารถเพิ่มบุ๊กมาร์คต่อไปได้ตามต้องการ ตัวอย่างเช่น บุ๊กมาร์คที่สามแยกออกมา:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### การกำหนดระดับโครงร่างของบุ๊กมาร์ค
**ภาพรวม**: จัดระเบียบบุ๊กมาร์คของคุณโดยตั้งค่าระดับโครงร่าง ซึ่งจะกำหนดลำดับชั้นที่ผู้ดู PDF จะเห็น

#### ขั้นตอนที่ 1: ตั้งค่า PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
ตัวเลือกเหล่านี้จะถูกนำไปใช้เมื่อคุณ **บันทึกเอกสารเป็น PDF**

#### ขั้นตอนที่ 2: เพิ่มระดับโครงร่าง
กำหนดระดับให้กับแต่ละบุ๊กมาร์ค; ตัวเลขที่น้อยกว่าจะปรากฏอยู่บนสุดของต้นไม้โครงร่าง:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### ขั้นตอนที่ 3: บันทึกเอกสาร
สุดท้ายให้สร้างไฟล์ PDF พร้อมโครงสร้างบุ๊กมาร์คที่กำหนดไว้:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### เคล็ดลับการแก้ไขปัญหา
- **บุ๊กมาร์คหาย**: ตรวจสอบให้แน่ใจว่า `startBookmark` ทุกตัวมี `endBookmark` ที่ตรงกัน  
- **ระดับไม่ถูกต้อง**: ตรวจสอบลำดับการเพิ่มระดับโครงร่าง; โครงสร้างจะตามตัวเลขระดับที่คุณกำหนด  
- **เอกสารขนาดใหญ่**: ใช้ `doc.removeUnusedResources()` ก่อนบันทึกเพื่อลดขนาด PDF

## การใช้งานในสถานการณ์จริง
ต่อไปนี้เป็นตัวอย่างการใช้งานจริงที่ **การเพิ่มบุ๊กมาร์ค PDF** มีประโยชน์อย่างมาก:

1. **เอกสารกฎหมาย** – กระโดดไปยังข้อ, ภาคผนวก หรือเอกสารแนบได้อย่างรวดเร็ว  
2. **รายงานการเงิน** – นำทางระหว่างส่วนต่าง ๆ, ตาราง, และแผนภูมิ  
3. **สื่อการเรียนรู้ออนไลน์** – ให้ผู้อ่านเข้าถึงสารบัญที่คลิกได้

## พิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ**: เมื่อประมวลผลไฟล์ Word ขนาดใหญ่มาก ให้เรียก `System.gc()` หลังบันทึกเพื่อคืนหน่วยความจำ  
- **ขนาดเอกสาร**: ลบรูปภาพที่ไม่จำเป็นหรือข้อความที่ซ่อนอยู่ก่อนสร้างบุ๊กมาร์ค เพื่อให้ PDF สุดท้ายมีขนาดเบา

## สรุป
คุณมีวิธีที่สมบูรณ์และพร้อมใช้งานในระดับผลิตเพื่อ **เพิ่มบุ๊กมาร์ค PDF**, กำหนดระดับโครงร่าง, และ **สร้าง PDF พร้อมบุ๊กมาร์ค** ด้วย Aspose.Words for Java วิธีนี้ช่วยปรับปรุงการใช้งาน PDF อย่างมากและมอบประสบการณ์การนำทางที่เป็นมืออาชีพให้กับผู้ใช้

**ขั้นตอนต่อไป**: ทดลองผสานเทคนิคนี้กับ Aspose.PDF for Java เพื่อแก้ไขบุ๊กมาร์คหลังจากสร้าง PDF แล้ว, หรือรวมเข้ากับบริการประมวลผลแบบแบตช์ที่เพิ่มสารบัญอัตโนมัติให้กับทุกรายงานที่คุณสร้าง

## คำถามที่พบบ่อย

**Q: ฉันจะติดตั้ง Aspose.Words for Java อย่างไร?**  
A: เพิ่มการพึ่งพา Maven หรือ Gradle ตามที่แสดงข้างต้น, จากนั้นวางไฟล์ลิขสิทธิ์ในโฟลเดอร์ resources ของโปรเจกต์และทำการเริ่มต้นที่การเริ่มทำงานของแอปพลิเคชัน

**Q: สามารถใช้บุ๊กมาร์คโดยไม่กำหนดระดับโครงร่างได้หรือไม่?**  
A: ใช่, แต่หากไม่มีระดับโครงร่าง ตัวดู PDF จะจัดรายการบุ๊กมาร์คทั้งหมดในระดับเดียวกัน ทำให้การนำทางยากขึ้น

**Q: มีขีดจำกัดการซ้อนกันของบุ๊กมาร์คหรือไม่?**  
A: ทางเทคนิคไม่มีขีดจำกัดที่แน่นอน, แต่ควรจำกัดระดับให้เหมาะสม (3‑5 ระดับ) เพื่อความอ่านง่าย

**Q: Aspose จัดการกับเอกสารขนาดใหญ่อย่างไร?**  
A: มันทำการสตรีมข้อมูลและมีเมธอดเช่น `Document.optimizeResources()` เพื่อช่วยลดการใช้หน่วยความจำ

**Q: สามารถแก้ไขบุ๊กมาร์คหลังจากบันทึก PDF แล้วได้หรือไม่?**  
A: แน่นอน — ใช้ Aspose.PDF for Java เพื่อแก้ไข, จัดลำดับใหม่, หรือ ลบ บุ๊กมาร์คหลังการสร้าง

## แหล่งข้อมูล
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

---

**อัปเดตล่าสุด:** 2026-03-15  
**ทดสอบด้วย:** Aspose.Words for Java 25.3  
**ผู้เขียน:** Aspose