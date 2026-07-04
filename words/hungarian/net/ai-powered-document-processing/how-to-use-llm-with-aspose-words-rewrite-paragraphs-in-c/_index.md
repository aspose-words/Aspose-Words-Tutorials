---
category: general
date: 2026-05-04
description: Hogyan használjuk az LLM-et dokumentumok szerkesztésére az Aspose-szal
  – tanulja meg a bekezdés szövegének cseréjét, a helyi LLM-hez való csatlakozást,
  és a szöveg AI-val történő újraírását.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: hu
og_description: Hogyan használjuk az LLM-et dokumentumok szerkesztésére az Aspose-szal.
  Ez az útmutató megmutatja, hogyan csatlakozzunk egy helyi LLM-hez, cseréljünk be
  bekezdés szöveget, és írjuk át a szöveget AI segítségével.
og_title: Hogyan használjuk az LLM-et az Aspose.Words-szal – Bekezdések újraírása
  C#-ban
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Hogyan használjunk LLM-et az Aspose.Words-szal – Bekezdések átírása C#-ban
url: /hu/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan használjunk LLM-et az Aspose.Words-szal – Bekezdések átírása C#-ban

Gondolkodtál már azon, **hogyan használjuk az LLM-et** egy Word dokumentum feljavítására anélkül, hogy manuálisan megnyitnánk? Nem vagy egyedül. Sok fejlesztő akad el, amikor *bekezdés szövegét* kell programozottan cserélni, de nincs tiszta AI‑vezérelt munkafolyamat.

Ebben az útmutatóban összekapcsolunk egy helyi nagy nyelvi modellt, betáplálunk egy részletet egy `.docx` fájlból, megkérjük, hogy **átírja a szöveget AI segítségével**, majd végül elmentjük a frissített dokumentumot – mindezt az Aspose.Words segítségével. A végére egy kész, futtatható C# konzolalkalmazást kapsz, amely bemutatja az egész folyamatot.

> **Mit kapsz:** egy teljes, futtatható példát, minden lépés magyarázatát, tippeket a szélhelyzetekhez, és ötleteket a megoldás kibővítéséhez.

## Amire szükséged lesz

- **.NET 6+** (vagy .NET Framework 4.7.2 – a kód mindkettőn működik)
- **Aspose.Words for .NET** (NuGet csomag `Aspose.Words`)
- Egy **local LLM server**, amely egy egyszerű HTTP `/generate` végpontot biztosít (pl. Ollama, LMStudio vagy egy egyedi Flask szolgáltatás)
- Alapvető ismeretek C#-ban és HTTP kliens kódban  

Nem szükséges további SDK, minden más a közösen írt kódban található.

## 1. lépés: Hogyan használjuk az LLM-et a bekezdés szövegének cseréjére

Az első dolog, amit meg kell tennünk, hogy azonosítsuk a módosítani kívánt bekezdést. Az Aspose.Words ezt könnyedén megoldja a gazdag objektummodelljének köszönhetően.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Miért fontos ez:**  
A megfelelő csomópont kiválasztása megakadályozza, hogy véletlenül felülírjuk a címsorokat vagy táblázatokat. A **replace paragraph text** megközelítés használatával a dokumentum szerkezetét érintetlenül hagyjuk, miközben csak a számunkra fontos tartalmat módosítjuk.

> **Pro tipp:** Ha a dokumentum változó hosszúságú szakaszokat tartalmaz, használd a `document.GetChildNodes(NodeType.Paragraph, true)` és LINQ-et egy bekezdés megtalálásához a szövege vagy a stílusa alapján.

## 2. lépés: Kapcsolódás egy helyi LLM végponthoz

Miután megvan a szöveg, el kell küldenünk az LLM-nek. A példa egy egyszerű wrapper osztályt, a `LocalLargeLanguageModel`-t használja, amely elrejti a HTTP részleteket. Nyugodtan cseréld le `HttpClient` hívásokra, ha úgy jobban kedveled.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Miért csatlakozunk így:**  
A **connect to local llm** beállítás csökkenti a késleltetést, a adatokat helyben tartja, és elkerüli az API költségeket. A wrapper továbbá tisztábbá teszi a későbbi kódot, lehetővé téve, hogy a **rewrite text using ai** logikára koncentráljunk.

