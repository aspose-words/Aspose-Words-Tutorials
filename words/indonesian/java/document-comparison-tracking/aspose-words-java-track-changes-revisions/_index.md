---
date: '2026-11-02'
description: Pelajari cara melacak perubahan dalam dokumen Word menggunakan Aspose.Words
  untuk Java, mencakup perbandingan dokumen, penanganan revisi inline, lisensi, dan
  tips kinerja.
keywords:
- how to track changes
- track formatting changes
- document comparison aspose
- aspose.words license java
lastmod: '2026-11-02'
og_description: Pelajari cara melacak perubahan dalam dokumen Word menggunakan Aspose.Words
  untuk Java, termasuk perbandingan dokumen, penanganan revisi inline, dan detail
  lisensi.
og_image_alt: Guide showing how to track changes in Word documents with Aspose.Words
  Java
og_title: Cara melacak perubahan dalam dokumen Word dengan Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-11-02'
  description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  headline: How to track changes in Word docs with Aspose.Words Java
  type: TechArticle
- description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  name: How to track changes in Word docs with Aspose.Words Java
  steps:
  - name: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
    text: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
  - name: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
    text: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
  - name: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
    text: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
  - name: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
    text: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
  - name: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
    text: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
  - name: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
    text: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
  type: HowTo
- questions:
  - answer: An inline node represents a run of text or a character‑level element inside
      a paragraph, such as a `Run` or a `Field`.
    question: What is an inline node in Aspose.Words?
  - answer: Call `document.startTrackRevisions()` on your `Document` instance before
      making any edits.
    question: How do I start tracking revisions with Aspose.Words Java?
  - answer: Yes, use `document.acceptAllRevisions()` or `document.rejectAllRevisions()`
      to apply the changes programmatically.
    question: Can I automate accepting or rejecting revisions in a document?
  - answer: It supports DOCX, PDF, HTML, ODT, RTF, EPUB, and more than 35 formats
      for both import and export.
    question: What types of documents does Aspose.Words support?
  - answer: Process the file section by section, use low‑memory load options, and
      leverage batch revision methods to keep CPU and RAM usage optimal.
    question: How do I handle large documents efficiently with Aspose.Words?
  type: FAQPage
tags:
- track changes
- Aspose.Words Java
- document revisions
- inline revisions
- Java document processing
title: Cara melacak perubahan dalam dokumen Word dengan Aspose.Words Java
url: /id/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara melacak perubahan dalam dokumen Word dengan Aspose.Words Java

Berkolaborasi pada dokumen penting sering berarti Anda perlu **melacak perubahan dalam dokumen Word** sehingga setiap edit terlihat dan dapat dikontrol. Aspose.Words untuk Java memberikan mesin “Track Changes” secara programatik yang bekerja tanpa Microsoft Word, memungkinkan Anda memulai, mengkueri, menerima, atau menolak revisi langsung dari kode Anda. Dalam panduan ini Anda akan menyiapkan perpustakaan, menjelajahi penanganan revisi inline, dan menemukan teknik ramah‑kinerja untuk file besar.

## Jawaban Cepat
- **Perpustakaan apa yang memungkinkan pelacakan perubahan dalam dokumen Word?** Aspose.Words for Java  
- **Manajer dependensi mana yang direkomendasikan?** Maven atau Gradle (kedua‑nya didukung)  
- **Apakah saya memerlukan lisensi untuk pengembangan?** Trial gratis dapat digunakan untuk evaluasi; lisensi diperlukan untuk penggunaan produksi  
- **Bisakah saya memproses dokumen besar secara efisien?** Ya – gunakan pemrosesan per‑section dan operasi batch  
- **Apakah ada metode untuk memulai pelacakan secara programatis?** `document.startTrackRevisions()` memulai sesi pelacakan  

## Apa itu cara melacak perubahan?
`how to track changes` mengacu pada proses mengaktifkan secara programatik fitur pelacakan revisi bawaan Word. Ketika aktif, setiap sisipan, penghapusan, edit format, atau pemindahan dicatat sebagai objek revisi terpisah. Objek‑objek ini kemudian dapat di‑enumerasi, ditinjau, dan baik diterima untuk membuat perubahan menjadi permanen atau ditolak untuk membuangnya, memberikan auditabilitas penuh atas edit dokumen.

## Mengapa menggunakan Aspose.Words untuk pelacakan perubahan?
Aspose.Words mendukung **lebih dari 35 format input dan output** — termasuk DOCX, PDF, HTML, dan ODT — dan dapat memproses **dokumen 500 halaman dalam kurang dari 3 detik** pada perangkat keras server standar tanpa memerlukan Microsoft Word. API‑nya bekerja di Windows, Linux, dan macOS, menjadikannya ideal untuk solusi berbasis cloud atau on‑premises yang memerlukan manajemen revisi yang dapat diandalkan.

