---
category: general
date: 2026-02-18
description: Pelajari cara mengonversi DOCX ke PDF dan menyimpan Word sebagai PDF
  sambil mempertahankan bentuk mengambang. Panduan ini menunjukkan cara mengekspor
  bentuk dengan benar.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: id
og_description: Konversi DOCX ke PDF dan pelajari cara mengekspor bentuk. Ikuti tutorial
  lengkap ini untuk menyimpan Word sebagai PDF dengan penandaan yang tepat.
og_title: Konversi DOCX ke PDF – Panduan Ekspor Bentuk Inline
tags:
- Aspose.Words
- Java
- PDF conversion
title: Konversi DOCX ke PDF dengan Ekspor Bentuk Inline – Panduan Langkah demi Langkah
url: /id/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi DOCX ke PDF – Panduan Ekspor Bentuk Inline

Pernahkah Anda perlu **mengonversi DOCX ke PDF** tetapi khawatir gambar mengambang atau kotak teks Anda akan menghilang atau bergeser? Anda tidak sendirian. Dalam banyak proyek—pikirkan generator laporan otomatis atau pipeline pemrosesan batch—mempertahankan tata letak tepat dokumen Word adalah hal yang tidak dapat dinegosiasikan.  

Berita baik? Dengan beberapa baris kode Anda dapat **menyimpan Word sebagai PDF** dan mengontrol apakah bentuk mengambang tersebut menjadi tag inline atau tetap sebagai elemen level‑blok. Di bawah ini Anda akan melihat secara tepat **cara mengekspor bentuk** sesuai keinginan, plus beberapa tip yang menyelamatkan Anda dari jebakan umum.

---

## Apa yang Akan Anda Pelajari

* Memuat file `.docx` dari disk.  
* Mengonfigurasi `PdfSaveOptions` sehingga bentuk mengambang diekspor sebagai tag inline.  
* Menulis PDF yang dihasilkan ke folder pilihan Anda.  
* Memahami mengapa flag `setExportFloatingShapesAsInlineTag` penting dan kapan Anda mungkin mengubahnya.  

Tidak ada layanan eksternal, tidak ada UI “klik‑untuk‑unduh” yang ajaib—hanya kode Java murni yang dapat Anda masukkan ke dalam proyek Maven atau Gradle mana pun.

---

## Prasyarat

| Persyaratan | Mengapa penting |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 or later) | Menyediakan kelas `Document` dan `PdfSaveOptions` yang digunakan dalam contoh. |
| **JDK 8+** | Perpustakaan ini dikompilasi untuk Java 8 dan yang lebih baru; runtime yang lebih lama akan melempar `UnsupportedClassVersionError`. |
| **A DOCX file** with at least one floating shape (image, text box, WordArt) | Untuk melihat efek opsi ekspor bentuk, Anda memerlukan dokumen yang memang berisi objek mengambang. |

Jika Anda sudah memiliki semua ini, bagus—mari kita mulai.

---

## Langkah 1 – Muat Dokumen Sumber  

Pertama kami membuat instance `Document` yang menunjuk ke `.docx` yang ingin Anda konversi. Konstruktor membaca file ke memori, mengurai paket OpenXML, dan menyiapkan model objek internal.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tip:** Jika Anda memproses banyak file dalam sebuah loop, gunakan kembali satu objek `Document` hanya setelah Anda memanggil `doc.close()` (atau biarkan garbage collector menanganinya). Ini mencegah kebocoran handle file di Windows.

---

## Langkah 2 – Konfigurasikan PDF Save Options untuk Mengekspor Bentuk  

Inti dari tutorial berada di sini. `PdfSaveOptions` memungkinkan Anda menentukan bagaimana konversi berperilaku. Menetapkan `setExportFloatingShapesAsInlineTag(true)` memaksa setiap bentuk mengambang diperlakukan sebagai elemen *inline* dalam struktur tag PDF. Itu berarti pembaca layar akan membaca bentuk tersebut dalam urutan yang sama dengan teks di sekitarnya, yang sering diperlukan untuk kepatuhan aksesibilitas.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**Kapan Anda akan mengaturnya ke `false`?**  
Jika PDF Anda ditujukan hanya untuk distribusi cetak dan Anda ingin bentuk tetap pada posisi aslinya tanpa memengaruhi urutan baca logis, Anda mungkin lebih memilih tagging level‑blok. Nilai default adalah `false`, jadi kami secara eksplisit mengaktifkan perilaku inline untuk tutorial ini.

---

## Langkah 3 – Simpan Dokumen sebagai PDF  

