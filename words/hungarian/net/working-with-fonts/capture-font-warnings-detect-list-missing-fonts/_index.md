---
category: general
date: 2025-12-31
description: Rögzítse a betűtípus‑figyelmeztetéseket az Aspose.Words‑ben a hiányzó
  betűtípusok felderítéséhez, és listázza a hiányzó betűtípusokat .NET‑alkalmazásában.
  Ismerje meg a lépésről‑lépésre C# megoldást.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: hu
og_description: Fogja el a betűtípus-figyelmeztetéseket az Aspose.Words-ben a hiányzó
  betűtípusok felderítéséhez és listázásához. Teljes C# útmutató kóddal és tippekkel.
og_title: Betűtípus‑figyelmeztetések rögzítése – Hiányzó betűtípusok felismerése és
  listázása
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Betűtípus Figyelmeztetések Rögzítése – Hiányzó Betűtípusok Felismerése és Listázása
url: /hu/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus Figyelmeztetések Rögzítése – Hiányzó Betűtípusok Felismerése és Listázása

Valaha is szükséged volt **betűtípus figyelmeztetések rögzítésére** egy Word-dokumentum betöltésekor, de nem tudtad, hogyan jelenítsd meg a hiányzó betűtípus részleteit? Nem vagy egyedül. Sok valós projektben a hiányzó betűtípusok elrendezési hibákat okoznak, és megfelelő figyelmeztetések nélkül a láthatatlan hibák után kell kutatnod.  

Ebben az útmutatóban megmutatjuk, hogyan **észlelheted a hiányzó betűtípusokat** és hogyan **listázhatod a hiányzó betűtípusokat** az Aspose.Words for .NET segítségével. A végére egy azonnal futtatható C# kódrészletet kapsz, amely kiírja az összes helyettesítési figyelmeztetést, így naplózhatod, riaszthatod vagy akár automatikusan is cserélheted a betűtípusokat.

---

## Miért fontos a betűtípus figyelmeztetések rögzítése

Amikor az Aspose.Words megnyit egy DOCX-et, amely egy a szerveren nem telepített betűtípust hivatkozik, csendben helyettesíti egy tartalék betűtípussal. A dokumentum rendben néz ki, de a vizuális hűség sérül – gondolj egy vállalati márka logójára, amely a rossz betűtípussal jelenik meg.  

A figyelmeztetések rögzítése lehetővé teszi, hogy:

* **Márka konzisztencia fenntartása** – pontosan tudod, mely betűtípusok hiányoznak.  
* **Automatikus helyreállítás** – programozottan cserélheted a hiányzó betűtípusokat.  
* **Megfelelőség auditálása** – jelentéseket generálhatsz jogi vagy tervezési felülvizsgálatokhoz.  

Röviden, a **betűtípus figyelmeztetések rögzítése** az első védelmi vonal a csendes betűtípus helyettesítés ellen.

---

## LoadOptions beállítása a hiányzó betűtípusok észleléséhez

A figyelmeztetések megjelenítésének kulcsa a `LoadOptions.FontSubstitutionWarning` tulajdonság. Alapértelmezés szerint `None` értékre van állítva, ami azt jelenti, hogy az Aspose.Words elnyeli az üzeneteket. `All`-ra állítva a könyvtár minden helyettesítési eseményt rögzít.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

**Pro tipp:** Ha már van egy egyéni betűtípus mappád, rendeld hozzá a `FontSettings.SetFontsFolder("path")` metódussal a dokumentum betöltése előtt. Így **észlelheted a hiányzó betűtípusokat**, amelyek nincsenek a rendszerkönyvtárban.

---

## Dokumentum betöltése és a hiányzó betűtípusok listázása

Miután a `LoadOptions` készen áll, a következő lépés a Word-fájl betöltése. A konstruktor elfogadja az opciók objektumát, és minden helyettesítés a dokumentum `WarningInfoCollection`-jában lesz rögzítve.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Ha a fájl olyan betűtípusokra hivatkozik, amelyek nem érhetők el, minden hiányzó betűtípus egy `WarningInfo` bejegyzést generál. A **hiányzó betűtípusok listázásához** egyszerűen iterálj a gyűjteményen.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

A tipikus kimenet így néz ki:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Minden sor pontosan megmondja, mely betűtípus hiányzott, ezzel teljesítve a **hiányzó betűtípusok listázása** követelményt.

---

## A WarningInfoCollection olvasása és értelmezése

