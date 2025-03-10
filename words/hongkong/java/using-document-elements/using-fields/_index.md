---
title: 在 Aspose.Words for Java 中使用字段
linktitle: 使用字段
second_title: Aspose.Words Java 文件處理 API
description: 在本逐步教程中學習如何有效地使用 Aspose.Words for Java 欄位。輕鬆建立動態 Word 文件。
weight: 11
url: /zh-hant/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用字段


在本逐步教學中，我們將指導您如何使用 Aspose.Words for Java 中的欄位輕鬆操作文件。 Aspose.Words for Java 是一個功能強大的 API，可讓您以程式設計方式處理 Word 文檔，從而完全控制其內容和格式。

## 一、簡介

Aspose.Words for Java 是任何在 Java 應用程式中處理 Word 文件的人的必備工具。欄位是可以在文件中儲存動態資料的佔位符。本教學將向您展示如何有效地使用欄位。

## 2. 設定您的環境

開始之前，請確保已安裝 Aspose.Words for Java。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/)。另外，請確保您的系統上安裝了 Java 和整合開發環境 (IDE)，例如 Eclipse 或 IntelliJ IDEA。

## 3. 載入Word文檔

在 Java 應用程式中，您需要載入要使用的 Word 文件。以下是一段可以幫助您入門的程式碼片段：

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

代替`"Your Document Directory"`和`"Your Output Directory"`與適當的路徑。

## 4. 自訂郵件合併

Aspose.Words for Java 為郵件合併作業提供了出色的支援。您可以透過設定郵件合併事件處理程序來自訂郵件合併流程。操作方法如下：

```java
//設定郵件合併事件處理程序來完成自訂工作。
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

//修剪郵件合併值的尾隨和前導空格。
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

## 5. 儲存文檔

自訂文件後，您可以使用以下程式碼儲存它：

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

代替`"Your Output Directory"`與所需的輸出路徑。

## 完整的原始碼
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
//設定郵件合併事件處理程序來完成自訂工作。
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
//修剪郵件合併值的尾隨和前導空格。
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
HandleMergeField類別的原始碼

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        //<摘要>
        //為文件中找到的每個郵件合併欄位呼叫此處理程序，
        /// 對於在資料來源中找到的每筆記錄。
        /// </摘要>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            //我們決定希望所有布林值都作為複選框表單欄位輸出。
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                //將“遊標”移至目前合併欄位。
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
            //不需要實施。
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
        //插入嵌套在 IF 欄位內的 MERGEFIELD。
        //由於IF欄位語句為假，因此內部MERGEFIELD的結果將不會顯示，
        //並且 MERGEFIELD 在郵件合併期間不會接收任何資料。
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        //如果我們將此標誌設為 true，我們仍然可以對錯誤語句 IF 欄位內的 MERGEFIELD 進行計數。
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        //結果在文件中將不可見，因為 IF 欄位為 false，
        //但內部MERGEFIELD確實收到了數據。
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
            //什麼也不做。
        }
        //<摘要>
        /// 當郵件合併引擎遇到文件中的 Image:XXX 合併欄位時呼叫此函數。
        /// 您有機會傳回一個 Image 物件、檔案名稱或包含該影像的串流。
        /// </摘要>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            //此欄位值是一個位元組數組，只需對其進行轉換並在其上建立一個流即可。
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            //現在郵件合併引擎將從串流中檢索影像。
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
        /// 為文件中遇到的每個合併欄位呼叫。
        /// 我們可以將一些資料傳回郵件合併引擎，或對文件執行其他操作。
        /// 在本例中我們修改儲存格格式。
        /// </摘要>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                //根據行號是偶數還是奇數選擇顏色。
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //目前無法設定整行的單元格屬性，因此我們必須迭代該行中的所有單元格。
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
            //什麼也不做。
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    //<摘要>
    /// 如果值為奇數則傳回 true；如果該值是偶數，則為 false。
    /// </摘要>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    //<摘要>
    /// 建立DataTable並用資料填充它。
    /// 在現實生活中，這個資料表應該從資料庫中填入。
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

## 六、結論

恭喜！您已經學習如何使用 Aspose.Words for Java 中的欄位來動態操作 Word 文件。這個強大的 API 使您能夠完全控製文檔，使其成為 Java 開發人員的寶貴資產。

## 7. 常見問題解答

### Q1：哪裡可以下載 Aspose.Words for Java？
您可以從以下位置下載 Aspose.Words for Java：[這裡](https://releases.aspose.com/words/java/).

### 問題 2：如何取得 Aspose.Words for Java 的臨時授權？
您可以從以下地址取得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 問題 3：在哪裡可以獲得 Aspose.Words for Java 的支援？
如需支持，您可以造訪 Aspose.Words 論壇[這裡](https://forum.aspose.com/).

### Q4：Aspose.Words for Java適合處理Word文件中的HTML內容嗎？
是的，Aspose.Words for Java 為處理 Word 文件中的 HTML 內容提供了出色的支援。

### Q5：我可以免費使用 Aspose.Words for Java 嗎？
 Aspose.Words for Java 是一款商業產品，但您可以透過免費試用版探索其功能[這裡](https://releases.aspose.com/).

立即開始使用 Aspose.Words for Java，以前所未有的方式控制您的 Word 文件！


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
