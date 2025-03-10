---
title: Ubah Kontrol Konten
linktitle: Ubah Kontrol Konten
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengubah tag dokumen terstruktur di Word menggunakan Aspose.Words untuk .NET. Perbarui teks, dropdown, dan gambar selangkah demi selangkah.
weight: 10
url: /id/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ubah Kontrol Konten

## Perkenalan

Jika Anda pernah bekerja dengan dokumen Word dan perlu mengubah kontrol konten terstruktur—seperti teks biasa, daftar dropdown, atau gambar—menggunakan Aspose.Words untuk .NET, Anda berada di tempat yang tepat! Tag Dokumen Terstruktur (SDT) adalah alat canggih yang membuat otomatisasi dokumen lebih mudah dan lebih fleksibel. Dalam tutorial ini, kita akan membahas cara mengubah SDT ini agar sesuai dengan kebutuhan Anda. Baik Anda memperbarui teks, mengubah pilihan dropdown, atau menukar gambar, panduan ini akan memandu Anda melalui proses tersebut langkah demi langkah.

## Prasyarat

Sebelum kita masuk ke inti modifikasi kontrol konten, pastikan Anda memiliki hal berikut:

1.  Aspose.Words untuk .NET Terpasang: Pastikan Anda telah memasang pustaka Aspose.Words. Jika belum, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).

2. Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda familier dengan konsep dasar pemrograman C#.

3. Lingkungan Pengembangan .NET: Anda harus menyiapkan IDE seperti Visual Studio untuk menjalankan aplikasi .NET.

4. Contoh Dokumen: Kami akan menggunakan contoh dokumen Word dengan berbagai jenis SDT. Anda dapat menggunakan salah satu dari contoh tersebut atau membuatnya sendiri.

5.  Akses ke Dokumentasi Aspose: Untuk informasi lebih rinci, lihat[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/).

## Mengimpor Ruang Nama

Untuk mulai bekerja dengan Aspose.Words, Anda perlu mengimpor namespace yang relevan ke dalam proyek C# Anda. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Ruang nama ini akan memberi Anda akses ke kelas dan metode yang diperlukan untuk memanipulasi tag dokumen terstruktur dalam dokumen Word Anda.

## Langkah 1: Siapkan Jalur Dokumen Anda

 Sebelum melakukan perubahan apa pun, Anda perlu menentukan jalur ke dokumen Anda. Ganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat dokumen Anda disimpan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Langkah 2: Ulangi Melalui Tag Dokumen Terstruktur

 Untuk mengubah SDT, Anda perlu melakukan pengulangan pada semua SDT dalam dokumen. Hal ini dilakukan dengan menggunakan`GetChildNodes` metode untuk mendapatkan semua node bertipe`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Ubah SDT berdasarkan jenisnya
}
```

## Langkah 3: Ubah SDT Teks Biasa

Jika SDT adalah tipe teks biasa, Anda dapat mengganti isinya. Pertama, hapus konten yang ada, lalu tambahkan teks baru.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Penjelasan: Di sini,`RemoveAllChildren()`membersihkan konten SDT yang ada. Kemudian kita membuat yang baru`Paragraph` Dan`Run` objek untuk menyisipkan teks baru.

## Langkah 4: Ubah SDT Daftar Dropdown

 Untuk SDT daftar dropdown, Anda dapat mengubah item yang dipilih dengan mengakses`ListItems` koleksi. Di sini, kita pilih item ketiga dalam daftar.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Penjelasan: Potongan kode ini memilih item pada indeks 2 (item ketiga) dari daftar dropdown. Sesuaikan indeks berdasarkan kebutuhan Anda.

## Langkah 5: Ubah SDT Gambar

Untuk memperbarui gambar dalam SDT gambar, Anda dapat mengganti gambar yang ada dengan yang baru.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Penjelasan: Kode ini memeriksa apakah bentuk tersebut berisi gambar dan kemudian menggantinya dengan gambar baru yang terletak di`ImagesDir`.

## Langkah 6: Simpan Dokumen Anda yang Telah Dimodifikasi

Setelah membuat semua perubahan yang diperlukan, simpan dokumen yang dimodifikasi dengan nama baru untuk menjaga dokumen asli Anda tetap utuh.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Penjelasan: Ini menyimpan dokumen dengan nama file baru sehingga Anda dapat dengan mudah membedakannya dari aslinya.

## Kesimpulan

Memodifikasi kontrol konten dalam dokumen Word menggunakan Aspose.Words untuk .NET mudah dilakukan setelah Anda memahami langkah-langkah yang terlibat. Baik Anda memperbarui teks, mengubah pilihan dropdown, atau menukar gambar, Aspose.Words menyediakan API yang tangguh untuk tugas-tugas ini. Dengan mengikuti tutorial ini, Anda dapat mengelola dan menyesuaikan kontrol konten terstruktur dokumen Anda secara efektif, membuat dokumen Anda lebih dinamis dan disesuaikan dengan kebutuhan Anda.

## Tanya Jawab Umum

1. Apa itu Structured Document Tag (SDT)?

SDT adalah elemen dalam dokumen Word yang membantu mengelola dan memformat konten dokumen, seperti kotak teks, daftar dropdown, atau gambar.

2. Bagaimana cara menambahkan item dropdown baru ke SDT?

 Untuk menambahkan item baru, gunakan`ListItems` properti dan menambahkan yang baru`SdtListItem` ke koleksi.

3. Dapatkah saya menggunakan Aspose.Words untuk menghapus SDT dari suatu dokumen?

Ya, Anda dapat menghapus SDT dengan mengakses node dokumen dan menghapus SDT yang diinginkan.

4. Bagaimana cara menangani SDT yang bersarang dalam elemen lain?

 Gunakan`GetChildNodes` metode dengan parameter yang sesuai untuk mengakses SDT bersarang.

5. Apa yang harus saya lakukan jika SDT yang perlu saya ubah tidak terlihat dalam dokumen?

Pastikan SDT tidak disembunyikan atau dilindungi. Periksa pengaturan dokumen dan pastikan kode Anda menargetkan jenis SDT dengan benar.


### Contoh kode sumber untuk Modifikasi Kontrol Konten menggunakan Aspose.Words untuk .NET 

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Selesai! Anda telah berhasil mengubah berbagai jenis kontrol konten dalam dokumen Word Anda menggunakan Aspose.Words for .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
