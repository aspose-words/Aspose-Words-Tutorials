---
category: general
date: 2026-01-13
description: Tanulja meg, hogyan hívja meg az LLM-et C#-ból egy helyi LLM végpont
  használatával, szerkessze a Word-fájlokat, távolítsa el az összes tartalmat, és
  mentse a docx-et – mindezt egyetlen oktatóanyagon belül.
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: hu
og_description: Hogyan hívjunk LLM-et C#-ból helyi modell segítségével, szerkesszünk
  Word-dokumentumokat, távolítsuk el az összes tartalmat, és mentsük hatékonyan a
  docx-et.
og_title: Hogyan hívjunk LLM-et C#‑ban – Lépésről lépésre útmutató
tags:
- Aspose.Words
- C#
- LLM Integration
title: Hogyan hívjuk meg az LLM-et C#-ban – Teljes útmutató helyi modellel
url: /hu/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hívjuk meg az LLM-et C#‑ban – Teljes útmutató helyi modellel

Gondolkodtál már **hogyan hívjuk meg az LLM‑et** egy .NET alkalmazásból anélkül, hogy adatot küldenénk a felhőbe? Nem vagy egyedül. Sok fejlesztő szeretné a promptokat és a dokumentumokat helyben tartani, különösen érzékeny szövegek esetén. Ebben a tutorialban egy valós példán keresztül mutatjuk be: hogyan használjunk egy önállóan üzemeltetett LLM végpontot egy Word dokumentum átfogalmazásához, az összes tartalom eltávolításához, a fájl szerkesztéséhez, és végül **hogyan mentsük el a docx‑et** vissza a lemezre.

Kitérünk a **helyi LLM használatára**, megmutatjuk a pontos kódot az Aspose.Words `Document` **összes tartalmának eltávolításához**, és elmagyarázzuk a Word fájlok programozott szerkesztésének finomságait. A végére egy másol‑és‑beilleszt megoldással fogsz rendelkezni, amely az Aspose.Words 7+ és bármely OpenAI‑kompatibilis helyi modell esetén működik.

## Előfeltételek – Amire szükséged lesz a kezdéshez

- **.NET 6+** (vagy .NET Framework 4.7.2, ha a klasszikus változatot részesíted előnyben)
- **Aspose.Words for .NET** NuGet csomag (`Aspose.Words` és `Aspose.Words.AI`)
- Egy **helyi LLM**, amely OpenAI‑kompatibilis `/v1` végpontot biztosít (pl. egy GPT‑Neo szerver a `http://localhost:8000/v1` címen)
- Egy minta `input.docx` fájl, amelyet egy általad irányított mappában helyezel el
- Visual Studio, Rider vagy bármely kedvenc szerkesztőd – a képernyőképeken VS Code‑t használok

> **Pro tipp:** Ha még nincs helyi modelled, nézd meg a ingyenes Docker‑képet a GPT‑Neo 2.7B‑hez – kevesebb mint egy perc alatt elindul, és ugyanazt az API‑szerződést követi, amit itt használunk.

## 1. lépés – A helyi LLM végpont konfigurálása (Hogyan hívjuk meg az LLM‑et)

Az első dolog, amit meg kell tenned, amikor **hogyan hívjuk meg az LLM‑et** C#‑ból, hogy létrehozz egy kliensobjektumot, amely a saját szolgáltatásodra mutat. Az Aspose.Words.AI egy `LocalLargeLanguageModel` segédfüggvényt biztosít, amely elrejti a HTTP hívásokat.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **Miért fontos:** A végpont saját kezű konfigurálásával teljes kontrollt gyakorolsz a kérés‑payloadok, a hitelesítés és a késleltetés felett. Ez a **hogyan hívjuk meg az LLM‑et** alapja, anélkül, hogy külső szolgáltatásokra támaszkodnál.

## 2. lépés – A forrás Word dokumentum betöltése (Hogyan szerkesszünk Word‑öt)

Ezután betöltjük az eredeti `.docx`‑et egy Aspose `Document`‑be. Ez a klasszikus “hogyan szerkesszünk Word‑öt” lépés: miután a fájl a memóriában van, lekérdezheted, módosíthatod vagy teljesen kicserélheted a tartalmát.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Ha a fájl nem létezik, `FileNotFoundException`‑t kapsz, ezért ellenőrizd, hogy az útvonal helyes‑e. `Stream`‑ből is betöltheted, ha feltöltésekkel dolgozol.

## 3. lépés – A módosított szöveg generálása a helyi LLM‑mel (Hogyan hívjuk meg az LLM‑et)

Most jön a varázslat: megkérjük az LLM‑et, hogy a teljes szöveget formális hangnemben írja át. A promptot egy rövid utasítás és a `document.GetText()`‑vel kinyert nyers szöveg összefűzésével építjük fel.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Szélsőséges eset:** Ha a forrásdokumentum hatalmas (több mint 10 k token), előfordulhat, hogy eléri a modell kontextus‑korlátját. Ilyenkor oszd fel a szöveget bekezdésekre, és minden darabra hívd meg a `GenerateText`‑et.

## 4. lépés – Az összes meglévő tartalom eltávolítása (Remove All Content)

Mielőtt az új szöveget beillesztenénk, tisztítani kell a dokumentumot. Az Aspose `RemoveAllChildren()`‑t kínálja, amely kitörli a szekciókat, bekezdéseket, táblákat – mindent. Ez a kanonikus mód **az összes tartalom eltávolítására** egy Word fájlból.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **Mi van, ha csak a törzset szeretnéd törölni, a fejléceket megtartani?** Használd a `document.Sections.Clear()`‑t, majd építsd újra a szükséges szekciókat.

## 5. lépés – A módosított szöveg beillesztése (Hogyan szerkesszünk Word‑öt)

