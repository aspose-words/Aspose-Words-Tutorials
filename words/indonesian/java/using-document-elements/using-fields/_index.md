---
"description": "Pelajari cara menggunakan Aspose.Words untuk bidang Java secara efektif dalam tutorial langkah demi langkah ini. Buat dokumen Word yang dinamis dengan mudah."
"linktitle": "Menggunakan Fields"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggunakan Fields di Aspose.Words untuk Java"
"url": "/id/java/using-document-elements/using-fields/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Fields di Aspose.Words untuk Java


Dalam tutorial langkah demi langkah ini, kami akan memandu Anda tentang cara menggunakan kolom di Aspose.Words untuk Java untuk memanipulasi dokumen dengan mudah. Aspose.Words untuk Java adalah API canggih yang memungkinkan Anda bekerja dengan dokumen Word secara terprogram, memberi Anda kendali penuh atas konten dan formatnya.

## 1. Pendahuluan

Aspose.Words untuk Java adalah alat penting bagi siapa saja yang menangani dokumen Word dalam aplikasi Java. Kolom adalah tempat penampung yang dapat menyimpan data dinamis dalam dokumen Anda. Tutorial ini akan menunjukkan kepada Anda cara bekerja dengan kolom secara efektif.

## 2. Menyiapkan Lingkungan Anda

Sebelum memulai, pastikan Anda telah menginstal Aspose.Words untuk Java. Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/java/)Pastikan juga Anda telah menginstal Java dan lingkungan pengembangan terintegrasi (IDE) seperti Eclipse atau IntelliJ IDEA di sistem Anda.

## 3. Memuat Dokumen Word

Dalam aplikasi Java Anda, Anda perlu memuat dokumen Word yang ingin Anda gunakan. Berikut ini cuplikan kode untuk membantu Anda memulai:

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
```

Mengganti `"Your Document Directory"` Dan `"Your Output Directory"` dengan jalur yang sesuai.

## 4. Menyesuaikan Gabungan Surat

Aspose.Words untuk Java menyediakan dukungan yang sangat baik untuk operasi gabungan surat. Anda dapat menyesuaikan proses gabungan surat dengan menyiapkan pengendali peristiwa gabungan surat. Berikut cara melakukannya:

```java
// Siapkan penangan peristiwa gabungan surat untuk melakukan pekerjaan kustom.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());

// Pangkas nilai gabungan surat spasi kosong di awal dan akhir.
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

## 5. Menyimpan Dokumen

Setelah menyesuaikan dokumen Anda, Anda dapat menyimpannya menggunakan kode berikut:

```java
doc.save(outPath + "WorkingWithFields.MailMergeFormFields.docx");
```

Mengganti `"Your Output Directory"` dengan jalur keluaran yang diinginkan.

## Kode Sumber Lengkap
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Mail merge destinations - Fax.docx");
// Siapkan penangan peristiwa gabungan surat untuk melakukan pekerjaan kustom.
doc.getMailMerge().setFieldMergingCallback(new HandleMergeField());
// Pangkas nilai gabungan surat spasi kosong di awal dan akhir.
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
Kode sumber Kelas HandleMergeField

