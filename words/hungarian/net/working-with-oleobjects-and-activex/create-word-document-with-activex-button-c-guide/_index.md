---
category: general
date: 2026-07-19
description: Word-dokumentum létrehozása Aspose.Words C#-val, és megtanulni, hogyan
  adjon hozzá ActiveX parancsgombot, állítsa be a gomb méretét, és szúrja be a gombot
  programozottan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: hu
lastmod: 2026-07-19
og_description: Készítsen Word-dokumentumot az Aspose.Words C# segítségével, és néhány
  másodperc alatt ágyazzon be egy ActiveX parancsgombot. Kövesse a lépésről‑lépésre
  útmutatót a gomb méretének beállításához és a gomb egyszerű beszúrásához.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Word dokumentum létrehozása ActiveX gombbal – C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word-dokumentum létrehozása ActiveX gombbal – C# útmutató
url: /hu/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása ActiveX gombbal – Teljes C# útmutató

Valaha is elgondolkodtál azon, hogyan **Word dokumentumot hozhatsz létre**, amely egy működő ActiveX gombot tartalmaz? Lehet, hogy egy jelentést automatizálsz, és szükséged van egy kattintható „Jóváhagyás” vezérlőre közvetlenül a fájlban. Ebben az útmutatóban lépésről lépésre bemutatjuk ezt – az Aspose.Words for .NET használatával ActiveX parancsgombot adunk hozzá, beállítjuk a méretét, és beillesztjük a kívánt helyre.

Ha valaha is azon töprengtél, *how to add activex* vezérlőket manuálisan a Word megnyitása nélkül, jó helyen vagy. A végére egy futtatható példát, minden lépés világos magyarázatát és tippeket a gyakori buktatók kezeléséhez kapsz.

## Mit fogsz megtanulni

- Hogyan állítsd be az Aspose.Words-ot egy C# projektben  
- A pontos kód a **create word document** létrehozásához és egy ActiveX parancsgomb beágyazásához  
- Módszerek a **set button size** beállítására, valamint a felirat és a név testreszabására  
- A megfelelő mód a **insert command button** beillesztésére és a **how to insert button** elvégzésére a dokumentum bármely helyén  
- Edge‑case szempontok (Word verzió, platformkorlátok, biztonsági figyelmeztetések)

### Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑on is működik).  
- Érvényes Aspose.Words for .NET licenc (vagy egy ingyenes értékelő kulcs).  
- Visual Studio 2022 (vagy bármely kedvelt IDE).  
- Alapvető ismeretek C#‑ban és az objektum‑orientált programozásban.

Más külső könyvtárra nincs szükség.

---

## 1. lépés: Word dokumentum létrehozása – Projekt beállítása

Mielőtt **insert command button**-t be tudnánk szúrni, szükségünk van egy üres Word fájlra a munkához. Ez a lépés bemutatja a klasszikus “create word document” mintát az Aspose.Words használatával.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Miért fontos:** A `Document` a teljes .docx fájlt képviseli, míg a `DocumentBuilder` a jelenlegi kurzorpozíciót követi. Minden későbbi beszúrás (beleértve az ActiveX vezérlőnket is) ehhez a builderhez viszonyítva történik.

---

## 2. lépés: Hogyan adjunk hozzá ActiveX‑t – Parancsgomb vezérlő felépítése

Most, hogy a dokumentum létezik, foglalkozzunk a **how to add activex** részével. Az Aspose.Words a `Forms2OleControl` osztályt biztosítja az ActiveX objektumokhoz. Itt létrehozunk egy parancsgombot és beállítjuk a tulajdonságait, beleértve a **set button size** követelményt.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tipp:** A méret pontban van mérve (1 pont = 1/72 hüvelyk). Állítsd a értékeket a layouthoz; egy tipikus eszköztár gomb esetén a 120 × 30 jól működik.

---

## 3. lépés: Parancsgomb beszúrása – A **Insert Command Button** magja

Miután a vezérlő készen áll, most **insert command button**-t szúrunk be a dokumentumba a builder aktuális helyén. A builder-t bárhová áthelyezheted (pl. egy bekezdés után), mielőtt meghívod ezt a metódust.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Ha **how to insert button**-t egy adott könyvjelzőnél szeretnéd beszúrni, egyszerűen előbb mozdítsd a builder-t:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Mi történik a háttérben?** Az Aspose.Words a szükséges OLE objektumfolyamokat írja a .docx csomagba, így a Word a gombot extra makrók nélkül is megjeleníti.

