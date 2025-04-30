---
"description": "เรียนรู้การใช้ Aspose.Words สำหรับฟิลด์ Java อย่างมีประสิทธิภาพด้วยบทช่วยสอนแบบทีละขั้นตอนนี้ สร้างเอกสาร Word แบบไดนามิกได้อย่างง่ายดาย"
"linktitle": "การใช้ฟิลด์"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้ฟิลด์ใน Aspose.Words สำหรับ Java"
"url": "/th/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ฟิลด์ใน Aspose.Words สำหรับ Java


ในบทช่วยสอนทีละขั้นตอนนี้ เราจะแนะนำคุณเกี่ยวกับวิธีใช้ฟิลด์ใน Aspose.Words สำหรับ Java เพื่อจัดการเอกสารได้อย่างง่ายดาย Aspose.Words สำหรับ Java เป็น API ที่มีประสิทธิภาพที่ช่วยให้คุณทำงานกับเอกสาร Word ได้ด้วยการเขียนโปรแกรม ทำให้คุณควบคุมเนื้อหาและการจัดรูปแบบได้อย่างเต็มที่

## 1. บทนำ

Aspose.Words สำหรับ Java เป็นเครื่องมือสำคัญสำหรับทุกคนที่ต้องจัดการกับเอกสาร Word ในแอปพลิเคชัน Java ฟิลด์คือตัวแทนที่สามารถจัดเก็บข้อมูลแบบไดนามิกในเอกสารของคุณได้ บทช่วยสอนนี้จะแสดงให้คุณเห็นถึงวิธีการทำงานกับฟิลด์อย่างมีประสิทธิภาพ

## 2. การตั้งค่าสภาพแวดล้อมของคุณ

ก่อนเริ่มต้น โปรดแน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ Java แล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases.aspose.com/words/java/)นอกจากนี้ ควรแน่ใจว่าคุณมี Java และสภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น Eclipse หรือ IntelliJ IDEA ติดตั้งอยู่บนระบบของคุณ

## 3. การโหลดเอกสาร Word

ในแอปพลิเคชัน Java ของคุณ คุณต้องโหลดเอกสาร Word ที่คุณต้องการใช้งาน นี่คือตัวอย่างโค้ดเพื่อช่วยคุณเริ่มต้น:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

แทนที่ `"Your Document Directory"` และ `"Your Output Directory"` ด้วยเส้นทางที่เหมาะสม

## 4. การปรับแต่งจดหมายเวียน

Aspose.Words สำหรับ Java ให้การสนับสนุนที่ยอดเยี่ยมสำหรับการดำเนินการผสานจดหมาย คุณสามารถปรับแต่งกระบวนการผสานจดหมายได้โดยการตั้งค่าตัวจัดการเหตุการณ์การผสานจดหมาย ดังต่อไปนี้คือวิธีการดำเนินการ:

```java
// ตั้งค่าตัวจัดการเหตุการณ์การผสานจดหมายเพื่อทำงานแบบกำหนดเอง
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// ตัดค่าการผสานจดหมายช่องว่างด้านท้ายและด้านนำ
doc.getMailMerge().setTrimWhitespaces(false);

String[] fieldNames = {
    "RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
    "Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};

Object[] fieldValues = {
    "Josh", "Jenny", "123456789", "", "Hello",
    "<b>HTML Body Test message 1</b>", true, false, true
};

doc.getMailMerge().execute(fieldNames, fieldValues);
```

## 5. การบันทึกเอกสาร

หลังจากปรับแต่งเอกสารของคุณแล้ว คุณสามารถบันทึกได้โดยใช้รหัสต่อไปนี้:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

แทนที่ `"Your Output Directory"` ด้วยเส้นทางเอาท์พุตตามที่ต้องการ

