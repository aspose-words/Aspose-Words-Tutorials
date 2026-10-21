---
category: general
date: 2026-10-07
description: Pelajari cara menambahkan kontrol konten dalam dokumen Word dengan Aspose.Words.
  Panduan ini juga menjelaskan cara membuat kontrol konten untuk bidang ID karyawan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: id
lastmod: 2026-10-07
og_description: Tambahkan kontrol konten dalam dokumen Word menggunakan Aspose.Words.
  Ikuti tutorial lengkap ini untuk mempelajari cara membuat kontrol konten dan menambahkan
  bidang ID karyawan.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: Menambahkan kontrol konten di Word dengan Aspose.Words – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: Cara menambahkan kontrol konten Word dalam dokumen Word menggunakan Aspose.Words
url: /id/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan content control word dalam dokumen Word menggunakan Aspose.Words

Jika Anda perlu **menambahkan content control word** ke file Word, tutorial ini menunjukkan secara tepat cara melakukannya dengan pustaka Aspose.Words untuk .NET. Baik Anda membangun dokumen bergaya formulir maupun mengotomatisasi entri data, Anda akan belajar **cara membuat content control** yang menangkap ID karyawan dalam satu langkah.

Dalam panduan ini Anda akan:

* Membuat dokumen Word kosong secara programatis.  
* Menyisipkan Structured Document Tag (SDT) teks biasa yang berfungsi sebagai content control.  
* Mengisi kontrol dengan ID karyawan dan menyimpan file.  

Prasyarat satu-satunya adalah versi .NET terbaru (disarankan 4.6+) dan lisensi Aspose.Words (atau trial gratis). Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Menambahkan content control word dengan Aspose.Words

Langkah utama pertama adalah membuat content control itu sendiri. Di Aspose.Words sebuah **content control** direpresentasikan oleh kelas `StructuredDocumentTag`. Dengan menambahkan SDT ke dokumen, Anda secara efektif **menambahkan content control word** yang dapat diedit nanti di Microsoft Word atau diproses secara programatis.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting*: `DocumentBuilder` memberikan antarmuka mirip kursor yang memungkinkan Anda menyisipkan node (paragraf, tabel, SDT, dll.) pada posisi saat ini. Memulai dengan dokumen bersih memastikan content control muncul tepat di tempat yang Anda inginkan.

## Cara membuat content control untuk bidang ID karyawan

Selanjutnya, konfigurasikan SDT agar berfungsi sebagai content control teks biasa yang akan menampung pengidentifikasi karyawan. Properti `Title` adalah apa yang ditampilkan Word di panel **Properties**, sementara `PlaceholderName` memberikan petunjuk kepada pengguna.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*Mengapa ini penting*: Menetapkan `Title` menjadi **EmployeeID** membuat kontrol dapat menjelaskan dirinya sendiri, yang berguna ketika Anda kemudian mengekstrak nilai dengan `StructuredDocumentTag.GetText()`. Placeholder meningkatkan pengalaman pengguna akhir dengan menunjukkan format yang diharapkan.

### Menambahkan bidang employee id di dalam content control

Sekarang sisipkan SDT ke dalam dokumen pada lokasi builder saat ini dan tulis nomor karyawan default.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*Mengapa ini penting*: `InsertNode` menempatkan SDT dalam pohon dokumen. `Writeln` berikutnya menulis konten **di dalam** kontrol karena kursor builder masih berada dalam node SDT. Jika Anda memanggil `Writeln` sebelum menyisipkan SDT, teks akan muncul di luar kontrol.

## Menyimpan dokumen dan memverifikasi content control

Akhirnya, simpan dokumen ke disk. File `.docx` yang disimpan akan berisi content control yang dapat Anda buka di Microsoft Word untuk melihat placeholder dan ID karyawan default.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*Mengapa ini penting*: Menggunakan jalur absolut atau relatif memungkinkan Anda mengontrol di mana file disimpan. Aspose.Words secara otomatis menulis bagian XML yang diperlukan untuk content control, sehingga tidak ada langkah tambahan yang diperlukan.

### Langkah verifikasi cepat

1. Buka `EmployeeForm.docx` di Word.  
2. Klik kotak abu-abu yang bertuliskan **Enter ID** – seharusnya diganti oleh **12345**.  
3. Buka tab **Developer** → **Design Mode** untuk melihat properti kontrol (Title = *EmployeeID*).

Jika kontrol tidak muncul, periksa kembali bahwa Anda menggunakan Aspose.Words ≥ 23.10; versi sebelumnya memiliki tanda tangan konstruktor yang berbeda untuk `StructuredDocumentTag`.

## Variasi opsional dan kasus tepi

| Skenario | Cara menyesuaikan kode |
|----------|------------------------|
| **Gunakan kontrol rich‑text** alih-alih teks biasa | Ubah `SdtType.PlainText` menjadi `SdtType.RichText`. |
| **Tambahkan kontrol ke dokumen yang sudah ada** | Muat file dengan `new Document("Existing.docx")` dan tempatkan builder pada bookmark yang diinginkan sebelum menyisipkan SDT. |
| **Kunci content control sehingga pengguna tidak dapat mengedit nilai** | Set `sdt.LockContentControl = true;` setelah membuat SDT. |
| **Terapkan tag khusus untuk ekstraksi nanti** | Gunakan `sdt.Tag = "EmpIdTag";` dan kemudian ambil dengan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **Setel content control berulang (beberapa ID)** | Buat SDT di dalam baris tabel dan duplikat baris tersebut sesuai kebutuhan. |

**Tips pro**: Selalu dispose objek `Document` (atau bungkus dalam blok `using`) saat bekerja di layanan yang berjalan lama untuk membebaskan sumber daya native dengan cepat.

## Kesimpulan

Anda kini tahu cara **menambahkan content control word** ke dokumen Word menggunakan Aspose.Words, cara **membuat content control** yang menangkap pengidentifikasi karyawan, dan cara **menambahkan bidang employee id** secara programatis. Dengan mengikuti langkah‑langkah di atas, Anda dapat menyematkan bidang terstruktur yang dapat diedit ke dalam dokumen apa pun yang dihasilkan, memudahkan pengumpulan atau penampilan data dalam format yang konsisten.

Selanjutnya, jelajahi topik terkait seperti **mengikat content control ke data XML**, **membuat content control berulang untuk tabel**, atau **menggunakan API Aspose.Words untuk mengekstrak nilai dari kontrol yang telah diisi**. Ekstensi ini memungkinkan Anda membangun formulir Word berbasis data yang lengkap tanpa pernah membuka file secara manual. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menambahkan Konten Menggunakan Document Builder di Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/)
- [Menambahkan Form Field Combo Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Menambahkan Form Field Check Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}