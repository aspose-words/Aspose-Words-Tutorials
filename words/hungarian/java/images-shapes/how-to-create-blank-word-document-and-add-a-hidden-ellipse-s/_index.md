---
category: general
date: 2026-09-21
description: Hozzon létre egy üres Word-dokumentumot egy rejtett ellipszissel C#-ban.
  Tanulja meg, hogyan lehet elrejteni a formát a Wordben, és hogyan generáljon programozottan
  rejtett alakzatot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: hu
lastmod: 2026-09-21
og_description: Hozzon létre üres Word-dokumentumot egy rejtett ellipszissel C#-ban.
  Ez az útmutató bemutatja, hogyan lehet elrejteni egy alakzatot a Wordben, és hogyan
  lehet programozottan rejtett alakzatokat létrehozni.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Üres Word-dokumentum létrehozása rejtett ellipszis alakzattal C#-ban
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan hozzunk létre üres Word-dokumentumot, és adjunk hozzá egy rejtett ellipszis
  alakzatot C#-ban
url: /hu/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre üres Word dokumentumot és adjunk hozzá egy rejtett ellipszis alakzatot C#‑ban

Ha **üres Word dokumentumot** kell létrehoznod, amely egy láthatatlan grafikát tartalmaz, ez az útmutató pontosan megmutatja, hogyan. A tutorial végére egy .docx fájlt kapsz, amely látszólag üres, de valójában egy ellipszis alakzatot tárol, amely rejtve van a megjelenítésben.

Az Aspose.Words for .NET-et fogjuk használni a dokumentum felépítéséhez, az ellipszis beszúrásához, elrejtéséhez és a fájl mentéséhez. A lépések bemutatják, hogyan **hozzunk létre ellipszis** objektumokat, a **helyes módját a shape elrejtésének Word‑ben**, valamint hogyan **hozzunk létre rejtett shape** kódot, amely bármely .NET projektben működik.

## Prerequisites

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel:

