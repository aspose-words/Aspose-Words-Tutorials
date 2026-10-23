---
category: general
date: 2026-10-23
description: Tanulja meg, hogyan szúrjon be ellipszist, és hogyan adjon hozzá téglalap
  alakzatot a Wordben az Aspose.Words használatával. Tartalmazza a kurzor áthelyezését
  az alakzatra, valamint a csoport alakzat létrehozásának módját.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: hu
lastmod: 2026-10-23
og_description: Hogyan szúrjunk be ellipszist és hogyan adjunk hozzá téglalap alakzatot
  a Wordben az Aspose.Words segítségével. Kövesse a lépésről‑lépésre útmutatót a kurzor
  alakzatra mozgatásához és csoportos alakzat létrehozásához.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Hogyan szúrjunk be ellipszis és téglalap alakzatokat egy Word csoport alakzatba
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan lehet ellipszis és téglalap alakzatokat beszúrni egy csoport alakzatba
  az Aspose.Words segítségével
url: /hu/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be ellipszis és téglalap alakzatokat egy csoport alakzatba az Aspose.Words segítségével

Ha szeretnéd megtudni, **hogyan szúrj be ellipszist** egy Word dokumentumba programozottan, ez az útmutató a teljes folyamatot mutatja be. Emellett láthatod, **hogyan adj hozzá téglalap** alakzatot, megtanulod, **hogyan mozdítsd a kurzort az alakzatra**, és felfedezed, **hogyan hozhatsz létre csoport alakzatot**, amely több rajzobjektumot tartalmaz.

A Word automatizálás gyakran pontos rajzobjektum-pozicionálást igényel. A tutorial végére képes leszel egy `.docx` fájlt generálni, amely egy csoportosított téglalapot és ellipszist tartalmaz, készen áll további stílusozásra vagy exportálásra. Nem szükséges külső eszköz, csak az Aspose.Words for .NET könyvtár és egy .NET fejlesztői környezet.

## Előfeltételek

* .NET 6.0 vagy újabb telepítve.
* Aspose.Words for .NET (NuGet csomag `Aspose.Words`) hozzáadva a projekthez.
* Alapvető C# szintaxis és Visual Studio (vagy bármely IDE) ismerete.

Ezek a követelmények biztosítják, hogy a kód további konfiguráció nélkül leforduljon.

## Hogyan hozzunk létre csoport alakzatot Wordben

A csoport alakzat egy tárolóként működik, amely lehetővé teszi több alakzat mozgatását, forgatását vagy formázását egy egységként. Az alábbi kód egy adott méretű (300 × 200 pont) csoportot hoz létre, és előkészíti a dokumentumot a további rajzolási műveletekhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Miért fontos ez a lépés*: A csoport alakzat egy helyi koordináta rendszert definiál. Az összes, a kurzor csoportba mozgatása után hozzáadott alakzat a csoport eredetéhez képest lesz elhelyezve, ami egyszerűvé teszi a elrendezés számításait.

## Hogyan adjunk hozzá téglalap alakzatot Wordben

Most, hogy a csoport létezik, **beszúrhatod a téglalap alakzatot** bele. A téglalap háttérként vagy vizuális helykitöltőként szolgálhat a többi tartalom számára.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Magyarázat*: A `MoveTo(group)` azt mondja a buildernek, hogy az aktív beszúrási pont a csoport alakzat. A kurzor mozgatása nélkül az `InsertShape` a téglalapot a fő dokumentumtörzsbe helyezné a csoport helyett.

## Hogyan szúrj be ellipszist

A téglalap elhelyezése után most bemutathatod, **hogyan szúrj be ellipszist**. Az ellipszis a ugyanabban a csoportban lesz középre helyezve, szükség esetén átfedve a téglalapot.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Miért kell a kurzort mozgatni*: Az `InsertShape` minden hívása a jelenlegi kurzorpozíciót veszi figyelembe. A `MoveTo(group)` újbóli meghívása garantálja, hogy az ellipszis is a csoport gyermekeként kerül be, megőrizve a kívánt hierarchiát.

## Mozgasd a kurzort az alakzatra további objektumok beszúrása előtt

