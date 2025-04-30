---
"description": "Pelajari cara menggunakan daftar di Aspose.Words untuk Java dengan tutorial langkah demi langkah ini. Atur dan format dokumen Anda secara efektif."
"linktitle": "Menggunakan Daftar"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggunakan Daftar di Aspose.Words untuk Java"
"url": "/id/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Daftar di Aspose.Words untuk Java


Dalam tutorial komprehensif ini, kita akan menjelajahi cara menggunakan daftar secara efektif di Aspose.Words untuk Java, API yang hebat untuk bekerja dengan dokumen Microsoft Word secara terprogram. Daftar sangat penting untuk menyusun dan mengatur konten dalam dokumen Anda. Kita akan membahas dua aspek utama dalam bekerja dengan daftar: memulai ulang daftar di setiap bagian dan menentukan level daftar. Mari kita mulai!

## Pengantar Aspose.Words untuk Java

Sebelum kita mulai bekerja dengan daftar, mari kita kenali Aspose.Words untuk Java. API ini menyediakan alat bagi pengembang untuk membuat, memodifikasi, dan memanipulasi dokumen Word dalam lingkungan Java. Ini adalah solusi serbaguna untuk berbagai tugas mulai dari pembuatan dokumen sederhana hingga pemformatan dan manajemen konten yang rumit.

### Menyiapkan Lingkungan Anda

Untuk memulai, pastikan Anda telah menginstal dan mengatur Aspose.Words untuk Java di lingkungan pengembangan Anda. Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/java/). 

## Memulai Ulang Daftar di Setiap Bagian

Dalam banyak skenario, Anda mungkin perlu memulai ulang daftar di setiap bagian dokumen Anda. Ini dapat berguna untuk membuat dokumen terstruktur dengan beberapa bagian, seperti laporan, manual, atau makalah akademis.

Berikut panduan langkah demi langkah tentang cara mencapainya menggunakan Aspose.Words untuk Java:

### Inisialisasi Dokumen Anda: 
Mulailah dengan membuat objek dokumen baru.

```java
Document doc = new Document();
```

### Tambahkan Daftar Bernomor: 
Tambahkan daftar bernomor ke dokumen Anda. Kami akan menggunakan gaya penomoran default.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Konfigurasikan Pengaturan Daftar: 
\Aktifkan daftar untuk memulai ulang di setiap bagian.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Pengaturan DocumentBuilder: 
Buat DocumentBuilder untuk menambahkan konten ke dokumen Anda.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Tambahkan Item Daftar: 
Gunakan loop untuk menambahkan item daftar ke dokumen Anda. Kami akan menyisipkan pemisah bagian setelah item ke-15.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Simpan Dokumen Anda: 
Simpan dokumen dengan opsi yang diinginkan.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Dengan mengikuti langkah-langkah ini, Anda dapat membuat dokumen dengan daftar yang dimulai ulang di setiap bagian, mempertahankan struktur konten yang jelas dan terorganisir.

## Menentukan Tingkat Daftar

Aspose.Words untuk Java memungkinkan Anda menentukan level daftar, yang khususnya berguna saat Anda memerlukan format daftar yang berbeda dalam dokumen Anda. Mari kita bahas cara melakukannya:

### Inisialisasi Dokumen Anda: 
Buat objek dokumen baru.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Buat Daftar Bernomor: 
Terapkan templat daftar bernomor dari Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Tentukan Tingkat Daftar: 
Ulangi melalui berbagai tingkat daftar dan tambahkan konten.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Buat Daftar Berpoin: 
Sekarang, mari membuat daftar berpoin.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Tentukan Tingkat Daftar Berpoin: 
Mirip dengan daftar bernomor, tentukan level dan tambahkan konten.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Pemformatan Daftar Berhenti: 
Untuk menghentikan pemformatan daftar, atur daftar ke null.

```java
builder.getListFormat().setList(null);
```

### Simpan Dokumen Anda: 
Simpan dokumen.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Dengan mengikuti langkah-langkah ini, Anda dapat membuat dokumen dengan tingkat daftar kustom, yang memungkinkan Anda mengontrol pemformatan daftar dalam dokumen Anda.

## Kode Sumber Lengkap
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection akan ditulis hanya jika kepatuhan lebih tinggi dari OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Buat daftar bernomor berdasarkan salah satu templat daftar Microsoft Word
        // dan menerapkannya pada paragraf pembuat dokumen saat ini.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Ada sembilan level dalam daftar ini, mari kita coba semuanya.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Buat daftar berpoin berdasarkan salah satu templat daftar Microsoft Word
        // dan menerapkannya pada paragraf pembuat dokumen saat ini.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Ini adalah cara untuk menghentikan pemformatan daftar.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Buat daftar berdasarkan templat.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Untuk menggunakan kembali daftar pertama, kita perlu memulai ulang penomoran dengan membuat salinan format daftar asli.
        List list2 = doc.getLists().addCopy(list1);
        // Kita dapat mengubah daftar baru dengan cara apa pun, termasuk menetapkan nomor awal baru.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Kesimpulan

Selamat! Anda telah mempelajari cara bekerja dengan daftar di Aspose.Words untuk Java secara efektif. Daftar sangat penting untuk mengatur dan menyajikan konten dalam dokumen Anda. Apakah Anda perlu memulai ulang daftar di setiap bagian atau menentukan tingkat daftar, Aspose.Words untuk Java menyediakan alat yang Anda butuhkan untuk membuat dokumen yang tampak profesional.

Sekarang Anda dapat dengan yakin menggunakan fitur-fitur ini untuk meningkatkan tugas pembuatan dan pemformatan dokumen Anda. Jika Anda memiliki pertanyaan atau memerlukan bantuan lebih lanjut, jangan ragu untuk menghubungi [Forum komunitas Aspose](https://forum.aspose.com/) untuk dukungan.

## Tanya Jawab Umum

### Bagaimana cara menginstal Aspose.Words untuk Java?
Anda dapat mengunduh Aspose.Words untuk Java dari [Di Sini](https://releases.aspose.com/words/java/) dan ikuti petunjuk instalasi dalam dokumentasi.

### Bisakah saya menyesuaikan format penomoran daftar?
Ya, Aspose.Words untuk Java menyediakan opsi yang luas untuk menyesuaikan format penomoran daftar. Anda dapat merujuk ke dokumentasi API untuk detailnya.

### Apakah Aspose.Words untuk Java kompatibel dengan standar dokumen Word terbaru?
Ya, Anda dapat mengonfigurasi Aspose.Words untuk Java agar mematuhi berbagai standar dokumen Word, termasuk ISO 29500.

### Bisakah saya membuat dokumen kompleks dengan tabel dan gambar menggunakan Aspose.Words untuk Java?
Tentu saja! Aspose.Words untuk Java mendukung pemformatan dokumen tingkat lanjut, termasuk tabel, gambar, dan banyak lagi. Periksa dokumentasi untuk contoh.

### Di mana saya bisa mendapatkan lisensi sementara untuk Aspose.Words untuk Java?
Anda bisa mendapatkan lisensi sementara [Di Sini](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}