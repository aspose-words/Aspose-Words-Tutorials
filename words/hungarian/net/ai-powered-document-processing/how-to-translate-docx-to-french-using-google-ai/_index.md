---
category: general
date: 2026-11-18
description: Tanulja meg, hogyan lehet a docx fájlt franciára fordítani a Google AI
  fordítással, az egész dokumentumot lefordítani, és a lefordított dokumentumot három
  lépésben elmenteni.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: hu
lastmod: 2026-11-18
og_description: Fordítsd le a docx-et franciára azonnal a Google AI fordítással. Kövesd
  ezt az útmutatót, hogy az egész dokumentumot lefordítsd, és könnyedén elmentsd a
  lefordított dokumentumot.
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: Docx fájl fordítása franciára a Google AI-val – gyors útmutató
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
title: Hogyan lehet a docx-et franciára fordítani a Google AI segítségével
url: /hu/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan fordítsuk le a docx-et franciára a Google AI segítségével

Ha **docx-et franciára** szeretnél fordítani, a Google AI fordítás lehetővé teszi, hogy néhány C# kódsorral lefordítsd az egész dokumentumot. Ez az útmutató pontosan megmutatja, hogyan fordítsd le egy DOCX fájlt, hogyan fordítsd le az egész dokumentum tartalmát, és hogyan mentsd el a lefordított dokumentumot megbízható módon.

Megtanulod, hogyan állítsd be a Google Cloud Translation klienst, hogyan tölts be egy Word fájlt, hogyan hívod meg az API-t minden bekezdés lefordításához, és végül hogyan írd meg a **save translated document** lépést. Nem szükséges külső szkriptek vagy kézi másolás‑beillesztés – minden a .NET alkalmazásodban fut.

## Amire szükséged lesz

* .NET 6.0 SDK vagy újabb telepítve  
* Egy Google Cloud projekt, amelyben a **Cloud Translation API** engedélyezve van  
* Egy service‑account JSON kulcsfájl (letöltve a Google Cloud konzolból)  
* Visual Studio 2022 (vagy bármelyik kedvenc C# IDE-d)  

Ezek az előfeltételek biztosítják, hogy a **google ai translation** hívások sikeresek legyenek, és hogy a Open XML SDK-val tudj DOCX fájlokat olvasni/írni.

## A projekt beállítása és a szükséges SDK-k telepítése

1. Hozz létre egy új konzolos projektet:

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. Add hozzá a tutorial által használt NuGet csomagokat:

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   *`Google.Cloud.Translate.V3`* biztosítja a **google ai translation** klienst, míg a *`DocumentFormat.OpenXml`* lehetővé teszi a DOCX fájlok kezelését anélkül, hogy a Microsoft Office telepítve lenne.

3. (Opcionális) Ha magasabb szintű wrappert szeretnél, telepítheted a `GroupDocs.Translator`-t:

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   Az alábbi kódpéldák mindkét megközelítéssel működnek; a Open XML változat teljes egészében látható a transzparencia érdekében.

## A forrás DOCX fájl betöltése

Az első funkcionális lépés a lefordítani kívánt Word dokumentum beolvasása. Az Open XML SDK segítségével kinyerheted minden bekezdés szövegét egy listába.

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

**Miért fontos:** A fájl egyszeri betöltése és a szöveg memóriában tartása lehetővé teszi, hogy **translate entire document** tartalmat egyetlen API hívással bekezdésenként fordíts le, elkerülve az ismétlődő fájl I/O műveleteket.

## Google AI fordítás végrehajtása

Miután megvannak az eredeti bekezdések, hívd meg a Translation API-t, hogy minden karakterláncot angolról (vagy bármely forrásnyelvről) franciára konvertálj. A kliens automatikusan felismeri a forrásnyelvet, ha `null`-t adsz meg.

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

**Miért fontos:** A **google ai translation** kötegelt kéréssel történő használata csökkenti a késleltetést és a költséget az egy‑hívás‑per‑bekezdés ciklusokhoz képest. A módszer emellett bemutatja a **how to translate docx** programozott módon.

## Új DOCX létrehozása a lefordított szöveggel

Miután megkaptad a francia szövegeket, írd vissza őket egy új DOCX fájlba. Az alábbi segédosztály egy új dokumentumot épít a lefordított bekezdésekből.

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

## Összeállítás – a teljes program

Az alábbiakban a teljes, futtatható konzolos alkalmazás látható, amely összekapcsolja a korábbi kódrészleteket. Bemutatja a **translate docx to french** funkciót, végrehajtja a **google ai translation**-t, és végül a **save translated document** lépést.

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

### Várható kimenet

Amikor futtatod a programot (`dotnet run`), a konzol valami hasonlót ír ki:

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

Nyisd meg az `output_fr.docx`-t Worddel, LibreOffice-szal vagy bármelyik megjelenítővel, és látni fogod, hogy az eredeti angol tartalom francia fordításokkal lett helyettesítve.

## Docx franciára fordítása – lépésről‑lépésre áttekintés

### 1. Google hitelesítő adatok biztonságos beállítása

* Helyezd a service‑account JSON fájlt egy biztonságos helyre, például

## Mit érdemes még megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és felfedezni alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan mentsünk lefordított Word dokumentumot C#-ban a Google AI segítségével](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Hogyan fordítsuk le a DOCX-et franciára és automatizáljuk a dokumentum fordítását](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}