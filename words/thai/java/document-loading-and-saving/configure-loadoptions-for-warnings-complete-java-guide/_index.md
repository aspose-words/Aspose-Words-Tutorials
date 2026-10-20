---
category: general
date: 2026-06-30
description: กำหนดค่า LoadOptions สำหรับคำเตือนใน Aspose.Words Java. เรียนรู้วิธีตั้งค่า
  callback คำเตือนสำหรับการแทนที่ฟอนต์และคำเตือนอื่น ๆ ของ load‑options.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: th
og_description: กำหนดค่า LoadOptions สำหรับคำเตือนใน Aspose.Words Java คู่มือนี้แสดงวิธีดักจับการแจ้งเตือนการแทนที่ฟอนต์ด้วย
  callback คำเตือน.
og_title: กำหนดค่า LoadOptions สำหรับคำเตือน – บทเรียน Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: กำหนดค่า LoadOptions สำหรับคำเตือน – คู่มือ Java ฉบับสมบูรณ์
url: /th/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กำหนดค่า LoadOptions สำหรับคำเตือน – คู่มือ Java ฉบับสมบูรณ์

เคยต้อง **กำหนดค่า LoadOptions สำหรับคำเตือน** เมื่อเปิดไฟล์ Word ด้วย Aspose.Words for Java หรือไม่? คุณไม่ได้เป็นคนเดียว นักพัฒนาหลายคนเจอปัญหาเมื่อฟอนต์ที่หายไปถูกแทนที่โดยเงียบ ๆ ทำให้ไฟล์ PDF สุดท้ายดูไม่ตรงกับแบรนด์ ข่าวดีคือ? ด้วยการเชื่อม **Java warning callback** เข้าไปใน `LoadOptions` ของคุณ คุณสามารถดักจับการแจ้งเตือนการแทนที่ฟอนต์ได้ทันทีเมื่อเกิดขึ้น

ในบทแนะนำนี้เราจะพาคุณผ่านตัวอย่างเชิงปฏิบัติที่ไม่เพียงแสดงวิธีตั้งค่า callback แต่ยังอธิบาย *ทำไม* แต่ละส่วนถึงสำคัญ เมื่อเสร็จสิ้นคุณจะสามารถ **จัดการคำเตือนฟอนต์**, บันทึกลงไฟล์, หรือแม้แต่เปลี่ยนฟอนต์แบบเรียลไทม์—โดยไม่ต้องเดา

## สิ่งที่คุณจะได้เรียนรู้

- โปรแกรม Java ที่สามารถรันได้เต็มรูปแบบและพิมพ์คำเตือนการแทนที่ฟอนต์ทุกครั้ง
- ความเข้าใจในกลไก **Aspose.Words font substitution**
- เคล็ดลับการปรับแต่งการจัดการคำเตือนสำหรับโครงการขนาดใหญ่
- ความรู้เชิงลึกเกี่ยวกับ **document loading options** และเวลาที่ควรปรับเปลี่ยน

> **ข้อกำหนดเบื้องต้น:** Java 8+ และไลบรารี Aspose.Words for Java (เวอร์ชัน 23.9 หรือใหม่กว่า) ไม่ต้องการการพึ่งพาอื่นใด

---

## ขั้นตอนที่ 1: กำหนดค่า LoadOptions สำหรับคำเตือน

สิ่งแรกที่คุณต้องมีคืออินสแตนซ์ `LoadOptions` ที่รู้ว่าต้องรายงานคำเตือน คิดว่า `LoadOptions` เป็นกล่องเครื่องมือที่คุณมอบให้ Aspose.Words ก่อนที่มันจะเปิดไฟล์

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
`LoadOptions` ควบคุมวิธีที่ไลบรารีอ่านเอกสาร โดยการกำหนด `IWarningCallback` คุณบอก Aspose.Words ให้เรียกโค้ดของคุณทุกครั้งที่เจอสิ่งที่ควรระวัง—เช่นฟอนต์ที่หายไป หากไม่มีการตั้งค่านี้ ไลบรารีจะทำการแทนที่ฟอนต์โดยเงียบ ๆ และคุณจะไม่รู้เลย

