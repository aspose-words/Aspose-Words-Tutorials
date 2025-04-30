---
"description": "Pelajari cara memasukkan kolom TOA tanpa menggunakan pembuat dokumen di Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk mengelola kutipan hukum secara efisien."
"linktitle": "Masukkan Bidang TOA Tanpa Pembuat Dokumen"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Masukkan Bidang TOA Tanpa Pembuat Dokumen"
"url": "/id/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Bidang TOA Tanpa Pembuat Dokumen

## Perkenalan

Membuat kolom Table of Authorities (TOA) dalam dokumen Word mungkin terasa seperti menyusun potongan puzzle yang rumit. Namun, dengan bantuan Aspose.Words for .NET, prosesnya menjadi lancar dan mudah. Dalam artikel ini, kami akan memandu Anda melalui langkah-langkah untuk menyisipkan kolom TOA tanpa menggunakan pembuat dokumen, sehingga memudahkan Anda mengelola kutipan dan referensi hukum dalam dokumen Word Anda.

## Prasyarat

Sebelum menyelami tutorialnya, mari kita bahas hal-hal penting yang Anda perlukan:

- Aspose.Words untuk .NET: Pastikan Anda telah menginstal versi terbaru. Anda dapat mengunduhnya dari [Situs web Aspose](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: IDE yang kompatibel dengan .NET seperti Visual Studio.
- Pengetahuan Dasar C#: Memahami sintaksis dan konsep dasar C# akan sangat membantu.
- Contoh Dokumen Word: Buat atau siapkan dokumen contoh tempat Anda ingin menyisipkan bidang TOA.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dari pustaka Aspose.Words. Pengaturan ini memastikan bahwa Anda memiliki akses ke semua kelas dan metode yang diperlukan untuk manipulasi dokumen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Mari kita uraikan prosesnya menjadi beberapa langkah sederhana yang mudah diikuti. Kami akan memandu Anda melalui setiap tahap, menjelaskan apa yang dilakukan setiap bagian kode dan bagaimana kode tersebut berkontribusi dalam pembuatan bidang TOA.

## Langkah 1: Inisialisasi Dokumen

Pertama, Anda perlu membuat instance dari `Document` kelas. Objek ini mewakili dokumen Word yang sedang Anda kerjakan.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Kode ini menginisialisasi dokumen Word baru. Anda dapat menganggapnya sebagai pembuatan kanvas kosong tempat Anda akan menambahkan konten.

## Langkah 2: Buat dan Konfigurasikan Bidang TA

Selanjutnya, kita akan menambahkan kolom TA (Table of Authorities). Kolom ini menandai entri yang akan muncul di TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Kami ingin memasukkan bidang TA dan TOA seperti ini:
// { TA \c 1 \l "Nilai 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Berikut rinciannya:
- Paragraph para = new Paragraph(doc);: Membuat paragraf baru dalam dokumen.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Menambahkan bidang TA ke paragraf. Itu `FieldType.FieldTOAEntry` menentukan bahwa ini adalah bidang entri TOA.
- fieldTA.EntryCategory = "1";: Mengatur kategori entri. Ini berguna untuk mengkategorikan berbagai jenis entri.
- fieldTA.LongCitation = "Nilai 0";: Menentukan teks kutipan yang panjang. Ini adalah teks yang akan muncul di TOA.
- doc.FirstSection.Body.AppendChild(para);: Menambahkan paragraf dengan bidang TA ke badan dokumen.

## Langkah 3: Tambahkan Bidang TOA

Sekarang, kita akan memasukkan bidang TOA aktual yang mengkompilasi semua entri TA ke dalam sebuah tabel.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Pada langkah ini:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Menambahkan bidang TOA ke paragraf.
- fieldToa.EntryCategory = "1";: Memfilter entri agar hanya menyertakan entri yang ditandai dengan kategori "1".

## Langkah 4: Perbarui Bidang TOA

Setelah memasukkan kolom TOA, Anda perlu memperbaruinya untuk memastikan kolom tersebut mencerminkan entri terkini.

```csharp
fieldToa.Update();
```

Perintah ini menyegarkan bidang TOA, memastikan bahwa semua entri yang ditandai ditampilkan dengan benar dalam tabel.

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen Anda dengan bidang TOA yang baru ditambahkan.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Baris kode ini menyimpan dokumen ke direktori yang ditentukan. Pastikan untuk mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya di mana Anda ingin menyimpan berkas Anda.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menambahkan kolom TOA ke dokumen Word tanpa menggunakan pembuat dokumen. Dengan mengikuti langkah-langkah ini, Anda dapat mengelola kutipan secara efisien dan membuat tabel otoritas yang komprehensif dalam dokumen hukum Anda. Aspose.Words untuk .NET membuat proses ini lancar dan efisien, memberi Anda alat untuk menangani tugas-tugas dokumen yang rumit dengan mudah.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menambahkan beberapa bidang TA dengan kategori yang berbeda?
Ya, Anda dapat menambahkan beberapa bidang TA dengan kategori berbeda dengan mengatur `EntryCategory` properti sebagaimana mestinya.

### Bagaimana saya dapat menyesuaikan tampilan TOA?
Anda dapat menyesuaikan tampilan TOA dengan memodifikasi properti bidang TOA, seperti format entri dan label kategori.

### Apakah mungkin untuk memperbarui bidang TOA secara otomatis?
Meskipun Anda dapat memperbarui bidang TOA secara manual menggunakan `Update` metode Aspose.Words saat ini tidak mendukung pembaruan otomatis pada perubahan dokumen.

### Dapatkah saya menambahkan bidang TA secara terprogram di bagian tertentu dalam dokumen?
Ya, Anda dapat menambahkan kolom TA di lokasi tertentu dengan memasukkannya ke dalam paragraf atau bagian yang diinginkan.

### Bagaimana cara menangani beberapa bidang TOA dalam satu dokumen?
Anda dapat mengelola beberapa bidang TOA dengan menetapkan yang berbeda `EntryCategory` nilai dan memastikan setiap bidang TOA memfilter entri berdasarkan kategorinya.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}