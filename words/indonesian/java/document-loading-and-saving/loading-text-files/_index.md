---
date: 2025-12-27
description: Pelajari cara mengatur arah, memuat file txt, menghapus spasi, dan mengonversi
  txt ke docx menggunakan Aspose.Words untuk Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Cara Mengatur Arah dan Memuat File Teks dengan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengatur Arah dan Memuat File Teks dengan Aspose.Words untuk Java

## Pendahuluan Memuat File Teks dengan Aspose.Words untuk Java

Dalam panduan ini, Anda akan menemukan **cara mengatur arah** saat memuat dokumen teks biasa dan melihat cara praktis untuk **memuat txt**, **memangkas spasi**, serta **mengonversi txt ke docx** menggunakan Aspose.Words untuk Java. Baik Anda sedang membangun layanan konversi dokumen atau memerlukan kontrol detail atas deteksi daftar, tutorial ini memandu Anda melalui setiap langkah dengan penjelasan yang jelas dan kode siap‑jalankan.

## Jawaban Cepat
- **Bagaimana cara mengatur arah teks untuk file TXT yang dimuat?** Gunakan `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` atau tentukan `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Apakah Aspose.Words dapat mendeteksi daftar bernomor dalam teks biasa?** Ya – aktifkan `DetectNumberingWithWhitespaces` pada `TxtLoadOptions`.
- **Bagaimana cara memangkas spasi di awal dan akhir?** Atur `TxtLeadingSpacesOptions.TRIM` dan `TxtTrailingSpacesOptions.TRIM`.
- **Apakah mungkin mengonversi file TXT ke DOCX dalam satu baris?** Muat TXT dengan `TxtLoadOptions` dan panggil `Document.save("output.docx")`.
- **Versi Java apa yang diperlukan?** Java 8+ sudah cukup untuk Aspose.Words 24.x.

## Apa itu “cara mengatur arah” di Aspose.Words?
Ketika file teks berisi skrip kanan‑ke‑kiri (misalnya Ibrani atau Arab), perpustakaan harus mengetahui urutan bacanya. Enum `DocumentDirection` memungkinkan Anda **mengatur arah** secara manual atau membiarkan Aspose mendeteksinya secara otomatis, sehingga tata letak dan format bidi menjadi tepat.

## Mengapa menggunakan Aspose.Words untuk memuat file TXT?
- **Deteksi daftar yang akurat** – menangani daftar bernomor, berpoin, dan daftar yang dipisahkan spasi.
- **Penanganan spasi yang detail** – memangkas atau mempertahankan spasi di awal/akhir.
- **Deteksi arah teks otomatis** – sempurna untuk dokumen multibahasa.
- **Konversi satu langkah** – muat `.txt` dan simpan sebagai `.docx`, `.pdf`, atau format lain yang didukung.

## Prasyarat
- Java 8 atau lebih baru.
- Perpustakaan Aspose.Words untuk Java (tambahkan dependensi Maven/Gradle atau JAR ke proyek Anda).
- Pengetahuan dasar tentang aliran I/O Java.

## Panduan Langkah‑per‑Langkah

### Langkah 1: Mendeteksi Daftar (cara memuat txt)
Untuk memuat dokumen teks dan secara otomatis mendeteksi daftar, buat instance `TxtLoadOptions` dan aktifkan deteksi daftar. Kode di bawah menunjukkan beberapa gaya daftar dan mengaktifkan penomoran yang peka spasi.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Tip pro:** Jika Anda hanya memerlukan deteksi daftar dasar, Anda dapat melewatkan opsi spasi – Aspose tetap akan mengenali pola standar `1.` dan `1)`.

### Langkah 2: Mengatur Opsi Spasi (cara memangkas spasi)
Spasi di awal dan akhir sering menyebabkan gangguan format. Gunakan `TxtLeadingSpacesOptions` dan `TxtTrailingSpacesOptions` untuk mengontrol perilaku ini.

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

> **Mengapa penting:** Memangkas spasi mencegah indentasi yang tidak diinginkan pada DOCX yang dihasilkan, sehingga dokumen terlihat bersih tanpa pemrosesan manual tambahan.

### Langkah 3: Mengontrol Arah Teks (cara mengatur arah)
Untuk bahasa kanan‑ke‑kiri, atur arah dokumen sebelum memuat. Contoh di bawah memuat file teks Ibrani dan mencetak flag bidi untuk mengonfirmasi arah.

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

> **Kesalahan umum:** Lupa mengatur `DocumentDirection` dapat menyebabkan teks Arab/Ibrani menjadi berantakan dengan karakter muncul dalam urutan yang salah.

### Kode Sumber Lengkap untuk Memuat File Teks dengan Aspose.Words untuk Java
Berikut adalah kode lengkap yang siap‑jalankan yang menggabungkan deteksi daftar, penanganan spasi, dan kontrol arah. Anda dapat menyalin‑tempelnya ke dalam satu kelas dan menjalankan tiga metode uji secara terpisah.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Masalah Umum dan Solusinya
| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| Daftar tidak terdeteksi | `DetectNumberingWithWhitespaces` tetap `false` untuk daftar yang dipisahkan spasi | Aktifkan `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Indentasi berlebih setelah memuat | Spasi di awal dipertahankan | Atur `TxtLeadingSpacesOptions.TRIM` |
| Teks Ibrani terbalik | Arah dokumen tidak diatur atau diatur ke `LEFT_TO_RIGHT` | Gunakan `DocumentDirection.AUTO` atau `RIGHT_TO_LEFT` |
| DOCX output kosong | Aliran input tidak direset sebelum pemuatan kedua | Buat ulang `ByteArrayInputStream` untuk setiap pemanggilan load |

