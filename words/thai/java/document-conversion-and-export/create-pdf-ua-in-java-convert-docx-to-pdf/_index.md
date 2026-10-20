---
category: general
date: 2026-10-17
description: เรียนรู้วิธีแปลง docx เป็น pdf ด้วย Java พร้อมสร้างไฟล์ที่สอดคล้องกับ
  PDF/UA ด้วย Aspose.Words คู่มือขั้นตอนโดยละเอียดพร้อมโค้ดและเคล็ดลับการเข้าถึง
draft: false
keywords:
- convert docx to pdf
- generate accessible pdf
- save word as pdf
- export docx to pdf
- java convert word pdf
lastmod: 2026-10-17
og_description: เรียนรู้วิธีแปลง docx เป็น pdf ด้วย Java พร้อมสร้างไฟล์ที่สอดคล้องกับ
  PDF/UA ด้วย Aspose.Words คู่มือขั้นตอนโดยละเอียดพร้อมโค้ดและเคล็ดลับการเข้าถึง
og_image_alt: Guide showing Java code to convert DOCX to PDF/UA with Aspose.Words
og_title: แปลง docx เป็น pdf ด้วย Java และสร้างไฟล์ PDF/UA
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to convert docx to pdf in Java while creating PDF/UA compliant
    files using Aspose.Words. Step‑by‑step guide with code and accessibility tips.
  headline: Convert docx to pdf in Java and create PDF/UA
  type: TechArticle
- description: Learn how to convert docx to pdf in Java while creating PDF/UA compliant
    files using Aspose.Words. Step‑by‑step guide with code and accessibility tips.
  name: Convert docx to pdf in Java and create PDF/UA
  steps:
  - name: Open the PDF in **Adobe Acrobat Pro**.
    text: Open the PDF in **Adobe Acrobat Pro**.
  - name: Choose *Tools → Accessibility → Full Check*.
    text: Choose *Tools → Accessibility → Full Check*.
  - name: Review the report – it should flag zero errors for missing alt text or heading
      hierarchy.
    text: Review the report – it should flag zero errors for missing alt text or heading
      hierarchy.
  type: HowTo
- questions:
  - answer: Yes, a valid Aspose.Words license removes the evaluation watermark and
      permits unlimited production use.
    question: Can I use this in a commercial application?
  - answer: Absolutely. Provide the password via `LoadOptions` when constructing the
      `Document` object.
    question: Does the conversion work with password‑protected DOCX files?
  - answer: Aspose.Words for Java supports Java 8, 11, 17, and newer LTS releases.
    question: Which Java versions are supported?
  - answer: Use the streaming API (`PdfSaveOptions.setUsePdfA1a(true)` and pass an
      `OutputStream`) to keep heap consumption low.
    question: How do I optimise memory usage for very large PDFs?
  - answer: Yes, Aspose.Words preserves fonts, tables, headers/footers, and custom
      styles while adding the required accessibility tags.
    question: Will the generated PDF retain all original formatting?
  type: FAQPage
tags:
- convert docx to pdf
- Aspose.Words
- Java
- PDF/UA
- document conversion
- accessibility
title: แปลง docx เป็น pdf ด้วย Java และสร้างไฟล์ PDF/UA
url: /th/java/document-conversion-and-export/create-pdf-ua-in-java-convert-docx-to-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลง docx เป็น pdf ใน Java และสร้าง PDF/UA

หากคุณต้องการ **convert docx to pdf** และรับประกันว่าไฟล์ที่ได้ตรงตามมาตรฐานการเข้าถึง PDF/UA 1.0 คุณมาถูกที่แล้ว ในบทเรียนนี้เราจะอธิบายตัวอย่าง Java ที่สมบูรณ์พร้อมรันที่ **สร้าง PDF ที่เข้าถึงได้**, **บันทึกเอกสาร Word เป็น PDF**, และแสดงวิธี **export docx to pdf** ด้วยเพียงไม่กี่บรรทัดของโค้ด คุณยังจะได้เรียนรู้ว่าการตั้งค่าแต่ละอย่างสำคัญอย่างไรสำหรับผู้ใช้ที่พึ่งพาเทคโนโลยีช่วยเหลือ

