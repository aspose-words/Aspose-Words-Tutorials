---
category: general
date: 2026-06-27
description: Pelajari cara menangkap peringatan substitusi font di Java menggunakan
  Aspose.Words. Tutorial langkah demi langkah ini juga mencakup callback peringatan
  dan penggunaan LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: id
og_description: Tangkap peringatan substitusi font di Java dengan Aspose.Words. Ikuti
  panduan ini untuk mengatur callback peringatan, menggunakan LoadOptions, dan menangani
  font yang hilang.
og_title: Tangkap Peringatan Substitusi Font di Java – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Menangkap Peringatan Penggantian Font di Java dengan Aspose.Words – Panduan
  Lengkap
url: /id/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangkap Peringatan Substitusi Font di Java dengan Aspose.Words – Panduan Lengkap

Pernahkah Anda perlu **menangkap peringatan substitusi font** saat memuat DOCX yang menggunakan jenis huruf eksotis? Anda bukan satu-satunya. Dalam banyak proyek dunia nyata—seperti generator laporan otomatis atau konverter dokumen batch—font yang hilang memicu substitusi diam‑diam yang dapat merusak kesetiaan tata letak.  

Untungnya, Aspose.Words memberikan cara yang bersih untuk mendengarkan peringatan tersebut. Dalam tutorial ini kami akan menuntun Anda melalui konfigurasi **LoadOptions**, menghubungkan **callback peringatan Aspose.Words**, dan mencetak setiap notifikasi *substitusi font* ke konsol. Pada akhir tutorial Anda akan tahu persis kapan sebuah font telah diganti dan bagaimana menanggapinya secara programatik.

> **Apa yang akan Anda dapatkan:** cuplikan kode Java yang dapat dijalankan sepenuhnya, penjelasan *mengapa* setiap bagian penting, serta tip untuk menangani kasus tepi seperti direktori font khusus.

## Prasyarat & Apa yang Anda Butuhkan

Sebelum kita melanjutkan, pastikan Anda memiliki:

- Java 8 atau yang lebih baru terpasang (kode ini juga berfungsi dengan Java 11+).
- JAR Aspose.Words for Java terbaru (unduh dari situs resmi atau Maven Central).
- File DOCX yang merujuk pada font yang tidak terpasang di mesin Anda (misalnya *font‑rich.docx* yang dapat Anda temukan di set demo Aspose).
- IDE yang memadai (IntelliJ IDEA, Eclipse, atau bahkan VS Code dengan ekstensi Java).

Tidak ada pustaka eksternal selain Aspose.Words yang diperlukan, dan contoh dijalankan dalam metode `main` biasa.

## Langkah 1: Siapkan LoadOptions – Titik Masuk untuk Pemuatan Kustom

`LoadOptions` adalah kantong konfigurasi Aspose.Words yang memberi tahu perpustakaan *bagaimana* membaca dokumen. Secara default ia menggantikan font yang hilang secara diam‑diam, tetapi Anda dapat mengubah perilaku tersebut dengan callback peringatan.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Mengapa ini penting:** Tanpa `LoadOptions`, dokumen dimuat secara tenang, dan Anda kehilangan visibilitas terhadap font yang hilang. Dengan membuat sebuah instance, Anda memperoleh hook untuk sistem peringatan.

## Langkah 2: Definisikan Callback Peringatan untuk *Menangkap Peringatan Substitusi Font*

