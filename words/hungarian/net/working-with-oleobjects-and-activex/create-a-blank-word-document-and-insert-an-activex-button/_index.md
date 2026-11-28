---
category: general
date: 2026-11-18
description: Hozzon létre egy üres Word-dokumentumot, és szúrjon be egy ActiveX gombot
  C#-val. Tanulja meg, hogyan adjon hozzá vezérlőt, állítsa be a gomb feliratát, és
  mentse a fájlt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: hu
lastmod: 2026-11-18
og_description: Hozzon létre egy üres Word-dokumentumot, és szúrjon be egy ActiveX
  gombot C#-ban. Kövesse ezt a teljes útmutatót a vezérlő hozzáadásához, a gomb feliratának
  beállításához és az eredmény mentéséhez.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Üres Word-dokumentum létrehozása és ActiveX gomb beillesztése – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Hozzon létre egy üres Word-dokumentumot, és szúrjon be egy ActiveX gombot
url: /hu/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása és ActiveX gomb beszúrása

Ha **üres Word dokumentumot** kell létrehoznod, és egy interaktív ActiveX gombot szeretnél elhelyezni benne, ez az útmutató pontosan megmutatja, hogyan teheted ezt meg az Aspose.Words for .NET segítségével. Megtekintheted a teljes kódot, megértheted, miért fontos minden sor, és megtanulhatod, hogyan **állítsd be a gomb feliratát**, hogy a vezérlő készen álljon a felhasználói interakcióra.

A fő cél mellett bemutatjuk a **how to insert ActiveX**-t, a **how to add control** lépéseit egy Word fájlba, valamint a **insert ActiveX button** finomságait egy egyedi felirattal. A végére egy újrahasználható mintát kapsz bármilyen dokumentum‑automatizálási helyzethez, amely beágyazott UI elemeket igényel.

## Mit fogsz megtanulni

* Hogyan **hozz létre egy üres Word dokumentumot** programozott módon.  
* A pontos API hívások, amelyek a **insert ActiveX button** beszúrásához és a tulajdonságok konfigurálásához szükségesek.  
* Hogyan **állítsd be a gomb feliratát**, hogy a vezérlő a kívánt szöveget jelenítse meg.  
* Tippek a fájl a kívánt helyre mentéséhez és a gyakori hibák kezeléséhez.

### Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+ esetén is működik).  
* Aspose.Words for .NET telepítve (`Install-Package Aspose.Words`).  
* Alapvető ismeretek C#-ban és Visual Studio-ban vagy bármely .NET‑kompatibilis IDE-ben.

---

## Üres Word dokumentum létrehozása az Aspose.Words segítségével

Az első lépés egy üres `Document` objektum példányosítása. Ez az objektum egy Word fájlt képvisel, amely tartalom nélkül van, amíg valamit nem adunk hozzá.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Why this matters*: Egy üres `Document` tiszta vásznat biztosít. Később beilleszthetsz bekezdéseket, táblázatokat vagy vezérlőket anélkül, hogy a meglévő formázás miatt aggódnál.

---

## DocumentBuilder inicializálása a dokumentummal való munkához

`DocumentBuilder` egy segédosztály, amely lehetővé teszi, hogy a jelenlegi kurzorpozícióba szúrj be tartalmat. Automatikusan nyomon követi, hol vagy a dokumentumban.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: `DocumentBuilder` nélkül manuálisan kellene manipulálnod az alacsony szintű csomópontfát. A builder egyszerűsíti a szöveg, képek és ActiveX vezérlők beszúrását.

---

## Hogyan szúrj be egy ActiveX gombot (insert activex button)

Most a `InsertForms2OleControl`-t használjuk egy ActiveX vezérlő beágyazásához. A metódus három argumentumot igényel:

1. A vezérlő típusa (`OleControlType.CommandButton`).  
2. A vezérlő belső neve (a VBA vagy makrókód által használt).  
3. Egy `RectangleF`, amely meghatározza a pozíciót és a méretet az oldalon.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Why this matters*: Ez a **how to insert activex** magja egy Word dokumentumban. A téglalap koordinátái pontban vannak kifejezve (1 pont = 1/72 hüvelyk). Állítsd be őket, hogy a gomb a kívánt helyen legyen.

