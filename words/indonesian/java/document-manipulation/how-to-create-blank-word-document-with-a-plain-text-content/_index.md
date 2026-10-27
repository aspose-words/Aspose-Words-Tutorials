---
category: general
date: 2026-10-23
description: Pelajari cara membuat dokumen Word kosong dan menyisipkan kontrol konten
  teks biasa (SDT) dengan placeholder menggunakan C#. Termasuk kode langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert control
- plain text content control
- how to add sdt
- add placeholder to tag
language: id
lastmod: 2026-10-23
og_description: Buat dokumen Word kosong dan sisipkan kontrol konten teks biasa (SDT)
  dengan placeholder menggunakan C#. Ikuti contoh lengkap yang dapat dijalankan.
og_image_alt: Screenshot showing a blank Word document with a highlighted plain text
  content control
og_title: Buat dokumen Word kosong dan tambahkan kontrol konten teks biasa – panduan
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create a blank Word document and insert a plain text content
    control (SDT) with a placeholder using C#. Includes step‑by‑step code.
  headline: How to create blank Word document with a plain text content control in
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- ContentControl
- WordAutomation
title: Cara membuat dokumen Word kosong dengan kontrol konten teks biasa di C#
url: /id/java/document-manipulation/how-to-create-blank-word-document-with-a-plain-text-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dengan kontrol konten teks biasa di C#

Jika Anda perlu **membuat dokumen Word kosong** secara programatis, panduan ini menunjukkan cara melakukannya secara tepat. Dengan menggunakan Aspose.Words untuk .NET, Anda dapat memulai dengan file kosong, menyisipkan StructuredDocumentTag (SDT) teks‑biasa, memberi judul, dan menambahkan placeholder yang berguna—semua dalam beberapa baris C#.

Tutorial ini mencakup setiap langkah yang Anda perlukan, mulai dari inisialisasi dokumen hingga menyimpan file `.docx` akhir. Pada akhir tutorial, Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat disisipkan ke proyek .NET mana pun.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) terpasang.
* Referensi ke paket NuGet **Aspose.Words**.
* IDE seperti Visual Studio 2022 atau Visual Studio Code.

Tidak ada pustaka tambahan yang diperlukan.

## Cara membuat dokumen Word kosong dan menambahkan kontrol konten teks biasa

Tugas utama pertama adalah membuat **dokumen Word kosong**. Ini memberi Anda kanvas bersih yang nantinya dapat Anda **sisipkan kontrol**.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini berhasil*: `Document()` membuat representasi dalam memori dari file Word tanpa halaman. `DocumentBuilder` adalah kelas pembantu yang memungkinkan Anda menambahkan paragraf, tabel, dan kontrol konten.

## Cara menyisipkan kontrol menggunakan DocumentBuilder

Setelah dokumen ada, Anda dapat **menyisipkan objek kontrol** langsung di posisi kursor. Untuk kontrol konten teks biasa, gunakan `InsertStructuredDocumentTag`.

```csharp
// Step 2: Insert a plain‑text StructuredDocumentTag (SDT) inline
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
```

*Penjelasan*:  
* `StructuredDocumentTagType.PlainText` memberi tahu Aspose.Words untuk membuat **kontrol konten teks biasa**.  
* `MarkupLevel.Inline` menempatkan kontrol di dalam paragraf saat ini, sehingga berperilaku seperti teks biasa.

## Cara menambahkan judul SDT dan teks placeholder

Kontrol yang diberi nama dengan baik lebih mudah ditemukan nanti, terutama ketika Anda perlu mengikat data atau melakukan validasi. Langkah **menambahkan placeholder ke tag** juga meningkatkan pengalaman pengguna.

```csharp
// Step 3: Give the SDT a meaningful title (used for identification)
sdt.Title = "CustomerName";

// Step 4: Add placeholder text so the user knows what to enter
sdt.AppendChild(new Run(doc, "Enter name here"));
```

*Mengapa ini penting*:  
* Properti `Title` adalah metadata yang dapat Anda query dengan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
* Placeholder (`Run` dengan “Enter name here”) muncul berwarna abu‑abu di Word, meminta pengguna akhir untuk menggantinya.

