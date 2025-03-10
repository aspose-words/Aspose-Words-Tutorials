---
title: Dapatkan Substitusi Tanpa Sufiks
linktitle: Dapatkan Substitusi Tanpa Sufiks
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengelola substitusi font tanpa sufiks di Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk memastikan dokumen Anda terlihat sempurna setiap saat.
weight: 10
url: /id/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dapatkan Substitusi Tanpa Sufiks

## Perkenalan

Selamat datang di panduan lengkap tentang pengelolaan substitusi font menggunakan Aspose.Words untuk .NET. Jika Anda pernah mengalami kesulitan dengan font yang tidak muncul dengan benar di dokumen Anda, Anda telah datang ke tempat yang tepat. Tutorial ini akan memandu Anda melalui proses langkah demi langkah untuk menangani substitusi font tanpa sufiks secara efisien.

## Prasyarat

Sebelum memulai tutorial, pastikan Anda memiliki hal berikut:

- Pengetahuan Dasar C#: Memahami pemrograman C# akan memudahkan untuk mengikuti dan menerapkan langkah-langkahnya.
-  Pustaka Aspose.Words untuk .NET: Unduh dan instal pustaka dari[tautan unduhan](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Siapkan lingkungan pengembangan seperti Visual Studio untuk menulis dan menjalankan kode Anda.
-  Contoh Dokumen: Contoh dokumen (misalnya,`Rendering.docx`) untuk digunakan selama tutorial ini.

## Mengimpor Ruang Nama

Pertama, kita perlu mengimpor namespace yang diperlukan untuk mengakses kelas dan metode yang disediakan oleh Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Langkah 1: Tentukan Direktori Dokumen

Untuk memulai, tentukan direktori tempat dokumen Anda berada. Ini membantu dalam menemukan dokumen yang ingin Anda kerjakan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Siapkan Penanganan Peringatan Substitusi

Selanjutnya, kita perlu menyiapkan penangan peringatan yang akan memberi tahu kita setiap kali terjadi penggantian font selama pemrosesan dokumen. Ini penting untuk mendeteksi dan menangani masalah font apa pun.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Langkah 3: Tambahkan Sumber Font Kustom

Pada langkah ini, kita akan menambahkan sumber fon khusus untuk memastikan bahwa Aspose.Words dapat menemukan dan menggunakan fon yang benar. Hal ini sangat berguna jika Anda memiliki fon tertentu yang disimpan dalam direktori khusus.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

Dalam kode ini:
-  Kami mengambil sumber font saat ini dan menambahkan yang baru`FolderFontSource` menunjuk ke direktori font kustom kami (`C:\\MyFonts\\`).
- Kami kemudian memperbarui sumber font dengan daftar baru ini.

## Langkah 4: Simpan Dokumen

Terakhir, simpan dokumen setelah menerapkan pengaturan substitusi font. Untuk tutorial ini, kami akan menyimpannya sebagai PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Langkah 5: Buat Kelas Penanganan Peringatan

 Untuk menangani peringatan secara efektif, buat kelas khusus yang mengimplementasikan`IWarningCallback` antarmuka. Kelas ini akan menangkap dan mencatat peringatan penggantian font apa pun.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

Di kelas ini:
-  Itu`Warning`metode menangkap peringatan yang terkait dengan penggantian font.
-  Itu`FontWarnings` koleksi menyimpan peringatan ini untuk pemeriksaan atau pencatatan lebih lanjut.

## Kesimpulan

Anda kini telah menguasai proses penanganan penggantian font tanpa sufiks menggunakan Aspose.Words untuk .NET. Pengetahuan ini akan memastikan bahwa dokumen Anda mempertahankan tampilan yang diinginkan, apa pun font yang tersedia di sistem. Teruslah bereksperimen dengan berbagai pengaturan dan sumber untuk memanfaatkan sepenuhnya kekuatan Aspose.Words.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menggunakan font dari beberapa direktori kustom?

 Anda dapat menambahkan beberapa`FolderFontSource` contoh kasus ke`fontSources` daftar dan perbarui sumber font sebagaimana mestinya.

### Di mana saya dapat mengunduh uji coba gratis Aspose.Words untuk .NET?

 Anda dapat mengunduh uji coba gratis dari[Halaman uji coba gratis Aspose](https://releases.aspose.com/).

###  Bisakah saya menangani beberapa jenis peringatan menggunakan`IWarningCallback`?

 Ya, itu`IWarningCallback` Antarmuka memungkinkan Anda menangani berbagai jenis peringatan, bukan hanya penggantian font.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Words?

 Untuk dukungan, kunjungi[Forum dukungan Aspose.Words](https://forum.aspose.com/c/words/8).

### Apakah mungkin untuk membeli lisensi sementara?

 Ya, Anda bisa mendapatkan lisensi sementara dari[halaman lisensi sementara](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
