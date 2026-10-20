---
category: general
date: 2026-07-29
description: Parancsgomb hozzáadása Word-dokumentumhoz az Aspose.Words segítségével.
  Tanulja meg, hogyan állíthatja be az ActiveX vezérlő tulajdonságait, és hogyan adhat
  meg parancsgomb feliratot néhány egyszerű lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: hu
lastmod: 2026-07-29
og_description: Parancsgomb hozzáadása Word dokumentumhoz az Aspose.Words segítségével.
  Ez a bemutató megmutatja, hogyan állíthatók be az ActiveX vezérlő tulajdonságai,
  és hogyan lehet gyorsan beállítani a parancsgomb feliratát.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Parancsgomb hozzáadása Word-dokumentumhoz – Aspose.Words lépésről‑lépésre
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Parancsgomb hozzáadása Word dokumentumhoz az Aspose.Words segítségével – Teljes
  útmutató
url: /hu/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Parancsgomb hozzáadása Word dokumentumhoz – Teljes programozási útmutató

Valaha szükséged volt **add command button to word document** funkcióra, de nem tudtad, mely API hívásokat kell használni? Nem vagy egyedül; sok fejlesztő szembesül ezzel, amikor először próbál interaktív vezérlőket beágyazni egy DOCX fájlba. A jó hír, hogy az Aspose.Words meglepően egyszerűvé teszi. Ebben az útmutatóban végigvezetünk a CommandButton ActiveX vezérlő létrehozásán, **set activex control properties**, és **set command button caption** – mindezt tiszta C# kóddal, amelyet most azonnal másolhatsz‑beilleszthetsz.

A tutorial végére egy teljesen működő Word fájlt kapsz, amely egy kattintható „Submit” gombot tartalmaz, készen áll a Microsoft Wordben való megnyitásra. Nincs külső VBA script, nincs manuális UI manipuláció—csak tiszta programozott vezérlés.

## Mit fogsz megtanulni

* Hogyan hozzunk létre egy üres Word dokumentumot és egy `DocumentBuilder`-t.
* A pontos metódushívás a **add command button to word document** funkcióhoz az Aspose.Words használatával.
* Módszerek a **set activex control properties** beállítására, például méret, pozíció és név.
* A megfelelő technika a **set command button caption** beállításához, hogy a gomb pontosan azt a szöveget jelenítse meg, amit szeretnél.
* Tippek a szélhelyzetek kezeléséhez, mint például különböző gombtípusok, DPI skálázás és a Word verzió kompatibilitás.

