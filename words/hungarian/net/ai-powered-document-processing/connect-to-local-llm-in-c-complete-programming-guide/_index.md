---
category: general
date: 2026-04-28
description: C#‑ból csatlakozz a helyi LLM‑hez, és kérd meg a nagy nyelvi modellt,
  hogy töltse be a Word‑dokumentumot, hívja meg a helyi LLM‑et, és automatikusan írja
  át a szöveget. Lépésről‑lépésre kód is mellékelve.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: hu
og_description: Csatlakozz C#-ból a helyi LLM-hez, és ismerd meg, hogyan kérdezd le
  a nagy nyelvi modellt, tölts be Word-dokumentumot, hívd meg a helyi LLM-et, és automatikusan
  írd át a szöveget percek alatt.
og_title: Csatlakozás helyi LLM-hez C#-ban – Teljes programozási útmutató
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Kapcsolódás helyi LLM-hez C#-ban – Teljes programozási útmutató
url: /hu/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kapcsolódás helyi LLM-hez C#-ban – Teljes programozási útmutató

Valaha is szükséged volt **helyi llm-hez kapcsolódni** egy .NET alkalmazásból, és azon tűnődtél, hogyan tudná egy Word‑fájlhoz beszélni? Nem vagy egyedül. Ebben az útmutatóban végigvezetünk a teljes folyamaton – helyi llm-hez kapcsolódás, **prompt large language model**, Word‑dokumentum betöltése, **call local llm**, és végül **rewrite text automatically**. A végére egy futtatható példát kapsz, amely bármely bekezdést formális hangnemre alakít át, külső API‑kulcsok nélkül.

## Amit ez a tutorial lefed

Először telepítjük a szükséges NuGet csomagokat, majd elindítunk egy egyszerű helyi LLM végpontot (gondolj az Ollama‑ra a 11434‑es porton). Ezután betöltünk egy `.docx` fájlt az Aspose.Words segítségével, elküldünk egy bekezdést az LLM‑nek, megkapjuk az átdolgozott változatot, és visszaírjuk ugyanabba a dokumentumba. Megmutatjuk, hogyan kezeljünk gyakori buktatókat – üres bekezdések, aszinkron felszabadítás, kódolási sajátosságok – hogy a kód ne csak demóként, hanem éles környezetben is működjön.

### Előfeltételek

- .NET 6.0 SDK vagy újabb (használhatod a .NET 8‑at is)
- Visual Studio 2022 vagy VS Code C# kiegészítővel
- **Aspose.Words for .NET** (az ingyenes próba is megfelelő)
- Helyileg futtatott LLM, amely támogatja a `/api/generate` szerződést (pl. Ollama, LMStudio)
- Alapvető ismeretek az async/await használatáról C#‑ban

> **Pro tipp:** Ha még nem telepítetted az Ollama‑t, futtasd a `ollama serve` parancsot, és húzz le egy modellt a `ollama pull llama3` segítségével. Az alapértelmezett HTTP végpont: `http://localhost:11434/api/generate`.

---

## 1. lépés: Szükséges csomagok telepítése

Először add hozzá az Aspose.Words és az Aspose.Words.AI NuGet csomagokat a projektedhez.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Ezek a könyvtárak biztosítják a **load word document** képességet, valamint egy könnyű réteget a **call local llm** híváshoz anélkül, hogy saját HTTP kéréseket kellene megírnod.

---

## 2. lépés: Kapcsolódás a helyi LLM végponthoz

Egy helyileg futtatott modellhez való csatlakozás olyan egyszerű, mint a `LocalLargeLanguageModel` példányosítása. A konstruktor a generálási végpont teljes URL‑jét várja.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Miért csomagoljuk be a végpontot egy osztályba? A `LocalLargeLanguageModel` kezeli a JSON sorosítást, az újrapróbálkozásokat és a streaming válaszokat – így a prompt logikára koncentrálhatsz, a `HttpClient`-el való bajlódás helyett.

---

## 3. lépés: A forrás Word‑dokumentum betöltése

Ezután a dokumentumot memóriába hozzuk. Az Aspose.Words gyakorlatilag minden Word‑formátumot támogat, így a `Document` a `input.docx`‑et Office telepítése nélkül is be tudja olvasni.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Ha stream‑mel kell dolgoznod (pl. egy ASP.NET‑en keresztül feltöltött fájl), egyszerűen cseréld le a fájlútvonalat egy `MemoryStream`‑re, és add át a `Document` konstruktorának.

---

## 4. lépés: Az aktuális bekezdés szövegének kinyerése

A `DocumentBuilder`‑rel navigálunk a dokumentumban. Ebben a példában az **első bekezdést** írjuk át, de a `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` segítségével több bekezdést is feldolgozhatsz.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

