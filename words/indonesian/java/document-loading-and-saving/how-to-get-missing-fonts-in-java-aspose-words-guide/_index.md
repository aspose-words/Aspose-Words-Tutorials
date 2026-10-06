---
category: general
date: 2026-02-15
description: Pelajari cara mendapatkan font yang hilang saat memuat dokumen Word di
  Java menggunakan Aspose.Words. Termasuk callback peringatan dan penanganan substitusi
  font.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: id
og_description: Cara mendapatkan font yang hilang di Java dengan Aspose.Words. Temukan
  callback peringatan, penanganan substitusi font, dan praktik terbaik untuk pemrosesan
  dokumen.
og_title: Cara Mendapatkan Font yang Hilang di Java – Panduan Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Cara Mendapatkan Font yang Hilang di Java – Panduan Aspose.Words
url: /id/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendapatkan Font yang Hilang di Java – Panduan Aspose.Words

Pernah membuka dokumen Word di Java hanya untuk melihat penggantian font yang aneh dan bertanya-tanya **bagaimana cara mendapatkan font yang hilang**? Anda bukan yang pertama mengalami kejutan itu. Dalam banyak aplikasi perusahaan, peringatan font yang hilang dapat merusak kesetiaan visual laporan, kontrak, atau materi pemasaran.

Berita baiknya? Aspose.Words memberikan cara yang bersih untuk menangkap peringatan tersebut melalui callback, sehingga Anda dapat mencatat, mengganti, atau bahkan memberi peringatan kepada pengguna sebelum dokumen dirender. Dalam tutorial ini kami akan membahas contoh lengkap yang dapat dijalankan yang menunjukkan **bagaimana cara mendapatkan font yang hilang**, menjelaskan mengapa callback penting, dan mencakup beberapa trik kasus tepi yang mungkin Anda perlukan dalam proyek dunia nyata.

> **Pro tip:** Jika Anda sudah menggunakan Aspose.Words 22.12 atau yang lebih baru, API yang ditunjukkan di bawah ini berfungsi langsung tanpa konfigurasi tambahan.

---

![Diagram yang menggambarkan cara mendapatkan font yang hilang menggunakan callback peringatan Aspose.Words](how-to-get-missing-fonts-diagram.png "diagram cara mendapatkan font yang hilang")

## Apa yang Dibahas dalam Tutorial Ini

- Menyiapkan **callback peringatan Java LoadOptions** untuk menangkap peringatan substitusi font.  
- Menyaring peringatan sehingga Anda hanya melihat yang terkait dengan font yang hilang.  
- Mencetak laporan yang jelas dan dapat dibaca manusia tentang font mana yang diganti dan apa yang menggantikannya.  
- Tips untuk menangani dokumen besar, menyesuaikan tingkat peringatan, dan mengintegrasikan solusi ke dalam pipeline pemrosesan yang lebih besar.

Pada akhir panduan ini Anda akan dapat menjawab pertanyaan “**bagaimana cara mendapatkan font yang hilang**?” dengan potongan kode siap‑jalankan dan pemahaman yang kuat tentang mekanisme dasarnya.

### Prasyarat

- Java 8 atau yang lebih baru terpasang.  
- Perpustakaan Aspose.Words untuk Java (unduh dari situs resmi atau tambahkan melalui Maven/Gradle).  
- Dokumen Word yang merujuk pada font yang tidak terpasang di mesin Anda (misalnya `MissingFont.docx`).  

Jika Anda belum memiliki salah satu dari itu, dapatkan perpustakaannya sekarang—menambahkannya ke Maven semudah:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Langkah 1: Siapkan Koleksi untuk Peringatan Substitusi Font

Sebelum memuat dokumen, kita memerlukan tempat untuk menyimpan semua peringatan yang dikeluarkan oleh Aspose.Words. `ArrayList<WarningInfo>` bekerja dengan baik karena mempertahankan urutan dan memungkinkan kita mengiterasi nanti.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Mengapa ini penting:* Callback peringatan dapat dipicu puluhan kali untuk satu file—pikirkan setiap glyph yang hilang, setiap masalah gambar tersemat, dll. Dengan mengumpulkannya terlebih dahulu, Anda menjaga fase pemuatan tetap cepat dan menunda pemrosesan ke dalam loop yang terkontrol.

---

## Langkah 2: Konfigurasikan LoadOptions dengan Callback Peringatan