```java
    private static class HandleMergeField implements IFieldMergingCallback
    {
        /// <ringkasan>
        /// Penanganan ini dipanggil untuk setiap bidang gabungan surat yang ditemukan dalam dokumen,
        /// untuk setiap catatan yang ditemukan dalam sumber data.
        /// </ringkasan>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e) throws Exception
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            // Kami memutuskan bahwa kami ingin semua nilai boolean dikeluarkan sebagai bidang formulir kotak centang.
            if (e.getFieldValue() instanceof /*Bahasa Inggris Boolean*/Boolean)
            {
                // Pindahkan "kursor" ke bidang gabungan saat ini.
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
            //  Implementasi tidak diperlukan.
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
        // Sisipkan MERGEFIELD yang bersarang di dalam kolom IF.
        // Karena pernyataan bidang IF salah, hasil MERGEFIELD bagian dalam tidak akan ditampilkan,
        // dan MERGEFIELD tidak akan menerima data apa pun selama penggabungan surat.
        FieldIf fieldIf = (FieldIf)builder.insertField(" IF 1 = 2 ");
        builder.moveTo(fieldIf.getSeparator());
        builder.insertField(" MERGEFIELD  FullName ");
        // Kita masih dapat menghitung MERGEFIELD di dalam bidang IF pernyataan salah jika kita menetapkan tanda ini ke benar.
        doc.getMailMerge().setUnconditionalMergeFieldsAndRegions(true);
        DataTable dataTable = new DataTable();
        dataTable.getColumns().add("FullName");
        dataTable.getRows().add("James Bond");
        doc.getMailMerge().execute(dataTable);
        // Hasilnya tidak akan terlihat dalam dokumen karena kolom IF salah,
        // tetapi MERGEFIELD bagian dalam memang menerima data.
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
            // Tidak melakukan apa pun.
        }
        /// <ringkasan>
        /// Ini dipanggil saat mesin gabungan surat menemukan bidang gabungan Gambar:XXX dalam dokumen.
        /// Anda memiliki kesempatan untuk mengembalikan objek Gambar, nama berkas, atau aliran yang berisi gambar.
        /// </ringkasan>
        public void /*IFieldMergingCallback.*/imageFieldMerging(ImageFieldMergingArgs e) throws Exception
        {
            // Nilai bidang merupakan array byte, masukkan saja dan buat aliran di atasnya.
            ByteArrayInputStream imageStream = new ByteArrayInputStream((byte[]) e.getFieldValue());
            // Kini mesin gabungan surat akan mengambil gambar dari aliran.
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
        /// <ringkasan>
        /// Dipanggil untuk setiap bidang gabungan yang ditemukan dalam dokumen.
        /// Kita dapat mengembalikan beberapa data ke mesin gabungan surat atau melakukan hal lain dengan dokumen tersebut.
        /// Dalam kasus ini kita memodifikasi format sel.
        /// </ringkasan>
        public void /*IFieldMergingCallback.*/fieldMerging(FieldMergingArgs e)
        {
            if (mBuilder == null)
                mBuilder = new DocumentBuilder(e.getDocument());
            if ("CompanyName".equals(e.getFieldName()))
            {
                // Pilih warna tergantung pada apakah nomor baris genap atau ganjil.
                Color rowColor = isOdd(mRowIdx) 
                    ? new Color((213), (227), (235)) 
                    : new Color((242), (242), (242));
                // Saat ini tidak ada cara untuk menetapkan properti sel untuk seluruh baris, jadi kami harus mengulangi semua sel di baris tersebut.
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
            // Tidak melakukan apa pun.
        }
        private DocumentBuilder mBuilder;
        private int mRowIdx;
    }
    /// <ringkasan>
    /// Mengembalikan true jika nilainya ganjil; false jika nilainya genap.
    /// </ringkasan>
    private static boolean isOdd(int value)
    {
        return (value / 2 * 2) == value;
    }
    /// <ringkasan>
    /// Buat DataTable dan isi dengan data.
    /// Dalam kehidupan nyata DataTable ini seharusnya diisi dari database.
    /// </ringkasan>
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

## 6. Kesimpulan

Selamat! Anda telah mempelajari cara menggunakan kolom di Aspose.Words untuk Java guna memanipulasi dokumen Word secara dinamis. API canggih ini memberi Anda kendali penuh atas dokumen Anda, menjadikannya aset berharga bagi pengembang Java.

## 7. Tanya Jawab Umum

### Q1: Di mana saya dapat mengunduh Aspose.Words untuk Java?
Anda dapat mengunduh Aspose.Words untuk Java dari [Di Sini](https://releases.aspose.com/words/java/).

### Q2: Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words untuk Java?
Anda dapat memperoleh lisensi sementara dari [Di Sini](https://purchase.aspose.com/temporary-license/).

### Q3: Di mana saya bisa mendapatkan dukungan untuk Aspose.Words untuk Java?
Untuk dukungan, Anda dapat mengunjungi forum Aspose.Words [Di Sini](https://forum.aspose.com/).

### Q4: Apakah Aspose.Words untuk Java cocok untuk menangani konten HTML dalam dokumen Word?
Ya, Aspose.Words untuk Java menyediakan dukungan luar biasa untuk menangani konten HTML dalam dokumen Word.

### Q5: Dapatkah saya menggunakan Aspose.Words untuk Java secara gratis?
Aspose.Words untuk Java adalah produk komersial, tetapi Anda dapat menjelajahi fiturnya dengan uji coba gratis yang tersedia [Di Sini](https://releases.aspose.com/).

Mulailah dengan Aspose.Words untuk Java hari ini dan kendalikan dokumen Word Anda seperti belum pernah sebelumnya!




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}