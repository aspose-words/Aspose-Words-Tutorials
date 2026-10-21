---
category: general
date: 2026-09-21
description: Word dokumentum programozott létrehozása, valamint a Word dokumentum
  mentése gomb, a parancsgomb beszúrása a Wordben és a parancsgomb feliratának beállítása
  a DocumentBuilder segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: hu
lastmod: 2026-09-21
og_description: Készítsen Word-dokumentumot programozottan az Aspose.Words segítségével.
  Tanulja meg, hogyan mentse a Word-dokumentum gombot, hogyan szúrjon be parancsgombot
  a Word-be, hogyan állítsa be a parancsgomb feliratát, és hogyan használja a DocumentBuilder-t
  interaktív űrlapokhoz.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Word-dokumentum létrehozása programozottan és gomb hozzáadása
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Word dokumentum programozott létrehozása és gomb beszúrása
url: /hu/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum programozott létrehozása és gomb beszúrása

Ha **programozott módon szeretnél Word dokumentumot létrehozni**, az Aspose.Words egy folyékony API-t biztosít, amely lehetővé teszi interaktív vezérlők, például egy CommandButton hozzáadását. Ez a bemutató elmagyarázza, **hogyan kell használni a DocumentBuilder‑t**, hogyan **menteni a Word dokumentum gombot**, és hogyan **állítsd be a parancsgomb feliratát**, hogy a gomb pontosan úgy jelenjen meg, ahogy elvárod a .docx fájlban.

Megtanulod, hogyan:

* Üres dokumentum inicializálása a `Document` segítségével.
* `DocumentBuilder` használata a dokumentum szerkesztéséhez.
* Egy **CommandButton** beszúrása (`insert command button word`).
* A gomb nevének és látható feliratának beállítása (`set command button caption`).
* Az eredmény lemezre mentése (`save word document button`).

A lépések .NET fejlesztőknek szólnak, C#‑ban és a legújabb Aspose.Words for .NET (v24.10) verzióval. Nem szükséges további NuGet csomag az Aspose.Words‑en kívül.

---

## Amit szükséges tudnod a kezdéshez

