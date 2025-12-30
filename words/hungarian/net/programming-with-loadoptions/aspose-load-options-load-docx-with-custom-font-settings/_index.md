---
category: general
date: 2025-12-29
description: Az Aspose betöltési beállítások lehetővé teszik a DOCX fájlok betöltését,
  miközben testreszabhatja a betűtípus-beállításokat és felderítheti a hiányzó betűtípusokat.
  Ismerje meg, hogyan tölthet be docx fájlokat teljes irányítással.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: hu
og_description: Az Aspose Load Options lehetővé teszi, hogy DOCX fájlokat töltsön
  be, miközben testreszabja a betűtípus-beállításokat és észleli a hiányzó betűtípusokat.
  Ismerje meg, hogyan tölthet be docx fájlokat teljes irányítással.
og_title: Aspose betöltési beállítások – DOCX betöltése egyedi betűtípus-beállításokkal
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose betöltési beállítások – DOCX betöltése egyéni betűtípus-beállításokkal
url: /hu/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – DOCX betöltése egyedi betűtípus‑beállításokkal

Gondolkodtál már azon, hogyan lehet egy DOCX fált betölteni C#‑ban anélkül, hogy hiányzó betűtípusokba ütköznél? Nem vagy egyedül. **Aspose Load Options** lehetővé teszi, hogy pontosan szabályozd, hogyan nyílik meg egy Word‑dokumentum, egyedi betűtípus‑beállításokat állíts be, és még a hiányzó betűtípusokat is észleld, mielőtt problémává válnának.

Ebben az útmutatóban végigvezetünk a teljes folyamaton: egy DOCX betöltése az Aspose.Words segítségével, **egyedi betűtípus‑beállítások** konfigurálása, valamint egy figyelmeztető visszahívás (warning callback) beállítása, amely megmondja, mely betűtípusok hiányoznak. A végére képes leszel **word document** fájlokat magabiztosan betölteni, függetlenül attól, hogy az eredeti szerző milyen betűtípusokat használt.

> **Prerequisite** – Szükséged van az Aspose.Words for .NET (legújabb verzió) hivatkozására a projektedben, valamint alapvető C# ismeretekre. Más könyvtárak nem szükségesek.

## Mit fogsz megtanulni

- Hogyan hozhatsz létre egy `LoadOptions` objektumot és csatolj egy figyelmeztető visszahívást.  
- Hogyan állíthatod be a `FontSettings`‑et **egyedi betűtípus‑beállítások** számára.  
- Hogyan **load docx**‑et valósíts meg, és ellenőrizd, hogy a hiányzó betűtípusok jelentésre kerülnek-e.  
- Tippek a szélsőséges esetek kezelésére, például beágyazott betűtípusok vagy hálózati alapú betűtípus‑mappák esetén.

## 1. lépés: Aspose.Words telepítése és a projekt előkészítése

Először is győződj meg róla, hogy az Aspose.Words telepítve van. A legegyszerűbb mód a NuGet használata:

```bash
dotnet add package Aspose.Words
```

Miután a csomag hozzá lett adva, hozz létre egy új C# konzolprojektet (vagy illeszd be a kódot bármely meglévő alkalmazásba). A kód .NET 6+ és .NET Framework 4.7.2+ környezetben egyaránt működik, így mindkét esetben fedett vagy.

> **Pro tip:** Ha .NET Core‑ra célozol, add hozzá a `using System;` sort a fájl tetejéhez; az IDE általában automatikusan beilleszti.

## 2. lépés: Aspose Load Options konfigurálása figyelmeztető visszahívással

Most jön a lényeg – **aspose load options**. A `LoadOptions` osztály lehetővé teszi, hogy finomhangold a dokumentum elemzését. Ezt fogjuk használni:

1. Egy visszahívás csatolására, amely akkor aktiválódik, amikor a betöltő nem találja a kért betűtípust.  
2. Egy `FontSettings` példány hozzárendelésére, amely később **egyedi betűtípus‑beállítások** módosítására szolgál.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Miért fontos:** Figyelmeztető visszahívás nélkül az Aspose csendben helyettesíti a hiányzó betűtípusokat, ami később elrendezési meglepetéseket okozhat. A visszahívásba ágyazva **korán észlelheted a hiányzó betűtípusokat**, és eldöntheted, hogy beágyazol egy helyettesítőt vagy a felhasználót a hiányzó betűtípus telepítésére kérdezed.

