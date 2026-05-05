---
category: general
date: 2026-05-04
description: บทเรียนการแทนที่ฟอนต์ของ Aspose แสดงวิธีจัดการกับฟอนต์ที่หายไปใน Java
  โดยใช้การเรียกกลับเตือนและ LoadOptions เพื่อการโหลดเอกสารที่เชื่อถือได้.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: th
og_description: บทแนะนำการแทนที่ฟอนต์ของ Aspose อธิบายวิธีจัดการกับฟอนต์ที่หายไปใน
  Java, จับเหตุการณ์การแทนที่, และทำให้เอกสารของคุณดูถูกต้อง.
og_title: บทเรียนการแทนที่ฟอนต์ของ Aspose – จัดการกับฟอนต์ที่หายไป
tags:
- Aspose.Words
- Java
- Font Management
title: บทเรียนการแทนที่ฟอนต์ของ Aspose – จัดการฟอนต์ที่หายไป
url: /th/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution Tutorial – จัดการฟอนต์ที่หายไป

เคยต้องการ **aspose font substitution tutorial** เพราะไฟล์ DOCX ที่คุณโหลดขึ้นมาดูผิดรูปหรือไม่? คุณไม่ได้เป็นคนเดียว—ฟอนต์ที่หายไปเป็นสาเหตุที่ซ่อนเร้นของบั๊กที่ทำให้รายงานที่จัดรูปแบบอย่างสมบูรณ์กลายเป็นข้อความยุ่งเหยิง ข่าวดีคือ Aspose.Words มีวิธีที่สะอาดตาในการ **จัดการฟอนต์ที่หายไป** ก่อนที่มันจะทำลายเลย์เอาต์ของคุณ

ในคู่มือนี้เราจะพาคุณผ่านตัวอย่าง Java ที่พร้อมรันเต็มรูปแบบ ซึ่งจับคำเตือนการแทนที่ฟอนต์ อธิบายว่าทำไมแต่ละส่วนจึงสำคัญ และแสดงวิธีตรวจสอบผลลัพธ์ เมื่ออ่านจบคุณจะรู้วิธีทำให้เอกสารของคุณดูคมชัดแม้ฟอนต์ต้นฉบับจะไม่มีอยู่บนเครื่อง

## สิ่งที่คุณจะได้เรียนรู้

- วิธีลงทะเบียน `IWarningCallback` แบบกำหนดเองเพื่อฟังเหตุการณ์ `FONT_SUBSTITUTION`  
- ทำไมการใช้ `LoadOptions` จึงเป็นวิธีที่แนะนำสำหรับการจัดการฟอนต์ที่เชื่อถือได้  
- วิธีทดสอบโซลูชันด้วยเอกสารที่ทำให้ฟอนต์เสีย intentionally  
- จุดบกพร่องทั่วไป (เช่น ลืมตั้งค่า callback) และวิธีแก้ไขอย่างรวดเร็ว  

**ข้อกำหนดเบื้องต้น**: มี Java 8+ ติดตั้ง, ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (หรือเวอร์ชันทดลองฟรี) และ IDE พื้นฐานอย่าง IntelliJ หรือ Eclipse ไม่ต้องใช้ไลบรารีภายนอกอื่นใด

---

