---
date: 2026-01-11
description: Pelajari cara menampilkan dan menyembunyikan bookmark serta membuat bookmark
  Java menggunakan Aspose.Words for Java untuk navigasi dan manipulasi dokumen yang
  efisien.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Tampilkan/Sembunyikan Bookmark dengan Aspose.Words untuk Java
url: /id/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tampilkan Sembunyikan Bookmark dengan Aspose.Words untuk Java

## Pengantar Penggunaan Bookmark di Aspose.Words untuk Java

Bookmark adalah fitur kuat di Aspose.Words untuk Java yang memungkinkan Anda **membuat bookmark java**, menavigasi ke konten tertentu, dan bahkan **menampilkan menyembunyikan bookmark** ketika Anda perlu menghasilkan versi dokumen yang berbeda. Dalam panduan langkah‑demi‑langkah ini kami akan membahas cara membuat, mengakses, memperbarui, menyalin, dan mengubah visibilitas bookmark, memberi Anda kontrol penuh atas manipulasi dokumen.

## Jawaban Cepat
- **Apa tujuan utama bookmark?** Untuk menandai dan kemudian mengambil bagian tertentu dari dokumen.  
- **Apakah saya dapat menyembunyikan penanda bookmark dalam output akhir?** Ya—gunakan API show/hide untuk mengubah visibilitasnya.  
- **Bagaimana cara membuat bookmark di dalam sel tabel?** Mulai dan akhiri bookmark dengan `DocumentBuilder` saat kursor berada di dalam sel.  
- **Apakah memungkinkan menyalin teks yang dibookmark ke dokumen lain?** Tentu saja—gunakan `NodeImporter` untuk mempertahankan format.  
- **Versi Aspose.Words apa yang diperlukan?** Rilis terbaru apa pun; kode ini bekerja dengan build 2026 terbaru.

## Apa itu “show hide bookmarks”?

Fitur **show hide bookmarks** memungkinkan Anda secara programatik menampilkan atau menyembunyikan delimiter bookmark dalam dokumen yang disimpan. Ini berguna ketika Anda ingin menghasilkan output bersih untuk pengguna akhir sambil tetap mempertahankan data bookmark untuk pemrosesan internal.

## Mengapa menggunakan bookmark dalam otomatisasi dokumen Java?

- **Navigasi efisien** – Lompat langsung ke bagian tanpa harus memindai seluruh file.  
- **Pembuatan konten dinamis** – Sisipkan, ganti, atau hapus teks yang terkait dengan bookmark.  
- **Visibilitas bersyarat** – Tampilkan atau sembunyikan penanda bookmark berdasarkan preferensi pengguna atau format output.  
- **Dapat digunakan kembali** – Salin fragmen yang dibookmark antar dokumen sambil mempertahankan gaya.

## Prasyarat
- Java Development Kit (JDK) 8 atau lebih tinggi.  
- Perpustakaan Aspose.Words untuk Java yang ditambahkan ke proyek Anda (Maven/Gradle atau JAR).  
- Familiaritas dasar dengan kelas `Document` dan `DocumentBuilder`.

## Panduan Langkah‑demi‑Langkah

### Langkah 1: Membuat Bookmark (create bookmark java)

Untuk menambahkan bookmark, Anda memulainya, menulis kontennya, lalu mengakhirinya. Contoh ini membuat bookmark sederhana bernama **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Langkah 2: Mengakses Bookmark (access bookmarks java)

Bookmark dapat diambil baik melalui indeks berbasis nol maupun melalui nama. Kode di bawah ini menunjukkan kedua pendekatan.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Langkah 3: Memperbarui Data Bookmark (update bookmark text)

Anda dapat mengganti nama bookmark atau mengganti konten teksnya. Ini berguna ketika dokumen dasar berubah.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Langkah 4: Bekerja dengan Teks yang Dibookmark (copy bookmarked text)

Menyalin fragmen yang dibookmark ke dokumen lain sambil mempertahankan format asli sangat mudah dengan `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Langkah 5: Menampilkan dan Menyembunyikan Bookmark (show hide bookmarks)

Potongan kode berikut menunjukkan cara menyembunyikan penanda bookmark dalam file yang disimpan. Berikan `false` untuk menyembunyikan, `true` untuk menampilkan.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Langkah 6: Membongkar Bookmark Baris (bookmark table cell)

Ketika bookmark melintasi baris tabel, mereka dapat menjadi berantakan. Metode utilitas di bawah ini membongkarnya dan memungkinkan Anda menghapus baris tertentu berdasarkan bookmarknya.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Masalah Umum dan Solusinya

| Masalah | Solusi |
|-------|----------|
| **Bookmark tidak ditemukan** | Pastikan nama bookmark cocok persis (case‑sensitive) dan dokumen telah disimpan setelah pembuatan. |
| **Teks yang disalin kehilangan format** | Gunakan `ImportFormatMode.KEEP_SOURCE_FORMATTING` dengan `NodeImporter` seperti yang ditunjukkan pada Langkah 4. |
| **Show/hide tidak memengaruhi output** | Pastikan Anda memanggil `showHideBookmarkedContent` **sebelum** menyimpan dokumen. |
| **Bookmark di dalam sel tabel diabaikan** | Letakkan pemanggilan start/end saat kursor builder berada di dalam sel target. |

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara membuat bookmark di dalam sel tabel?**  
J: Gunakan `DocumentBuilder` untuk memindahkan kursor ke sel yang diinginkan, lalu panggil `startBookmark` dan `endBookmark` di sekitar konten sel.

**T: Bisakah saya menyalin bookmark ke dokumen lain?**  
J: Ya—gunakan kelas `NodeImporter` (lihat Langkah 4) untuk mengimpor node yang dibookmark sambil mempertahankan format aslinya.

**T: Bagaimana cara menghapus baris berdasarkan bookmarknya?**  
J: Pertama temukan baris yang berisi bookmark, lalu panggil `remove` pada node baris (seperti yang ditunjukkan pada Langkah 6).

**T: Apa saja contoh penggunaan umum untuk bookmark?**  
J: Membuat daftar isi, mengekstrak bagian tertentu untuk pelaporan, dan mengotomatiskan perakitan dokumen berdasarkan pilihan pengguna.

**T: Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Words untuk Java?**  
J: Untuk dokumentasi detail dan unduhan, kunjungi [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Terakhir Diperbarui:** 2026-01-11  
**Diuji Dengan:** Aspose.Words untuk Java 24.11 (2026)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}