## Prasyarat

- **Java Development Kit (JDK):** versi 8 atau lebih tinggi.  
- **IDE:** IntelliJ IDEA, Eclipse, atau NetBeans.  
- **Alat build:** Maven atau Gradle untuk manajemen dependensi.  
- Pengetahuan dasar Java untuk memahami potongan kode.

## Menyiapkan Aspose.Words

### Pengaturan Maven

Tambahkan dependensi berikut ke file `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

### Pengaturan Gradle

Sertakan baris ini dalam file `build.gradle` Anda:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Pengadaan Lisensi

Aspose menawarkan trial gratis untuk menguji fiturnya, memungkinkan Anda mengevaluasi apakah sesuai dengan kebutuhan Anda. Untuk memulai:

1. **Trial gratis:** Unduh perpustakaan dari [Aspose Downloads](https://releases.aspose.com/words/java/) dan gunakan dengan batasan evaluasi.  
2. **Lisensi sementara:** Dapatkan lisensi sementara untuk penggunaan lebih lama tanpa batasan evaluasi dengan mengunjungi [Temporary License](https://purchase.aspose.com/temporary-license/).  
3. **Beli lisensi:** Pertimbangkan pembelian jika Anda memerlukan akses penuh ke fitur Aspose.Words dengan mengikuti instruksi pada halaman pembelian mereka.

#### Inisialisasi Dasar

`Document` adalah objek utama Aspose.Words yang mewakili file Word dalam memori. Untuk menginisialisasi, buat instance `Document` dan mulai bekerja dengannya:

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("input.docx");
        // Further processing here
    }
}
```

## Cara melacak perubahan dalam dokumen Word menggunakan Aspose.Words Java
`document.startTrackRevisions()` memulai sesi pelacakan revisi pada dokumen. Muat file Word, panggil `startTrackRevisions()` untuk memulai sesi pelacakan, lakukan edit yang diinginkan, dan akhirnya simpan dokumen. API mencatat setiap edit sebagai objek revisi yang dapat Anda enumerasi, terima, atau tolak kemudian. Pola dua langkah ini—memulai pelacakan, melakukan edit—mencakup sisipan, penghapusan, perubahan format, dan pemindahan.

## Panduan Implementasi

Di bagian ini kami menjelajahi cara menangani berbagai jenis revisi menggunakan Aspose.Words Java.

### Menangani revisi inline

#### Gambaran Umum

Saat melacak perubahan, revisi inline muncul di dalam paragraf sebagai run. Mereka dapat berupa sisipan, penghapusan, perubahan format, atau operasi pemindahan. Memahami tiap tipe memungkinkan Anda membangun alat tinjau yang ramah UI.

#### Implementasi Kode

Potongan berikut menunjukkan cara memeriksa tipe revisi dari node inline:

```java
import com.aspose.words.Document;
import com.aspose.words.Paragraph;
import com.aspose.words.Run;
import com.aspose.words.Revision;
import org.testng.Assert;

public class RevisionHandler {
    public void handleRevisions() throws Exception {
        Document doc = new Document("Revision runs.docx");

        // Check the number of revisions
        Assert.assertEquals(6, doc.getRevisions().getCount());

        // Accessing a specific revision's parent node
        Run run = (Run) doc.getRevisions().get(0).getParentNode();

        Paragraph paragraph = run.getParentParagraph();
        com.aspose.words.RunCollection runs = paragraph.getRuns();

        Assert.assertEquals(runs.getCount(), 6);

        // Identifying different types of revisions
        Assert.assertTrue(runs.get(2).isInsertRevision());  // Insert revision
        Assert.assertTrue(runs.get(2).isFormatRevision());  // Format revision
        Assert.assertTrue(runs.get(4).isMoveFromRevision()); // Move from revision
        Assert.assertTrue(runs.get(1).isMoveToRevision());   // Move to revision
        Assert.assertTrue(runs.get(5).isDeleteRevision());   // Delete revision
    }
}
```

`RevisionType` adalah enumerasi yang mengklasifikasikan jenis perubahan—Insert, Delete, Format, MoveFrom, atau MoveTo. Dengan memeriksa properti ini Anda dapat memutuskan apakah menampilkan perubahan kepada pengguna atau menerapkan aturan penerimaan otomatis.

