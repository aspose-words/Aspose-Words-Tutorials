---
category: general
date: 2026-02-18
description: Készíts markdownot a dokumentumból egyszerű lépésekkel, exportáld a dokumentumot
  markdown formátumba, és mentsd a képeket egy almappába. Tanulja meg, hogyan mentse
  a dokumentumot markdownként C#‑ban.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: hu
og_description: Készíts markdownot dokumentumból C#‑ban, és tanuld meg, hogyan exportálj
  dokumentumot markdown formátumba, miközben a képeket egy almappába mented. Kövesd
  a lépésről‑lépésre útmutatót.
og_title: Markdown készítése dokumentumból – Képek exportálása és mentése
tags:
- C#
- Aspose.Words
- Markdown export
title: Markdown létrehozása dokumentumból – Képek exportálása és mentése
url: /hu/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Markdown létrehozása dokumentumból – Exportálás és képek mentése

Valaha is szükséged volt **markdown létrehozására dokumentumból**, de nem tudtad, hogyan tartsd rendben a beágyazott képeket? Nem vagy egyedül. Sok projektben programozottan generálunk jelentéseket, kézikönyveket vagy blogvázlatokat, és az utolsó dolog, amit szeretnénk, egy káosznyi képfájl a kimeneti mappában.

Ebben a tutorialban végigvezetünk egy teljes, azonnal futtatható megoldáson, amely **exportálja a dokumentumot markdown formátumba**, minden képet egy dedikált *md‑resources* almappába helyez, és végül **elmenti a dokumentumot markdownként** az Aspose.Words for .NET API segítségével. A végére egyetlen metódust kapsz, amelyet bármely C# kódbázisba beilleszthetsz, valamint néhány tippet a szélsőséges esetek kezelésére.

> **Gyors áttekintés:**  
> • `MarkdownSaveOptions` beállítása  
> • `IResourceSavingCallback` megadása, amely a képeket egy almappába irányítja  
> • `Document.Save` meghívása a konfigurált beállításokkal  

Ha kíváncsi vagy, miért választunk visszahívást a post‑processzing helyett, olvass tovább – a magyarázat lépésről lépésre van kifejtve.

---

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑vel is működik)  
- Aspose.Words for .NET (NuGet csomag `Aspose.Words`)  
- Egy forrás `Document` objektum (lehet .docx, .pdf, .rtf, stb.)  

További könyvtárak nem szükségesek; a visszahívás API beépített az Aspose.Words‑be.

---

## 1. lépés: Markdown létrehozása dokumentumból – mentési beállítások konfigurálása

Az első dolog, amit teszünk, hogy példányosítjuk a `MarkdownSaveOptions`‑t. Ez az objektum megmondja az Aspose.Words‑nek, hogyan viselkedjen a konverzió, például melyik Markdown változatot használja, beágyazza-e a képeket Base64‑ként, és hová helyezze a generált fájlokat.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Miért fontos:**  
> Ha nem hozunk létre explicit `MarkdownSaveOptions`‑t, a könyvtár az alapértelmezett beállításokra támaszkodik, amelyek a képeket közvetlenül a Markdown fájlba ágyazzák Base64‑karakterláncként. Ez hatalmas fájlt eredményez, és aláássa a tiszta *images* mappa célját.

---

## 2. lépés: Dokumentum exportálása markdownba és erőforráskezelés definiálása

Most megmondjuk a mentőnek, **hova** helyezze az egyes képeket. Az `IResourceSavingCallback` interfész egy olyan horgot biztosít, amely minden erőforrás (kép, SVG, stb.) esetén lefut, amelyet az export során felfedez. A visszahíváson belül:

1. Ellenőrizzük, hogy a célmappa létezik-e (`md-resources/`).  
2. Beállítjuk az `OutputFileName`‑t a mappára és az eredeti erőforrás nevére.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Gyakori kérdés:** *Mi van, ha inkább be szeretném ágyazni a képeket ahelyett, hogy menteném őket?*  
> Egyszerűen hagyd ki a visszahívást, vagy állítsd be `args.OutputFileName = null;`‑t – a mentő automatikusan Base64‑ként ágyazza be a képet.