## Pertanyaan yang Sering Diajukan

### Q: Apa itu Aspose.Words untuk Java?
A: Aspose.Words untuk Java adalah perpustakaan pemrosesan dokumen yang kuat yang memungkinkan pengembang membuat, memanipulasi, dan mengonversi dokumen Word secara programatis dalam aplikasi Java. Ia mendukung beragam fitur, mulai dari pemuatan teks sederhana hingga format kompleks dan konversi.

### Q: Bagaimana cara memulai dengan Aspose.Words untuk Java?
A: 1. Unduh dan instal perpustakaan Aspose.Words untuk Java. 2. Lihat dokumentasi di [Referensi API Aspose.Words untuk Java](https://reference.aspose.com/words/java/) untuk informasi detail dan contoh. 3. Jelajahi kode contoh dan tutorial untuk belajar menggunakan perpustakaan secara efektif.

### Q: Bagaimana cara memuat dokumen teks menggunakan Aspose.Words untuk Java?
A: Gunakan kelas `TxtLoadOptions` bersama konstruktor `Document`. Tentukan opsi seperti deteksi daftar, penanganan spasi, atau arah teks seperti yang ditunjukkan pada bagian langkah‑per‑langkah di atas.

### Q: Bisakah saya mengonversi dokumen teks yang dimuat ke format lain?
A: Ya. Setelah memuat file TXT ke dalam objek `Document`, panggil `doc.save("output.pdf")`, `doc.save("output.docx")`, atau format lain yang didukung.

### Q: Bagaimana cara menangani spasi dalam dokumen teks yang dimuat?
A: Kendalikan spasi di awal dan akhir dengan `TxtLeadingSpacesOptions` dan `TxtTrailingSpacesOptions`. Atur ke `TRIM` untuk menghapus spasi yang tidak diinginkan, atau ke `PRESERVE` jika Anda perlu mempertahankan jarak asli.

### Q: Apa pentingnya arah teks dalam Aspose.Words untuk Java?
A: Arah teks memastikan render yang tepat untuk skrip kanan‑ke‑kiri (Ibrani, Arab, dll.). Dengan mengatur `DocumentDirection`, Anda menjamin teks bidi ditampilkan dengan benar dalam dokumen hasil.

### Q: Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan untuk Aspose.Words untuk Java?
A: Kunjungi [Dokumentasi Aspose.Words untuk Java](https://reference.aspose.com/words/java/) untuk referensi API, contoh kode, dan panduan detail. Anda juga dapat bergabung dengan forum komunitas Aspose atau menghubungi dukungan Aspose untuk pertanyaan spesifik.

### Q: Apakah Aspose.Words untuk Java cocok untuk proyek komersial?
A: Ya. Ia menawarkan opsi lisensi untuk penggunaan pribadi maupun komersial. Tinjau ketentuan lisensi di situs Aspose untuk memilih paket yang tepat bagi proyek Anda.

## Kesimpulan
Anda kini memiliki rangkaian lengkap untuk **memuat file txt**, **mendeteksi daftar**, **memangkas spasi**, dan **mengatur arah** saat mengonversi teks biasa menjadi dokumen Word yang kaya dengan Aspose.Words untuk Java. Terapkan pola ini untuk mengotomatisasi alur kerja dokumen, meningkatkan dukungan multibahasa, dan memastikan output yang bersih serta profesional setiap saat.

---

**Terakhir Diperbarui:** 2025-12-27  
**Diuji Dengan:** Aspose.Words untuk Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}