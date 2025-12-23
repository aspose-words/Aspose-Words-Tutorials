---
category: general
date: 2025-12-23
description: Tanulja meg, hogyan állítsa helyre a sérült docx fájlokat, használja
  a helyreállítási módot, exportálja az egyenleteket LaTeX‑be, és generáljon egyedi
  képfájl‑neveket C#‑ban. Lépésről‑lépésre kód magyarázatokkal.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: hu
og_description: Helyreállítsa a sérült docx fájlokat, használja a helyreállítási módot,
  exportálja az egyenleteket LaTeX‑be, és generáljon egyedi képneveket az Aspose.Words
  segítségével C#‑ban.
og_title: Korrupt docx helyreállítása – Teljes C# oktató
tags:
- Aspose.Words
- C#
- Document Recovery
title: Sérült docx helyreállítása – Teljes útmutató a javításhoz, a matematikai képletek
  LaTeX-be exportálásához és egyedi képfájl-nevek generálásához
url: /hu/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sérült docx helyreállítása – Teljes útmutató a javításhoz, a matematikai egyenletek LaTeX-be exportálásához és egyedi képfájlnevek generálásához

Már előfordult, hogy megnyitott egy **.docx** fájlt, amely nem tölt be, mert sérült? Nem vagy egyedül. Sok valós projektben egy hibás Word fájl leállíthatja az egész munkafolyamatot, de a jó hír, hogy programozottan **recover corrupted docx** fájlokat helyreállíthat.

Ebben az útmutatóban végigvezetünk a pontos lépéseken, hogy **recover corrupted docx**, bemutassuk, **how to use recovery mode**, demonstráljuk a **export equations to LaTeX** funkciót, és végül **generate unique image names** a Markdown mentésekor. A végére egyetlen, futtatható C# programod lesz, amely minden feladatot hibamentesen elvégez.

## Előfeltételek

- .NET 6 vagy újabb (a kód .NET Framework 4.6+‑vel is működik).  
- Aspose.Words for .NET (ingyenes próba vagy licencelt verzió). Telepítés NuGet‑en keresztül:

```bash
dotnet add package Aspose.Words
```

- Alapvető ismeretek C#‑ban és fájl‑I/O‑ban.  
- Egy sérült `corrupt.docx` fájl a teszteléshez (a sérülést egy érvényes fájl csonkításával szimulálhatod).

> **Pro tipp:** Ments egy biztonsági másolatot az eredeti fájlról, mielőtt elkezdenéd— a helyreállítás csak akkor destruktív, ha felülírod a forrást.

## 1. lépés – A sérült DOCX helyreállítása Recovery Mode használatával

