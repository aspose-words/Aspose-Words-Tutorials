---
"description": "Học cách sử dụng Aspose.Words cho các trường Java một cách hiệu quả trong hướng dẫn từng bước này. Tạo tài liệu Word động một cách dễ dàng."
"linktitle": "Sử dụng các trường"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng Fields trong Aspose.Words cho Java"
"url": "/vi/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Fields trong Aspose.Words cho Java


Trong hướng dẫn từng bước này, chúng tôi sẽ hướng dẫn bạn cách sử dụng các trường trong Aspose.Words for Java để thao tác tài liệu một cách dễ dàng. Aspose.Words for Java là một API mạnh mẽ cho phép bạn làm việc với các tài liệu Word theo chương trình, giúp bạn kiểm soát hoàn toàn nội dung và định dạng của chúng.

## 1. Giới thiệu

Aspose.Words for Java là một công cụ thiết yếu cho bất kỳ ai xử lý tài liệu Word trong các ứng dụng Java. Các trường là chỗ giữ chỗ có thể lưu trữ dữ liệu động trong tài liệu của bạn. Hướng dẫn này sẽ chỉ cho bạn cách làm việc với các trường một cách hiệu quả.

## 2. Thiết lập môi trường của bạn

Trước khi bắt đầu, hãy đảm bảo bạn đã cài đặt Aspose.Words for Java. Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/java/)Ngoài ra, hãy đảm bảo rằng bạn đã cài đặt Java và môi trường phát triển tích hợp (IDE) như Eclipse hoặc IntelliJ IDEA trên hệ thống của mình.

## 3. Tải một tài liệu Word

Trong ứng dụng Java của bạn, bạn cần tải tài liệu Word mà bạn muốn làm việc. Sau đây là một đoạn mã để bạn bắt đầu:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Thay thế `"Your Document Directory"` Và `"Your Output Directory"` với những con đường thích hợp.

## 4. Tùy chỉnh Mail Merge

Aspose.Words for Java cung cấp hỗ trợ tuyệt vời cho các hoạt động trộn thư. Bạn có thể tùy chỉnh quy trình trộn thư bằng cách thiết lập trình xử lý sự kiện trộn thư. Sau đây là cách thực hiện:

```java
// Thiết lập trình xử lý sự kiện trộn thư để thực hiện công việc tùy chỉnh.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Cắt bớt khoảng trắng ở đầu và cuối giá trị trộn thư.
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

## 5. Lưu tài liệu

Sau khi tùy chỉnh tài liệu, bạn có thể lưu tài liệu bằng mã sau:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Thay thế `"Your Output Directory"` với đường dẫn đầu ra mong muốn.

## Mã nguồn đầy đủ
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Thiết lập trình xử lý sự kiện trộn thư để thực hiện công việc tùy chỉnh.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Cắt bớt khoảng trắng ở đầu và cuối giá trị trộn thư.
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
Mã nguồn của Class HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <tóm tắt>
        /// Trình xử lý này được gọi cho mọi trường hợp trộn thư được tìm thấy trong tài liệu,
        /// cho mọi bản ghi được tìm thấy trong nguồn dữ liệu.
        /// </tóm tắt>
        public void /*Lệnh gọi lại IFieldMerging.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Chúng tôi quyết định rằng chúng tôi muốn tất cả các giá trị boolean được xuất ra dưới dạng các trường biểu mẫu hộp kiểm.
            if (e.getFieldValue() instanceof /*Boolean*/Boolean)
            {
                // Di chuyển "con trỏ" đến trường hợp nhập hiện tại.
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
            //  Không cần phải thực hiện.
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
        // Chèn MERGEFIELD lồng vào bên trong trường IF.
        // Vì câu lệnh trường IF là sai nên kết quả của MERGEFIELD bên trong sẽ không được hiển thị,
        // và MERGEFIELD sẽ không nhận được bất kỳ dữ liệu nào trong quá trình trộn thư.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Chúng ta vẫn có thể đếm MERGEFIELD bên trong các trường IF có câu lệnh sai nếu chúng ta đặt cờ này thành true.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Kết quả sẽ không hiển thị trong tài liệu vì trường IF là sai,
        // nhưng MERGEFIELD bên trong thực sự đã nhận được dữ liệu.
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
        public void /*Lệnh gọi lại IFieldMerging.*/fieldMerging(FieldMergingArgs args)
        {
            // Không làm gì cả.
        }
        /// <tóm tắt>
        /// Lệnh này được gọi khi công cụ trộn thư gặp trường trộn Image:XXX trong tài liệu.
        /// Bạn có cơ hội trả về một đối tượng Hình ảnh, tên tệp hoặc luồng chứa hình ảnh.
        /// </tóm tắt>
        public void /*Lệnh gọi lại IFieldMerging.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Giá trị trường là một mảng byte, chỉ cần ép kiểu và tạo một luồng trên đó.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Bây giờ công cụ trộn thư sẽ lấy hình ảnh từ luồng.
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
        public void /*Lệnh gọi lại IFieldMerging.*/fieldMerging(FieldMergingArgs e) throws Exception
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
        public void /*Lệnh gọi lại IFieldMerging.*/imageFieldMerging(ImageFieldMergingArgs args)
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
        /// <tóm tắt>
        /// Được gọi cho mọi trường hợp hợp nhất gặp phải trong tài liệu.
        /// Chúng ta có thể trả lại một số dữ liệu cho công cụ trộn thư hoặc làm gì đó khác với tài liệu.
        /// Trong trường hợp này chúng ta sửa đổi định dạng ô.
        /// </tóm tắt>
        public void /*Lệnh gọi lại IFieldMerging.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Chọn màu tùy thuộc vào số hàng là chẵn hay lẻ.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Hiện tại không có cách nào để thiết lập thuộc tính ô cho toàn bộ hàng, vì vậy chúng ta phải lặp lại tất cả các ô trong hàng.
                for (int colIdx = 0; colIdx < 4; colIdx++)
                {
                    mBuilder.moveToCell(0, mRowIdx, colIdx, 0);
                    mBuilder.getCellFormat().getShading().setBackgroundPatternColor(rowColor);
                }
                mRowIdx++;
            }
        }
        public void /*Lệnh gọi lại IFieldMerging.*/imageFieldMerging(ImageFieldMergingArgs args)
        {
            // Không làm gì cả.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <tóm tắt>
    /// Trả về true nếu giá trị là lẻ; false nếu giá trị là chẵn.
    /// </tóm tắt>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <tóm tắt>
    /// Tạo DataTable và nhập dữ liệu vào đó.
    /// Trong thực tế, DataTable này phải được điền từ cơ sở dữ liệu.
    /// </tóm tắt>
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

## 6. Kết luận

Xin chúc mừng! Bạn đã học cách sử dụng các trường trong Aspose.Words for Java để thao tác các tài liệu Word một cách năng động. API mạnh mẽ này cung cấp cho bạn quyền kiểm soát hoàn toàn đối với các tài liệu của mình, khiến nó trở thành một tài sản có giá trị đối với các nhà phát triển Java.

## 7. Câu hỏi thường gặp

### Câu hỏi 1: Tôi có thể tải Aspose.Words cho Java ở đâu?
Bạn có thể tải xuống Aspose.Words cho Java từ [đây](https://releases.aspose.com/words/java/).

### Câu hỏi 2: Làm thế nào tôi có thể nhận được giấy phép tạm thời cho Aspose.Words dành cho Java?
Bạn có thể xin giấy phép tạm thời từ [đây](https://purchase.aspose.com/temporary-license/).

### Câu hỏi 3: Tôi có thể nhận hỗ trợ cho Aspose.Words dành cho Java ở đâu?
Để được hỗ trợ, bạn có thể truy cập diễn đàn Aspose.Words [đây](https://forum.aspose.com/).

### Câu hỏi 4: Aspose.Words for Java có phù hợp để xử lý nội dung HTML trong tài liệu Word không?
Có, Aspose.Words for Java cung cấp hỗ trợ tuyệt vời cho việc xử lý nội dung HTML trong tài liệu Word.

### Câu hỏi 5: Tôi có thể sử dụng Aspose.Words cho Java miễn phí không?
Aspose.Words for Java là một sản phẩm thương mại, nhưng bạn có thể khám phá các tính năng của nó với bản dùng thử miễn phí [đây](https://releases.aspose.com/).

Hãy bắt đầu sử dụng Aspose.Words for Java ngay hôm nay và kiểm soát các tài liệu Word của bạn theo cách chưa từng có!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}