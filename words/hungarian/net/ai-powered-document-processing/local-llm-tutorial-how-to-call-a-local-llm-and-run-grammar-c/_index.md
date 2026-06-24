---
category: general
date: 2026-06-24
description: Helyi LLM oktató, amely bemutatja, hogyan hívj meg egy helyi LLM-et,
  tölts be egy Word-dokumentumot, és futtass nyelvtani ellenőrzést AI nyelvtani ellenőrzéssel
  C#-ban.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: hu
og_description: A helyi LLM oktatóanyag lépésről lépésre bemutatja, hogyan hívj meg
  egy helyi LLM-et, tölts be egy Word‑dokumentumot, és futtass AI nyelvtani ellenőrzést
  C#‑ban.
og_title: Helyi LLM oktató – Helyi LLM hívása és nyelvtani ellenőrzés
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Helyi LLM útmutató – Hogyan hívjunk meg egy helyi LLM-et és végezzünk nyelvhelyességi
  ellenőrzést
url: /hu/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Helyi LLM Bemutató – Helyi LLM Hívása és Nyelvtani Ellenőrzés Futtatása

Valaha is elgondolkodtál, hogyan **futtathatsz nyelvtani ellenőrzést** egy Word fájlon anélkül, hogy bármit is a felhőbe küldenél? Ebben a **helyi llm bemutatóban** összekapcsolunk egy ön‑hostolt nagy nyelvi modellt, betöltünk egy `.docx` fájlt, és hagyjuk, hogy az AI rendbe tegye a szöveget. Nincsenek API kulcsok, nincs külső forgalom – csak a saját géped végzi a nehéz munkát.

Átvezetünk minden egyes kódsoron, elmagyarázzuk, miért fontos minden részlet, és még megmutatjuk, hogyan kezeld a tipikus buktatókat (például hiányzó fájlok vagy elérhetetlen végpont). A végére egy kész, futtatható C# konzolalkalmazást kapsz, amely **ai nyelvtani ellenőrzést** végez egy helyben futtatott modellen.

> **Mit kapsz:** egy teljes, futtatható programot, egyértelmű magyarázatot minden lépéshez, és tippeket a megoldás nagyobb dokumentumokra vagy különböző LLM szolgáltatókra való skálázásához.

