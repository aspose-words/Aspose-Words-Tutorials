---
"description": "Pelajari cara menggunakan objek OLE dan kontrol ActiveX di Aspose.Words untuk Java. Buat dokumen interaktif dengan mudah. Mulailah sekarang!"
"linktitle": "Menggunakan Objek OLE dan Kontrol ActiveX"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggunakan Objek OLE dan Kontrol ActiveX di Aspose.Words untuk Java"
"url": "/id/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Objek OLE dan Kontrol ActiveX di Aspose.Words untuk Java

Dalam tutorial ini, kita akan menjelajahi cara bekerja dengan objek OLE (Object Linking and Embedding) dan kontrol ActiveX di Aspose.Words untuk Java. Objek OLE dan kontrol ActiveX adalah alat canggih yang memungkinkan Anda menyempurnakan dokumen dengan menyematkan atau menautkan konten eksternal, seperti spreadsheet, file multimedia, atau kontrol interaktif. Ikuti terus saat kami mempelajari contoh kode dan mempelajari cara menggunakan fitur-fitur ini secara efektif.

### Prasyarat

Sebelum kita memulai, pastikan Anda memiliki prasyarat berikut:

1. Aspose.Words untuk Java: Pastikan Anda telah menginstal pustaka Aspose.Words di proyek Java Anda. Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/java/).

2. Lingkungan Pengembangan Java: Anda harus memiliki lingkungan pengembangan Java yang berfungsi pada sistem Anda.

### Memasukkan Objek OLE

Mari kita mulai dengan memasukkan objek OLE ke dalam dokumen Word. Kita akan membuat dokumen Word sederhana lalu memasukkan objek OLE yang mewakili halaman web.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", benar, benar, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Dalam kode ini, kita membuat dokumen baru dan menyisipkan objek OLE yang menampilkan situs web Aspose. Anda dapat mengganti URL dengan konten yang diinginkan.

### Memasukkan Objek OLE dengan OlePackage

Selanjutnya, mari kita jelajahi cara menyisipkan objek OLE menggunakan OlePackage. Ini memungkinkan Anda untuk menyematkan file eksternal sebagai objek OLE dalam dokumen Anda.

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

Dalam contoh ini, kami menyisipkan objek OLE menggunakan OlePackage, yang memungkinkan Anda menyertakan file eksternal sebagai objek tertanam.

### Memasukkan Objek OLE sebagai Ikon

Sekarang, mari kita lihat cara menyisipkan objek OLE sebagai ikon. Ini berguna saat Anda ingin menampilkan ikon yang mewakili berkas yang disematkan.

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

Dalam kode ini, kami menyisipkan objek OLE sebagai ikon, memberikan representasi konten yang disematkan secara lebih menarik secara visual.

### Membaca Properti Kontrol ActiveX

Sekarang, mari kita alihkan fokus kita ke kontrol ActiveX. Kita akan mempelajari cara membaca properti kontrol ActiveX dalam dokumen Word.

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

Dalam kode ini, kami mengulangi bentuk dalam dokumen Word, mengidentifikasi kontrol ActiveX, dan mengambil propertinya.

### Kesimpulan

Selamat! Anda telah mempelajari cara bekerja dengan objek OLE dan kontrol ActiveX di Aspose.Words untuk Java. Fitur-fitur ini membuka banyak kemungkinan untuk membuat dokumen yang dinamis dan interaktif.

### Tanya Jawab Umum

### Apa tujuan objek OLE dalam dokumen Word? 
   - Objek OLE memungkinkan Anda menyematkan atau menautkan konten eksternal, seperti file atau halaman web, dalam dokumen Word.

### Dapatkah saya menyesuaikan tampilan objek OLE dalam dokumen saya? 
   - Ya, Anda dapat menyesuaikan tampilan objek OLE, termasuk mengatur ikon dan nama file.

### Apa itu kontrol ActiveX, dan bagaimana kontrol tersebut dapat menyempurnakan dokumen saya? 
   - Kontrol ActiveX adalah elemen interaktif yang dapat menambahkan fungsionalitas ke dokumen Word Anda, seperti kontrol formulir atau pemutar multimedia.

### Apakah Aspose.Words untuk Java cocok untuk otomatisasi dokumen tingkat perusahaan? 
   - Ya, Aspose.Words untuk Java adalah pustaka yang hebat untuk mengotomatiskan pembuatan dan manipulasi dokumen dalam aplikasi Java.

### Di mana saya bisa mendapatkan akses ke Aspose.Words untuk Java? 
   - Anda dapat mengunduh Aspose.Words untuk Java dari [Di Sini](https://releases.aspose.com/words/java/).

Mulailah dengan Aspose.Words untuk Java hari ini dan dapatkan potensi penuh otomatisasi dan penyesuaian dokumen!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}