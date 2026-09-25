---
category: general
date: 2026-01-11
description: เรียนรู้วิธีการจับคำเตือนการแทนที่ฟอนต์โดยใช้ Aspose.Words สำหรับ Java
  บทเรียนเชิงขั้นตอนนี้ยังครอบคลุม LoadOptions และการเรียกคืนคำเตือนด้วย
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: th
og_description: บันทึกคำเตือนการแทนที่ฟอนต์ด้วย Aspose.Words for Java. ทำตามคำแนะนำนี้เพื่อกำหนด
  LoadOptions และ callback คำเตือนสำหรับการโหลดเอกสารที่เชื่อถือได้.
og_title: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java – คู่มือเต็ม
tags:
- Aspose.Words
- Java
- Document Processing
title: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกคำเตือนการแทนที่ฟอนต์ – คู่มือเต็ม Java

คุณเคยต้องการ **บันทึกคำเตือนการแทนที่ฟอนต์** ขณะเปิดเอกสาร Word ที่ขาดฟอนต์หรือไม่? นี่เป็นปัญหาที่พบบ่อย โดยเฉพาะเมื่อคุณกำลังสร้าง PDF หรือพิมพ์บนเซิร์ฟเวอร์ที่ไม่ได้ติดตั้งฟอนต์ทุกแบบ ข่าวดีคือ Aspose.Words for Java ทำให้เรื่องนี้ง่ายดาย—เพียงกำหนดอ็อบเจ็กต์ `LoadOptions` แล้วเชื่อมต่อ callback สำหรับคำเตือน ในคู่มือนี้คุณจะได้เห็นขั้นตอนการทำอย่างละเอียด เหตุผลที่สำคัญ และสิ่งที่คาดว่าจะเกิดขึ้นเมื่อคำเตือนถูกเรียกใช้

เราจะพูดถึงหัวข้อที่เกี่ยวข้องเช่น **Aspose.Words font substitution**, การใช้ **Java warning callback**, และแนวทางปฏิบัติที่ดีที่สุดสำหรับ **LoadOptions usage**. เมื่อจบคุณจะมีโค้ดสั้นที่พร้อมใช้งานซึ่งบันทึกเหตุการณ์ฟอนต์ที่หายไปทุกครั้ง เพื่อให้กระบวนการต่อเนื่องของคุณไม่ต้องเจอความประหลาดใจ

## ข้อกำหนดเบื้องต้น

- Java 17 (หรือ JDK ล่าสุด) ที่ติดตั้งและกำหนดค่าแล้ว
- Aspose.Words for Java 23.10 (หรือใหม่กว่า) บน classpath ของคุณ
- เอกสาร Word ที่อ้างอิงฟอนต์ที่คุณไม่มีในเครื่อง (เช่น `DocWithMissingFont.docx`)
- ความคุ้นเคยพื้นฐานกับบล็อก try/catch ของ Java—ไม่มีอะไรซับซ้อน

หากรายการใดข้างต้นไม่คุ้นเคย ให้หยุดพักสักครู่และติดตั้งไลบรารีจาก Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

เมื่อพื้นฐานพร้อมแล้ว ไปสู่โค้ดกันเลย

## ขั้นตอนที่ 1: ตั้งค่า Warning Callback เพื่อ **บันทึกคำเตือนการแทนที่ฟอนต์**

