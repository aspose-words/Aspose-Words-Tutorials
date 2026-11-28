---
category: general
date: 2026-08-23
description: Terjemahkan string ke bahasa Spanyol dalam C# menggunakan Aspose.Words
  AI Translator dan penyedia Google. Ikuti panduan langkah demi langkah untuk menerjemahkan
  string dalam C# dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: id
lastmod: 2026-08-23
og_description: Terjemahkan string ke bahasa Spanyol dalam C# dengan Aspose.Words
  AI. Tutorial ini menunjukkan cara mengatur penyedia Google, menerjemahkan sebuah
  string, dan menampilkan hasilnya.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: Menerjemahkan string ke bahasa Spanyol dalam C# – contoh kode lengkap
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: Terjemahkan string ke bahasa Spanyol dalam C# dengan Aspose.Words AI
url: /id/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menerjemahkan string ke Bahasa Spanyol di C# dengan Aspose.Words AI

Jika Anda perlu **menerjemahkan string ke Bahasa Spanyol** dalam aplikasi .NET, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat contoh lengkap yang dapat dijalankan yang membuat penerjemah, memanggil layanan Google, dan mencetak teks dalam Bahasa Spanyol.

Tutorial ini juga mencakup **menerjemahkan string di C#** menggunakan pustaka Aspose.Words AI, sehingga Anda dapat mengintegrasikan lokalisasi langsung ke dalam basis kode Anda tanpa skrip eksternal.

## Apa yang Anda perlukan

- .NET 6.0 SDK atau yang lebih baru (kode ini dapat dikompilasi dengan .NET Core dan .NET Framework)
- API key Google Cloud Translation yang aktif
- Paket NuGet `Aspose.Words.AI` (pasang dengan `dotnet add package Aspose.Words.AI`)
- Editor kode atau IDE seperti Visual Studio 2022

Prasyarat ini memastikan contoh dapat dijalankan langsung.

## Menerjemahkan string ke Bahasa Spanyol dengan Aspose.Words AI

Bagian ini membuat objek `Translator` yang dikonfigurasi untuk penyedia Google. Penyedia ini menangani permintaan HTTP ke endpoint terjemahan Google.

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**Mengapa ini berhasil:**  
- `Translator` mengabstraksi panggilan HTTP, menangani otentikasi dengan API key yang Anda berikan.  
- `TranslationProvider.Google` memberi tahu SDK untuk mengarahkan permintaan ke Google Cloud Translation.  
- `Language.Spanish` memilih kode bahasa target (`es`).  
- Metode `Translate` mengembalikan string yang telah diterjemahkan, yang dapat Anda gunakan di mana saja dalam aplikasi Anda.

## Menyiapkan penyedia terjemahan Google

1. **Dapatkan API key** dari Google Cloud Console → APIs & Services → Credentials.  
2. **Aktifkan Cloud Translation API** untuk proyek Anda.  
3. Simpan key dengan aman (variabel lingkungan, secret manager, dll.). Contoh ini menggunakan literal untuk kejelasan, tetapi kode produksi sebaiknya tidak menuliskan rahasia secara langsung.

## Menerjemahkan string di C# – langkah demi langkah

| Langkah | Aksi | Alasan |
|------|--------|--------|
| 1 | Membuat instance `Translator` dengan `TranslationProvider.Google` | Menghubungkan SDK ke layanan Google |
| 2 | Panggil `Translate(source, Language.Spanish)` | Mengirim teks sumber dan menerima hasil dalam Bahasa Spanyol |
| 3 | Tampilkan hasil dengan `Console.WriteLine` | Memverifikasi terjemahan dan menunjukkan cara penggunaan |

Menjalankan program akan mencetak:

```
¡Hola mundo!
```

> **Catatan:** Output yang tepat mungkin sedikit berbeda tergantung pada model terjemahan Google (misalnya, “Hola mundo” vs. “¡Hola mundo!”). Kedua-duanya merupakan padanan Bahasa Spanyol yang valid.

## Jalankan dan verifikasi output

1. Buka terminal di folder proyek.  
2. Jalankan `dotnet run`.  
3. Pastikan konsol menampilkan frasa dalam Bahasa Spanyol.

Jika konsol menampilkan error seperti *“401 Unauthorized”*, periksa kembali bahwa API key sudah benar dan Cloud Translation API telah diaktifkan untuk proyek.

## Kesulitan umum dan praktik terbaik

- **Batas kuota API** – Google memberlakukan batas permintaan per akun penagihan. Pantau penggunaan di Cloud Console untuk menghindari throttling yang tidak terduga.  
- **Latensi jaringan** – Panggilan terjemahan adalah permintaan HTTP remote. Pertimbangkan untuk menyimpan cache string yang sering diterjemahkan guna mengurangi latensi.  
- **Masalah enkoding** – SDK bekerja dengan string UTF‑8; pastikan file sumber Anda disimpan dengan enkoding UTF‑8 untuk mempertahankan karakter khusus.  
- **Penanganan error** – Bungkus panggilan `Translate` dalam blok try‑catch untuk menangani `ApiException` dan menyediakan teks cadangan.

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## Memperluas contoh

- **Terjemahkan ke bahasa lain** – Ganti `Language.Spanish` dengan `Language.French`, `Language.German`, dll.  
- **Terjemahan batch** – Panggil `Translate` di dalam loop untuk memproses daftar string.  
- **Integrasi dengan UI** – Gunakan string yang diterjemahkan di halaman Razor ASP.NET Core, Windows Forms, atau aplikasi WPF.

## Kesimpulan

Anda kini tahu cara **menerjemahkan string ke Bahasa Spanyol** di C# menggunakan Aspose.Words AI dan layanan Google Translation. Solusi lengkap mencakup penyiapan penyedia, pemanggilan terjemahan, penanganan error, dan verifikasi output.

Dari sini, coba bereksperimen dengan bahasa tambahan, cache hasil untuk kinerja, dan integrasikan penerjemah ke dalam pipeline lokalisasi yang lebih besar.

--- 

*Siap untuk melokalisasi lebih banyak konten? Lihat tutorial berikutnya tentang **translate string in C# with Azure Cognitive Services** untuk penyedia cloud alternatif.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Ganti Dengan String](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Ganti Dengan String](/words/english/net/find-and-replace-text/replace-with-string/)
- [Buat Dokumen Word dengan Aspose.Words – Panduan Langkah demi Langkah](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}