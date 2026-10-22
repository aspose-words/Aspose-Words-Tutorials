---
category: general
date: 2026-10-13
description: Pelajari cara menambahkan tombol perintah secara programatis menggunakan
  Aspose.Words. Panduan ini juga menunjukkan cara membuat tombol dokumen Word dengan
  kode C# lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: id
lastmod: 2026-10-13
og_description: Tambahkan tombol perintah secara programatis ke dokumen Word menggunakan
  Aspose.Words. Ikuti tutorial lengkap ini untuk membuat tombol dokumen Word dengan
  C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Menambahkan tombol perintah secara programatik ke dokumen Word – panduan
  langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara menambahkan tombol perintah secara programatis di dokumen Word
url: /id/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan tombol perintah secara programatis dalam dokumen Word  

Jika Anda perlu **menambahkan tombol perintah secara programatis**, Aspose.Words menyediakan API yang bersih yang memungkinkan Anda menyematkan kontrol formulir OLE langsung ke dalam file .docx. Tutorial ini memandu Anda melalui setiap langkah yang diperlukan untuk **membuat tombol dokumen Word** yang berperilaku seperti tombol formulir biasa ketika dokumen dibuka di Microsoft Word.  

Anda akan belajar cara menyiapkan lingkungan pengembangan, menyisipkan tombol, mengkonfigurasi propertinya, dan memverifikasi hasilnya. Tidak diperlukan utilitas eksternal—hanya proyek .NET dan pustaka Aspose.Words untuk .NET.  

## Prasyarat  

Sebelum memulai, pastikan Anda memiliki:  

* .NET 6.0 SDK atau yang lebih baru terpasang.  
* Versi terbaru Aspose.Words untuk .NET (contoh menggunakan 23.12, tetapi rilis 22.x+ mana pun dapat digunakan).  
* IDE seperti Visual Studio 2022 atau Visual Studio Code.  

Kode ini berjalan di Windows, macOS, dan Linux karena Aspose.Words bersifat platform‑independen.  

## Langkah 1: Menyiapkan proyek dan merujuk Aspose.Words  

1. Buat proyek konsol baru:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Tambahkan paket NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Buka **Program.cs** dan ganti isinya dengan kerangka yang ditunjukkan pada langkah berikutnya.  

Menyiapkan proyek dengan cara ini memastikan bahwa kompilator dapat menemukan namespace `Aspose.Words` dan `Aspose.Words.Drawing.Forms` yang diperlukan untuk kontrol formulir.  

## Langkah 2: Menginisialisasi dokumen kosong dan DocumentBuilder  