A `WarningInfoCollection` különböző figyelmeztetéstípusokat tartalmazhat (pl. `DocumentStructure`, `ImageLoading`). A betűtípus-problémákra való kizárólagos fókuszáláshoz szűrd le `WarningType.FontSubstitution` alapján.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Miért szűrj? Mert egy nagy dokumentum figyelmeztetéseket generálhat sérült képekről vagy nem támogatott funkciókról is. A gyűjtemény szűkítésével elkerülöd a zajt, és a **betűtípus figyelmeztetések rögzítése** kimenet tiszta marad.

---

## Teljes működő példa – Betűtípus figyelmeztetések rögzítése akcióban

Az alábbiakban a teljes, önálló program látható, amelyet bármely .NET konzolprojektbe beilleszthetsz. Bemutatja a `LoadOptions` konfigurálásától a hiányzó betűtípusok rendezett listájának kiírásáig minden lépést.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Várható konzol kimenet**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Ha a dokumentum nem tartalmaz hiányzó betűtípusokat, a következőt fogod látni:

```
All referenced fonts are available – no warnings captured.
```

---

## Gyakori szélsőséges esetek és megoldásuk

| Szituáció | Miért fordul elő | Javasolt megoldás |
|-----------|------------------|-------------------|
| **A dokumentum beágyazott OpenType betűtípust használ** | Az Aspose.Words képes beágyazott betűtípusok olvasására, de csak ha a fájl nem sérült. | Először ellenőrizd a DOCX-et Wordben; szükség esetén ágyazd be újra a betűtípust. |
| **Sok figyelmeztetés** (pl. 200+ hiányzó betűtípus) | A régi rendszerekből történő tömeges import gyakran sokféle betűtípust hivatkozik. | A figyelmeztetéseket kötegelt módon dolgozd fel: tárold őket adatbázisban, majd futtass egy betűtípus‑telepítő scriptet. |
| **A WarningInfoCollection üres** | Vagy a dokumentum minden betűtípust tartalmaz, vagy a `FontSubstitutionWarning` `None`-ra van állítva. | Ellenőrizd a `LoadOptions` beállításait, és győződj meg róla, hogy a helyes fájlútvonalat töltöd be. |
| **Egyéni betűtípusok hálózati megosztáson** | A hálózati késleltetés időtúllépést okozhat a betűtípus keresésekor. | Töltsd be előre a betűtípusokat a `FontSettings`-be a `SetFontsFolder` használatával, és állítsd `CacheFontData = true`-ra. |

---

## Képi illusztráció

![betűtípus figyelmeztetések rögzítése példa](https://example.com/images/capture-font-warnings.png "betűtípus figyelmeztetések rögzítése példa")

*A képernyőkép egy konzol futtatást mutat, ahol két hiányzó betűtípust jelent a rendszer.*

---

## Következő lépések – Túl a egyszerű jelentésen

Most, hogy **betűtípus figyelmeztetéseket rögzíthetsz**, gondolj a helyreállítás automatizálására:

1. **Automatikus betűtípus helyettesítés** – Cseréld le a hiányzó betűtípusokat a vállalat által jóváhagyott tartalékra a `FontSettings.SubstitutionSettings` módosításával.  
2. **Naplózás egy felügyeleti rendszerbe** – A figyelmeztető üzeneteket irányítsd a Serilog, ELK vagy Azure Application Insights felé.  
3. **Felhasználó számára készített jelentések** – Készíts HTML vagy PDF összefoglalót, amelyben a tervezők áttekinthetik, mely betűtípusok telepítése szükséges.  

Mindezek a kiterjesztések ugyanarra az alapra épülnek, amit bemutattunk: a `LoadOptions` konfigurálása, a dokumentum betöltése és a `WarningInfoCollection` olvasása.

---

## Következtetés

Most megtanultad, hogyan **rögzítsd a betűtípus figyelmeztetéseket** az Aspose.Words-ban, **észleld a hiányzó betűtípusokat**, és **listázd a hiányzó betűtípusokat** egy tiszta, konzol‑barát kimenettel. A megközelítés egyszerű, csak néhány C# sorra van szükség, és bármely .NET verzióval működik, amely támogatja az Aspose.Words 23.x vagy újabb verzióját.  

Próbáld ki egy olyan DOCX példán, amely egy szándékosan eltávolított betűtípust hivatkozik – a figyelmeztetések azonnal megjelennek. Ettől kezdve eldöntheted, hogy telepíted a hiányzó betűtípusokat, programozottan helyettesíted őket, vagy egyszerűen naplózod a problémát későbbi áttekintés céljából.  

Boldog kódolást, és legyenek a dokumentumaid mindig a megfelelő betűtípusokkal megjelenítve!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}