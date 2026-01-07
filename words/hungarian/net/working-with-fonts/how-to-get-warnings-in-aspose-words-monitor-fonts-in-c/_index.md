---
category: general
date: 2026-01-06
description: Tanulja meg, hogyan kapjon figyelmeztetéseket a dokumentumok betöltésekor,
  és hogyan figyelje a betűtípusokat az Aspose.Words használatával. Ez az útmutató
  a figyelmeztetési visszahívásokat és a betűtípus‑helyettesítés nyomon követését
  tárgyalja.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: hu
og_description: Hogyan kapjunk figyelmeztetéseket az Aspose.Words-ben? Kövesse ezt
  a lépésről‑lépésre útmutatót a betűtípusok nyomon követéséhez és a helyettesítési
  üzenetek rögzítéséhez a dokumentumok betöltése közben.
og_title: Figyelmeztetések lekérése az Aspose.Words-ben – Betűtípusok monitorozása
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Hogyan kapjunk figyelmeztetéseket az Aspose.Words-ben – Betűtípusok figyelése
  C#-ban
url: /hu/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan kapjunk figyelmeztetéseket az Aspose.Words-ben – Betűtípusok figyelése C#-ban

Gondolkodtál már azon, **hogyan kapjunk figyelmeztetéseket**, amikor egy Word-dokumentum olyan betűtípusokat tartalmaz, amelyek nincsenek telepítve? Ez gyakori probléma—az alkalmazásod csendben helyettesíti a hiányzó betűtípusokat, és soha nem tudod, mi változott. A jó hír, hogy bekapcsolódhatsz az Aspose.Words figyelmeztető rendszerébe, és **valós időben figyelheted a betűtípusokat**.

Ebben az útmutatóban pontosan megmutatjuk, hogyan lehet elkapni ezeket a betűtípus‑helyettesítési figyelmeztetéseket, miért fontos ez, és mit tegyél az információval, miután megvan. Nincs külső dokumentáció, csak egy teljes, futtatható példa, amelyet most beilleszthetsz a Visual Studio‑ba.

> **Pro tipp:** Ha dokumentum‑konverziós csővezettet építesz, a hiányzó betűtípusok korai naplózása megakadályozza a későbbi, kellemetlen elrendezési meglepetéseket.

---

## Amire szükséged lesz