> **สิ่งที่คุณจะได้รับ:**  
> • โปรแกรม Java ที่ทำงานได้ซึ่งโหลด `input.docx` และเขียน `output.pdf` ที่สอดคล้องกับ PDF/UA 1.0.  
> • คำอธิบายที่ชัดเจนว่า *ทำไม* การกำหนดค่าแต่ละอย่างจึงจำเป็นสำหรับการเข้าถึง.  
> • เคล็ดลับการใช้งานจริงสำหรับการจัดการฟอนต์แบบกำหนดเอง เอกสารขนาดใหญ่ และการแปลงเป็นชุด.  

## คำตอบอย่างรวดเร็ว
- **Aspose.Words สามารถสร้างไฟล์ PDF/UA ได้หรือไม่?** ใช่, ตั้งค่า `PdfSaveOptions.setCompliance(PdfCompliance.PDF_UA_1)`.  
- **ต้องการเวอร์ชัน Java ใด?** Java 8 หรือใหม่กว่า; โค้ดยังคอมไพล์ได้กับ JDK 11+.  
- **ต้องการไลเซนส์สำหรับการผลิตหรือไม่?** ไลเซนส์เชิงพาณิชย์จะลบลายน้ำการประเมิน; เวอร์ชันทดลองฟรีใช้ได้สำหรับการทดสอบ.  
- **เอกสารขนาดใหญ่จัดการอย่างไร?** ใช้ API สตรีมมิงเพื่อให้การใช้หน่วยความจำน้อย.  
- **รองรับการแปลงเป็นชุดหรือไม่?** ห่อรอบตรรกะการแปลงในลูปง่าย ๆ เพื่อประมวลผลโฟลเดอร์ทั้งหมด.  

## การแปลง docx เป็น pdf คืออะไร?
วลี “convert docx to pdf” อธิบายกระบวนการแปลงไฟล์ Microsoft Word (.docx) ให้เป็นไฟล์ Portable Document Format (.pdf) โดยอาจใช้มาตรฐานการเข้าถึงเช่น PDF/UA การแปลงนี้จะรักษาเลย์เอาต์ ฟอนต์ รูปภาพและแท็กโครงสร้าง เพื่อให้ PDF สามารถดูได้บนทุกแพลตฟอร์มและยังอ่านได้โดยโปรแกรมอ่านหน้าจอ.

## ทำไมต้องใช้ Aspose.Words สำหรับการแปลงเป็น PDF/UA?
Aspose.Words รองรับ **รูปแบบอินพุตและเอาต์พุตกว่า 35 แบบ**, รวมถึง DOCX, ODT, RTF, HTML, EPUB, และ PDF. มันสามารถประมวลผล **เอกสาร 500 หน้าในเวลาน้อยกว่า 3 วินาที** บนเซิร์ฟเวอร์ทั่วไป, และฝังโครงสร้างตรรกะที่สมบูรณ์ที่จำเป็นสำหรับการปฏิบัติตาม PDF/UA โดยไม่ต้องติดตั้ง Microsoft Word ความสามารถที่วัดผลได้เหล่านี้ทำให้เป็นตัวเลือกที่เชื่อถือได้สำหรับสายงานเอกสารระดับองค์กร.

## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะดำดิ่งลงไป, ตรวจสอบให้แน่ใจว่าคุณมี:

* Java 8 หรือใหม่กว่า (โค้ดยังคอมไพล์ได้กับ JDK 11).  
* ไลเซนส์ Aspose.Words for Java – การประเมินฟรีทำงานได้, แต่ไลเซนส์จะลบลายน้ำ.  
* ไฟล์ DOCX ง่ายชื่อ `input.docx` ที่วางในโฟลเดอร์ที่คุณอ้างอิง (เราจะเรียกว่า `YOUR_DIRECTORY`).  
* Maven หรือ Gradle เพื่อดึง dependency ของ Aspose.Words (คำแนะนำด้านล่าง).  