## 3. lépés: A DOCX betöltése a konfigurált beállításokkal

Miután a `LoadOptions` készen áll, a DOCX betöltése egyetlen sorban megoldható. A `Document` konstruktor elfogadja a fájl elérési útját és a korábban épített opciókat.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Ha a forrásfájl olyan betűtípust hivatkozik, amely nincs a rendszerben vagy az egyedi mappában, a kimenet ilyesmi lesz:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Ez a azonnali visszajelzés felbecsülhetetlen értékű, ha egy olyan kötegelt feldolgozó csővezetéket építesz, amelynek vizuális hűség garantálása a cél.

## 4. lépés: A betöltött dokumentum ellenőrzése (opcionális, de hasznos)

Betöltés után érdemes megerősíteni, hogy a dokumentum tartalma elérhető-e. Egy gyors sanity‑checkhez írjuk ki az első bekezdés szövegét.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

A program futtatása most a következőt adja:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## 5. lépés: Szélsőséges esetek és haladó tippek

### 5.1 Beágyazott betűtípusok kezelése

Néhány DOCX fájl közvetlenül beágyazza a szükséges betűtípusokat. Az Aspose.Words automatikusan ezeket használja, így nem kapsz róluk figyelmeztetést. Azonban ha szándékosan **load word document** fájlokat töltesz be, amelyek eltávolítják a beágyazott betűtípusokat (például egy konverzió után), akkor a hiányzó bettípusokat a korábban bemutatott `SetFontsFolder`‑rel kell megadni.

### 5.2 Memory Stream használata fájlútvonal helyett

Ha a DOCX adatbázisban vagy HTTP‑kérésből érkezik, betöltheted egy `MemoryStream`‑ből:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Ugyanazok a **aspose load options** érvényesek, és a figyelmeztető visszahívás továbbra is működik.

### 5.3 Betűtípus‑helyettesítés globális felülírása

Ha inkább egy konkrét helyettesítő betűtípust (például Arial) szeretnél használni a hiányzóak helyett, hozzáadhatsz egy helyettesítési szabályt:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Ezt kombinálhatod a figyelmeztető visszahívással, hogy naplózd a helyettesítési eseményt és konzisztens maradjon a kimenet.

## 6. lépés: Teljes, működő példa

Az alábbi program teljes, másolás‑beillesztés‑kész megoldást mutat, amely tartalmazza az összes előző lépést. Mentsd `Program.cs`‑ként, állítsd vissza a NuGet csomagokat, és futtasd.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Várt kimenet

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Ha nincs hiányzó betűtípus, a figyelmeztető sorok egyszerűen nem jelennek meg.

## Vizuális áttekintés

![aspose load options example](/images/aspose-load-options.png "Diagram showing Aspose Load Options workflow")

*Az ábra azt mutatja, hogyan helyezkednek el a **Aspose Load Options** a fájlforrás és a `Document` objektum között, kezelve a betűtípus‑feloldást és a hiányzó betűtípusok észlelését.*

## Összegzés

Végigvezettünk egy komplett megoldáson a **aspose load options** használatával, megmutatva, hogyan **load docx**‑et úgy, hogy **custom font settings**‑et alkalmazz és **detect missing fonts**‑t hajts végre. Egy figyelmeztető visszahívás konfigurálásával és opcionálisan egy egyedi betűtípus‑mappa megadásával teljes láthatóságot kapsz a betűtípus‑problémákra, mielőtt azok a renderelést befolyásolnák.

Innen tovább felfedezheted a kapcsolódó témákat, például a **load word document** konvertálását PDF‑re, vízjelek hozzáadását, vagy több tucat fájl kötegelt feldolgozását egy mappában. Ugyanaz a minta – `LoadOptions` létrehozása, visszahívások csatolása, majd `new Document(...)` hívása – az egész Aspose.Words API‑ban működik.

Van kérdésed egy konkrét szélsőséges esettel kapcsolatban, például jobbra‑balra nyelvek vagy titkosított DOCX fájlok kezelése? Hagyd meg a kommentet, vagy nézd meg az Aspose.Words dokumentációt a mélyebb részletekért. Boldog kódolást, és legyenek a dokumentumaid mindig úgy megjelenítve, ahogy elvárod!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}