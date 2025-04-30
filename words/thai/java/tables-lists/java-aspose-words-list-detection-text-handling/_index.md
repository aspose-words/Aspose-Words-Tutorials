---
"date": "2025-03-28"
"description": "เรียนรู้วิธีการตรวจจับรายการ การจัดการข้อความ และอื่นๆ โดยใช้ Aspose.Words สำหรับ Java คู่มือนี้ครอบคลุมการตรวจจับรายการที่คั่นด้วยช่องว่าง การตัดช่องว่าง การกำหนดทิศทางเอกสาร การปิดใช้งานการตรวจจับการนับหมายเลขอัตโนมัติ และการจัดการไฮเปอร์ลิงก์"
"title": "การตรวจจับรายการหลักและการจัดการข้อความใน Java ด้วย Aspose.Words&#58; คู่มือฉบับสมบูรณ์"
"url": "/th/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# การตรวจจับรายการหลักและการจัดการข้อความใน Java ด้วย Aspose.Words: คู่มือฉบับสมบูรณ์

## การแนะนำ

การทำงานกับเอกสารแบบข้อความธรรมดา มักจะทำให้เกิดความท้าทายในการระบุข้อมูลที่มีโครงสร้าง เช่น รายการ เนื่องจากตัวแบ่งที่ไม่สอดคล้องกันและปัญหาการจัดรูปแบบ ไลบรารี Aspose.Words สำหรับ Java มีคุณสมบัติที่แข็งแกร่งเพื่อแก้ไขปัญหาเหล่านี้ รวมถึงการตรวจจับการนับเลขด้วยช่องว่าง การตัดช่องว่าง การกำหนดทิศทางของเอกสาร การปิดใช้งานการตรวจจับการนับเลขอัตโนมัติ และการจัดการไฮเปอร์ลิงก์ในเอกสารข้อความ บทช่วยสอนนี้ช่วยให้คุณสามารถจัดการข้อมูลข้อความได้อย่างมีประสิทธิภาพโดยใช้ Aspose.Words

**สิ่งที่คุณจะได้เรียนรู้:**
- เทคนิคในการตรวจจับรายการที่คั่นด้วยช่องว่าง
- วิธีการตัดช่องว่างที่ไม่ต้องการออกจากเนื้อหาเอกสาร
- แนวทางในการระบุทิศทางการอ่านไฟล์ข้อความ
- วิธีการปิดการตรวจจับการนับเลขอัตโนมัติ
- กลยุทธ์ในการตรวจจับและจัดการไฮเปอร์ลิงก์ในเอกสารข้อความธรรมดา

มาทบทวนข้อกำหนดเบื้องต้นที่จำเป็นก่อนใช้งานฟีเจอร์เหล่านี้กัน

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

### ห้องสมุดที่จำเป็น:
- **Aspose.คำศัพท์สำหรับภาษา Java**: เวอร์ชัน 25.3 ขึ้นไป.

### การตั้งค่าสภาพแวดล้อม:
- ตรวจสอบให้แน่ใจว่าสภาพแวดล้อมการพัฒนาของคุณรองรับ Maven หรือ Gradle เนื่องจากจำเป็นต้องจัดการการอ้างอิง

### ข้อกำหนดเบื้องต้นของความรู้:
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรมภาษา Java
- ความคุ้นเคยกับระบบสร้าง Maven หรือ Gradle

## การตั้งค่า Aspose.Words

หากต้องการเริ่มใช้ Aspose.Words สำหรับ Java ในโปรเจ็กต์ของคุณ คุณต้องรวมการอ้างอิงที่จำเป็นเข้าไปด้วย ดังต่อไปนี้:

**เมเวน:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**เกรเดิ้ล:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### การขอใบอนุญาต

หากต้องการใช้ Aspose.Words ได้อย่างเต็มประสิทธิภาพ ควรพิจารณาขอรับใบอนุญาต:
- **ทดลองใช้งานฟรี**: พร้อมสำหรับการทดสอบฟีเจอร์ต่างๆ
- **ใบอนุญาตชั่วคราว**: เพื่อวัตถุประสงค์ในการประเมินโดยไม่มีข้อจำกัด
- **ซื้อ**:ใบอนุญาตเต็มรูปแบบเพื่อใช้งานอย่างต่อเนื่อง

เมื่อคุณมีใบอนุญาตแล้ว ให้เริ่มต้นใบอนุญาตในแอปพลิเคชันของคุณเพื่อปลดล็อคฟังก์ชันการทำงานทั้งหมดของไลบรารี

## คู่มือการใช้งาน