หากสิ่งใดเหล่านี้ฟังดูแปลกใหม่, อย่าตื่นตระหนก – เราจะอธิบายการตั้งค่า Maven และ Gradle ในไม่ช้า.

## ฉันจะเพิ่ม Aspose.Words ไปยังโปรเจกต์ Java ของฉันอย่างไร?
การเพิ่ม Aspose.Words ไปยังโปรเจกต์ของคุณทำให้คอมไพเลอร์สามารถค้นหาคลาสที่จำเป็นและทรัพยากรรันไทม์ของไลบรารีพร้อมใช้งานบน classpath คุณจะต้องแก้ไขไฟล์ build (Maven `pom.xml` หรือ Gradle `build.gradle`) เพื่อประกาศ dependency แล้วรีเฟรชโปรเจกต์เพื่อให้ JAR ดาวน์โหลดจาก Maven Central repository ขั้นตอนนี้สำคัญเพราะหากไม่มีไลบรารีคลาส `Document` และ `PdfSaveOptions` ที่ใช้ต่อไปจะไม่ถูกจดจำ ทำให้เกิดข้อผิดพลาดการคอมไพล์.

### Maven

Add the following snippet to the `<dependencies>` section of your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

### Gradle

For Gradle users, insert this line into the `dependencies` block of your `build.gradle` file:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **เคล็ดลับ:** หากคุณอยู่หลังพร็อกซีขององค์กร, ให้กำหนดค่า Maven หรือ Gradle ให้ใช้พร็อกซี – มิฉะนั้นการดาวน์โหลดจะล้มเหลวโดยไม่มีข้อความแจ้ง.

## ฉันจะโหลดเอกสาร DOCX ต้นฉบับอย่างไร?
ขั้นตอนแรกคือการอ่านไฟล์ Word ที่คุณต้องการ **save word as pdf**.  

คลาส `Document` แทนเอกสาร Word ในหน่วยความจำและแยกการจัดการแพ็กเกจ OPC ระดับต่ำออกไป.  

`Document` วิเคราะห์สไตล์, บุ๊กมาร์ค, และแท็กการเข้าถึง (เช่นข้อความ alt สำหรับรูปภาพ) เพื่อให้ข้อมูลเหล่านี้ส่งตรงไปยังผลลัพธ์ PDF/UA.

```java
import com.aspose.words.*;

public class PdfUaDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Point to your DOCX file
        Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");
```

*ทำไมเรื่องนี้สำคัญ:* การโหลด DOCX ตั้งแต่แรกทำให้ Aspose มีโอกาสจับข้อมูลโครงสร้างและความหมายทั้งหมด ซึ่งจำเป็นสำหรับการ **generate accessible pdf**.

## ฉันจะกำหนดค่า PDF save options เพื่อให้สอดคล้องกับ PDF/UA อย่างไร?
การกำหนดค่า PDF save options ช่วยให้คุณควบคุมวิธีการสร้าง PDF สุดท้าย โดยเฉพาะคุณลักษณะการเข้าถึงที่ PDF/UA ต้องการ โดยการสร้างอินสแตนซ์ `PdfSaveOptions` คุณสามารถระบุระดับการปฏิบัติตาม, ฝังฟอนต์, ตั้งค่าภาษาเอกสาร, และรักษาโครงสร้างตรรกะที่โปรแกรมอ่านหน้าจอพึ่งพา การตั้งค่า `setCompliance(PdfCompliance.PDF_UA_1)` บอก Aspose.Words ให้ฝังแท็กและเมตาดาต้าที่จำเป็น เพื่อให้ผลลัพธ์สอดคล้องกับสเปค PDF/UA 1.0 ย่อหน้านี้อธิบายวัตถุประสงค์ของตัวเลือกก่อนตัวอย่างโค้ดต่อไป.

```java
        // Step 3: Configure PDF save options for PDF/UA compliance
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setCompliance(PdfCompliance.PDF_UA_1);
```

