---
category: general
date: 2026-07-03
description: ส่งออกรูปทรงลอยแบบในบรรทัดขณะแปลง Word เป็น PDF ในบรรทัดเดียวกัน เรียนรู้วิธีตั้งค่าตัวเลือก
  PDF และบันทึก Word เป็น PDF ด้วยตัวเลือกใน Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: th
og_description: ส่งออกรูปทรงลอย inline เมื่อคุณแปลงเอกสาร Word เป็น PDF บทเรียนนี้จะแสดงวิธีตั้งค่าตัวเลือก
  PDF และบันทึก Word เป็น PDF.
og_title: ส่งออกรูปทรงลอยแบบอินไลน์ – คู่มือการแปลง PDF ด้วย Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: ส่งออกรูปทรงลอยในบรรทัด – คู่มือฉบับสมบูรณ์สำหรับการแปลงเป็น PDF
url: /th/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ส่งออกรูปทรงลอยตัวแบบ Inline – คู่มือฉบับสมบูรณ์สำหรับการแปลงเป็น PDF

เคยต้อง **ส่งออกรูปทรงลอยตัวแบบ inline** เมื่อต้องแปลงเอกสาร Word เป็น PDF หรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจอปัญหาเดียวกันเมื่อไดอะแกรมหรือไอคอนของพวกเขากระพริบไปเป็นเลเยอร์แยก ข่าวดีคือมีตัวเลือก PDF เพียงอย่างเดียวที่ทำให้รูปทรงเหล่านั้นอยู่ภายในแท็ก `<span>` อย่างแนบแน่น รักษาเลย์เอาต์ให้ตรงกับที่คุณเห็นใน Word

ในบทแนะนำนี้เราจะพาคุณผ่าน **วิธีตั้งค่าตัวเลือก PDF** ใน Java, แสดงโค้ดที่ **บันทึก Word เป็น PDF พร้อมตัวเลือก** อย่างแม่นยำ, และอธิบายว่าทำไมคุณอาจต้องการ **แปลง Word เป็น PDF แบบ inline** แทนการส่งออกแบบบล็อก‑ระดับ เรียนรู้จนจบ คุณจะได้สคริปต์พร้อมใช้งานที่สามารถใส่ลงในโครงการ Maven หรือ Gradle ใดก็ได้

## สิ่งที่คุณจะได้เรียนรู้

- ความแตกต่างระหว่างการส่งออกรูปทรงลอยตัวแบบ inline `<span>` กับแบบบล็อก `<div>`  
- วิธีกำหนดค่า `PdfSaveOptions` เพื่อบังคับให้เรนเดอร์แบบ inline  
- โค้ดขั้นตอน‑ต่อ‑ขั้นตอนที่โหลดไฟล์ `.docx`, ประยุกต์ตัวเลือก, แล้วเขียนเป็น PDF  
- ข้อผิดพลาดทั่วไป (ฟอนต์หาย, รูปทรงที่ไม่รองรับ) และวิธีหลีกเลี่ยง  
- เคล็ดลับสำหรับการทดสอบผลลัพธ์และขยายวิธีการไปยังองค์ประกอบเอกสารอื่น ๆ  

**ข้อกำหนดเบื้องต้น** – คุณต้องมี Java 8 หรือใหม่กว่า, ไลบรารี Aspose.Words for Java (หรือ API ใด ๆ ที่มีคลาส `PdfSaveOptions` คล้ายกัน) และไฟล์ Word ตัวอย่างที่มีรูปทรงลอยตัว (บทแนะนำนี้ใช้ไฟล์ `FloatingShapes.docx`) ไม่ต้องใช้เครื่องมือภายนอกอื่นใด

---

## ขั้นตอนที่ 1: โหลดเอกสาร Word ต้นฉบับ

สิ่งแรกที่ทำคือเปิดไฟล์ `.docx` ที่ต้องการแปลง วิธีทำค่อนข้างตรงไปตรงมา แต่ต้องแน่ใจว่าเส้นทางเป็นแบบ absolute หรือแก้ไขได้อย่างถูกต้องจาก classpath ของคุณ

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*ทำไมจึงสำคัญ:*  
หากเอกสารไม่ถูกโหลดอย่างถูกต้อง การแปลงเป็น PDF ถัดไปจะโยน `FileNotFoundException` การใช้ `Document` ทำให้โมเดลอ็อบเจกต์ภายในเต็มไปด้วยข้อมูล รวมถึงรูปทรงลอยตัวที่อยู่บนหน้า

