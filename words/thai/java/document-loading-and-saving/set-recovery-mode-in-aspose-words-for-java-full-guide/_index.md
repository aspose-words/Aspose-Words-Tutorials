---
category: general
date: 2026-07-03
description: ตั้งค่าโหมดการกู้คืนเพื่อกู้ไฟล์ Word ที่เสียหายใน Java และแสดงจำนวนหน้าหลังจากโหลด
  เรียนรู้ขั้นตอนโดยละเอียดกับ Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: th
og_description: ตั้งค่าโหมดการกู้คืนใน Aspose.Words for Java เพื่อกู้ไฟล์ Word ที่เสียหายและแสดงจำนวนหน้า
  ทำตามตัวอย่างเต็มได้เลยตอนนี้
og_title: ตั้งค่าโหมดการกู้คืนใน Aspose.Words สำหรับ Java – บทเรียนเต็ม
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: ตั้งค่าโหมดการกู้คืนใน Aspose.Words สำหรับ Java – คู่มือเต็ม
url: /th/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่า Recovery Mode ใน Aspose.Words for Java – คู่มือเต็ม

เคยสงสัยไหมว่า **จะตั้งค่า recovery mode** อย่างไรเมื่อโหลดไฟล์ `.docx` ที่เสียหายด้วย Aspose.Words? คุณไม่ได้เป็นคนเดียวที่หัวเราะกับเอกสาร Word ที่เสียและไม่เปิดได้ ในบทเรียนนี้เราจะพาคุณผ่านขั้นตอนทั้งหมด—วิธีกำหนดค่าห้องสมุดเพื่อ **กู้ไฟล์ Word ที่เสีย** แล้ว **แสดงจำนวนหน้า** ของเนื้อหาที่โหลดสำเร็จ

เราจะครอบคลุมทุกอย่างตั้งแต่การปรับ `LoadOptions` เล็กน้อยจนถึง `System.out.println` สุดท้ายที่บอกจำนวนหน้าที่รอดชีวิตจากภารกิจกู้ข้อมูล ไม่มีเรื่องฟุ่มเฟือย มีเพียงโซลูชันพร้อมคัดลอก‑วางที่ทำงานกับ Aspose.Words 23.12 รุ่นล่าสุด

## สิ่งที่คุณจะได้เรียน

- ทำไม recovery mode ถึงสำคัญและตัวเลือกใดบ้างที่ Aspose.Words มีให้  
- วิธี **ตั้งค่า recovery mode** ผ่านโปรแกรมด้วย Java  
- วิธี **แสดงจำนวนหน้า** หลังจากโหลดเอกสาร เพื่อยืนยันว่าการกู้สำเร็จ  
- ข้อผิดพลาดทั่วไปเมื่อจัดการกับไฟล์ Word ที่เสียและวิธีหลีกเลี่ยง  

ก่อนที่เราจะลงลึก ตรวจสอบให้แน่ใจว่าคุณมี:

1. ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (หรือคีย์ประเมินผลชั่วคราว)  
2. Java 17 หรือใหม่กว่า ติดตั้งบนเครื่องของคุณ  
3. ไฟล์ `Corrupted.docx` ที่เสียและต้องการทดสอบ  

มีครบหรือยัง? ดีมาก—มาเริ่มทำกันเลย

> **เคล็ดลับ:** แม้คุณจะใช้รุ่นทดลอง ฟีเจอร์ recovery ทำงานเหมือนกับในรุ่นที่มีใบอนุญาตเต็ม

---

## ## วิธีตั้งค่า Recovery Mode ด้วย Aspose.Words for Java

หัวใจของวิธีแก้ปัญหาอยู่ในคลาส `LoadOptions` โดยค่าเริ่มต้น Aspose.Words จะพยายามโหลดเอกสารให้ดีที่สุด แต่เมื่อไฟล์เสียอย่างรุนแรง คุณต้องบอกมันว่า *จะทำอย่างไร* นั่นคือจุดที่ **set recovery mode** เข้ามาช่วย

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### ทำไมต้องใช้ `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words จะพาร์สส่วนที่เข้าใจได้แล้วต่อต่อกันเป็นเอกสารที่ทำงานได้บางส่วน เหมาะเมื่อคุณต้องการดึง **เนื้อหาใด ๆ** จากไฟล์ที่เสีย  
- **SKIP** – ห้องสมุดจะข้ามส่วนที่เสียทั้งหมด ซึ่งอาจเร็วกว่าแต่จะทิ้งข้อมูลมากกว่า  