![helyi llm bemutató diagram](https://example.com/local-llm-tutorial-diagram.png "Diagram a helyi llm bemutató folyamatáról")

## Előfeltételek

- .NET 6.0 SDK vagy újabb (letöltheted a Microsoft oldaláról)
- Egy helyben futó LLM szerver, amely OpenAI‑kompatibilis végpontot biztosít (pl. Ollama, LM Studio, vagy egy egyedi FastAPI wrapper)
- Az `AiGrammar` NuGet csomag (vagy bármely könyvtár, amely biztosítja a `LocalLargeLanguageModel`, `Document` és `AiModelType` osztályokat)
- Egy minta Word dokumentum (`input.docx`) egy mappában, amelyre később hivatkozol

Ennyi—nincs szükség extra felhő hitelesítő adatra.

## 1. lépés: Helyi LLM Bemutató – Végpont Beállítása

Az első dolog, amire szükségünk van, egy **call local llm** objektum, amely tudja, hová küldje a kéréseket. Gondolj rá úgy, mint egy telefonszámra, amelyet tárcsálsz, mielőtt beszélni tudnál.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Miért fontos ez:**  
A legtöbb LLM SDK egy HTTP végpontot vár, amely követi az OpenAI API szerződését. Az `Endpoint` `http://localhost:8000/v1`-re mutatva azt mondjuk a könyvtárnak, hogy **call local llm**-et használjon az OpenAI szerverek helyett. A dummy API kulcs csak egy helyőrző – egyes kliensek nem fogadják el a null értéket, ezért adunk neki egy ártalmatlan értéket.

> **Pro tipp:** Ha a LLM-et egy reverz proxy mögött futtatod, állítsd be az `Endpoint`-ot a proxy URL-re, és hagyd, hogy a proxy kezelje a TLS terminálást. Ez egyszerűvé és biztonságossá teszi a konzolalkalmazást.

## 2. lépés: Word Dokumentum Betöltése a Nyelvtani Ellenőrzéshez

Miután a modell elérhető, be kell **load word document** tartalmat memóriába töltenünk. A `Document` osztály elrejti a `.docx` feldolgozás részleteit számunkra.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Miért fontos ez:**  
A bináris `.docx` fájl közvetlenül az LLM-nek adása összezavarná. A `Document` segédeszköz kinyeri a nyers szöveget, miközben megőrzi a bekezdéselválasztásokat, ami tiszta bemenetet biztosít a **ai grammar check** számára. A létezés ellenőrzése megakadályoz egy kellemetlen `FileNotFoundException`-t, amely egyébként összeomlasztaná az alkalmazást.

## 3. lépés: Nyelvtani Ellenőrzés Futtatása az LLM-mel

Itt a bemutató szíve: megkérjük a helyi modellt, hogy lektorálja a szöveget. A `CheckGrammar` metódus elrejti a HTTP részleteket és egy eredményobjektumot ad vissza.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Miért fontos ez:**  
`AiModelType.Gpt4` csak egy címke, amely megmondja a távoli szolgáltatásnak, melyik prompt sablont használja. Ha kisebb modellt használsz (pl. `Llama2`), cseréld ki ennek megfelelően. A könyvtár sorosítja a dokumentum szövegét, elküldi a `http://localhost:8000/v1/completions` címre, és feldolgozza a javított kimenetet.

> **Szélsőséges eset:** Ha az LLM időtúllép, a `CheckGrammar` `TimeoutException`-t dob. Tedd a hívást egy `try/catch` blokkba, ha nagy dokumentumokra vagy terhelt szerverre számítasz.

## 4. lépés: A Javított Szöveg Kiírása

Végül megjelenítjük a megtisztított változatot. Egy valódi alkalmazásban visszaírhatod egy új `.docx` fájlba, de ehhez a bemutatóhoz egy konzol kiírás elég.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Várható kimenet**  

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Ha az LLM nem talált hibát, a kimenet azonos lesz a bemenettel, ami még mindig hasznos jelzés.

## Teljes Működő Példa

Mindent összevonva, itt a teljes program, amelyet egyszerűen beilleszthetsz egy új konzolprojektbe:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Hogyan Futtassuk

1. Nyiss egy terminált a projekt mappájában.  
2. Futtasd a `dotnet run` parancsot.  
3. Figyeld, ahogy a konzol kiírja a javított szöveget.

Ez a teljes **local llm tutorial** kevesebb mint 100 sor kódban.

## Gyakran Ismételt Kérdések (GYIK)

### Használhatok másik LLM márkát?

Természetesen. Amíg a szerver tiszteletben tartja az OpenAI v1 API sémát, egyszerűen módosítsd az `Endpoint`-ot és válaszd ki a megfelelő `AiModelType` enum értéket (pl. `AiModelType.Llama2`). A kód többi része változatlan marad.

### Mi van, ha a dokumentumom hatalmas (10 MB+)?

A nagy adatmennyiségek meghaladhatják sok szerver alapértelmezett kérésméretét. Oszd fel a dokumentumot szakaszokra, és hívj `CheckGrammar`-t szakaszonként, majd fűzd össze az eredményeket. Ez csökkenti az időtúllépés esélyét is.

### Hogyan írjam vissza a javított kimenetet egy `.docx` fájlba?

A `Document` osztály általában biztosít egy `Save(string path, string content)` metódust. Miután megkaptad a `result.CorrectedText`-et, hívd meg:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Nézd meg a könyvtár dokumentációját a pontos szignatúráért.

### Biztonsági kockázatot jelent a dummy API kulcs?

Nem. A kulcsot a self‑hostolt végpontok figyelmen kívül hagyják, de egyes SDK-k megkövetelik, hogy ne legyen null string. Egy `"dummy"` helyőrző használata kielégíti az SDK-t anélkül, hogy bármilyen titkot felfedne.

## Következő Lépések és Kapcsolódó Témák

- **Finomhangold a helyi LLM-edet** domain‑specifikus nyelvtanra (pl. jogi vagy orvosi írás).  
- **Futtass egy kötegelt feladatot**, amely egy teljes mappában lévő Word fájlokat dolgozza fel – nagyszerű kiadási folyamatokhoz.  
- Fedezd fel a **streaming válaszokat**, ha valós‑időben szeretnél javaslatokat a felhasználó gépelése közben.  
- Kombináld ezt **helyesírás-ellenőrző könyvtárakkal** a dupla rétegű minőségkapu érdekében.

Ezek az ötletek mind a **local llm tutorial** alapvető koncepcióira épülnek, így ugyanazokat a mintákat fogod látni – **call local llm**, **load word document**, **run grammar check**, és **handle results** – a teljes anyagban.

---

*Boldog kódolást! Ha elakadsz, írj egy megjegyzést alább, és együtt megoldjuk a problémát.*

## Mit Érdemes Következőként Tanulni?

Az alábbi bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Betöltés Kódolással Word Dokumentumban](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Titkosított Betöltés Word Dokumentumban](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Sérült DOCX helyreállítása – Word Dokumentum Megnyitása és Betöltése](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}