---

## ขั้นตอนที่ 2: สร้าง PDF Save Options และตั้งค่ารูปทรงลอยตัวเป็น Inline

นี่คือจุดที่เกิด “เวทมนตร์” โดยค่าเริ่มต้น Aspose.Words จะส่งออกรูปทรงลอยตัวเป็นองค์ประกอบระดับบล็อก `<div>` ซึ่งอาจทำให้การไหลของข้อความใน PDF‑แบบ HTML พัง การตั้งค่า `setExportFloatingShapesAsInlineTag(true)` บอกเอนจินให้ห่อแต่ละรูปทรงด้วยแท็ก inline `<span>` แทน

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*ทำไมจึงสำคัญ:*  
- **ความแม่นยำของเลย์เอาต์** – แท็ก inline ทำให้รูปทรงจัดตำแหน่งตรงกับข้อความรอบข้าง ลดช่องว่างที่ไม่ต้องการ  
- **การค้นหาได้** – องค์ประกอบ inline มีโอกาสถูกทำดัชนีโดยโปรแกรมอ่าน PDF อย่างถูกต้องมากกว่า  
- **การควบคุมสไตล์** – คุณสามารถกำหนด CSS ให้กับ `<span>` หากต้องการแปลง PDF กลับเป็น HTML อีกครั้ง  

> **เคล็ดลับ:** หากคุณต้องการพฤติกรรมแบบบล็อกเก่า ๆ สำหรับเอกสารเฉพาะ เพียงส่งค่า `false` หรือไม่เรียกเมธอดนี้เลย

---

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น PDF ด้วยตัวเลือกที่กำหนดไว้

ตอนนี้คุณเพียงแค่รวม `Document` ที่โหลดไว้กับ `PdfSaveOptions` แล้วเขียนไฟล์ออกบรรทัดเดียวนี้ทำหน้าที่หนักทั้งหมด

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*ทำไมจึงสำคัญ:*  
เมธอด `save` จะเคารพทุกแฟล็กที่คุณตั้งค่าใน `pdfOptions` หากลืมส่งตัวเลือกเข้าไป ระบบจะกลับไปใช้การส่งออกแบบบล็อกเริ่มต้น ทำให้ **ส่งออกรูปทรงลอยตัวแบบ inline** ไม่สำเร็จ

---

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมขนาดกะทัดรัดที่คุณสามารถคอมไพล์และรันได้ทันที แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงบนเครื่องของคุณ

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** – หลังจากรันโปรแกรมแล้ว เปิดไฟล์ `FloatingShapes.pdf` คุณจะเห็นรูปทรงอยู่ชิดกับข้อความ ไม่มีช่องว่างสีขาวเพิ่ม และการแสดงผล HTML (หากคุณตรวจสอบโครงสร้างภายในของ PDF) จะมีแท็ก `<span>` ครอบรอบแต่ละรูปทรง

