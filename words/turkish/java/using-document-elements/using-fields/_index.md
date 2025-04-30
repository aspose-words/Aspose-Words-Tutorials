---
"description": "Bu adım adım eğitimde Aspose.Words for Java alanlarını etkili bir şekilde kullanmayı öğrenin. Dinamik Word belgelerini kolaylıkla oluşturun."
"linktitle": "Alanları Kullanma"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Alanları Kullanma"
"url": "/tr/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Alanları Kullanma


Bu adım adım eğitimde, Aspose.Words for Java'da belgeleri kolayca düzenlemek için alanları nasıl kullanacağınız konusunda size rehberlik edeceğiz. Aspose.Words for Java, Word belgeleriyle programatik olarak çalışmanıza olanak tanıyan ve içerikleri ve biçimlendirmeleri üzerinde tam kontrol sağlayan güçlü bir API'dir.

## 1. Giriş

Aspose.Words for Java, Java uygulamalarında Word belgeleriyle uğraşan herkes için olmazsa olmaz bir araçtır. Alanlar, belgenizde dinamik verileri depolayabilen yer tutuculardır. Bu eğitim, alanlarla etkili bir şekilde nasıl çalışacağınızı gösterecektir.

## 2. Ortamınızı Ayarlama

Başlamadan önce, Aspose.Words for Java'nın yüklü olduğundan emin olun. Bunu şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/)Ayrıca sisteminizde Java ve Eclipse veya IntelliJ IDEA gibi entegre bir geliştirme ortamının (IDE) yüklü olduğundan emin olun.

## 3. Bir Word Belgesi Yükleme

Java uygulamanızda, çalışmak istediğiniz Word belgesini yüklemeniz gerekir. Başlamanız için işte bir kod parçası:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Yer değiştirmek `"Your Document Directory"` Ve `"Your Output Directory"` uygun yollarla.

## 4. Posta Birleştirmeyi Özelleştirme

Java için Aspose.Words, posta birleştirme işlemleri için mükemmel destek sağlar. Bir posta birleştirme olay işleyicisi ayarlayarak posta birleştirme sürecini özelleştirebilirsiniz. İşte nasıl yapacağınız:

```java
// Özel çalışmayı yapmak için posta birleştirme olay işleyicisini ayarlayın.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Posta birleştirme değerlerinde son ve öndeki boşlukları kırpın.
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

## 5. Belgeyi Kaydetme

Belgenizi özelleştirdikten sonra aşağıdaki kodu kullanarak kaydedebilirsiniz:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Yer değiştirmek `"Your Output Directory"` İstenilen çıktı yolu ile.

## Tam Kaynak Kodu
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Özel çalışmayı yapmak için posta birleştirme olay işleyicisini ayarlayın.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Posta birleştirme değerlerinde son ve öndeki boşlukları kırpın.
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
HandleMergeField Sınıfının kaynak kodu

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <özet>
        /// Bu işleyici, belgede bulunan her birleştirme alanı için çağrılır.
        /// Veri kaynağında bulunan her kayıt için.
        /// </özet>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Tüm Boole değerlerinin onay kutusu form alanları olarak çıktı olarak verilmesini istediğimize karar verdik.
            if (e.getFieldValue() instanceof /*Boolean*/Boolean)
            {
                // "İmleci" geçerli birleştirme alanına taşıyın.
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
            //  Uygulanması zorunlu değildir.
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
        // Bir IF alanının içine yerleştirilmiş bir MERGEFIELD ekleyin.
        // IF alan ifadesi yanlış olduğundan, iç MERGEFIELD'ın sonucu görüntülenmeyecektir.
        // ve MERGEFIELD, posta birleştirme sırasında herhangi bir veri almayacaktır.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Bu bayrağı true olarak ayarlarsak, yine de yanlış ifadeli IF alanlarındaki MERGEFIELD'leri sayabiliriz.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Sonuç belgede görünmeyecektir çünkü IF alanı yanlıştır.
        // ancak iç MERGEFIELD gerçekten de veri aldı.
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
            // Hiçbir şey yapmayın.
        }
        /// <özet>
        /// Bu, posta birleştirme motorunun belgede Image:XXX birleştirme alanıyla karşılaştığında çağrılır.
        /// Bir Resim nesnesi, dosya adı veya resmi içeren bir akışı döndürme şansınız var.
        /// </özet>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Alan değeri bir bayt dizisidir, sadece onu dönüştürün ve üzerinde bir akış oluşturun.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Artık posta birleştirme motoru görüntüyü akıştan alacaktır.
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
        /// <özet>
        /// Belgede karşılaşılan her birleştirme alanı için çağrılır.
        /// Birleştirme motoruna bazı veriler döndürebiliriz veya belgeyle başka bir şey yapabiliriz.
        /// Bu durumda hücre biçimlendirmesini değiştiriyoruz.
        /// </özet>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Satır numarasının çift veya tek olmasına göre rengi seçin.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Şu anda tüm satır için hücre özelliklerini ayarlamanın bir yolu yok, bu yüzden satırdaki tüm hücreler üzerinde yineleme yapmamız gerekiyor.
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
            // Hiçbir şey yapmayın.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <özet>
    /// Değer tek ise true, çift ise false döndürür.
    /// </özet>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <özet>
    /// DataTable'ı oluşturup içini verilerle doldur.
    /// Gerçek hayatta bu DataTable'ın bir veritabanından doldurulması gerekir.
    /// </özet>
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

## 6. Sonuç

Tebrikler! Aspose.Words for Java'da Word belgelerini dinamik olarak düzenlemek için alanları nasıl kullanacağınızı öğrendiniz. Bu güçlü API, belgeleriniz üzerinde tam kontrol sağlayarak onu Java geliştiricileri için değerli bir varlık haline getirir.

## 7. SSS

### S1: Aspose.Words for Java'yı nereden indirebilirim?
Java için Aspose.Words'ü şu adresten indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/).

### S2: Aspose.Words for Java için geçici lisansı nasıl alabilirim?
Geçici lisansı şuradan alabilirsiniz: [Burada](https://purchase.aspose.com/temporary-license/).

### S3: Java için Aspose.Words desteğini nereden alabilirim?
Destek için Aspose.Words forumunu ziyaret edebilirsiniz [Burada](https://forum.aspose.com/).

### S4: Aspose.Words for Java, Word belgelerindeki HTML içeriğini işlemek için uygun mudur?
Evet, Aspose.Words for Java, Word belgelerindeki HTML içeriğinin işlenmesi için mükemmel destek sağlar.

### S5: Aspose.Words for Java'yı ücretsiz kullanabilir miyim?
Aspose.Words for Java ticari bir üründür, ancak ücretsiz deneme sürümüyle özelliklerini keşfedebilirsiniz [Burada](https://releases.aspose.com/).

Bugün Aspose.Words for Java'yı kullanmaya başlayın ve Word belgelerinizin kontrolünü daha önce hiç olmadığı kadar ele alın!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}