### Tip

Ha a gombnak egy adott oldalon kell megjelennie, először mozdítsd a builder kurzorát:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Hogyan állítsd be a gomb feliratát (set button caption)

Miután a vezérlő el lett helyezve, módosíthatod a tulajdonságait. A legfeltűnőbb tulajdonság a `Caption`, amely meghatározza a gombon megjelenő szöveget.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Why this matters*: A felhasználók a feliratot látják, nem a belső nevet. Ennek módosítása a gombot értelmesebbé teszi a végső dokumentumban.

---

## A gombot tartalmazó dokumentum mentése

Végül írd a dokumentumot a lemezre. Bármely támogatott formátumot választhatod (`.docx`, `.pdf`, stb.). Itt Word dokumentumként mentünk.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Why this matters*: A fájl megőrzése lehetővé teszi, hogy megnyisd a Microsoft Wordben és teszteld a gombot. Amikor a dokumentum megnyílik, a gomb a “Press” felirattal jelenik meg.

### Várt eredmény

`with_button.docx` megnyitása Wordben egy üres oldalt mutat egy téglalap alakú gombbal, amely **Press** felirattal van ellátva. Alapértelmezés szerint a gomb megnyomása nem csinál semmit, mivel nincs hozzá VBA makró csatolva, de a vezérlő teljesen működőképes, és később kóddal összekapcsolható.

## Hogyan adj hozzá vezérlőt egy adott bekezdéshez (how to add control)

Néha a gombot egy adott bekezdésen belül szeretnéd elhelyezni, például egy útmutató szöveg után. Használd a `MoveTo`-t, hogy a buildert a vezérlő beszúrása előtt pozicionáld.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Why this matters*: Ez a minta bemutatja, hogyan **how to add control** kontextusban, biztosítva, hogy a dokumentum elrendezése logikus maradjon.

## Gyakori hibák és hogyan kerüld el őket

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| A gomb az oldalról kívül jelenik meg | A téglalap koordinátái az oldal margóin kívül vannak | `builder.PageSetup` használata az oldal méreteinek lekéréséhez és egy biztonságos `RectangleF` kiszámításához. |
| A felirat nem jelenik meg | `Caption` beállítva, mielőtt a vezérlő teljesen inicializálódna | `Caption` **a `InsertForms2OleControl` hívás után** állítsd be, ahogy a 4. lépésben látható. |
| A dokumentum a gomb nélkül mentődik | A builder kurzora a beszúrás után el lett mozdítva anélkül, hogy a változások el lettek volna mentve | Tartsd a buildert ugyanazon az oldalon, vagy hívd meg a `builder.Document.UpdatePageLayout()`-t a mentés előtt. |

## Teljes, futtatható példa

Az alábbiakban a teljes programot találod, amelyet másolhatsz, beilleszthetsz és futtathatsz. Üres Word fájlt hoz létre, beszúr egy ActiveX gombot, beállítja a feliratát, és elmenti az eredményt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output**: A program futtatása után nyisd meg a `C:\Temp\with_button.docx` fájlt a Microsoft Wordben. Egyetlen oldalt fogsz látni a „Below is an ActiveX button created programmatically:” szöveggel, majd egy **Press** feliratú gombbal.

## Következtetés

Most már tudod, hogyan **hozz létre egy üres Word dokumentumot**, **szúrj be egy ActiveX gombot**, **állítsd be a gomb feliratát**, és **mentsd** az eredményt az Aspose.Words for .NET segítségével. Ugyanaz a minta kiterjeszthető más ActiveX vezérlőkre (jelölőnégyzetek, listamezők stb.) a `OleControlType` módosításával.  

Ezután felfedezheted a **how to insert ActiveX button** eseményeket VBA-val, vagy a **how to add control** hozzáadását meglévő dokumentumokhoz, amelyek már tartalmaznak tartalmat. Mindkét téma közvetlenül az itt bemutatott koncepciókra épül.

Boldog kódolást, és nyugodtan kísérletezz különböző méretekkel, pozíciókkal és feliratokkal, hogy megfeleljenek alkalmazásod UI követelményeinek!

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek az ebben az útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to create Word document C# with an ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}