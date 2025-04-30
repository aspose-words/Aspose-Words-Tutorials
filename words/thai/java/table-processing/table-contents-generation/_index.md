---
"description": "เรียนรู้วิธีสร้างสารบัญแบบไดนามิกโดยใช้ Aspose.Words สำหรับ Java เรียนรู้การสร้างสารบัญด้วยคำแนะนำทีละขั้นตอนและตัวอย่างโค้ดต้นฉบับ"
"linktitle": "สารบัญ รุ่น"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "สารบัญ รุ่น"
"url": "/th/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สารบัญ รุ่น

## การแนะนำ

เคยประสบปัญหาในการสร้างสารบัญ (TOC) ที่ดูเป็นมืออาชีพและไดนามิกในเอกสาร Word ของคุณหรือไม่? ไม่ต้องมองหาที่อื่นอีกแล้ว! ด้วย Aspose.Words สำหรับ Java คุณสามารถทำให้กระบวนการทั้งหมดเป็นแบบอัตโนมัติ ช่วยประหยัดเวลาและมั่นใจได้ถึงความถูกต้อง ไม่ว่าคุณจะกำลังสร้างรายงานที่ครอบคลุมหรือเอกสารวิชาการ บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการสร้างสารบัญด้วยโปรแกรม Java พร้อมเริ่มใช้งานหรือยัง? มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. Java Development Kit (JDK): ติดตั้งบนระบบของคุณ คุณสามารถดาวน์โหลดได้จาก [เว็บไซต์ของออราเคิล](https://www-oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words สำหรับ Java Library: ดาวน์โหลดเวอร์ชันล่าสุดจาก [หน้าวางจำหน่าย](https://releases-aspose.com/words/java/).
3. สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE): เช่น IntelliJ IDEA, Eclipse หรือ NetBeans
4. ใบอนุญาตชั่วคราว Aspose: เพื่อหลีกเลี่ยงข้อจำกัดในการประเมิน ให้รับ [ใบอนุญาตชั่วคราว](https://purchase-aspose.com/temporary-license/).

## แพ็คเกจนำเข้า

หากต้องการใช้ Aspose.Words สำหรับ Java ได้อย่างมีประสิทธิภาพ โปรดตรวจสอบให้แน่ใจว่าคุณได้นำเข้าคลาสที่จำเป็น ต่อไปนี้คือคลาสที่นำเข้า:

```java
import com.aspose.words.*;
```

ปฏิบัติตามขั้นตอนต่อไปนี้เพื่อสร้าง TOC แบบไดนามิกในเอกสาร Word ของคุณ

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

ขั้นตอนแรกคือการสร้างเอกสารใหม่และใช้ `DocumentBuilder` คลาสที่จะจัดการมัน


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: หมายถึงเอกสาร Word
- `DocumentBuilder`:คลาสตัวช่วยที่ช่วยให้จัดการเอกสารได้อย่างง่ายดาย

## ขั้นตอนที่ 2: แทรกสารบัญ

ต่อไปเรามาแทรก TOC ไว้ที่จุดเริ่มต้นของเอกสารกันดีกว่า


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: แทรกฟิลด์ TOC พารามิเตอร์ระบุ:
  - `\o "1-3"`: รวมถึงหัวข้อระดับ 1 ถึง 3
  - `\h`: สร้างรายการแบบไฮเปอร์ลิงก์
  - `\z`: ระงับหมายเลขหน้าสำหรับเอกสารเว็บ
  - `\u`:รักษาสไตล์สำหรับไฮเปอร์ลิงก์
- `insertBreak`: เพิ่มตัวแบ่งหน้าหลัง TOC

## ขั้นตอนที่ 3: เพิ่มหัวข้อเพื่อเติมลงใน TOC

หากต้องการเพิ่มเนื้อหาใน TOC คุณต้องเพิ่มย่อหน้าที่มีรูปแบบหัวเรื่อง


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: กำหนดรูปแบบย่อหน้าเป็นระดับหัวเรื่องที่เฉพาะเจาะจง (เช่น `HEADING_1`- `HEADING_2`-
- `writeln`เพิ่มข้อความลงในเอกสารตามรูปแบบที่ระบุ

## ขั้นตอนที่ 4: เพิ่มหัวข้อที่ซ้อนกัน

เพื่อแสดงระดับ TOC ให้รวมหัวเรื่องที่ซ้อนกัน


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- เพิ่มหัวเรื่องระดับที่ลึกกว่าเพื่อแสดงลำดับชั้นใน TOC

## ขั้นตอนที่ 5: อัปเดตฟิลด์ TOC

ต้องอัปเดตฟิลด์ TOC เพื่อแสดงหัวเรื่องล่าสุด


```java
doc.updateFields();
```

- `updateFields`:รีเฟรชฟิลด์ทั้งหมดในเอกสารเพื่อให้แน่ใจว่า TOC สะท้อนถึงหัวเรื่องที่เพิ่มเข้ามา

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารในรูปแบบที่คุณต้องการ


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: ส่งออกเอกสารไปยัง `.docx` ไฟล์ คุณสามารถระบุรูปแบบอื่น ๆ เช่น `.pdf` หรือ `.txt` หากจำเป็น

## บทสรุป

ขอแสดงความยินดี! คุณได้สร้างสารบัญแบบไดนามิกในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ Java ด้วยโค้ดเพียงไม่กี่บรรทัด คุณก็สามารถทำภารกิจที่ปกติแล้วอาจต้องใช้เวลาเป็นชั่วโมงให้กลายเป็นระบบอัตโนมัติได้ แล้วขั้นตอนต่อไปล่ะ ลองทดลองใช้รูปแบบและสไตล์หัวเรื่องต่างๆ เพื่อปรับแต่งสารบัญให้เหมาะกับความต้องการเฉพาะของคุณ

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งรูปแบบ TOC เพิ่มเติมได้หรือไม่
แน่นอน! คุณสามารถปรับพารามิเตอร์ TOC ได้ เช่น การรวมหมายเลขหน้า การจัดตำแหน่งข้อความ หรือการใช้รูปแบบหัวเรื่องแบบกำหนดเอง

### จำเป็นต้องมีใบอนุญาตสำหรับ Aspose.Words สำหรับ Java หรือไม่
ใช่ ต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ คุณสามารถเริ่มต้นด้วย [ใบอนุญาตชั่วคราว](https://purchase-aspose.com/temporary-license/).

### ฉันสามารถสร้าง TOC สำหรับเอกสารที่มีอยู่ได้หรือไม่
ใช่! โหลดเอกสารลงใน `Document` วัตถุและทำตามขั้นตอนเดียวกันเพื่อแทรกและอัพเดต TOC

### วิธีนี้ใช้ได้กับการส่งออก PDF ไหม
ใช่ TOC จะปรากฏใน PDF หากคุณบันทึกเอกสารใน `.pdf` รูปแบบ

### ฉันสามารถหาเอกสารเพิ่มเติมได้ที่ไหน
ตรวจสอบออก [Aspose.Words สำหรับเอกสาร Java](https://reference.aspose.com/words/java/) สำหรับตัวอย่างและรายละเอียดเพิ่มเติม


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}