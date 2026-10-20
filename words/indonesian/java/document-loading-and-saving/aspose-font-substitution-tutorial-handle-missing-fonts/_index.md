---
category: general
date: 2026-05-04
description: Tutorial substitusi font Aspose menunjukkan cara menangani font yang
  hilang di Java menggunakan callback peringatan dan LoadOptions untuk memuat dokumen
  secara andal.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: id
og_description: Tutorial substitusi font Aspose menjelaskan cara menangani font yang
  hilang di Java, menangkap peristiwa substitusi, dan menjaga tampilan dokumen Anda
  tetap tepat.
og_title: Tutorial Substitusi Font Aspose – Menangani Font yang Hilang
tags:
- Aspose.Words
- Java
- Font Management
title: Tutorial Penggantian Font Aspose – Menangani Font yang Hilang
url: /id/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial Substitusi Font Aspose – Menangani Font yang Hilang

Pernah membutuhkan **tutorial substitusi font Aspose** karena sebuah DOCX yang Anda muat tiba‑tiba tampil salah? Anda tidak sendirian—font yang hilang adalah sumber bug yang licik yang dapat mengubah laporan yang terformat sempurna menjadi berantakan. Kabar baiknya, Aspose.Words menyediakan cara bersih untuk **menangani font yang hilang** sebelum mereka merusak tata letak Anda.

Dalam panduan ini kami akan menelusuri contoh Java lengkap yang siap dijalankan, yang menangkap peringatan substitusi font, menjelaskan mengapa setiap bagian penting, dan menunjukkan cara memverifikasi hasilnya. Pada akhir tutorial Anda akan tahu persis cara menjaga dokumen tetap tajam meskipun tipe huruf asli tidak ada di mesin.

## Apa yang Akan Anda Pelajari

- Cara mendaftarkan `IWarningCallback` khusus yang mendengarkan peristiwa `FONT_SUBSTITUTION`.  
- Mengapa menggunakan `LoadOptions` merupakan pendekatan yang direkomendasikan untuk penanganan font yang andal.  
- Cara menguji solusi dengan dokumen yang sengaja rusak.  
- Kesalahan umum (misalnya, lupa mengatur callback) dan perbaikan cepat.  

**Prasyarat**: Java 8+ terpasang, lisensi Aspose.Words for Java yang valid (atau evaluasi gratis), serta IDE dasar seperti IntelliJ atau Eclipse. Tidak diperlukan pustaka eksternal lain.

---

