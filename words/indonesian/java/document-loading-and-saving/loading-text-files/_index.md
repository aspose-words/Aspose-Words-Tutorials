---
"description": "Buka Kekuatan Aspose.Words untuk Java. Pelajari Cara Memuat Dokumen Teks, Mengelola Daftar, Menangani Spasi, dan Mengontrol Arah Teks."
"linktitle": "Memuat File Teks dengan"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Memuat File Teks dengan Aspose.Words untuk Java"
"url": "/id/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Memuat File Teks dengan Aspose.Words untuk Java


## Pengantar Memuat File Teks dengan Aspose.Words untuk Java

Dalam panduan ini, kita akan membahas cara memuat berkas teks menggunakan Aspose.Words untuk Java dan memanipulasinya sebagai dokumen Word. Kita akan membahas berbagai aspek seperti mendeteksi daftar, menangani spasi, dan mengendalikan arah teks.

## Langkah 1: Mendeteksi Daftar

Untuk memuat dokumen teks dan mendeteksi daftar, Anda dapat mengikuti langkah-langkah berikut:

```java
// Buat dokumen teks biasa dalam bentuk string dengan bagian-bagian yang dapat ditafsirkan sebagai daftar.
// Saat dimuat, tiga daftar pertama akan selalu terdeteksi oleh Aspose.Words,
// dan objek Daftar akan dibuat untuknya setelah dimuat.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// Daftar keempat, dengan spasi di antara nomor daftar dan isi item daftar,
// hanya akan terdeteksi sebagai daftar jika "DetectNumberingWithWhitespaces" dalam objek LoadOptions diatur ke benar,
// untuk menghindari paragraf yang dimulai dengan angka salah terdeteksi sebagai daftar.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Muat dokumen sambil menerapkan LoadOptions sebagai parameter dan verifikasi hasilnya.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Kode ini menunjukkan cara memuat dokumen teks dengan berbagai format daftar dan menggunakan `DetectNumberingWithWhitespaces` opsi untuk mendeteksi daftar dengan benar.

## Langkah 2: Menangani Opsi Spasi

Untuk mengontrol spasi di awal dan akhir saat memuat dokumen teks, Anda dapat menggunakan kode berikut:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

Dalam contoh ini, kami memuat dokumen teks dan memangkas spasi awal dan akhir menggunakan `TxtLeadingSpacesOptions.TRIM` Dan `TxtTrailingSpacesOptions.TRIM`.

## Langkah 3: Mengontrol Arah Teks

Untuk menentukan arah teks saat memuat dokumen teks, Anda dapat menggunakan kode berikut:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Kode ini mengatur arah dokumen ke deteksi otomatis (`DocumentDirection.AUTO`) dan memuat dokumen teks dengan teks Ibrani. Anda dapat menyesuaikan arah dokumen sesuai kebutuhan.

## Kode Sumber Lengkap Untuk Memuat File Teks dengan Aspose.Words untuk Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Buat dokumen teks biasa dalam bentuk string dengan bagian-bagian yang dapat ditafsirkan sebagai daftar.
	// Saat dimuat, tiga daftar pertama akan selalu terdeteksi oleh Aspose.Words,
	// dan objek Daftar akan dibuat untuknya setelah dimuat.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Daftar keempat, dengan spasi di antara nomor daftar dan isi item daftar,
	// hanya akan terdeteksi sebagai daftar jika "DetectNumberingWithWhitespaces" dalam objek LoadOptions diatur ke benar,
	// untuk menghindari paragraf yang dimulai dengan angka salah terdeteksi sebagai daftar.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Muat dokumen sambil menerapkan LoadOptions sebagai parameter dan verifikasi hasilnya.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Kesimpulan

Dalam panduan ini, kami telah mempelajari cara memuat berkas teks menggunakan Aspose.Words untuk Java, mendeteksi daftar, menangani spasi, dan mengontrol arah teks. Teknik-teknik ini memungkinkan Anda untuk memanipulasi dokumen teks secara efektif dalam aplikasi Java Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk Java?

Aspose.Words untuk Java adalah pustaka pemrosesan dokumen canggih yang memungkinkan pengembang membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram dalam aplikasi Java. Pustaka ini menyediakan berbagai fitur untuk bekerja dengan teks, tabel, gambar, dan elemen dokumen lainnya.

### Bagaimana saya bisa memulai dengan Aspose.Words untuk Java?

Untuk memulai Aspose.Words untuk Java, ikuti langkah-langkah berikut:
1. Unduh dan instal pustaka Aspose.Words untuk Java.
2. Lihat dokumentasi di [Referensi API Aspose.Words untuk Java](https://reference.aspose.com/words/java/) untuk informasi dan contoh terperinci.
3. Jelajahi contoh kode dan tutorial untuk mempelajari cara menggunakan pustaka secara efektif.

### Bagaimana cara memuat dokumen teks menggunakan Aspose.Words untuk Java?

Untuk memuat dokumen teks menggunakan Aspose.Words untuk Java, Anda dapat menggunakan `TxtLoadOptions` kelas dan `Document` kelas. Pastikan Anda menentukan opsi yang tepat untuk menangani spasi dan arah teks sesuai kebutuhan. Lihat panduan langkah demi langkah dalam artikel ini untuk contoh terperinci.

### Bisakah saya mengonversi dokumen teks yang dimuat ke format lain?

Ya, Aspose.Words untuk Java memungkinkan Anda mengonversi dokumen teks yang dimuat ke berbagai format, termasuk DOCX, PDF, dan lainnya. Anda dapat menggunakan `Document` kelas untuk melakukan konversi. Periksa dokumentasi untuk contoh konversi tertentu.

### Bagaimana cara menangani spasi dalam dokumen teks yang dimuat?

Anda dapat mengontrol bagaimana spasi di awal dan akhir ditangani dalam dokumen teks yang dimuat menggunakan `TxtLoadOptions`Opsi seperti `TxtLeadingSpacesOptions` Dan `TxtTrailingSpacesOptions` memungkinkan Anda memangkas atau mempertahankan spasi sesuai kebutuhan. Lihat bagian "Menangani Opsi Spasi" dalam panduan ini untuk contohnya.

### Apa pentingnya arah teks dalam Aspose.Words untuk Java?

Arah teks sangat penting untuk dokumen yang berisi skrip atau bahasa campuran, seperti bahasa Ibrani atau Arab. Aspose.Words untuk Java menyediakan opsi untuk menentukan arah teks, memastikan rendering dan format teks yang tepat dalam bahasa ini. Bagian "Mengontrol Arah Teks" dalam panduan ini menunjukkan cara mengatur arah teks.

### Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan untuk Aspose.Words untuk Java?

Untuk sumber daya, dokumentasi, dan dukungan tambahan, kunjungi [Dokumentasi Aspose.Words untuk Java](https://reference.aspose.com/words/java/)Anda juga dapat berpartisipasi dalam forum komunitas Aspose.Words atau menghubungi dukungan Aspose untuk mendapatkan bantuan terkait masalah atau pertanyaan tertentu.

### Apakah Aspose.Words untuk Java cocok untuk proyek komersial?

Ya, Aspose.Words untuk Java cocok untuk proyek pribadi dan komersial. Aplikasi ini menawarkan opsi lisensi untuk mengakomodasi berbagai skenario penggunaan. Pastikan untuk meninjau ketentuan lisensi dan harga di situs web Aspose untuk memilih lisensi yang sesuai untuk proyek Anda.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}