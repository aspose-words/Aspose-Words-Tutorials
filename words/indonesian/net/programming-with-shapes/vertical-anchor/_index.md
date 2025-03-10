---
title: Jangkar Vertikal
linktitle: Jangkar Vertikal
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengatur posisi jangkar vertikal untuk kotak teks dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah yang mudah disertakan.
weight: 10
url: /id/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jangkar Vertikal

## Perkenalan

Pernahkah Anda merasa perlu mengontrol di mana tepatnya teks muncul di dalam kotak teks dalam dokumen Word? Mungkin Anda ingin teks Anda ditambatkan ke bagian atas, tengah, atau bawah kotak teks? Jika demikian, Anda berada di tempat yang tepat! Dalam tutorial ini, kita akan menjelajahi cara menggunakan Aspose.Words untuk .NET guna mengatur jangkar vertikal kotak teks dalam dokumen Word. Anggap penjangkaran vertikal sebagai tongkat ajaib yang memposisikan teks Anda tepat di tempat yang Anda inginkan dalam wadahnya. Siap untuk mencobanya? Mari kita mulai!

## Prasyarat

Sebelum kita menyelami lebih dalam tentang dasar-dasar penjangkaran vertikal, Anda perlu menyiapkan beberapa hal:

1.  Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Jika Anda belum memilikinya, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Visual Studio: Tutorial ini mengasumsikan Anda menggunakan Visual Studio atau IDE .NET lain untuk pengkodean.
3. Pengetahuan Dasar C#: Keakraban dengan C# dan .NET akan membantu Anda mengikutinya dengan lancar.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dalam kode C# Anda. Di sinilah Anda memberi tahu aplikasi Anda di mana menemukan kelas dan metode yang akan Anda gunakan. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ruang nama ini menyediakan kelas yang Anda perlukan untuk bekerja dengan dokumen dan bentuk.

## Langkah 1: Inisialisasi Dokumen

Pertama-tama, Anda perlu membuat dokumen Word baru. Anggap saja ini seperti menyiapkan kanvas sebelum mulai melukis.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Di Sini,`Document` adalah kanvas kosongmu, dan`DocumentBuilder` adalah kuas Anda, yang memungkinkan Anda menambahkan bentuk dan teks.

## Langkah 2: Masukkan Bentuk Kotak Teks

Sekarang, mari tambahkan kotak teks ke dokumen kita. Di sinilah teks Anda akan berada. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 Dalam contoh ini,`ShapeType.TextBox` menentukan bentuk yang Anda inginkan, dan`200, 200` adalah lebar dan tinggi kotak teks dalam poin.

## Langkah 3: Mengatur Jangkar Vertikal

Di sinilah keajaiban terjadi! Anda dapat mengatur perataan vertikal teks di dalam kotak teks. Ini menentukan apakah teks akan ditambatkan ke bagian atas, tengah, atau bawah kotak teks.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 Dalam kasus ini,`TextBoxAnchor.Bottom`memastikan bahwa teks akan ditambatkan ke bagian bawah kotak teks. Jika Anda ingin teks dipusatkan atau disejajarkan ke bagian atas, Anda akan menggunakan`TextBoxAnchor.Center` atau`TextBoxAnchor.Top`, masing-masing.

## Langkah 4: Tambahkan Teks ke Kotak Teks

Sekarang saatnya menambahkan beberapa konten ke kotak teks Anda. Anggap saja seperti mengisi kanvas Anda dengan sentuhan akhir.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Di Sini,`MoveTo` memastikan bahwa teks dimasukkan ke dalam kotak teks, dan`Write` menambahkan teks sebenarnya.

## Langkah 5: Simpan Dokumen

Langkah terakhir adalah menyimpan dokumen Anda. Ini seperti meletakkan lukisan yang sudah selesai ke dalam bingkai.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Kesimpulan

Nah, itu dia! Anda baru saja mempelajari cara mengontrol perataan vertikal teks dalam kotak teks di dokumen Word menggunakan Aspose.Words untuk .NET. Baik Anda meletakkan teks di bagian atas, tengah, atau bawah, fitur ini memberi Anda kontrol yang tepat atas tata letak dokumen Anda. Jadi, lain kali Anda perlu mengubah penempatan teks dokumen Anda, Anda akan tahu persis apa yang harus dilakukan!

## Pertanyaan yang Sering Diajukan

### Apa itu penahan vertikal dalam dokumen Word?
Kontrol penahan vertikal menentukan posisi teks dalam kotak teks, seperti perataan atas, tengah, atau bawah.

### Bisakah saya menggunakan bentuk lain selain kotak teks?
Ya, Anda dapat menggunakan penahan vertikal dengan bentuk lain, meskipun kotak teks merupakan kasus penggunaan yang paling umum.

### Bagaimana cara mengubah titik jangkar setelah membuat kotak teks?
 Anda dapat mengubah titik jangkar dengan mengatur`VerticalAnchor` properti pada objek bentuk kotak teks.

### Mungkinkah untuk menjangkarkan teks di tengah kotak teks?
 Tentu saja! Gunakan saja`TextBoxAnchor.Center` untuk memusatkan teks secara vertikal dalam kotak teks.

### Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Words untuk .NET?
 Lihat di sini[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) untuk rincian dan panduan lebih lanjut.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