![ตัวอย่างการส่งออกรูปทรงลอยตัวแบบ inline](https://example.com/export-inline.png "ภาพหน้าจอแสดงรูปทรงลอยตัวที่เรนเดอร์แบบ inline ใน PDF")

*ข้อความแทนภาพ:* **export floating shapes inline** screenshot of PDF with inline shapes.

---

## คำถามทั่วไป & กรณีขอบ

### 1. “ถ้าเอกสารของฉันมี SmartArt ที่ซับซ้อนล่ะ?”

SmartArt ถือเป็นวัตถุการวาดรูป แฟล็ก inline ทำงานกับรูปเวกเตอร์ส่วนใหญ่ แต่ SmartArt ที่ซับซ้อนมากอาจยังคงถูกเรนเดอร์เป็นภาพ ในกรณีนั้นให้พิจารณาแปลง SmartArt ให้เป็นแบนใน Word ก่อนแปลง, หรือใช้ `pdfOptions.setExportSmartArtAsImage(true)` เพื่อบังคับให้ส่งออกเป็นภาพ

### 2. “ฉันสามารถผสมการส่งออกแบบ inline และ block ในเอกสารเดียวได้ไหม?”

เสียใจที่ API ใช้การตั้งค่านี้ทั่วทั้งเอกสาร หากต้องการพฤติกรรมผสม ให้แยกเอกสารเป็นส่วน ๆ ส่งออกแต่ละส่วนด้วยตัวเลือกต่างกัน แล้วรวม PDF ด้วย `PdfMerger`

### 3. “ตัวเลือกนี้มีผลต่อการฝังฟอนต์หรือไม่?”

ไม่มี. การฝังฟอนต์ควบคุมโดย `pdfOptions.setEmbedFullFonts(true)` (ค่าเริ่มต้น) คุณสามารถเปิดหรือปิดได้โดยไม่กระทบต่อแฟล็กรูปทรง inline

### 4. “ฉันจะตรวจสอบว่ารูปทรงจริง ๆ เป็น `<span>` หรือไม่?”

เปิด PDF ด้วยเครื่องมือเช่น **PDF.js** หรือ **Adobe Acrobat** → **Edit PDF** → **Object Inspector** คุณจะเห็นรูปทรงห่อด้วยแท็ก `<span>` ใน XML หากเห็น `<div>` แสดงว่าตัวเลือกไม่ได้ถูกนำไปใช้

---

## ขยายวิธีการ – ตัวเลือกที่เกี่ยวข้อง

ในขณะที่คุณอยู่ที่นี่ คุณอาจอยากสำรวจ “น็อบ” การแปลง PDF อื่น ๆ อีกบ้าง:

| ตัวเลือก | ทำหน้าที่ | กรณีใช้งานทั่วไป |
|--------|----------|----------------|
| `setCompressImages(true)` | ลดขนาดภาพ | ดาวน์โหลดเร็วขึ้น |
| `setUseHighQualityRendering(true)` | ปรับปรุงการเรนเดอร์เวกเตอร์ | PDF สำหรับการพิมพ์ |
| `setExportDocumentStructure(true)` | เพิ่มแท็กโครงสร้างเพื่อการเข้าถึง | ปฏิบัติตาม WCAG |
| `setSaveFormat(SaveFormat.PDF)` | กำหนดรูปแบบอย่างชัดเจน (หายาก) | สายงานหลายรูปแบบ |

ตัวเลือกเหล่านี้ทำงานร่วมกับสถานการณ์ **convert word to pdf inline** ที่ต้องการทั้งความแม่นยำของเลย์เอาต์และประสิทธิภาพ

---

## การทดสอบการแปลงของคุณ

1. **ตรวจสอบด้วยตา** – เปิด PDF ในสองโปรแกรม (Chrome และ Adobe Reader) เพื่อให้แน่ใจว่ารูปทรงจัดตำแหน่งตรงกัน  
2. **เปรียบเทียบอัตโนมัติ** – ใช้ไลบรารีอย่าง `pdfbox` ดึง XML แล้วตรวจสอบว่ามีแท็ก `<span>` อยู่หรือไม่  
3. **วัดประสิทธิภาพ** – วัดเวลาแปลงโดยมีและไม่มี `setCompressImages` เพื่อดู trade‑off  

ตัวอย่าง JUnit อย่างรวดเร็ว:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## สรุป

ตอนนี้คุณมีวิธีแก้ปัญหาแบบครบวงจรสำหรับ **ส่งออกรูปทรงลอยตัวแบบ inline** เมื่อ **แปลง Word เป็น PDF แบบ inline** ด้วยการกำหนดค่า `PdfSaveOptions` คุณสามารถควบคุมแท็ก HTML ที่ใช้สำหรับแต่ละรูปทรง ทำให้ PDF ของคุณเป็นระเบียบและค้นหาได้ง่าย อย่าลืมทดสอบผลลัพธ์ ปรับตัวเลือกที่เกี่ยวข้อง เช่น การบีบอัดภาพ และจัดการกรณีขอบเช่น SmartArt ที่ซับซ้อน

พร้อมก้าวต่อไปหรือยัง? ลองใช้เทคนิคเดียวกันเพื่อ **ส่งออกตารางลอยตัวแบบ inline** หรือทดลอง PDF ที่สไตล์ด้วย CSS ผ่าน `HtmlSaveOptions` ของ Aspose วิธีการเดียวกัน—โหลด, ตั้งค่า, บันทึก—ใช้ได้กับเกือบทุกสถานการณ์การแปลงเอกสารเป็น PDF

มีคำถามเพิ่มเติมเกี่ยวกับ **วิธีตั้งค่า pdf options** หรืออยากขอความช่วยเหลือเกี่ยวกับ **save word as pdf options** สำหรับไลบรารีอื่น ๆ? แสดงความคิดเห็นได้เลย, แล้วขอให้เขียนโค้ดสนุก!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอน‑ต่อ‑ขั้นตอน เพื่อให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโครงการของคุณ

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}