---

## 4. lépés: Dokumentum mentése – A **Create Word Document** ciklus befejezése

Az utolsó lépés egyszerű: a fájl lemezre mentése. Ez befejezi a **create word document** körfolyamatot, az ActiveX beágyazását és a mentést.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Nyisd meg a létrehozott fájlt a Microsoft Wordben (csak Windows). Egy kattintható „Click Me” feliratú gombot kell látnod. A kattintás a CommandButton alapértelmezett műveletét indítja el – semmi sem történik, hacsak nem csatolsz VBA kódot, de a vezérlő teljesen működőképes.

> **Várható kimenet:** Egy .docx fájl egyetlen oldallal, egy beillesztési pontnál középre helyezett gombbal, mérete 120 × 30 pt, felirata “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Kép alt szöveg:* **ActiveX gomb beillesztve egy Word dokumentumba C#-ban** (matches `og_image_alt`).

---

## 5. lépés: Edge Cases, biztonság és legjobb gyakorlatok

### Platformkorlátok
- Az ActiveX vezérlők csak a Windows verziójú Wordben futnak. Ha a közönséged macOS vagy Word Online felhasználókat is tartalmaz, a gomb statikus képként jelenik meg.
- Egyes vállalati környezetek biztonsági okokból letiltják az ActiveX-et; ilyenkor alá kell írni a dokumentumot, vagy tájékoztatni a felhasználókat a tartalom engedélyezéséről.

### VBA interakció (opcionális)
Ha azt szeretnéd, hogy a gomb egy makrót hajtson végre, a mentés után VBA projektet kell hozzáadnod a dokumentumhoz. Az Aspose.Words nem generál VBA kódot automatikusan, de a `Document.VbaProject` API-val be lehet injektálni.

### Névütközések
Mindig adj minden vezérlőnek egyedi `Name` értéket. Azonos név újbóli használata futásidejű hibákat okozhat, amikor a Word megpróbálja feloldani a vezérlőt.

### Teljesítmény tipp
Sok vezérlő beszúrásakor használd újra ugyanazt a `DocumentBuilder` példányt, és kerüld a `doc.Save` hívását egy cikluson belül. Csoportosítsd a beszúrásokat, és a végén egyszer mentsd el.

---

## Teljes működő példa

Mindent egy helyre téve, itt egy teljes, másolás‑beillesztésre kész program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Futtasd a programot, nyisd meg a mentett fájlt, és a gombot pontosan ott fogod látni, ahol a builder pozícionálva volt.

---

## Következtetés

Most **created word document**-ot hoztunk létre a semmiből, megtanultuk a **how to add activex**-t a `Forms2OleControl` konfigurálásával, elsajátítottuk a **set button size** tulajdonságokat, és bemutattuk a helyes módot a **insert command button** és a **how to insert button** bármely helyre történő beillesztésére a fájlban.

Egyetlen kódmintából most egy szilárd alapot kaptál a fejlettebb Word automatizáláshoz – legyen szó interaktív űrlapokkal ellátott sablonok építéséről, felhasználói jóváhagyást igénylő szerződések generálásáról, vagy egyszerűen csak néhány hasznos vezérlő elhelyezéséről egy jelentésben.

### Mi a következő?

- **Style the button** – betűtípusok, színek módosítása, vagy képháttér hozzáadása.  
- **Attach VBA macros** – a gombot számítások végrehajtására vagy külső programok indítására használni.  
- **Combine with other controls** – jelölőnégyzetek, listamezők vagy akár beágyazott Excel táblázatok.

Nyugodtan kísérletezz, és ha elakadsz, hagyj egy megjegyzést alul. Boldog kódolást, és élvezd a Word automatizálását az Aspose.Words-szal!

## Mit érdemes még megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Aspose.Words for .NET használatával](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Csoport alakzat létrehozása Word dokumentumban Aspose.Words for .NET segítségével](/words/english/net/working-with-shapes/add-group-shape/)
- [Beágyazott kép beszúrása Word dokumentumba Aspose.Words használatával](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}