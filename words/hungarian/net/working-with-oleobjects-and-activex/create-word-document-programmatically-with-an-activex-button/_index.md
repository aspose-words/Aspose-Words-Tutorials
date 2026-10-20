---
category: general
date: 2026-10-20
description: Programozottan hozza létre a Word‑dokumentumot, és adjon hozzá egy parancsgombot
  az Aspose.Words segítségével. Tanulja meg, hogyan szúrjon be ActiveX‑vezérlőt, és
  állítsa be a gomb feliratát.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: hu
lastmod: 2026-10-20
og_description: Hozzon létre Word-dokumentumot programozottan, és ágyazzon be egy
  ActiveX parancsgombot. Ez az útmutató bemutatja, hogyan szúrja be a vezérlőt, és
  hogyan állítsa be a feliratát az Aspose.Words segítségével.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Word-dokumentum létrehozása programozott módon – ActiveX gomb hozzáadása
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word-dokumentum programozott létrehozása ActiveX gombbal
url: /hu/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum programozott létrehozása ActiveX gombbal

Word dokumentum programozott létrehozása az Aspose.Words segítségével, majd egy parancsgomb hozzáadása, amelyre a felhasználók kattinthatnak. Ez az útmutató végigvezeti az ActiveX vezérlő beszúrásán, a tulajdonságok konfigurálásán, és a **.docx** fájlba mentésen.

Egy teljes, futtatható példát láthatsz, amelyet beilleszthetsz egy konzolalkalmazásba. A tutorial végére képes leszel olyan Word fájlt generálni, amely egy teljesen működő parancsgombot tartalmaz, és megérted, hogyan **add command button**, **add activex control**, **insert activex button**, és **set button caption** anélkül, hogy elhagynád a C# kódodat.

## Prerequisites

Mielőtt elkezdenéd, győződj meg róla, hogy a következők telepítve vannak:

* .NET 6.0 SDK vagy újabb  
* Visual Studio 2022 (vagy bármely C#‑kompatibilis IDE)  
* Aspose.Words for .NET licencfájl (az ingyenes próba is működik ebben a példában)  
* Alapvető C# ismeretek és a .NET projekt rendszerrel való jártaság  

Nem szükséges további NuGet csomag, mivel az ActiveX támogatás be van építve az **Aspose.Words** könyvtárba.

## 1. lépés: A projekt beállítása és az Aspose.Words hozzáadása

1. Nyiss egy terminált vagy a Visual Studio‑t, és hozz létre egy új konzolprojektet:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Add hozzá az Aspose.Words csomagot:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Opcionális) Ha rendelkezel licencfájllal, helyezd el a projekt gyökerében, és add hozzá a következő sort a `Program.cs` elejére, hogy elkerüld a kiértékelési vízjeleket:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## 2. lépés: Word dokumentum programozott létrehozása – a dokumentum inicializálása

Az első művelet a **Word dokumentum programozott létrehozása**. Ezt egy `Document` objektum és egy `DocumentBuilder` példányosításával végzed, amely lehetővé teszi a dokumentum tartalmának szerkesztését.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

A `Document` az egész fájlt képviseli, míg a `DocumentBuilder` egy kurzort tart, amelyet a dokumentum bármely pontjára mozgathatsz. Ez a felosztás tiszta API‑t biztosít, és lehetővé teszi, hogy később **add activex control** anélkül, hogy alacsony szintű struktúrákat kellene kézzel kezelned.

## 3. lépés: Parancsgomb hozzáadása – ActiveX vezérlő beszúrása

Most **add command button** egy `OleControlType.CommandButton` típusú ActiveX vezérlő beszúrásával. Az `InsertForms2OleControl` metódus a vezérlő típusát, egy helyet (`Point`) és egy méretet (`Size`) igényel.

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

A fenti hívás **insert activex button** a dokumentumba a megadott koordinátákon. A koordinátákat pontban mérik (1 pt ≈ 1/72 in). Ha a gombot egy konkrét bekezdéshez szeretnéd helyezni, előbb mozdítsd a builder kurzorát:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## 4. lépés: Gomb felirat beállítása – a parancsgomb szövegének testreszabása

Egy címke nélküli gomb zavaró, ezért **set button caption** egy értelmes szövegre. A `Caption` tulajdonság határozza meg a gombon megjelenő szöveget, míg a `Name` programozási azonosítót ad a vezérlőnek.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Ha később a dokumentumot makró‑támogatott formátumba (`.docm`) exportálod, az `OnClick` értéknek meg kell egyeznie egy VBA makró nevével. Egy egyszerű `.docx` esetén a tulajdonság tárolódik, de nem hajtódik végre, ami a legtöbb automatizálási szcenárióban megfelelő.

## 5. lépés: A dokumentum mentése, amely tartalmazza az ActiveX gombot

A vezérlő konfigurálása után **save the document**. Válassz egy olyan könyvtárat, amelyhez írási jogosultságod van, és használd a `.docx` kiterjesztést a legnagyobb kompatibilitás érdekében.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Amikor megnyitod a generált fájlt a Microsoft Word‑ben, egy **Submit** feliratú gombot látsz a megadott koordinátákon. A gombra kattintva az asztali kliens megpróbálja futtatni a `SubmitForm` makrót (ha létezik).

## 6. lépés: Az eredmény ellenőrzése és gyakori problémák hibaelhárítása

1. Nyisd meg az `ActiveXCommandButton.docx` fájlt a Microsoft Word‑ben.  
2. Válts **Design Mode**‑ra (Fejlesztői fül → **Design Mode**) a gomb kereteinek megtekintéséhez.  
3. Ha a gomb nem jelenik meg, ellenőrizd, hogy a **Developer** fül engedélyezve van-e, és hogy a Word verziód támogatja-e az ActiveX vezérlőket.  
4. Makró‑támogatott fájlok (`.docm`) esetén győződj meg róla, hogy az `OnClick`‑ben megadott makró neve megegyezik egy VBA rutin nevével; ellenkező esetben a Word biztonsági figyelmeztetést jelenít meg.

### Profi tipp

Az ActiveX vezérlők csak Windows‑on működnek. Ha platformközi interaktivitásra van szükséged, fontold meg a **Content Controls** (`RichTextContentControl`) használatát egy ActiveX gomb helyett.

## Teljes forráskód

Az alábbiakban a teljes, készen álló program látható. Másold be a `Program.cs` fájlba, és futtasd a `dotnet run` parancsot.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## Mit érdemes következőként tanulni?


Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}