Kelas `Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan API yang lancar untuk menambahkan konten.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Mengapa langkah ini penting* – Tanpa `DocumentBuilder` Anda tidak dapat menempatkan tombol secara tepat pada halaman. Builder juga menghormati lokasi kursor saat ini, memudahkan penyisipan beberapa kontrol nanti.  

## Langkah 3: Menyisipkan kontrol OLE tombol perintah  

Aspose.Words memperlakukan tombol perintah sebagai kontrol OLE tipe `ControlType.CommandButton`. Anda menentukan lokasinya dan ukurannya dengan `RectangleF` yang diukur dalam poin (1 poin = 1/72 inci).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Poin penting**  

* Asal persegi panjang (X, Y) relatif terhadap sudut kiri‑atas halaman.  
* Mengubah `Width` atau `Height` mengubah ukuran visual tombol.  
* `InsertForms2OleControl` mengembalikan objek `Forms2OleControl` yang dapat Anda konfigurasikan lebih lanjut.  

## Langkah 4: Mengkonfigurasi nama dan caption tombol  

**Nama** digunakan oleh mesin makro Word untuk mengidentifikasi kontrol, sementara **caption** adalah teks yang dilihat pengguna.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Jika Anda berencana menambahkan makro VBA nanti, gunakan nama yang deskriptif karena perekam makro Word merujuk properti ini.  

## Langkah 5: (Opsional) Simpan dokumen dan verifikasi hasil  

Menyimpan file memungkinkan Anda membukanya di Microsoft Word untuk memastikan tombol muncul dan berfungsi.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Saat Anda membuka *CommandButtonDemo.docx* di Word, Anda akan melihat tombol berlabel **Submit** yang ditempatkan kira‑kira 1,4 inci dari margin kiri dan 2,1 inci dari atas halaman. Mengklik tombol tidak melakukan apa‑apa secara default karena tidak ada makro yang terlampir, tetapi kontrol visual berfungsi penuh.  

## Langkah 6: Kasus tepi dan jebakan umum  

| Situasi | Hal yang perlu diwaspadai | Perbaikan yang disarankan |
|-----------|-------------------|-----------------|
| **Tombol tumpang teks yang ada** | Persegi panjang dapat berpotongan dengan paragraf, menyebabkan masalah tata letak. | Sisipkan tombol setelah memanggil `builder.Writeln()` untuk memindahkan kursor ke baris baru, atau sesuaikan koordinat `Y`. |
| **Dokumen terbuka dengan peringatan** | Beberapa versi Word menandai kontrol OLE yang tidak memiliki program terhubung. | Pastikan tipe kontrol adalah `CommandButton`; Word memperlakukannya sebagai elemen formulir standar dan tidak memerlukan program eksternal. |
| **Menjalankan di Linux dengan lingkungan tanpa tampilan** | Word tidak dapat diluncurkan untuk menguji UI, tetapi file tetap valid. | Gunakan tes unit yang membaca properti kontrol (`commandButton.Name`, `commandButton.Caption`) untuk memverifikasi bahwa mereka telah diatur dengan benar. |
| **Dibutuhkan beberapa tombol** | Menggunakan kembali `DocumentBuilder` yang sama tanpa memindahkan kursor menambahkan tombol di atas tombol sebelumnya. | Panggil `builder.MoveToDocumentEnd()` atau sesuaikan nilai `Y` persegi panjang sebelum setiap penyisipan. |

Menangani kasus tepi ini lebih awal menghemat waktu saat memperluas solusi ke formulir lengkap dengan puluhan kontrol.  

## Langkah 7: Contoh lengkap yang dapat dijalankan  

Berikut adalah program mandiri yang dapat Anda salin, tempel, dan jalankan tanpa modifikasi (kecuali pemulihan NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Output yang diharapkan**  

Menjalankan program mencetak jalur yang mirip dengan:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Membuka *CommandButtonDemo.docx* yang dihasilkan menampilkan satu tombol **Submit** yang ditempatkan pada koordinat yang didefinisikan dalam kode. Tidak ada elemen UI tambahan yang muncul, mengonfirmasi bahwa alur kerja **menambahkan tombol perintah secara programatis** berhasil.  

## Kesimpulan  

Anda sekarang tahu cara **menambahkan tombol perintah secara programatis** ke dokumen Word menggunakan Aspose.Words, dan Anda juga memahami cara **membuat tombol dokumen Word** yang nantinya dapat dihubungkan ke makro VBA atau alat otomasi eksternal. Prosesnya terdiri dari menginisialisasi dokumen, menyisipkan kontrol OLE `CommandButton`, mengkonfigurasi propertinya, dan menyimpan file.  

Dari sini Anda dapat:  

* Menambahkan lebih banyak kontrol (checkbox, bidang teks) dengan mengulangi langkah 3 menggunakan nilai `ControlType` yang berbeda.  
* Menyambungkan makro VBA ke tombol untuk melakukan tindakan seperti menyimpan formulir atau mengirim email.  
* Menghasilkan seluruh formulir secara dinamis dengan melakukan loop pada koleksi definisi bidang yang didorong oleh data.  

Bereksperimenlah dengan koordinat persegi panjang dan caption tombol untuk menyesuaikan desain UI Anda. Selamat coding!  

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Tambahkan Field Form Combo Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Tambahkan Field Form Check Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Buat dokumen word kosong dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}