---
"description": "เรียนรู้การใช้เชิงอรรถและเชิงท้ายอย่างมีประสิทธิภาพใน Aspose.Words สำหรับ Java พัฒนาทักษะการจัดรูปแบบเอกสารของคุณวันนี้!"
"linktitle": "การใช้เชิงอรรถและเชิงอรรถท้ายเรื่อง"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้เชิงอรรถและเชิงอรรถใน Aspose.Words สำหรับ Java"
"url": "/th/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้เชิงอรรถและเชิงอรรถใน Aspose.Words สำหรับ Java


ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการใช้เชิงอรรถและเชิงท้ายใน Aspose.Words สำหรับ Java เชิงอรรถและเชิงท้ายเป็นองค์ประกอบสำคัญในการจัดรูปแบบเอกสาร มักใช้สำหรับการอ้างอิง เอกสารอ้างอิง และข้อมูลเพิ่มเติม Aspose.Words สำหรับ Java มอบฟังก์ชันการทำงานที่แข็งแกร่งเพื่อทำงานกับเชิงอรรถและเชิงท้ายได้อย่างราบรื่น

## 1. บทนำเกี่ยวกับเชิงอรรถและเชิงอรรถท้ายเรื่อง

เชิงอรรถและเชิงท้ายคือคำอธิบายประกอบที่ให้ข้อมูลเพิ่มเติมหรือการอ้างอิงภายในเอกสาร เชิงอรรถจะปรากฏที่ด้านล่างของหน้า ในขณะที่เชิงอรรถจะถูกรวบรวมไว้ที่ท้ายส่วนหรือท้ายเอกสาร เชิงอรรถมักใช้ในเอกสารวิชาการ รายงาน และเอกสารทางกฎหมายเพื่ออ้างอิงแหล่งที่มาหรือชี้แจงเนื้อหา

## 2. การตั้งค่าสภาพแวดล้อมของคุณ

ก่อนที่เราจะลงมือดำเนินการกับเชิงอรรถและเชิงอรรถท้ายบท คุณต้องตั้งค่าสภาพแวดล้อมการพัฒนาของคุณก่อน ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและกำหนดค่า Aspose.Words for Java API ในโปรเจ็กต์ของคุณแล้ว

## 3. การเพิ่มเชิงอรรถลงในเอกสารของคุณ

หากต้องการเพิ่มเชิงอรรถในเอกสารของคุณ ให้ทำตามขั้นตอนเหล่านี้:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // ระบุจำนวนคอลัมน์ที่จะใช้ในการจัดรูปแบบพื้นที่เชิงอรรถ
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. การแก้ไขตัวเลือกเชิงอรรถ

คุณสามารถปรับเปลี่ยนตัวเลือกเชิงอรรถเพื่อปรับแต่งลักษณะและพฤติกรรมของเชิงอรรถได้ ดังนี้:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. การเพิ่มเชิงอรรถในเอกสารของคุณ

การเพิ่มหมายเหตุท้ายเล่มลงในเอกสารของคุณนั้นทำได้ง่าย ๆ ดังต่อไปนี้:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. การปรับแต่งการตั้งค่า Endnote

คุณสามารถปรับแต่งการตั้งค่าเชิงอรรถเพิ่มเติมเพื่อให้ตรงตามข้อกำหนดของเอกสารของคุณได้

## ซอร์สโค้ดที่สมบูรณ์
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // ระบุจำนวนคอลัมน์ที่จะใช้ในการจัดรูปแบบพื้นที่เชิงอรรถ
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. บทสรุป

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีการทำงานกับเชิงอรรถและเชิงท้ายใน Aspose.Words สำหรับ Java คุณสมบัติเหล่านี้มีประโยชน์อย่างยิ่งในการสร้างเอกสารที่มีโครงสร้างดีพร้อมการอ้างอิงและการอ้างอิงที่เหมาะสม

ตอนนี้คุณได้เรียนรู้วิธีใช้เชิงอรรถและเชิงอรรถตอนท้ายแล้ว คุณสามารถปรับปรุงการจัดรูปแบบเอกสารของคุณและทำให้เนื้อหาของคุณดูเป็นมืออาชีพมากขึ้นได้

### คำถามที่พบบ่อย

### 1. ความแตกต่างระหว่างเชิงอรรถและเชิงอรรถท้ายเรื่องคืออะไร?
เชิงอรรถจะปรากฏที่ด้านล่างของหน้า ในขณะที่เชิงอรรถตอนท้ายจะถูกเก็บรวบรวมไว้ที่ตอนท้ายของส่วนหรือเอกสาร

### 2. ฉันจะเปลี่ยนตำแหน่งของเชิงอรรถหรือเชิงอรรถตอนท้ายได้อย่างไร
คุณสามารถใช้ `setPosition` วิธีการเปลี่ยนตำแหน่งของเชิงอรรถหรือเชิงท้าย

### 3. ฉันสามารถปรับแต่งการจัดรูปแบบของเชิงอรรถและเชิงอรรถตอนท้ายได้หรือไม่
ใช่ คุณสามารถปรับแต่งการจัดรูปแบบของเชิงอรรถและเชิงอรรถตอนท้ายโดยใช้ Aspose.Words สำหรับ Java ได้

### 4. เชิงอรรถและเชิงท้ายมีความสำคัญในการจัดรูปแบบเอกสารหรือไม่
ใช่ เชิงอรรถและเชิงอรรถตอนท้ายมีความจำเป็นสำหรับการให้ข้อมูลอ้างอิงและข้อมูลเพิ่มเติมในเอกสาร

อย่าลังเลที่จะสำรวจฟีเจอร์เพิ่มเติมของ Aspose.Words สำหรับ Java และปรับปรุงความสามารถในการสร้างเอกสารของคุณ ขอให้สนุกกับการเขียนโค้ด!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}