A `?.` operátor megakadályozza a `NullReferenceException`‑t, ha a dokumentum véletlenül üres. Ez egy tipikus **edge case**, amely a kezdőket gyakran meglepi.

---

## 5. lépés: Prompt a LLM‑nek a bekezdés átírásához

Most ténylegesen **prompt large language model**. A prompt egyszerű angol szöveg; a wrapper JSON‑ként küldi el a helyi végpontra.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Miért így fogalmazzuk meg a kérést? Az LLM‑ek a világos, egyfeladatos utasításokra reagálnak a legjobban. A kettőspont után egy sortörés elválasztja az instrukciót a tartalomtól, csökkentve annak esélyét, hogy a modell visszhangozza a promptot.

**Várható kimenet** – Ha az `originalParagraph` értéke `"Hey, what's up?"`, a LLM így válaszolhat:

> “Good day, how may I assist you?”

A végeredményt ellenőrizheted a kiíratással:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## 6. lépés: Az átírt szöveg visszaillesztése a dokumentumba

Miután megvan az új szöveg, lecseréljük a régi bekezdést. A `DocumentBuilder.Writeln` új sort ír és előre mozgatja a kurzort, ami tökéletes a hozzáfűzéshez. Ha **ugyanazt a bekezdést** szeretnéd felülírni, használhatod a `docBuilder.CurrentParagraph.RemoveAllChildren()`‑t a írás előtt.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Mindkét megközelítés látható, hogy a munkafolyamatodhoz leginkább illeszkedőt választhasd.

---

## 7. lépés: A módosított dokumentum mentése

Végül a változtatásokat egy új fájlba mentjük. Az Aspose.Words automatikusan a fájlkiterjesztés alapján választja ki a formátumot.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Nyisd meg az `output.docx`‑et Word‑ben, és láthatod, hogy a bekezdés most formális hangnemben jelenik meg.

---

## Teljes működő példa

Alább a **komplett, önálló program** található. Másold be egy konzolprojektbe, állítsd vissza a NuGet csomagokat, és futtasd – nincs szükség extra konfigurációra a futó helyi LLM‑en kívül.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Mit várhatsz a futtatás során

1. A konzol kiírja az eredeti és az átírt bekezdést.  
2. Az `output.docx` megjelenik az `input.docx` mellett.  
3. A fájl megnyitásakor az új formális bekezdés a régi után (vagy a helyettesítő kód használata esetén felülírva) látható.

---

## Gyakori edge case‑ek kezelése

| Helyzet | Megoldás |
|-----------|----------|
| **Üres vagy csak szóközöket tartalmazó bekezdés** | A promptolás előtt ellenőrizd a `string.IsNullOrWhiteSpace` értéket (lásd 3. lépés). |
| **Az LLM hibát vagy üres stringet ad vissza** | A `PromptAsync`‑t tedd `try/catch`‑be, és ha hiba történik, használd az eredeti szöveget. |
| **Több bekezdést kell átírni** | Iterálj a `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` elemein, és alkalmazd ugyanazt a prompt logikát. |
| **Nagy dokumentumok késleltetést okoznak** | Csoportosíts bekezdéseket, és egyetlen kérésben küldd el őket (max. 4 KB prompt egy híváshoz). |
| **Nem‑ASCII karakterek eltorzulnak** | Győződj meg róla, hogy a LLM végpont UTF‑8‑at használ (a legtöbb modern modell így működik). |

---

## Következő lépések és kapcsolódó témák

- **Prompt large language model** részletesebb instrukciókkal (pl. stílus útmutató, hosszkorlát).  
- **Call local llm** használata web‑API‑ban, hogy a dokumentum‑automatizálást szolgáltatásként tedd elérhetővé.  
- **Load word document** párhuzamos stream‑ekkel nagy áteresztőképességű forgatókönyvekhez.  
- Kombináld ezt a megközelítést **rewrite text automatically**‑val tömeges e‑mail generáláshoz vagy jelentés‑standardizáláshoz.  

Ha mélyebben szeretnél elmerülni, nézd meg az Aspose dokumentációját a **document merging** témakörben, valamint az Ollama API referenciát a saját mintavételi paraméterekhez.

---

## Összegzés

Megmutattuk, hogyan **kapcsolódj helyi llm-hez** C#‑ból, **prompt large language model**, **load word document**, **call local llm**, és **rewrite text automatically** – mindezt egyetlen futtatható konzolalkalmazásban. A minta skálázható: cseréld a promptot, iterálj bekezdéseken, vagy tedd elérhetővé egy ASP.NET végponton keresztül. A legfontosabb tanulság, hogy a helyi AI modellek szorosan integrálhatók a hagyományos dokumentum‑feldolgozó könyvtárakkal, így erőteljes automatizálást érhetsz el anélkül, hogy elhagynád a megbízható on‑prem környezetet.

Kérdések a szálkezeléssel kapcsolatban,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}