> **Előfeltétel:** Visual Studio (vagy bármely C# IDE) Aspose.Words for .NET telepítéssel (NuGet csomag `Aspose.Words`). Előzetes ActiveX tapasztalat nem szükséges.

## 1. lépés: A projekt beállítása és a névterek importálása

Mielőtt **add command button to word document** funkciót használhatnánk, szükségünk van egy C# projektre, amely hivatkozik az Aspose.Words-re. Hozz létre egy új .NET konzolalkalmazást, majd add hozzá a NuGet csomagot:

```bash
dotnet add package Aspose.Words
```

Most hozd be a szükséges névtereket a forrásfájlba:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Ezek a három `using` direktíva hozzáférést biztosít a `Document`, `DocumentBuilder` és a `Forms2OleControl` osztályokhoz, amelyek az ActiveX beszúrását vezérlik.

*Pro tipp:* Ha Visual Studio-t használsz, az IDE automatikusan javasolja ezen direktívák hozzáadását, amikor beírod az osztályneveket.

## 2. lépés: Üres dokumentum és builder létrehozása

Egy új `Document` objektum egy üres Word fájlt képvisel. A `DocumentBuilder` a kényelmes „tollunk”, amely lehetővé teszi a rajzolást, szöveg beszúrását, és – ami a legfontosabb – az ActiveX vezérlők elhelyezését.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ekkor a dokumentum csak egy üres vászon – tekintsd úgy, mint egy tiszta papírlapot, amely a parancsgombodra vár.

## 3. lépés: A CommandButton ActiveX vezérlő beszúrása

Most végre **add command button to word document**. Az Aspose.Words a `InsertForms2OleControl` metódust biztosítja, amely elfogadja a vezérlő típusát és méreteit. A `Forms2OleControlType.CommandButton`-t fogjuk használni, és kényelmes 150 pont szélességet és 30 pont magasságot adunk neki.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

A metódus egy `Forms2OleControl` példányt ad vissza, amelyet a következő lépésben a **set activex control properties** beállításához fogunk használni.

## 4. lépés: A vezérlő konfigurálása – Név, Felirat és Pozíció

### A felirat beállítása

A felirat a gombon megjelenő szöveg. A **set command button caption** beállításához egyszerűen rendelj egy karakterláncot a `Caption` tulajdonsághoz:

```csharp
commandButton.Caption = "Submit";
```

A `"Submit"`-t bármire módosíthatod – „Save”, „Export”, „Launch”, stb. – és a Word pontosan azt a szöveget jeleníti meg.

### A vezérlő elnevezése

Egy jelentőségteljes név adása a vezérlőnek megkönnyíti a későbbi hivatkozást (például Word makrók automatizálásakor). Beállítjuk a `Name` tulajdonságot:

```csharp
commandButton.Name = "btnSubmit";
```

### Pozicionálás az oldalon

A Word pontokat (1/72 hüvelyk) használ a elrendezéshez. Állítsd a `Left` és `Top` tulajdonságokat, hogy a gombot a kívánt helyre helyezd:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Ha a gombot egy bekezdéshez szeretnéd igazítani, előbb mozgathatod a builder kurzorát, majd beszúrhatod a vezérlőt; a koordináták ehhez a helyhez lesznek relatívak.

*Szélhelyzet:* Magas DPI‑ú monitorokon a vizuális méret kissé eltérhet a Wordben. A gomb fizikai méretének eszközök között állandó megtartásához kiszámíthatod a pontokat a cél DPI alapján (normál esetben 96 DPI a Wordhez).

## 5. lépés: Dokumentum mentése

Miután a gomb teljesen konfigurálva van, a fájl mentése egyetlen sorban megoldható:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Az eredményül kapott `CommandButton.docx` egy teljesen működő ActiveX gombot tartalmaz. Nyisd meg a Microsoft Wordben, és egy „Submit” gombot látsz, amely pontosan a megadott helyen van.

### Várt eredmény

1. A Word dokumentum egyetlen oldallal nyílik meg.  
2. Egy téglalap alakú gomb, amely **Submit** felirattal rendelkezik, megjelenik a megadott koordinátákon.  
3. Ha jobb‑kattintasz a gombra és a **Properties** (Tulajdonságok) menüt választod, láthatod a `btnSubmit` nevet és a beállított egyéb tulajdonságokat.

## 6. lépés: Haladó variációk és gyakori buktatók

### Más ActiveX típusok beszúrása

A `InsertForms2OleControl` metódus nem csak parancsgombokra korlátozódik. Beágyazhatsz jelölőnégyzeteket, opciógombokat vagy akár egyedi ActiveX objektumokat:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Ugyanez a **set activex control properties** minta érvényes – csak cseréld ki a típus enumot.

### Word verziók kezelése

A régebbi Word verziók (2007 előtti) a bináris `.doc` formátumot használják, amely más módon tárolja az ActiveX vezérlőket. Az Aspose.Words automatikusan konvertálja a vezérlőt, amikor `.doc`-ként mented, de egyes tulajdonságok (például a pontos pozicionálás) eltolódhatnak. Ha örökölt formátumokra célozol, teszteld a kimenetet a szükséges Word verzióban.

### Biztonsági beállítások

A Word letilthatja az ActiveX vezérlőket szigorú makróbiztonságú gépeken. A „Security Warning” (Biztonsági figyelmeztetés) párbeszédablak elkerüléséhez fontold meg:

* A dokumentum aláírását egy megbízható tanúsítvánnyal.  
* A felhasználók tájékoztatását, hogy engedélyezzék az ActiveX tartalmat az adott fájlhelyen.  
* Makró‑mentes alternatíva használatát (pl. egyszerű tartalomvezérlők), ha a biztonság aggály.

## 7. lépés: Teljes működő példa

Az alábbiakban a teljes, futtatható program található, amely tartalmazza a megbeszélt összes lépést. Másold be a `Program.cs` fájlodba, szükség esetén módosítsd a kimeneti útvonalat, és nyomd meg a **Run** gombot.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Mit csinál ez a kód:**

* Új dokumentummal kezd.  
* Beszúr egy parancsgombot, **sets activex control properties**, és **sets command button caption**.  
* Hozzáad egy rövid magyarázó bekezdést.  
* Mentés `CommandButton.docx` néven.

Futtasd a programot, nyisd meg a generált fájlt, és a gombot a magyarázó szöveg alatt fogod látni.

## Összegzés

Most bemutattuk, hogyan **add command button to word document** az Aspose.Words segítségével, hogyan **set activex control properties**, és hogyan **set command button caption** – mindezt egy tömör, termelés‑kész C# kódrészletben. A megközelítés skálázható: cseréld ki a vezérlő típusát, módosítsd a méreteket, vagy iterálj egy adatforráson, hogy automatikusan több tucat gombot ágyazz be.

Szeretnél tovább menni? Próbáld ki:

* A gomb összekapcsolását egy makróval, amely adat exportot indít.  
* Képek vagy egyedi ikonok hozzáadását a gombba a `Picture` tulajdonság használatával.  
* Teljes űrlap építését több ActiveX vezérlővel (szövegdobozok, kombinált listák stb.).

A kísérletezés a legjobb módja a Word automatizálás elsajátításának. Ha elakadsz, ellenőrizd újra a DPI számításokat és a Word biztonsági beállításait. Boldog kódolást, és legyenek a dokumentumaid egyre interaktívabbak!

## Mit érdemes következőként megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}