---
title: 在 Aspose.Words for Java 中使用字段
linktitle: 使用字段
second_title: Aspose.Words Java 文档处理 API
description: 在本分步教程中学习如何有效地使用 Aspose.Words for Java 字段。轻松创建动态 Word 文档。
weight: 11
url: /zh/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用字段


在本分步教程中，我们将指导您如何使用 Aspose.Words for Java 中的字段轻松操作文档。Aspose.Words for Java 是一个功能强大的 API，允许您以编程方式处理 Word 文档，让您完全控制其内容和格式。

## 1. 简介

Aspose.Words for Java 是任何在 Java 应用程序中处理 Word 文档的人的必备工具。字段是可以在文档中存储动态数据的占位符。本教程将向您展示如何有效地使用字段。

## 2. 设置你的环境

开始之前，请确保已安装 Aspose.Words for Java。您可以从以下网址下载[这里](https://releases.aspose.com/words/java/)。另外，确保您的系统上安装了 Java 和集成开发环境 (IDE)，如 Eclipse 或 IntelliJ IDEA。

## 3. 加载 Word 文档

在 Java 应用程序中，您需要加载要处理的 Word 文档。以下是一段代码，可帮助您入门：

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

代替`"Your Document Directory"`和`"Your Output Directory"`使用适当的路径。

## 4. 自定义邮件合并

Aspose.Words for Java 为邮件合并操作提供了出色的支持。您可以通过设置邮件合并事件处理程序来自定义邮件合并过程。操作方法如下：

```java
//设置邮件合并事件处理程序来执行自定义工作。
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

//修剪邮件合并值的尾随和前导空格。
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

## 5.保存文档

自定义文档后，您可以使用以下代码保存它：

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

代替`"Your Output Directory"`使用所需的输出路径。

## 完整源代码
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
//设置邮件合并事件处理程序来执行自定义工作。
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
//修剪邮件合并值的尾随和前导空格。
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
HandleMergeField 类的源代码

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        //<摘要>
        //文档中的每个邮件合并字段都会调用此处理程序，
        /// 针对数据源中找到的每条记录。
        /// </摘要>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            //我们决定将所有布尔值都输出为复选框表单字段。
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                //将“光标”移动到当前合并字段。
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
            //无需实施。
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
        //插入嵌套在 IF 字段内的 MERGEFIELD。
        //由于 IF 字段语句为假，因此不会显示内部 MERGEFIELD 的结果，
        //并且 MERGEFIELD 在邮件合并期间将不会接收任何数据。
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        //如果将此标志设置为真，我们仍然可以计算错误语句 IF 字段内的 MERGEFIELDs。
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        //由于 IF 字段为 false，因此结果不会显示在文档中。
        //但内部的 MERGEFIELD 确实接收到了数据。
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
            //什么也不做。
        }
        //<摘要>
        /// 当邮件合并引擎在文档中遇到 Image:XXX 合并字段时调用此方法。
        /// 您有机会返回一个图像对象、文件名或包含图像的流。
        /// </摘要>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            //字段值是一个字节数组，只需将其转换并在其上创建一个流。
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            //现在邮件合并引擎将从流中检索图像。
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
        //<摘要>
        /// 对文档中遇到的每个合并字段进行调用。
        /// 我们可以将一些数据返回给邮件合并引擎或者对文档执行其他操作。
        /// 在这种情况下，我们修改单元格格式。
        /// </摘要>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                //根据行数是偶数还是奇数选择颜色。
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //目前没有办法为整行设置单元格属性，所以我们必须遍历该行中的所有单元格。
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
            //什么也不做。
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    //<摘要>
    /// 如果值为奇数，则返回 true；如果值为偶数，则返回 false。
    /// </摘要>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    //<摘要>
    /// 创建 DataTable 并用数据填充。
    /// 在现实生活中，这个 DataTable 应该从数据库中填充。
    /// </摘要>
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

## 6. 结论

恭喜！您已经学会了如何使用 Aspose.Words for Java 中的字段来动态操作 Word 文档。这个强大的 API 让您可以完全控制您的文档，这对 Java 开发人员来说是一笔宝贵的财富。

## 7. 常见问题解答

### 问题1：我可以在哪里下载 Aspose.Words for Java？
您可以从以下位置下载 Aspose.Words for Java[这里](https://releases.aspose.com/words/java/).

### 问题2：如何获取 Aspose.Words for Java 的临时许可证？
您可以从[这里](https://purchase.aspose.com/temporary-license/).

### 问题 3：在哪里可以获得 Aspose.Words for Java 的支持？
如需支持，您可以访问 Aspose.Words 论坛[这里](https://forum.aspose.com/).

### Q4: Aspose.Words for Java 适合处理Word文档中的HTML内容吗？
是的，Aspose.Words for Java 为处理 Word 文档中的 HTML 内容提供了出色的支持。

### Q5：我可以免费使用 Aspose.Words for Java 吗？
 Aspose.Words for Java 是一款商业产品，但您可以通过免费试用版探索其功能[这里](https://releases.aspose.com/).

立即开始使用 Aspose.Words for Java 并以前所未有的方式控制您的 Word 文档！


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
