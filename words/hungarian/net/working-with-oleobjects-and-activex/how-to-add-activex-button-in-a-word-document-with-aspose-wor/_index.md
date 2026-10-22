---
category: general
date: 2026-08-14
description: Hogyan adjon hozzá ActiveX gombot egy Word dokumentumhoz az Aspose.Words
  segítségével – tanulja meg, hogyan hozhat létre egy üres Word dokumentumot, és hogyan
  szúrhat be programozottan egy ActiveX gombot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: hu
lastmod: 2026-08-14
og_description: Hogyan adjon hozzá ActiveX gombot egy Word dokumentumba az Aspose.Words
  segítségével. Ez az útmutató megmutatja, hogyan hozhat létre egy üres Word dokumentumot,
  szúrjon be egy ActiveX gombot, és mentse el az eredményt.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Hogyan adjunk hozzá ActiveX gombot a Word-höz – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Hogyan adhatunk hozzá ActiveX gombot egy Word-dokumentumhoz az Aspose.Words
  használatával
url: /hu/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adhatunk hozzá ActiveX gombot egy Word dokumentumhoz az Aspose.Words segítségével

Ha **ActiveX** vezérlőket szeretne hozzáadni egy generált Word fájlhoz, ez az útmutató pontos lépéseket mutat. Megtanulja, hogyan **szúrhat be ActiveX gombot** programozottan, egy **üres Word dokumentum létrehozásával** kezdve, és egy mentett fájllal végződve, amely megnyitható a Microsoft Wordben.

Gomb hozzáadása, amely VBA kódot futtat vagy makrót indít, gyakori követelmény az automatizált jelentéskészítők, űrlap sablonok vagy interaktív szerződések esetén. Az Aspose.Words for .NET használatával a dokumentumot Office indítása nélkül építheti fel, így a folyamat gyors és szerverbarát marad.

## Előfeltételek

* .NET 6.0 (vagy újabb) SDK telepítve.
* Visual Studio 2022 vagy bármely C#‑kompatibilis IDE.
* Aspose.Words for .NET NuGet csomag (`Aspose.Words` 24.9 vagy újabb verzió).  
  Telepítse a következővel:
  ```bash
  dotnet add package Aspose.Words
  ```
* Windows környezet, ha tesztelni szeretné az ActiveX gombot, mivel az ActiveX vezérlők a Microsoft Word Windows verzióját igénylik.

## 1. lépés: Üres Word dokumentum létrehozása

Az első feladat a **üres Word dokumentum** létrehozása memóriában. Az Aspose.Words a `Document` osztályt biztosítja ehhez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` a teljes .docx fájlt képviseli. Ebben a pontban a dokumentum még nem tartalmaz oldalakat, de azonnal elkezdhet tartalmat hozzáadni.

## 2. lépés: DocumentBuilder inicializálása

`DocumentBuilder` egy segédeszköz, amely lehetővé teszi szöveg, kép és egyéb objektumok beszúrását a dokumentumba. A most létrehozott `Document` példányon működik.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder egy kurzorpozíciót tart fenn; minden, amit ez után beszúr, az első oldal elején jelenik meg.

## 3. lépés: ActiveX CommandButton vezérlő beszúrása

Az Aspose.Words a `InsertForms2OleControl` metódust biztosítja régi űrlapvezérlők, köztük az ActiveX hozzáadásához. A metódus a vezérlő típusát és méretét pontban várja.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

A visszaadott `Forms2OleControl` objektum lehetővé teszi a vezérlő tulajdonságainak, például a név és a felirat beállítását.

## 4. lépés: A gomb tulajdonságainak beállítása

Egy értelmes `Name` beállítása lehetővé teszi, hogy később VBA kódból hivatkozzon a vezérlőre. A `Caption` a gombon megjelenő szöveg.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tipp:** Tartsa a nevet röviden és alfanumerikusan; a Word elutasítja a szóközöket vagy speciális karaktereket tartalmazó neveket.

## 5. lépés: Dokumentum mentése

Végül írja a dokumentumot a lemezre. Használja a `.docx` kiterjesztést a modern Word fájlokhoz; az ActiveX gomb ugyanúgy működik `.doc` fájlokban is, de a `.docx` az új projektekhez ajánlott formátum.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Amikor megnyitja a `ActiveXButton.docx` fájlt a Microsoft Wordben, egy kattintható **Submit** gombot fog látni. Ha engedélyezi a makrókat, VBA kódot csatolhat a `btnSubmit_Click` eseményhez, és a gomb megnyomásakor lefut.

## Teljes, futtatható példa

Az összes részlet egyesítése egy önálló programot eredményez, amelyet másolhat, beilleszthet és futtathat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Várható kimenet** – A program futtatása után a konzol kiírja a mentés helyét, és a generált fájl Wordben való megnyitása egy **Submit** feliratú gombot mutat, amely az első oldal tetején helyezkedik el.

## Gyakori kérdések és szélsőséges esetek kezelése

### Működik a gomb minden Word verzióban?

Az ActiveX vezérlőket a Windows-on futó asztali Word verzió támogatja. Nem jelennek meg a Word Online, a macOS‑os Word vagy a mobil kliensekben. Ha keresztplatformos interaktivitásra van szükség, fontolja meg a tartalomvezérlők vagy HTML‑alapú megoldások használatát.

### Mit tegyek, ha más méretre vagy pozícióra van szükségem?

`InsertForms2OleControl` a vezérlőt a jelenlegi builder kurzornál helyezi el. Áthelyezéshez állítsa be a kurzort a `builder.MoveTo` használatával a beszúrás előtt, vagy módosítsa a vezérlő `Left` és `Top` tulajdonságait a létrehozás után:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Hozzáadhatok más ActiveX típusokat is?

Igen. A `Forms2OleControlType` felsorolás tartalmazza a `CheckBox`, `OptionButton`, `ListBox` és további elemeket. Cserélje le a `CommandButton`-t a kívánt enum értékre, és ennek megfelelően állítsa be a tulajdonságokat.

### Szükséges-e makró a gomb működéséhez?

A gomb önmagában semmit sem csinál, amíg nem csatol VBA kódot. Wordben nyomja meg a **Alt+F11**-et a VBA szerkesztő megnyitásához, keresse meg a `btnSubmit_Click`-et, és írja meg a kívánt logikát. A generált dokumentum megőrzi a VBA projektet, ha engedélyezi a **SaveFormat.Doc** (örökölt `.doc`) formátumot, de a `.docx` fájlok nem tárolhatnak VBA makrókat. Használja a `.doc` formátumot, ha beágyazott VBA-ra van szükség.

## Következtetés

Most már tudja, **hogyan adjon hozzá ActiveX** vezérlőket egy Word fájlhoz az Aspose.Words segítségével. A **üres Word dokumentum** létrehozása, egy `DocumentBuilder` inicializálása, **ActiveX gomb beszúrása**, a tulajdonságok beállítása és a fájl mentése lépéseinek követésével közvetlenül a .NET kódjából generálhat interaktív Word sablonokat.

Ezután fedezze fel a kapcsolódó témákat, például a **insert ActiveX button** eseménykezelést, a **create word document aspose** táblák vagy képek hozzáadását, valamint a makró‑engedélyezett dokumentumok biztonságos kezelését vállalati környezetben. Kísérletezzen különböző vezérlőtípusokkal és elrendezési beállításokkal, hogy a felhasználói élményt az alkalmazása igényeihez igazítsa.

Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}