สิ่งแรกที่คุณต้องการคือ callback ที่ Aspose.Words จะเรียกใช้เมื่อพบฟอนต์ที่หายไป นี่คือจุดที่เราจะ **บันทึกคำเตือนการแทนที่ฟอนต์** Callback นี้จะทำการ implement อินเทอร์เฟซ `IWarningCallback` และตรวจสอบ `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**ทำไมเรื่องนี้ถึงสำคัญ:** หากไม่มี callback, Aspose.Words จะเปลี่ยนฟอนต์ที่หายไปเป็นฟอนต์เริ่มต้นโดยเงียบ ๆ และคุณจะไม่รู้ว่าผลลัพธ์ที่แสดงเปลี่ยนแปลงไปอย่างไร การบันทึกคำเตือนทำให้คุณสามารถบันทึก, แจ้งเตือน, หรือแม้กระทั่งยกเลิกการโหลดได้หากฟอนต์ที่หายไปเป็นสิ่งสำคัญ

## ขั้นตอนที่ 2: กำหนดค่า **LoadOptions** และลงทะเบียน Callback

ตอนนี้เราจะสร้างอินสแตนซ์ของ `LoadOptions` และเชื่อมต่อ `FontWarningCallback` ของเรา ขั้นตอนนี้สำคัญสำหรับ **LoadOptions usage** และทำให้การโหลดเอกสารทุกครั้งผ่านตัวกรองคำเตือนเดียวกัน

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**เคล็ดลับ:** คุณสามารถใช้ `LoadOptions` เดียวกันสำหรับหลายเอกสารได้ ซึ่งช่วยลดบรรทัดโค้ดที่ซ้ำซ้อนและรับประกันการจัดการ **document loading warnings** อย่างสม่ำเสมอในแอปพลิเคชันของคุณ

## ขั้นตอนที่ 3: โหลดเอกสารและสังเกตผลลัพธ์

เมื่อเชื่อมต่อ callback แล้ว เพียงโหลดไฟล์ Word ของคุณ หากเอกสารอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง callback จะทำงานและพิมพ์รายละเอียดลงคอนโซล

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล

สมมติว่า `DocWithMissingFont.docx` อ้างอิงฟอนต์ที่หายไป *“Comic Sans MS”* คุณจะเห็นประมาณนี้:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

หากเอกสารไม่มี **ฟอนต์ที่หายไป** คอนโซลจะแสดงเพียงบรรทัดสุดท้ายเท่านั้น ซึ่งยืนยันว่า callback ของคุณไม่ได้สร้างผลบวกเท็จ

## ขั้นตอนที่ 4: จัดการกรณีขอบและข้อผิดพลาดทั่วไป

### ฟอนต์ที่หายไปหลายแบบ

หากเอกสารใช้ฟอนต์ที่ไม่มีอยู่หลายแบบ callback จะทำงานหนึ่งครั้งต่อฟอนต์ คุณจะได้รับชุดข้อความแต่ละข้อความมี `source` และ `description` ของตนเอง ไม่จำเป็นต้องเพิ่มโค้ด—เพียงตรวจสอบให้ระบบบันทึกของคุณรองรับการเรียกต่อเนื่องอย่างรวดเร็ว

### การละเว้นคำเตือน

ในกรณีหายากคุณอาจต้องการละเว้นการแทนที่บางประเภท (เช่น คุณรู้ว่าการ fallback ใด ๆ ยอมรับได้) ขยายตรรกะของ callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### ความปลอดภัยของเธรด

โดยค่าเริ่มต้น `LoadOptions` ของ Aspose.Words ไม่ปลอดภัยต่อการทำงานหลายเธรด หากคุณโหลดเอกสารพร้อมกัน ให้สร้างอินสแตนซ์ `LoadOptions` แยกสำหรับแต่ละเธรด หรือทำให้ callback ทำงานแบบซิงโครไนซ์เพื่อหลีกเลี่ยง race condition

## ขั้นตอนที่ 5: ตรวจสอบฟอนต์ที่ถูกแทนที่ในเอกสารผลลัพธ์

หลังจากโหลด คุณอาจต้องการยืนยันว่าการแทนที่เกิดขึ้นจริง API ให้คุณวนลูปทุก run และตรวจสอบชื่อฟอนต์ที่ใช้จริง:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

โค้ดสั้นนี้พิมพ์แต่ละ text run พร้อมฟอนต์สุดท้ายของมัน เป็นการตรวจสอบความถูกต้องที่สะดวกเมื่อคุณสร้าง pipeline การแปลง PDF อัตโนมัติ

## ตัวอย่างการทำงานเต็มรูปแบบ

Putting everything together, here’s the complete, ready‑to‑run program:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

บันทึกไฟล์นี้เป็น `FontSubstitutionInfo.java` คอมไพล์ด้วย `javac` แล้วรัน `java FontSubstitutionInfo` คุณจะเห็นข้อความคำเตือน (ถ้ามี) ตามด้วยรายการของ runs และฟอนต์สุดท้ายของแต่ละอัน

## ภาพประกอบ

![ภาพหน้าจอแสดงผลลัพธ์คอนโซลที่แสดงคำเตือนการแทนที่ฟอนต์](/images/font-substitution-warning.png "ตัวอย่างการบันทึกคำเตือนการแทนที่ฟอนต์")

*Alt text:* **capture font substitution warnings** – ผลลัพธ์คอนโซลหลังจากโหลดเอกสารที่มีฟอนต์หายไป

## สรุป

ตอนนี้คุณรู้วิธี **บันทึกคำเตือนการแทนที่ฟอนต์** ด้วย Aspose.Words for Java แล้ว โดยการกำหนดอ็อบเจ็กต์ `LoadOptions` และให้ `IWarningCallback` ที่กำหนดเอง คุณจะได้มองเห็นเหตุการณ์ฟอนต์ที่หายไปทั้งหมดซึ่งอาจส่งผลต่อการแสดงผลของเอกสารโดยเงียบ ๆ เทคนิคนี้เชื่อมต่อโดยตรงกับการจัดการ **Aspose.Words font substitution**, ทำให้ **document loading warnings** มีความน่าเชื่อถือ และให้ความยืดหยุ่นในการบันทึก, แจ้งเตือน หรือยกเลิกตามกฎธุรกิจของคุณ

### ขั้นตอนต่อไป?

- สำรวจรูปแบบ **Java warning callback** สำหรับประเภทคำเตือนอื่น ๆ (เช่น `DEPRECATED_FEATURE`).
- ผสานวิธีนี้กับ **PDF conversion** เพื่อรับประกันว่าฟอนต์ที่แทนที่จะไม่ทำให้เลย์เอาต์เสียหาย.
- ศึกษาเชิงลึกเกี่ยวกับ **LoadOptions usage**—ทดลองใช้ `Password`, `Encoding`, และ `ResourceLoadingCallback` สำหรับสถานการณ์ขั้นสูง

คุณสามารถปรับแต่ง callback, ส่งคำเตือนไปยังเฟรมเวิร์กการบันทึก, หรือแม้กระทั่งโยนข้อยกเว้นแบบกำหนดเองหากฟอนต์สำคัญหายไปได้อย่างอิสระ ขอบเขตไม่มีขีดจำกัด และตอนนี้คุณมีพื้นฐานที่มั่นคงสำหรับการพัฒนาต่อไป

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณแสดงผลตามที่คุณคาดหวังเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}