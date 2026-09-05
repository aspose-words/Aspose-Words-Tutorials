---
category: general
date: 2026-09-05
description: Word dokumentum létrehozása Aspose.Words C#-vel, és megtanulni, hogyan
  szúrjunk be ActiveX parancsgombot, állítsuk be a gomb méretét, valamint adjunk interaktív
  gombfunkciót.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: hu
lastmod: 2026-09-05
og_description: Word dokumentum létrehozása C#-ban és ActiveX parancsgomb beillesztése.
  Ez az útmutató bemutatja, hogyan állítsuk be a gomb méretét, és hogyan adjunk hozzá
  interaktív gombfunkciókat.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Word dokumentum létrehozása ActiveX parancsgombbal C#‑ban – lépésről‑lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Hogyan készítsünk Word-dokumentumot ActiveX parancsgombbal C#‑ban
url: /hu/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre Word dokumentumot ActiveX parancsgombbal C#-ban

Ha programozott módon **Word dokumentumot** kell létrehoznod, és beágyazni egy kattintható UI elemet, ez az útmutató pontosan megmutatja, hogyan. Az Aspose.Words for .NET használatával **Word dokumentumot** hozhatsz létre, **parancsgombot adhatsz hozzá**, és szabályozhatod a megjelenését – mindezt anélkül, hogy megnyitnád a Microsoft Word‑et.

Megtanulod, hogyan **szúrj be ActiveX** vezérlőket, **állítsd be a gomb méretét**, és hogyan működjön a gomb interaktív UI komponensként. Nem szükséges előzetes COM vagy VBA tapasztalat; elegendő egy .NET fejlesztői környezet és az Aspose.Words könyvtár.

## Mit fogsz elérni

Az útmutató végére képes leszel:

* **Word dokumentumot létrehozni** nulláról C#‑ban.
* **ActiveX parancsgombot beszúrni** (a klasszikus „Click Me” vezérlő).
* **Beállítani a gomb méretét** és pontos pozícióját.
* Opcionálisan egyszerű **interaktív gomb** logikát hozzáadni (pl. makróhelyőrző).
* A fájlt `.docx` formátumban menteni, amely megnyitható a Microsoft Word‑ben vagy bármely kompatibilis megjelenítőben.

### Előfeltételek

