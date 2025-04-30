---
"description": "เรียนรู้การใช้ OLE objects และ ActiveX controls ใน Aspose.Words สำหรับ Java สร้างเอกสารแบบโต้ตอบได้อย่างง่ายดาย เริ่มต้นเลยตอนนี้!"
"linktitle": "การใช้ OLE Objects และ ActiveX Controls"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้ OLE Objects และ ActiveX Controls ใน Aspose.Words สำหรับ Java"
"url": "/th/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ OLE Objects และ ActiveX Controls ใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีการทำงานกับอ็อบเจ็กต์ OLE (Object Linking and Embedding) และตัวควบคุม ActiveX ใน Aspose.Words สำหรับ Java อ็อบเจ็กต์ OLE และตัวควบคุม ActiveX เป็นเครื่องมืออันทรงพลังที่ช่วยให้คุณปรับปรุงเอกสารของคุณโดยการฝังหรือลิงก์เนื้อหาภายนอก เช่น สเปรดชีต ไฟล์มัลติมีเดีย หรือตัวควบคุมแบบโต้ตอบ ติดตามขณะที่เราเจาะลึกตัวอย่างโค้ดและเรียนรู้วิธีใช้คุณลักษณะเหล่านี้อย่างมีประสิทธิภาพ

### ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. Aspose.Words สำหรับ Java: ตรวจสอบว่าคุณได้ติดตั้งไลบรารี Aspose.Words ไว้ในโปรเจ็กต์ Java ของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/java/).

2. สภาพแวดล้อมการพัฒนา Java: คุณควรมีการตั้งค่าสภาพแวดล้อมการพัฒนา Java ที่ใช้งานได้บนระบบของคุณ

### การแทรกวัตถุ OLE

เริ่มต้นด้วยการแทรกวัตถุ OLE ลงในเอกสาร Word เราจะสร้างเอกสาร Word ง่ายๆ จากนั้นแทรกวัตถุ OLE ที่แสดงถึงหน้าเว็บ

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", true, true, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

ในโค้ดนี้ เราสร้างเอกสารใหม่และแทรกวัตถุ OLE เพื่อแสดงเว็บไซต์ Aspose คุณสามารถแทนที่ URL ด้วยเนื้อหาที่ต้องการได้

### การแทรกวัตถุ OLE ด้วย OlePackage

ต่อไป เราจะมาดูวิธีการแทรกวัตถุ OLE โดยใช้ OlePackage กัน ซึ่งจะช่วยให้คุณฝังไฟล์ภายนอกเป็นวัตถุ OLE ในเอกสารของคุณได้

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

ในตัวอย่างนี้ เราจะแทรกวัตถุ OLE โดยใช้ OlePackage ซึ่งทำให้คุณสามารถรวมไฟล์ภายนอกเป็นวัตถุที่ฝังไว้ได้

### การแทรกวัตถุ OLE เป็นไอคอน

ตอนนี้มาดูวิธีการแทรกวัตถุ OLE เป็นไอคอนกัน ซึ่งมีประโยชน์เมื่อคุณต้องการแสดงไอคอนที่แสดงถึงไฟล์ที่ฝังไว้

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

ในโค้ดนี้ เราแทรกวัตถุ OLE เป็นไอคอน เพื่อให้การนำเสนอเนื้อหาที่ฝังไว้ดูน่าสนใจยิ่งขึ้น

### การอ่านคุณสมบัติของตัวควบคุม ActiveX

ตอนนี้เรามาเน้นที่ตัวควบคุม ActiveX กันดีกว่า เราจะเรียนรู้วิธีอ่านคุณสมบัติของตัวควบคุม ActiveX ภายในเอกสาร Word

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

ในโค้ดนี้ เราจะวนซ้ำผ่านรูปร่างในเอกสาร Word ระบุตัวควบคุม ActiveX และดึงคุณสมบัติของตัวควบคุมดังกล่าว

### บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการทำงานกับอ็อบเจ็กต์ OLE และตัวควบคุม ActiveX ใน Aspose.Words สำหรับ Java แล้ว คุณสมบัติเหล่านี้เปิดโลกแห่งความเป็นไปได้สำหรับการสร้างเอกสารแบบไดนามิกและโต้ตอบได้

### คำถามที่พบบ่อย

### วัตถุประสงค์ของวัตถุ OLE ในเอกสาร Word คืออะไร 
   - อ็อบเจ็กต์ OLE ช่วยให้คุณฝังหรือลิงก์เนื้อหาภายนอก เช่น ไฟล์หรือหน้าเว็บภายในเอกสาร Word ได้

### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของวัตถุ OLE ในเอกสารของฉันได้หรือไม่ 
   - ใช่ คุณสามารถปรับแต่งลักษณะที่ปรากฏของวัตถุ OLE ได้ รวมถึงการตั้งค่าไอคอนและชื่อไฟล์

### ตัวควบคุม ActiveX คืออะไร และสามารถปรับปรุงเอกสารของฉันได้อย่างไร 
   - ตัวควบคุม ActiveX เป็นองค์ประกอบแบบโต้ตอบที่สามารถเพิ่มฟังก์ชันการทำงานให้กับเอกสาร Word ของคุณ เช่น ตัวควบคุมฟอร์มหรือเครื่องเล่นมัลติมีเดีย

### Aspose.Words สำหรับ Java เหมาะกับการทำงานอัตโนมัติของเอกสารในระดับองค์กรหรือไม่ 
   - ใช่ Aspose.Words สำหรับ Java เป็นไลบรารีอันทรงพลังสำหรับการสร้างและจัดการเอกสารแบบอัตโนมัติในแอปพลิเคชัน Java

### ฉันสามารถเข้าถึง Aspose.Words สำหรับ Java ได้จากที่ใด 
   - คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้จาก [ที่นี่](https://releases-aspose.com/words/java/).

เริ่มต้นใช้งาน Aspose.Words สำหรับ Java วันนี้และปลดล็อกศักยภาพเต็มรูปแบบของการทำงานอัตโนมัติและการปรับแต่งเอกสาร!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}