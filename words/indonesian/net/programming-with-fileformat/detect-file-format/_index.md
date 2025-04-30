---
"description": "Pelajari cara mendeteksi format file dokumen menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah yang komprehensif ini."
"linktitle": "Deteksi Format File Dokumen"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Deteksi Format File Dokumen"
"url": "/id/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Deteksi Format File Dokumen

## Perkenalan

Di dunia digital saat ini, mengelola berbagai format dokumen secara efisien sangatlah penting. Baik Anda menangani Word, PDF, HTML, atau format lainnya, kemampuan mendeteksi dan memproses file-file ini dengan benar dapat menghemat banyak waktu dan tenaga Anda. Dalam tutorial ini, kita akan membahas cara mendeteksi format file dokumen menggunakan Aspose.Words untuk .NET. Panduan ini akan memandu Anda melalui semua hal yang perlu Anda ketahui, mulai dari prasyarat hingga panduan langkah demi langkah yang terperinci.

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda memiliki semua yang Anda butuhkan:

- Aspose.Words untuk .NET: Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/)Pastikan Anda memiliki lisensi yang valid. Jika tidak, Anda bisa mendapatkan lisensi [lisensi sementara](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Versi terbaru apa pun akan berfungsi dengan baik.
- .NET Framework: Pastikan Anda menginstal versi yang benar.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Mari kita uraikan contoh ini menjadi beberapa langkah agar lebih mudah diikuti.

## Langkah 1: Siapkan Direktori

Pertama, kita perlu menyiapkan direktori tempat file akan diurutkan berdasarkan formatnya.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Buat direktori jika belum ada.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Langkah 2: Dapatkan Daftar File

Berikutnya, kita akan mendapatkan daftar file dari direktori, tidak termasuk dokumen yang rusak.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Langkah 3: Mendeteksi Format File

Sekarang, kita mengulangi setiap berkas dan mendeteksi formatnya menggunakan Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Menampilkan jenis dokumen
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Kesimpulan

Mendeteksi format berkas dokumen menggunakan Aspose.Words untuk .NET merupakan proses yang mudah. Dengan menyiapkan direktori, mendapatkan daftar berkas, dan memanfaatkan Aspose.Words untuk mendeteksi format berkas, Anda dapat mengatur dan mengelola dokumen secara efisien. Pendekatan ini tidak hanya menghemat waktu tetapi juga memastikan bahwa Anda menangani berbagai format dokumen dengan benar.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang hebat untuk bekerja dengan dokumen Word secara terprogram. Pustaka ini memungkinkan pengembang untuk membuat, memodifikasi, dan mengonversi dokumen dalam berbagai format.

### Bisakah Aspose.Words mendeteksi dokumen terenkripsi?
Ya, Aspose.Words dapat mendeteksi jika suatu dokumen dienkripsi dan Anda dapat menangani dokumen tersebut sebagaimana mestinya.

### Format apa yang dapat dideteksi Aspose.Words?
Aspose.Words dapat mendeteksi berbagai format termasuk DOC, DOCX, RTF, HTML, MHTML, ODT, dan masih banyak lagi.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words?
Anda bisa mendapatkan lisensi sementara dari [Aspose Pembelian](https://purchase.aspose.com/temporary-license/) halaman.

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Words?
Dokumentasi untuk Aspose.Words dapat ditemukan [Di Sini](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}