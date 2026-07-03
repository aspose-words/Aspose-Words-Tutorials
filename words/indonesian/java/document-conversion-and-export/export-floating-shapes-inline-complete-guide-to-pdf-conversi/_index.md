---
category: general
date: 2026-07-03
description: Ekspor bentuk mengambang secara inline saat mengonversi Word ke PDF secara
  inline. Pelajari cara mengatur opsi PDF dan menyimpan Word sebagai PDF dengan opsi
  di Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: id
og_description: Ekspor bentuk mengambang secara inline saat Anda mengonversi dokumen
  Word ke PDF. Tutorial ini menunjukkan cara mengatur opsi PDF dan opsi menyimpan
  Word sebagai PDF.
og_title: Ekspor Bentuk Mengambang Inline – Panduan Konversi PDF Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Ekspor Bentuk Mengambang Inline – Panduan Lengkap Konversi PDF
url: /id/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Bentuk Mengambang Inline – Panduan Lengkap Konversi PDF

Pernah perlu **mengekspor bentuk mengambang inline** saat Anda mengonversi dokumen Word ke PDF? Anda tidak sendirian—banyak pengembang mengalami masalah ini ketika diagram atau ikon mereka secara misterius berpindah ke lapisan terpisah. Kabar baiknya, ada satu opsi PDF yang dapat menjaga bentuk‑bentuk tersebut tetap berada di dalam tag `<span>`, mempertahankan tata letak persis seperti yang Anda lihat di Word.

Dalam tutorial ini kami akan membahas **cara mengatur opsi PDF** di Java, menunjukkan kode tepat untuk **menyimpan Word sebagai opsi PDF**, dan menjelaskan mengapa Anda mungkin ingin **mengonversi Word ke PDF inline** alih‑alih ekspor default berbasis blok. Pada akhir tutorial, Anda akan memiliki cuplikan kode siap‑jalankan yang dapat Anda masukkan ke proyek Maven atau Gradle mana pun.

## Apa yang Akan Anda Pelajari

- Perbedaan antara ekspor `<span>` inline dan `<div>` blok untuk bentuk mengambang.  
- Cara mengonfigurasi `PdfSaveOptions` agar memaksa render inline.  
- Kode langkah‑demi‑langkah yang memuat file `.docx`, menerapkan opsi, dan menulis PDF.  
- Jebakan umum (font yang hilang, bentuk yang tidak didukung) dan cara menghindarinya.  
- Tips untuk menguji output dan memperluas pendekatan ke elemen dokumen lainnya.

**Prasyarat** – Anda memerlukan Java 8 atau yang lebih baru, perpustakaan Aspose.Words for Java (atau API apa pun yang meniru kelas `PdfSaveOptions`‑nya), serta file Word contoh dengan bentuk mengambang (tutorial ini menggunakan `FloatingShapes.docx`). Tidak diperlukan alat eksternal lain.

---

## Langkah 1: Muat Dokumen Word Sumber

Hal pertama yang Anda lakukan adalah membuka `.docx` yang ingin Anda ubah. Ini cukup sederhana, tetapi pastikan jalurnya absolut atau ter‑resolve dengan benar dari classpath Anda.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Mengapa ini penting:*  
Jika dokumen tidak dimuat dengan benar, konversi PDF berikutnya akan melempar `FileNotFoundException`. Menggunakan `Document` memastikan model objek internal terisi penuh, termasuk semua bentuk mengambang yang berada di halaman.

---

## Langkah 2: Buat PDF Save Options dan Atur Bentuk Mengambang menjadi Inline

Di sinilah keajaiban terjadi. Secara default Aspose.Words mengekspor bentuk mengambang sebagai elemen `<div>` tingkat blok, yang dapat mengganggu alur pada PDF berbasis HTML. Menetapkan `setExportFloatingShapesAsInlineTag(true)` memberi tahu engine untuk membungkus setiap bentuk dalam `<span>` inline.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Mengapa ini penting:*  
- **Kesetiaan tata letak** – Tag inline menjaga bentuk tetap sejajar dengan teks di sekitarnya, menghindari celah yang tidak diinginkan.  
- **Keterbacaan** – Elemen inline lebih mudah diindeks dengan benar oleh pembaca PDF.  
- **Kontrol styling** – Anda dapat menargetkan `<span>` dengan CSS jika kemudian mengonversi PDF kembali ke HTML.

> **Pro tip:** Jika Anda pernah membutuhkan perilaku blok lama untuk dokumen tertentu, cukup beri nilai `false` atau hilangkan pemanggilan metode tersebut.

---

## Langkah 3: Simpan Dokumen sebagai PDF Menggunakan Opsi yang Dikonfigurasi

Sekarang Anda menggabungkan `Document` yang telah dimuat dengan `PdfSaveOptions` dan menulis file keluar. Baris tunggal ini melakukan pekerjaan berat.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Mengapa ini penting:*  
Metode `save` menghormati setiap flag yang Anda set pada `pdfOptions`. Lupa menyertakan opsi akan kembali ke ekspor blok default, yang menghilangkan tujuan **mengekspor bentuk mengambang inline**.

