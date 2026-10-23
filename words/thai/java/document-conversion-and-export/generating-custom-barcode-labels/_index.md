---
date: 2026-10-23
description: เรียนรู้วิธีสร้าง QR code Java labels ด้วย Aspose.Words. คู่มือ step‑by‑step
  นี้แสดงวิธี embed barcodes ในเอกสาร Word และ customize size, colors, และ format.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: สร้าง Custom Barcode Labels
og_description: เรียนรู้วิธีสร้าง QR code Java labels ด้วย Aspose.Words. คู่มือนี้อธิบายการ
  embed barcode, การควบคุม size, และการปรับสีในเอกสาร Word.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: วิธีสร้าง QR code Java labels ด้วย Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: วิธีสร้าง QR code Java labels ด้วย Aspose.Words
url: /th/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง QR code Java labels ด้วย Aspose.Words

บาร์โค้ดเป็นสิ่งสำคัญในแอปพลิเคชันสมัยใหม่—ไม่ว่าจะเป็นการจัดการสินค้าคงคลัง, การพิมพ์ตั๋ว, หรือการสร้างบัตรประจำตัว. ในบทเรียนนี้คุณจะ **create QR code Java** labels และฝังลงในเอกสาร Word โดยใช้ interface `IBarcodeGenerator`. เราจะอธิบายทุกขั้นตอน ตั้งแต่การตั้งค่าสภาพแวดล้อมจนถึงการแทรกรูปบาร์โค้ด, เพื่อให้คุณสามารถเริ่มใช้บาร์โค้ดในโครงการ Java ของคุณได้ทันที.

## คำตอบอย่างรวดเร็ว
- **บทเรียนนี้สอนอะไร?** วิธีสร้าง QR code Java labels และฝังลงในไฟล์ Word ด้วย Aspose.Words for Java.  
- **ประเภทบาร์โค้ดที่ใช้ในตัวอย่างคืออะไร?** QR code (คุณสามารถเปลี่ยนเป็นประเภทใดก็ได้จาก 20+ ประเภทที่รองรับ).  
- **ฉันต้องการไลเซนส์หรือไม่?** จำเป็นต้องมีไลเซนส์ชั่วคราวเพื่อการเข้าถึงไม่จำกัดระหว่างการพัฒนา.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า.  
- **ฉันสามารถเปลี่ยนขนาดหรือสีของบาร์โค้ดได้หรือไม่?** ได้—ปรับการตั้งค่า `BarcodeParameters` และ `BarcodeGenerator`.

## create QR code Java คืออะไร?
`create QR code Java` หมายถึงการสร้างภาพ QR‑code อย่างโปรแกรมในสภาพแวดล้อม Java และแทรกลงในเอกสารหรือคอมโพเนนต์ UI. Aspose.Words for Java ร่วมกับ Aspose.BarCode ช่วยให้คุณสร้างภาพได้ทั้งหมดในหน่วยความจำ, ไม่ต้องใช้ไฟล์ชั่วคราว.

## ทำไมต้องสร้างบาร์โค้ดแบบกำหนดเองด้วย Aspose.Words?
Aspose.Words รองรับ **35+ รูปแบบการนำเข้าและส่งออก** และสามารถประมวลผล **เอกสาร 500‑หน้าในเวลาน้อยกว่า 3 วินาที** บนฮาร์ดแวร์เซิร์ฟเวอร์มาตรฐาน. การใช้การสร้างบาร์โค้ดในหน่วยความจำของมันทำให้คุณควบคุมประเภท, ขนาด, และสีได้อย่างเต็มที่ พร้อมรักษากระบวนการทำงานให้เป็นแบบ Java‑centric และไม่ขึ้นกับแพลตฟอร์ม.

## ข้อกำหนดเบื้องต้น

