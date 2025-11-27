---
date: '2025-11-27'
description: เรียนรู้วิธีสร้างบุ๊กมาร์ก, สร้างไฟล์ PDF พร้อมบุ๊กมาร์ก, และแปลงไฟล์
  Word เป็น PDF ใน Java ด้วย Aspose.Words คู่มือนี้ครอบคลุมบุ๊กมาร์กซ้อนและระดับโครงร่าง.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: th
title: วิธีสร้างบุ๊กมาร์กและกำหนดระดับโครงร่างในไฟล์ PDF ด้วย Aspose.Words Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างบุ๊กมาร์กและกำหนดระดับโครงร่างใน PDF ด้วย Aspose.Words Java

## Introduction
หากคุณเคยประสบปัญหาในการ **สร้างบุ๊กมาร์ก** ที่จัดระเบียบได้ดีเมื่อแปลงเอกสาร Word เป็น PDF คุณมาถูกที่แล้ว ในบทแนะนำนี้เราจะอธิบายขั้นตอนทั้งหมดของการสร้าง PDF พร้อมบุ๊กมาร์ก การซ้อนกันของบุ๊กมาร์ก และการกำหนดระดับโครงร่าง เพื่อให้ PDF สุดท้ายนำทางได้ง่าย เมื่อเสร็จคุณจะสามารถ **แปลง Word เป็น PDF ด้วย Java** แบบมีโครงสร้างบุ๊กมาร์กที่สะอาดและทำงานได้ในโปรแกรมอ่าน PDF ใด ๆ

### What You’ll Learn
- ตั้งค่า Aspose.Words for Java ในสภาพแวดล้อมการพัฒนาของคุณ  
- **วิธีสร้างบุ๊กมาร์ก** ด้วยโปรแกรมและซ้อนกัน  
- กำหนดระดับโครงร่างของบุ๊กมาร์กเพื่อสร้าง PDF ที่บุ๊กมาร์กสอดคล้องกับโครงสร้างเอกสาร  
- บันทึกไฟล์ Word เป็น PDF พร้อมคงลำดับชั้นของบุ๊กมาร์กไว้

## Quick Answers
- **What is the primary class for building documents?** `DocumentBuilder`.  
- **Which option controls bookmark hierarchy?** `BookmarksOutlineLevelCollection` inside `PdfSaveOptions`.  
- **Can I use Maven or Gradle?** Yes – both are shown below.  
- **Do I need a license?** A free trial works for testing; a permanent license is required for production.  
- **Is this approach suitable for large documents?** Yes, but consider memory‑optimisation techniques (e.g., removing unused resources).

### Prerequisites
ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

- **Libraries and Dependencies** – Aspose.Words for Java (25.3 หรือใหม่กว่า)  
- **Environment** – JDK 8 หรือใหม่กว่า และ IDE เช่น IntelliJ IDEA หรือ Eclipse  
- **Basic Knowledge** – ความรู้พื้นฐานการเขียนโปรแกรม Java และความคุ้นเคยกับ Maven หรือ Gradle

## Setting Up Aspose.Words
เพื่อเริ่มต้น ให้เพิ่ม dependencies ที่จำเป็นในโปรเจกต์ของคุณ ตัวอย่างการเพิ่ม Aspose.Words ด้วย Maven หรือ Gradle มีดังนี้:

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

### License Acquisition
Aspose.Words เป็นไลบรารีเชิงพาณิชย์ แต่คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรีได้:

