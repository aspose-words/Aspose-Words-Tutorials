---
category: general
date: 2026-07-23
description: Word dokumentum gomb létrehozása az Aspose.Words segítségével – lépésről
  lépésre útmutató az ActiveX CommandButton beillesztéséhez egy .docx fájlba.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: hu
lastmod: 2026-07-23
og_description: 'Word dokumentum gomb létrehozása az Aspose.Words segítségével: tanulja
  meg, hogyan ágyazhat be egy ActiveX CommandButton-t egy Word fájlba percek alatt.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Word dokumentum létrehozása gomb – Aspose.Words teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Word dokumentum létrehozása gomb az Aspose.Words segítségével – Teljes kódpélda
url: /hu/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum gomb létrehozása az Aspose.Words segítségével – Teljes programozási útmutató

Valaha szükséged volt **create word document button** funkcióra, de nem tudtad, melyik API-t kellene használnod? Nem vagy egyedül – a legtöbb fejlesztő akadályba ütközik, amikor interaktív vezérlőket próbál beágyazni egy .docx fájlba. A jó hír? Az Aspose.Words for .NET segítségével néhány kódsorral teljesen működőképes ActiveX CommandButton-t helyezhetsz el egy Word dokumentumban.

Ebben az útmutatóban végigvezetünk a teljes folyamaton: a projekt beállításától, egy `DocumentBuilder` inicializálásán, a gomb beszúrásán a `InsertForms2OleControl` segítségével, egészen a fájl mentéséig, hogy a Word felismerje a vezérlőt. A végére egy azonnal használható Word fájlt kapsz, amely tartalmaz egy kattintható gombot – COM interop akrobátiára nincs szükség.

## Amire szükséged lesz

- **.NET 6.0** vagy újabb (a kód .NET Framework 4.6+ verzióval is működik).  
- **Aspose.Words for .NET** NuGet csomag (23.9 vagy újabb verzió).  
- Alapvető C# ismeretek (a szintaxis kezdőbarát lesz).  
- Visual Studio 2022 vagy bármely kedvelt IDE.

Ennyi – nincs extra COM referencia, nincs Office interop, csak tiszta managed kód.

---

## 1. lépés: Aspose.Words beállítása a **create word document button** létrehozásához

Először is add hozzá az Aspose.Words csomagot a projektedhez:

```bash
dotnet add package Aspose.Words
```

Vagy ha a Visual Studio NuGet UI-t használod, keresd meg az “Aspose.Words” csomagot és kattints a **Install** gombra. Ez az egyetlen sor hozzáférést biztosít a `Document`, `DocumentBuilder` és a `InsertForms2OleControl` metódusokhoz, amelyekre később szükség lesz.

> **Pro tip:** Tartsd naprakészen a NuGet csomagjaidat; az újabb kiadások gyakran tartalmaznak hibajavításokat az ActiveX kezeléshez.

## 2. lépés: **DocumentBuilder** inicializálása egy **ActiveX CommandButton**-hoz

Most létrehozunk egy új Word dokumentumot és elindítunk egy `DocumentBuilder`-t. A `DocumentBuilder`-t tekintheted egy ecsetnek, amely lehetővé teszi, hogy tartalmat rajzolj a vászonra.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Vedd észre, hogy importáljuk a `System.Drawing`-ot – a `Rectangle` struktúra határozza meg a gomb helyét és méretét. Itt fog élni a **ActiveX CommandButton**.

## 3. lépés: **InsertForms2OleControl** használata a **CommandButton** hozzáadásához

Itt a tutorial szíve: a gomb beszúrása. A `InsertForms2OleControl` metódus három argumentumot vár – a vezérlő típust, egy `Rectangle`-t, és opcionálisan egy nevet. A `OleControlType.CommandButton`-t fogjuk használni, hogy pontosan azt a vezérlőt jelöljük ki, amelyre szükségünk van.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Ez az egyetlen hívás sokat csinál:

1. **Creates** egy OLE objektumot a Word fájlban.  
2. **Registers** mint ActiveX CommandButton, amelyet a Word kattintható UI elemmé alakít.  
3. **Positions** a megadott téglalap szerint.

