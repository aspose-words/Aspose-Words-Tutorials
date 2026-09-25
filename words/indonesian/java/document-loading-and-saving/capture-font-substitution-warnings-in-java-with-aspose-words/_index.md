---
category: general
date: 2026-01-11
description: Pelajari cara menangkap peringatan substitusi font menggunakan Aspose.Words
  untuk Java. Tutorial langkah demi langkah ini juga mencakup LoadOptions dan callback
  peringatan.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: id
og_description: Tangkap peringatan substitusi font dengan Aspose.Words untuk Java.
  Ikuti panduan ini untuk menyiapkan LoadOptions dan callback peringatan agar pemuatan
  dokumen menjadi andal.
og_title: Menangkap Peringatan Substitusi Font di Java – Tutorial Lengkap
tags:
- Aspose.Words
- Java
- Document Processing
title: Menangkap Peringatan Substitusi Font di Java dengan Aspose.Words – Panduan
  Lengkap
url: /id/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangkap Peringatan Substitusi Font – Tutorial Java Lengkap

Pernahkah Anda perlu **menangkap peringatan substitusi font** saat membuka dokumen Word dengan font yang hilang? Ini adalah masalah umum, terutama ketika Anda menghasilkan PDF atau mencetak di server yang tidak memiliki semua jenis huruf terpasang. Kabar baiknya? Aspose.Words untuk Java membuatnya mudah—cukup konfigurasikan objek `LoadOptions` dan sambungkan callback peringatan. Dalam panduan ini Anda akan melihat secara tepat cara melakukannya, mengapa hal ini penting, dan apa yang diharapkan ketika peringatan muncul.

Kami juga akan menyentuh topik terkait seperti **substitusi font Aspose.Words**, menggunakan **callback peringatan Java**, dan praktik terbaik untuk **penggunaan LoadOptions**. Pada akhir tutorial, Anda akan memiliki potongan kode siap‑jalankan yang mencatat setiap kejadian font yang hilang, sehingga proses selanjutnya tidak akan mengejutkan Anda.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- Java 17 (atau JDK terbaru lainnya) terpasang dan terkonfigurasi.
- Aspose.Words for Java 23.10 (atau lebih baru) di classpath Anda.
- Dokumen Word yang merujuk pada font yang tidak Anda miliki secara lokal (misalnya `DocWithMissingFont.docx`).
- Pemahaman dasar tentang blok try/catch Java—tidak ada yang rumit.

Jika ada yang belum familiar, jeda sejenak dan instal pustaka dari Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Setelah fondasi siap, mari masuk ke kode.

## Langkah 1: Siapkan Callback Peringatan untuk **Menangkap Peringatan Substitusi Font**

