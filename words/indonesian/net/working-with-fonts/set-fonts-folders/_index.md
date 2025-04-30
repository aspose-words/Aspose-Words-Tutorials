---
"description": "Pelajari cara mengatur folder font khusus di Aspose.Words untuk .NET dengan panduan langkah demi langkah yang komprehensif ini. Sempurna bagi pengembang yang ingin menyempurnakan font dokumen."
"linktitle": "Atur Folder Font"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Atur Folder Font"
"url": "/id/net/working-with-fonts/set-fonts-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atur Folder Font

## Perkenalan

Hai! Siap menyelami dunia font kustom di Aspose.Words untuk .NET? Mari kita mulai. Tutorial ini akan memandu Anda melalui proses pengaturan folder font kustom, memastikan dokumen Anda terlihat seperti yang Anda inginkan. Baik Anda pengembang berpengalaman atau baru memulai, panduan ini akan memandu Anda melalui setiap langkah. Jadi, mari kita buat font tersebut tampak luar biasa!

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

- Aspose.Words untuk .NET: Anda dapat [Unduh](https://releases.aspose.com/words/net/) itu jika Anda belum melakukannya.
- Visual Studio: Versi mana pun bisa digunakan, tetapi versi terbaru selalu yang terbaik.
- Dokumen: Kami akan menggunakan dokumen Word untuk tutorial ini. Anda dapat membuat dokumen sendiri atau menggunakan dokumen yang sudah ada.
- Font Kustom: Siapkan beberapa font kustom. Kami akan menggunakan ini untuk menunjukkan cara mengatur folder font.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini penting untuk mengakses kelas dan metode yang kita perlukan dari Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Setelah namespace ini diimpor, kita siap untuk mulai menyiapkan folder font kustom kita.

## Langkah 1: Tentukan Direktori Dokumen Anda

Mari kita mulai dengan menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda disimpan. Kita akan menggunakan variabel yang disebut `dataDir` untuk menyimpan jalur ini.

```csharp
// Jalur ke direktori dokumen Anda 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori Anda. Hal ini penting karena Aspose.Words perlu mengetahui tempat menemukan dokumen Anda.

## Langkah 2: Mengatur Sumber Font

Selanjutnya, kita perlu mengatur sumber font. Di sinilah kita memberi tahu Aspose.Words di mana menemukan font kustom kita. Kita akan menggunakan `FontSettings.DefaultInstance.SetFontsSources` metode untuk mencapai hal ini.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Inilah yang sedang kami lakukan:

- SystemFontSource: Ini memberitahu Aspose.Words untuk menggunakan font default sistem.
- FolderFontSource: Di sinilah kita menentukan folder yang berisi font kustom kita. Ganti `"C:\\MyFonts\\"` dengan jalur ke direktori font kustom Anda. `true` parameter menunjukkan bahwa subdirektori juga harus disertakan.

## Langkah 3: Muat Dokumen Anda

Sekarang setelah kita menyiapkan sumber font kita, saatnya memuat dokumen yang ingin kita gunakan. Kita akan menggunakan `Document` kelas dari Aspose.Words untuk ini.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Pastikan bahwa `"Rendering.docx"` adalah nama dokumen Word Anda. Jika dokumen Anda memiliki nama yang berbeda, pastikan untuk memperbaruinya.

## Langkah 4: Simpan Dokumen Anda sebagai PDF

Terakhir, mari simpan dokumen kita sebagai PDF untuk melihat font kustom yang sedang digunakan. Kita akan menggunakan `Save` metode dari `Document` kelas.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Ini akan menyimpan dokumen Anda sebagai PDF di direktori yang ditentukan, menggunakan font khusus yang telah kita siapkan sebelumnya.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menyiapkan folder font khusus di Aspose.Words untuk .NET dan menyimpan dokumen Anda sebagai PDF dengan font khusus tersebut. Keren, bukan? Menyesuaikan font dapat membuat perbedaan besar dalam tampilan dokumen Anda, dan sekarang Anda tahu persis cara melakukannya. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menginstal Aspose.Words untuk .NET?

Kamu bisa [Unduh](https://releases.aspose.com/words/net/) versi terbaru Aspose.Words untuk .NET dari situs web.

### Bisakah saya menggunakan beberapa folder font khusus?

Ya, Anda dapat menambahkan beberapa `FolderFontSource` contoh kasus ke `SetFontsSources` metode untuk menggunakan font dari direktori yang berbeda.

### Apakah perlu menyertakan font sistem?

Menyertakan font sistem adalah opsional tetapi disarankan untuk memastikan semua font standar tersedia.

### Jenis berkas apa yang didukung oleh Aspose.Words?

Aspose.Words mendukung berbagai format file, termasuk DOCX, DOC, PDF, TXT, HTML, dan masih banyak lagi.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words?

Anda bisa mendapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) dari situs web Aspose untuk mencoba fitur lengkap Aspose.Words.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}