> **Szélsőséges eset:** Néhány régebbi dokumentum duplikált képfájlneveket tartalmaz. A fenti visszahívás felülírja a korábbi fájlt. Ennek elkerülésére egy GUID‑ot is hozzáfűzhetsz:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## 3. lépés: Dokumentum mentése markdownként és a mentett képek ellenőrzése

Miután a beállítások teljesen konfigurálva vannak, az utolsó hívás egy egy‑soros parancs, amely a Markdown fájlt és a kapcsolódó képeket a lemezre írja.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Ha minden rendben megy, a következőket fogod látni:

- `MyReport.md` – a forrásdokumentum Markdown ábrázolása.  
- `md-resources/` – egy mappa a .md fájl mellett, amely minden kinyert képet tartalmaz (pl. `image001.png`, `image002.jpg`).  

**Példa Markdown részlet** (az Aspose.Words által automatikusan generálva):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Pro tipp:** Nyisd meg a generált `.md` fájlt VS Code‑ban vagy bármely Markdown előnézetben; a képeknek azonnal meg kell jelenniük, mivel a relatív útvonalak egyeznek a mappaszerkezettel.

---

## Teljes, futtatható példa

Az alábbi önálló konzolprogramot beillesztheted egy új .NET projektbe, majd futtathatod. Létrehoz egy egyszerű Word dokumentumot, hozzáad egy képet, és **markdownot hoz létre a dokumentumból**, miközben a képet egy almappába menti.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**A futtatás után a következőket kell látnod**:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Nyisd meg az `ExportedDoc.md`‑t – a kép hivatkozása a `md-resources/sample-image.png`‑re mutat, és a kép helyesen jelenik meg bármely Markdown nézőben.

---

## Gyakran előforduló változatok

| Szenárió | Hogyan kell módosítani a kódot |
|----------|-------------------------------|
| **Kép exportálásának kihagyása** (beágyazás Base64‑ként) | Egyszerűen hagyd el a `ResourceSavingCallback`‑et, vagy állítsd be `args.OutputFileName = null;`‑t a visszahíváson belül. |
| **Képek formátumának megváltoztatása** (pl. minden PNG) | A visszahíváson belül módosítsd `args.ResourceFileName`‑t, és opcionálisan konvertáld a streamet írás előtt. |
| **Egyedi mappanév** | Cseréld le a `"md-resources/"`‑t bármely relatív vagy abszolút útvonalra, amelyet szeretnél. |
| **Több dokumentum batch‑feldolgozása** | Iterálj egy `Document` objektumok gyűjteményén, újrahasználva ugyanazt a `MarkdownSaveOptions` példányt (csak győződj meg róla, hogy a mappa tisztítva van vagy egyedi névvel rendelkezik minden futtatásnál). |

---

## Összegzés

Most már tudod, **hogyan kell markdownot létrehozni dokumentumból**, **hogyan exportálni a dokumentumot markdownba**, és **hogyan menteni a képeket almappába** egy tiszta, visszahíváson alapuló megközelítéssel. A fő tanulságok:

- Használd a `MarkdownSaveOptions`‑t a finomhangolt export vezérléséhez.  
- Implementáld az `IResourceSavingCallback`‑t, hogy a képeket egy dedikált mappába irányítsd, így a Markdownod rendezett marad.  
- Ugyanez a minta más erőforrás típusokra is működik (SVG, audio) – csak ellenőrizd a `args.ResourceType`‑t.  

Ezután felfedezheted a **markdown mentését egyedi címsorstílusokkal**, vagy integrálhatod ezt a rutinot egy ASP.NET Web API‑ba, amely ZIP‑ben adja vissza a `.md` fájlt és annak erőforrásait. Akárhogy is, az építőelemek most már a szerszámtáradban vannak.

Van kérdésed, vagy találtál egy olyan széljegyet, amit nem fedtünk le? Írj egy megjegyzést alul, és jó kódolást!

---

![markdown létrehozása dokumentumból példa](placeholder.png "markdown létrehozása dokumentumból példa")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}