![Aspose font substitution tutorial diagram](https://example.com/images/font-substitution-diagram.png "แผนภาพ Aspose font substitution tutorial")

## ขั้นตอนที่ 1 – กำหนด Warning Callback เพื่อจับการแทนที่ฟอนต์  

สิ่งแรกที่ Aspose.Words ทำเมื่อไม่พบฟอนต์ที่ร้องขอคือส่งเหตุการณ์ `WarningInfo` โดยการทำ `IWarningCallback` คุณสามารถบันทึก แสดงผล หรือแม้แต่ยกเลิกการโหลดได้หากต้องการ

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**ทำไมเรื่องนี้สำคัญ** – หากไม่มี callback คุณจะไม่มีวันรู้ว่า Aspose ได้สลับ *Arial* เป็น *Liberation Sans* (หรือฟอนต์สำรองใด ๆ ที่เลือก) การสลับแบบเงียบนี้อาจทำให้เลย์เอาต์เปลี่ยนแปลง โดยเฉพาะในตารางหรือเลย์เอาต์หลายคอลัมน์

---

## ขั้นตอนที่ 2 – ผูก Callback กับ `LoadOptions`

`LoadOptions` เป็นศูนย์กลางของทุกอย่างที่มีผลต่อการอ่านเอกสาร โดยการเชื่อม callback ที่นี่คุณรับประกันว่า **ทุก** เอกสารที่โหลดด้วยตัวเลือกเหล่านี้จะเรียกใช้ตรรกะเตือนของคุณ

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**เคล็ดลับ** – หากคุณวางแผนจะโหลดหลายเอกสารเป็นชุด ให้ใช้อินสแตนซ์ `LoadOptions` เดียวกัน มันช่วยลดภาระการสร้างอ็อบเจกต์และทำให้การบันทึกของคุณสอดคล้องกัน

---

## ขั้นตอนที่ 3 – โหลดเอกสารที่อาจต้องการการแทนที่ฟอนต์  

ตอนนี้เราจะอ่านไฟล์ที่เรารู้ว่าขาดฟอนต์ เปลี่ยน `YOUR_DIRECTORY` ให้เป็นโฟลเดอร์ที่เก็บไฟล์ทดสอบของคุณ

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

เมื่อ loader พบ glyph ที่ไม่สามารถแสดงได้ callback จาก **ขั้นตอน 1** จะพิมพ์ข้อความเป็นมิตรลงคอนโซล ตัวอย่างเช่น:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**กรณีขอบ** – หากเอกสารมีฟอนต์ *embedded* อยู่ Aspose จะใช้ฟอนต์เหล่านั้นก่อนและข้ามการเตือน นี่เป็นพฤติกรรมที่คาดหวัง; คุณจะเห็นคำเตือนเฉพาะฟอนต์ที่จริง ๆ แล้วหายไปเท่านั้น

---

## ขั้นตอนที่ 4 – บันทึกเอกสาร (พร้อมฟอนต์ที่ถูกแทนที่)

หลังจากการโหลดเสร็จสิ้น Aspose จะได้สลับฟอนต์ที่หายไปภายในแล้ว การบันทึกเอกสารจะคงการแทนที่ไว้ ดังนั้นไฟล์ผลลัพธ์จะดูเหมือนกับที่คุณเห็นในคอนโซล

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

เปิด `loaded.docx` ด้วย Word หรือ LibreOffice คุณจะเห็นเลย์เอาต์ไม่เปลี่ยนแปลง แม้ว่าฟอนต์ต้นฉบับจะไม่ได้ติดตั้งบนเครื่องของคุณ

---

## ขั้นตอนที่ 5 – ตรวจสอบผลลัพธ์ด้วยโปรแกรม (ทางเลือก)

หากต้องการความมั่นใจเพิ่มเติมว่าไม่มีการแทนที่ที่ไม่คาดคิดผ่านเข้ามา คุณสามารถสอบถามตารางฟอนต์ของเอกสารหลังโหลดได้

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

ผลลัพธ์ควรแสดงฟอนต์สำรอง (เช่น *Arial*) แทนฟอนต์ที่หายไป นี่เป็นประโยชน์สำหรับ pipeline อัตโนมัติที่ต้องการรับประกันว่า PDF หรือ DOCX สุดท้ายตรงตามข้อกำหนดของแบรนด์

---

## เคล็ดลับระดับมืออาชีพ & จุดบกพร่องทั่วไป

- **เคล็ดลับระดับมืออาชีพ:** ตั้งค่า `loadOptions.setFontSettings(new FontSettings())` หากต้องการชี้ Aspose ไปยังโฟลเดอร์ฟอนต์แบบกำหนดเองก่อนโหลด วิธีนี้จะลดจำนวนการแทนที่ลง
- **ระวัง:** ลืมเรียก `setWarningCallback` โค้ดจะยังทำงานได้ แต่คุณจะพลาดข้อความวินิจฉัยสำคัญ
- **หมายเหตุเรื่องประสิทธิภาพ:** การโหลดเอกสารขนาดใหญ่ที่มีฟอนต์หายหลายตัวอาจสร้างคำเตือนจำนวนมาก พิจารณาจำกัดการแสดงผลหรือเขียนลงไฟล์ล็อกแทน `System.out`
- **ต้องการยกเลิกการโหลดเมื่อมีการแทนที่?** แทนที่การเรียก `System.out.println` ด้วย `throw new RuntimeException(info.getDescription())` ภายใน callback วิธีนี้จะบังคับให้การโหลดล้มเหลว ซึ่งเหมาะกับสถานการณ์ที่ต้องการความสอดคล้องอย่างเคร่งครัด

---

## คำถามที่พบบ่อย

**ถาม: วิธีนี้ทำงานกับ PDF หรือรูปภาพได้หรือไม่?**  
ตอบ: Callback คำเตือนจำกัดเฉพาะขั้นตอนการโหลดของรูปแบบการประมวลผล Word (`.docx`, `.doc`, `.rtf` เป็นต้น) การเรนเดอร์ PDF ใช้ pipeline ที่แตกต่างกัน แต่คุณยังสามารถจับคำเตือนที่เกี่ยวกับฟอนต์ได้ผ่าน `PdfLoadOptions`

**ถาม: สามารถแทนที่ฟอนต์เฉพาะด้วยฟอนต์ที่เลือกเองได้หรือไม่?**  
ตอบ: ได้ สร้างอ็อบเจกต์ `FontSettings` แล้วเรียก `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")` จากนั้นกำหนดให้กับ `loadOptions.setFontSettings(fontSettings)`

**ถาม: Callback นี้ปลอดภัยต่อการทำงานหลายเธรดหรือไม่?**  
ตอบ: การทำงานเริ่มต้นไม่ได้ทำให้ synchronized หากคุณโหลดเอกสารแบบขนาน ต้องแน่ใจว่าการทำงานของ callback ของคุณรองรับการเข้าถึงพร้อมกัน (เช่น ใช้ `ConcurrentLinkedQueue` สำหรับการบันทึก)

---

## สรุป

คุณได้เรียนรู้ **aspose font substitution tutorial** ครบถ้วนที่แสดงวิธี **จัดการฟอนต์ที่หายไป** อย่างราบรื่นใน Java โดยการกำหนด `IWarningCallback` แบบกำหนดเอง ผูกกับ `LoadOptions` แล้วบันทึกเอกสาร คุณจะทำให้ผลลัพธ์คงที่ไม่ว่าฟอนต์ใดติดตั้งบนเครื่องโฮสต์

ต่อไปคุณอาจสำรวจ:

- ตารางการแทนที่ฟอนต์แบบกำหนดเองสำหรับการสอดคล้องกับแบรนด์  
- การรวม logger ของคำเตือนกับ SLF4J หรือ Log4j เพื่อการวินิจฉัยระดับ production  
- การขยาย callback เพื่อเก็บสถิติทั่วทั้งชุดเอกสาร

ลองใช้งาน ปรับฟอนต์สำรอง แล้วให้เอกสารของคุณสวยงามแม้ฟอนต์ต้นฉบับจะหายไป ขอให้เขียนโค้ดสนุกนะ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}