![Diagram tutorial substitusi font Aspose](https://example.com/images/font-substitution-diagram.png "Diagram tutorial substitusi font Aspose")

## Langkah 1 – Definisikan Callback Peringatan untuk Menangkap Substitusi  

Hal pertama yang dilakukan Aspose.Words ketika tidak dapat menemukan font yang diminta adalah memicu peristiwa `WarningInfo`. Dengan mengimplementasikan `IWarningCallback` Anda dapat mencatat, menampilkan, atau bahkan menghentikan proses muat jika diinginkan.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Mengapa ini penting** – Tanpa callback Anda tidak akan pernah tahu bahwa Aspose menukar *Arial* dengan *Liberation Sans* (atau fallback apa pun yang dipilih). Penukaran diam-diam ini dapat menyebabkan pergeseran tata letak, terutama pada tabel atau tata letak multi‑kolom.

---

## Langkah 2 – Sambungkan Callback ke `LoadOptions`

`LoadOptions` adalah pusat kendali untuk segala hal yang memengaruhi cara dokumen dibaca. Dengan menancapkan callback di sini Anda menjamin bahwa **setiap** dokumen yang dimuat dengan opsi ini akan memicu logika peringatan Anda.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Tip** – Jika Anda berencana memuat beberapa dokumen secara batch, gunakan kembali instance `LoadOptions` yang sama. Ini mengurangi overhead pembuatan objek dan menjaga konsistensi pencatatan Anda.

---

## Langkah 3 – Muat Dokumen yang Mungkin Membutuhkan Substitusi Font  

Sekarang kita benar‑benar membaca file yang diketahui kehilangan sebuah font. Ganti `YOUR_DIRECTORY` dengan folder yang berisi file uji Anda.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

Ketika pemuat menemukan glyph yang tidak dapat dirender, callback dari **Langkah 1** mencetak pesan ramah ke konsol. Contohnya:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Kasus tepi** – Jika dokumen berisi font yang *tersemat*, Aspose akan menggunakan font tersebut terlebih dahulu dan melewatkan peringatan. Itu adalah perilaku yang diharapkan; Anda hanya akan melihat peringatan untuk font yang benar‑benar hilang.

---

## Langkah 4 – Simpan Dokumen (Sekarang dengan Font yang Digantikan)

Setelah proses muat selesai, Aspose sudah menukar font yang hilang secara internal. Menyimpan dokumen mempertahankan substitusi tersebut, sehingga output terlihat persis seperti yang Anda lihat di konsol.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Buka `loaded.docx` di Word atau LibreOffice dan Anda akan melihat tata letak tetap tidak berubah, meskipun font asli tidak terpasang di mesin Anda.

---

## Langkah 5 – Verifikasi Hasil Secara Programatis (Opsional)

Jika Anda ingin memastikan tidak ada substitusi tak terduga yang lolos, Anda dapat menanyakan tabel font dokumen setelah muat.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

Output seharusnya berisi font fallback (misalnya, *Arial*) alih‑alih font yang hilang. Ini berguna untuk pipeline otomatis dimana Anda memerlukan jaminan bahwa PDF atau DOCX akhir memenuhi persyaratan merek.

---

## Tips Pro & Kesalahan Umum

- **Tips pro:** Atur `loadOptions.setFontSettings(new FontSettings())` jika Anda perlu menunjuk Aspose ke folder font khusus sebelum memuat. Ini mengurangi jumlah substitusi.  
- **Waspadai:** Lupa memanggil `setWarningCallback`. Kode tetap berjalan, tetapi Anda akan kehilangan pesan diagnostik penting.  
- **Catatan kinerja:** Memuat dokumen besar dengan banyak font yang hilang dapat menghasilkan banyak peringatan. Pertimbangkan untuk membatasi output atau menulis ke file log alih‑alih `System.out`.  
- **Bagaimana jika Anda perlu menghentikan proses pada substitusi?** Ganti pemanggilan `System.out.println` dengan `throw new RuntimeException(info.getDescription())` di dalam callback. Itu memaksa proses muat gagal, yang berguna untuk skenario kepatuhan ketat.

---

## Pertanyaan yang Sering Diajukan

**T: Apakah ini bekerja dengan format PDF atau gambar?**  
J: Callback peringatan khusus untuk fase pemuatan format pemrosesan Word (`.docx`, `.doc`, `.rtf`, dll.). Rendering PDF menggunakan pipeline yang berbeda, tetapi Anda masih dapat menangkap peringatan terkait font melalui `PdfLoadOptions`.

**T: Bisakah saya menggantikan font tertentu dengan font pilihan saya?**  
J: Ya. Buat objek `FontSettings`, panggil `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")`, dan tetapkan ke `loadOptions.setFontSettings(fontSettings)`.

**T: Apakah callback bersifat thread‑safe?**  
J: Implementasi default tidak disinkronkan. Jika Anda memuat dokumen secara paralel, pastikan implementasi callback Anda menangani akses bersamaan (misalnya, menggunakan `ConcurrentLinkedQueue` untuk pencatatan).

---

## Kesimpulan

Anda kini memiliki **tutorial substitusi font Aspose** lengkap yang menunjukkan cara **menangani font yang hilang** secara elegan di Java. Dengan mendefinisikan `IWarningCallback` khusus, menyambungkannya ke `LoadOptions`, dan menyimpan dokumen, Anda menjaga konsistensi output terlepas dari font apa yang terpasang di mesin host.

Dari sini Anda dapat menjelajahi:

- Tabel substitusi font khusus untuk penggantian yang sesuai merek.  
- Mengintegrasikan logger peringatan dengan SLF4J atau Log4j untuk diagnostik tingkat produksi.  
- Memperluas callback untuk mengumpulkan statistik across batch dokumen.

Cobalah, sesuaikan font fallback, dan biarkan dokumen Anda tetap indah meskipun tipe huruf asli menghilang. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}