* .NET 6.0 SDK vagy újabb verzió telepítve  
* Visual Studio 2022 (vagy bármely C# szerkesztő)  
* Aspose.Words for .NET licenccel vagy egy ingyenes értékelő példánnyal  
* Alapvető C# szintaxis ismeretekkel  

Nem szükséges további NuGet csomag a `Aspose.Words`‑en kívül.

## Create blank Word document with Aspose.Words

Az első lépés egy üres Word fájl generálása. Ez egy tiszta vászon, ahová később elrejthető grafikákat szúrhatunk be.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Miért kezdünk egy üres dokumentummal** – Egy üres fájlból indulva garantáljuk, hogy semmilyen nem kívánt tartalom ne zavarja a rejtett alakzatot. Emellett a fájlméret minimális marad, ami akkor hasznos, amikor a dokumentumot később sablonként használjuk.

## How to create ellipse inside the blank document

Ezután szükségünk van egy `DocumentBuilder`‑re a tartalom hozzáadásához. A builder lehetővé teszi, hogy pontosan oda helyezzük a shape‑eket, ahová szeretnénk.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Magyarázat** – A `ShapeType.Ellipse` azt mondja az Aspose.Words‑nek, hogy egy köríves alakzatot rajzoljon. A szélesség és magasság pontban van megadva (1 pt ≈ 1/72 inch). Ezeket az értékeket a tervezési igényeidnek megfelelően módosíthatod.

## Hide shape in Word so it doesn’t appear in the layout

Egy rejtett shape továbbra is jelen van a dokumentum XML‑ében, ami hasznos lehet metaadatok, feltételes formázás vagy későbbi programozott módosítások esetén. A rejtéshez a `Hidden` tulajdonságot `true`‑ra állítjuk.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Miért rejtjük el az alakzatot** – A rejtett shape‑eket a layout motor figyelmen kívül hagyja, így az oldal teljesen üresnek tűnik. Az alakzat adatai azonban megmaradnak, ami hasznos lehet jelölők, könyvjelzők vagy egyedi XML tárolására, amelyet a downstream folyamatok olvashatnak.

## Save the document with the hidden shape

Végül a fájlt leírjuk a lemezre. A mentett `.docx` Microsoft Word‑ben megnyitva nem mutat semmilyen látható tartalmat, de a rejtett ellipszis továbbra is jelen van.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Ellenőrzés** – Nyisd meg a generált fájlt Word‑ben, majd nyomd meg az `Alt+F9`‑et a mezőkódok váltásához, és a `Ctrl+A` → `Ctrl+Shift+F9` kombinációt a rejtett objektumok megtekintéséhez. Látni fogod az ellipszist a dokumentum XML‑ében (`word/document.xml`), de semmit sem a lapon.

---

## Full, runnable example

Az alábbi teljes programot másold be egy új konzolos projektbe. Tartalmazza az összes `using` direktívát és a `Main` metódust, így extra keretrendszer nélkül futtatható.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Várható kimenet** – A program futtatásakor a konzol kiírja a fájl útvonalát, és a létrehozott Word fájl nem tartalmaz látható objektumokat. Ha a dokumentumot egy zip‑eszközzel (`.docx` egy zip archívum) vizsgálod, megtalálod a `<w:pict>` elemet, amely leírja az ellipszist a `word/document.xml`‑ben.

---

## Common variations and edge cases

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Másik alakzat** | Cserélje le a `ShapeType.Ellipse`‑t `ShapeType.Rectangle`, `ShapeType.Line`, stb.-re. | Lehetővé teszi más grafikák elrejtését, miközben ugyanazt a munkafolyamatot használja. |
| **Több rejtett alakzat** | Hívja meg többször az `InsertShape`‑t, és minden esetben állítsa be a `Hidden = true` értéket. | Hasznos jelölők vagy helyettesítők gyűjteményének beágyazásához. |
| **Feltételes láthatóság** | Használja a `shape.Visible = false`‑t a `shape.Hidden = true`‑val együtt extra biztonság kedvéért. | Néhány régebbi Word verzió másként kezeli a `Visible`‑t; mindkettő beállítása lefedi az összes esetet. |
| **Mentés stream‑be** | Cserélje le a `doc.Save(path)`‑t `doc.Save(stream, SaveFormat.Docx)`‑re. | Lehetővé teszi a dokumentum közvetlen HTTP‑n keresztüli küldését vagy adatbázisban való tárolását. |
| **Stílus alkalmazása** | Beszúrás után módosítsa a `ellipse.FillColor`, `ellipse.LineWeight` stb. értékeket a rejtés előtt. | Az alakzat stílusa megmarad az XML‑ben, ami későbbi visszafejtéshez hasznos lehet. |

**Pro tip:** Mindig teszteld a rejtett shape‑ot a célzott Word verzión (pl. Word 2019, Word 365), mert időnként megjelenési sajátosságok merülnek fel, amikor a rejtett objektumok összetett oldalelrendezésekkel ütköznek.

---

## Frequently asked questions

**Q: Befolyásolja a shape elrejtése a dokumentum méretét?**  
A: Az alakzat XML‑je csak néhány száz bájtot ad hozzá, ami a legtöbb esetben elhanyagolható. A fájl mérete lényegében ugyanaz marad, mint egy valóban üres dokumentumé.

**Q: Később programozottan vissza tudom-e állítani a shape láthatóságát?**  
A: Igen. Töltsd be a dokumentumot, keresd meg a shape‑t (`doc.GetChildNodes(NodeType.Shape, true)`), és állítsd be a `shape.Hidden = false` értéket.

**Q: Megjelenik a rejtett shape nyomtatáskor?**  
A: Nem. A rejtett objektumok kizárásra kerülnek a nyomtatási elrendezésből, így a nyomtatott oldal üres marad.

**Q: Ez a megközelítés csak az Office Open XML (OOXML) esetén működik?**  
A: A `Hidden` tulajdonság az OOXML specifikáció része, ezért bármely olyan Word processzor, amely teljes mértékben implementálja az OOXML‑t (Word, LibreOffice, Google Docs) tiszteletben tartja a rejtett jelzőt.

---

## Conclusion

Most már tudod, hogyan **hozz létre üres Word dokumentumot**, **hozz létre ellipszist**, **rejtett shape‑et Word‑ben**, és **rejtett shape‑et** használj az Aspose.Words for .NET‑el. A tutorial lefedte a teljes életciklust – az üres fájl inicializálásától a shape beszúrásán, elrejtésén és mentésén át – valamint az ellenőrzési lépéseket és gyakori variációkat.

A következő lépéseid lehetnek:

* Rejtett szövegdobozok hozzáadása metaadatokhoz (`hide shape in word` technika szövegre alkalmazva)  
* Egyedi XML részek használata strukturált adatok tárolására a rejtett shape‑ek mellett  
* A rejtett‑shape dokumentum PDF‑re konvertálása a rejtett elemek megőrzésével  

Kísérletezz különböző alakzatokkal és láthatósági beállításokkal, hogy megtapasztald, a rejtett tartalom hogyan szolgálhat könnyű adatbázisként a Word fájlokban.

Jó kódolást!

## What Should You Learn Next?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutató technikáira épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek az API további funkcióinak elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeidben.

- [Téglalap alakzat létrehozása Word‑ben C#‑ban – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Word dokumentum létrehozása árnyékolt téglalappal – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}