Aspose.Words mengirimkan peristiwa peringatan melalui antarmuka `IWarningCallback`. Implementasikan secara inline (atau sebagai kelas terpisah) dan saring untuk `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Penjelasan:**  
- `info.getWarningType()` memberi tahu Anda kategori peringatannya.  
- `WarningType.FONT_SUBSTITUTION` adalah nilai enum yang kami butuhkan.  
- `info.getDescription()` berisi pesan yang dapat dibaca manusia, misalnya *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Dengan mencetak deskripsi, Anda **menangkap peringatan substitusi font** secara real‑time.

## Langkah 3: Muat Dokumen Menggunakan LoadOptions yang Telah Dikonfigurasi

Sekarang callback sudah terpasang, muat DOCX Anda. Callback peringatan akan otomatis dipicu selama proses parsing.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya ke file uji Anda. Ketika konstruktor `Document` dijalankan, setiap font yang hilang memicu callback yang telah didefinisikan sebelumnya, dan Anda akan melihat pesan substitusi di konsol.

## Langkah 4: Verifikasi Dokumen yang Dimuat (Opsional tetapi Membantu)

Setelah memuat, Anda mungkin ingin memastikan integritas dokumen—jumlah halaman, ekstraksi teks, dll. Langkah ini tidak wajib untuk menangkap peringatan, tetapi membantu Anda melihat dampak substitusi.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Jika sebuah font digantikan, tata letak mungkin bergeser sedikit; memeriksa jumlah halaman dapat mengungkap perubahan tersebut.

## Langkah 5: Lanjutan – Menangani Font yang Digantikan Secara Programatik

Terkadang Anda tidak hanya ingin mencatat peringatan—Anda mungkin perlu menyematkan font cadangan atau menyesuaikan gaya. Berikut pola cepat yang dapat Anda terapkan.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Dengan mengarahkan Aspose.Words ke folder yang berisi font asli, Anda dapat *mencegah* substitusi sama sekali. Jika folder tersebut tidak ada, callback peringatan tetap menangkap peristiwa, memberi Anda strategi cadangan.

## Contoh Lengkap yang Dapat Dijalankan

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Output konsol yang diharapkan** (ketika font yang hilang ditemukan):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Jika semua font tersedia, callback tetap diam—tidak ada yang dicetak, persis seperti yang diharapkan.

## Kesulitan Umum & Tips Profesional

| Kesulitan | Mengapa terjadi | Solusi |
|-----------|----------------|--------|
| **Callback tidak pernah dipanggil** | Anda lupa menempelkan callback ke `LoadOptions` **atau** menggunakan konstruktor default `Document` tanpa melewatkan `loadOptions`. | Selalu panggil `loadOptions.setWarningCallback(...)` **dan** gunakan overload `new Document(path, loadOptions)`. |
| **Terlalu banyak peringatan memenuhi log** | Dokumen besar dengan banyak font yang hilang menghasilkan satu peringatan per substitusi. | Saring lebih lanjut dengan memeriksa `info.getDescription()` untuk nama font tertentu, atau kumpulkan peringatan dalam daftar untuk diproses nanti. |
| **Font yang digantikan memengaruhi tata letak** | Font cadangan mungkin memiliki metrik berbeda (ukuran, spasi). | Sediakan folder font khusus (lihat Langkah 5) atau sesuaikan gaya dokumen setelah dimuat. |
| **Menjalankan di server tanpa tampilan** | Font fallback default mungkin bergantung pada font sistem yang tidak terpasang di server. | Sertakan font yang diperlukan bersama aplikasi Anda dan arahkan `FontSettings` ke folder tersebut. |

## Pertanyaan yang Sering Diajukan

**T: Apakah ini bekerja dengan PDF atau format lain?**  
J: Ya. Callback peringatan bersifat format‑agnostik; ia dipicu untuk jenis dokumen apa pun yang dimuat Aspose.Words (DOC, DOCX, RTF, HTML, dll.). Perbedaannya hanya pada set peringatan yang mungkin muncul.

**T: Bisakah saya menangkap jenis peringatan lain, seperti peringatan *resolusi gambar*?**  
J: Tentu saja. Di dalam metode `warning`, periksa `info.getWarningType()` untuk nilai enum lain seperti `WarningType.IMAGE_RESOLUTION`. Kemudian tangani sesuai kebutuhan.

**T: Bagaimana jika saya membutuhkan daftar font yang digantikan setelah dokumen dimuat?**  
J: Simpan setiap `info.getDescription()` dalam `List<String>` di dalam callback. Setelah pemuatan selesai, Anda akan memiliki koleksi yang dapat Anda log, kirim ke layanan pemantauan, atau gunakan untuk memicu rutin pengunduhan font.

## Kesimpulan

Anda kini tahu **cara menangkap peringatan substitusi font** di Java menggunakan Aspose.Words, mengapa setiap bagian penting, dan bagaimana memperluas solusi untuk skenario dunia nyata. Dengan memanfaatkan `LoadOptions`, sebuah `callback peringatan Aspose.Words`, dan opsional `FontSettings`, Anda memperoleh visibilitas penuh terhadap font yang hilang dan dapat menjaga pipeline konversi dokumen Anda tetap dapat diandalkan.

Siap untuk langkah selanjutnya? Coba ganti `System.out.println` dengan logger seperti SLF4J, atau integrasikan daftar peringatan ke UI yang memberi peringatan kepada pengguna sebelum mereka menyelesaikan konversi batch. Anda juga dapat menjelajahi **callback peringatan Aspose.Words** untuk jenis peringatan lain, seperti *fitur yang tidak didukung* atau *peringatan gambar resolusi tinggi*.  

Selamat coding, semoga PDF Anda tidak pernah mengalami pertukaran font yang tak terduga lagi! 

![Tangkapan layar yang menunjukkan output konsol dari peringatan substitusi font yang ditangkap](image-placeholder.png "capture font substitution warnings")


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Aktifkan Peringatan Substitusi Font di Aspose.Words – Panduan Lengkap](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cara Mengatur LoadOptions di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cara Membuat Dokumen PDF dengan Aspose.Words untuk Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}