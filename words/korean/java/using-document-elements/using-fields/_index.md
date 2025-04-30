---
"description": "이 단계별 튜토리얼을 통해 Aspose.Words for Java 필드를 효과적으로 사용하는 방법을 알아보세요. 동적인 Word 문서를 손쉽게 만들어 보세요."
"linktitle": "필드 사용"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 필드 사용"
"url": "/ko/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 필드 사용


이 단계별 튜토리얼에서는 Aspose.Words for Java의 필드를 사용하여 문서를 쉽게 조작하는 방법을 안내합니다. Aspose.Words for Java는 Word 문서를 프로그래밍 방식으로 작업할 수 있는 강력한 API로, 문서의 내용과 서식을 완벽하게 제어할 수 있습니다.

## 1. 서론

Aspose.Words for Java는 Java 애플리케이션에서 Word 문서를 다루는 모든 사람에게 필수적인 도구입니다. 필드는 문서에 동적 데이터를 저장할 수 있는 자리 표시자입니다. 이 튜토리얼에서는 필드를 효과적으로 사용하는 방법을 보여줍니다.

## 2. 환경 설정

시작하기 전에 Aspose.Words for Java가 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/)또한, 시스템에 Java와 Eclipse나 IntelliJ IDEA 같은 통합 개발 환경(IDE)이 설치되어 있는지 확인하세요.

## 3. Word 문서 로딩

Java 애플리케이션에서 작업할 Word 문서를 로드해야 합니다. 다음은 시작하는 데 도움이 되는 코드 조각입니다.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

바꾸다 `"Your Document Directory"` 그리고 `"Your Output Directory"` 적절한 경로를 사용하여.

## 4. 메일 병합 사용자 지정

Aspose.Words for Java는 메일 병합 작업에 대한 탁월한 지원을 제공합니다. 메일 병합 이벤트 핸들러를 설정하여 메일 병합 프로세스를 사용자 지정할 수 있습니다. 방법은 다음과 같습니다.

```java
// 사용자 지정 작업을 수행하기 위해 메일 병합 이벤트 핸들러를 설정합니다.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// 메일 병합 값의 앞뒤 공백을 제거합니다.
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

## 5. 문서 저장

문서를 사용자 지정한 후 다음 코드를 사용하여 저장할 수 있습니다.

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

바꾸다 `"Your Output Directory"` 원하는 출력 경로를 사용합니다.

## 완전한 소스 코드
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// 사용자 지정 작업을 수행하기 위해 메일 병합 이벤트 핸들러를 설정합니다.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// 메일 병합 값의 앞뒤 공백을 제거합니다.
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
클래스 HandleMergeField의 소스 코드

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <요약>
        /// 이 핸들러는 문서에서 발견된 모든 메일 병합 필드에 대해 호출됩니다.
        /// 데이터 소스에서 발견된 모든 레코드에 대해.
        /// </요약>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // 우리는 모든 부울 값을 체크박스 양식 필드로 출력하기로 결정했습니다.
            if (e.getFieldValue() instanceof /*부울*/Boolean)
            {
                // "커서"를 현재 병합 필드로 이동합니다.
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
            //  구현이 필요하지 않습니다.
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
        // IF 필드 내부에 중첩된 MERGEFIELD를 삽입합니다.
        // IF 필드 문이 거짓이므로 내부 MERGEFIELD의 결과는 표시되지 않습니다.
        // 그리고 MERGEFIELD는 메일 병합 중에 어떠한 데이터도 수신하지 않습니다.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // 이 플래그를 true로 설정하면 거짓 문장 IF 필드 내부의 MERGEFIELD를 여전히 계산할 수 있습니다.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // IF 필드가 false이기 때문에 결과가 문서에 표시되지 않습니다.
        // 하지만 내부 MERGEFIELD는 실제로 데이터를 수신했습니다.
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
            // 아무것도 하지 마세요.
        }
        /// <요약>
        /// 이것은 메일 병합 엔진이 문서에서 Image:XXX 병합 필드를 발견했을 때 호출됩니다.
        /// 이미지가 포함된 이미지 객체, 파일 이름 또는 스트림을 반환할 수 있습니다.
        /// </요약>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // 필드 값은 바이트 배열입니다. 이를 캐스팅하여 스트림을 생성하기만 하면 됩니다.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // 이제 메일 병합 엔진이 스트림에서 이미지를 검색합니다.
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
        /// <요약>
        /// 문서에서 발견된 모든 병합 필드에 대해 호출됩니다.
        /// 메일 병합 엔진에 일부 데이터를 반환하거나 문서에서 다른 작업을 수행할 수 있습니다.
        /// 이 경우 셀 서식을 수정합니다.
        /// </요약>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // 행 번호가 짝수인지 홀수인지에 따라 색상을 선택하세요.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // 현재로선 행 전체에 대한 셀 속성을 설정할 방법이 없으므로 행의 모든 셀을 반복해야 합니다.
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
            // 아무것도 하지 마세요.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <요약>
    /// 값이 홀수이면 true를 반환하고, 값이 짝수이면 false를 반환합니다.
    /// </요약>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <요약>
    /// DataTable을 만들고 데이터를 채웁니다.
    /// 실제로 이 DataTable은 데이터베이스에서 채워져야 합니다.
    /// </요약>
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

## 6. 결론

축하합니다! Aspose.Words for Java의 필드를 사용하여 Word 문서를 동적으로 조작하는 방법을 배웠습니다. 이 강력한 API는 문서를 완벽하게 제어할 수 있게 해 주므로 Java 개발자에게 매우 귀중한 자산입니다.

## 7. FAQ

### 질문 1: Aspose.Words for Java를 어디서 다운로드할 수 있나요?
Aspose.Words for Java는 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/).

### 질문 2: Aspose.Words for Java에 대한 임시 라이선스를 어떻게 받을 수 있나요?
임시면허를 취득할 수 있습니다. [여기](https://purchase.aspose.com/temporary-license/).

### 질문 3: Java용 Aspose.Words에 대한 지원은 어디에서 받을 수 있나요?
지원을 받으려면 Aspose.Words 포럼을 방문하세요. [여기](https://forum.aspose.com/).

### 질문 4: Aspose.Words for Java는 Word 문서에서 HTML 콘텐츠를 처리하는 데 적합합니까?
네, Aspose.Words for Java는 Word 문서에서 HTML 콘텐츠를 처리하는 데 탁월한 지원을 제공합니다.

### Q5: Aspose.Words for Java를 무료로 사용할 수 있나요?
Aspose.Words for Java는 상용 제품이지만 무료 평가판을 통해 기능을 탐색할 수 있습니다. [여기](https://releases.aspose.com/).

지금 당장 Aspose.Words for Java를 시작하고 그 어느 때보다 Word 문서를 효율적으로 관리해보세요!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}