| Követelmény | Indoklás |
|-------------|----------|
| .NET 6.0 vagy újabb | Biztosítja a C# kód futtatásához szükséges runtime‑ot. |
| Aspose.Words for .NET (legújabb verzió) | Biztosítja a példában használt `Document`, `DocumentBuilder` és `Forms2OleControl` API‑kat. |
| Visual Studio 2022 (vagy bármely C# IDE) | Lehetővé teszi a minta egyszerű lefordítását és futtatását. |
| Alapvető C# ismeretek | Szükséges a kódfolyamat megértéséhez. |

> **Pro tipp:** Ha az Aspose.Words próbaverzióját használod, győződj meg róla, hogy a licencet beállítod a kód futtatása előtt, hogy elkerüld a kiértékelési vízjeleket.

## Hogyan hozzunk létre Word dokumentumot – általános munkafolyamat

Az eljárás négy logikai lépésből áll:

1. **Új dokumentum inicializálása** és egy `DocumentBuilder` létrehozása a szerkesztéshez.  
2. **ActiveX parancsgomb beszúrása** a `InsertForms2OleControl` használatával.  
3. **A gomb konfigurálása** – felirat, méret és pozíció.  
4. **A dokumentum mentése** a lemezre.

Minden lépést alább külön szekcióban magyarázunk.

![Word dokumentum ActiveX gombbal](/images/activex-button.png "Képernyőkép egy Word dokumentumról, amely ActiveX parancsgombot tartalmaz, C#-val létrehozva")

## Hogyan szúrjunk be ActiveX parancsgombot

A **hogyan szúrjunk be activex** rész a `InsertForms2OleControl` metódussal kezdődik. Ez a metódus egy COM‑alapú vezérlőt hoz létre, amelyet a Word ActiveX objektumként kezel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Miért működik:** A `OleControlType.CommandButton` azt mondja az Aspose.Words‑nek, hogy hozza létre a klasszikus VB‑stílusú gombot. A méret és a helyzet pontokban van megadva (1 pont = 1/72 hüvelyk), ami pontos elrendezés‑szabályozást tesz lehetővé.

## Hogyan adjunk hozzá parancsgombot és állítsuk be a gomb méretét

Miután a vezérlő be lett szúrva, módosíthatod a vizuális tulajdonságait. A **parancsgomb hozzáadása** lépés magában foglalja a **gomb méretének beállítását** is.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Magyarázat:**  

* `Caption` a gombon megjelenő felirat.  
* `Width` és `Height` lehetővé teszik a **gomb méretének beállítását** a kezdeti beszúrás után – hasznos, ha a méret futásidőben változó adatoktól függ.  
* `Left` és `Top` áthelyezik a vezérlőt a dokumentum újra‑létrehozása nélkül.

> **Gyakori hiba:** Ha pontok helyett pixeleket használsz, a gomb túl kicsi vagy túl nagy lesz. Mindig konvertáld a pixelértékeket (`px * 72 / DPI`), ha képernyőmérőkből indul.

## Hogyan adjunk hozzá interaktív gombot (opcionális)

Az ActiveX gomb kattintáskor makrót tud végrehajtani, de a VBA kód beágyazása C#‑ból kívül esik egy tiszta Aspose.Words munkafolyamat keretein. Ehelyett hozzáadhatsz egy helyőrző tulajdonságot, amelyet a Word makrónévként ismer fel.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Amikor a felhasználó megnyitja a generált `.docx` fájlt a Word‑ben, a gomb kattintása megpróbálja futtatni a `MyMacroName` makrót. Ha a makró nem létezik, a Word felkéri a felhasználót, hogy hozza létre.

**Miért lehet ez hasznos:** Vállalati űrlapok esetén, ahol egy makró tölti ki a mezőket, a C# kódnak csak a gombot kell elhelyeznie; a makró logika a dokumentum VBA‑projektjében él.

## Dokumentum mentése és az eredmény ellenőrzése

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Várt kimenet:** A `CommandButton.docx` megnyitása a Microsoft Word‑ben egy **Click Me** feliratú gombot mutat, amely 100 pt távolságra van a bal margótól és 120 pt a tetejétől. A gomb méretei **200 pt × 80 pt**. A gomb kattintása elindítja a makróhelyőrzőt (ha létezik).

## Teljes működő példa

Az alábbiakban a teljes, futtatható program látható, amely mindent összehoz. Másold be egy új Console App projektbe, add hozzá az Aspose.Words NuGet csomagot, és futtasd.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Futtasd a programot, majd nyisd meg a generált fájlt. Látni fogod a **interaktív gombot**, amely készen áll a további testreszabásra.

## Gyakran ismételt kérdések

| Kérdés | Válasz |
|----------|--------|
| **Működik ez .NET Core‑dal?** | Igen. Az Aspose.Words támogatja a .NET Standard‑ot, így ugyanaz a kód fut .NET 5/6/7‑en is. |
| **Használhatok más ActiveX vezérlőket (pl. CheckBox)?** | Természetesen. Cseréld le a `OleControlType.CommandButton`-t `OleControlType.CheckBox`, `OleControlType.OptionButton` stb. értékekre. |
| **Mi a teendő, ha egy nagyobb gombra van szükség fekvő oldalra?** | Állítsd be a `Width`, `Height`, `Left` és `Top` tulajdonságokat arányosan. Ne feledd, hogy a pontok értéke változatlan marad az oldal tájolásától függetlenül. |
| **Szükséges-e makró a gomb kattinthatóságához?** | Nem. A gomb teljesen funkcionális UI elemként; a makró csak egyedi viselkedést ad hozzá kattintáskor. |

## Következtetés

Most már tudod, hogyan **hozz létre Word dokumentumot** az Aspose.Words segítségével, **adj hozzá parancsgombot**, **állítsd be a gomb méretét**, és opcionálisan kapcsolj a gombhoz egy makrót a **interaktív gomb** viselkedéshez. Ez a megközelítés lehetővé teszi űrlapok automatizálását, dinamikus jelentések generálását vagy Word‑alapú UI prototípusok építését közvetlenül C#‑ból.

Ezután érdemes megvizsgálni:

* **Hogyan szúrjunk be ActiveX jelölőnégyzeteket** felmérő űrlapokhoz.  
* **Hogyan adjunk hozzá gazdag szöveges tartalmat** a gomb köré a `DocumentBuilder` használatával.  
* **Hogyan védjük a dokumentumot**, miközben a gomb funkcionális marad.

Nyugodtan kísérletezz különböző vezérlőtípusokkal, méretekkel és makrónevekkel, hogy a saját forgatókönyvedhez illeszkedjenek. Boldog kódolást!

## Mit érdemes következőként megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Aspose.Words for .NET használatával](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Beágyazott kép beszúrása Word dokumentumba Aspose.Words segítségével](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Word dokumentum táblázattal létrehozása Aspose.Words használatával](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}