---
title: การใส่ลายน้ำเอกสารและการตั้งค่าหน้า
linktitle: การใส่ลายน้ำเอกสารและการตั้งค่าหน้า
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีการใช้ลายน้ำและตั้งค่าคอนฟิกูเรชันหน้าด้วย Aspose.Words สำหรับ Java คู่มือฉบับสมบูรณ์พร้อมโค้ดต้นฉบับ
weight: 13
url: /th/java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การใส่ลายน้ำเอกสารและการตั้งค่าหน้า

## การแนะนำ

ในแวดวงการจัดการเอกสาร Aspose.Words สำหรับ Java ถือเป็นเครื่องมืออันทรงพลังที่ช่วยให้ผู้พัฒนาสามารถควบคุมทุกแง่มุมของการประมวลผลเอกสารได้ ในคู่มือฉบับสมบูรณ์นี้ เราจะเจาะลึกถึงความซับซ้อนของการใส่ลายน้ำในเอกสารและการตั้งค่าหน้าโดยใช้ Aspose.Words สำหรับ Java ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งก้าวเข้าสู่โลกแห่งการประมวลผลเอกสารด้วย Java คู่มือทีละขั้นตอนนี้จะช่วยให้คุณมีความรู้และโค้ดต้นฉบับที่คุณต้องการ

## การใส่ลายน้ำบนเอกสาร

### การเพิ่มลายน้ำ

การเพิ่มลายน้ำลงในเอกสารอาจมีความสำคัญต่อการสร้างแบรนด์หรือรักษาความปลอดภัยให้กับเนื้อหาของคุณ Aspose.Words สำหรับ Java ช่วยให้ภารกิจนี้ง่ายขึ้น ดังต่อไปนี้:

```java
// โหลดเอกสาร
Document doc = new Document("document.docx");

// สร้างลายน้ำ
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// วางตำแหน่งลายน้ำ
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// แทรกลายน้ำ
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// บันทึกเอกสาร
doc.save("document_with_watermark.docx");
```

### การปรับแต่งลายน้ำ

คุณสามารถปรับแต่งลายน้ำเพิ่มเติมได้โดยการปรับเปลี่ยนแบบอักษร ขนาด สี และการหมุน ความยืดหยุ่นนี้ช่วยให้ลายน้ำของคุณเข้ากับสไตล์เอกสารของคุณได้อย่างลงตัว

## การตั้งค่าหน้า

### ขนาดและทิศทางของหน้า

การตั้งค่าหน้ากระดาษเป็นสิ่งสำคัญในการจัดรูปแบบเอกสาร Aspose.Words สำหรับ Java ช่วยให้ควบคุมขนาดและทิศทางของหน้ากระดาษได้อย่างสมบูรณ์:

```java
// โหลดเอกสาร
Document doc = new Document("document.docx");

// ตั้งค่าขนาดหน้าเป็น A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// เปลี่ยนทิศทางหน้าเป็นแนวนอน
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// บันทึกเอกสารที่แก้ไข
doc.save("formatted_document.docx");
```

### ระยะขอบและการกำหนดหมายเลขหน้า

การควบคุมระยะขอบและหมายเลขหน้าอย่างแม่นยำถือเป็นสิ่งสำคัญสำหรับเอกสารระดับมืออาชีพ ทำได้ด้วย Aspose.Words สำหรับ Java:

```java
// โหลดเอกสาร
Document doc = new Document("document.docx");

// ตั้งค่าระยะขอบ
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// เปิดใช้งานการกำหนดหมายเลขหน้า
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// บันทึกเอกสารที่จัดรูปแบบแล้ว
doc.save("formatted_document.docx");
```

## คำถามที่พบบ่อย

### ฉันจะลบลายน้ำออกจากเอกสารได้อย่างไร

หากต้องการลบลายน้ำออกจากเอกสาร ให้คุณทำซ้ำตามรูปร่างของเอกสารและลบรูปร่างที่แสดงลายน้ำออก ต่อไปนี้คือตัวอย่างบางส่วน:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### ฉันสามารถเพิ่มลายน้ำหลาย ๆ อันลงในเอกสารเดียวได้หรือไม่

ใช่ คุณสามารถเพิ่มลายน้ำหลายรายการลงในเอกสารได้โดยการสร้างวัตถุรูปร่างเพิ่มเติมและจัดตำแหน่งตามต้องการ

### ฉันจะเปลี่ยนขนาดหน้าให้ถูกต้องตามแนวนอนได้อย่างไร

หากต้องการตั้งค่าขนาดหน้าให้ถูกต้องตามแนวนอน ให้แก้ไขความกว้างและความสูงของหน้าดังต่อไปนี้:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### แบบอักษรเริ่มต้นสำหรับลายน้ำคืออะไร?

แบบอักษรเริ่มต้นสำหรับลายน้ำคือ Calibri โดยมีขนาดแบบอักษร 36

### ฉันจะเพิ่มหมายเลขหน้าโดยเริ่มจากหน้าใดหน้าหนึ่งได้อย่างไร?

คุณสามารถทำได้โดยกำหนดหมายเลขหน้าเริ่มต้นในเอกสารของคุณดังนี้:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### ฉันจะจัดข้อความให้อยู่กึ่งกลางในส่วนหัวหรือส่วนท้ายได้อย่างไร?

คุณสามารถจัดข้อความให้อยู่กึ่งกลางในส่วนหัวหรือส่วนท้ายได้โดยใช้เมธอด setAlignment บนออบเจ็กต์ Paragraph ภายในส่วนหัวหรือส่วนท้าย

## บทสรุป

ในคู่มือที่ครอบคลุมนี้ เราได้สำรวจศิลปะของการใส่ลายน้ำในเอกสารและการตั้งค่าหน้าโดยใช้ Aspose.Words สำหรับ Java เมื่อคุณมีโค้ดตัวอย่างและข้อมูลเชิงลึกที่ให้มา ตอนนี้คุณก็มีเครื่องมือในการจัดการและจัดรูปแบบเอกสารของคุณอย่างประณีตแล้ว Aspose.Words สำหรับ Java ช่วยให้คุณสามารถสร้างเอกสารที่มีตราสินค้าอย่างมืออาชีพที่ปรับแต่งตามข้อกำหนดเฉพาะของคุณได้

การเรียนรู้การจัดการเอกสารถือเป็นทักษะอันมีค่าสำหรับนักพัฒนา และ Aspose.Words for Java คือเพื่อนคู่ใจของคุณในการเดินทางครั้งนี้ เริ่มสร้างเอกสารที่สวยงามได้แล้ววันนี้!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
