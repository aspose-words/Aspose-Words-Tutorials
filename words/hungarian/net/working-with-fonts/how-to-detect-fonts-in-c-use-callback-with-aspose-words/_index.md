---
category: general
date: 2026-03-17
description: Hogyan lehet felismerni a betűtípusokat C#‑ban az Aspose.Words és egy
  figyelmeztető visszahívás segítségével. Tanulja meg, hogyan használja a visszahívást
  a hiányzó betűtípus‑helyettesítések rögzítésére a dokumentumok betöltése közben.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: hu
og_description: Hogyan lehet felismerni a betűtípusokat C#-ban az Aspose.Words használatával.
  Ez az útmutató bemutatja, hogyan használjunk visszahívást a hiányzó betűtípusra
  vonatkozó figyelmeztetések rögzítéséhez egy dokumentum betöltése közben.
og_title: Hogyan detektáljuk a betűtípusokat C#-ban – Callback használata az Aspose.Words-szal
tags:
- Aspose.Words
- C#
- Document Processing
title: Hogyan lehet betűtípusokat detektálni C#-ban – Callback használata az Aspose.Words-szal
url: /hu/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan lehet betűtípusokat észlelni C#‑ban – Figyelmeztető visszahívás használata az Aspose.Words‑szal

Szükséged volt már **betűtípusok észlelésére** egy Word‑dokumentumban programozott módon, és azon tűnődtél, miért néznek furcsán ki bizonyos karakterek a konvertálás után? Nem vagy egyedül. Sok valós projektnél – számlagenerálók, jelentésexportálók vagy kötegelt feldolgozó csővezetékek – a hiányzó betűtípusok csendes elrendezési hibákat okoznak, amelyeket nehéz nyomon követni.

A jó hír? Az Aspose.Words tiszta módot biztosít ezeknek a problémáknak a feltárására egy figyelmeztető visszahívással. Ebben az útmutatóban megmutatjuk, **hogyan használj visszahívást** a betűtípus‑helyettesítések rögzítésére, amelyet az Aspose a dokumentum betöltésekor végez, és egy kész‑példát kapsz, amely egyértelmű jelentést nyomtat a hiányzó betűtípusokról.

A következőket fogjuk áttekinteni:

* A minimális előfeltételeket (egy .NET projekt és az Aspose.Words NuGet csomag).  
* Hogyan valósítsd meg az `IWarningCallback`‑t a `WarningType.FontSubstitution` figyelésére.  
* Hogyan csatlakoztasd a visszahívást a `LoadOptions`‑hoz, és tölts be egy dokumentumot.  
* Milyen lesz a kimenet, valamint néhány gyakorlati tipp a termelési kódhoz.

A végére képes leszel automatikusan **betűtípusok észlelésére** bármely DOCX, DOC vagy RTF fájlban, és a hiányzó betűtípus‑információk alapján reagálni – legyen szó naplózásról, felhasználói értesítésről vagy tartalék betűtípus használatáról.

---

