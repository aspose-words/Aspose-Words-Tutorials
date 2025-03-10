---
title: Mengubah Pemberhentian Tab Daftar Isi di Dokumen Word
linktitle: Mengubah Pemberhentian Tab Daftar Isi di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengubah tab stop TOC dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini akan membantu Anda membuat Daftar Isi yang tampak profesional.
weight: 10
url: /id/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengubah Pemberhentian Tab Daftar Isi di Dokumen Word

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana cara mempercantik Daftar Isi (TOC) di dokumen Word Anda? Mungkin Anda ingin tab stop tersebut sejajar sempurna untuk sentuhan profesional. Anda berada di tempat yang tepat! Hari ini, kita akan membahas secara mendalam cara mengubah tab stop TOC menggunakan Aspose.Words untuk .NET. Tetaplah di sini, dan saya jamin Anda akan pulang dengan semua pengetahuan untuk membuat TOC Anda terlihat menarik dan rapi.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE apa pun yang kompatibel dengan C#.
3. Dokumen Word: Khususnya, yang berisi Daftar Isi.

Sudah paham? Keren! Ayo mulai.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan. Ini seperti mengemas peralatan Anda sebelum memulai sebuah proyek.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Mari kita uraikan proses ini menjadi beberapa langkah yang sederhana dan mudah dipahami. Kita akan mulai dari memuat dokumen, mengubah tab TOC, dan menyimpan dokumen yang telah diperbarui.

## Langkah 1: Muat Dokumen

Mengapa? Kita perlu mengakses dokumen Word yang berisi TOC yang ingin kita ubah.

Bagaimana? Berikut cuplikan kode sederhana untuk membantu Anda memulai:

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Memuat dokumen yang berisi daftar isi
Document doc = new Document(dataDir + "Table of contents.docx");
```

Bayangkan dokumen Anda seperti kue, dan kita akan menambahkan sedikit hiasan. Langkah pertama adalah mengeluarkan kue itu dari kotaknya.

## Langkah 2: Identifikasi Paragraf Daftar Isi

Mengapa? Kita perlu menentukan paragraf yang membentuk TOC. 

Bagaimana? Ulangi paragraf-paragraf tersebut dan periksa gayanya:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Paragraf TOC ditemukan
    }
}
```

Bayangkan seperti memindai kerumunan untuk menemukan teman-teman Anda. Di sini, kita mencari paragraf yang diberi gaya entri TOC.

## Langkah 3: Ubah Tab Stop

Mengapa? Di sinilah keajaiban terjadi. Mengubah tab stop membuat TOC Anda tampak lebih bersih.

Bagaimana? Hapus tab stop yang ada dan tambahkan yang baru pada posisi yang dimodifikasi:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Ini seperti menata ulang furnitur di ruang tamu hingga terasa pas. Kami menyesuaikan tab stop tersebut agar sempurna.

## Langkah 4: Simpan Dokumen yang Dimodifikasi

Mengapa? Untuk memastikan semua kerja keras Anda tersimpan dan dapat dilihat atau dibagikan.

Bagaimana? Simpan dokumen dengan nama baru agar dokumen asli tetap utuh:

```csharp
// Simpan dokumen yang dimodifikasi
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

Dan voila! Daftar Isi Anda sekarang memiliki tab stop persis di tempat yang Anda inginkan.

## Kesimpulan

Mengubah tab stop TOC dalam dokumen Word menggunakan Aspose.Words untuk .NET mudah dilakukan setelah Anda menguraikannya. Dengan memuat dokumen, mengidentifikasi paragraf TOC, mengubah tab stop, dan menyimpan dokumen, Anda dapat memperoleh tampilan yang rapi dan profesional. Ingat, latihan akan menghasilkan kesempurnaan, jadi teruslah bereksperimen dengan posisi tab stop yang berbeda untuk memperoleh tata letak yang Anda inginkan.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya mengubah penghentian tab untuk tingkat TOC yang berbeda secara terpisah?
Ya, Anda bisa! Cukup periksa setiap level TOC tertentu (Toc1, Toc2, dst.) dan sesuaikan dengan tepat.

### Bagaimana jika dokumen saya memiliki beberapa TOC?
Kode ini memindai semua paragraf bergaya TOC, sehingga akan mengubah semua TOC yang ada dalam dokumen.

### Apakah mungkin untuk menambahkan beberapa tab stop pada entri TOC?
 Tentu saja! Anda dapat menambahkan tab stop sebanyak yang diperlukan dengan menyesuaikan`para.ParagraphFormat.TabStops` koleksi.

### Bisakah saya mengubah penyelarasan pemberhentian tab dan gaya penunjuk?
Ya, Anda dapat menentukan perataan dan gaya pemimpin yang berbeda saat menambahkan perhentian tab baru.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?
 Ya, Anda memerlukan lisensi yang valid untuk menggunakan Aspose.Words untuk .NET setelah masa uji coba. Anda bisa mendapatkannya[lisensi sementara](https://purchase.aspose.com/temporary-license/) atau[beli satu](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