## ซอร์สโค้ดที่สมบูรณ์
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// ตั้งค่าตัวจัดการเหตุการณ์การผสานจดหมายเพื่อทำงานแบบกำหนดเอง
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// ตัดค่าการผสานจดหมายช่องว่างด้านท้ายและด้านนำ
doc.getMailMerge().setTrimWhitespaces(false);
String[] fieldNames = {
	"RecipientName", "SenderName", "FaxNumber", "PhoneNumber",
	"Subject", "Body", "Urgent", "ForReview", "PleaseComment"
};
Object[] fieldValues = {
	"Josh", "Jenny", "123456789", "", "Hello",
	"<b>HTML Body Test message 1</b>", true, false, true
};
doc.getMailMerge().execute(fieldNames, fieldValues);
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```
ซอร์สโค้ดของคลาส HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <สรุป>
        //ตัวจัดการนี้จะถูกเรียกใช้สำหรับฟิลด์จดหมายเวียนทุกฟิลด์ที่พบในเอกสาร
        /// สำหรับทุกรายการที่พบในแหล่งข้อมูล
        /// </สรุป>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // เราตัดสินใจว่าเราต้องการให้ค่าบูลีนทั้งหมดถูกส่งออกเป็นฟิลด์ฟอร์มกล่องกาเครื่องหมาย
            if (e.getFieldValue() instanceof /*บูลีน*/Boolean)
            {
                // ย้าย "เคอร์เซอร์" ไปยังฟิลด์ผสานปัจจุบัน
                mBuilder.moveToMergeField(e.getFieldName());
                String checkBoxName = MessageFormat.format("{0}{1}", e.getFieldName(), e.getRecordIndex());
                mBuilder.insertCheckBox(checkBoxName, (Boolean) e.getFieldValue(), 0);
                return;
            }
            switch (e.getFieldName())
            {
                case "Body":
                    mBuilder.moveToMergeField(e.getFieldName());
                    mBuilder.insertHtml((String) e.getFieldValue());
                    break;
                case "Subject":
                {
                    mBuilder.moveToMergeField(e.getFieldName());
                    String textInputName = MessageFormat.format("{0}{1}", e.getFieldName(), e.getRecordIndex());
                    mBuilder.insertTextInput(textInputName, TextFormFieldType.REGULAR, "", (String) e.getFieldValue(), 0);
                    break;
                }
            }
        }
        public void imageFieldMerging(ImageFieldMergingArgs args)
        {
            args.setImageFileName("Image.png");
            args.getImageWidth().setValue(200.0);
            args.setImageHeight(new MergeFieldImageDimension(200.0, MergeFieldImageDimensionUnit.PERCENT));
        }
        private DocumentBuilder mBuilder;
    }
    @Test
    public void mailMergeImageField() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("
{{#foreach example}}");
        builder.writeln("
{{Image(126pt;126pt):stempel}}");
        builder.writeln("
{{/foreach example}}");
        doc.getMailMerge().setUseNonMergeFields(true);
        doc.getMailMerge().setTrimWhitespaces(true);
        doc.getMailMerge().setUseWholeParagraphAsRegion(false);
        doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS
                | MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS
                | MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS
                | MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);
        doc.getMailMerge().setFieldMergingCallback(new ImageFieldMergingHandler());
        doc.getMailMerge().executeWithRegions(new DataSourceRoot());
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeImageField.docx");
    }
    private static class ImageFieldMergingHandler implements IFieldMergingCallback
    {
        public void fieldMerging(FieldMergingArgs args)
        {
            //  ไม่จำเป็นต้องมีการดำเนินการใดๆ
        }
        public void imageFieldMerging(ImageFieldMergingArgs args) throws Exception
        {
            Shape shape = new Shape(args.getDocument(), ShapeType.IMAGE);
            {
                shape.setWidth(126.0); shape.setHeight(126.0); shape.setWrapType(WrapType.SQUARE);
            }
            shape.getImageData().setImage("Your Directory Path" + "Mail merge image.png");
            args.setShape(shape);
        }
    }
    public static class DataSourceRoot implements IMailMergeDataSourceRoot
    {
        public IMailMergeDataSource getDataSource(String s)
        {
            return new DataSource();
        }
        private static class DataSource implements IMailMergeDataSource
        {
            private boolean next = true;
            private String tableName()
            {
                return "example";
            }
            @Override
            public String getTableName() {
                return tableName();
            }
            public boolean moveNext()
            {
                boolean result = next;
                next = false;
                return result;
            }
            public IMailMergeDataSource getChildDataSource(String s)
            {
                return null;
            }
            public boolean getValue(String fieldName, Ref<Object> fieldValue)
            {
                fieldValue.set(null);
                return false;
            }
        }
    }
    @Test
    public void mailMergeAndConditionalField() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // แทรก MERGEFIELD ที่ซ้อนอยู่ในฟิลด์ IF
        // เนื่องจากคำสั่งฟิลด์ IF เป็นเท็จ ผลลัพธ์ของ MERGEFIELD ภายในจะไม่แสดง
        // และ MERGEFIELD จะไม่รับข้อมูลใดๆ ในระหว่างการรวมจดหมาย
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // เราจะยังคงนับ MERGEFIELD ภายในฟิลด์ IF ที่เป็นคำสั่งเท็จได้หากเราตั้งค่าแฟล็กนี้เป็น true
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // ผลลัพธ์จะไม่ปรากฏในเอกสารเนื่องจากฟิลด์ IF เป็นเท็จ
        // แต่ MERGEFIELD ด้านในก็ได้รับข้อมูลแล้ว
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "Northwind.mdb";
        Connection connection = DriverManager.getConnection(connString, "Admin", "");
        Statement statement = connection.createStatement();
        ResultSet resultSet = statement.executeQuery("SELECT * FROM Employees");
        DataTable dataTable = new DataTable(resultSet, "Employees");
        IDataReader dataReader = new DataTableReader(dataTable);
        doc.getMailMerge().executeWithRegions(dataReader, "Employees");
        connection.close();
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeImageFromBlob.docx");
    }
    public static class HandleMergeImageFieldFromBlob implements IFieldMergingCallback
    {
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs args)
        {
            // ไม่ต้องทำอะไร
        }
        /// <สรุป>
        /// นี่จะถูกเรียกใช้เมื่อโปรแกรมผสานจดหมายพบฟิลด์ผสาน Image:XXX ในเอกสาร
        /// คุณมีโอกาสที่จะส่งคืนวัตถุ Image ชื่อไฟล์ หรือสตรีมที่ประกอบด้วยรูปภาพ
        /// </สรุป>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // ค่าของฟิลด์เป็นอาร์เรย์ไบต์ เพียงแค่แคสต์และสร้างสตรีมบนนั้น
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // ขณะนี้เครื่องมือผสานจดหมายจะดึงภาพจากสตรีม
            e.setImageStream(imageStream);
        }
    }
    @Test
    public void handleMailMergeSwitches() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Field sample - MERGEFIELD.docx");
        doc.getMailMerge().setFieldMergingCallback(new MailMergeSwitches());
        final String HTML = "<html>\r\n                    <h1>Hello world!</h1>\r\n            </html>";
        doc.getMailMerge().execute(new String[] { "htmlField1" }, new Object[] { HTML });
        doc.save("Your Directory Path" + "WorkingWithFields.HandleMailMergeSwitches.docx");
    }
    public static class MailMergeSwitches implements IFieldMergingCallback
    {
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (e.getFieldName().startsWith("HTML"))
            {
                if (e.getField().getFieldCode().contains("\\b"))
                {
                    FieldMergeField field = e.getField();
                    DocumentBuilder builder = new DocumentBuilder(e.getDocument());
                    builder.moveToMergeField(e.getDocumentFieldName(), true, false);
                    builder.write(field.getTextBefore());
                    builder.insertHtml(e.getFieldValue().toString());
                    e.setText("");
                }
            }
        }
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
        }
    }
    @Test
    public void alternatingRows() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeFieldAlternatingRows());
        DataTable dataTable = getSuppliersDataTable();
        doc.getMailMerge().executeWithRegions(dataTable);
        doc.save("Your Directory Path" + "WorkingWithFields.AlternatingRows.doc");
    }
    private static class HandleMergeFieldAlternatingRows implements IFieldMergingCallback
    {
        /// <สรุป>
        /// เรียกใช้สำหรับฟิลด์ผสานทุกฟิลด์ที่พบในเอกสาร
        //เราจะส่งข้อมูลบางส่วนกลับไปยังโปรแกรมผสานจดหมายหรือทำอย่างอื่นกับเอกสารได้
        /// ในกรณีนี้เราจะปรับเปลี่ยนการจัดรูปแบบเซลล์
        /// </สรุป>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // เลือกสีขึ้นอยู่กับว่าหมายเลขแถวเป็นคู่หรือคี่
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // ในขณะนี้ยังไม่มีวิธีตั้งค่าคุณสมบัติเซลล์สำหรับแถวทั้งหมด ดังนั้นเราจะต้องทำซ้ำในเซลล์ทั้งหมดในแถว
                for (int colIdx = 0; colIdx < 4; colIdx++)
                {
                    mBuilder.moveToCell(0, mRowIdx, colIdx, 0);
                    mBuilder.getCellFormat().getShading().setBackgroundPatternColor(rowColor);
                }
                mRowIdx++;
            }
        }
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
            // ไม่ต้องทำอะไร
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <สรุป>
    /// คืนค่าเป็นจริงถ้าค่าเป็นคี่ คืนค่าเท็จถ้าค่าเป็นคู่
    /// </สรุป>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <สรุป>
    /// สร้าง DataTable และกรอกข้อมูลลงไป
    //ในชีวิตจริง DataTable นี้ควรได้รับการกรอกจากฐานข้อมูล
    /// </สรุป>
    private DataTable getSuppliersDataTable()
    {
        DataTable dataTable = new DataTable("Suppliers");
        dataTable.getColumns().add("CompanyName");
        dataTable.getColumns().add("ContactName");
        for (int i = 0; i < 10; i++)
        {
            DataRow datarow = dataTable.newRow();
            dataTable.getRows().add(datarow);
            datarow.set(0, "Company " + i);
            datarow.set(1, "Contact " + i);
        }
        return dataTable;
	}
}
```