1. **Free Trial** – ดาวน์โหลดจาก [Aspose release page](https://releases.aspose.com/words/java/)  
2. **Temporary License** – ขอรับที่ [temporary‑license page](https://purchase.aspose.com/temporary-license/) หากต้องการคีย์ระยะสั้น  
3. **Full License** – ซื้อผ่าน [Aspose purchasing portal](https://purchase.aspose.com/buy) สำหรับการใช้งานในโปรดักชัน  

หลังจากได้ไฟล์ลิขสิทธิ์แล้ว ให้โหลดไฟล์นั้นเมื่อแอปพลิเคชันเริ่มทำงานเพื่อเปิดใช้งานฟีเจอร์ทั้งหมด

## How to Create Bookmarks in PDFs with Aspose.Words Java
ด้านล่างเราจะแบ่งการทำงานออกเป็นขั้นตอนที่ชัดเจนและเป็นลำดับเลขแต่ละขั้นตอนจะมีคำอธิบายสั้น ๆ ตามด้วยบล็อกโค้ดต้นฉบับ (ไม่เปลี่ยนแปลง)

### Step 1: Initialize a Document and a DocumentBuilder
เราเริ่มด้วยการสร้างอินสแตนซ์ `Document` ใหม่และ `DocumentBuilder` ที่ช่วยให้เราสามารถแทรกเนื้อหาและบุ๊กมาร์กได้

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Step 2: Insert the First (Parent) Bookmark
สร้างบุ๊กมาร์กระดับบนสุดที่จะใช้เป็นพาเรนต์สำหรับบุ๊กมาร์กลูกในขั้นตอนต่อไป

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Step 3: Nest a Child Bookmark Inside the Parent
ต่อไปเราจะเพิ่มบุ๊กมาร์กที่สองซึ่งอยู่ภายในบุ๊กมาร์กแรก เพื่อแสดงการซ้อนกัน

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Step 4: Close the Parent Bookmark
ปิดบุ๊กมาร์กภายนอกหลังจากเนื้อหาที่ซ้อนอยู่เสร็จสิ้น

```java
builder.endBookmark("Bookmark 1");
```

### Step 5: Add an Independent Third Bookmark
คุณสามารถเพิ่มบุ๊กมาร์กเพิ่มเติมที่ไม่ได้ซ้อนกับบุ๊กมาร์กอื่นได้เสมอ

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Configuring Bookmark Outline Levels
หลังจากบุ๊กมาร์กถูกสร้างแล้ว เราจะบอก Aspose.Words ว่าบุ๊กมาร์กเหล่านั้นควรปรากฏในโครงร่างของ PDF อย่างไร (แถบนำทางด้านซ้าย)

### Step 6: Prepare PdfSaveOptions
`PdfSaveOptions` ให้เราควบคุมการตั้งค่าโครงร่างได้

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Step 7: Assign Hierarchy Levels
แต่ละบุ๊กมาร์กจะได้รับระดับจำนวนเต็ม; ตัวเลขที่น้อยกว่าจะอยู่สูงกว่าในลำดับชั้น

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Step 8: Save the Document as a PDF
สุดท้ายให้ส่งออกเอกสาร Word เป็น PDF พร้อมคงลำดับชั้นของบุ๊กมาร์กไว้

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Why Use This Approach to Generate PDF with Bookmarks?
- **Professional Navigation** – ผู้อ่านสามารถกระโดดไปยังส่วนต่าง ๆ ได้โดยตรง ทำให้การใช้งานรายงานขนาดใหญ่หรือสัญญากฎหมายสะดวกขึ้น  
- **Full Control** – คุณกำหนดลำดับชั้นเอง ไม่ใช่โปรแกรมอ่าน PDF  
- **Cross‑Platform** – ทำงานได้เช่นเดียวกันบน Windows, Linux, และ macOS เนื่องจากเป็น Java แท้ ๆ  

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---|---|---|
| Missing bookmarks in PDF | A `startBookmark` without matching `endBookmark` | Verify every `startBookmark` has a corresponding `endBookmark`. |
| Incorrect hierarchy | Outline levels assigned out of order | Ensure parent bookmarks have lower level numbers than their children. |
| License not applied | License file not loaded before document creation | Load the license at the very start of your application (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Practical Applications
1. **Legal Documents** – นำทางไปยังข้อ, ภาคผนวก, และเอกสารแนบได้อย่างรวดเร็ว  
2. **Financial Reports** – กระโดดระหว่างส่วนต่าง ๆ เช่น งบกำไรขาดทุน, งบดุล, และหมายเหตุ  
3. **E‑Learning Materials** – ให้สารบัญที่สะท้อนโครงร่างของ PDF อย่างแม่นยำ  

## Performance Considerations
- **Memory Management** – สำหรับไฟล์ Word ขนาดใหญ่มาก ควรเรียก `doc.cleanup()` ก่อนบันทึก  
- **Resource Optimization** – ลบรูปภาพหรือสไตล์ที่ไม่ได้ใช้เพื่อลดขนาด PDF  

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: Add the Maven or Gradle dependency shown earlier, then place your license file in the classpath and load it at runtime.

**Q: Can I create bookmarks without setting outline levels?**  
A: Yes, but the PDF viewer will display them as a flat list, which can be hard to navigate in complex documents.

**Q: Is there a limit to how deep bookmarks can be nested?**  
A: Technically no, but most PDF viewers support up to 9 levels comfortably. Keep the hierarchy logical for readers.

**Q: How does Aspose handle very large Word files?**  
A: The library streams content and provides methods like `Document.optimizeResources()` to reduce memory footprint.

**Q: Can I edit the bookmarks after the PDF is generated?**  
A: Absolutely – you can use Aspose.PDF for Java to add, remove, or rename bookmarks in an existing PDF.

## Resources
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

**Last Updated:** 2025-11-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose