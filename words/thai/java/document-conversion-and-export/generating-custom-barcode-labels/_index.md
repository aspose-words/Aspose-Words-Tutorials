---
date: 2025-12-10
description: เรียนรู้วิธีสร้างป้ายบาร์โค้ดแบบกำหนดเองโดยใช้ Aspose.Words for Java
  คู่มือขั้นตอนต่อขั้นตอนนี้จะแสดงวิธีฝังบาร์โค้ดในเอกสาร Word
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: สร้างป้ายบาร์โค้ดแบบกำหนดเองใน Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สร้างป้ายบาร์โค้ดแบบกำหนดเองใน Aspose.Words สำหรับ Java

## บทนำการสร้างบาร์โค้ดแบบกำหนดเองใน Aspose.Words สำหรับ Java

บาร์โค้ดเป็นส่วนสำคัญในแอปพลิเคชันสมัยใหม่—ไม่ว่าจะเป็นการจัดการสินค้าคงคลัง การพิมพ์ตั๋ว หรือการสร้างบัตรประจำตัว ในบทเรียนนี้คุณจะ **สร้างป้ายบาร์โค้ดแบบกำหนดเอง** และฝังลงในเอกสาร Word โดยตรงด้วยอินเทอร์เฟซ `IBarcodeGenerator` เราจะเดินผ่านทุกขั้นตอน ตั้งแต่การตั้งค่าสภาพแวดล้อมจนถึงการแทรกรูปบาร์โค้ด เพื่อให้คุณสามารถใช้บาร์โค้ดในโครงการ Java ของคุณได้ทันที

## คำตอบสั้น
- **บทเรียนนี้สอนอะไร?** วิธีสร้างป้ายบาร์โค้ดแบบกำหนดเองและฝังลงในไฟล์ Word ด้วย Aspose.Words สำหรับ Java  
- **บาร์โค้ดประเภทใดที่ใช้ในตัวอย่าง?** QR code (คุณสามารถเปลี่ยนเป็นประเภทที่รองรับอื่นได้)  
- **ต้องการไลเซนส์หรือไม่?** จำเป็นต้องมีไลเซนส์ชั่วคราวเพื่อเข้าถึงแบบไม่จำกัดระหว่างการพัฒนา  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือสูงกว่า  
- **สามารถเปลี่ยนขนาดหรือสีของบาร์โค้ดได้หรือไม่?** ได้—ปรับการตั้งค่า `BarcodeParameters` และ `BarcodeGenerator`

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มเขียนโค้ด ตรวจสอบว่าคุณมีสิ่งต่อไปนี้แล้ว:

- Java Development Kit (JDK): เวอร์ชัน 8 ขึ้นไป  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/)  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/)  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse หรือ IDE ที่คุณชอบ  
- ไลเซนส์ชั่วคราว: รับ [temporary license](https://purchase.aspose.com/temporary-license/) เพื่อการเข้าถึงแบบไม่จำกัด

## นำเข้าแพ็กเกจ

เราจะใช้ไลบรารี Aspose.Words และ Aspose.BarCode นำเข้าแพ็กเกจต่อไปนี้ในโปรเจกต์ของคุณ:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

การนำเข้าเหล่านี้ทำให้เราสามารถเข้าถึง API การสร้างบาร์โค้ดและคลาสเอกสาร Word ที่จำเป็นได้

## ขั้นตอนที่ 1: สร้างคลาสยูทิลิตี้สำหรับการทำงานกับบาร์โค้ด

เพื่อให้โค้ดหลักสะอาด เราจะรวมฟังก์ชันช่วยเหลือทั่วไป—เช่น **แปลง twips เป็นพิกเซล** และ **แปลงสีแบบ hex**—ไว้ในคลาสยูทิลิตี้

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

- `twipsToPixels` – Word วัดมิติเป็น **twips**; เมธอดนี้แปลงเป็นพิกเซลบนหน้าจอ ซึ่งมีประโยชน์เมื่อคุณต้องการกำหนดขนาดรูปบาร์โค้ดอย่างแม่นยำ  
- `convertColor` – แปลงสตริงฐานสิบหก (เช่น `"FF0000"` สำหรับสีแดง) เป็นอ็อบเจ็กต์ `java.awt.Color` เพื่อให้คุณ **how to insert barcode** ด้วยสีพื้นหน้าและพื้นหลังที่กำหนดเองได้

## ขั้นตอนที่ 2: Implement ตัวสร้างบาร์โค้ดแบบกำหนดเอง

ต่อไปเราจะทำการ Implement อินเทอร์เฟซ `IBarcodeGenerator` คลาสนี้จะรับผิดชอบการ **generate qr code java**‑style images ที่ Aspose.Words สามารถฝังได้

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

- `getBarcodeImage` สร้างอินสแตนซ์ของ `BarcodeGenerator` ใช้สีที่ส่งมาจาก `BarcodeParameters` แล้วคืนค่าเป็น `BufferedImage`  
- เมธอดนี้ยังจัดการข้อผิดพลาดอย่างราบรื่นโดยคืนรูปภาพตัวแทน เพื่อให้การสร้างเอกสาร Word ไม่หยุดทำงาน

## ขั้นตอนที่ 3: สร้างบาร์โค้ดและ **embed barcode in Word**

เมื่อมีตัวสร้างพร้อม เราสามารถสร้างรูปบาร์โค้ดและ **insert it into a Word document** ได้ทันที

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

1. **การเริ่มต้น Document** – สร้าง `Document` ใหม่ (หรือโหลดเทมเพลตที่มีอยู่)  
2. **Barcode Parameters** – กำหนดประเภทบาร์โค้ด (`QR`), ค่าที่จะเข้ารหัส, และสีพื้นหน้า/พื้นหลัง  
3. **การแทรกรูปภาพ** – `builder.insertImage` วางบาร์โค้ดที่ขนาดต้องการ (200 × 200 พิกเซล) นี่คือหัวใจของ **how to insert barcode** ลงในไฟล์ Word  
4. **การบันทึก** – เอกสารสุดท้าย `CustomBarcodeLabels.docx` จะมีบาร์โค้ดฝังอยู่พร้อมพิมพ์หรือแจกจ่าย

## ทำไมต้องสร้างป้ายบาร์โค้ดแบบกำหนดเองด้วย Aspose.Words?

- **ควบคุมเต็มรูปแบบ** ของลักษณะบาร์โค้ด (ประเภท, ขนาด, สี)  
- **การบูรณาการที่ราบรื่น** – ไม่ต้องสร้างไฟล์ภาพกลาง; บาร์โค้ดถูกสร้างในหน่วยความจำและฝังโดยตรง  
- **ข้ามแพลตฟอร์ม** – ทำงานบน OS ใดก็ได้ที่รองรับ Java เหมาะสำหรับการสร้างเอกสารฝั่งเซิร์ฟเวอร์  
- **ขยายได้** – สามารถวนลูปผ่านแหล่งข้อมูลเพื่อสร้างป้ายส่วนบุคคลหลายร้อยใบในครั้งเดียว

## ปัญหาที่พบบ่อยและการแก้ไข

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| บาร์โค้ดแสดงเป็นสีขาว | สีใน `BarcodeParameters` เหมือนกัน (เช่น ดำบนพื้นหลังดำ) | ตรวจสอบค่าของ `foregroundColor` และ `backgroundColor` |
| รูปภาพบิดเบี้ยว | ขนาดพิกเซลที่ส่งให้ `insertImage` ไม่ถูกต้อง | ปรับค่า width/height หรือใช้การแปลง `twipsToPixels` เพื่อให้ได้ขนาดที่แม่นยำ |
| เกิดข้อผิดพลาดประเภทบาร์โค้ดที่ไม่รองรับ | ใช้ประเภทที่ `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` ไม่รู้จัก | ตรวจสอบให้แน่ใจว่าชื่อประเภทบาร์โค้ดตรงกับหนึ่งใน `EncodeTypes` ที่รองรับ (เช่น `"QR"`, `"CODE128"`) |

## คำถามที่พบบ่อย

**ถาม: สามารถใช้ Aspose.Words for Java โดยไม่ต้องมีไลเซนส์ได้หรือไม่?**  
ตอบ: ได้, แต่จะมีข้อจำกัดบางประการ ขอแนะนำให้รับ [temporary license](https://purchase.aspose.com/temporary-license/) เพื่อใช้งานเต็มรูปแบบ

**ถาม: สามารถสร้างบาร์โค้ดประเภทใดได้บ้าง?**  
ตอบ: Aspose.BarCode รองรับ QR, Code 128, EAN‑13 และรูปแบบอื่น ๆ อีกหลายประเภท ดูรายละเอียดใน [documentation](https://reference.aspose.com/words/java/) สำหรับรายการทั้งหมด

**ถาม: จะเปลี่ยนขนาดบาร์โค้ดได้อย่างไร?**  
ตอบ: ปรับค่า width และ height ใน `builder.insertImage` หรือใช้ `twipsToPixels` เพื่อแปลงหน่วยวัดของ Word เป็นพิกเซล

**ถาม: สามารถใช้ฟอนต์แบบกำหนดเองสำหรับข้อความบาร์โค้ดได้หรือไม่?**  
ตอบ: ได้, คุณสามารถปรับฟอนต์ของข้อความผ่านคุณสมบัติ `CodeTextParameters` ของ `BarcodeGenerator`

**ถาม: หากเจอปัญหาจะหาความช่วยเหลือได้จากที่ไหน?**  
ตอบ: เยี่ยมชม [support forum](https://forum.aspose.com/c/words/8/) เพื่อรับความช่วยเหลือจากชุมชนและวิศวกรของ Aspose

## สรุป

โดยทำตามขั้นตอนข้างต้น คุณจะรู้วิธี **generate custom barcode** และ **embed barcode in Word** ด้วย Aspose.Words สำหรับ Java เทคนิคนี้ยืดหยุ่นพอสำหรับแท็กสินค้าคงคลัง, ตั๋วงานอีเวนท์ หรือสถานการณ์ใด ๆ ที่ต้องการบาร์โค้ดเป็นส่วนหนึ่งของเอกสารที่สร้างขึ้น ทดลองใช้ประเภทบาร์โค้ดและตัวเลือกการจัดรูปแบบต่าง ๆ เพื่อให้ตรงกับความต้องการของธุรกิจคุณ

---

**Last Updated:** 2025-12-10  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}