![Hogyan lehet betűtípusokat észlelni egy Word‑dokumentumban az Aspose.Words figyelmeztető visszahívásával](https://example.com/images/detect-fonts.png "hogyan lehet betűtípusokat észlelni egy Word‑dokumentumban")

## Amit szükséged lesz

* **.NET 6.0** vagy újabb (a példa .NET Framework 4.6+‑al is lefordítható).  
* **Aspose.Words for .NET** – telepítsd a NuGet‑en keresztül: `Install-Package Aspose.Words`.  
* Egy minta Word‑fájl, amely szándékosan egy olyan betűtípust hivatkozik, amely nincs telepítve (pl. `MissingFont.docx`).  

További könyvtárak nem szükségesek; minden az Aspose névtérben található.

---

## Betűtípusok észlelése figyelmeztető visszahívással

### 1. lépés: Hozz létre egy figyelmeztető‑visszahívás osztályt

A visszahívás implementálja az `IWarningCallback` interfészt. Amikor az Aspose.Words olyan betűtípust talál, amelyet nem talál, egy `WarningInfo`‑t generál a `WarningType.FontSubstitution` típussal. Az osztályunk egyszerűen egy barátságos sort ír a konzolra.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Miért fontos:** A `WarningType.FontSubstitution` szűrésével elkerüljük a zajos figyelmeztetéseket (például elavult funkciók), és a napló csak arra a konkrét problémára fókuszál, amelyet meg akarsz oldani – **a hiányzó betűtípusok észlelésére**.

---

### 2. lépés: Csatold a visszahívást a `LoadOptions`‑hoz

A `LoadOptions` lehetővé teszi a dokumentum beolvasásának testreszabását. A `FontWarningCollector`‑t a `WarningCallback` tulajdonsághoz rendelve az Aspose minden hiányzó betűtípus esetén meghívja azt.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tipp:** Itt beállíthatod a `LoadOptions.FontSettings`‑et is, ha programozottan szeretnél tartalék betűtípust megadni. Ez egy haladóbb forgatókönyv, amelyet később érintünk.

---

### 3. lépés: Töltsd be a dokumentumot és figyeld a kimenetet

Most már betöltjük a fájlt. Amint az Aspose beolvassa a dokumentumot, minden nem megtalált betűtípus aktiválja a visszahívásunkat.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Várható konzolkimenet** (ha a dokumentum a *Comic Sans MS* betűtípust hivatkozza, amely nincs telepítve):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Ha a dokumentum több hiányzó betűtípust tartalmaz, minden betűtípushoz egy sor jelenik meg – pontosan a **betűtípusok észleléséhez** szükséges információval.

---

## Visszahívás használata összetettebb forgatókönyvekhez

### Naplózás fájlba a konzol helyett

Éles környezetben valószínűleg tartós naplóra van szükség. Cseréld le a `Console.WriteLine`‑t egy `StreamWriter`‑re:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Figyelmeztetések gyűjtése későbbi elemzéshez

Előfordulhat, hogy a dokumentum betöltése után szeretnéd a hiányzó betűtípusok listáját felhasználni, például egy UI‑párbeszédablakban megjeleníteni. Tárold a figyelmeztetéseket egy `List<string>`‑ben, és tedd elérhetővé:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Tartalék betűtípus programozott megadása

Ha van egy vállalati betűtípus, amelyet kötelezően használni szeretnél, hozzáadhatod a `FontSettings`‑hez a betöltés előtt:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Ezután az Aspose a hiányzó betűtípusokat az *Arial Unicode MS*‑re cseréli, miközben a helyettesítést továbbra is jelzi a visszahíváson keresztül. Így egy praktikus módja van a **visszahívás használatának** a detektálás és az automatikus javítás egyidejű megoldására.

---

## Gyakori hibák és profi tippek

| Hiba | Miért fordul elő | Hogyan kerüld el |
|------|------------------|------------------|
| **Elfelejtett `Aspose.Words.Warnings` hivatkozás** | Az `IWarningCallback` interfész ott található. | A fájl tetején add hozzá a `using Aspose.Words.Warnings;` sort. |
| **Dokumentum betöltése `LoadOptions` nélkül** | Az alapértelmezett betöltő csendben helyettesíti a betűtípusokat figyelmeztetés nélkül. | Mindig hozz létre egy `LoadOptions` példányt, és rendeld hozzá a visszahívást. |
| **Korlátozott jogosultságokkal futó szerver** | A naplófájl írása `UnauthorizedAccessException`‑t dobhat. | Használj írható mappát (pl. az alkalmazás adatkönyvtárát), vagy maradj a memóriában tárolt gyűjteményeknél. |
| **Több szál osztozik ugyanazon gyűjtőn** | A `FontWarningCollector` alapértelmezésben nem szálbiztos. | Hozz létre külön gyűjtőt szálanként, vagy védd a listát egy lock‑kal. |
| **Feltételezés, hogy a visszahívás beágyazott betűtípusokra is lefut** | A beágyazott betűtípusok már a dokumentumban vannak, ezért nem keletkezik figyelmeztetés. | Ha a beágyazott betűtípusok integritását akarod ellenőrizni, vizsgáld meg a `FontInfo`‑t a `FontSettings`‑en keresztül. |

---

## Teljes, működő példa (másolás‑beillesztés kész)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Ami látnod kell** (ha a fájl két hiányzó betűtípust hivatkozik):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Ha a fájl csak telepített betűtípusokat használ, a konzol egyszerűen ezt írja:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Összegzés

Áttekintettük, **hogyan lehet betűtípusokat észlelni** egy Word‑dokumentumban egy egyedi figyelmeztető visszahívás beillesztésével az Aspose.Words‑ba. Ez a megközelítés könnyű, csak

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}