- **Aspose.Words for .NET** (legújabb verzió; az API nem változott a v23.10 óta)
- .NET fejlesztői környezet (Visual Studio, Rider vagy VS Code a C# kiegészítővel)
- Egy minta `.docx`, amely egy olyan betűtípust hivatkozik, amely nincs telepítve (pl. **„NonExistentFont”**)

Ennyi—nincs további NuGet csomag az Aspose.Words‑en kívül.

## 1. lépés – Figyelmeztetésgyűjtő beállítása (Primary Keyword in Header)

Az első dolog, amire szükséged van, egy hely a figyelmeztetések tárolására, amint előfordulnak. Az Aspose.Words a `WarningCallback` tulajdonságot biztosítja a `LoadOptions`‑on keresztül pontosan erre a célra.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Miért fontos:**  
Amikor a könyvtár hiányzó betűtípust talál, nem dob kivételt; egy `WarningInfo` objektumot bocsát ki. Egy gyűjtő csatlakoztatásával teljes rálátást nyersz minden helyettesítési eseményre, lehetővé téve a **betűtípusok figyelését** anélkül, hogy a konzolt felesleges üzenetekkel szennyeznéd.

## 2. lépés – Dokumentum betöltése a figyelmeztetés‑engedélyezett beállításokkal

Most ténylegesen beolvassuk a fájlt. Az előző lépésben előkészített `LoadOptions` biztosítja, hogy minden betűtípus‑kapcsolódó figyelmeztetés rögzítésre kerüljön.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Mi történik a háttérben?**  
Az Aspose.Words beolvassa a Word-fájlt, feloldja a betűtípusokat, és amikor nem találja a kért betűtípust, egy helyettesítőre (általában Arial) vált. A helyettesítés egy `WarningType.FontSubstitution` figyelmeztetést generál, amely a `warningCollector`‑be kerül.

## 3. lépés – Gyűjtött figyelmeztetések ellenőrzése (Primary Keyword Appears Again)

Miután a dokumentum betöltődött, egyszerűen végigiterálunk a `warningCollector`‑en, és kiírjuk a betűtípus‑helyettesítési üzeneteket.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Várható kimenet** (ha a hiányzó betűtípus *„FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Ha a dokumentum több ismeretlen betűtípust tartalmaz, minden helyettesítéshez egy sor jelenik meg — tökéletes naplózáshoz vagy riasztáshoz.

## 4. lépés – Opcionális: Figyelmeztetések naplózása vagy mentése

Éles környezetben valószínűleg többre van szükséged, mint egy `Console.WriteLine`. Íme egy gyors példa, amely a figyelmeztetéseket egy JSON fájlba írja későbbi elemzés céljából.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Most már van egy állandó rekordod, amelyet betáplálhatsz egy felügyeleti műszerfalba, vagy akár automatikus kérést indíthatsz a hiányzó betűtípusfájlok beszerzésére.

## 5. lépés – Az eredmény ellenőrzése és takarítás

Futtasd a programot. Ha látod a helyettesítési üzeneteket, sikeresen **kapottál figyelmeztetéseket**, és most aktívan **figyeled a betűtípusokat**. Ha semmi sem jelenik meg, ellenőrizd, hogy a tesztdokumentum valóban egy nem telepített betűtípust hivatkozik-e.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

A nulla darabszám általában azt jelenti, hogy:

1. Minden betűtípust feloldottak (lehet, hogy a betűtípus *valóban* telepítve van helyileg), vagy
2. A dokumentum nem tartalmazott olyan betűtípus‑hivatkozást, amely helyettesítést igényelt volna.

## Gyakori hibák és elkerülésük

| Hiba | Miért fordul elő | Megoldás |
|------|------------------|----------|
| **Nem jelennek meg figyelmeztetések** | A betűtípus valójában létezik a rendszeren, vagy a dokumentum csak beépített betűtípusokat használ. | Nevezd át a betűtípust a forrásfájlban valami lehetetlenre (pl. `XYZ123`), és próbáld újra. |
| **Túl sok figyelmeztetés (zaj)** | Sok dokumentumot töltesz be egy ciklusban a gyűjtő kiürítése nélkül. | Hozz létre új `WarningInfoCollection`‑t minden egyes dokumentumhoz, vagy hívd a `warningCollector.Clear()`‑t a feldolgozás után. |
| **Teljesítménybeli hatás** | A túlzott lemezre írás lassíthatja a kötegelt feldolgozást. | Gyűjtsd a figyelmeztetéseket memóriában, és írd őket tömbben, vagy használj aszinkron fájl‑I/O‑t. |
| **Hiányzó `using Aspose.Words.Loading;`** | A `LoadOptions` osztály ebben a névtérben található. | Add hozzá a hiányzó `using` direktívát, ahogy az 1. lépésben látható. |

## A megoldás kibővítése – Egyéb figyelmeztetéstípusok figyelése

Bár a betűtípus‑helyettesítés a legszembetűnőbb, az Aspose.Words figyelmeztetéseket is kiadhat:

- **Elavult funkciók** (`WarningType.Deprecated`),
- **Lehetséges adatveszteség** (`WarningType.DataLoss`),
- **Nem támogatott fájlformátumok** (`WarningType.UnsupportedFileFormat`).

A 3. lépésben a szűrőt kibővítheted, hogy ezeket is elkapd:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Így már nem csak **hogyan figyeljük a betűtípusokat**, hanem **hogyan kapjunk figyelmeztetéseket** bármilyen, az alkalmazásod által előforduló helyzetre is.

## Teljes működő példa (másolás‑beillesztés kész)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Futtasd:** Építsd fel a projektet, indítsd el, és látni fogod a figyelmeztetéseket kiírva és mentve. Ez a teljes válasz a **hogyan kapjunk figyelmeztetéseket** és a **hogyan figyeljük a betűtípusokat** kérdésekre az Aspose.Words használatával.

## Összegzés

Most már tudod, **hogyan kapjunk figyelmeztetéseket** az Aspose.Words‑től, különösen a betűtípus‑helyettesítési helyzetekben, és megtanultad, **hogyan figyeljük a betűtípusokat** a dokumentum‑betöltési folyamat során. A `WarningCallback` csatolásával, a gyűjtött `WarningInfo` iterálásával, valamint az adatok opcionális mentésével teljes átláthatóságot nyersz a hiányzó betűtípus‑események felett — ami elengedhetetlen képesség bármely dokumentum‑feldolgozó csővezeték számára.

Mi a következő lépés? Próbáld meg kibővíteni a figyelmeztetési szűrőt, hogy adatveszteség‑ vagy elavult‑funkció‑figyelmeztetéseket is lefedjen, vagy integráld a JSON‑naplót egy felügyeleti műszerfalba, például Grafana‑ba. Ugyanaz a minta minden figyelmeztetéstípusra működik, így jól fel vagy készülve, hogy bármilyen problémát nyomon kövess, amit az Aspose.Words dob.

Boldog kódolást, és legyenek a dokumentumaid mindig úgy megjelenítve, ahogy elvárod!

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}