Sekarang opsi sudah siap, panggil `save` dengan nama file target dan objek opsi. Perpustakaan menangani pekerjaan berat: mesin tata letak, penyematan font, dan pembuatan tag.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

Setelah pemanggilan selesai, Anda akan menemukan `shapes.pdf` di folder yang ditentukan. Buka di Adobe Acrobat atau penampil PDF apa pun yang menampilkan tag (biasanya di **File → Properties → Tags**) dan Anda akan melihat bahwa bentuk mengambang muncul sebagai tag inline.

---

## Contoh Lengkap yang Dapat Dijalankan  

Menggabungkan semuanya, berikut kelas Java mandiri yang dapat Anda kompilasi dan jalankan. Pastikan JAR Aspose.Words ada di classpath Anda.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Hasil yang diharapkan:**  
- File PDF berisi konten teks yang sama dengan DOCX asli.  
- Semua gambar mengambang atau kotak teks kini ditandai *inline*, artinya mereka muncul dalam urutan baca bukan sebagai blok terpisah.  
- Jika Anda membuka panel **Tags** PDF, Anda akan melihat elemen `<Figure>` yang berada di dalam `<Paragraph>`—tepatnya apa yang dijamin oleh `setExportFloatingShapesAsInlineTag(true)`.

---

## Pertanyaan yang Sering Diajukan & Kasus Tepi  

### 1️⃣ Apakah ini bekerja dengan file DOCX yang dilindungi kata sandi?  
Ya—cukup berikan kata sandi sebelum memuat:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Bagaimana dengan gambar SVG atau EMF di dalam file Word?  
Aspose.Words secara otomatis merasterisasi grafik vektor saat menyimpan ke PDF. Jika Anda memerlukan mereka tetap vektor, atur:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ Bagaimana cara saya mempertahankan hyperlink saat mengonversi?  
Tautan dipertahankan secara default. Namun, jika Anda menonaktifkan tag (`pdfOptions.setSaveFormat(SaveFormat.PDF)` tanpa opsi), Anda mungkin kehilangan struktur logis. Pertahankan objek `PdfSaveOptions` untuk mempertahankan baik tag maupun tautan.

### 4️⃣ Apakah saya dapat memproses batch folder berisi file DOCX?  
Tentu saja. Bungkus logika `DocxToPdfWithShapes` dalam loop yang mengiterasi `Files.list(Paths.get("YOUR_DIRECTORY"))`. Ingat untuk menangani pengecualian per file sehingga satu dokumen yang buruk tidak menghentikan seluruh proses.

---

## Tips dari Pengalaman Praktis  

* **Waspadai font yang hilang.** Jika DOCX sumber menggunakan font khusus yang tidak terpasang di server, PDF akan mengganti dengan font cadangan, yang berpotensi merusak tata letak. Gunakan `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` untuk memaksa penyematan.  
* **Pengujian aksesibilitas.** Setelah konversi, jalankan **Accessibility Checker** di Acrobat. Tagging inline biasanya meningkatkan skor, tetapi Anda mungkin masih perlu menambahkan teks alternatif ke gambar secara manual.  
* **Tip kinerja:** Untuk dokumen besar (100+ halaman), aktifkan `pdfOptions.setMemoryOptimization(true)` untuk mengurangi penggunaan heap.

---

## Konfirmasi Visual  

Di bawah ini adalah tangkapan layar cepat PDF yang dibuka di Adobe Acrobat, menampilkan bentuk yang ditandai inline disorot di panel **Tags**.

![contoh output konversi docx ke pdf](image.png)

*Teks alternatif: contoh output konversi docx ke pdf yang menunjukkan tag bentuk inline.*

---

## Kesimpulan  

Anda kini tahu **cara mengonversi DOCX ke PDF** sambil mengontrol cara objek mengambang diekspor. Dengan mengaktifkan atau menonaktifkan `setExportFloatingShapesAsInlineTag`, Anda memutuskan apakah bentuk menjadi bagian dari urutan baca atau tetap sebagai blok independen—penting untuk aksesibilitas dan keakuratan visual.  

Dari sini Anda dapat:

* **Menyimpan Word sebagai PDF** secara massal untuk pengarsipan.  
* Bereksperimen dengan `PdfSaveOptions` lain seperti `setCompliance(PdfCompliance.PDF_A_1B)` untuk preservasi jangka panjang.  
* Selami lebih dalam **cara mengekspor bentuk** dengan menjelajahi dokumentasi lengkap Aspose.Words atau mencoba flag `setExportDocumentStructure(true)` untuk pohon tag yang lebih kaya.

Cobalah, sesuaikan opsi-opsinya, dan biarkan PDF Anda terlihat persis seperti yang Anda inginkan. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}