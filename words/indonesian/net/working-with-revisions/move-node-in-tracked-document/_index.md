---
title: Pindahkan Node Dalam Dokumen yang Dilacak
linktitle: Pindahkan Node Dalam Dokumen yang Dilacak
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara memindahkan node dalam dokumen Word yang dilacak menggunakan Aspose.Words untuk .NET dengan panduan terperinci dan langkah demi langkah. Sempurna untuk pengembang.
weight: 10
url: /id/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pindahkan Node Dalam Dokumen yang Dilacak

## Perkenalan

Hai, penggemar Aspose.Words! Jika Anda pernah perlu memindahkan node dalam dokumen Word saat melacak revisi, Anda berada di tempat yang tepat. Hari ini, kita akan membahas cara melakukannya menggunakan Aspose.Words untuk .NET. Anda tidak hanya akan mempelajari proses langkah demi langkah, tetapi Anda juga akan memperoleh beberapa kiat dan trik untuk membuat manipulasi dokumen Anda lancar dan efisien.

## Prasyarat

Sebelum kita mulai mengerjakan beberapa kode, mari pastikan Anda memiliki semua yang dibutuhkan:

-  Aspose.Words untuk .NET: Unduh[Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan .NET: Pastikan Anda telah menyiapkan lingkungan pengembangan .NET yang kompatibel.
- Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang C#.

Sudah mendapatkan semuanya? Bagus! Mari kita lanjutkan ke namespace yang perlu kita impor.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan. Namespace ini penting untuk bekerja dengan Aspose.Words dan menangani node dokumen.

```csharp
using Aspose.Words;
using System;
```

Baiklah, mari kita bagi prosesnya menjadi beberapa langkah yang mudah dikelola. Setiap langkah akan dijelaskan secara terperinci untuk memastikan Anda memahami apa yang terjadi di setiap tahap.

## Langkah 1: Inisialisasi Dokumen

 Untuk memulai, kita perlu menginisialisasi dokumen baru dan menggunakan`DocumentBuilder` untuk menambahkan beberapa paragraf.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Menambahkan beberapa paragraf
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Periksa jumlah paragraf awal
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Langkah 2: Mulai Melacak Revisi

Selanjutnya, kita perlu mulai melacak revisi. Hal ini penting karena memungkinkan kita melihat perubahan yang dibuat pada dokumen.

```csharp
// Mulai melacak revisi
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Langkah 3: Pindahkan Node

Sekarang tibalah bagian inti dari tugas kita: memindahkan simpul dari satu lokasi ke lokasi lain. Kita akan memindahkan paragraf ketiga dan meletakkannya sebelum paragraf pertama.

```csharp
// Tentukan node yang akan dipindahkan dan rentang akhirnya
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Pindahkan node dalam rentang yang ditentukan
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Langkah 4: Hentikan Pelacakan Revisi

Setelah kita memindahkan node, kita perlu berhenti melacak revisi.

```csharp
// Berhenti melacak revisi
doc.StopTrackRevisions();
```

## Langkah 5: Simpan Dokumen

Terakhir, mari simpan dokumen yang telah dimodifikasi ke direktori yang ditentukan.

```csharp
// Simpan dokumen yang dimodifikasi
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Keluarkan jumlah paragraf akhir
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil memindahkan node dalam dokumen yang dilacak menggunakan Aspose.Words untuk .NET. Pustaka canggih ini memudahkan Anda memanipulasi dokumen Word secara terprogram. Baik Anda membuat, mengedit, atau melacak perubahan, Aspose.Words siap membantu Anda. Jadi, silakan dan cobalah. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?

Aspose.Words untuk .NET adalah pustaka kelas untuk bekerja dengan dokumen Word secara terprogram. Pustaka ini memungkinkan pengembang untuk membuat, mengedit, mengonversi, dan mencetak dokumen Word dalam aplikasi .NET.

### Bagaimana cara melacak revisi dalam dokumen Word menggunakan Aspose.Words?

 Untuk melacak revisi, gunakan`StartTrackRevisions` metode pada`Document` objek. Ini akan mengaktifkan pelacakan revisi, yang menunjukkan perubahan apa pun yang dibuat pada dokumen.

### Bisakah saya memindahkan beberapa node di Aspose.Words?

Ya, Anda dapat memindahkan beberapa node dengan mengulanginya dan menggunakan metode seperti`InsertBefore` atau`InsertAfter` untuk menempatkannya di lokasi yang diinginkan.

### Bagaimana cara menghentikan pelacakan revisi di Aspose.Words?

 Gunakan`StopTrackRevisions` metode pada`Document` keberatan untuk menghentikan pelacakan revisi.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?

 Anda dapat menemukan dokumentasi terperinci[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