Hal pertama yang Anda perlukan adalah callback yang akan dipanggil Aspose.Words setiap kali menemukan font yang hilang. Di sinilah kita **menangkap peringatan substitusi font**. Callback ini mengimplementasikan antarmuka `IWarningCallback` dan memeriksa `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Mengapa ini penting:** Tanpa callback, Aspose.Words secara diam-diam mengganti font yang hilang dengan font default, dan Anda tidak akan tahu bahwa tampilan visual telah berubah. Dengan menangkap peringatan, Anda dapat mencatat, memberi peringatan, atau bahkan menghentikan proses pemuatan jika font yang hilang bersifat kritis.

## Langkah 2: Konfigurasikan **LoadOptions** dan Daftarkan Callback

Sekarang kita membuat instance `LoadOptions` dan melampirkan `FontWarningCallback` kami. Langkah ini penting untuk **penggunaan LoadOptions** dan memastikan setiap pemuatan dokumen melewati filter peringatan yang sama.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tip:** Anda dapat menggunakan kembali objek `LoadOptions` yang sama untuk beberapa dokumen, yang menghemat beberapa baris kode boilerplate dan menjamin penanganan **peringatan pemuatan dokumen** yang konsisten di seluruh aplikasi Anda.

## Langkah 3: Muat Dokumen dan Amati Output

Dengan callback yang sudah terhubung, cukup muat file Word Anda. Jika dokumen merujuk pada font yang tidak terpasang, callback akan dipicu dan mencetak detail ke konsol.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Output Konsol yang Diharapkan

Dengan asumsi `DocWithMissingFont.docx` merujuk pada font yang hilang *“Comic Sans MS”*, Anda akan melihat sesuatu seperti:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Jika dokumen **tidak mengandung font yang hilang**, konsol hanya akan menampilkan baris terakhir, mengonfirmasi bahwa callback Anda tidak menghasilkan positif palsu.

## Langkah 4: Menangani Kasus Tepi dan Kesalahan Umum

### Beberapa Font yang Hilang

Jika sebuah dokumen menggunakan beberapa font yang tidak tersedia, callback akan dijalankan satu kali per font. Anda akan menerima serangkaian pesan, masing‑masing dengan `source` dan `description`‑nya. Tidak diperlukan kode tambahan—pastikan saja sistem pencatatan Anda dapat menangani pemanggilan berurutan yang cepat.

### Menekan Peringatan

Dalam kasus yang jarang, Anda mungkin ingin mengabaikan substitusi tertentu (mis., Anda tahu fallback tertentu dapat diterima). Perluas logika callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Keamanan Thread

`LoadOptions` Aspose.Words tidak thread‑safe secara default. Jika Anda memuat dokumen secara paralel, buat instance `LoadOptions` terpisah per thread, atau sinkronkan callback untuk menghindari kondisi balapan.

## Langkah 5: Memverifikasi Font yang Disubstitusi dalam Dokumen Hasil

Setelah pemuatan, Anda mungkin ingin memastikan bahwa substitusi memang terjadi. API memungkinkan Anda mengiterasi semua run dan memeriksa nama font efektif:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Potongan kode ini mencetak setiap run teks beserta font akhirnya. Ini merupakan pemeriksaan sanity yang berguna saat Anda membangun pipeline konversi PDF otomatis.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Simpan sebagai `FontSubstitutionInfo.java`, kompilasi dengan `javac`, dan jalankan `java FontSubstitutionInfo`. Anda akan melihat pesan peringatan (jika ada) diikuti oleh daftar run dan font akhirnya.

## Bantuan Visual

![Tangkapan layar output konsol yang menunjukkan peringatan substitusi font](/images/font-substitution-warning.png "contoh menangkap peringatan substitusi font")

*Alt text:* **capture font substitution warnings** – output konsol setelah memuat dokumen dengan font yang hilang.

## Kesimpulan

Anda kini tahu cara **menangkap peringatan substitusi font** menggunakan Aspose.Words untuk Java. Dengan mengonfigurasi objek `LoadOptions` dan menyediakan `IWarningCallback` khusus, Anda memperoleh visibilitas penuh terhadap setiap kejadian font yang hilang yang sebaliknya dapat memengaruhi tampilan dokumen secara diam‑diam. Teknik ini terhubung langsung ke penanganan **substitusi font Aspose.Words**, memastikan **peringatan pemuatan dokumen** yang dapat diandalkan, dan memberi Anda fleksibilitas untuk mencatat, memberi peringatan, atau menghentikan proses berdasarkan aturan bisnis Anda.

### Selanjutnya?

- Jelajahi pola **Java warning callback** untuk tipe peringatan lain (mis., `DEPRECATED_FEATURE`).
- Gabungkan pendekatan ini dengan **konversi PDF** untuk memastikan bahwa font yang disubstitusi tidak merusak tata letak.
- Selami lebih dalam penggunaan **LoadOptions**—coba dengan `Password`, `Encoding`, dan `ResourceLoadingCallback` untuk skenario yang lebih maju.

Jangan ragu untuk menyesuaikan callback, mengarahkan peringatan ke kerangka kerja logging, atau bahkan melempar pengecualian khusus jika font kritis tidak tersedia. Langit adalah batasnya, dan kini Anda memiliki fondasi yang kuat untuk membangun lebih lanjut.

Selamat coding, semoga dokumen Anda selalu ditampilkan persis seperti yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}