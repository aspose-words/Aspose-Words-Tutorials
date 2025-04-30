---
"description": "Pelajari cara menggunakan Aspose.Words untuk revisi Java secara efisien. Panduan langkah demi langkah untuk pengembang. Optimalkan manajemen dokumen Anda."
"linktitle": "Menggunakan Revisi"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggunakan Revisi di Aspose.Words untuk Java"
"url": "/id/java/using-document-elements/using-revisions/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Revisi di Aspose.Words untuk Java


Jika Anda seorang pengembang Java yang ingin bekerja dengan dokumen dan perlu menerapkan kontrol revisi, Aspose.Words untuk Java menyediakan seperangkat alat yang hebat untuk membantu Anda mengelola revisi secara efektif. Dalam tutorial ini, kami akan memandu Anda menggunakan revisi di Aspose.Words untuk Java langkah demi langkah. 

## 1. Pengenalan Aspose.Words untuk Java

Aspose.Words untuk Java adalah API Java yang tangguh yang memungkinkan Anda membuat, memodifikasi, dan memanipulasi dokumen Word tanpa memerlukan Microsoft Word. Ini sangat berguna saat Anda perlu menerapkan revisi dalam dokumen Anda.

## 2. Menyiapkan Lingkungan Pengembangan Anda

Sebelum kita mulai menggunakan Aspose.Words untuk Java, Anda perlu menyiapkan lingkungan pengembangan Anda. Pastikan Anda telah menginstal perangkat pengembangan Java yang diperlukan dan pustaka Aspose.Words untuk Java.

## 3. Membuat Dokumen Baru

Mari kita mulai dengan membuat dokumen Word baru menggunakan Aspose.Words untuk Java. Berikut cara melakukannya:

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. Menambahkan Konten ke Dokumen

Sekarang Anda memiliki dokumen kosong, Anda dapat menambahkan konten ke dalamnya. Dalam contoh ini, kita akan menambahkan tiga paragraf:

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. Memulai Pelacakan Revisi

Untuk melacak revisi dalam dokumen Anda, Anda dapat menggunakan kode berikut:

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. Melakukan Revisi

Mari kita buat revisi dengan menambahkan paragraf lain:

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. Menerima dan Menolak Revisi

Anda dapat menerima atau menolak revisi dalam dokumen Anda menggunakan Aspose.Words untuk Java. Revisi dapat dikelola dengan mudah di Microsoft Word setelah dokumen dibuat.

## 8. Menghentikan Pelacakan Revisi

Untuk menghentikan pelacakan revisi, gunakan kode berikut:

```java
doc.stopTrackRevisions();
```

## 9. Menyimpan Dokumen

Terakhir, simpan dokumen Anda:

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. Kesimpulan

Dalam tutorial ini, kami telah membahas dasar-dasar penggunaan revisi di Aspose.Words untuk Java. Anda telah mempelajari cara membuat dokumen, menambahkan konten, memulai dan menghentikan pelacakan revisi, dan menyimpan dokumen Anda.

Sekarang Anda memiliki alat yang Anda butuhkan untuk mengelola revisi secara efektif di aplikasi Java Anda menggunakan Aspose.Words untuk Java.

## Kode Sumber Lengkap
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// Tambahkan teks ke paragraf pertama, lalu tambahkan dua paragraf lagi.
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// Kami memiliki tiga paragraf, tidak ada satupun yang terdaftar sebagai jenis revisi apa pun
// Jika kami menambahkan/menghapus konten apa pun dalam dokumen saat melacak revisi,
// mereka akan ditampilkan seperti itu dalam dokumen dan dapat diterima/ditolak.
doc.startTrackRevisions("John Doe", new Date());
// Paragraf ini merupakan revisi dan akan menyetel tanda "IsInsertRevision" yang sesuai.
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// Dapatkan kumpulan paragraf dokumen dan hapus satu paragraf.
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// Karena kami melacak revisi, paragraf tersebut masih ada dalam dokumen, akan memiliki "IsDeleteRevision" yang ditetapkan
// dan akan ditampilkan sebagai revisi di Microsoft Word, hingga kami menerima atau menolak semua revisi.
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// Paragraf revisi hapus dihapus setelah kami menerima perubahan.
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //adalah Is.Kosong
// Menghentikan pelacakan revisi membuat teks ini muncul sebagai teks normal.
// Revisi tidak dihitung saat dokumen diubah.
doc.stopTrackRevisions();
// Simpan dokumen.
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## Tanya Jawab Umum

### 1. Dapatkah saya menggunakan Aspose.Words untuk Java dengan bahasa pemrograman lain?

Tidak, Aspose.Words untuk Java dirancang khusus untuk pengembangan Java.

### 2. Apakah Aspose.Words untuk Java kompatibel dengan semua versi Microsoft Word?

Ya, Aspose.Words untuk Java dirancang agar kompatibel dengan berbagai versi Microsoft Word.

### 3. Dapatkah saya melacak revisi pada dokumen Word yang ada?

Ya, Anda dapat menggunakan Aspose.Words untuk Java untuk melacak revisi dalam dokumen Word yang ada.

### 4. Apakah ada persyaratan lisensi untuk menggunakan Aspose.Words untuk Java?

Ya, Anda perlu memperoleh lisensi untuk menggunakan Aspose.Words untuk Java dalam proyek Anda. Anda dapat [dapatkan akses ke lisensi di sini](https://purchase.aspose.com/buy).

### 5. Di mana saya dapat menemukan dukungan untuk Aspose.Words untuk Java?

Untuk pertanyaan atau masalah apa pun, Anda dapat mengunjungi [Forum dukungan Aspose.Words untuk Java](https://forum.aspose.com/).

Mulailah dengan Aspose.Words untuk Java hari ini dan sederhanakan proses manajemen dokumen Anda.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}