Az első dolog, amit tennünk kell, hogy az Aspose.Words‑nak jelezzük, hogy a bejövő fájlt potenciálisan sérültnek tekintse. Itt jön képbe a **how to use recovery mode**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Miért fontos:**  
Ha a `RecoveryMode.Recover engedélyezve van, az Aspose.Words megpróbálja újraépíteni a belső dokumentumfát, kihagyva a nem olvasható részeket, miközben a lehető legtöbb tartalmat megőrzi. Enélkül a `Document` konstruktor kivételt dobna, és elveszítenéd a lehetőséget a fájl megmentésére.

> **Mi van, ha a fájl javíthatatlan?**  
> A könyvtár továbbra is visszaad egy `Document` objektumot, de egyes csomópontok hiányozhatnak. Megvizsgálhatod a `doc.GetChildNodes(NodeType.Any, true).Count` értékét, hogy lásd, hány elem maradt meg.

## 2. lépés – Office Math egyenletek exportálása LaTeX-be Markdown mentésekor

Sok technikai dokumentum tartalmaz Office Math‑al írt egyenleteket. Ha ezeket az egyenleteket LaTeX‑ben szeretnéd (például egy tudományos blogon való közzétételhez), kérheted az Aspose.Words‑t, hogy elvégezze a konverziót.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Hogyan működik:**  
`OfficeMathExportMode.LaTeX` azt mondja a mentőnek, hogy minden `OfficeMath` csomópontot cseréljen le a LaTeX reprezentációjára, amely `$…$` (inline) vagy `$$…$$` (display) környezetbe van ágyazva. A kapott Markdown fájl közvetlenül felhasználható statikus weboldalkészítőknek, mint a Hugo vagy a Jekyll.

> **Különleges eset:** Ha az eredeti dokumentum komplex egyenletobjektumokat tartalmaz (pl. mátrixok), a LaTeX konverzió több soros kimenetet generálhat. Ellenőrizd a létrehozott `.md` fájlt, hogy megfelel-e a formázási elvárásaidnak.

## 3. lépés – Dokumentum mentése PDF‑ként, miközben a lebegő alakzatok címkéit szabályozzuk

Néha szükség van ugyanannak a dokumentumnak PDF‑változatára, de fontos, hogy a lebegő alakzatok (képek, szövegdobozok) hogyan legyenek címkézve az akadálymentesség érdekében. Az `ExportFloatingShapesAsInlineTag` jelző ezt a kontrollt biztosítja.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Miért kapcsoljuk ezt a jelzőt?**  
- `true` → A lebegő alakzatok `<Figure>` címkévé válnak, amelyet sok képernyőolvasó különálló képként felirattal kezel.  
- `false` → Az alakzatok általános `<Div>` címkékbe kerülnek, amelyeket az asszisztív technológiák esetleg figyelmen kívül hagynak. Válaszd a hozzáférhetőségi igényeidnek megfelelően.

## 4. lépés – Exportálás Markdown‑ba egyedi képfeldolgozással (egyedi képfájlnevek generálása)

Amikor egy Word dokumentumot Markdown‑ba mentünk, az összes beágyazott kép a lemezre íródik. Alapértelmezés szerint az eredeti fájlnevet kapják, ami ütközéseket okozhat, ha sok dokumentumot dolgozol fel ugyanabban a mappában. Kapcsoljuk be a mentési folyamatba, és **generate unique image names** automatikusan.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Mi történik a háttérben?**  
A `ResourceSavingCallback` minden külső erőforrás (képek, SVG‑k stb.) mentésekor meghívásra kerül. Ha egy teljes elérési utat adsz vissza, meghatározod, hová kerül a fájl és milyen néven. A GUID biztosítja a **generate unique image names**-t manuális nyilvántartás nélkül.

> **Tipp:** Ha determinisztikus elnevezési sémára van szükséged (pl. a kép alt szövegén alapulva), cseréld le a `Guid.NewGuid()`-t a `resourceInfo.Name` hash‑ére.

## Teljes működő példa

Mindent összerakva, itt a teljes program, amelyet beilleszthetsz egy konzolalkalmazásba:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Várt kimenet

A program futtatása hasonló konzolüzeneteket kell, hogy eredményezzen:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Három fájlt találsz majd:

| Fájl | Cél |
|------|---------|
| `out.md` | Markdown, ahol minden Office Math egyenlet LaTeX‑ként jelenik meg (`$…$` vagy `$$…$$`). |
| `out.pdf` | PDF változat lebegő alakzatok `<Figure>` címkével a jobb hozzáférhetőségért. |
| `out2.md` + `md_images\*` | Markdown plus egy mappa egyedi névvel ellátott képfájlokkal (GUID‑alapú). |

## Gyakran Ismételt Kérdések és Különleges Esetek

| Kérdés | Válasz |
|----------|--------|
| **Mi van, ha a sérült fájl nem tartalmaz helyreállítható tartalmat?** | Az Aspose.Words továbbra is visszaad egy `Document` objektumot, de lehet, hogy üres. Ellenőrizd a `doc.GetChildNodes(NodeType.Paragraph, true).Count` értéket, mielőtt folytatnád. |
| **Módosíthatom a LaTeX határolót?** | Igen—állítsd be a `markdownMathOptions.MathDelimiter = "$$"` értéket, hogy kényszerítsd a display‑stílusú határolókat. |
| **Szükséges-e felszabadítani a `Document` objektumot?** | A `Document` osztály implementálja az `IDisposable` interfészt. Csomagold `using` blokkba, ha sok fájlt dolgozol fel, hogy a natív erőforrások gyorsan felszabaduljanak. |
| **Hogyan őrizhetem meg az eredeti képfájlneveket?** | A visszatérési értékként `Path.Combine(imageFolder, resourceInfo.Name)`-t adj a callbackben. Csak ne feledd a névütközések kockázatát. |
| **Biztonságos-e a GUID megközelítés verziókezelésű repókban?** | A GUID-ok futásról futásra stabilak, de nem emberi olvasásra alkalmasak. Ha reprodukálható nevekre van szükséged, hash-eld az eredeti nevet egy projekt‑széles sóval. |

## Összegzés

Megmutattuk, hogyan **recover corrupted docx** fájlokat helyreállíthatod, bemutattuk, hogyan **how to use

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}