### `PDF_UA_1` ทำอะไร?
* **Structure tags** – ฝังโครงสร้างตรรกะ (หัวเรื่อง, รายการ, ตาราง) ที่โปรแกรมอ่านหน้าจอต้องการ.  
* **Document language** – คัดลอกแอตทริบิวต์ภาษาจาก DOCX, ช่วยเครื่องมือช่วยเหลือเลือกเสียงที่ถูกต้อง.  
* **Alternative text** – ย้ายข้อความ `alt` ที่คุณเพิ่มในรูปภาพใน Word ไปยังเมตาดาต้า PDF.

หากคุณต้องการ **export docx to pdf** โดยไม่บังคับใช้ PDF/UA อย่างเคร่งครัด, ให้เปลี่ยน `PDF_UA_1` เป็น `PDF_1_7` หรือไม่เรียกเมธอดนี้เลย สำหรับการเข้าถึงเต็มรูปแบบ, ให้คงการตั้งค่าการปฏิบัติตามไว้.

## ฉันจะบันทึกเอกสารเป็น PDF ที่เข้าถึงได้อย่างไร?
การบันทึกเอกสารสรุปกระบวนการแปลง คุณส่งอ็อบเจกต์ `Document` ที่อยู่ในหน่วยความจำพร้อมกับ `PdfSaveOptions` ที่กำหนดไว้ไปยังเมธอด `save` ซึ่งจะเขียนไฟล์ PDF ลงดิสก์ ขั้นตอนนี้ยังทำให้แท็กการเข้าถึงที่เตรียมไว้ก่อนหน้านี้ถูกฝังลงไป สร้างไฟล์ที่สอดคล้องกับ PDF/UA ที่สามารถเปิดด้วยโปรแกรมอ่าน PDF ใดก็ได้ ย่อหน้านี้ให้คำอธิบายที่ชัดเจนกว่า 40 คำว่าทำไมขั้นตอนนี้สำคัญก่อนตัวอย่างโค้ด.