| Előfeltétel | Indoklás |
|--------------|----------|
| Visual Studio 2022 (vagy bármilyen C# IDE) | A minta kód lefordításához és futtatásához. |
| .NET 6.0 SDK vagy újabb | A példához szükséges futtatókörnyezetet biztosítja. |
| Aspose.Words for .NET (v24.10 vagy újabb) | Az a könyvtár, amely lehetővé teszi a **programozott Word dokumentum létrehozását** és az űrlapvezérlők manipulálását. |
| Alapvető ismeretek a C#‑ról és az OOP koncepciókról | A kódfolyamat megértéséhez szükséges. |

Az Aspose.Words‑t telepítheted a NuGet‑en keresztül:

```bash
dotnet add package Aspose.Words
```

---

## Word dokumentum programozott létrehozása

Az első lépés egy üres `Document` példány létrehozása. Ez az objektum a teljes Word fájlt reprezentálja a memóriában.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

A dokumentum programozott létrehozása egy tiszta vásznat biztosít, amelyre bekezdéseket, táblázatokat vagy interaktív vezérlőket helyezhetsz el.  

---

## A DocumentBuilder használata

`DocumentBuilder` az elsődleges osztály egy `Document` szerkesztéséhez. Metódusai lehetővé teszik szöveg, kép és űrlapmező beszúrását. Ebben a bemutatóban a CommandButton elhelyezésére használjuk.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder egy belső kurzort tart fenn, amely az aktuális beszúrási helyre mutat. Alapértelmezés szerint az első szakasz elején kezd, ami ideális a példánkhoz.

---

## CommandButton beszúrása Word dokumentumba

Az Aspose.Words a CommandButton‑t ActiveX vezérlőként kezeli. Az `InsertForms2OleControl` metódus egy általános OLE vezérlőt hoz létre, amelyet aztán gombként konfigurálunk.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Ezen a ponton a vezérlő már létezik a dokumentumban, de vizuális megjelenése csak a típus definiálása után jelenik meg.

---

## Parancsgomb feliratának beállítása

Most megmondjuk az OLE vezérlőnek, hogy CommandButton‑ként viselkedjen, és adunk neki egy barátságos feliratot.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

A **parancsgomb feliratának** beállítása elengedhetetlen, mivel a Word ezt a szöveget jeleníti meg a gomb felületén. Ha kihagyod a `SetCaption` hívást, a gomb egy általános címkével fog megjelenni.

---

## Word dokumentum gomb mentése

Végül a dokumentumot lemezre mentjük. A `Save` metódus az egész Word csomagot, beleértve az újonnan beszúrt gombot, egy .docx fájlba írja.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

A `CommandButton.docx` fájl most már egy teljesen működő gombot tartalmaz **Submit** felirattal. Amikor a felhasználó megnyitja a fájlt a Microsoft Word‑ben és rákattint a gombra, az alapértelmezett művelet (amelyet később VBA‑val köthetsz) végrehajtódik.

---

## Teljes működő példa

Az alábbiakban a teljes program látható, amelyet másolhatsz, beilleszthetsz és futtathatsz. Bemutatja a teljes munkafolyamatot a dokumentum létrehozásától a gomb mentéséig.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Várt eredmény**

* Egy `CommandButton.docx` nevű fájl a megadott útvonalon.
* A fájl Microsoft Word‑ben történő megnyitása egyetlen **Submit** gombot mutat az első oldalon.
* A gomb kiválasztható, átméretezhető, vagy összekapcsolható egy makróval a Word **Fejlesztő** lapjáról.

---

## Gyakori kérdések és speciális esetek kezelése

| Kérdés | Válasz |
|----------|--------|
| *Mi van, ha több gombra van szükségem?* | Ismételd meg a 3‑6. lépéseket különböző nevekkel és feliratokkal. Minden gombnak egyedi `SetName` értékkel kell rendelkeznie. |
| *Beállíthatom a gomb méretét?* | Igen. A vezérlő beszúrása után módosíthatod a `Width` és `Height` tulajdonságait az `OleFormat` objektumon keresztül. |
| *Minden Word verzióban működik a gomb?* | Az ActiveX vezérlők a Word asztali (Windows) verziójában támogatottak. Nem jelennek meg a Word Online‑ban vagy macOS‑en. |
| *Hogyan adhatok hozzá kattintás‑kezelőt?* | VBA kódot kell írnod, amely a gomb nevét (`btnSubmit`) hivatkozza. A VBA makrót a `doc.VbaProject` segítségével ágyazhatod be. |
| *Mi van, ha a gombot egy táblázat cellájába kell beszúrni?* | A builder kurzorát mozdítsd a kívánt cellához (`builder.MoveTo(cell.FirstParagraph)`) az `InsertForms2OleControl` hívása előtt. |

---

## Profi tippek

* **Profi tipp:** Mindig állíts be értelmes nevet a `SetName`‑vel. Ez egyszerűsíti a VBA automatizálást és könnyebbé teszi a hibakeresést.
* **Figyelj:** A `SetControlType` hívás elhagyása. Enélkül az OLE objektum egy általános helyőrzőként jelenik meg, nem kattintható gombként.
* **Teljesítmény tipp:** Ha sok dokumentumot generálsz egy ciklusban, használd újra ugyanazt a `DocumentBuilder` példányt, és minden beszúrás előtt hívd meg a `builder.MoveToDocumentEnd()`‑t, hogy elkerüld a felesleges kurzorállításokat.

---

## Következő lépések

Most, hogy tudod, hogyan **programozott módon Word dokumentumot hozhatsz létre**, **CommandButton‑t szúrj be Word‑be**, **állítsd be a parancsgomb feliratát**, és **mentse a Word dokumentum gombot**, felfedezheted a fejlettebb forgatókönyveket:

* Adj hozzá **TextFormField** vezérlőket a felhasználói bevitelhez.
* Kombináld a gombokat **MacroButton** mezőkkel a VBA közvetlen futtatásához.
* Használd a **DocumentBuilder.InsertImage**‑t ikonok elhelyezéséhez a gombokon.
* Integrálj ASP.NET‑tel Word űrlapok generálásához

## Mit érdemes legközelebb tanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Új Word dokumentum létrehozása](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word dokumentum létrehozása Aspose.Words for .NET‑tel](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Beágyazott kép beszúrása Word dokumentumba Aspose.Words használatával](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}