#### Penjelasan
- **Revisi sisipan:** Teks yang ditambahkan saat pelacakan aktif.  
- **Revisi format:** Perubahan pada font, warna, atau gaya yang diterapkan pada teks yang ada.  
- **Revisi pindah dari / ke:** Mewakili teks yang dipindahkan dalam dokumen; mereka selalu muncul sebagai pasangan.  
- **Revisi hapus:** Teks yang dihapus tetapi tetap dipertahankan hingga Anda menerima atau menolaknya.

### Aplikasi Praktis

Skenario dunia nyata di mana penanganan revisi bersinar:

1. **Pengeditan kolaboratif:** Tim dapat meninjau dan menyetujui perubahan sebelum mempublikasikan kontrak akhir.  
2. **Peninjauan dokumen hukum:** Pengacara melacak amandemen pada klausul, memastikan setiap perubahan dapat diaudit.  
3. **Dokumentasi perangkat lunak:** Penulis teknis mengelola pembaruan referensi API sambil mempertahankan riwayat versi.

### Pertimbangan Kinerja

`LoadOptions` mengonfigurasi cara dokumen dimuat, termasuk pengaturan penggunaan memori. Memproses dokumen besar yang penuh revisi dapat memakan banyak memori. Ikuti praktik terbaik berikut:

- **Pemrosesan per‑section:** Muat dan proses satu section pada satu waktu untuk menjaga penggunaan memori tetap rendah.  
- **Operasi batch:** Gunakan `Document.acceptAllRevisions()` atau `Document.rejectAllRevisions()` pada seluruh section alih‑alih node individu bila memungkinkan.  
- **API streaming:** Untuk file lebih besar dari 1 GB, gunakan mode streaming `LoadOptions` untuk menghindari memuat seluruh file ke RAM.

## Kesulitan Umum dan Pemecahan Masalah

`document.startTrackRevisions()` memulai pelacakan revisi pada instance Document yang diberikan.  

- **Revisi hilang setelah pengeditan:** Pastikan Anda memanggil `document.startTrackRevisions()` *sebelum* melakukan perubahan apa pun; memulai pelacakan setelah edit tidak akan menangkap modifikasi sebelumnya.  
- **Perubahan format tak terduga:** Beberapa perubahan gaya dilaporkan sebagai `RevisionType.Format`. Jika Anda hanya peduli pada konten teks, filter revisi format dalam logika enumerasi Anda.  
- **Perlambatan dokumen besar:** Aktifkan `LoadOptions.memoryUsage = LoadOptions.MemoryUsageMode.LowMemory` untuk mengurangi konsumsi memori puncak.

## Pertanyaan yang Sering Diajukan

`Document.acceptAllRevisions()` menerapkan setiap revisi yang tertunda, menjadikan semua perubahan permanen. `Document.rejectAllRevisions()` membuang semua revisi yang tertunda, mengembalikan dokumen ke keadaan aslinya.

**Q: Apa itu node inline di Aspose.Words?**  
A: Node inline mewakili satu run teks atau elemen tingkat karakter di dalam paragraf, seperti `Run` atau `Field`.

**Q: Bagaimana cara memulai pelacakan revisi dengan Aspose.Words Java?**  
A: Panggil `document.startTrackRevisions()` pada instance `Document` Anda sebelum melakukan edit apa pun.

**Q: Bisakah saya mengotomatisasi penerimaan atau penolakan revisi dalam dokumen?**  
A: Ya, gunakan `document.acceptAllRevisions()` atau `document.rejectAllRevisions()` untuk menerapkan perubahan secara programatik.

**Q: Jenis dokumen apa yang didukung Aspose.Words?**  
A: Ia mendukung DOCX, PDF, HTML, ODT, RTF, EPUB, dan lebih dari 35 format untuk impor maupun ekspor.

**Q: Bagaimana cara menangani dokumen besar secara efisien dengan Aspose.Words?**  
A: Proses file per‑section, gunakan opsi load memori rendah, dan manfaatkan metode revisi batch untuk menjaga penggunaan CPU dan RAM optimal.

## Sumber Daya

- [Aspose.Words Java Documentation](https://reference.aspose.com/words/java/)  
- [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

Mulailah perjalanan Anda dengan Aspose.Words Java hari ini, dan manfaatkan potensi penuh pemrosesan dokumen dalam aplikasi Anda!



---

**Terakhir Diperbarui:** 2026-11-02  
**Diuji Dengan:** Aspose.Words 25.3 untuk Java  
**Penulis:** Aspose

## Tutorial Terkait

- [Implement Change Tracking in Aspose.Words for Java](/words/java/document-comparison-tracking/)
- [Convert Word to PDF with Aspose.Words for Java Document Conversion API](/words/java/document-converting/)
- [Aspose Words Loadoptions Recover Corrupted Word Docs In Java](/words/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}