---
category: general
date: 2026-11-18
description: Pelajari cara menerjemahkan file docx ke bahasa Prancis dengan terjemahan
  AI Google, terjemahkan seluruh dokumen, dan simpan dokumen terjemahan dalam tiga
  langkah saja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: id
lastmod: 2026-11-18
og_description: Terjemahkan file docx ke bahasa Prancis secara instan menggunakan
  terjemahan AI Google. Ikuti panduan ini untuk menerjemahkan seluruh dokumen dan
  menyimpan dokumen terjemahan dengan mudah.
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: Terjemahkan docx ke Bahasa Prancis dengan Google AI – panduan cepat
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  headline: How to translate docx to French using Google AI
  type: TechArticle
- description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  name: How to translate docx to French using Google AI
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the NuGet packages that the tutorial relies on:'
    text: 'Add the NuGet packages that the tutorial relies on:'
  - name: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
    text: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
  type: HowTo
tags:
- C#
- Google AI
- Document translation
- Localization
title: Cara menerjemahkan docx ke bahasa Prancis menggunakan Google AI
url: /id/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menerjemahkan docx ke Bahasa Prancis menggunakan Google AI

Jika Anda perlu **menerjemahkan docx ke Bahasa Prancis**, terjemahan AI Google memungkinkan Anda menerjemahkan seluruh dokumen hanya dengan beberapa baris kode C#. Tutorial ini menunjukkan secara tepat cara menerjemahkan file DOCX, menerjemahkan seluruh konten dokumen, dan menyimpan dokumen yang telah diterjemahkan dengan cara yang dapat diandalkan.

Anda akan belajar cara menyiapkan klien Google Cloud Translation, memuat file Word, memanggil API untuk menerjemahkan setiap paragraf, dan akhirnya menulis langkah **save translated document**. Tidak diperlukan skrip eksternal atau penyalinan‑tempel manual—semuanya berjalan di dalam aplikasi .NET Anda.

## Apa yang Anda perlukan

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Proyek Google Cloud dengan **Cloud Translation API** diaktifkan  
* File kunci JSON akun layanan (diunduh dari konsol Google Cloud)  
* Visual Studio 2022 (atau IDE C# lain yang Anda sukai)  

Prasyarat ini memastikan panggilan **google ai translation** berhasil dan Anda dapat membaca/menulis file DOCX dengan Open XML SDK.

## Siapkan proyek dan instal SDK yang diperlukan

1. Buat proyek konsol baru:

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. Tambahkan paket NuGet yang dibutuhkan tutorial ini:

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   *`Google.Cloud.Translate.V3`* menyediakan klien **google ai translation**, sementara *`DocumentFormat.OpenXml`* memungkinkan Anda bekerja dengan file DOCX tanpa harus menginstal Microsoft Office.

3. (Opsional) Jika Anda lebih suka wrapper tingkat‑lebih‑tinggi, Anda juga dapat menginstal `GroupDocs.Translator`:

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   Contoh kode di bawah ini bekerja dengan kedua pendekatan; versi Open XML ditampilkan secara lengkap untuk transparansi.

## Muat file DOCX sumber

Langkah fungsional pertama adalah membaca dokumen Word yang ingin Anda terjemahkan. Dengan menggunakan Open XML SDK, Anda dapat mengekstrak teks setiap paragraf ke dalam sebuah daftar.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Reads all paragraph texts from a DOCX file.
    /// </summary>
    public static class DocxReader
    {
        public static List<string> GetParagraphs(string path)
        {
            var paragraphs = new List<string>();

            using (WordprocessingDocument wordDoc = WordprocessingDocument.Open(path, false))
            {
                Body body = wordDoc.MainDocumentPart.Document.Body;
                foreach (Paragraph para in body.Elements<Paragraph>())
                {
                    paragraphs.Add(para.InnerText);
                }
            }

            return paragraphs;
        }
    }
}
```

**Mengapa ini penting:** Memuat file sekali dan menyimpan teks di memori memungkinkan Anda **translate entire document** dengan satu panggilan API per paragraf, menghindari I/O file berulang.

## Lakukan terjemahan Google AI

Setelah Anda memiliki paragraf asli, panggil Translation API untuk mengonversi setiap string dari Bahasa Inggris (atau bahasa sumber apa pun) ke Bahasa Prancis. Klien secara otomatis mendeteksi bahasa sumber jika Anda mengirim `null`.

```csharp
using Google.Cloud.Translate.V3;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Handles translation using Google Cloud Translation (v3).
    /// </summary>
    public static class Translator
    {
        private static readonly TranslationServiceClient client;

        static Translator()
        {
            // The GOOGLE_APPLICATION_CREDENTIALS environment variable should point to your JSON key.
            client = TranslationServiceClient.Create();
        }

        /// <summary>
        /// Translates a list of strings to French.
        /// </summary>
        public static async Task<List<string>> TranslateToFrenchAsync(List<string> texts)
        {
            var request = new TranslateTextRequest
            {
                Parent = $"projects/{client.ProjectId}/locations/global",
                TargetLanguageCode = "fr",
                // SourceLanguageCode can be omitted for auto‑detection.
            };

            // Add all texts to the request.
            request.Contents.AddRange(texts);

            // Execute the translation.
            TranslateTextResponse response = await client.TranslateTextAsync(request);

            var translated = new List<string>();
            foreach (Translation translation in response.Translations)
            {
                translated.Add(translation.TranslatedText);
            }

            return translated;
        }
    }
}
```

**Mengapa ini penting:** Menggunakan **google ai translation** dalam permintaan batch mengurangi latensi dan biaya dibandingkan dengan loop satu‑panggilan‑per‑paragraf. Metode ini juga memperlihatkan **how to translate docx** secara programatik.

## Buat DOCX baru dengan teks terjemahan

Setelah Anda menerima string Bahasa Prancis, tulis kembali ke dalam file DOCX baru. Kelas pembantu berikut membangun dokumen baru dari paragraf yang telah diterjemahkan.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Writes a list of paragraphs to a new DOCX file.
    /// </summary>
    public static class DocxWriter
    {
        public static void Write(string outputPath, List<string> frenchParagraphs)
        {
            // Ensure the directory exists.
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath)!);

            // Create a new document.
            using (WordprocessingDocument wordDoc = WordprocessingDocument.Create(outputPath, DocumentFormat.OpenXml.WordprocessingDocumentType.Document))
            {
                MainDocumentPart mainPart = wordDoc.AddMainDocumentPart();
                mainPart.Document = new Document();
                Body body = mainPart.Document.AppendChild(new Body());

                foreach (string paraText in frenchParagraphs)
                {
                    Paragraph para = new Paragraph(new Run(new Text(paraText)));
                    body.AppendChild(para);
                }

                mainPart.Document.Save();
            }
        }
    }
}
```

