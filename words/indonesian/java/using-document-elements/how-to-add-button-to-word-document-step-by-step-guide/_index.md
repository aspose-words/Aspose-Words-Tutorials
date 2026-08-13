---
category: general
date: 2026-07-20
description: Cara menambahkan tombol ke dokumen Word menggunakan Aspose.Words. Pelajari
  cara menyisipkan tombol Forms2OleControl dengan DocumentBuilder dalam hitungan menit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: id
lastmod: 2026-07-20
og_description: Cara menambahkan tombol ke dokumen Word dengan Aspose.Words. Ikuti
  panduan praktis ini untuk menyematkan Forms2OleControl CommandButton menggunakan
  Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Cara Menambahkan Tombol ke Dokumen Word – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Cara Menambahkan Tombol ke Dokumen Word – Panduan Langkah demi Langkah
url: /id/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menambahkan Tombol ke Dokumen Word – Tutorial Lengkap Aspose.Words

Pernah bertanya-tanya **cara menambahkan tombol ke dokumen Word** tanpa membuka UI dan mengklik‑klik? Anda bukan satu‑satunya. Banyak pengembang perlu menyematkan kontrol interaktif secara programatik—bayangkan tombol “Submit” dalam sebuah templat yang nanti diisi oleh pengguna akhir. Kabar baik? Dengan Aspose.Words untuk Java Anda dapat melakukannya dalam beberapa baris kode.

Dalam tutorial ini kami akan membimbing Anda melalui langkah‑langkah tepat untuk menyisipkan `Forms2OleControl` berjenis **CommandButton** menggunakan `DocumentBuilder`. Pada akhir tutorial Anda akan memiliki file `.docx` siap pakai yang menampilkan tombol dapat‑klik berlabel “Click Me”. Tidak ada misteri, hanya kode yang jelas dan alasan di balik setiap baris.

## Apa yang Akan Anda Pelajari

- Cara membuat dokumen Word baru dari awal.
- Cara menggunakan **DocumentBuilder** untuk menempatkan **Forms2OleControl**.
- Mengapa Anda harus mengatur caption tombol dan ukuran seperti yang kami lakukan.
- Cara menyimpan dan memverifikasi hasil.
- Jebakan umum (misalnya, pustaka yang hilang, tipe kontrol yang tidak didukung) dan cara menghindarinya.

**Prasyarat** – Anda memerlukan Java 8+ (atau lebih baru) dan pustaka Aspose.Words untuk Java (versi 23.12 atau lebih baru). IDE seperti IntelliJ IDEA atau Eclipse akan mempermudah, tetapi editor teks apa pun juga dapat digunakan.

---

## Langkah 1: Siapkan Proyek Anda dan Impor Dependensi

Sebelum kode apa pun dijalankan, Maven (atau Gradle) harus tahu dari mana mengambil Aspose.Words. Tambahkan potongan kode berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Jika Anda lebih suka Gradle, setaraannya adalah:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Tips Pro:** Gunakan rilis terbaru; versi lama mungkin tidak memiliki API `Forms2OleControl`.

Setelah dependensi terpasang, Anda siap menulis kode Java.

## Langkah 2: Buat Dokumen Baru dan Dapatkan DocumentBuilder

Kelas `Document` mewakili seluruh paket `.docx`, sementara `DocumentBuilder` adalah kuas yang Anda gunakan untuk menambahkan konten ke dalamnya. Anggap `DocumentBuilder` sebagai “kursor” yang mengetahui di mana elemen berikutnya harus ditempatkan.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:** Menginisialisasi `Document` baru memberi Anda kanvas bersih. Builder secara otomatis mengarah ke paragraf pertama, sehingga Anda tidak perlu mengelola bagian atau halaman secara manual.

## Langkah 3: Sisipkan Forms2OleControl Berjenis CommandButton

Sekarang hadir bintang utama: `insertForms2OleControl`. Metode ini membuat kontrol OLE (Object Linking and Embedding) yang diperlakukan Word sebagai elemen formulir. Kami akan memberikan tiga argumen:

1. `Forms2OleControlType.COMMANDBUTTON` – memberi tahu Word bahwa kita menginginkan sebuah tombol.
2. `100` – lebar dalam poin (≈1,39 inci).
3. `30` – tinggi dalam poin (≈0,42 inci).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Cara kerjanya:** Di balik layar Aspose.Words membuat XML yang sesuai di bagian `word/document.xml`, merujuk pada objek OLE. Dimensi yang Anda berikan dihormati oleh mesin tata letak Word, sehingga tombol muncul tepat di posisi kursor builder.