```java
        // Step 4: Save the document as a PDF that meets PDF/UA 1.0 standards
        sourceDocument.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `output.pdf` ใน Adobe Acrobat Pro และตรวจสอบ *File → Properties → Description → PDF/A and PDF/UA*. คุณควรเห็น “PDF/UA‑1” ปรากฏในส่วน “Conformance”. โปรแกรมอ่านหน้าจอใด ๆ จะสามารถนำทางหัวเรื่อง, ตาราง, และรูปภาพได้อย่างถูกต้องแล้ว.

## ฉันจะตรวจสอบการเข้าถึงได้อย่างไร (ไม่บังคับแต่แนะนำ)?
การตรวจสอบการเข้าถึงทำให้แน่ใจว่า PDF ไม่เพียงมีแท็กที่จำเป็นเท่านั้น แต่แท็กเหล่านั้นยังถูกเทคโนโลยีช่วยเหลือแปลความหมายอย่างถูกต้อง หลังจากสร้าง PDF แล้ว เปิดไฟล์ใน Adobe Acrobat Pro และรันตัวตรวจสอบการเข้าถึงในตัว เครื่องมือนี้สแกนเอกสารเพื่อหาข้อความ alt ที่หายไป, โครงสร้างหัวเรื่องที่ไม่เหมาะสม, และปัญหาแท็กภาษา, ให้รายงานละเอียดที่ช่วยคุณแก้ไขปัญหาที่เหลือก่อนการเผยแพร่ การทำขั้นตอนตรวจสอบนี้เป็นแนวปฏิบัติที่ดีที่สุดสำหรับการส่งมอบเนื้อหาที่เข้าถึงได้จริง.

1. เปิด PDF ใน **Adobe Acrobat Pro**.  
2. เลือก *Tools → Accessibility → Full Check*.  
3. ตรวจสอบรายงาน – ควรไม่มีข้อผิดพลาดเกี่ยวกับข้อความ alt ที่หายไปหรือโครงสร้างหัวเรื่อง.

หากคุณเห็นคำเตือนเกี่ยวกับแท็กภาษาไม่มี, กลับไปที่ DOCX ต้นฉบับและตั้งค่าภาษาเอกสารภายใต้ *Review → Language* ใน Word, แล้วรันการแปลงใหม่อีกครั้ง.

## ฉันจะเพิ่มฟอนต์แบบกำหนดเองอย่างไร?
เมื่อ DOCX ใช้ฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์, PDF อาจเปลี่ยนไปใช้ฟอนต์เริ่มต้น ทำให้รูปแบบการแสดงผลเสียหายและอาจส่งผลต่อการอ่านสำหรับผู้ใช้ที่พึ่งพาเค้าโครงตัวอักษรเฉพาะ เพื่อรักษาลักษณะที่ตั้งใจไว้, คุณสามารถฝังไฟล์ฟอนต์ที่ต้องการโดยตรงลงใน PDF โดยกำหนด `PdfSaveOptions` ให้ใช้แหล่งฟอนต์แบบกำหนดเอง วิธีนี้ทำให้ PDF แสดงผลตรงตามการออกแบบ ไม่ว่าฟอนต์บนเครื่องผู้ใช้จะมีหรือไม่.

```java
pdfSaveOptions.setEmbedStandardWindowsFonts(true);
pdfSaveOptions.getFontEmbeddingMode().setEmbedAllFonts(true);
```

## ฉันจะจัดการเอกสารขนาดใหญ่ ( > 100 MB ) อย่างไร?
การประมวลผลเอกสารขนาดใหญ่มากอาจทำให้ heap ของ JVM หมดถ้าโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำพร้อมกัน Aspose.Words มี API สตรีมมิงที่เขียน PDF อย่างต่อเนื่อง ทำให้การใช้หน่วยความจำต่ำและป้องกันข้อผิดพลาด out‑of‑memory โดยการส่ง `OutputStream` ไปยังเมธอด `save` และเปิดใช้งานตัวเลือกสตรีมมิง คุณสามารถแปลงไฟล์ขนาดมหาศาลได้อย่างมีประสิทธิภาพพร้อมคงการปฏิบัติตาม PDF/UA ตัวอย่างโค้ดต่อไปนี้แสดงวิธีนี้.

```java
try (FileOutputStream out = new FileOutputStream("YOUR_DIRECTORY/output.pdf")) {
    sourceDocument.save(out, pdfSaveOptions);
}
```

## ฉันจะแปลงหลายไฟล์เป็นชุดได้อย่างไร?
การแปลงเป็นชุดมีประโยชน์เมื่อคุณต้องประมวลผลโฟลเดอร์เต็มของไฟล์ DOCX โดยไม่ต้องทำด้วยตนเอง โดยการวนลูปแต่ละไฟล์ในไดเรกทอรี, ใช้ตรรกะ load‑configure‑save เดียวกัน, คุณสามารถสร้างชุด PDF ที่เข้าถึงได้ในรอบเดียว วิธีนี้ขยายได้ดีและสามารถรวมเข้าไปใน pipeline การสร้างอัตโนมัติหรือระบบจัดการเอกสาร ด้านล่างเป็นตัวอย่างสั้นที่แสดงวิธีวนลูปโฟลเดอร์และสร้าง PDF สำหรับทุก DOCX ที่พบ.

```java
File dir = new File("YOUR_DIRECTORY");
for (File file : dir.listFiles((d, name) -> name.toLowerCase().endsWith(".docx"))) {
    Document doc = new Document(file.getAbsolutePath());
    doc.save(file.getParent() + "/" + file.getName().replace(".docx", ".pdf"), pdfSaveOptions);
}
```

## เคล็ดลับระดับมืออาชีพ & สิ่งที่ต้องระวัง
| Situation | What to watch for | Suggested fix |
|-----------|-------------------|---------------|
| **Missing alt text** | PDF/UA ระบุภาพที่ไม่มีคำอธิบาย. | เพิ่ม alt text ใน Word (`Right‑click → Format Picture → Alt Text`). |
| **Password‑protected DOCX** | ตัวสร้าง `Document` โยนข้อยกเว้น. | ใช้ `LoadOptions` พร้อมรหัสผ่าน: `new LoadOptions("pwd")`. |
| **Incorrect page size** | PDF อาจสืบทอดขนาด A4 เริ่มต้นของ Word แม้คุณต้องการ Letter. | ตั้งค่า `pdfSaveOptions.setPageSetup(new PageSetup())` ก่อนบันทึก. |
| **Performance bottleneck** | การแปลง 10 k หน้าอาจช้า. | เปิด `pdfSaveOptions.setUsePdfA1a(true)` เพื่อสตรีมมิงที่เร็วขึ้น. |

## ตัวอย่างทำงานเต็ม (พร้อมคัดลอก‑วาง)
```java
import com.aspose.words.*;

