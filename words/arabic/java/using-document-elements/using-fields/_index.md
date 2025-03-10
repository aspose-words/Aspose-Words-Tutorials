---
title: استخدام الحقول في Aspose.Words للغة Java
linktitle: استخدام الحقول
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعلم كيفية استخدام Aspose.Words لحقول Java بفعالية في هذا البرنامج التعليمي خطوة بخطوة. قم بإنشاء مستندات Word ديناميكية بسهولة.
weight: 11
url: /ar/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام الحقول في Aspose.Words للغة Java


في هذا البرنامج التعليمي خطوة بخطوة، سنرشدك إلى كيفية استخدام الحقول في Aspose.Words for Java للتعامل مع المستندات بسهولة. Aspose.Words for Java عبارة عن واجهة برمجة تطبيقات قوية تتيح لك العمل مع مستندات Word برمجيًا، مما يمنحك التحكم الكامل في محتواها وتنسيقها.

## 1. المقدمة

يعد Aspose.Words for Java أداة أساسية لأي شخص يتعامل مع مستندات Word في تطبيقات Java. الحقول عبارة عن عناصر نائبة يمكنها تخزين البيانات الديناميكية في مستندك. سيوضح لك هذا البرنامج التعليمي كيفية العمل مع الحقول بشكل فعال.

## 2. إعداد البيئة الخاصة بك

 قبل أن تبدأ، تأكد من تثبيت Aspose.Words for Java. يمكنك تنزيله من[هنا](https://releases.aspose.com/words/java/)تأكد أيضًا من تثبيت Java وبيئة التطوير المتكاملة (IDE) مثل Eclipse أو IntelliJ IDEA على نظامك.

## 3. تحميل مستند Word

في تطبيق Java الخاص بك، تحتاج إلى تحميل مستند Word الذي تريد العمل به. فيما يلي مقتطف من التعليمات البرمجية لمساعدتك في البدء:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 يستبدل`"Your Document Directory"` و`"Your Output Directory"` مع المسارات المناسبة.

## 4. تخصيص دمج البريد

يوفر Aspose.Words for Java دعمًا ممتازًا لعمليات دمج البريد. يمكنك تخصيص عملية دمج البريد من خلال إعداد معالج حدث دمج البريد. وإليك كيفية القيام بذلك:

```java
// إعداد معالج حدث دمج البريد للقيام بالعمل المخصص.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// قم بقص المسافات البيضاء الزائدة والبادئة في قيم دمج البريد.
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

## 5. حفظ المستند

بعد تخصيص مستندك، يمكنك حفظه باستخدام الكود التالي:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 يستبدل`"Your Output Directory"` مع مسار الإخراج المطلوب.

## الكود المصدر الكامل
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// إعداد معالج حدث دمج البريد للقيام بالعمل المخصص.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// قم بقص المسافات البيضاء الزائدة والبادئة في قيم دمج البريد.
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
الكود المصدر لفئة HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <ملخص>
        //يتم استدعاء هذا المعالج لكل حقل دمج بريد موجود في المستند،
        /// لكل سجل موجود في مصدر البيانات.
        /// </ملخص>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // لقد قررنا أننا نريد إخراج كافة القيم المنطقية كحقول نموذج مربع الاختيار.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // نقل "المؤشر" إلى حقل الدمج الحالي.
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
        builder.writeln("{{#foreach example}}");
        builder.writeln("{{Image(126pt;126pt):stempel}}");
        builder.writeln("{{/foreach example}}");
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
            // لا يتطلب التنفيذ.
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
        // إدراج MERGEFIELD متداخلاً داخل حقل IF.
        // نظرًا لأن بيان الحقل IF خاطئ، فلن يتم عرض نتيجة MERGEFIELD الداخلي،
        //ولن يستقبل MERGEFIELD أي بيانات أثناء دمج البريد.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // لا يزال بإمكاننا حساب MERGEFIELDs داخل حقول IF ذات العبارة الخاطئة إذا قمنا بتعيين هذا العلم إلى true.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // لن تكون النتيجة مرئية في المستند لأن حقل IF خاطئ،
        // لكن حقل MERGEFIELD الداخلي تلقى بالفعل بيانات.
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
            // لا تفعل شيئا.
        }
        /// <ملخص>
        //يتم استدعاء هذا عندما يواجه محرك دمج البريد حقل الدمج Image:XXX في المستند.
        //لديك فرصة لإرجاع كائن صورة، أو اسم ملف، أو مجرى يحتوي على الصورة.
        /// </ملخص>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // قيمة الحقل عبارة عن مصفوفة بايتات، فقط قم بإلقائها وإنشاء تدفق عليها.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // الآن سوف يقوم محرك دمج البريد باسترداد الصورة من الدفق.
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
        /// <ملخص>
        /// يتم استدعاؤها لكل حقل دمج موجود في المستند.
        //يمكننا إما إرجاع بعض البيانات إلى محرك دمج البريد أو القيام بشيء آخر بالمستند.
        /// في هذه الحالة نقوم بتعديل تنسيق الخلية.
        /// </ملخص>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // حدد اللون اعتمادًا على ما إذا كان رقم الصف زوجيًا أم فرديًا.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //لا توجد طريقة لتعيين خصائص الخلية للصف بأكمله في الوقت الحالي، لذلك يتعين علينا التكرار على جميع الخلايا في الصف.
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
            // لا تفعل شيئا.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <ملخص>
    /// يعود صحيحًا إذا كانت القيمة فردية؛ ويعود خطأً إذا كانت القيمة زوجية.
    /// </ملخص>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <ملخص>
    /// إنشاء جدول البيانات وملئه بالبيانات.
    //في الحياة الواقعية، يجب ملء جدول البيانات هذا من قاعدة البيانات.
    /// </ملخص>
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

## 6. الخاتمة

تهانينا! لقد تعلمت كيفية استخدام الحقول في Aspose.Words for Java للتعامل مع مستندات Word بشكل ديناميكي. تمنحك واجهة برمجة التطبيقات القوية هذه التحكم الكامل في مستنداتك، مما يجعلها أصلًا قيمًا لمطوري Java.

## 7. الأسئلة الشائعة

### س1: أين يمكنني تنزيل Aspose.Words لـ Java؟
 يمكنك تنزيل Aspose.Words for Java من[هنا](https://releases.aspose.com/words/java/).

### س2: كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words لـ Java؟
 يمكنك الحصول على ترخيص مؤقت من[هنا](https://purchase.aspose.com/temporary-license/).

### س3: أين يمكنني الحصول على الدعم لـ Aspose.Words لـ Java؟
 للحصول على الدعم، يمكنك زيارة منتدى Aspose.Words[هنا](https://forum.aspose.com/).

### س4: هل Aspose.Words for Java مناسب للتعامل مع محتوى HTML في مستندات Word؟
نعم، يوفر Aspose.Words for Java دعمًا ممتازًا للتعامل مع محتوى HTML في مستندات Word.

### س5: هل يمكنني استخدام Aspose.Words لـ Java مجانًا؟
 Aspose.Words for Java هو منتج تجاري، ولكن يمكنك استكشاف ميزاته من خلال إصدار تجريبي مجاني متاح[هنا](https://releases.aspose.com/).

ابدأ باستخدام Aspose.Words for Java اليوم وتحكم في مستندات Word الخاصة بك بشكل لم يسبق له مثيل!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