---

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program ringkas yang dapat Anda kompilasi dan jalankan sekarang. Ganti `YOUR_DIRECTORY` dengan jalur aktual di mesin Anda.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output yang diharapkan** – Setelah menjalankan program, buka `FloatingShapes.pdf`. Anda akan melihat bentuk‑bentuk berada tepat bersebelahan teks, tanpa ruang putih tambahan, dan representasi HTML‑nya (jika Anda memeriksa struktur internal PDF) akan berisi tag `<span>` di sekitar setiap bentuk.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Teks alt gambar:* **export floating shapes inline** screenshot of PDF with inline shapes.

---

## Pertanyaan Umum & Kasus Tepi

### 1. “Bagaimana jika dokumen saya berisi SmartArt yang kompleks?”

SmartArt diperlakukan sebagai objek gambar. Flag inline bekerja untuk kebanyakan bentuk vektor, tetapi SmartArt yang sangat rumit mungkin tetap dirender sebagai gambar. Dalam kasus tersebut, pertimbangkan untuk meratakan SmartArt di Word sebelum konversi, atau gunakan `pdfOptions.setExportSmartArtAsImage(true)` untuk memaksa ekspor gambar.

### 2. “Apakah saya dapat menggabungkan ekspor inline dan blok dalam dokumen yang sama?”

Sayangnya API menerapkan pengaturan secara global. Jika Anda memerlukan perilaku campuran, bagi dokumen menjadi beberapa bagian, ekspor tiap bagian secara terpisah dengan opsi berbeda, lalu gabungkan PDF‑nya menggunakan `PdfMerger`.

### 3. “Apakah ini memengaruhi penyematan font?”

Tidak. Penyematan font dikendalikan oleh `pdfOptions.setEmbedFullFonts(true)` (default). Anda dapat mengaktifkan atau menonaktifkannya tanpa menyentuh flag bentuk inline.

### 4. “Bagaimana cara memverifikasi bahwa bentuk benar‑benar `<span>`?”

Buka PDF yang dihasilkan dengan alat seperti **PDF.js** atau **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Anda akan melihat bentuk dibungkus dalam elemen `<span>` pada XML yang mendasarinya. Jika yang muncul `<div>`, opsi belum diterapkan.

---

## Memperluas Pendekatan – Opsi Terkait

Sambil Anda di sini, Anda mungkin juga ingin menjelajahi pengaturan konversi PDF lainnya:

| Opsi | Fungsinya | Kasus penggunaan umum |
|------|-----------|------------------------|
| `setCompressImages(true)` | Mengurangi ukuran gambar | Unduhan lebih cepat |
| `setUseHighQualityRendering(true)` | Meningkatkan render vektor | PDF siap cetak |
| `setExportDocumentStructure(true)` | Menambahkan tag struktural untuk aksesibilitas | Kepatuhan WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Menetapkan format secara eksplisit (jarang diperlukan) | Pipeline multi‑format |

Pengaturan ini cocok dipasangkan dengan skenario **convert word to pdf inline** di mana Anda memerlukan kesetiaan tata letak sekaligus performa.

---

## Menguji Konversi Anda

1. **Pemeriksaan visual** – Buka PDF di dua penampil (Chrome dan Adobe Reader) untuk memastikan bentuk‑bentuk sejajar.  
2. **Diff otomatis** – Gunakan perpustakaan seperti `pdfbox` untuk mengekstrak XML dan memastikan keberadaan tag `<span>`.  
3. **Benchmark performa** – Ukur waktu proses dengan dan tanpa `setCompressImages` untuk melihat trade‑off.

Contoh JUnit singkat:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Kesimpulan

Anda kini memiliki solusi menyeluruh, dari awal hingga akhir, untuk **mengekspor bentuk mengambang inline** ketika Anda **mengonversi Word ke PDF inline**. Dengan mengonfigurasi `PdfSaveOptions` Anda mengontrol tag HTML yang digunakan untuk setiap bentuk, menjaga PDF tetap rapi dan dapat dicari. Ingatlah untuk menguji output, menyesuaikan opsi terkait seperti kompresi gambar, dan menangani kasus tepi seperti SmartArt yang kompleks.

Siap melangkah ke tahap berikutnya? Coba terapkan teknik yang sama untuk **mengekspor tabel mengambang inline** atau bereksperimen dengan PDF bergaya CSS menggunakan `HtmlSaveOptions` Aspose. Pola yang sama—muat, konfigurasikan, simpan—berlaku untuk hampir semua skenario dokumen‑ke‑PDF.

Ada pertanyaan lebih lanjut tentang **cara mengatur pdf options** atau butuh bantuan dengan **save word as pdf options** untuk perpustakaan lain? Tinggalkan komentar, dan selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}