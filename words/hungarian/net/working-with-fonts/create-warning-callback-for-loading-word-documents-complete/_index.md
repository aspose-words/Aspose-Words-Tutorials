---
category: general
date: 2026-03-25
description: Hozzon létre figyelmeztető visszahívást a Word-dokumentum betöltéséhez
  és a hiányzó betűtípusok észleléséhez. Ismerje meg, hogyan konfigurálhatja a betűtípus-beállításokat
  az Aspose.Words for .NET-ben.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: hu
og_description: Figyelmeztető visszahívás létrehozása a Word-dokumentum betöltéséhez,
  miközben hiányzó betűtípusokat észlel. Ez az útmutató bemutatja, hogyan konfigurálhatók
  a betűtípus-beállítások az Aspose.Words-ban.
og_title: Figyelmeztető visszahívás létrehozása – Word-dokumentum betöltése és hiányzó
  betűtípusok felderítése
tags:
- Aspose.Words
- C#
- Font handling
title: Figyelmeztető visszahívás létrehozása Word-dokumentumok betöltéséhez – Teljes
  útmutató
url: /hu/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Figyelmeztető visszahívás létrehozása – Word dokumentum betöltése és hiányzó betűtípusok észlelése

Volt már szükséged **figyelmeztető visszahívás** létrehozására egy Word dokumentum betöltésekor, és azon tűnődtél, miért tűnnek el egyszerűen a betűtípusok? Nem vagy egyedül. Sok vállalati alkalmazásban a hiányzó betűtípusok elrendezési katasztrófákat okoznak, és megfelelő visszahívás nélkül előfordulhat, hogy egyáltalán nem veszed észre a problémát.  

A jó hír? Az Aspose.Words for .NET segítségével **betöltheted a Word dokumentumot**, **észlelheted a hiányzó betűtípusokat**, és **konfigurálhatod a betűtípus beállításokat** néhány rendezett kódsorban. Ebben az útmutatóban végigvezetünk egy teljes, futtatható példán, elmagyarázzuk, miért fontos minden rész, és megmutatjuk, hogyan ellenőrizheted, hogy a figyelmeztető visszahívás a megfelelően működik.

> **Mit fogsz megtanulni**  
> * Egy teljes C# program, amely betölti a DOCX-et, jelentést készít a betűtípus helyettesítésekről, és lehetővé teszi a betűtípus keresési útvonalak testreszabását.  
> * A `FontSettings`, `LoadOptions` és `IWarningCallback` osztályok megértése.  
> * Tippek a széljegyek kezelésére, például beágyazott betűtípusok vagy rendszer‑szintű betűtípus mappák esetén.

---

## Előfeltételek

- .NET 6+ (vagy .NET Framework 4.7.2+) C# fordítóval.  
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`).  
- Egy minta Word fájl (`input.docx`), amely legalább egy a gépen nem telepített betűtípust használ (pl. *Calibri Light* egy minimális Windows konténerben).  
- Alapvető ismeretek a C# konzolalkalmazásokról.

Nem szükséges további könyvtár; minden az Aspose.Words-ben található.

---

## 1. lépés: Figyelmeztető visszahívás létrehozása a hiányzó betűtípusok észleléséhez

A feladvány **elsődleges** része egy olyan osztály, amely megvalósítja az `IWarningCallback` interfészt. Az Aspose.Words minden alkalommal meghívja ezt a visszahívást, amikor olyan helyzetbe ütközik, amely figyelmeztetést igényel – a betűtípus helyettesítés a leggyakoribb.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Miért fontos** – Visszahívás nélkül a naplókat kellene átnézned utólag. A figyelmeztetések valós időben történő kezelése lehetővé teszi, hogy eldöntsd, megszakítsd-e a betöltést, helyettesítsd a hiányzó betűtípust egy tartalék betűtípussal, vagy egyszerűen naplózd a problémát későbbi áttekintéshez.

---

## 2. lépés: FontSettings konfigurálása egyedi betűtípuskezeléshez

Mielőtt ténylegesen betöltenénk a dokumentumot, érdemes lehet megmondani az Aspose.Words-nek, hol keressen a rendszerben nem jelenlévő betűtípusokat. Itt jön képbe a `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Miért fontos** – Ha az Aspose.Words-et egy olyan mappára irányítod, amely tartalmazza a hiányzó betűtípusokat, gyakran elkerülheted a helyettesítést. Ha ez nem lehetséges, egy ésszerű alapértelmezett (például *Arial*) olvashatóvá teszi a dokumentumot.

---

## 3. lépés: Word dokumentum betöltése a konfigurált figyelmeztető visszahívással

