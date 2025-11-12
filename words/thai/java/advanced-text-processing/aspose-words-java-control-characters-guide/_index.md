---
date: '2025-11-12'
description: เรียนรู้วิธีแทรกอักขระควบคุม จัดการการขึ้นบรรทัดใหม่ และเพิ่มการแบ่งหน้า
  หรือคอลัมน์ใน Java ด้วย Aspose.Words เพื่อการจัดรูปแบบเอกสารที่แม่นยำ
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: th
title: แทรกอักขระควบคุมใน Java ด้วย Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกอักขระควบคุมใน Java ด้วย Aspose.Words
## บทนำ
คุณต้องการควบคุมการขึ้นบรรทัด, แท็บ หรือการแบ่งหน้าอย่างแม่นยำพิกเซลเมื่อสร้างใบแจ้งหนี้, รายงาน หรือจดหมายข่าวหรือไม่?  
อักขระควบคุมเป็นบล็อกที่มองไม่เห็นซึ่งทำให้คุณสามารถกำหนดรูปแบบเอกสารได้โดยโปรแกรม  
ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **แทรก**, **ตรวจสอบ**, และ **จัดการ** อักขระควบคุม เช่น การขึ้นบรรทัด, ช่องว่างที่ไม่แยกบรรทัด, และการแบ่งคอลัมน์ ด้วย Aspose.Words for Java API

**สิ่งที่คุณจะทำได้:**
1. แทรกและตรวจสอบการขึ้นบรรทัด, การขึ้นบรรทัดใหม่, และการแบ่งหน้า  
2. เพิ่มช่องว่าง, แท็บ, ช่องว่างที่ไม่แยกบรรทัด, และการแบ่งคอลัมน์เพื่อสร้างเลย์เอาต์หลายคอลัมน์  
3. ปรับใช้เคล็ดลับการทำงานที่ดีที่สุดสำหรับการอัตโนมัติเอกสารขนาดใหญ่

## ข้อกำหนดเบื้องต้น
ก่อนเริ่ม, ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้พร้อมใช้งาน:

| ข้อกำหนด | รายละเอียด |
|-------------|----------|
| **Aspose.Words for Java** | เวอร์ชัน 25.3 หรือใหม่กว่า (API มีความเสถียรในรุ่นต่อ ๆ ไป) |
| **JDK** | Java 8 + (แนะนำ Java 11 หรือ 17) |
| **IDE** | IntelliJ IDEA, Eclipse หรือเครื่องมือแก้ไข Java ใด ๆ |
| **เครื่องมือสร้าง** | Maven **หรือ** Gradle สำหรับจัดการ dependency |
| **License** | ไฟล์ลิขสิทธิ์ Aspose.Words ชั่วคราวหรือที่ซื้อแล้ว |

### เช็คลิสต์สภาพแวดล้อมอย่างรวดเร็ว
1. ติดตั้ง Maven **หรือ** Gradle แล้ว  
2. ไฟล์ลิขสิทธิ์เข้าถึงได้ (เช่น `src/main/resources/aspose.words.lic`)  
3. โครงการคอมไพล์โดยไม่มีข้อผิดพลาด

## การตั้งค่า Aspose.Words
เราจะเพิ่มไลบรารีลงในโครงการก่อน แล้วโหลดลิขสิทธิ์ เลือกระบบสร้างที่ตรงกับ workflow ของคุณ

### Maven Dependency
เพิ่มโค้ดต่อไปนี้ในไฟล์ `pom.xml` ภายใน `<dependencies>`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle Dependency
ใส่บรรทัดนี้ในบล็อก `dependencies` ของ `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Initialization (Java code)
```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **หมายเหตุ:** แทนที่ `"path/to/aspose.words.lic"` ด้วยพาธจริงของไฟล์ลิขสิทธิ์ของคุณ

## ฟีเจอร์ 1: จัดการ Carriage Returns และ Page Breaks
Carriage returns (`ControlChar.CR`) และ page breaks (`ControlChar.PAGE_BREAK`) มีความสำคัญเมื่อคุณต้องการให้ข้อความผลลัพธ์สะท้อนการจัดวางที่มองเห็นได้ของเอกสาร

### การทำงานตามขั้นตอน
1. **สร้าง Document และ DocumentBuilder ใหม่**  
2. **เขียนสองย่อหน้า**  
3. **ตรวจสอบว่าข้อความที่สร้างมีอักขระควบคุมที่คาดหวัง**  
4. **ตัดข้อความและตรวจสอบผลอีกครั้ง**