## Langkah 4: Atur Caption (Teks) pada Tombol

Tombol tanpa label membingungkan—bayangkan tombol lift yang tidak bersuara. Metode `setCaption` mengatur teks yang terlihat:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Anda dapat mengubah caption menjadi apa saja: “Submit”, “Approve”, atau bahkan string yang dilokalkan. Caption disimpan dalam properti objek OLE, sehingga Word akan menampilkannya secara native.

## Langkah 5: Simpan Dokumen dan Verifikasi Hasil

Akhirnya, tulis file ke disk. Pilih folder yang Anda memiliki hak menulis; jika tidak, Anda akan mendapatkan `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Buka `button-demo.docx` di Microsoft Word. Anda akan melihat tombol berlabel **Click Me** yang ditempatkan di bagian atas dokumen. Mengkliknya di Word akan memicu perilaku OLE default (biasanya pesan placeholder, kecuali Anda mengaitkan macro).

## Kasus Pinggiran Umum dan Cara Menanganinya

| Situasi | Mengapa Terjadi | Solusi |
|-----------|----------------|-----|
| **Tidak ada tipe `Forms2OleControl`** | Versi Aspose.Words yang lebih lama tidak mengekspor enum ini. | Upgrade ke 23.12+ atau lebih baru. |
| **Tombol muncul sebagai gambar** | Pengaturan keamanan Word memblokir kontrol OLE. | Aktifkan “Trust access to the VBA project object model” di Trust Center, atau gunakan file `.docm` yang mendukung macro. |
| **Ukuran tidak tepat** | Kebingungan antara poin dan piksel. | Ingat 1 poin = 1/72 inci. Sesuaikan angka sesuai kebutuhan. |
| **Menyimpan menghasilkan `FileNotFoundException`** | Path tidak ada. | Pastikan direktori (`output/`) dibuat sebelum `doc.save`. Gunakan `new File("output").mkdirs();`. |

## Memperluas Contoh: Menambahkan Beberapa Tombol atau Kontrol Lain

Jika Anda membutuhkan lebih dari satu tombol, cukup pindahkan kursor builder dengan `builder.moveTo` atau `builder.writeln()` sebelum memanggil `insertForms2OleControl` lagi.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Anda juga dapat menyisipkan **CheckBox**, **ComboBox**, atau **ListBox** dengan mengganti `Forms2OleControlType.COMMANDBUTTON` dengan nilai enum yang sesuai (`CHECKBOX`, `COMBOBOX`, dll.). Parameter lebar/tinggi yang sama tetap berlaku.

## Bagaimana Ini Berintegrasi dengan Alur Kerja Otomasi Word yang Lebih Besar

- **Pembuatan Template:** Buat template kontrak yang mencakup tombol “Approve” untuk persetujuan selanjutnya.
- **Pelaporan:** Hasilkan laporan harian dengan tombol “Refresh Data” yang memicu macro.
- **Distribusi Formulir:** Kirim kuesioner dengan kontrol interaktif yang sudah terisi sebelumnya.

Semua skenario ini mendapat manfaat dari pendekatan **otomasi Word** yang kami tunjukkan. Dengan menyematkan kontrol secara programatik, Anda menghilangkan penyuntingan manual dan mengurangi kesalahan manusia.

## Kode Sumber Lengkap (Siap Salin‑Tempel)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Output yang diharapkan:** Saat Anda membuka `output/button-demo.docx` di Microsoft Word, Anda akan melihat dua tombol—“Click Me” dan “Submit”—ditumpuk secara vertikal di bagian atas file.

## Kesimpulan

Kami telah menjawab **cara menambahkan tombol ke dokumen Word** menggunakan Aspose.Words untuk Java, langkah demi langkah. Dimulai dari `Document` kosong, kami memanfaatkan **DocumentBuilder** untuk menyisipkan `Forms2OleControl` berjenis **CommandButton**, mengatur caption yang ramah, dan menyimpan hasilnya. Pendekatan ini dapat diperluas ke banyak kontrol dan terintegrasi dengan bersih ke dalam pipeline **otomasi Word** yang lebih luas.

Siap untuk tantangan berikutnya? Coba ganti tombol dengan **CheckBox**, atau kaitkan macro untuk merespons ketika pengguna mengklik tombol dalam file `.docm`. Pola yang sama berlaku—hanya ubah enum dan sesuaikan caption.

Jika Anda mengalami kendala, periksa kembali versi pustaka dan izin folder output. Jangan ragu untuk meninggalkan komentar di bawah dengan pertanyaan atau berbagi kasus penggunaan Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Menyisipkan Gambar Inline dalam Dokumen Word menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}