- Java Development Kit (JDK): เวอร์ชัน 8 หรือสูงกว่า.  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse หรือ IDE ใดก็ได้ที่คุณต้องการ.  
- Temporary License: รับ [temporary license](https://purchase.aspose.com/temporary-license/) เพื่อการเข้าถึงไม่จำกัด.

## นำเข้าแพ็กเกจ

เราจะใช้ไลบรารี Aspose.Words และ Aspose.BarCode. นำเข้าแพ็กเกจต่อไปนี้ในโปรเจคของคุณ:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

การนำเข้าเหล่านี้ทำให้เรามีการเข้าถึง API การสร้างบาร์โค้ดและคลาสเอกสาร Word ที่เราต้องการ.

## ขั้นตอนที่ 1: สร้างคลาสยูทิลิตี้สำหรับการทำงานกับบาร์โค้ด

คลาสยูทิลิตี้นี้บรรจุตัวช่วยที่ใช้ซ้ำได้ เช่น **convert twips to pixels** และ **hex‑color conversion**. คลาส `CustomBarcodeGeneratorUtils` ให้เมธอดแบบ static สำหรับการแปลงหน่วยและการจัดการสี.

### โค้ด

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**คำอธิบาย**  
- `twipsToPixels` – Word วัดมิติเป็น **twips**; เมธอดนี้แปลงเป็นพิกเซลของหน้าจอ, มีประโยชน์เมื่อคุณต้องการกำหนดขนาดภาพบาร์โค้ดอย่างแม่นยำ.  
- `convertColor` – แปลงสตริงฐานสิบหก (เช่น `"FF0000"` สำหรับสีแดง) เป็นอ็อบเจกต์ `java.awt.Color`, ทำให้คุณสามารถ **add barcode to Word document** ด้วยสีพื้นหน้าและพื้นหลังที่กำหนดเอง.

## ขั้นตอนที่ 2: ทำการ implement ตัวสร้างบาร์โค้ดแบบกำหนดเอง

ตอนนี้เราจะทำการ implement interface `IBarcodeGenerator`. คลาสนี้รับผิดชอบในการ **generate QR code Java**‑style images ที่ Aspose.Words สามารถฝังได้. Interface `IBarcodeGenerator` กำหนดเมธอดเดียวที่คืนค่า `BufferedImage` แสดงบาร์โค้ด.

### โค้ด

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**คำอธิบาย**  
- `getBarcodeImage` สร้างอินสแตนซ์ของ `BarcodeGenerator`, ใช้สีที่ส่งมาจาก `BarcodeParameters`, และสุดท้ายคืนค่า `BufferedImage`.  
- เมธอดนี้ยังจัดการข้อผิดพลาดอย่างราบรื่นโดยคืนภาพ placeholder, ทำให้การสร้างเอกสาร Word ไม่เกิดการหยุดทำงาน.

## วิธีฝังบาร์โค้ดใน Word ด้วย Aspose.Words?

โหลดไฟล์ Word ของคุณด้วย `new Document("template.docx")` (หรือสร้าง `Document` ใหม่) และเรียก `builder.insertImage` พร้อมภาพบาร์โค้ดที่ได้จาก generator. รูปแบบสองขั้นตอนนี้ฝังบาร์โค้ดโดยตรงโดยไม่ต้องเขียนไฟล์ชั่วคราวลงดิสก์. โดยระบุขนาดภาพเป็นพิกเซลหรือแปลง Word twips เป็นพิกเซล, คุณสามารถควบคุมขนาดและตำแหน่งของบาร์โค้ดในเอกสารได้อย่างแม่นยำ, เพื่อให้ได้เลย์เอาต์ระดับมืออาชีพที่พิมพ์ได้อย่างถูกต้องบนเครื่องพิมพ์ใดก็ได้.

## ขั้นตอนที่ 3: สร้างบาร์โค้ดและฝังบาร์โค้ดใน Word

เมื่อ generator พร้อม, เราสามารถสร้างภาพบาร์โค้ดและ **insert it into a Word document** ได้แล้ว.

### โค้ด

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**คำอธิบาย**  

1. **Document initialization** – สร้าง `Document` ใหม่ (หรือคุณสามารถโหลดเทมเพลตที่มีอยู่).  
2. **Barcode parameters** – กำหนดประเภทบาร์โค้ด (`QR`), ค่าที่จะเข้ารหัส, และสีพื้นหน้า/พื้นหลัง.  
3. **Image insertion** – `builder.insertImage` วางบาร์โค้ดที่สร้างไว้ในขนาดที่ต้องการ (200 × 200 พิกเซล). นี้เป็นหัวใจของ **how to embed barcode in Word**.  
4. **Saving** – เอกสารสุดท้าย, `CustomBarcodeLabels.docx`, มีบาร์โค้ดฝังอยู่พร้อมสำหรับการพิมพ์หรือแจกจ่าย.

## ปัญหาทั่วไป & การแก้ไขข้อผิดพลาด

| ปรากฏบาร์โค้ดเป็นสีขาว | สี `BarcodeParameters` เหมือนกัน (เช่น ดำบนดำ) | ตรวจสอบค่าของ `foregroundColor` และ `backgroundColor`. |
| ภาพบิดเบี้ยว | กำหนดขนาดพิกเซลผิดให้กับ `insertImage` | ปรับค่า width/height หรือใช้การแปลง `twipsToPixels` เพื่อขนาดที่แม่นยำ. |
| เกิดข้อผิดพลาดประเภทบาร์โค้ดที่ไม่รองรับ | ใช้ประเภทที่ `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` ไม่รู้จัก | ตรวจสอบให้แน่ใจว่าสตริงประเภทบาร์โค้ดตรงกับหนึ่งใน `EncodeTypes` ที่รองรับ (เช่น `"QR"`, `"CODE128"`). |

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้ Aspose.Words for Java ได้โดยไม่ต้องมีไลเซนส์หรือไม่?**  
A: ใช่, แต่จะมีข้อจำกัดของรุ่นทดลอง. รับ [temporary license](https://purchase.aspose.com/temporary-license/) เพื่อฟังก์ชันเต็ม.

**Q: ฉันสามารถสร้างบาร์โค้ดประเภทใดได้บ้าง?**  
A: Aspose.BarCode รองรับ QR, Code 128, EAN‑13, DataMatrix, PDF417, และรูปแบบอื่น ๆ มากกว่า 20 สัญลักษณ์. ดู [documentation](https://reference.aspose.com/words/java/) สำหรับรายการทั้งหมด.

**Q: ฉันจะเปลี่ยนขนาดบาร์โค้ดได้อย่างไร?**  
A: ปรับค่า width และ height ใน `builder.insertImage`, หรือคำนวณ Word twips อย่างแม่นยำด้วย `twipsToPixels` เพื่อควบคุมพิกเซลอย่างเต็มที่.

**Q: สามารถใช้ฟอนต์กำหนดเองสำหรับข้อความบาร์โค้ดได้หรือไม่?**  
A: ใช่, คุณสามารถกำหนดฟอนต์ของข้อความผ่าน property `CodeTextParameters` ของ `BarcodeGenerator`.

**Q: ฉันจะหาความช่วยเหลือได้จากที่ไหนหากเจอปัญหา?**  
A: เยี่ยมชม [support forum](https://forum.aspose.com/c/words/8/) เพื่อรับความช่วยเหลือจากชุมชนและวิศวกรของ Aspose.

## สรุป

โดยทำตามขั้นตอนข้างต้น, คุณจะรู้วิธี **create QR code Java** images และ **embed barcode in Word** เอกสารด้วย Aspose.Words for Java. เทคนิคนี้ยืดหยุ่นพอสำหรับแท็กสินค้าคงคลัง, ตั๋วงานอีเวนท์, หรือสถานการณ์ใด ๆ ที่ต้องการบาร์โค้ดเป็นส่วนหนึ่งของเอกสารที่สร้างขึ้น. ทดลองใช้ประเภทบาร์โค้ด, สี, และตัวเลือกขนาดต่าง ๆ เพื่อให้ตรงกับความต้องการของธุรกิจของคุณ.

---

**อัปเดตล่าสุด:** 2026-10-23  
**ทดสอบกับ:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**ผู้เขียน:** Aspose

## บทเรียนที่เกี่ยวข้อง

- [สร้าง PDF จาก Word พร้อมการสร้างบาร์โค้ด – Aspose.Words for Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [บันทึก Word เป็น Pdf ด้วย Aspose Words ขั้นตอนโดยขั้นตอน คู่มือ Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [สร้างเอกสาร Word ว่างใน Java ด้วย Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}