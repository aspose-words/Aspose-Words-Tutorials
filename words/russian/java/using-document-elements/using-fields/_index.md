---
title: Использование полей в Aspose.Words для Java
linktitle: Использование полей
second_title: API обработки документов Java Aspose.Words
description: Научитесь эффективно использовать Aspose.Words для полей Java в этом пошаговом руководстве. Создавайте динамические документы Word с легкостью.
weight: 11
url: /ru/java/using-document-elements/using-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование полей в Aspose.Words для Java


В этом пошаговом руководстве мы расскажем вам, как использовать поля в Aspose.Words для Java для легкой обработки документов. Aspose.Words для Java — это мощный API, который позволяет вам работать с документами Word программно, предоставляя вам полный контроль над их содержимым и форматированием.

## 1. Введение

Aspose.Words for Java — это необходимый инструмент для тех, кто работает с документами Word в приложениях Java. Поля — это заполнители, которые могут хранить динамические данные в вашем документе. Этот урок покажет вам, как эффективно работать с полями.

## 2. Настройка вашей среды

 Прежде чем начать, убедитесь, что у вас установлен Aspose.Words for Java. Вы можете загрузить его с[здесь](https://releases.aspose.com/words/java/). Также убедитесь, что в вашей системе установлены Java и интегрированная среда разработки (IDE), например Eclipse или IntelliJ IDEA.

## 3. Загрузка документа Word

В вашем приложении Java вам нужно загрузить документ Word, с которым вы хотите работать. Вот фрагмент кода, с которого можно начать:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

 Заменять`"Your Document Directory"` и`"Your Output Directory"` с соответствующими путями.

## 4. Настройка слияния писем

Aspose.Words for Java обеспечивает превосходную поддержку операций слияния почты. Вы можете настроить процесс слияния почты, настроив обработчик событий слияния почты. Вот как это сделать:

```java
// Настройте обработчик событий слияния почты для выполнения специальной работы.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Обрезайте конечные и начальные пробелы в значениях слияния почты.
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

## 5. Сохранение документа

После настройки документа вы можете сохранить его, используя следующий код:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

 Заменять`"Your Output Directory"` с желаемым выходным путем.

## Полный исходный код
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Настройте обработчик событий слияния почты для выполнения специальной работы.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Обрезайте конечные и начальные пробелы в значениях слияния почты.
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
Исходный код класса HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <резюме>
        /// Этот обработчик вызывается для каждого поля слияния, найденного в документе,
        /// для каждой записи, найденной в источнике данных.
        /// </резюме>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Мы решили, что хотим, чтобы все логические значения выводились в виде полей формы с флажками.
            if (e.getFieldValue() instanceof /*boolean*/Boolean)
            {
                // Переместите «курсор» в текущее поле слияния.
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
            // Реализация не требуется.
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
        // Вставьте MERGEFIELD, вложенный в поле IF.
        // Поскольку оператор поля IF является ложным, результат внутреннего MERGEFIELD не будет отображен,
        //и MERGEFIELD не будет получать никаких данных во время слияния почты.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Мы по-прежнему можем подсчитывать MERGEFIELD внутри полей IF с ложным оператором, если установим этот флаг в значение true.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Результат не будет виден в документе, поскольку поле IF имеет значение false,
        // но внутренний MERGEFIELD действительно получил данные.
        doc.save("Your Directory Path" + "WorkingWithFields.MailMergeAndConditionalField.docx");
    }
    @Test
    public void mailMergeImageFromBlob() throws Exception
    {
        Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind employees.docx");
        doc.getMailMerge().setFieldMergingCallback(new HandleMergeImageFieldFromBlob());
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        String connString = "jdbc:ucanaccess://" + getDatabaseDir() + "Борей.mdb";
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
            // Ничего не делать.
        }
        /// <резюме>
        /// Вызывается, когда механизм слияния почты обнаруживает в документе поле слияния Image:XXX.
        /// У вас есть возможность вернуть объект изображения, имя файла или поток, содержащий изображение.
        /// </резюме>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Значение поля — это массив байтов, просто приведите его к типу и создайте на его основе поток.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Теперь механизм слияния писем извлечет изображение из потока.
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
        /// <резюме>
        /// Вызывается для каждого поля слияния, встречающегося в документе.
        /// Мы можем либо вернуть некоторые данные в механизм слияния почты, либо сделать что-то еще с документом.
        /// В этом случае мы изменяем форматирование ячеек.
        /// </резюме>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Выберите цвет в зависимости от того, четный или нечетный номер строки.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                //На данный момент нет возможности задать свойства ячеек для всей строки, поэтому нам придется перебрать все ячейки в строке.
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
            // Ничего не делать.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <резюме>
    /// Возвращает true, если значение нечетное; false, если значение четное.
    /// </резюме>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <резюме>
    /// Создайте DataTable и заполните его данными.
    /// В реальной жизни этот DataTable должен заполняться из базы данных.
    /// </резюме>
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

## 6. Заключение

Поздравляем! Вы узнали, как использовать поля в Aspose.Words для Java для динамического управления документами Word. Этот мощный API дает вам полный контроль над вашими документами, что делает его ценным активом для разработчиков Java.

## 7. Часто задаваемые вопросы

### В1: Где я могу скачать Aspose.Words для Java?
 Вы можете загрузить Aspose.Words для Java с сайта[здесь](https://releases.aspose.com/words/java/).

### В2: Как получить временную лицензию на Aspose.Words для Java?
 Вы можете получить временную лицензию[здесь](https://purchase.aspose.com/temporary-license/).

### В3: Где я могу получить поддержку по Aspose.Words для Java?
 Для получения поддержки вы можете посетить форум Aspose.Words.[здесь](https://forum.aspose.com/).

### В4: Подходит ли Aspose.Words for Java для обработки HTML-контента в документах Word?
Да, Aspose.Words для Java обеспечивает превосходную поддержку обработки HTML-контента в документах Word.

### В5: Могу ли я использовать Aspose.Words для Java бесплатно?
 Aspose.Words для Java — коммерческий продукт, но вы можете изучить его возможности с помощью бесплатной пробной версии.[здесь](https://releases.aspose.com/).

Начните работу с Aspose.Words для Java уже сегодня и получите невиданный ранее контроль над своими документами Word!


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
