---
date: '2026-04-27'
description: เรียนรู้วิธีตั้งบุ๊กมาร์กและบันทึก PDF พร้อมบุ๊กมาร์กโดยใช้ Aspose.Words
  for Java เพิ่มความอ่านง่ายและการนำทางด้วยคู่มือที่ครอบคลุมนี้
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: วิธีตั้งบุ๊กมาร์คในไฟล์ PDF ด้วย Aspose.Words Java
url: /th/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งบุ๊กมาร์กใน PDF ด้วย Aspose.Words Java

## บทนำ
หากคุณกำลังประสบปัญหาในการจัดการ **วิธีตั้งบุ๊กมาร์ก** เมื่อแปลงเอกสาร Word เป็น PDF คุณมาถูกที่แล้ว ในบทเรียนนี้เราจะอธิบายกระบวนการทั้งหมดโดยใช้ Aspose.Words for Java ตั้งแต่การสร้างบุ๊กมาร์กซ้อนจนถึงการกำหนดระดับโครงร่างของบุ๊กมาร์ก เพื่อให้ PDF สุดท้ายดูเรียบร้อยเป็นมืออาชีพและง่ายต่อการนำทาง

**สิ่งที่คุณจะได้เรียนรู้**
- ตั้งค่า Aspose.Words for Java ในโปรเจคของคุณ  
- **สร้างบุ๊กมาร์กซ้อน** ภายในเอกสาร Word  
- **กำหนดระดับโครงร่างของบุ๊กมาร์ก** เพื่อสร้างโครงร่าง PDF ที่เป็นโครงสร้าง  
- **บันทึก PDF พร้อมบุ๊กมาร์ก** ที่สะท้อนลำดับชั้นที่คุณกำหนด  

### คำตอบสั้น
- **คลาสหลักสำหรับสร้างเอกสารคืออะไร?** `DocumentBuilder`  
- **ตัวเลือกใดที่ควบคุมลำดับชั้นของบุ๊กมาร์ก?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **ฉันสามารถใช้ Maven หรือ Gradle ได้หรือไม่?** ใช่ ทั้งสองได้รับการสนับสนุน (ดูโค้ดตัวอย่าง)  
- **ฉันต้องการไลเซนส์หรือไม่?** รุ่นทดลองใช้ได้สำหรับการประเมิน; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการใช้งานจริง  
- **PDF จะรักษาบุ๊กมาร์กซ้อนได้หรือไม่?** แน่นอน เมื่อกำหนดระดับโครงร่างอย่างถูกต้อง  

## “วิธีตั้งบุ๊กมาร์ก” ใน PDF คืออะไร?
การตั้งบุ๊กมาร์กหมายถึงการกำหนดรายการที่คลิกได้ในแถบการนำทางของ PDF ซึ่งจะกระโดดไปยังส่วนเฉพาะของเอกสาร เมื่อบุ๊กมาร์กถูกซ้อนและกำหนดระดับโครงร่าง พวกมันจะแสดงเป็นต้นไม้ที่สามารถยุบ/ขยายได้ ทำให้การสำรวจเอกสารขนาดใหญ่ง่ายขึ้นมาก

## ทำไมต้องใช้ Aspose.Words สำหรับระดับโครงร่างของบุ๊กมาร์ก?
Aspose.Words ให้คุณควบคุมการแปลง Word‑to‑PDF อย่างเต็มรูปแบบผ่านโปรแกรม รวมถึงความสามารถในการ **สร้าง PDF พร้อมบุ๊กมาร์ก** ที่สะท้อนโครงสร้างของเอกสารของคุณ สิ่งนี้ช่วยขจัดความจำเป็นในการประมวลผลหลังการแปลงด้วยมือและรับประกันประสบการณ์ผู้ใช้ที่สม่ำเสมอในทุก PDF ที่สร้าง