Ha később további alakzatokat szeretnél hozzáadni, mindig **mozdítsd a kurzort az alakzatra** minden egyes beszúrás előtt. Ez a minta elkerüli a véletlen elhelyezést a csoporton kívül.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tipp*: A `MoveTo(group)` újrafelhasználása olcsó és javítja a kód olvashatóságát. Emellett megkönnyíti a jövőbeni karbantartást, mivel a beszúrási kontextus egyértelmű.

## Dokumentum mentése

Végül, mentsd a dokumentumot a lemezre. A példa a fájlt `GroupShape.docx` néven menti egy általad megadott mappába.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Amikor megnyitod a mentett fájlt a Microsoft Wordben, egyetlen csoportot látsz, amely egy téglalapot és egy ellipszist tartalmaz, mindkettő helyesen pozícionálva.

### Várt kimenet

* Egy `GroupShape.docx` nevű `.docx` fájl.
* A dokumentumon belül egy csoportosított rajzobjektum, mérete 300 × 200 pont.
* A csoporton belül:
  * Egy téglalap (100 × 50 pont), a csoport eredeténél elhelyezve.
  * Egy ellipszis (80 × 80 pont), átfedve a téglalapot.
  * Bármely további alakzat, amelyet a kurzor mozgatása után adtál hozzá.

## Gyakori variációk és szélsőséges esetek

| Situation | Recommended approach |
|-----------|----------------------|
| **Különböző egységméretek** | Az Aspose.Words pontokat használ (1 pt = 1/72 in). A `InsertShape` hívása előtt konvertáld a centimétereket vagy hüvelyket pontokra. |
| **Alakzatok forgatása a csoporton belül** | Az alakzat beszúrása után szerezd meg a `ShapeBase` objektumát, és állítsd be a `ShapeBase.RotationAngle` értékét. |
| **Szöveg hozzáadása egy alakzaton belül** | Használd a `ShapeBase.AppendChild(new Paragraph(document))` metódust, majd adj hozzá egy `Run`-t a kívánt szöveggel. |
| **Mentés PDF-be a DOCX helyett** | Hívd meg a `document.Save("GroupShape.pdf", SaveFormat.Pdf);` - a csoport hierarchia megmarad a PDF kimenetben. |

Ezek a variációk azt mutatják, hogy ugyanaz a **hogyan szúrj be ellipszist** logika számos valós helyzethez adaptálható.

## Profi tippek

* **Használd ugyanazt a `DocumentBuilder` példányt** – csökkenti a memóriahasználatot és a dokumentum állapotát konzisztenssé teszi.
* **Ellenőrizd az alakzat méreteit** – rendkívül nagy szélességek vagy magasságok megjelenítési problémákat okozhatnak a régebbi Word verziókban.
* **Csoportosíts a stílusozás előtt** – a kitöltőszínek vagy vonalstílusok a csoporton alkalmazása, miután minden gyermek hozzá lett adva, egységes megjelenést biztosít.

## Következtetés

Most már érted, **hogyan szúrj be ellipszist** és **hogyan adj hozzá téglalap** alakzatot egy csoportosított tárolóba egy Word dokumentumban az Aspose.Words használatával. Azáltal, hogy következetesen **mozdítod a kurzort az alakzatra** minden egyes beszúrás előtt, tiszta hierarchiát tartasz fenn és elkerülöd a véletlen elhelyezést. A teljes példa lefordul, fut, és egy csoportosított alakzatot hoz létre, amely tovább testreszabható vagy exportálható.

Készen állsz a további felfedezésre? Próbáld meg kombinálni ezt a technikát a **hogyan hozhatsz létre csoport alakzatot** segítségével összetett diagramokhoz, vagy kísérletezz a **beszúr téglalap alakzat Wordben** szövegdobozokkal együtt a gazdag jelentéskészítéshez. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre téglalap alakzatot és csoport alakzatokat Wordben az Aspose.Words segítségével](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Hogyan hozzunk létre üres Word dokumentumot és adjunk hozzá rejtett ellipszis alakzatot C#-ban](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Hogyan hozzunk létre csoport alakzatot docx-ben és adjunk hozzá interaktív vezérlőket C#-ban](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}