Ha módosítani szeretnéd a gomb feliratát vagy egyéb tulajdonságait, a beszúrás után hozzáférhetsz az alatta lévő `OleFormat`-hoz. A legtöbb esetben az alapértelmezett felirat (“CommandButton1”) elegendő.

## 4. lépés: A **CommandButton**-t tartalmazó Word dokumentum mentése

A mentés egyszerű – csak egy olyan mappára mutass, amelyhez írási jogosultságod van. A fájlkiterjesztésnek `.docx`-nek kell lennie, hogy a gomb megmaradjon a körutazás során.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Amikor megnyitod a `CommandButton.docx` fájlt a Microsoft Wordben, egy kis gombot látsz az első oldal bal‑felső sarkában. Alapértelmezés szerint a kattintás nem csinál semmit (ehhez VBA szükséges), de a vezérlő teljesen működőképes és később összekapcsolható.

> **Why this works:** Az Aspose.Words közvetlenül a DOCX csomagba írja az OLE adatfolyamot, megkerülve a Word futásidejű vezérlőgenerálását. Ez garantálja, hogy a gomb pontosan ott jelenik meg, ahol elhelyezted.

## 5. lépés: A gomb ellenőrzése Wordben

Nyisd meg a generált fájlt:

1. Indítsd el a Microsoft Wordöt.  
2. Navigálj a **File → Open** menüpontra, és válaszd ki a `CommandButton.docx` fájlt.  
3. Egy “CommandButton1” feliratú téglalap alakú gombot kell látnod.

Ha nem látod a gombot, ellenőrizd, hogy a **Design Mode** engedélyezve van-e (Developer → Design Mode). Ez kapcsolja be az ActiveX vezérlők vizuális megjelenítését.

## 6. lépés: Haladó beállítások – az **ActiveX CommandButton** testreszabása

Az alábbiakban néhány gyors trükköt találsz, amelyek hasznosak lehetnek:

| Cél | Kódrészlet |
|------|--------------|
| Felirat módosítása | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Makró név beállítása (Word makró támogatást igényel) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Átméretezés beszúrás után | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Ezek a példák bemutatják az `InsertForms2OleControl` rugalmasságát. Más ActiveX vezérlőket is beágyazhatsz, például `CheckBox` vagy `ListBox`, a `OleControlType` enum megfelelő értékének cseréjével.

## Teljes működő példa

Az alábbi program teljes, másolás‑beillesztés‑kész megoldást nyújt, amely **creates a word document button**-t hoz létre a semmiből:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Expected output when you run the program:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Nyisd meg a keletkezett fájlt, és a gomb pontosan ott lesz, ahol a kód elhelyezte.

## Gyakori hibák és elkerülésük

- **Missing `System.Drawing` reference** – A `Rectangle` struktúra itt található; nélküle a fordító hibát jelez.  
- **Using an older Aspose.Words version** – A korábbi kiadások nem támogatták teljes mértékben a `InsertForms2OleControl`-t. Frissíts a legújabb stabil csomagra.  
- **Saving as `.doc` instead of `.docx`** – Az OLE adatfolyam eltávolításra kerül a régebbi bináris formátumban, így a gomb eltűnik.  
- **Running on a headless server without Word installed** – A gomb továbbra is a fájlban lesz, de Word nélkül nem tudod előnézetben megtekinteni. Ez rendben van az automatizált generálási folyamatokhoz.

## Következő lépések – a **create word document button** munkafolyamat kibővítése

Miután elsajátítottad az alapokat, gondolj ezekre a haladó ötletekre:

- **Attach VBA macros** a gombhoz egyedi üzleti logika megvalósításához.  
- **Generate multiple buttons** egy ciklusban dinamikus űrlapokhoz.  
- **Combine with Aspose.PDF** a dokumentum PDF‑be exportálásához, miközben megőrzi a vizuális elrendezést (a gomb statikus képpé válik PDF‑ben).  
- **

## Mit tanulj meg legközelebb?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy további API funkciókat saját projektjeidben is könnyedén alkalmazhass.

- [Word dokumentum létrehozása az Aspose.Words for .NET segítségével](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Téglalap alakú forma létrehozása Wordben az Aspose.Words‑szel – Lépés‑ről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Beágyazott kép beszúrása Word dokumentumba az Aspose.Words segítségével](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}