ในสถานการณ์ส่วนใหญ่ **PARSE** เป็นตัวเลือกที่ปลอดภัยกว่า เพราะช่วยให้กู้ข้อความ, รูปภาพ, และการจัดรูปแบบได้มากที่สุด

---

## ## แสดงจำนวนหน้า หลังการกู้คืน

เมื่อเอกสารถูกโหลด ขั้นตอนต่อไปที่สมเหตุสมผลคือการตรวจสอบความสำเร็จของการดำเนินการ ตัวชี้วัดที่ง่ายที่สุดและให้ข้อมูลมากที่สุดคือจำนวนหน้า เมธอด `Document.getPageCount()` ทำหน้าที่นี้โดยตรง

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

หากไฟล์อ่านไม่ได้เลย Aspose.Words จะโยนข้อยกเว้น *ก่อน* ถึงบรรทัดนี้ หากคุณเห็นจำนวนหน้าเป็น `0` หรือจำนวนที่ต่ำมาก มักหมายความว่า recovery mode ต้องละทิ้งส่วนใหญ่ของไฟล์ต้นฉบับ

**ผลลัพธ์ที่คาดหวัง (ตัวอย่าง):**

```
Document loaded, page count = 12
```

ซึ่งบ่งบอกว่าห้องสมุดสามารถสร้างหน้าได้สิบสองหน้าจากแหล่งข้อมูลที่เสีย—ค่อนข้างดีสำหรับ `.docx` ที่พัง

---

## ## กรณีขอบและข้อผิดพลาดทั่วไป

### 1️⃣ ส่วนหัว/ส่วนท้ายที่เสีย
บางครั้งเพียงเนื้อหาหลักเท่านั้นที่พาร์สได้ ส่วนหัวและส่วนท้ายอาจหายไป หากคุณพึ่งพาเหล่านี้สำหรับแบรนด์ดิ้ง คุณอาจต้อง **ใส่กลับ** หลังการกู้

### 2️⃣ รูปภาพที่ไม่โหลด
รูปภาพที่ฝังอยู่มักถูกตัดออกเมื่อคอนเทนเนอร์ zip (รูปแบบ `.docx` พื้นฐาน) เสีย คุณสามารถตรวจสอบได้โดยวนลูป `doc.getSections()` และเช็ค `Section.getBody().getParagraphs()` สำหรับอ็อบเจ็กต์ `Shape`

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

หากลูปไม่พิมพ์อะไรเลย หมายความว่า recovery mode น่าจะข้ามรูปภาพไป

### 3️⃣ เอกสารขนาดใหญ่และหน่วยความจำ
การกู้ไฟล์เสียขนาด 200 หน้าอาจใช้หน่วยความจำมาก พิจารณาเพิ่มขนาด heap ของ JVM (`-Xmx2g`) เมื่อคาดว่าจะต้องจัดการเอกสารขนาดใหญ่

### 4️⃣ ข้อจำกัดของใบอนุญาต
เวอร์ชันประเมินผลอาจจำกัดฟีเจอร์บางอย่าง แต่ **recovery** ทำงานเต็มที่ อย่างไรก็ตาม จำนวนหน้าที่พิมพ์อาจถูกจำกัดไว้เพียงไม่กี่หน้าในรุ่นทดลอง ควรทดสอบด้วยรุ่นที่มีใบอนุญาตสำหรับการผลิต

---

## ## ตัวอย่างเต็มขั้นตอน (รันได้)

ด้านล่างเป็นโปรแกรมที่สมบูรณ์ สามารถวางลงในโปรเจกต์ Maven หรือ Gradle ใดก็ได้ รวมการประกาศ dependency ที่จำเป็นสำหรับ Aspose.Words 23.12

