---
category: general
date: 2026-07-16
description: Atur ukuran tombol secara programatis dalam dokumen Word menggunakan
  Aspose.Words untuk Java. Pelajari cara menyisipkan tombol ActiveX, mengatur lokasi
  tombol, dan lainnya.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: id
lastmod: 2026-07-16
og_description: Atur ukuran tombol dalam dokumen Word menggunakan Java. Panduan langkah
  demi langkah ini menunjukkan cara menyisipkan tombol ActiveX, mengatur lokasi tombol,
  dan menambahkan tombol secara programatik.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Atur Ukuran Tombol di Word dengan Java – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Atur Ukuran Tombol di Word dengan Java – Panduan Lengkap Aspose.Words
url: /id/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengatur Ukuran Tombol di Word dengan Java – Panduan Lengkap Aspose.Words

Pernah bertanya-tanya bagaimana cara **set button size** di dalam file Word tanpa membuka UI? Anda bukan satu‑satunya. Ketika Anda perlu menghasilkan dokumen berisi formulir secara dinamis—misalnya paket orientasi dengan tombol “Submit”—melakukannya secara programatik menghemat berjam‑jam pekerjaan manual.

Dalam tutorial ini kita akan membahas langkah‑langkah tepat untuk **insert ActiveX button**, menyesuaikan dimensinya, menempatkannya dengan benar, dan akhirnya menyimpan file. Pada akhir tutorial Anda akan dapat **programmatically add button** ke dokumen Word apa pun menggunakan Aspose.Words untuk Java.

## Prasyarat – Apa yang Anda Butuhkan Sebelum Memulai

- **Java Development Kit (JDK) 8+** – kode dapat dijalankan pada JDK terbaru mana pun.  
- **Aspose.Words for Java** library (unduh JAR terbaru dari situs resmi).  
- **IDE** pilihan Anda—IntelliJ IDEA, Eclipse, atau bahkan editor teks sederhana sudah cukup.  
- Familiaritas dasar dengan sintaks Java; tidak diperlukan pengetahuan mendalam tentang otomatisasi Word.

> *Pro tip:* Letakkan JAR Aspose.Words pada classpath proyek Anda, jika tidak Anda akan mendapatkan `ClassNotFoundException` saat mencoba mengimpor `com.aspose.words.*`.

## Langkah 1: Buat Dokumen Word Baru

Hal pertama yang kita lakukan adalah membuat dokumen kosong dan sebuah `DocumentBuilder`. Anggap builder sebagai pena yang memungkinkan kita menggambar apa saja di dalam file.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mengapa ini penting:** Objek `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` adalah mesin kerja yang memungkinkan kita menyisipkan paragraf, tabel, dan—ya—kontrol ActiveX.

## Langkah 2: Sisipkan ActiveX Button – Momen “Insert ActiveX Button”

Sekarang kita benar‑benarnya **insert activex button** ke dalam dokumen. Aspose.Words menyediakan metode praktis `insertForms2OleControl` yang mengembalikan objek `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Apa yang terjadi di balik layar?* `Forms2OleControlType.COMMAND_BUTTON` memberi tahu Word bahwa kita menginginkan CommandButton klasik, sama seperti yang Anda tarik dari tab Developer di UI.

## Langkah 3: Atur Ukuran dan Lokasi Tombol – Logika Inti “Set Button Size”

Inilah tempat kata kunci utama bersinar. Kita akan **set button size** dan juga **set button location** sehingga kontrol muncul tepat di tempat yang diinginkan pada halaman.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Mengapa Anda harus peduli:** Point adalah satuan ukuran native di Word (1 point = 1/72 inci). Dengan mengatur `setLeft`, `setTop`, `setWidth`, dan `setHeight` Anda mendapatkan kontrol pixel‑perfect—tidak lagi “kelihatan tepat di layar saya tapi tidak di printer”.

> *Jebakan umum:* Lupa mengatur lebar atau tinggi akan membuat tombol tetap pada ukuran default, yang bisa terlalu kecil untuk diklik. Selalu tentukan keduanya.

## Langkah 4: Simpan Dokumen – “Create Word Document Button” Selesai

Akhirnya, kita menulis file ke disk. Nama langkah ini menunjukkan bahwa kita **creating a Word document button** di dalam .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Saat Anda membuka `CommandButtonDemo.docx` di Microsoft Word, Anda akan melihat tombol **Submit** yang ditempatkan 100 pt dari tepi kiri dan 150 pt dari atas, berukuran 80 × 30 pt. Mengkliknya di UI akan memicu perilaku default ActiveX (yang kemudian dapat Anda hubungkan dengan VBA jika diperlukan).

### Screenshot Output yang Diharapkan

![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png "Screenshot of a Word file where the button size has been set using Aspose.Words for Java")

*Alt text:* set button size in a Word document using Java

## Langkah 5 (Opsional): Tambahkan Lebih Banyak Kontrol atau Gaya pada Tombol

Jika Anda perlu **programmatically add button** lebih dari satu tombol Submit, cukup ulangi blok penyisipan dengan nama dan caption baru. Anda juga dapat menyesuaikan font, warna latar, atau bahkan mengikat makro VBA nanti.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* Jaga semua dimensi tombol tetap konsisten untuk tampilan profesional. Cara cepatnya adalah menyimpan lebar/tinggi dalam konstanta.

## Pertanyaan Umum & Kasus Pinggir

### “Apakah saya bisa mengatur ukuran tombol menggunakan sentimeter alih‑alih point?”
API Word hanya menerima point, tetapi Anda dapat mengonversi sentimeter ke point (`points = cm * 28.3465`). Buat metode bantu kecil jika Anda lebih suka satuan metrik.

### “Bagaimana jika saya ingin tombol muncul pada halaman tertentu?”
Setelah menyisipkan tombol, Anda dapat memindahkan kursor ke halaman tertentu menggunakan `builder.moveToPage(pageNumber)`. Sisipkan kontrol tepat setelah pemindahan, lalu atur lokasinya seperti contoh di atas.

### “Apakah ini bekerja dengan file .doc (Word 97‑2003)?”
Ya—Aspose.Words secara otomatis menangani format lama. Cukup ubah ekstensi file pada `doc.save("Demo.doc")`.

## Contoh Lengkap yang Dapat Dijalankan

Berikut adalah seluruh program yang dapat Anda salin‑tempel ke kelas Java dan jalankan langsung (asalkan JAR Aspose.Words berada di classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Jalankan program, buka `CommandButtonDemo.docx` yang dihasilkan, dan Anda akan melihat dua tombol dengan ukuran rapi siap untuk berinteraksi.

## Kesimpulan – Anda Telah Menguasai Pengaturan Ukuran Tombol di Word

Kami baru saja menelusuri solusi lengkap dari awal hingga akhir untuk **set button size** dan **set button location** menggunakan Aspose.Words untuk Java. Dengan mengikuti langkah‑langkah ini Anda dapat **insert activex button**, **programmatically add button** kontrol, dan pada akhirnya **create word document button** yang berperilaku persis seperti yang Anda butuhkan.

Apa selanjutnya? Coba sematkan tombol di dalam sel tabel, atau lampirkan makro VBA yang memvalidasi bidang formulir sebelum pengiriman. Pola yang sama berlaku untuk kontrol ActiveX lain seperti checkbox atau combo box—cukup ganti `Forms2OleControlType.COMMAND_BUTTON` dengan nilai enum yang sesuai.

Jika Anda menemui kendala, tinggalkan komentar di bawah. Selamat coding, dan nikmati kekuatan pembuatan dokumen Word otomatis!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to remove footers from Word documents using Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}