---
category: general
date: 2026-08-04
description: Hozzon létre üres Word-dokumentumot, és szúrjon be parancsgombot az Aspose.Words
  segítségével. Tanulja meg beállítani a gomb méretét, és hozzáadni egy kattintható
  gombot C#-ban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: hu
lastmod: 2026-08-04
og_description: Készítsen üres Word-dokumentumot az Aspose.Words segítségével, és
  szúrjon be egy parancsgombot. Ez az útmutató bemutatja, hogyan állítható be a gomb
  mérete, hogyan adhat hozzá kattintható gombot, és hogyan menthető a fájl.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Üres Word-dokumentum létrehozása és parancsgomb hozzáadása – teljes C#-tanfolyam
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Üres Word-dokumentum létrehozása parancsgombbal – lépésről‑lépésre útmutató
url: /hu/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása parancsgombbal – lépésről‑lépésre útmutató

Ha **create blank word document**-ra van szükséged, amely interaktív gombot tartalmaz, ez az útmutató pontosan megmutatja, hogyan kell ezt megtenni az Aspose.Words for .NET segítségével. Megtanulod, hogyan **insert command button**, hogyan állíthatod be a megjelenését, és hogyan teheted kattinthatóvá – mindezt néhány C# sorban.

Az útmutató mindent lefed a projekt beállításától a végleges fájl mentéséig, így a teljes megoldást egyszerűen be tudod másolni a saját alkalmazásodba. Útközben elmagyarázzuk, hogyan **add clickable button**, **set button size**, és **create command button** programozottan.

## Előfeltételek

* .NET 6.0 SDK vagy újabb telepítve.
* Visual Studio 2022 (vagy bármely .NET‑et támogató IDE).
* Aspose.Words for .NET NuGet csomag (`Aspose.Words` verzió 23.12 vagy újabb).
* Alapvető ismeretek C#‑ban és objektum‑orientált programozásban.

Nem szükséges további Office interop összetevő, mivel az Aspose.Words teljesen függetlenül működik a Microsoft Word‑től.

## 1. lépés: A .NET projekt beállítása

Hozz létre egy konzolos alkalmazást, amely a Word automatizálási kódot fogja tartalmazni.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Ez a parancs létrehoz egy új `WordButtonDemo` mappát egy azonnal futtatható `Program.cs` fájllal, és hozzáadja az Aspose.Words könyvtárat.

## 2. lépés: Üres Word dokumentum létrehozása

Az első művelet a **create blank word document**. Az Aspose.Words egy `Document` osztályt biztosít, amely alapból egy üres Word fájlt képvisel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Egy üres dokumentum létrehozása tiszta vásznat biztosít, amelyre beilleszthetsz bekezdéseket, táblázatokat, vagy ebben az esetben egy OLE parancsgombot.

## 3. lépés: DocumentBuilder inicializálása

A `DocumentBuilder` egy segédeszköz, amely lehetővé teszi tartalom beillesztését a dokumentumba. Csatolnod kell azt a dokumentumhoz, amelyet éppen most hoztál létre.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder fenntartja az aktuális kurzorpozíciót, így minden későbbi beillesztés pontosan ott történik, ahol szeretnéd.

## 4. lépés: Parancsgomb beillesztése

Most **insert command button** (egy OLE `Forms2OleControl`) kerül a dokumentumba. Az `InsertForms2OleControl` metódus három argumentumot igényel:

1. Az OLE vezérlő ProgID‑je – `"CommandButton"` egy szabványos gombhoz.
2. Egy `Rectangle`, amely meghatározza a **set button size**‑t és a pozíciót.
3. A felirat, amely a gombon megjelenik.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Amikor a dokumentumot Wordben megnyitod, a gomb úgy viselkedik, mint bármely natív űrlapvezérlő – kattinthatsz rá, és a Word elindítja a hozzá tartozó makrót (ha létezik). Ez teljesíti a **add clickable button** követelményt.

### Miért használjuk a Forms2OleControl‑t?

A `Forms2OleControl` közvetlenül a DOCX fájlba ágyaz egy OLE objektumot, megőrizve a vezérlő tulajdonságait anélkül, hogy a Word Interop összetevőre lenne szükség. Ez a legmegbízhatóbb módja a **create command button** létrehozásának, amely minden Word verzióban működik.