Tiszta lapra már beírhatjuk az LLM‑generált szöveget. A `DocumentBuilder` egy barátságos réteg, amely lehetővé teszi bekezdések, táblák, képek stb. hozzáadását. Itt egyszerűen egyetlen bekezdésként írjuk ki az egész stringet.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Ha gazdagabb formázásra van szükséged (félkövér, címsorok), elemezheted az LLM kimenetét markdown jelölések után, és ennek megfelelően állíthatod be a `builder.Font` beállításokat.

## 6. lépés – A frissített dokumentum mentése (Hogyan mentsük el a docx‑et)

Végül a változtatásokat egy új fájlba mentjük. Ez bemutatja, **hogyan mentsük el a docx‑et** programozott szerkesztés után.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

A `Save` metódus automatikusan a fájlkiterjesztés alapján detektálja a formátumot, így egyetlen sor módosításával PDF‑re, HTML‑re vagy ODT‑re is exportálhatsz.

### Várt eredmény

Amikor megnyitod a `output.docx`‑et, az eredeti tartalom teljesen átfogalmazva, egy kifinomult, formális stílusban jelenik meg. Nincsenek megmaradt táblák, fejlécek vagy láblécek a forrásból – csak a frissen generált szöveg, amit az LLM‑nek kértél.

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "how to call llm example")

*Image alt text:* **hogyan hívjuk meg az LLM‑et példaként, amely a átfogalmazott Word dokumentumot mutatja**

## Gyakori kérdések és hibaelhárítás

### 1. “Mi van, ha az LLM hibát ad vissza?”

A `GenerateText` metódus `HttpRequestException`‑t dob nem‑2xx válaszok esetén. Tekerd be a hívást egy `try/catch`‑be, és vizsgáld meg az `ex.Message`‑et. Gyakran hiányzik egy API‑kulcs fejléc, vagy a modell token‑korlátját lépted túl.

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. “Szerkeszthetek-e a dokumentum egyes részeit anélkül, hogy mindent törölnék?”

Természetesen. Használd a `document.GetChildNodes(NodeType.Paragraph, true)`‑t a bekezdések felsorolásához, majd csak ott cseréld le a `Paragraph.Text` tulajdonságot, ahol változtatni szeretnél. Ez a megközelítés lehetővé teszi a **hogyan szerkesszünk Word‑öt** finom szintű módosítását, miközben a stílusok megmaradnak.

### 3. “Létezik‑e mód a eredeti formázás megtartására?”

Ha a stílusok megőrzése a cél, fontold meg, hogy az LLM kimenetét egyszerű szövegként kapod, majd a `builder.Font.StyleIdentifier`‑t alkalmazod minden bekezdésre a sablonod alapján. Alternatívaként használhatod a `DocumentBuilder.InsertHtml()`‑t, ha az LLM HTML‑t tud előállítani.

### 4. “Hogyan kezeljem a nagy dokumentumokat?”

Oszd fel a dokumentumot szekciókra (`document.Sections`), és minden szekciót külön dolgozz fel. Ez nemcsak a token‑korlátot kerülő megoldás, hanem csökkenti a memória‑nyomást is.

## Teljesítmény tippek

- **Használd újra a `LocalLargeLanguageModel` példányt** több hívás között; az alatta lévő `HttpClient` élő kapcsolatot tart.
- **Cache‑eld a módosított szöveget**, ha ugyanazt a promptot gyakran futtatod – az LLM hívások költségesek lehetnek még helyi hardveren is.
- **Párhuzamosítsd** a szekciófeldolgozást `Parallel.ForEach`‑el, ha többmagos CPU‑val és szálbiztos LLM klienssel rendelkezel.

## Következő lépések – A munkafolyamat bővítése

Most, hogy már tudod **hogyan hívjuk meg az LLM‑et**, **helyi LLM használata**, **az összes tartalom eltávolítása**, **hogyan szerkesszünk Word‑öt**, és **hogyan mentsük el a docx‑et**, érdemes lehet:

- **Kötegelt feldolgozás**: egy mappában lévő `.docx` fájlok ciklikus átfogalmazása.
- **Egyedi promptok**: a prompt testreszabása összefoglalók, felsorolások vagy fordítások generálásához.
- **Integráció ASP.NET Core‑dal**: HTTP végpont kiépítése, amely fájlfeltöltést fogad, futtatja az LLM‑et, és visszaadja a szerkesztett dokumentumot.
- **Haladó stíluskezelés**: markdown feldolgozása az LLM‑től, és a Word stílusokra való leképezése `DocumentBuilder`‑rel.

Ezek a kiterjesztések mind a már bemutatott alapmintára épülnek, így minimális erőfeszítéssel adaptálhatod a kódot.

---

## Összegzés

Ebben az útmutatóban bemutattuk, **hogyan hívjuk meg az LLM‑et** C#‑ból egy önálló végponton keresztül, demonstráltuk a **helyi LLM használatát**, megmutattuk a helyes **az összes tartalom eltávolítását** egy Word fájlból, elmagyaráztuk a **hogyan szerkesszünk Word‑öt** programozottan, és egyértelmű példával illusztráltuk a **hogyan mentsük el a docx‑et**. A teljes, futtatható mintakód készen áll bármely .NET projektbe, a magyarázatok pedig megadják a “miért” hátterét minden lépéshez – így könnyen módosíthatod, bővítheted vagy hibakeresheted a megoldást.

Próbáld ki, kísérletezz különböző promptokkal, és hagyd, hogy a helyi LLM végezze a nehéz munkát a dokumentum‑automatizálási folyamataidban. Ha elakadsz, a hibaelhárítási szekció a megfelelő irányba mutat. Jó kódolást, és élvezd az on‑prem LLM‑ek erejét!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}