## ข้อกำหนดเบื้องต้น
- **ไลบรารีและการพึ่งพา**: Aspose.Words for Java (เวอร์ชัน 25.3 หรือใหม่กว่า).  
- **สภาพแวดล้อม**: JDK 8 หรือใหม่กว่า, IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- **ความรู้**: พื้นฐาน Java, ความคุ้นเคยกับ Maven หรือ Gradle.  

## การตั้งค่า Aspose.Words
เพิ่มไลบรารีที่จำเป็นลงในระบบการสร้างของคุณ.

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

### การขอรับไลเซนส์
Aspose.Words เป็นผลิตภัณฑ์เชิงพาณิชย์ แต่คุณสามารถเริ่มต้นด้วยการทดลองใช้งานฟรี.

1. **ทดลองใช้ฟรี**: ดาวน์โหลดจาก [Aspose's release page](https://releases.aspose.com/words/java/) เพื่อทดสอบความสามารถทั้งหมด.  
2. **ไลเซนส์ชั่วคราว**: ขอรับไลเซนส์ชั่วคราวที่ [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) หากต้องการ.  
3. **ซื้อไลเซนส์**: สำหรับการใช้งานต่อเนื่อง ให้ซื้อไลเซนส์จาก [Aspose’s purchasing portal](https://purchase.aspose.com/buy).  

เริ่มต้นไฟล์ไลเซนส์ในโค้ดของคุณเพื่อเปิดใช้งานคุณสมบัติทั้งหมด.

## คู่มือการดำเนินการ
ด้านล่างเป็นขั้นตอนแบบละเอียดที่ครอบคลุม **การสร้างบุ๊กมาร์กซ้อน**, การกำหนดระดับโครงร่างของพวกมัน, และสุดท้าย **การบันทึก PDF พร้อมบุ๊กมาร์ก**.

### การสร้างบุ๊กมาร์กซ้อน
**ภาพรวม**: สร้างเอกสาร Word และฝังบุ๊กมาร์กที่สะท้อนลำดับชั้น.

#### ขั้นตอนที่ 1: เริ่มต้น Document และ Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
โค้ดนี้สร้างเอกสารใหม่พร้อมสำหรับการแทรกเนื้อหา

#### ขั้นตอนที่ 2: แทรกบุ๊กมาร์กซ้อน
เริ่มด้วยบุ๊กมาร์กหลัก จากนั้นซ้อนบุ๊กมาร์กที่สองภายในมัน.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

#### ขั้นตอนที่ 3: เพิ่มบุ๊กมาร์กเพิ่มเติม
คุณสามารถเพิ่มบุ๊กมาร์กอิสระอื่น ๆ ตามต้องการต่อไป.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### การกำหนดระดับโครงร่างของบุ๊กมาร์ก
**ภาพรวม**: กำหนดระดับโครงร่างเพื่อให้แถบบุ๊กมาร์กของ PDF แสดงลำดับชั้นตามที่ต้องการ.

#### ขั้นตอนที่ 1: ตั้งค่า PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
ตัวเลือกเหล่านี้จะใช้เมื่อบันทึกเอกสารเป็น PDF.

#### ขั้นตอนที่ 2: เพิ่มระดับโครงร่าง
แมปชื่อบุ๊กมาร์กแต่ละรายการกับระดับโครงร่าง (1 = ระดับบนสุด, 2 = ลูก, ฯลฯ).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### ขั้นตอนที่ 3: บันทึกเอกสาร
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
PDF ที่ได้จะมีโครงสร้างต้นไม้ของบุ๊กมาร์ก

## ปัญหาทั่วไปและวิธีแก้
- **บุ๊กมาร์กหาย** – ตรวจสอบว่า `startBookmark` ทุกตัวมี `endBookmark` ที่ตรงกัน.  
- **ลำดับชั้นไม่ถูกต้อง** – ตรวจสอบหมายเลขระดับโครงร่าง; ลูกต้องมีหมายเลขสูงกว่าพ่อแม่.  
- **เอกสารขนาดใหญ่** – เรียก `doc.removeUnusedResources()` ก่อนบันทึกเพื่อลดขนาดไฟล์.  

## การประยุกต์ใช้งานจริง
1. **สัญญากฎหมาย** – กระโดดไปยังข้อและข้อย่อยได้อย่างรวดเร็ว.  
2. **รายงานประจำปี** – นำทางส่วนต่าง ๆ ตาราง และแผนภูมิได้อย่างง่ายดาย.  
3. **สื่อการเรียนรู้ออนไลน์** – ให้สารบัญที่คลิกได้สำหรับนักเรียน.  

## ข้อพิจารณาด้านประสิทธิภาพ
- ลบโหนดที่ไม่จำเป็นก่อนการแปลงเพื่อให้ PDF มีน้ำหนักเบา.  
- สำหรับไฟล์ขนาดใหญ่มาก ควรพิจารณา stream เอกสารเพื่อหลีกเลี่ยงการใช้หน่วยความจำสูง.  

## สรุป
ตอนนี้คุณรู้แล้ว **วิธีตั้งบุ๊กมาร์ก**, การกำหนดระดับโครงร่างของพวกมัน, และ **การบันทึก PDF พร้อมบุ๊กมาร์ก** ด้วย Aspose.Words for Java เทคนิคนี้ช่วยปรับปรุงการนำทางใน PDF อย่างมากและทำให้เอกสารของคุณดูเป็นมืออาชีพ

**ขั้นตอนต่อไป**: ลองเพิ่มไอคอนแบบกำหนดเองให้กับบุ๊กมาร์กหรือผสานกระบวนการนี้เข้ากับบริการประมวลผลแบบชุด

## คำถามที่พบบ่อย

**Q: ฉันจะติดตั้ง Aspose.Words for Java อย่างไร?**  
A: เพิ่ม dependency ของ Maven หรือ Gradle ตามที่แสดงด้านบน, จากนั้นวางไฟล์ไลเซนส์ของคุณในโฟลเดอร์ resources ของโปรเจค

**Q: ฉันสามารถสร้างบุ๊กมาร์กโดยไม่กำหนดระดับโครงร่างได้หรือไม่?**  
A: ได้, แต่หากไม่มีระดับโครงร่าง แถบการนำทางของ PDF จะรายการบุ๊กมาร์กทั้งหมดในระดับเดียวกัน ทำให้เอกสารขนาดใหญ่ยากต่อการเรียกดู

**Q: มีขีดจำกัดความลึกของการซ้อนบุ๊กมาร์กหรือไม่?**  
A: โดยเทคนิคไม่มี, แต่ควรรักษาลำดับชั้นให้ผู้ใช้อ่านง่าย—โดยทั่วไป 3‑4 ระดับเพียงพอ

**Q: Aspose จัดการกับไฟล์ Word ขนาดใหญ่อย่างไร?**  
A: มัน stream เนื้อหาและมีเมธอดเช่น `Document.optimizeResources()` เพื่อรักษาการใช้หน่วยความจำให้ต่ำ

**Q: ฉันสามารถแก้ไขบุ๊กมาร์กหลังจาก PDF ถูกสร้างแล้วได้หรือไม่?**  
A: ได้, คุณสามารถใช้ Aspose.PDF for Java เพื่อแก้ไขชื่อบุ๊กมาร์ก, จุดหมาย, หรือลำดับชั้นหลังการแปลง

---

**อัปเดตล่าสุด:** 2026-04-27  
**ทดสอบกับ:** Aspose.Words 25.3 for Java  
**ผู้เขียน:** Aspose  

## แหล่งข้อมูล
- [เอกสาร Aspose.Words](https://reference.aspose.com/words/java/)
- [ดาวน์โหลดเวอร์ชันล่าสุด](https://releases.aspose.com/words/java/)
- [ซื้อไลเซนส์](https://purchase.aspose.com/buy)
- [ทดลองใช้ฟรี](https://releases.aspose.com/words/java/)
- [สมัครไลเซนส์ชั่วคราว](https://purchase.aspose.com/temporary-license/)
- [ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}