## 5. lépés: A gomb testreszabása (opcionális)

Lehet, hogy pontosabban szeretnéd **set button size**-t beállítani, vagy további tulajdonságokat módosítani, például a betűtípust vagy a háttérszínt. Az Aspose.Words hozzáférést biztosít az alap OLE objektumhoz, lehetővé téve további finomhangolásokat.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Ha más méretre van szükséged, egyszerűen módosítsd a `Rectangle` értékeket a 4. lépésben. A koordinátákat pontban mérik (1 pt = 1/72 inch), így a `120` körülbelül 1,67 hüvelyk szélességnek felel meg.

## 6. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. A kapott fájl egy **blank word document**‑ot tartalmaz egy teljesen működő parancsgombbal.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Amikor megnyitod a `CommandButtonDemo.docx` fájlt a Microsoft Wordben, egy „Click Me” feliratú gombot látsz. A gombra kattintva megjelenik az alapértelmezett makró párbeszédablak, hacsak nem csatolsz egy egyéni makrót.

## Teljes forráskód

Az alábbiakban a teljes programot találod, amelyet beilleszthetsz a `Program.cs` fájlba. Tartalmazza a fent leírt összes lépést, és módosítás nélkül lefordítható.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Várt eredmény

A program futtatása létrehozza a `CommandButtonDemo.docx` fájlt. A fájl Wordben való megnyitása a következőt mutatja:

* Egyetlen oldal, amely egy **Click Me** feliratú gombot tartalmaz.
* A gomb betartja a **set button size**‑t (120 × 30 pont).
* A gombra kattintva a Word alapértelmezett parancsgomb viselkedése aktiválódik, ami megerősíti, hogy a **add clickable button** művelet sikeres volt.

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Működik ez .doc fájlokkal?** | Igen. Módosítsd a fájl kiterjesztését `doc.Save("file.doc")`-ben. Az OLE vezérlő a régi bináris formátumban is tárolódik. |
| **Mi a teendő, ha több gombra van szükség?** | Hívd meg többször az `InsertForms2OleControl`‑t, és minden új gombhoz állítsd be a `Rectangle`‑t, hogy elkerüld az átfedést. |
| **Csatolhatok makrót a gombhoz?** | A gomb önmagában nem tartalmaz makrokódot. VBA makrót kell manuálisan vagy a `Document` objektum `Modules` gyűjteményén keresztül hozzáadni a dokumentumhoz. |
| **Látható a gomb PDF exportáláskor?** | Amikor a DOCX‑et PDF‑re exportálod az Aspose.Words használatával, a gomb statikus képként jelenik meg, nem interaktív vezérlőként. |
| **Mely Word verziók támogatottak?** | Az OLE parancsgomb a Word 2007‑től kezdve működik, mivel a szabványos Forms2.0 specifikációt követi. |

## Következtetés

Most már tudod, hogyan **create blank word document**, **insert command button**, **add clickable button**, és **set button size** az Aspose.Words for .NET segítségével. A teljes példa bemutatja a **create command button** munkafolyamatot az elejétől a végéig, erős alapot biztosítva a fejlettebb Word automatizálási feladatokhoz.

## Következő lépések

* Fedezz fel más OLE vezérlőket (pl. `CheckBox`, `ListBox`) a ProgID módosításával az `InsertForms2OleControl`‑ben.
* Kombináld a gombot egy VBA makróval, hogy egyedi műveleteket hajtson végre a felhasználó kattintásakor.
* Használd az Aspose.Words `DocumentBuilder`‑jét további tartalom, például táblázatok, képek vagy lábjegyzetek hozzáadására a gomb beillesztése előtt.
* Kísérletezz a **set button size** értékekkel, hogy megfeleljenek a dokumentumod elrendezési követelményeinek.

Boldog kódolást, és élvezd a gazdagabb Word dokumentumok interaktív vezérlőkkel való építését!

## Mit érdemes még megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Üres Word dokumentum létrehozása árnyékolt téglalap alakzattal – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Word dokumentum létrehozása az Aspose.Words for .NET használatával](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}