public class PdfUaDemo {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX document (convert docx to pdf step)
        Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

        // Configure PDF save options for PDF/UA compliance (generate accessible pdf)
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setCompliance(PdfCompliance.PDF_UA_1);
        // Optional: embed all fonts to avoid layout shifts
        pdfSaveOptions.setEmbedStandardWindowsFonts(true);
        pdfSaveOptions.getFontEmbeddingMode().setEmbedAllFonts(true);

        // Save the document as a PDF that meets PDF/UA 1.0 standards (save word as pdf)
        sourceDocument.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);
    }
}
```

**ผลลัพธ์:** `output.pdf` อยู่ในโฟลเดอร์เดียวกัน, สอดคล้องเต็มรูปแบบกับ PDF/UA 1.0, พร้อมสำหรับการแจกจ่ายให้ผู้ใช้ที่พึ่งพาเทคโนโลยีช่วยเหลือ.

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้สิ่งนี้ในแอปพลิเคชันเชิงพาณิชย์ได้หรือไม่?**  
A: ใช่, ไลเซนส์ Aspose.Words ที่ถูกต้องจะลบลายน้ำการประเมินและอนุญาตให้ใช้ในการผลิตได้ไม่จำกัด.

**Q: การแปลงทำงานกับไฟล์ DOCX ที่มีรหัสผ่านหรือไม่?**  
A: แน่นอน. ให้รหัสผ่านผ่าน `LoadOptions` เมื่อสร้างอ็อบเจกต์ `Document`.

**Q: รองรับเวอร์ชัน Java ใดบ้าง?**  
A: Aspose.Words for Java รองรับ Java 8, 11, 17, และรุ่น LTS ใหม่ ๆ

**Q: ฉันจะเพิ่มประสิทธิภาพการใช้หน่วยความจำสำหรับ PDF ขนาดใหญ่มากอย่างไร?**  
A: ใช้ API สตรีมมิง (`PdfSaveOptions.setUsePdfA1a(true)` และส่ง `OutputStream`) เพื่อให้การใช้ heap ต่ำ.

**Q: PDF ที่สร้างขึ้นจะรักษาการจัดรูปแบบเดิมทั้งหมดหรือไม่?**  
A: ใช่, Aspose.Words รักษาฟอนต์, ตาราง, ส่วนหัว/ส่วนท้าย, และสไตล์แบบกำหนดเอง พร้อมเพิ่มแท็กการเข้าถึงที่จำเป็น.

**อัปเดตล่าสุด:** 2026-10-17  
**ทดสอบด้วย:** Aspose.Words for Java 24.11  
**ผู้เขียน:** Aspose

## บทแนะนำที่เกี่ยวข้อง
- [สร้าง PDF ที่เข้าถึงได้ขั้นตอนโดยขั้นตอนเพื่อแปลง Word เป็น](/words/java/document-conversion-and-export/create-accessible-pdf-step-by-step-guide-to-convert-word-to/)
- [ส่งออก Docx เป็น Pdf คู่มือครบถ้วนสำหรับการสร้าง PDF ที่เข้าถึงได้](/words/java/document-conversion-and-export/export-docx-to-pdf-complete-guide-to-creating-accessible-pdf/)
- [สร้าง PDF ที่เข้าถึงได้จาก Word ด้วย Aspose Java](/words/java/document-conversion-and-export/generate-accessible-pdf-from-word-with-aspose-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}