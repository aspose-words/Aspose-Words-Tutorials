---
"description": "Pelajari cara mengimplementasikan panggilan balik pemenggalan kata dalam Aspose.Words untuk .NET guna menyempurnakan pemformatan dokumen dengan panduan langkah demi langkah yang komprehensif ini."
"linktitle": "Panggilan Balik Pemenggalan Kata"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Panggilan Balik Pemenggalan Kata"
"url": "/id/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Panggilan Balik Pemenggalan Kata


## Perkenalan

Hai! Pernahkah Anda merasa terjerat dalam kerumitan pemformatan teks, terutama saat berhadapan dengan bahasa yang memerlukan pemenggalan kata? Anda tidak sendirian. Pemenggalan kata, meskipun penting untuk tata letak teks yang tepat, bisa jadi sedikit menyulitkan. Tapi coba tebak? Aspose.Words untuk .NET siap membantu Anda. Pustaka canggih ini memungkinkan Anda mengelola pemformatan teks dengan lancar, termasuk menangani pemenggalan kata melalui mekanisme panggilan balik. Penasaran? Mari selami seluk-beluk cara menerapkan panggilan balik pemenggalan kata menggunakan Aspose.Words untuk .NET.

## Prasyarat

Sebelum kita mulai mengerjakan kode, mari pastikan Anda memiliki semua yang dibutuhkan:

1. Aspose.Words untuk .NET: Pastikan Anda memiliki pustaka. Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
2. IDE: Lingkungan pengembangan seperti Visual Studio.
3. Pengetahuan Dasar C#: Pemahaman tentang C# dan kerangka kerja .NET.
4. Kamus Pemenggalan Kata: Kamus pemenggalan kata untuk bahasa yang ingin Anda gunakan.
5. Lisensi Aspose: Lisensi Aspose yang valid. Anda bisa mendapatkan lisensi ini [lisensi sementara](https://purchase.aspose.com/temporary-license/) jika Anda tidak memilikinya.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini memastikan kode kita memiliki akses ke semua kelas dan metode yang kita perlukan dari Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Langkah 1: Daftarkan Panggilan Balik Hyphenation

Untuk memulai, kita perlu mendaftarkan panggilan balik pemenggalan kata. Di sinilah kita memberi tahu Aspose.Words untuk menggunakan logika pemenggalan kata kustom kita.

```csharp
try
{
    // Daftarkan panggilan balik pemenggalan kata.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

Di sini, kami membuat contoh panggilan balik kustom kami dan menetapkannya ke `Hyphenation.Callback`.

## Langkah 2: Tentukan Jalur Dokumen

Selanjutnya, kita perlu menentukan direktori tempat dokumen kita disimpan. Ini penting karena kita akan memuat dan menyimpan dokumen dari jalur ini.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke dokumen Anda.

## Langkah 3: Muat Dokumen

Sekarang, mari kita muat dokumen yang memerlukan pemenggalan kata.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Di sini, kami memuat dokumen teks Jerman. Anda dapat mengganti `"German text.docx"` dengan nama berkas dokumen Anda.

## Langkah 4: Simpan Dokumen

Setelah memuat dokumen, kami menyimpannya ke berkas baru, menerapkan panggilan balik pemenggalan kata dalam prosesnya.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Baris ini menyimpan dokumen sebagai PDF dengan penerapan tanda hubung.

## Langkah 5: Tangani Pengecualian Kamus Penghubung yang Hilang

Terkadang, Anda mungkin mengalami masalah saat kamus pemenggalan kata tidak ada. Mari kita tangani masalah itu.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

Di blok ini, kami menangkap pengecualian spesifik yang terkait dengan kamus yang hilang dan mencetak pesannya.

## Langkah 6: Terapkan Kelas Panggilan Balik Pemenggalan Kata Kustom

Sekarang, mari kita terapkan `CustomHyphenationCallback` kelas yang menangani permintaan kamus pemenggalan kata.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Daftarkan kamus untuk bahasa yang diminta.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

Di kelas ini, `RequestDictionary` Metode ini dipanggil setiap kali kamus pemenggalan kata dibutuhkan. Metode ini memeriksa bahasa dan mendaftarkan kamus yang sesuai.

## Kesimpulan

Nah, itu dia! Anda baru saja mempelajari cara menerapkan pemanggilan pemenggalan kata dalam Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat memastikan dokumen Anda diformat dengan baik, apa pun bahasanya. Baik Anda menggunakan bahasa Inggris, Jerman, atau bahasa lainnya, metode ini memungkinkan Anda menangani pemenggalan kata dengan mudah.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka manipulasi dokumen canggih yang memungkinkan pengembang untuk membuat, memodifikasi, dan mengonversi dokumen secara terprogram.

### Mengapa pemenggalan kata penting dalam pemformatan dokumen?
Pemenggalan kata memperbaiki tata letak teks dengan memisahkan kata pada tempat yang tepat, sehingga menghasilkan dokumen yang lebih mudah dibaca dan menarik secara visual.

### Bisakah saya menggunakan Aspose.Words secara gratis?
Aspose.Words menawarkan uji coba gratis. Anda bisa mendapatkannya [Di Sini](https://releases.aspose.com/).

### Bagaimana cara mendapatkan kamus pemenggalan kata?
Anda dapat mengunduh kamus pemenggalan kata dari berbagai sumber daring atau membuatnya sendiri jika diperlukan.

### Apa yang terjadi jika kamus pemenggalan kata tidak ada?
Jika kamus tidak ada, `RequestDictionary` metode ini melempar pengecualian, yang dapat Anda tangani untuk memberi tahu pengguna atau menyediakan solusi sementara.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}