#### 1. สร้าง Document
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. แทรกย่อหน้า
```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. ตรวจสอบอักขระควบคุม
```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. ตัดและตรวจสอบข้อความ
```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**ผลลัพธ์:** สตริง `doc.getText()` ตอนนี้มีสัญลักษณ์ CR และ page‑break อย่างชัดเจน ทำให้ระบบ downstream (เช่น ตัวส่งออก plain‑text) รักษาเลย์เอาต์ได้

## ฟีเจอร์ 2: แทรกอักขระควบคุมหลายประเภท
นอกเหนือจาก carriage returns, Aspose.Words มีค่าสถิตสำหรับช่องว่าง, แท็บ, line feeds, paragraph breaks, และ column breaks ส่วนนี้จะแสดงวิธีฝังแต่ละอักขระ

### การทำงานตามขั้นตอน
1. **เริ่มต้น DocumentBuilder ใหม่**  
2. **เขียนตัวอย่างสำหรับอักขระช่องว่าง, non‑breaking space, และแท็บ**  
3. **เพิ่ม line feeds, paragraph breaks, และ section breaks แล้วตรวจสอบจำนวนโหนด**  
4. **สร้างเลย์เอาต์สองคอลัมน์และแทรก column break**

#### 1. เริ่มต้น DocumentBuilder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. แทรกอักขระที่เกี่ยวกับช่องว่าง
- **Space (`ControlChar.SPACE_CHAR`)**
```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```
- **Non‑Breaking Space (`ControlChar.NON_BREAKING_SPACE`)**
```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```
- **Tab (`ControlChar.TAB`)**
```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. Line, Paragraph, และ Section Breaks
```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. Column Break ในเลย์เอาต์หลายคอลัมน์
```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**ผลลัพธ์:** ตอนนี้เอกสารมีหน้าสองคอลัมน์ที่ข้อความไหลอัตโนมัติจากคอลัมน์แรกไปยังคอลัมน์ที่สองหลังจาก `COLUMN_BREAK`

## การประยุกต์ใช้งานจริง
| สถานการณ์ | วิธีที่อักขระควบคุมช่วยได้ |
|----------|-----------------------------|
| **การสร้างใบแจ้งหนี้** | ใช้ `PAGE_BREAK` เพื่อเริ่มหน้าใหม่สำหรับแต่ละชุดใบแจ้งหนี้ |
| **รายงานการเงิน** | จัดแนวตัวเลขด้วย `TAB` และคงหัวเรื่องไว้ด้วย `NON_BREAKING_SPACE` |
| **เลย์เอาต์จดหมายข่าว** | สร้างบทความข้างเคียงด้วย `COLUMN_BREAK` ในส่วนหลายคอลัมน์ |
| **การส่งออกเนื้อหา CMS** | รักษาโครงสร้างบรรทัดเมื่อแปลง rich text เป็น plain text ผ่าน `LINE_FEED` |
| **เทมเพลตอัตโนมัติ** | แทรก `PARAGRAPH_BREAK` หรือ `SECTION_BREAK` อย่างไดนามิกตามข้อมูลผู้ใช้ |

## ข้อควรพิจารณาด้านประสิทธิภาพ
* **Batch Inserts:** รวมหลายคำสั่ง `write` เป็นการทำงานเดียวเพื่อลดการรีเฟรชภายใน |
* **หลีกเลี่ยงการ Traversal โหนดบ่อย:** แคชผลลัพธ์ `NodeCollection` เมื่อจำเป็นต้องนับย่อหน้าซ้ำหลายครั้ง |
* **Profile เอกสารขนาดใหญ่:** ใช้โปรไฟเลอร์ Java (เช่น VisualVM) เพื่อตรวจหาจุดคอในลูปการจัดการข้อความ |

## สรุป
คุณได้เรียนรู้วิธี **แทรก**, **ตรวจสอบ**, และ **ปรับประสิทธิภาพ** อักขระควบคุมในเอกสาร Java ด้วย Aspose.Words อย่างเป็นขั้นตอน เทคนิคเหล่านี้จะช่วยให้คุณสร้างใบแจ้งหนี้, รายงาน, และสิ่งพิมพ์หลายคอลัมน์ระดับมืออาชีพโดยอัตโนมัติ

## ขั้นตอนต่อไป
1. ทดลองใช้ค่าสถิต `ControlChar` เพิ่มเติม เช่น `EM_SPACE` หรือ `EN_SPACE`  
2. ผสานอักขระควบคุมกับฟิลด์ mail‑merge เพื่อสร้างเอกสารแบบไดนามิก  
3. สำรวจฟีเจอร์ Aspose.Words เช่น **การป้องกันเอกสาร**, **ลายน้ำ**, และ **การแทรกรูปภาพ** เพื่อเพิ่มความหลากหลายให้ผลลัพธ์ของคุณ

**ลองทำเลยวันนี้:** เพิ่มโค้ดตัวอย่างข้างต้นในโครงการ Java ถัดไปของคุณ แล้วดูว่าอักขระควบคุมที่แม่นยำสามารถทำให้กระบวนการทำงานกับเอกสารของคุณเป็นเรื่องง่ายขึ้นได้อย่างไร!

## คำถามที่พบบ่อย
1. **อักขระควบคุมคืออะไร?**  
   สัญลักษณ์ที่ไม่แสดงผล (เช่น แท็บ, line feed) ที่มีผลต่อการจัดวางเอกสารโดยไม่ปรากฏเป็นข้อความที่มองเห็นได้

2. **ฉันจะเริ่มใช้ Aspose.Words for Java ได้อย่างไร?**  
   เพิ่ม dependency ของ Maven หรือ Gradle, โหลดลิขสิทธิ์ของคุณ, แล้วทำตามตัวอย่างโค้ดในคู่มือนี้

3. **ฉันสามารถใช้ column breaks สำหรับจดหมายข่าวได้หรือไม่?**  
   ได้ — `ControlChar.COLUMN_BREAK` ทำงานร่วมกับคุณสมบัติ `TextColumns` เพื่อแบ่งเนื้อหาเป็นคอลัมน์หลายคอลัมน์

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}