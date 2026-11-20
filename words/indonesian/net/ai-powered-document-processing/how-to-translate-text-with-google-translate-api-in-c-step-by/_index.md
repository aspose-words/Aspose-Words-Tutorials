---
category: general
date: 2026-11-15
description: Pelajari cara menerjemahkan teks dengan Google di C#. Tutorial ini menampilkan
  contoh Google Translate, penanganan banyak bahasa, dan praktik terbaik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: id
lastmod: 2026-11-15
og_description: Cara menerjemahkan teks dengan Google di C# menggunakan contoh lengkap
  Google Translate. Ikuti tutorial ini untuk menerjemahkan banyak bahasa dengan aman.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Cara menerjemahkan teks dengan Google Translate API di C# – tutorial singkat
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Cara menerjemahkan teks dengan Google Translate API di C# – panduan langkah
  demi langkah
url: /id/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menerjemahkan teks dengan Google Translate API di C# – panduan langkah demi langkah

Jika Anda perlu **how to translate text** dalam aplikasi .NET, Google Cloud Translation API menawarkan solusi yang handal dan tidak bergantung pada bahasa. Dalam tutorial ini Anda akan melihat **Google Translate example** yang menerjemahkan string sederhana, memperluas menjadi **translate multiple languages**, dan mengikuti praktik terbaik untuk kunci API serta penanganan error.

Anda akan mendapatkan program konsol C# yang siap dijalankan, pemahaman yang jelas tentang **translate text with Google**, dan kepercayaan untuk menyesuaikan kode bagi proyek yang lebih besar.

## Apa yang dibahas dalam tutorial ini

* Menyiapkan proyek Google Cloud dan mendapatkan kunci API.  
* Menginstal paket NuGet `Google.Cloud.Translation.V2`.  
* Menulis kode yang bersih dan dapat digunakan kembali yang **how to translate text** menggunakan SDK resmi.  
* Memperluas solusi untuk **translate multiple languages** dalam satu panggilan.  
* Kesulitan umum dan tips untuk implementasi tingkat produksi.  

### Prasyarat

* .NET 6.0 SDK atau yang lebih baru (kode dapat dikompilasi dengan .NET Core dan .NET Framework).  
* Akun Google Cloud dengan **Cloud Translation API** diaktifkan.  
* Familiaritas dasar dengan C# dan aplikasi konsol.  

---

## Langkah 1: Instal pustaka klien Google Cloud Translation

Pustaka klien resmi mengabstraksi panggilan HTTP dan menangani otentikasi untuk Anda.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Menjalankan perintah tersebut menambahkan paket `Google.Cloud.Translation.V2` ke proyek Anda, memberi Anda akses ke kelas `TranslationClient` yang digunakan sepanjang panduan ini.

> **Mengapa langkah ini penting** – Menggunakan SDK menghindari konstruksi permintaan manual, mengurangi bug, dan memastikan Anda selaras dengan versi API terbaru dari Google.

## Langkah 2: Buat helper penerjemahan yang dapat digunakan kembali

Mengkapsulkan logika penerjemahan dalam kelas statis membuat kode dapat digunakan kembali dan memisahkan penanganan kunci API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Mengapa kami mengembalikan dictionary** – Ketika Anda perlu **translate multiple languages**, mengorganisir hasil berdasarkan kode bahasa memudahkan proses selanjutnya.

## Langkah 3: Bangun aplikasi konsol yang menggunakan helper

Berikut adalah `Program.cs` lengkap yang mendemonstrasikan penerjemahan teks tunggal serta penerjemahan batch.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Output konsol yang diharapkan**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Mengapa blok try/catch?** – Kesalahan jaringan, batas kuota, atau kunci API yang tidak valid akan memunculkan pengecualian. Menangani mereka dengan baik meningkatkan pengalaman pengguna dan menjaga aplikasi Anda tetap stabil.

## Langkah 4: Amankan kunci API Anda

Menyisipkan kunci API secara langsung, seperti yang ditunjukkan di atas, dapat diterima untuk demo cepat tetapi tidak untuk produksi. Ikuti praktik berikut:

* Simpan kunci dalam variabel lingkungan (`GOOGLE_API_KEY`) dan baca saat runtime:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Gunakan **Google Application Default Credentials** alih-alih kunci API saat berjalan di Google Cloud (App Engine, Cloud Run, dll.).
* Batasi kunci hanya untuk Translation API di konsol Google Cloud dan batasi penggunaan ke alamat IP atau referer tertentu.

## Langkah 5: Perluas solusi untuk skenario dunia nyata

### Menangani deteksi bahasa

Jika Anda perlu mengetahui bahasa sumber, objek respons berisi `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Menerjemahkan dokumen besar

API mendukung hingga 30 KB per permintaan. Untuk teks yang lebih besar, bagi konten menjadi potongan, terjemahkan setiap potongan, lalu gabungkan hasilnya. Jaga batas kalimat tetap utuh untuk menghindari frasa yang canggung.

### Pembatasan laju dan kuota

Google memberlakukan batas permintaan per menit. Terapkan kebijakan retry dengan back‑off eksponensial untuk menghormati batas kuota dan menghindari error `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Pertanyaan umum dan kasus tepi

**Q: Bisakah saya menerjemahkan seluruh halaman HTML?**  
A: Ya. Gunakan parameter `Format` (`"text"` atau `"html"`) saat memanggil `TranslateText`. SDK mengekspos ini melalui overload `TranslateText` yang menerima `TranslateTextRequest`.

**Q: Bagaimana jika sebuah bahasa tidak didukung?**  
A: API mengembalikan error. Validasi kode bahasa terhadap daftar yang dikembalikan oleh `client.ListSupportedLanguages()` sebelum membuat permintaan.

**Q: Apakah API mengenakan biaya per karakter?**  
A: Google menagih per karakter yang diterjemahkan. Perkirakan biaya menggunakan halaman harga dan pertimbangkan caching terjemahan yang sering digunakan.

---

## Kesimpulan

Anda sekarang tahu **how to translate text** di C# menggunakan Google Translate API resmi. Tutorial ini mencakup **Google translate example**, mendemonstrasikan **translate multiple languages**, dan menyoroti praktik siap produksi seperti keamanan kunci API dan penanganan error. Dengan menggunakan kembali helper `Translator`, Anda dapat mengintegrasikan penerjemahan ke dalam layanan .NET apa pun, aplikasi desktop, atau mikroservis.

**Langkah selanjutnya**

* Jelajahi **Google Translate tutorial** untuk fitur lanjutan seperti glosarium dan model khusus.  
* Gabungkan kode ini dengan ASP.NET Core untuk membuat API web multibahasa.  
* Bereksperimen dengan batch translation file CSV untuk mengotomatisasi pipeline lokalisasi.

Selamat coding, dan nikmati membangun aplikasi yang dapat diakses secara global!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara menyimpan dokumen Word yang diterjemahkan di C# dengan Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Menerjemahkan string ke bahasa Spanyol di C# dengan Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}