มาแยกรายละเอียดฟีเจอร์แต่ละอย่างและดูวิธีใช้งานโดยใช้ Aspose.Words สำหรับ Java กัน

### ตรวจจับการนับด้วยช่องว่าง

**ภาพรวม:** คุณลักษณะนี้ช่วยให้คุณระบุรายการภายในเอกสารข้อความธรรมดาที่ใช้ช่องว่างเป็นตัวแบ่งเขตได้

#### ขั้นตอนที่ 1: โหลดเอกสาร
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // -
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### ขั้นตอนที่ 2: ตรวจสอบการตรวจจับรายการ
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*พารามิเตอร์และวิธีการ:*
- `setDetectNumberingWithWhitespaces(true)`: กำหนดค่าตัวแยกวิเคราะห์เพื่อจดจำรายการที่มีตัวคั่นช่องว่าง
- `doc.getLists().getCount()`: ดึงจำนวนรายการที่ตรวจพบในเอกสาร

### ตัดช่องว่างด้านหน้าและด้านหลัง

**ภาพรวม:** คุณสมบัตินี้จะตัดช่องว่างที่ไม่จำเป็นที่จุดเริ่มต้นหรือจุดสิ้นสุดบรรทัดในเอกสารข้อความธรรมดา ช่วยให้การจัดรูปแบบข้อความมีความสะอาด

#### ขั้นตอนที่ 1: กำหนดค่าตัวเลือกการโหลด
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // -
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### ขั้นตอนที่ 2: ตรวจสอบการตัดแต่ง
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*การกำหนดค่าที่สำคัญ:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: ตัดช่องว่างตั้งแต่จุดเริ่มต้นของบรรทัด
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: ลบช่องว่างที่ปลายบรรทัด

### ตรวจจับทิศทางเอกสาร

**ภาพรวม:** กำหนดว่าควรอ่านเอกสารจากขวาไปซ้าย (RTL) หรือไม่ เช่น ข้อความภาษาฮีบรูหรืออาหรับ

#### ขั้นตอนที่ 1: ตั้งค่าการตรวจจับอัตโนมัติ
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### ปิดใช้งานการตรวจจับการนับหมายเลขอัตโนมัติ

**ภาพรวม:** ป้องกันไม่ให้ไลบรารีตรวจจับและจัดรูปแบบรายการโดยอัตโนมัติ

#### ขั้นตอนที่ 1: กำหนดค่าตัวเลือกการโหลด
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### ตรวจจับไฮเปอร์ลิงก์ในข้อความ

**ภาพรวม:** ระบุและจัดการไฮเปอร์ลิงก์ภายในเอกสารข้อความธรรมดา

#### ขั้นตอนที่ 1: ตั้งค่าตัวเลือกการตรวจจับ
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // -
    "https://เอกสาร.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## การประยุกต์ใช้งานจริง

1. **ระบบจัดการเนื้อหา (CMS):** จัดรูปแบบเนื้อหาที่ผู้ใช้สร้างขึ้นให้เป็นรายการที่มีโครงสร้างโดยอัตโนมัติ
2. **เครื่องมือสกัดข้อมูล:** ใช้การตรวจจับรายการเพื่อจัดระเบียบข้อมูลที่ไม่มีโครงสร้างสำหรับการวิเคราะห์
3. **ท่อประมวลผลข้อความ:** ปรับปรุงการประมวลผลเอกสารเบื้องต้นด้วยการตัดช่องว่างและตรวจจับทิศทางของข้อความ

## การพิจารณาประสิทธิภาพ

เพื่อเพิ่มประสิทธิภาพการทำงาน:
- โหลดเอกสารด้วยการดำเนินการขั้นต่ำ โดยเน้นที่คุณสมบัติที่จำเป็น
- จัดการการใช้หน่วยความจำด้วยการประมวลผลเอกสารขนาดใหญ่เป็นส่วนๆ หากเป็นไปได้

## บทสรุป

การใช้ Aspose.Words สำหรับ Java ช่วยให้คุณจัดการข้อมูลข้อความในเอกสารข้อความธรรมดาได้อย่างมีประสิทธิภาพ ตั้งแต่การตรวจจับรายการที่คั่นด้วยช่องว่างไปจนถึงการจัดการทิศทางข้อความและไฮเปอร์ลิงก์ เครื่องมืออันทรงพลังเหล่านี้ช่วยให้จัดการเอกสารได้อย่างมีประสิทธิภาพ หากต้องการข้อมูลเพิ่มเติม โปรดดูที่ [เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/java/) หรือลองใช้งานแบบทดลองใช้ฟรี


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}