Most mindent összekapcsolunk: létrehozzuk a `LoadOptions`-t, beillesztjük a `FontSettings`-et és a `FontWarningHandler`-t, majd végül betöltjük a dokumentumot.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Miért fontos** – A `LoadOptions` az egyetlen hely, ahol beállíthatod, *hogyan* olvasd be a dokumentumot. A betűtípus konfiguráció és a figyelmeztető visszahívás megadásával biztosítjuk, hogy minden hiányzó betűtípust a megfelelő helyeken keresse meg **és** azonnal jelentse.

---

## 4. lépés: Az eredmény ellenőrzése – mit kell látnod?

Futtasd a programot a konzolból. Ha a `input.docx` olyan betűtípust használ, amely nincs telepítve, és nem is található a `C:\SharedFonts` mappában, akkor valami ilyesmit látsz:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Ha minden betűtípus elérhető, a figyelmeztető sor egyszerűen nem jelenik meg. Ez a valós idejű visszajelzés felbecsülhetetlen értékű az automatizált dokumentumfeldolgozó csővezetékekben, ahol a csendes betűtípuscsere sértheti a márka irányelveit.

---

## 5. lépés: Gyakori buktatók és legjobb gyakorlatok tippek

| Buktató | Hogyan kerüld el |
|---------|-----------------|
| **Elfelejtetted hivatkozni a `Aspose.Words.Fonts`-ra** | Győződj meg róla, hogy a fájl tetején van `using Aspose.Words.Fonts;`; különben a fordító hiányzó típusokra panaszkodik. |
| **A betűtípus mappa útvonala hibás** | Ellenőrizd újra az útvonalat, és állítsd be a `recursive: true` értéket, ha almappák vannak. Használd a `Path.GetFullPath`-t a hibakereséshez. |
| **Több figyelmeztető visszahívás** | Az Aspose.Words csak az utolsó hozzárendelt `WarningCallback`-et veszi figyelembe. Tarts egyetlen kezelőt, amely delegál, ha összetettebb logikára van szükség. |
| **Futtatás UI nélküli szerveren** | A konzolra írás rendben van, de webalkalmazások esetén érdemes lehet fájlba vagy felügyeleti rendszerbe naplózni a `Console.WriteLine` helyett. |
| **Nagy dokumentumok teljesítménycsökkenést okoznak** | Használd újra ugyanazt a `FontSettings` példányt több betöltésnél; az ismételt létrehozás költséges lehet. |

**Pro tipp:** Ha a figyelmeztetéseket későbbi elemzéshez szeretnéd *összegyűjteni*, tárold őket egy `List<string>`-ben a kezelőben a közvetlen kiírás helyett.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Ezután a dokumentum betöltése után ellenőrizheted a `handler.Messages`-t.

---

## 6. lépés: A megoldás kiterjesztése – mi van, ha be kell ágyazni egy tartalék betűtípust?

Néha azt szeretnéd, hogy a hiányzó betűtípus *be legyen ágyazva* a kimeneti PDF-be, hogy az azt követő megjelenítők pontosan lássák a megjelenést. A dokumentum betöltése után kényszerítheted a beágyazást:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Ez a kódrészlet bemutatja, hogyan lehet a **betűtípus beállítások konfigurálása** megközelítést a betöltésen túl is kiterjeszteni.

---

## Teljes futtatható példa

Az alábbiakban a teljes program található, amelyet beilleszthetsz egy új Console App projektbe. Tartalmazza a fent tárgyalt összes részt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Várható kimenet** (ha hiányzó betűtípus van):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Ha nem történik helyettesítés, csak a sikerüzenetek jelennek meg.

---

## Összegzés

Most **létrehoztunk egy figyelmeztető visszahívást**, amely megbízhatóan **észleli a hiányzó betűtípusokat** a **Word dokumentum betöltése** közben az Aspose.Words használatával, és bemutattuk, hogyan **konfigurálhatod a betűtípus beállításokat**, hogy irányítsd, hol keresse a könyvtár a betűtípusokat és melyik tartalékot használja. A `FontSettings` és a `LoadOptions` összekapcsolásával teljes áttekintést kapsz a betűtípusokkal kapcsolatos problémákról – többé nem lesznek csendes elrendezési hibák.

Következő lépések? Próbáld megcserélni a `FontWarningHandler`-t egy adatbázisba író naplózóval, vagy kísérletezz **betűtípus helyettesítési szabályokkal**, hogy a konkrét hiányzó betűtípusokat márka‑jóváhagyott alternatívákra térképezd. Emellett felfedezheted a **dinamikus betűtípus betöltést** felhő tárolóból, ha az alkalmazásod konténerizált környezetben fut.

Van kérdésed egy adott széljeggyel kapcsolatban – például OpenType funkciók kezelése vagy titkosított DOCX fájlok kezelése? Hagyj egy megjegyzést alább, és jó kódolást!  

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}