> **เคล็ดลับ:** หากต้องการดักจับ *ทุก* คำเตือน ให้ลบเงื่อนไข `if` ออกไป ตอนนี้เราจะเน้นที่ปัญหาฟอนต์เพราะเป็นสาเหตุหลักของความผิดปกติในการจัดหน้า

---

## ขั้นตอนที่ 2: โหลดเอกสารโดยใช้ตัวเลือกที่กำหนดไว้

เมื่อ callback พร้อมแล้ว ให้โหลดไฟล์ `.docx` (หรือรูปแบบที่รองรับอื่น) ด้วย `LoadOptions` เดียวกัน นี่คือจุดที่ **document loading options** มีผลจริง

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**เบื้องหลังการทำงาน:**  
เมื่อ Aspose.Words วิเคราะห์ `input.docx` มันจะสแกนตารางฟอนต์ หากฟอนต์ที่อ้างอิงในเอกสารไม่ได้ติดตั้งบนเครื่องโฮสต์ เ็นจิ้นจะสร้างคำเตือน `FONT_SUBSTITUTION` ซึ่งจะเรียก callback ที่เรากำหนดไว้ทันที

---

## ขั้นตอนที่ 3: บันทึกเอกสาร – คำเตือนได้ถูกพิมพ์แล้ว

การบันทึกเอกสารทำได้ง่าย แต่เป็นช่วงเวลาที่คุณสามารถตรวจสอบว่า callback ทำงานถูกต้องหรือไม่ คำเตือนทั้งหมดจะถูกพิมพ์ในขั้นตอนการโหลด ดังนั้นการบันทึกจึงเป็นเพียงการทำความสะอาด

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

หากคุณไม่เห็นอะไรเลย อาจเป็นเพราะเอกสารใช้ฟอนต์ที่ติดตั้งแล้วทั้งหมด หรือ callback ไม่ได้เชื่อมต่ออย่างถูกต้อง—ตรวจสอบขั้นตอน 1 อีกครั้ง

---

## ขั้นตอนที่ 4: ขยาย Callback เพื่อ **จัดการคำเตือนฟอนต์** อย่างราบรื่น

การพิมพ์ลงคอนโซลเหมาะกับการสาธิต แต่โค้ดในสภาพแวดล้อมการผลิตมักต้องการการจัดการที่ลึกซึ้งกว่า: บันทึกลงไฟล์, ส่งการแจ้งเตือน, หรือแม้แต่สลับฟอนต์โดยอัตโนมัติ

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**เหตุผลที่คุณควรทำเช่นนี้:**  
ไฟล์บันทึกให้ข้อมูลเชิงลึกหลังเหตุการณ์โดยเฉพาะเมื่อประมวลผลชุดเอกสารจำนวนมาก บล็อกการแทนที่แบบเลือกทำให้คุณ **กำหนดค่า LoadOptions สำหรับคำเตือน** *และ* แทรกแซงเพื่อบังคับใช้นโยบายฟอนต์ขององค์กร

---

## ขั้นสูง: การควบคุมสถานการณ์ **Aspose.Words Font Substitution** อื่น ๆ

Callback ไม่ได้จำกัดแค่ฟอนต์ที่หายไป คุณยังสามารถดักจับ:

- **อักขระ Unicode ที่ไม่รองรับ** (`WarningType.UNSUPPORTED_CHAR`)
- **ปัญหาการเขียนสคริปต์ซับซ้อน** (`WarningType.COMPLEX_SCRIPT`)

