---
category: general
date: 2026-11-15
description: Tanulja meg, hogyan fordíthat szöveget a Google segítségével C#-ban.
  Ez az útmutató egy Google Translate példát mutat be, több nyelv kezelését és a legjobb
  gyakorlatokat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: hu
lastmod: 2026-11-15
og_description: Hogyan fordítsunk szöveget a Google segítségével C#-ban egy teljes
  Google Translate példával. Kövesd ezt az útmutatót, hogy több nyelvet biztonságosan
  fordíts.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Hogyan fordítsunk szöveget a Google Translate API-val C#-ban – gyors útmutató
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
title: Hogyan fordítsunk szöveget a Google Translate API-val C#-ban – lépésről lépésre
  útmutató
url: /hu/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan fordítsunk szöveget a Google Translate API-val C#-ban – lépésről‑lépésre útmutató

Ha **hogyan fordítsunk szöveget** kell egy .NET alkalmazásban, a Google Cloud Translation API megbízható, nyelvfüggetlen megoldást kínál. Ebben az útmutatóban egy **Google Translate példa** látsz, amely egy egyszerű karakterláncot fordít le, kiterjed a **több nyelv fordítására**, és a legjobb gyakorlatokat követi az API kulcsok és a hibakezelés terén.

Egy készen‑futó C# konzolprogrammal, a **Google‑al történő szövegfordítás** világos megértésével, és a kód nagyobb projektekhez való adaptálásának bizalmával távozhatsz.

## Amit ez az útmutató lefed

* Google Cloud projekt beállítása és API kulcs beszerzése.  
* A `Google.Cloud.Translation.V2` NuGet csomag telepítése.  
* Tiszta, újrahasználható kód írása, amely **hogyan fordítsunk szöveget** a hivatalos SDK-val.  
* A megoldás kiterjesztése **több nyelv fordítására** egyetlen hívásban.  
* Gyakori buktatók és tippek a produkciószintű megvalósításokhoz.

### Előfeltételek

* .NET 6.0 SDK vagy újabb (a kód .NET Core és .NET Framework alatt is fordul).  
* A Google Cloud fiók, amelyen a **Cloud Translation API** engedélyezve van.  
* Alapvető ismeretek C#-ról és konzolalkalmazásokról.  

---

## 1. lépés: A Google Cloud Translation klienskönyvtár telepítése

A hivatalos klienskönyvtár elrejti a HTTP hívásokat és kezeli a hitelesítést helyetted.

```bash
dotnet add package Google.Cloud.Translation.V2
```

A parancs futtatása hozzáadja a `Google.Cloud.Translation.V2` csomagot a projektedhez, így hozzáférsz a `TranslationClient` osztályhoz, amelyet az egész útmutatóban használunk.

> **Miért fontos ez a lépés** – Az SDK használata elkerüli a manuális kérésépítést, csökkenti a hibákat, és biztosítja, hogy a Google legújabb API verziójával legyen összhangban.

## 2. lépés: Újrahasználható fordítósegéd létrehozása

A fordítási logika egy statikus osztályba való kapszulázása újrahasználhatóvá teszi a kódot, és elkülöníti az API‑kulcs kezelését.

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

> **Miért visszaadunk egy szótárat** – Amikor **több nyelv fordítására** van szükség, az eredmények nyelvkód szerint való rendezése egyszerűvé teszi a további feldolgozást.

## 3. lépés: A segédet használó konzolalkalmazás felépítése

Az alábbiakban egy teljes `Program.cs` látható, amely bemutatja az egyszerű szövegfordítást és a kötegelt fordítást is.

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

**Várható konzolkimenet**

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

> **Miért vannak a try/catch blokkok?** – Hálózati hibák, kvóta korlátok vagy egy érvénytelen API kulcs kivételeket dob. Ezeknek a hibáknak az elegáns kezelése javítja a felhasználói élményt és stabilan tartja az alkalmazást.

## 4. lépés: Az API kulcs védelme

Az API kulcs kódba ágyazása, ahogy fent látható, gyors demóhoz elfogadható, de nem alkalmas termeléshez. Kövesd az alábbi gyakorlatokat:

* Tárold a kulcsot egy környezeti változóban (`GOOGLE_API_KEY`) és olvasd be futásidőben:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Használd a **Google Application Default Credentials**-t API kulcs helyett, amikor a Google Cloud-on (App Engine, Cloud Run, stb.) futtatod.
* Korlátozd a kulcsot a Translation API-ra a Google Cloud konzolon, és korlátozd a használatot konkrét IP-címekre vagy hivatkozókra.

## 5. lépés: A megoldás kiterjesztése valós környezetekhez

### Nyelvfelismerés kezelése

Ha tudnod kell a forrásnyelvet, a válaszobjektum tartalmazza a `DetectedSourceLanguage` mezőt:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Nagy dokumentumok fordítása

Az API legfeljebb 30 KB-ot támogat kérésenként. Nagyobb szövegek esetén oszd fel a tartalmat darabokra, fordítsd le minden darabot, majd fűzd össze az eredményeket. Tartsd meg a mondatszegélyeket, hogy elkerüld a szokatlan megfogalmazásokat.

### Kéréskorlátok és kvóták

A Google percenkénti kéréskorlátot alkalmaz. Implementálj egy újrapróbálkozási szabályt exponenciális visszatéréssel, hogy tiszteletben tartsd a kvóta korlátokat és elkerüld a `429 Too Many Requests` hibákat.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Gyakori kérdések és szélhelyzetek

**Q: Lefordíthatok egy teljes HTML oldalt?**  
A: Igen. Használd a `Format` paramétert (`"text"` vagy `"html"`), amikor a `TranslateText`-et hívod. Az SDK ezt a `TranslateText` túlterhelésen keresztül teszi elérhetővé, amely egy `TranslateTextRequest`-et fogad.

**Q: Mi van, ha egy nyelv nem támogatott?**  
A: Az API hibát ad vissza. A kérések előtt ellenőrizd a nyelvkódokat a `client.ListSupportedLanguages()` által visszaadott lista alapján.

**Q: Az API karakterenként számláz?**  
A: A Google a lefordított karakterek száma alapján számláz. Becsüld meg a költségeket a díjszabási oldalon, és fontold meg a gyakori fordítások gyorsítótárazását.

---

## Összegzés

Most már tudod, **hogyan fordítsunk szöveget** C#-ban a hivatalos Google Translate API használatával. Az útmutató egy **Google translate példát** mutatott be, demonstrálta a **több nyelv fordítását**, és kiemelte a termelésre kész gyakorlatokat, mint az API‑kulcs biztonsága és a hibakezelés. A `Translator` segéd újrahasználatával bármely .NET szolgáltatásba, asztali alkalmazásba vagy mikroszolgáltatásba beépítheted a fordítást.

**Következő lépések**

* Fedezd fel a **Google Translate tutorial**-t a fejlett funkciókhoz, mint a szójegyzékek és egyedi modellek.  
* Kombináld ezt a kódot az ASP.NET Core-val, hogy többnyelvű web API-t hozz létre.  
* Kísérletezz CSV fájlok kötegelt fordításával a lokalizációs folyamatok automatizálásához.

Boldog kódolást, és élvezd a globálisan elérhető alkalmazások építését!

## Mit érdemes legközelebb megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan mentsünk lefordított Word dokumentumot C#-ban Google AI-val](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Karakterlánc fordítása spanyolra C#-ban Aspose.Words AI-val](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}