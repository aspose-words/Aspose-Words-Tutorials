---
category: general
date: 2026-10-20
description: Buat file DOCX kosong secara programatis dan sematkan tombol perintah
  menggunakan Java. Pelajari kode lengkap untuk membuat dokumen Word, menyimpan Word
  dengan tombol, dan mengatur caption tombol perintah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: id
lastmod: 2026-10-20
og_description: Buat file DOCX kosong secara programatis dan sematkan tombol perintah.
  Ikuti panduan Java langkah demi langkah ini untuk menyimpan Word dengan tombol dan
  mengatur caption tombol perintah.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Buat DOCX kosong secara programatis – tambahkan tombol perintah
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Buat DOCX kosong secara programatis dan tambahkan tombol perintah
url: /id/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat DOCX kosong secara programatis dan tambahkan tombol perintah

Jika Anda perlu **membuat DOCX kosong secara programatis**, tutorial ini menunjukkan cara menyematkan tombol perintah langsung ke dalam file. Anda akan mendapatkan *kode membuat dokumen word* lengkap yang menyimpan dokumen Word dengan tombol, memungkinkan Anda **mengatur caption tombol perintah**, dan bekerja dengan pustaka Aspose.Words for Java terbaru.

Menyematkan kontrol interaktif dalam file DOCX berguna ketika Anda ingin mendistribusikan templat yang memicu makro, meluncurkan program eksternal, atau sekadar membimbing pengguna dengan tombol “Click Me” yang dapat diklik. Langkah‑langkah di bawah ini mencakup semua hal mulai dari menginisialisasi dokumen kosong hingga menyimpan file akhir ke disk.

## Prasyarat

* Java 17 atau yang lebih baru terinstal.
* Maven (atau alat build pilihan Anda) untuk mengelola dependensi.
* Aspose.Words for Java 23.9 atau lebih baru. Tambahkan dependensi ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Sebuah IDE seperti IntelliJ IDEA atau VS Code (editor apa pun yang mendukung Java dapat digunakan).

## Buat DOCX kosong secara programatis – langkah demi langkah

Bagian-bagian berikut memecah proses menjadi langkah‑langkah yang jelas dan bernomor. Setiap langkah menjelaskan **mengapa** langkah tersebut diperlukan, bukan hanya **apa** yang harus diketik.

### Langkah 1: Inisialisasi dokumen kosong baru

Dokumen kosong adalah kanvas tempat Anda akan menempatkan tombol perintah. Aspose.Words menyediakan kelas `Document` untuk tujuan ini.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Mengapa ini penting*: Memulai dengan `Document` yang kosong memastikan tidak ada pemformatan tersembunyi atau kontrol yang sudah ada yang mengganggu tombol yang akan Anda tambahkan nanti.

### Langkah 2: Siapkan `DocumentBuilder`

`DocumentBuilder` adalah pembantu yang memungkinkan Anda menyisipkan konten, termasuk kontrol OLE, tanpa harus berurusan dengan manipulasi node tingkat rendah.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting*: Builder mempertahankan posisi kursor saat ini, sehingga tombol akan ditempatkan tepat di lokasi yang Anda tentukan.

### Langkah 3: Sisipkan tombol perintah OLE

Word memperlakukan kontrol interaktif sebagai objek OLE (Object Linking and Embedding). Aspose.Words mengekspos `Forms2OleControl` untuk hal ini.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Mengapa ini penting*: Menyisipkan kontrol membuat placeholder yang kemudian dapat Anda konfigurasikan (tipe, caption, posisi).

### Langkah 4: Konfigurasikan tombol – tipe, caption, dan lokasi

Anda harus menentukan tipe kontrol (`COMMANDBUTTON`), mengatur caption yang terlihat oleh pengguna, dan menempatkannya di halaman.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Mengapa ini penting*:  
* **Type** memberi tahu Word bahwa kontrol berperilaku seperti tombol yang dapat diklik.  
* **Caption** adalah teks yang dilihat pengguna; mengubahnya adalah cara Anda **mengatur caption tombol perintah**.  
* **Left** dan **Top** mengontrol penempatan tepat, yang penting ketika Anda **menambahkan tombol perintah word** dokumen yang memerlukan tata letak presisi.