เพียงขยายเงื่อนไข `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

วิธีนี้ทำให้โซลูชันของคุณแข็งแรงสำหรับเอกสารหลายภาษา ซึ่งเป็นกรณีขอบที่พบบ่อยในแอปพลิเคชันระดับโลก

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่พร้อมรัน เพียงคัดลอกไปวางใน IDE ของ Java ใดก็ได้ แทนที่ตัวแปร `YOUR_DIRECTORY` ด้วยพาธของคุณ แล้วกด *Run*

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- คอนโซลพิมพ์คำเตือนการแทนที่ฟอนต์ใด ๆ
- `font-warnings.log` มีรายการพร้อมเวลาประทับ (หากคุณเปิดใช้งานการบันทึกแบบเลือก)
- `output.docx` ถูกบันทึกด้วยฟอนต์ที่แทนที่ตามที่กำหนดไว้

---

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ปัญหา | ทำไมถึงเกิด | วิธีแก้ |
|---------|----------------|-----|
| **ไม่มีคำเตือนปรากฏ** | Callback ไม่ได้เชื่อมต่อ หรือเอกสารใช้ฟอนต์ที่ติดตั้งแล้วทั้งหมด | ตรวจสอบว่า `loadOptions.setWarningCallback(...)` ถูกเรียก *ก่อน* โหลดเอกสาร |
| **FileNotFoundException** บน `input.docx` | พาธผิดหรือไฟล์ไม่ได้อยู่ในโครงการ | ใช้พาธเต็มหรือวางไฟล์ในโฟลเดอร์ resources ของโปรเจกต์ |
| **ประสิทธิภาพช้าลง** เมื่อประมวลผลเอกสารหลายพันไฟล์ | การบันทึกลงดิสก์มากเกินไปสำหรับแต่ละคำเตือน | เก็บบันทึกเป็นบัฟเฟอร์แล้วเขียนเป็นชุด, หรือจำกัดการบันทึกเฉพาะคำเตือนสำคัญ |
| **ฟอนต์ถูกแทนที่โดยไม่คาดคิด** แม้มี fallback | ตารางการแทนที่ไม่ได้ถูกนำไปใช้เร็วพอ | ตั้งค่าการแทนที่ **ก่อน** โหลดเอกสาร, หรือใช้ `FontSettings.setSubstitutionSettings` แบบทั่วโลก |

---

## ขั้นตอนต่อไป

เมื่อคุณเชี่ยวชาญการ **กำหนดค่า LoadOptions สำหรับคำเตือน** แล้ว ลองสำรวจหัวข้อต่อไปนี้:

- **การประมวลผลเป็นชุด**: วนลูปโฟลเดอร์เอกสารทั้งหมด รวบรวมคำเตือนฟอนต์เป็นรายงานเดียว
- **ผู้ให้บริการฟอนต์แบบกำหนดเอง**: โหลดฟอนต์จากแชร์เครือข่ายหรือทรัพยากรฝังในแอปแทนการใช้ OS
- **ผสานกับเฟรมเวิร์กบันทึก** เช่น Log4j เพื่อให้ได้การติดตามระดับองค์กร
- สำรวจ **document loading options** อื่น ๆ เช่นการตรวจจับ `LoadFormat` หรือการจัดการ `Password` สำหรับไฟล์ที่ป้องกัน

ทุกหัวข้อนี้ใช้รูปแบบเดียวกัน—สร้างอ็อบเจ็กต์ `LoadOptions`, แนบ callback ที่เหมาะสม, แล้วให้ Aspose.Words ทำงานหนักให้คุณ

---

## สรุป

เราได้เจาะลึกวิธี **กำหนดค่า LoadOptions สำหรับคำเตือน** ใน Aspose.Words for Java ตั้งค่า **Java warning callback** และใช้ข้อมูลนั้นเพื่อ **จัดการคำเตือนฟอนต์** อย่างชาญฉลาด โค้ดสั้นกระชับ แนวคิดชัดเจน และคุณมีพื้นฐานที่มั่นคงสำหรับการขยายการจัดการคำเตือนไปยังสถานการณ์อื่น ๆ เช่นอักขระที่ไม่รองรับหรือสคริปต์ซับซ้อน

ลองใช้งาน ปรับตารางการแทนที่ให้ตรงกับฟอนต์แบรนด์ของคุณ แล้วดูการแทนที่ฟอนต์เงียบ ๆ หายไปอย่างไร้รอยต่อ Happy coding!

![แผนภาพแสดงกระบวนการกำหนดค่า LoadOptions สำหรับคำเตือน, โหลดเอกสาร, ดักจับเหตุการณ์การแทนที่ฟอนต์, และบันทึกผลลัพธ์](configure-loadoptions-for-warnings-diagram.png "กระบวนการกำหนดค่า LoadOptions สำหรับคำเตือน")

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ในโครงการของคุณ

- [จับคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [วิธีตั้งค่า LoadOptions ใน Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [วิธีโหลดเอกสาร RTF พร้อมกำหนดค่า RTF Load Options ใน Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}