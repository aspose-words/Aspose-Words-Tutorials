---
category: general
date: 2026-09-11
description: Tanulja meg, hogyan hozhat létre Word-dokumentumot C#-ban, és programozottan
  adjon hozzá egy parancsgombot az Aspose.Words használatával néhány egyszerű lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: hu
lastmod: 2026-09-11
og_description: Word dokumentum létrehozása C#‑ban, és programozottan parancsgomb
  hozzáadása az Aspose.Words segítségével. Kövesse ezt a teljes útmutatót a működő
  megoldáshoz.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Word-dokumentum létrehozása C#-ban – parancsgomb hozzáadása programozottan
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Hogyan hozhatunk létre Word dokumentumot C#-ban, és programozottan adhatunk
  hozzá egy parancsgombot
url: /hu/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre Word dokumentumot C#‑ban és adhatunk hozzá programozottan egy parancsgombot

Ha **Word dokumentumot szeretnél létrehozni C#‑ban** és egy interaktív gombot beágyazni, ez az útmutató pontosan megmutatja, hogyan teheted meg. Az Aspose.Words segítségével néhány sor kóddal programozottan hozzáadhatsz egy **CommandButton** vezérlőt, így elkerülve a Word‑ben végzendő manuális UI munkát.

Ebben a tutorialban megtanulod, hogyan:

* Inicializálj egy üres Word fájlt C#‑ban.
* Helyezz el egy ActiveX **CommandButton** vezérlőt.
* Állítsd be a gomb tulajdonságait, például a nevet és a feliratot.
* Mentsd el a dokumentumot, hogy a gomb megjelenjen a fájl Microsoft Word‑ben történő megnyitásakor.

Nem szükséges külső eszköz, csak az Aspose.Words for .NET könyvtár, és a lépések .NET 6+ vagy .NET Framework 4.6.2 és újabb verziókkal működnek.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel a következőkkel:

| Követelmény | Indok |
|------------|--------|
| .NET 6 SDK (vagy .NET Framework 4.6.2+) | Biztosítja a futtatókörnyezetet a C# projekthez. |
| Visual Studio 2022 (vagy bármely C# IDE) | Megkönnyíti a kód írását, felépítését és futtatását. |
| Aspose.Words for .NET NuGet csomag | Tartalmazza a példában használt `Document`, `DocumentBuilder` és `Forms2OleControl` osztályokat. |
| Alapvető C# szintaxis ismerete | Lehetővé teszi a kód követését további tanulási görbe nélkül. |

Az Aspose.Words csomagot a NuGet konzolon keresztül adhatod hozzá:

```powershell
Install-Package Aspose.Words
```

## 1. lépés: Új C# konzolprojekt létrehozása

Hozz létre egy konzolalkalmazást, amely generálja a Word fájlt. Nyiss egy terminált és futtasd:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

A generált `Program.cs` fájl fogja tartalmazni a következő lépésekben bemutatott kódot.

## 2. lépés: Üres dokumentum és DocumentBuilder létrehozása

Az első művelet egy `Document` objektum példányosítása, amely egy üres `.docx` fájlt képvisel, valamint egy `DocumentBuilder`, amely lehetővé teszi a dokumentum tartalmának szerkesztését.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:**  
A `Document` a Word összes elemének (bekezdések, táblázatok, vezérlők) tárolója. A `DocumentBuilder` egy folyékony API‑t biztosít az objektumok aktuális kurzorpozícióba történő beszúrásához anélkül, hogy alacsony szintű csomópontgyűjteményekkel kellene foglalkozni.

## 3. lépés: ActiveX CommandButton vezérlő beszúrása

Az Aspose.Words támogatja a régi ActiveX vezérlők beszúrását az `InsertForms2OleControl` metódus segítségével. A metódus megköveteli a vezérlő típusát és a kívánt méretet pontban.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Mi történik a háttérben:**  
A Word egy ActiveX vezérlőt OLE (Object Linking and Embedding) objektumként kezel. A `Forms2OleControl` osztály becsomagolja az OLE adatot, és olyan tulajdonságokat tesz elérhetővé, mint a `Name` és a `Caption`.

## 4. lépés: A gomb neve és felirata beállítása

Miután a vezérlő elhelyezésre került, testreszabhatod a futási idejű tulajdonságait. Egy értelmes `Name` segít később azonosítani a gombot, míg a `Caption` határozza meg a gombon megjelenő szöveget.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Pro tipp:**  
Ha a gomb kattintási eseményét VBA‑val szeretnéd kezelni, a `Name` lesz a makró neve, például `Sub btnSubmit_Click()`.

## 5. lépés: Dokumentum mentése lemezre

Végül írd a dokumentumot egy `.docx` fájlba. Válassz egy olyan mappát, amelyhez írási jogosultságod van; a példa egy relatív útvonalat használ, amely a projekt kimeneti könyvtárára mutat.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

A program futtatása után a `CommandButton.docx` jön létre. A fájl Microsoft Word‑ben történő megnyitásakor egy kattintható **Submit** gomb jelenik meg:

![Word document with a Submit command button](/images/command-button.png "Screenshot of a Word document containing a Submit command button created with C#")

*Image alt text (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Az eredmény ellenőrzése

1. Indítsd el a Word‑öt és nyisd meg a `CommandButton.docx` fájlt.  
2. A dokumentum törzsében látnod kell egy **Submit** feliratú gombot.  
3. A gomb fölé húzva megjelenik a `btnSubmit` név a **Properties** ablaktáblán (Fejlesztői fül → Tulajdonságok).  

Ha a gomb nem jelenik meg, ellenőrizd, hogy a **Developer** (Fejlesztő) fül engedélyezve van‑e a Word‑ben (File → Options → Customize Ribbon → jelöld be a *Developer* opciót). Az ActiveX vezérlők rejtve maradnak, ha ez a fül le van tiltva.

## Gyakori variációk és szélhelyzetek kezelése

| Helyzet | Ajánlott módosítás |
|-----------|------------------------|
| **Eltérő gombméret** | Módosítsd a `InsertForms2OleControl` szélesség‑ és magasságargumentumait. Például a `150, 40` nagyobb gombot hoz létre. |
| **Több gomb** | Hívd meg többször az `InsertForms2OleControl`‑t, a builder kurzorát a hívások között mozgatva (`builder.Writeln();`). |
| **ActiveX nélküli gomb** | Használd az `InsertFormField`‑et, hogy egy régi űrlapmezőt (pl. jelölőnégyzetet) adj hozzá, ha olyan régebbi Word‑verziókkal kell kompatibilitást biztosítani, amelyek blokkolják az ActiveX‑et. |
| **Keresztplatformos használat** | Az ActiveX vezérlők csak a Windows‑os Word‑ben működnek. Mac‑en vagy web‑alapú megjelenítők esetén fontold meg egy gombként stilizált hiperhivatkozás beszúrását. |
| **Biztonsági figyelmeztetések** | A Word biztonsági figyelmeztetést jeleníthet meg ActiveX‑t tartalmazó dokumentum megnyitásakor. A dokumentum megbízható tanúsítvánnyal való aláírása csökkenti ezt a súrlódást. |

## Teljes, futtatható példa

Az alábbiakban a teljes program látható, amelyet egyszerűen másolj be a `Program.cs`‑be. A kód a Aspose.Words NuGet csomag hozzáadása után módosítás nélkül lefordítható és futtatható.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Várható konzolkimenet:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

A generált fájl megnyitása után a **Submit** gomb készen áll a használatra.

## Összegzés

Most már tudod, hogyan **hozz létre Word dokumentumot C#‑ban** és **programozottan adj hozzá parancsgombot** az Aspose.Words segítségével. A folyamat lényegében egy `Document` inicializálása, egy `Forms2OleControl` beszúrása, a tulajdonságok beállítása és a fájl mentése. Innen tovább:

* További vezérlők (pl. jelölőnégyzetek, szövegmezők) hozzáadása a `ControlType` módosításával.
* VBA makrók csatolása a gombhoz egyedi logika megvalósításához.
* Ennek a technikának a kombinálása más Aspose.Words funkciókkal, például levélösszevonással vagy sablonkitöltéssel.

Kísérletezz különböző méretekkel, feliratokkal és több gombbal, hogy a saját automatizálási forgatókönyvedhez illeszkedjen. Boldog kódolást!

## Mit tanulj meg legközelebb?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutató technikáira épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy további API‑funkciókat saját projektjeidben is könnyedén alkalmazhass.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}