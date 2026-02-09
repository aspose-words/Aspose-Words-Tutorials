---
date: 2026-02-09
description: สร้างป้ายบาร์โค้ดแบบกำหนดเองโดยใช้ Aspose Barcode Java ใน Aspose.Words
  for Java เรียนรู้วิธีฝังบาร์โค้ดในเอกสาร Word และสร้างตัวอย่าง QR Code ด้วย Java.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: การสร้างป้ายบาร์โค้ดแบบกำหนดเองด้วย Aspose Barcode Java
url: /th/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สร้างป้ายบาร์โค้ดแบบกำหนดเองด้วย Aspose Barcode Java

## บทนำการสร้างป้ายบาร์โค้ดแบบกำหนดเองใน Aspose.Words สำหรับ Java

บาร์โค้ดเป็นสิ่งสำคัญในแอปพลิเคชันสมัยใหม่ และ **Aspose Barcode Java** ทำให้การสร้างบาร์โค้ดโดยตรงในเอกสาร Word เป็นเรื่องง่าย ไม่ว่าคุณจะต้องการ **ฝังบาร์โค้ดใน Word**, สร้าง QR code สำหรับ URL, หรือแปลงหน่วยวัดต่าง ๆ บทเรียนนี้จะพาคุณผ่านทุกขั้นตอนที่จำเป็น พร้อมหรือยัง? ไปกันเลย!

## คำตอบสั้น
- **ไลบรารีใดสร้างบาร์โค้ดใน Java?** Aspose Barcode Java คู่กับ Aspose.Words for Java.  
- **ประเภทบาร์โค้ดที่แสดงคืออะไร?** QR code (generate qr code java).  
- **ฉันจะแปลง twips เป็นพิกเซลอย่างไร?** ใช้วิธีการยูทิลิตี้ `twipsToPixels` ที่ให้มา.  
- **ฉันสามารถเพิ่มบาร์โค้ดลงในไฟล์ Word ที่มีอยู่ได้หรือไม่?** ได้ – เพียงใช้เมธอด `DocumentBuilder.insertImage`.  
- **ฉันต้องการใบอนุญาตหรือไม่?** ใบอนุญาตชั่วคราวจะลบข้อจำกัดการประเมิน.

## Aspose Barcode Java คืออะไร?
Aspose Barcode Java เป็น API ที่ทรงพลังซึ่งช่วยให้นักพัฒนาสามารถสร้างบาร์โค้ด 1D และ 2D หลากหลายประเภท (รวมถึง QR code) อย่างอัตโนมัติ เมื่อรวมกับ Aspose.Words สำหรับ Java คุณสามารถ **ฝังบาร์โค้ดใน Word** เอกสารได้โดยไม่ต้องออกจากสภาพแวดล้อม Java ของคุณ.

## ทำไมต้องใช้ Aspose Barcode Java ร่วมกับ Aspose.Words?
- **การควบคุมเต็มรูปแบบ** เกี่ยวกับลักษณะของบาร์โค้ด (สี, ขนาด, รูปแบบ).  
- **การบูรณาการที่ราบรื่น** – ภาพบาร์โค้ดสามารถแทรกโดยตรงลงในเอกสาร Word.  
- **ข้ามแพลตฟอร์ม** – ทำงานบนแพลตฟอร์มที่รองรับ Java ใดก็ได้.  
- **ขยายได้** – คุณสามารถสร้างคลาสยูทิลิตี้เพื่อใช้ตรรกะบาร์โค้ดซ้ำในหลายโครงการ.

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มเขียนโค้ด โปรดตรวจสอบว่าคุณมีสิ่งต่อไปนี้:

- Java Development Kit (JDK): เวอร์ชัน 8 หรือสูงกว่า.  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse หรือ IDE ใดก็ได้ที่คุณชอบ.  
- Temporary License: รับ [temporary license](https://purchase.aspose.com/temporary-license/) เพื่อการเข้าถึงโดยไม่มีข้อจำกัด.

## นำเข้าแพ็กเกจ

เราจะใช้ไลบรารี Aspose.Words และ Aspose.BarCode ให้นำเข้าแพ็กเกจต่อไปนี้ในโปรเจกต์ของคุณ:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

การนำเข้าดังกล่าวทำให้เราสามารถใช้ฟีเจอร์การสร้างบาร์โค้ดและรวมเข้ากับเอกสาร Word ได้  
มาจัดแบ่งงานนี้เป็นขั้นตอนที่จัดการได้

## ขั้นตอนที่ 1: สร้างคลาสยูทิลิตี้สำหรับการทำงานกับบาร์โค้ด

เพื่อทำให้การทำงานที่เกี่ยวกับบาร์โค้ดง่ายขึ้น เราจะสร้างคลาสยูทิลิตี้พร้อมเมธอดช่วยเหลือสำหรับงานทั่วไป เช่น การแปลงสีและ **convert twips to pixels**.

### Code:

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

- `twipsToPixels` แปลงหน่วยวัดที่ Word ใช้ (twips) เป็นพิกเซลบนหน้าจอ – เป็นยูทิลิตี้ที่มีประโยชน์เมื่อคุณต้องการขนาดที่แม่นยำ.  
- `convertColor` แปลงสตริงสีแบบ hexadecimal (เช่น “FF0000”) ให้เป็นอ็อบเจ็กต์ Java `Color` ทำให้คุณสามารถกำหนดสีพื้นหน้าและพื้นหลังของบาร์โค้ดได้.

## ขั้นตอนที่ 2: นำไปใช้ Custom Barcode Generator

เราจะทำการนำเข้าอินเทอร์เฟซ `IBarcodeGenerator` เพื่อให้ Aspose.Words สามารถขอภาพบาร์โค้ดได้ทุกครั้งที่พบฟิลด์บาร์โค้ด.

### Code:

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

- `getBarcodeImage` สร้าง `BarcodeGenerator` โดยใช้ประเภท **generate qr code java** ที่คุณระบุ (QR ในตัวอย่างของเรา).  
- มันกำหนดสีพื้นหน้าและพื้นหลังผ่านเมธอดยูทิลิตี้ แล้วคืนค่าภาพที่เรนเดอร์แล้ว.  
- ภาพสำรองทำให้โปรแกรมดำเนินต่อได้แม้การสร้างบาร์โค้ดล้มเหลว.

## ขั้นตอนที่ 3: สร้างบาร์โค้ดและเพิ่มลงในเอกสาร Word

ตอนนี้เราจะรวมทุกอย่างเข้าด้วยกัน: สร้างเอกสาร, สร้างบาร์โค้ด, และ **how to add barcode** ไปยังไฟล์ Word.

### Code:

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

1. **Document Initialization** – สร้าง `Document` ใหม่ (หรือคุณอาจโหลดไฟล์ .docx ที่มีอยู่).  
2. **Barcode Parameters** – กำหนดประเภท (`QR`), ค่า, และสี, แสดงการใช้ **generate qr code java**.  
3. **Image Insertion** – `builder.insertImage` วางบาร์โค้ดในตำแหน่งที่ต้องการ, แสดงอย่างชัดเจน **how to add barcode** ไปยังไฟล์ Word.  
4. **Saving** – เอกสารสุดท้าย (`CustomBarcodeLabels.docx`) มีบาร์โค้ดฝังอยู่พร้อมสำหรับการพิมพ์หรือแจกจ่าย.

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|-------|-----|
| บาร์โค้ดปรากฏเป็นสีขาว | สตริงสีไม่ถูกต้องหรือประเภทบาร์โค้ดไม่รองรับ | ตรวจสอบรูปแบบสีแบบ hex และใช้ประเภทที่รองรับ (เช่น QR, Code128). |
| ขนาดภาพไม่ตรง | การแปลงพิกเซลไม่ถูกต้อง | ใช้ `twipsToPixels` เพื่อคำนวณขนาดที่แม่นยำตามการจัดวางของ Word. |
| ข้อยกเว้นใบอนุญาต | ไม่มีใบอนุญาต Aspose ที่ถูกต้อง | ใช้ใบอนุญาตชั่วคราวหรือใบอนุญาตที่ซื้อก่อนรันโค้ด. |

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้ Aspose.Words สำหรับ Java ได้โดยไม่ต้องมีใบอนุญาตหรือไม่?**  
A: ใช่, แต่คุณจะเจอข้อจำกัดการประเมินผล รับ [temporary license](https://purchase.aspose.com/temporary-license/) เพื่อการทำงานเต็มรูปแบบ.

**Q: ฉันสามารถสร้างบาร์โค้ดประเภทใดได้บ้าง?**  
A: Aspose.BarCode รองรับ QR, Code 128, EAN‑13 และอื่น ๆ อีกมาก ดู [documentation](https://reference.aspose.com/words/java/) อย่างเป็นทางการสำหรับรายการทั้งหมด.

**Q: ฉันจะเปลี่ยนขนาดบาร์โค้ดได้อย่างไร?**  
A: ปรับพารามิเตอร์ความกว้าง/ความสูงใน `builder.insertImage` หรือแก้ไขคุณสมบัติ `XDimension` และ `BarHeight` ของอ็อบเจ็กต์ `BarcodeGenerator`.

**Q: ฉันสามารถใช้ฟอนต์กำหนดเองสำหรับส่วนที่อ่านได้ของบาร์โค้ดหรือไม่?**  
A: แน่นอน ใช้คุณสมบัติ `CodeTextParameters` เพื่อกำหนดฟอนต์, ขนาด, และสไตล์.

**Q: ฉันจะหาความช่วยเหลือเกี่ยวกับ Aspose.Words ได้จากที่ไหน?**  
A: เยี่ยมชม [support forum](https://forum.aspose.com/c/words/8/) เพื่อรับความช่วยเหลือจากชุมชนและการสนับสนุนอย่างเป็นทางการ.

---

**อัปเดตล่าสุด:** 2026-02-09  
**ทดสอบกับ:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}