## Gabungkan semuanya – program lengkap

Berikut adalah aplikasi konsol lengkap yang dapat dijalankan dan menggabungkan semua potongan kode sebelumnya. Program ini mendemonstrasikan **translate docx to french**, melakukan **google ai translation**, dan akhirnya **save translated document**.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    class Program
    {
        static async Task Main(string[] args)
        {
            // ------------------------------------------------------------------
            // 1️⃣ Load the source document
            // ------------------------------------------------------------------
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"Input file not found: {inputPath}");
                return;
            }

            var originalParagraphs = DocxReader.GetParagraphs(inputPath);
            Console.WriteLine($"Loaded {originalParagraphs.Count} paragraphs from input.docx.");

            // ------------------------------------------------------------------
            // 2️⃣ Translate the entire document to French using Google AI
            // ------------------------------------------------------------------
            var frenchParagraphs = await Translator.TranslateToFrenchAsync(originalParagraphs);
            Console.WriteLine("Translation completed – document is now in French.");

            // ------------------------------------------------------------------
            // 3️⃣ Save the translated document
            // ------------------------------------------------------------------
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output_fr.docx");
            DocxWriter.Write(outputPath, frenchParagraphs);
            Console.WriteLine($"Saved translated document to: {outputPath}");
        }
    }
}
```

### Output yang diharapkan

Saat Anda menjalankan program (`dotnet run`), konsol akan mencetak sesuatu yang mirip dengan:

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

Buka `output_fr.docx` dengan Word, LibreOffice, atau penampil apa pun, dan Anda akan melihat konten Bahasa Inggris asli digantikan oleh terjemahan Bahasa Prancis.

## Menerjemahkan docx ke Bahasa Prancis – ikhtisar langkah‑demi‑langkah

### 1. Siapkan kredensial Google secara aman

* Tempatkan file JSON akun layanan di lokasi yang aman, misalnya

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [How to save translated Word document in C# with Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [How to translate DOCX to French and automate document translation](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)
- [translate docx to french with Aspose.Words and Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}