## 6. บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีใช้ฟิลด์ใน Aspose.Words สำหรับ Java เพื่อจัดการเอกสาร Word แบบไดนามิกแล้ว API ที่มีประสิทธิภาพนี้ช่วยให้คุณควบคุมเอกสารของคุณได้อย่างสมบูรณ์ ทำให้เป็นทรัพยากรที่มีค่าสำหรับนักพัฒนา Java

## 7. คำถามที่พบบ่อย

### คำถามที่ 1: ฉันสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้ที่ไหน
คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้จาก [ที่นี่](https://releases-aspose.com/words/java/).

### คำถามที่ 2: ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ Java ได้อย่างไร
คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [ที่นี่](https://purchase-aspose.com/temporary-license/).

### คำถามที่ 3: ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ Java ได้จากที่ไหน
หากต้องการความช่วยเหลือ คุณสามารถเยี่ยมชมฟอรัม Aspose.Words [ที่นี่](https://forum-aspose.com/).

### คำถามที่ 4: Aspose.Words สำหรับ Java เหมาะกับการจัดการเนื้อหา HTML ในเอกสาร Word หรือไม่
ใช่ Aspose.Words สำหรับ Java รองรับการจัดการเนื้อหา HTML ในเอกสาร Word ได้อย่างยอดเยี่ยม

### คำถามที่ 5: ฉันสามารถใช้ Aspose.Words สำหรับ Java ได้ฟรีหรือไม่?
Aspose.Words สำหรับ Java เป็นผลิตภัณฑ์เชิงพาณิชย์ แต่คุณสามารถสำรวจคุณลักษณะต่างๆ ของมันได้ด้วยการทดลองใช้ฟรี [ที่นี่](https://releases-aspose.com/).

เริ่มต้นใช้งาน Aspose.Words สำหรับ Java วันนี้และควบคุมเอกสาร Word ของคุณได้อย่างที่ไม่เคยมีมาก่อน!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}