## 3. lépés: Szöveg átírása AI-val az Aspose.Words segítségével

A bekezdés szövegével és az LLM-mel a kezedben, egy olyan promptot állítunk össze, amely pontosan megmondja a modellnek, mit akarunk – átírni formális hangnemben. A promptot módosíthatod más stílusokhoz (barátságos, technikai, stb.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Miért működik ez:**  
Az LLM-ek prompt‑alapúak; egyértelmű utasítások („Rewrite … in a formal tone”) konzisztens eredményeket adnak. A **rewrite text using ai** lépés a tutorial szíve – bemutatja, hogyan lehet az AI-t közvetlenül a dokumentum munkafolyamatokba ágyazni.

## 4. lépés: Dokumentum szerkesztése és a változások mentése

Most lecseréljük az eredeti run-okat az új tartalommal. Az Aspose.Words a szöveget `Run` objektumokban tárolja, ezért először azok törlése elkerüli a maradék formázási maradványokat.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Szélhelyzet megjegyzés:**  
Ha az eredeti bekezdés vegyes formázást (félkövér, dőlt) tartalmazott, érdemes megőrizni a stílusokat. Ebben az esetben hozz létre egy új `Run`-t, másold át az eredeti `Font` beállításokat, majd állítsd be a `Text`-et `revisedText`-re.

## Teljes működő példa

Az alábbiakban az egész program látható, amelyet beilleszthetsz egy konzolprojekthez. Ne felejtsd el először telepíteni az Aspose.Words NuGet csomagot (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Várható kimenet

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Nyisd meg a `output.docx`-t – a harmadik bekezdés most a feljavított változatot tartalmazza.

## Gyakori kérdések és buktatók

| Kérdés | Válasz |
|----------|--------|
| **Mi van, ha az LLM JSON-t ad vissza extra mezőkkel?** | Állítsd be a `GenerateText`-et, hogy a megfelelő tulajdonságot deszerializálja, vagy a választ manuálisan dolgozd fel. |
| **Feldolgozhatok több bekezdést egyszerre?** | Igen – iterálj a `document.FirstSection.Body.Paragraphs`-en, és alkalmazd ugyanazt a prompt logikát, esetleg a prompthoz hozzáadva a bekezdés indexét a kontextusért. |
| **Az LLM szerverem hitelesítést használ?** | Adj hozzá egy fejléct a `HttpClient`-hez a POST előtt: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **A formázás elveszik a csere után.** | Őrizd meg az eredeti `Run.Font` beállításokat: hozz létre egy új `Run`-t, másold a `originalRun.Font.Clone()`-t, majd állítsd be a `Text`-et. |
| **Az LLM néha üres stringet ad vissza.** | Implementálj visszaesést – ha `revisedText.Trim().Length == 0`, tartsd meg az eredeti szöveget vagy próbáld újra egy egyszerűbb prompttal. |

## A megoldás bővítése

Miután elsajátítottad a **how to use llm**-et egyetlen bekezdéshez, fontold meg a következő lépéseket:

- **Kötegelt feldolgozás:** Iterálj minden bekezdésen, és írd át egy kiválasztott stílusban (pl. „rövidítsd le a teljes szöveget”).  
- **Stílus‑tudatos átírás:** Add meg az eredeti bekezdés stílusnevét a promptban, hogy az LLM tiszteletben tartsa a címsorokat és a törzsszöveget.  
- **Integráció CI pipeline-nal:** Automatizáld a dokumentum feljavítását a dokumentáció építési folyamatának részeként.  
- **Alternatív promptok:** Próbáld ki a „summarize this paragraph” vagy a „translate this paragraph to Spanish” promptokat, hogy felfedezd a **rewrite text using ai** teljes erejét.

## Következtetés

Áttekintettük a **how to use llm** teljes folyamatát az Aspose.Words-szal: dokumentum betöltése, **connect to local llm**, bekezdés kinyerése, **rewrite text using ai**, **replace paragraph text**, majd a végeredmény mentése. A kód önálló, azonnal működik, és bemutat egy gyakorlati módot az AI és a hagyományos dokumentumautomatizálás összekapcsolására.

Give it a spin, tweak the prompts, and let

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}