### ส่วนของ Maven `pom.xml`

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### ไฟล์ซอร์ส Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**สิ่งที่ทำ:**

1. **ตั้งค่า recovery mode** – เป็นแกนหลักของบทเรียนนี้  
2. โหลดไฟล์เสียโดยใช้ `LoadOptions` ที่กำหนดไว้  
3. **แสดงจำนวนหน้า** เพื่อให้คุณได้รับฟีดแบ็กทันที  
4. บันทึกไฟล์ที่ทำความสะอาดแล้ว (`Recovered.docx`) เพื่อเปิดใน Word ต่อไป

เรียกโปรแกรมด้วย:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

คุณควรเห็นจำนวนหน้าที่พิมพ์ออกมาที่คอนโซล ยืนยันว่าการกู้สำเร็จ

---

## ## ภาพรวมเชิงภาพ (รูป)

![set recovery mode flow diagram](https://example.com/images/recovery-mode-flow.png "แผนภาพแสดงวิธีการตั้งค่า set recovery mode ใน Aspose.Words for Java")

*ข้อความแทนรูปรวมคีย์เวิร์ดหลัก **set recovery mode** เพื่อรองรับ SEO*

---

## ## คำถามที่พบบ่อย

**ถาม: ถ้า `RecoveryMode.PARSE` ยังโยนข้อยกเว้นล่ะ?**  
ตอบ: ปกติหมายถึงไฟล์อยู่ในสภาพที่กู้ไม่ได้—อาจเป็นเพราะคอนเทนเนอร์ zip พังเสียหายอย่างสมบูรณ์ ในกรณีนี้คุณอาจต้องใช้เครื่องมือซ่อมของบุคคลที่สามก่อนนำไปให้ Aspose.Words ประมวลผล

**ถาม: สามารถผสาน `RecoveryMode.PARSE` กับ callback การโหลดเอกสารแบบกำหนดเองได้ไหม?**  
ตอบ: ทำได้แน่นอน ใช้ `IWarningCallback` เพื่อดักจับคำเตือนที่ Aspose.Words ส่งออกระหว่างการพาร์ส ซึ่งช่วยให้คุณรู้ว่าตรงไหนถูกข้าม

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**ถาม: การเปลี่ยน recovery mode จะส่งผลต่อไฟล์ต้นฉบับหรือไม่?**  
ตอบ: ไม่เลย Aspose.Words ทำงานบนสำเนาในหน่วยความจำ ไฟล์ต้นฉบับจะไม่ถูกแก้ไขจนกว่าคุณจะเรียก `doc.save()` อย่างชัดเจน

---

## ## สรุป

เราได้ครอบคลุมวิธี **ตั้งค่า recovery mode** ใน Aspose.Words for Java ทำไม `PARSE` มักเป็นตัวเลือกที่ดีที่สุดสำหรับการกู้ไฟล์ที่เสีย และวิธี **แสดงจำนวนหน้า** เพื่อยืนยันผลลัพธ์ ด้วยตัวอย่างครบถ้วน คุณจึงมีโซลูชันพร้อมรันที่สามารถ **กู้ไฟล์ Word ที่เสีย** และให้ฟีดแบ็กทันทีเกี่ยวกับความสำเร็จของการดำเนินการ

ขั้นตอนต่อไป? ลองสลับเป็น `RecoveryMode.SKIP` เพื่อดูความแตกต่าง ทดลองกับไฟล์หลายส่วนขนาดใหญ่ หรือผสานตรรกะนี้เข้าไปในเว็บเซอร์วิสที่ซ่อมไฟล์ที่ผู้ใช้อัปโหลดแบบอัตโนมัติ แพทเทิร์นเดียวกันนี้ยังใช้ได้กับ PDF (ด้วย Aspose.PDF) และการกู้ข้อความธรรมดาด้วยไลบรารีอื่น—จำไว้ว่าแนวคิดหลักคือ: กำหนดค่าตัวโหลด, พยายามกู้, แล้วตรวจสอบด้วยเมตริกง่าย ๆ อย่างจำนวนหน้า

ขอให้เขียนโค้ดสนุกและเอกสารของคุณคงอยู่สมบูรณ์!

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Combine Multiple Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}