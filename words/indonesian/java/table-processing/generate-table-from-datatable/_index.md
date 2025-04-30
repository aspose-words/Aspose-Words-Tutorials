---
"description": "Pelajari cara membuat tabel dari DataTable menggunakan Aspose.Words untuk Java. Buat dokumen Word profesional dengan tabel yang diformat dengan mudah."
"linktitle": "Hasilkan Tabel dari Datatable"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Hasilkan Tabel dari Datatable"
"url": "/id/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hasilkan Tabel dari Datatable

## Perkenalan

Membuat tabel secara dinamis dari sumber data merupakan tugas umum dalam banyak aplikasi. Baik Anda membuat laporan, faktur, atau ringkasan data, kemampuan mengisi tabel dengan data secara terprogram dapat menghemat banyak waktu dan tenaga. Dalam tutorial ini, kita akan membahas cara membuat tabel dari DataTable menggunakan Aspose.Words untuk Java. Kita akan membagi proses menjadi beberapa langkah yang dapat dikelola, memastikan Anda memiliki pemahaman yang jelas tentang setiap bagian.

## Prasyarat

Sebelum menyelami kodenya, mari pastikan Anda memiliki semua yang dibutuhkan untuk memulai:

1. Java Development Kit (JDK): Pastikan Anda telah menginstal JDK di komputer Anda. Anda dapat mengunduhnya dari [Situs web Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Aspose.Words untuk Java: Anda memerlukan pustaka Aspose.Words. Anda dapat mengunduh versi terbaru dari [Halaman rilis Aspose](https://releases.aspose.com/words/java/).

3. IDE: Lingkungan Pengembangan Terpadu (IDE) seperti IntelliJ IDEA atau Eclipse akan membuat pengkodean lebih mudah.

4. Pengetahuan Dasar Java: Keakraban dengan konsep pemrograman Java akan membantu Anda memahami potongan kode dengan lebih baik.

5. Contoh Data: Untuk tutorial ini, kita akan menggunakan file XML bernama "List of people.xml" untuk mensimulasikan sumber data. Anda dapat membuat file ini dengan contoh data untuk pengujian.

## Langkah 1: Buat Dokumen Baru

Pertama, kita perlu membuat dokumen baru tempat tabel akan berada. Ini adalah kanvas untuk pekerjaan kita.

```java
Document doc = new Document();
```

Di sini, kita membuat instance baru `Document` objek. Ini akan berfungsi sebagai dokumen kerja tempat kita akan membuat tabel.

## Langkah 2: Inisialisasi DocumentBuilder

Selanjutnya kita akan menggunakan `DocumentBuilder` kelas, yang memungkinkan kita memanipulasi dokumen dengan lebih mudah.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itu `DocumentBuilder` Objek menyediakan metode untuk menyisipkan tabel, teks, dan elemen lain ke dalam dokumen.

## Langkah 3: Mengatur Orientasi Halaman

Karena kita mengharapkan tabel kita lebar, kita akan mengatur orientasi halaman ke lanskap.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Langkah ini krusial karena memastikan tabel kita pas di halaman tanpa terpotong.

## Langkah 4: Memuat Data dari XML

Sekarang, kita perlu memuat data kita dari file XML ke dalam `DataTable`Dari sinilah data kami berasal.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

Di sini, kita membaca file XML dan mengambil tabel pertama dari dataset. Ini `DataTable` akan menampung data yang ingin kita tampilkan dalam dokumen kita.

## Langkah 5: Impor Tabel dari DataTable

Sekarang tibalah bagian yang menarik: mengimpor data kita ke dalam dokumen sebagai tabel.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

Kami menyebut metode tersebut `importTableFromDataTable`, melewati `DocumentBuilder`, kita `DataTable`, dan boolean untuk menunjukkan apakah akan menyertakan judul kolom.

## Langkah 6: Tata Gaya Tabel

Setelah kita memiliki meja, kita dapat menerapkan beberapa gaya untuk membuatnya tampak bagus.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Kode ini menerapkan gaya yang telah ditetapkan pada tabel, meningkatkan daya tarik visual dan keterbacaannya.

## Langkah 7: Hapus Sel yang Tidak Diinginkan

Jika Anda memiliki kolom yang tidak ingin ditampilkan, seperti kolom gambar, Anda dapat menghapusnya dengan mudah.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Langkah ini memastikan bahwa tabel kita hanya menampilkan informasi yang relevan.

## Langkah 8: Simpan Dokumen

Terakhir, kita simpan dokumen kita dengan tabel yang dihasilkan.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Baris ini menyimpan dokumen dalam direktori yang ditentukan, sehingga Anda dapat meninjau hasilnya.

## Metode importTableFromDataTable

Mari kita lihat lebih dekat `importTableFromDataTable` metode. Metode ini bertanggung jawab untuk membuat struktur tabel dan mengisinya dengan data.

### Langkah 1: Mulai Tabel

Pertama, kita perlu memulai tabel baru dalam dokumen.

```java
Table table = builder.startTable();
```

Ini menginisialisasi tabel baru dalam dokumen kita.

### Langkah 2: Tambahkan Judul Kolom

Jika kita ingin memasukkan judul kolom, kita centang `importColumnHeadings` bendera.

```java
if (importColumnHeadings) {
    // Simpan format asli
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Mengatur format judul
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Masukkan nama kolom
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Mengembalikan format asli
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

Blok kode ini memformat baris judul dan memasukkan nama kolom dari `DataTable`.

### Langkah 3: Isi Tabel dengan Data

Sekarang, kita mengulang setiap baris `DataTable` untuk memasukkan data ke dalam tabel.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

Di bagian ini, kami menangani berbagai tipe data, memformat tanggal dengan tepat sambil memasukkan data lain sebagai teks.

### Langkah 4: Akhiri Tabel

Terakhir, kita selesaikan tabel setelah semua data dimasukkan.

```java
builder.endTable();
```

Baris ini menandai akhir tabel kita, yang memungkinkan `DocumentBuilder` untuk mengetahui bahwa kita telah selesai dengan bagian ini.

## Kesimpulan

Nah, itu dia! Anda telah berhasil mempelajari cara membuat tabel dari DataTable menggunakan Aspose.Words untuk Java. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah membuat tabel dinamis dalam dokumen Anda berdasarkan berbagai sumber data. Baik Anda membuat laporan atau faktur, metode ini akan menyederhanakan alur kerja Anda dan menyempurnakan proses pembuatan dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk Java?
Aspose.Words untuk Java adalah pustaka yang hebat untuk membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram.

### Bisakah saya menggunakan Aspose.Words secara gratis?
Ya, Aspose menawarkan versi uji coba gratis. Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/).

### Bagaimana cara menata tabel di Aspose.Words?
Anda dapat menerapkan gaya menggunakan pengenal gaya dan opsi yang telah ditentukan sebelumnya yang disediakan oleh perpustakaan.

### Tipe data apa yang dapat saya masukkan ke dalam tabel?
Anda dapat memasukkan berbagai jenis data, termasuk teks, angka, dan tanggal, yang dapat diformat sesuai kebutuhan.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Words?
Anda dapat menemukan dukungan dan mengajukan pertanyaan di [Forum Aspose](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}