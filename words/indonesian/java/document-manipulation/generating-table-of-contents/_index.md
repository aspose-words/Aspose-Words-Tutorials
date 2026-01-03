---
date: 2026-01-03
description: Pelajari cara menyesuaikan nomor halaman saat menyisipkan daftar isi
  menggunakan Aspose.Words untuk Java. Sesuaikan gaya TOC dan buat dokumen dengan
  mudah.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Sesuaikan Nomor Halaman & Buat Daftar Isi dengan Aspose.Words untuk Java
url: /id/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sesuaikan Nomor Halaman & Buat Daftar Isi di Aspose.Words untuk Java

Dalam tutorial ini Anda akan mempelajari cara **menyesuaikan nomor halaman** dan **menyisipkan daftar isi** (TOC) dengan Aspose.Words untuk Java. Daftar isi yang terstruktur dengan baik memudahkan navigasi dokumen panjang, dan penyetelan perataan nomor halaman memberikan pengalaman profesional bagi pembaca. Kami akan membahas cara membuat dokumen, menyesuaikan gaya TOC, serta mengatur tab stop sehingga nomor halaman berada tepat pada posisi yang diinginkan.

## Jawaban Cepat
- **Apa arti “menyesuaikan nomor halaman”?** Memodifikasi tab stop yang menyelaraskan nomor halaman dalam TOC.  
- **Bisakah saya menyisipkan daftar isi secara otomatis?** Ya – gunakan kelas `FieldToc`.  
- **Apakah saya memerlukan lisensi untuk menjalankan kode?** Versi percobaan gratis dapat digunakan untuk pengembangan; lisensi diperlukan untuk produksi.  
- **Versi Aspose mana yang didukung?** Contoh ini bekerja dengan rilis terbaru Aspose.Words untuk Java.  
- **Apakah memungkinkan menyesuaikan gaya TOC?** Tentu – Anda dapat mengubah font, ketebalan, dan lainnya.

## Apa itu Daftar Isi di Aspose.Words?
TOC adalah sebuah field yang memindai dokumen untuk gaya heading (misalnya Heading 1, Heading 2) dan menghasilkan daftar entri beserta nomor halamannya. Aspose.Words memungkinkan Anda menyisipkan field ini secara programatis dan mengontrol tampilan secara penuh.

## Mengapa menyesuaikan nomor halaman dalam TOC?
Menyesuaikan tab stop memberi Anda kontrol presisi atas posisi nomor halaman, yang penting untuk:

- Mempertahankan tata letak kolom yang bersih dan rata.  
- Menyesuaikan dengan panduan gaya perusahaan.  
- Meningkatkan keterbacaan pada dokumen cetak maupun digital.

## Prasyarat
- Aspose.Words untuk Java sudah ditambahkan ke proyek Anda (Maven/Gradle).  
- Familiaritas dasar dengan sintaks Java.  

## Panduan Langkah‑per‑Langkah

### Langkah 1: Buat dokumen baru
Pertama, buat objek `Document` kosong yang akan menampung konten dan TOC Anda.

```java
Document doc = new Document();
```

### Langkah 2: Sesuaikan gaya TOC
Anda dapat mengubah tampilan setiap level TOC. Pada contoh ini kami membuat entri level pertama menjadi tebal, yang merupakan permintaan format umum.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Langkah 3: Tambahkan konten ke dokumen Anda
Sisipkan heading (misalnya `Heading1`, `Heading2`) dan paragraf biasa. Field TOC nanti akan secara otomatis mengambil heading‑heading ini. *(Kode dihilangkan untuk singkat – fokus pada pembuatan TOC.)*

### Langkah 4: Sisipkan field TOC
Tempatkan TOC di lokasi yang diinginkan—biasanya di awal dokumen.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Langkah 5: Simpan dokumen
Persistensikan dokumen ke disk. Anda dapat memilih format apa pun yang didukung seperti DOCX, PDF, atau HTML.

```java
doc.save("your_output_path_here");
```

## Menyesuaikan Tab Stop dalam TOC (Sesuaikan Nomor Halaman)
Jika tab stop default tidak menyelaraskan nomor halaman sesuai kebutuhan, Anda dapat mengiterasi semua paragraf TOC dan mengubah posisi tab mereka.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Sekarang entri TOC menampilkan nomor halaman tepat pada posisi yang Anda inginkan, memberikan tampilan dokumen yang lebih profesional.

## Masalah Umum & Tips
- **Heading tidak muncul di TOC:** Pastikan heading Anda menggunakan gaya bawaan (`Heading1`, `Heading2`, dll.) atau memetakan gaya kustom ke level TOC.  
- **Tab stop tidak diterapkan:** Verifikasi bahwa paragraf tersebut memang termasuk dalam gaya TOC (`TOC_1`‑`TOC_9`).  
- **Kinerja pada dokumen besar:** Panggil `doc.updateFields()` setelah menyisipkan TOC untuk memperbarui entri dalam satu kali proses.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara mengubah format entri TOC?**  
J: Gunakan `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` dimana *X* adalah level (1‑9) dan ubah font, warna, atau pengaturan paragrafnya.

**T: Bagaimana cara menambahkan lebih banyak level ke TOC saya?**  
J: Sesuaikan switch `FieldToc` `\o "1-3"` (misalnya) untuk menyertakan level heading tambahan, lalu perbarui gaya `TOC_X` yang bersangkutan.

**T: Bisakah saya mengubah posisi tab stop untuk entri TOC tertentu?**  
J: Ya – iterasi paragraf seperti pada bagian “Menyesuaikan Tab Stop” dan ubah masing‑masing tab stop secara individual.

**T: Apakah memungkinkan menghasilkan TOC dalam output PDF?**  
J: Tentu. Simpan dokumen sebagai PDF (`doc.save("output.pdf")`) setelah TOC; field akan dirender secara otomatis.

**T: Apakah saya harus memanggil `updateFields()` secara manual?**  
J: Saat Anda menyisipkan `FieldToc`, Aspose.Words memperbaruinya saat penyimpanan, namun memanggil `doc.updateFields()` memberikan hasil langsung untuk keperluan debugging.

## Kesimpulan
Anda telah mempelajari cara **menyesuaikan nomor halaman**, **menyisipkan daftar isi**, dan **menyesuaikan gaya TOC** menggunakan Aspose.Words untuk Java. Teknik‑teknik ini memungkinkan Anda membuat dokumen yang bersih, dapat dinavigasi, dan diformat secara profesional sesuai standar penerbitan apa pun.

---  

**Terakhir Diperbarui:** 2026-01-03  
**Diuji Dengan:** Aspose.Words untuk Java (rilis terbaru)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}