### Langkah 5: Simpan dokumen dengan tombol yang disematkan

Akhirnya, tulis file ke disk. File yang dihasilkan dapat dibuka di Microsoft Word, di mana tombol akan berfungsi sepenuhnya.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Mengapa ini penting*: Langkah ini **menyimpan Word dengan tombol** sehingga kontrol tetap ada di semua mesin. File dapat didistribusikan sebagai templat atau digunakan dalam pipeline pembuatan laporan otomatis.

## Contoh lengkap yang berfungsi

Salin seluruh kelas di bawah ini ke dalam file bernama `CommandButtonDemo.java`, sesuaikan `YOUR_DIRECTORY` ke jalur yang nyata, dan jalankan dengan `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Hasil yang diharapkan

Ketika Anda membuka `CommandButton.docx` di Microsoft Word:

* Dokumen sepenuhnya kosong kecuali ada tombol dengan label **Click Me**.
* Mengklik tombol akan menampilkan perilaku default Word (tidak melakukan apa‑apa kecuali makro terlampir), mengonfirmasi bahwa kontrol OLE telah disematkan dengan benar.

## Pertanyaan umum & kasus tepi

| Question | Answer |
|----------|--------|
| **Apakah saya dapat mengubah ukuran tombol?** | Ya. Gunakan `commandButton.setWidth(double)` dan `commandButton.setHeight(double)` untuk menyesuaikan dimensi dalam poin. |
| **Bagaimana jika saya membutuhkan makro yang terlampir pada tombol?** | Tombol itu sendiri hanyalah kontrol OLE. Anda harus menambahkan makro VBA ke dokumen secara manual atau melalui utilitas `addMacro` pada API `Document` Aspose.Words. |
| **Apakah tombol akan berfungsi di LibreOffice?** | LibreOffice mendukung kontrol OLE terbatas. Tombol muncul, tetapi perilaku kliknya mungkin berbeda. |
| **Bagaimana cara menambahkan beberapa tombol?** | Ulangi Langkah 3‑4 dengan instance `Forms2OleControl` baru. Sesuaikan `setLeft`/`setTop` untuk setiap tombol agar tidak tumpang tindih. |
| **Apakah kode ini kompatibel dengan .NET?** | Logika yang sama berlaku, tetapi Anda akan menggunakan kelas `Aspose.Words` untuk .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Tips dari lapangan

* **Pro tip:** Gunakan `builder.moveToDocumentEnd()` sebelum menyisipkan tombol jika Anda menginginkannya berada di akhir dokumen, terlepas dari konten sebelumnya.
* **Waspadai:** Nilai `Left`/`Top` yang sangat kecil dapat menempatkan tombol di luar area yang dapat dicetak, membuatnya tidak terlihat di tampilan tata letak Word.
* **Catatan kinerja:** Menyisipkan banyak kontrol OLE dapat meningkatkan ukuran file. Jika Anda hanya membutuhkan petunjuk visual, pertimbangkan menggunakan `Shape` biasa dengan hyperlink sebagai gantinya.

## Kesimpulan

Anda sekarang tahu cara **membuat DOCX kosong secara programatis** dan menyematkan tombol perintah yang berfungsi penuh menggunakan Java. Tutorial ini mencakup seluruh alur kerja *kode membuat dokumen word*, menunjukkan cara **menyimpan Word dengan tombol**, memperlihatkan cara yang benar untuk **menambahkan elemen tombol perintah word**, dan menjelaskan cara **mengatur caption tombol perintah**.

Dari sini Anda dapat:

* Menambahkan lebih banyak kontrol OLE (checkbox, combo box) untuk formulir yang lebih kaya.
* Menempelkan makro VBA agar tombol melakukan aksi khusus.
* Menggabungkan teknik ini dengan mail‑merge dokumen untuk templat dinamis dan interaktif.

Silakan bereksperimen dengan gaya tombol, posisi, dan kontrol tambahan untuk menyesuaikan kebutuhan bisnis spesifik Anda. Selamat coding

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat dokumen word kosong dengan tombol perintah – panduan langkah demi langkah](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Cara Menyisipkan Tombol ActiveX di Word – Atur Caption Tombol](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Buat Dokumen Word Kosong dengan Java – Panduan Lengkap Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}