## Cara menyimpan dokumen dengan SDT

Akhirnya, simpan file ke disk. Path dapat berupa absolut atau relatif terhadap direktori kerja aplikasi Anda.

```csharp
// Step 5: Save the document with the SDT to a file
doc.Save("SDTExample.docx");
```

Saat Anda membuka **SDTExample.docx** di Microsoft Word, Anda akan melihat satu baris yang berisi placeholder berwarna abu‑abu di dalam kotak berbingkai—tepat **kontrol konten teks biasa** yang Anda buat.

### Output yang diharapkan

| Lokasi | Petunjuk visual |
|----------|------------|
| Di dalam paragraf pertama | Kotak persegi panjang berlabel “Enter name here” (placeholder) |

Anda dapat mengetikkan nama langsung ke dalam kotak; Word akan memperlakukan teks yang dimasukkan sebagai konten SDT.

## Menambahkan beberapa kontrol (opsional)

Jika Anda memerlukan lebih dari satu **kontrol konten teks biasa**, ulangi langkah 2‑4 dengan posisi `DocumentBuilder` yang baru. Misalnya, untuk menambahkan bidang alamat:

```csharp
builder.Writeln(); // Move to a new paragraph
StructuredDocumentTag addressSdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
addressSdt.Title = "CustomerAddress";
addressSdt.AppendChild(new Run(doc, "Enter address here"));
```

*Tips*: Gunakan `builder.Writeln()` untuk memulai paragraf baru sebelum menyisipkan SDT lain, sehingga tata letak tetap rapi.

## Kesalahan umum dan cara menghindarinya

| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| Teks placeholder menghilang setelah disimpan | SDT dibuat dengan `MarkupLevel.Block` bukan `Inline` | Gunakan `MarkupLevel.Inline` untuk placeholder inline |
| Judul tidak dapat dicari | Judul tidak pernah diset atau diset setelah penyimpanan | Setel `sdt.Title` **sebelum** memanggil `doc.Save()` |
| Dokumen muncul kosong di Word | Tidak ada konten yang ditambahkan setelah membuat dokumen | Pastikan Anda menambahkan setidaknya satu paragraf atau kontrol sebelum menyimpan |

## Tips pro: Menggunakan kembali potongan kode dalam metode utilitas

Membungkus logika membuatnya dapat digunakan kembali di berbagai proyek:

```csharp
public static Document CreateDocumentWithPlainTextControl(string title, string placeholder)
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);

    StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
    sdt.Title = title;
    sdt.AppendChild(new Run(doc, placeholder));

    return doc;
}

// Usage
Document myDoc = CreateDocumentWithPlainTextControl("OrderNumber", "Enter order #");
myDoc.Save("OrderForm.docx");
```

*Mengapa ini membantu*: Metode tersebut mengisolasi logika **membuat dokumen Word kosong**, memungkinkan Anda menghasilkan banyak templat dengan judul dan placeholder berbeda tanpa menduplikasi kode.

## Langkah selanjutnya

Setelah Anda mengetahui **cara menyisipkan kontrol** dan **menambahkan placeholder ke tag**, Anda dapat menjelajahi:

* Mengikat SDT ke bagian XML khusus (`doc.CustomXmlParts`) – berguna untuk templat berbasis data.  
* Mengonversi dokumen ke PDF sambil mempertahankan kontrol konten.  
* Menggunakan nilai `StructuredDocumentTagType` lain seperti `Date`, `ComboBox`, atau `CheckBox` untuk formulir yang lebih kaya.

Setiap topik ini dibangun di atas pola inti yang ditunjukkan di sini.

---

**Ringkasan**

Tutorial ini memandu Anda melalui pembuatan **dokumen Word kosong**, penyisipan **kontrol konten teks biasa**, pemberian judul, dan penambahan placeholder yang berguna. Contoh lengkap yang dapat dijalankan dapat disalin ke proyek .NET mana pun, dan metode utilitas opsional menunjukkan cara memperluas pendekatan ini. Dengan fondasi ini, Anda siap membangun formulir dan templat berbasis Word yang canggih dalam C#.

---

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}