Aspose.Words memungkinkan Anda menyambungkan sebuah `IWarningCallback`. Di dalam callback, kami akan menambahkan setiap `WarningInfo` ke dalam daftar kami dari Langkah 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Penjelasan:* Metode `warning` dipanggil **secara sinkron** selama pemuatan dokumen. Dengan hanya memasukkan `WarningInfo` ke dalam `fontWarnings`, kami menghindari I/O berat (seperti mencatat ke file) yang dapat memperlambat pemuatan. Pola ini—koleksi‑lalu‑proses—adalah cara yang direkomendasikan untuk menangani batch peringatan yang besar.

---

## Langkah 3: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Sekarang kami benar‑benar membaca file Word. Jika dokumen berisi font yang tidak terpasang, Aspose.Words secara otomatis akan menggantinya dan memicu callback peringatan yang baru saja kami hubungkan.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Apa yang terjadi di balik layar?* Aspose.Words mem-parsing tabel font file, membandingkannya dengan font yang tersedia di OS host, dan untuk setiap entri yang hilang ia membuat `WarningInfo` dengan `WarningSource.FontSubstitution`. Sumber itu adalah kunci yang akan kami gunakan untuk mengisolasi peringatan font yang hilang.

---

## Langkah 4: Filter dan Tampilkan Hanya Peringatan Substitusi Font

Setelah pemuatan, `fontWarnings` mungkin berisi campuran pesan (misalnya fitur usang, masalah gambar). Kami hanya peduli pada font yang hilang, jadi kami mengiterasi daftar dan mencetak laporan singkat.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Contoh output**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Mengapa ini berguna:* Field `description` memberi tahu Anda font apa yang diminta dokumen, sementara `additionalInfo` memberi tahu font apa yang sebenarnya digunakan oleh Aspose.Words. Dengan data tersebut Anda dapat:

- Meminta pengguna untuk menginstal font yang hilang.  
- Secara program menanamkan font pengganti ke dalam dokumen (`doc.getFontInfos().add(...)`).  
- Mencatat peristiwa untuk audit kepatuhan.

---

## Menangani Kasus Tepi dan Variasi Umum

### 1. Menekan Peringatan Non‑Font

Jika Anda hanya menginginkan pesan terkait font, Anda dapat memperketat callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Ini mengurangi penggunaan memori saat memproses batch yang sangat besar.

### 2. Menyesuaikan Tingkat Keparahan Peringatan

Aspose.Words mengkategorikan peringatan berdasarkan `WarningType`. Untuk font yang hilang Anda biasanya akan melihat `WarningType.FontSubstitution`. Jika Anda perlu memperlakukan mereka sebagai kesalahan (misalnya, menghentikan pemuatan), lemparkan pengecualian di dalam callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Bekerja dengan Stream Alih-alih File

Kadang dokumen datang dari basis data atau permintaan HTTP. Pendekatan yang sama bekerja dengan `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Pastikan untuk menutup stream setelah pemuatan.

### 4. Menggunakan Folder Font Kustom

Jika Anda memiliki kumpulan font perusahaan yang disimpan di drive bersama, arahkan Aspose.Words ke folder tersebut:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Sekarang perpustakaan akan mencari di sana *sebelum* kembali ke font sistem, secara dramatis mengurangi jumlah peringatan font yang hilang.

---

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut kelas mandiri yang dapat Anda masukkan ke dalam proyek Java mana pun:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Jalankan program ini, dan Anda akan melihat daftar rapi setiap font yang harus diganti oleh Aspose.Words. Tanpa perpustakaan tambahan, tanpa sihir tersembunyi—hanya Java murni dan kekuatan API **Aspose.Words missing font**.

---

## Kesimpulan

Kami telah menjawab pertanyaan inti **bagaimana cara mendapatkan font yang hilang** dalam lingkungan Java menggunakan Aspose.Words. Dengan melampirkan callback peringatan `LoadOptions`, mengumpulkan objek `WarningInfo`, dan memfilter sumber `FontSubstitution`, Anda memperoleh visibilitas lengkap terhadap masalah terkait font sebelum proses rendering apa pun terjadi. Pendekatan ini dapat diskalakan dari utilitas satu‑file hingga pemroses batch besar, dan cukup fleksibel untuk mengakomodasi folder font kustom, penanganan tingkat keparahan, atau input berbasis stream.

Langkah selanjutnya? Coba tanamkan font pengganti langsung ke dalam dokumen (`doc.getFontInfos().add(...)`) sehingga file akhir benar‑benar mandiri, atau integrasikan laporan peringatan ke dalam dasbor pemantauan. Anda juga dapat menjelajahi topik terkait seperti **document processing Java**, **Aspose.Words font substitution warning**, dan **Java LoadOptions warning callback** untuk memperdalam keahlian Anda.

Selamat coding, dan semoga dokumen Anda selalu dirender dengan font yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}