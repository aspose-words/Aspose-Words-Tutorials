---
category: general
date: 2026-11-22
description: Programozott módon Word dokumentum létrehozása C#-ban, téglalap alakzat
  beszúrása, több alakzat beszúrása, és az alakzatok Word-be írása az Aspose.Words
  segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: hu
lastmod: 2026-11-22
og_description: Programozottan hozza létre a Word dokumentumot C#-ban téglalap alakzat
  beszúrásával, több alakzat hozzáadásával, és az alakzatok Word-be írásával az Aspose.Words
  segítségével.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Programozott módon Word-dokumentum létrehozása alakzatokkal C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Programozott módon Word dokumentum létrehozása alakzatokkal C#‑ban
url: /hu/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programozottan Word dokumentum létrehozása alakzatokkal C#‑ban

Ha **programozottan Word dokumentumot** szeretnél létrehozni, amely egyedi grafikákat tartalmaz, ez az útmutató megmutatja, hogyan teheted meg az Aspose.Words for .NET segítségével. Megtanulod, hogyan illessz be egy téglalap alakzatot, adj hozzá további alakzatokat, csoportosítsd őket, és végül írd ki az alakzatokat Word‑be – mindezt néhány C#‑sorban.

A grafikákkal ellátott Word fájl létrehozása már nem igényel kézi szerkesztést vagy makró szkripteket. A tutorial végére egy újrahasználható metódust kapsz, amely egy `.docx` fájlt hoz létre, benne egy téglalappal és egy ellipszissel, amelyek együtt vannak csoportosítva, készen állnak a további feldolgozásra vagy jelentéskészítésre.

## Amire szükséged lesz

- .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑al is működik)
- Aspose.Words for .NET (NuGet csomag `Aspose.Words`)
- Egy IDE, például Visual Studio 2022 (bármely szerkesztő, amely képes C#‑t fordítani)

> **Pro tip:** A csomagot a `dotnet add package Aspose.Words` CLI parancs segítségével telepítheted, mielőtt elkezdenéd a kódolást.

## Programozottan Word dokumentum létrehozása – áttekintés

Az általános folyamat három logikai fázisból áll:

1. **Inicializálás** egy új `Document` és egy `DocumentBuilder` példány létrehozásával.  
2. **Több alakzat beillesztése** (egy téglalap és egy ellipszis) és azok elhelyezése egy `GroupShape`‑ben.  
3. **Alakzatok írása Word‑be** a `Document` `.docx` fájlba mentésével.

Minden fázist alább külön lépésben mutatunk be, így a kódot egyszerűen átmásolhatod a projektedbe.

![Programozottan Word dokumentum létrehozása csoportosított alakzatokkal](grouped-shapes.png){: .align-center alt="Programozottan Word dokumentum létrehozása csoportosított alakzatokkal"}

## 1. lépés: A dokumentum és a builder inicializálása

A `Document` osztály képviseli a teljes Word fájlt, míg a `DocumentBuilder` egy folyékony API‑t biztosít a tartalom hozzáadásához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Miért fontos:* A `Document` először történő létrehozása tiszta vásznat biztosít. A `DocumentBuilder` nyomon követi a jelenlegi beszúrási pontot, ami elengedhetetlen, amikor később alakzatokat csatolsz egy bekezdés hierarchiához.

## 2. lépés: Csoportos alakzat konténer beillesztése

A `GroupShape` lehetővé teszi, hogy több egyedi alakzatot egy egységként kezelj. Ez akkor hasznos, ha egyszerre szeretnéd őket mozgatni vagy átméretezni.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Magyarázat:* Az `InsertGroupShape` egy üres konténert illeszt be, és automatikusan a jelenlegi alakzattá teszi. Az összes későbbi alakzat beillesztése ebbe a konténerbe kerül, amíg a csoportot be nem zárod.

## Téglalap alakzat beillesztése

Most hozzáadjuk az első grafikát – egy téglalapot. Ez teljesíti a **insert rectangle shape** követelményt.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

A téglalap örökli a csoport formázási kontextusát, így a `GroupShape`‑en belül jelenik meg. Később beállíthatod a vonal színét, kitöltését vagy szöveget is, ha szükséges.

## Több alakzat beillesztése

A **insert multiple shapes** képesség bemutatásához egy ellipszist illesztünk be közvetlenül a téglalap után. További alakzatokat (például háromszögeket, csillagokat) is hozzáadhatsz, mielőtt lezárod a csoportot.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Ekkor a csoport két különálló alakzatot tartalmaz: egy téglalapot és egy ellipszist. Mivel ugyanazzal a szülővel rendelkeznek, egységként mozgathatók.

## 3. lépés: A csoportos alakzat csatolása a bekezdés hierarchiához

A Word dokumentumok tartalmát bekezdésfákban tárolják. Ahhoz, hogy a csoport látható legyen a végleges fájlban, csatolni kell a jelenlegi bekezdéshez.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Miért szükséges ez a lépés:* A csoport bekezdéshez való hozzáfűzése nélkül az alakzatok csak a memóriában léteznek, és a dokumentum mentésekor kimaradnak.

## 4. lépés: A dokumentum mentése – alakzatok írása Word‑be

Végül a memóriában lévő `Document`‑et lemezre írjuk. Ezzel teljesül a **write shapes to word** cél.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Amikor megnyitod a `GroupShape.docx` fájlt a Microsoft Word‑ben, egy csoportosított téglalapot és egy ellipszist látsz, pontosan úgy, ahogy a kód beillesztette.

### Várt kimenet

- Egy **GroupShape.docx** nevű fájl a projekt kimeneti mappájában.
- A Word fájlban: egyetlen bekezdés, amely egy csoportosított téglalapot (100 pt × 50 pt) és egy ellipszist (80 pt × 40 pt) tartalmaz. Bármelyik alakzat kiválasztása az egész csoportot kijelöli.

## Gyakori edge case‑ek kezelése

| Helyzet | Ajánlás |
|-----------|----------------|
| **Eltérő DPI vagy oldalméret** | Állítsd be explicit módon a `builder.PageSetup.PaperSize` értékét alakzatok beillesztése előtt, hogy elkerüld a váratlan méretezést. |
| **Alakzatok pontos pozicionálása szükséges** | Használd a `builder.MoveTo`‑t a beszúrási pont mozgatásához, majd állítsd be a `groupShape.Left` és `groupShape.Top` tulajdonságokat (értékek pontban). |

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}