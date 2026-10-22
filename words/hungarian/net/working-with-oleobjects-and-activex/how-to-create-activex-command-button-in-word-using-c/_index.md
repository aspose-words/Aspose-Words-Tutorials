---
category: general
date: 2026-09-21
description: Tanulja meg, hogyan hozhat létre ActiveX parancsgombot egy Word dokumentumban
  az Aspose.Words és C# segítségével. A lépésről‑lépésre útmutató bemutatja a beszúrást,
  a pozicionálást és a mentést.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: hu
lastmod: 2026-09-21
og_description: Hozzon létre ActiveX parancsgombot egy Word-dokumentumban C# és az
  Aspose.Words használatával. Kövesse ezt a teljes útmutatót a gomb programozott beszúrásához,
  elhelyezéséhez és mentéséhez.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: ActiveX parancsgomb létrehozása Wordben C#‑val – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Hogyan hozzunk létre ActiveX parancsgombot a Wordben C#‑val
url: /hu/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre ActiveX command button-t a Wordben C# használatával

Ha **ActiveX command button**-t kell létrehoznia egy Word fájlban, ez az útmutató pontos lépéseket mutat. Az Aspose.Words for .NET használatával a gombot teljesen C# kódból adhatja hozzá, helyezheti el és konfigurálhatja.

Az ActiveX gomb programozott beszúrása megszünteti a kézi UI munkát, és lehetővé teszi az automatizált dokumentumgenerálást űrlapokhoz, jelentésekhez vagy interaktív sablonokhoz. Ebben az oktatóanyagban megtanulja, hogyan használja a **DocumentBuilder**‑t, az **InsertForms2OleControl** metódust és a kapcsolódó tulajdonságokat egy teljesen funkcionális gomb létrehozásához.

## Amire szüksége lesz

* .NET 6.0 SDK vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
* Aspose.Words for .NET (NuGet csomag `Aspose.Words`)
* IDE, például Visual Studio 2022 vagy VS Code
* Alapvető C# és Word dokumentum koncepciók ismerete

További Office telepítés nem szükséges, mivel az Aspose.Words függetlenül működik a Microsoft Wordtől.

## 1. lépés: A C# projekt beállítása

Hozzon létre egy új konzolos projektet, és adja hozzá az Aspose.Words csomagot.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Az `Aspose.Words` könyvtár biztosítja a **DocumentBuilder** osztályt, amelyet a dokumentum manipulálásához használunk.

## 2. lépés: A dokumentum és a builder inicializálása

Az első kódrészlet egy üres dokumentumot és egy `DocumentBuilder` példányt hoz létre. Ez az objektum a Word‑feldolgozási műveletek belépési pontja.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:** A `DocumentBuilder` nyomon követi az aktuális kurzorpozíciót, így minden későbbi beszúrás pontosan ott jelenik meg, ahol a kurzort elhelyezi.

## 3. lépés: ActiveX command button beszúrása

Az **InsertForms2OleControl** metódus a kért típusú ActiveX vezérlőt hozza létre. Itt egy `CommandButton`-t kérünk, és megadjuk a méretét pontban (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Magyarázat:**  
* `OleControlType.CommandButton` azt mondja az Aspose.Words‑nek, hogy gombot hozzon létre, nem más vezérlő típust.  
* A metódus egy `Forms2OleControl` objektumot ad vissza, amely a pozicionálási és tulajdonságmezőket teszi elérhetővé.

## 4. lépés: A gomb pozicionálása és tulajdonságainak beállítása

A beszúrás után a gombot a lap bármely pontjára áthelyezheti, és adhat neki programozott nevet és látható feliratot.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Pro tipp:** A koordináta‑rendszer a lap bal‑felső sarkában kezdődik. Állítsa a `Left` és `Top` értékeket, hogy a gombot a többi űrlapmezőhöz igazítsa.

## 5. lépés: A dokumentum mentése

Végül írja a dokumentumot a lemezre. A fájl tartalmazni fogja az ActiveX gombot, amely készen áll a Microsoft Wordben való megnyitásra, ahol a gomb interaktív lesz.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Amikor megnyitja a `ActiveXCommandButton.docx` fájlt a Wordben, egy **Submit** feliratú gombot fog látni a megadott helyen. A gombra kattintva a Wordben az alapértelmezett parancsgomb viselkedés aktiválódik (amelyet később VBA‑val vagy Word‑kiegészítőkkel testreszabhat).

## Teljes, futtatható példa

Az összes részlet összeállítása egy önálló programot eredményez, amelyet másolhat, beilleszthet és futtathat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Várható kimenet:** A konzol kiírja a *„Document created successfully.”* üzenetet, és a mappában most már megtalálható az `ActiveXCommandButton.docx`. A fájl megnyitása a Microsoft Wordben egy kattintható **Submit** gombot mutat, amely 100 pt-re van a bal margótól és 150 pt-re a lap tetejétől.

## Gyakori hibák és elkerülésük módja

| Probléma | Miért fordul elő | Megoldás |
|-------|----------------|-----|
| A gomb az oldalról kívül jelenik meg | A `Left`/`Top` értékek meghaladják az oldal méreteit | Használja a `doc.FirstSection.PageSetup.PageWidth` és `PageHeight` értékeket a biztonságos koordináták kiszámításához |
| A gomb nem látható a Wordben | A dokumentumot olyan formátumban mentették, amely eltávolítja az ActiveX vezérlőket (pl. `.txt`) | Mindig `.docx` vagy `.doc` formátumban mentse |
| Futtatási hiba `ArgumentOutOfRangeException` | Szélesség vagy magasság nulla vagy negatív értékre van állítva | Győződjön meg róla, hogy az `InsertForms2OleControl`‑nek átadott méretparaméterek pozitív számok legyenek |

## A megoldás bővítése

A gombot további tulajdonságok beállításával is testreszabhatja, például `Enabled`, `Visible`, vagy VBA‑val makrót csatolhat. A **Forms2OleControl** osztály lehetővé teszi más ActiveX vezérlők, például jelölőnégyzetek (`OleControlType.CheckBox`) vagy kombinált listák (`OleControlType.ComboBox`) beszúrását is.

Ha egy ciklusban több gombot kell generálnia, a beszúrási logikát egy segédmetódusba kapszulázhatja:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Következtetés

Most már tudja, hogyan **hozzon létre ActiveX command button**-t egy Word dokumentumban C# és Aspose.Words használatával. Az útmutató bemutatta a projekt beállítását, a gomb beszúrását az `InsertForms2OleControl`‑lel, a pozicionálását és a végső fájl mentését. Ezzel az alapokkal automatizálhat összetett űrlapokat, beágyazhat interaktív vezérlőket, és integrálhat Word dokumentumokat nagyobb .NET megoldásokba.

Ezután fedezze fel a kapcsolódó témákat, például az **Aspose.Words ActiveX** űrlapmezőket, a **C# DocumentBuilder** fejlett formázást, vagy a **ActiveX control in Word** programozott hozzáadását jelölőnégyzetekhez és legördülő listákhoz. Kísérletezzen különböző koordinátákkal és méretekkel, hogy megfeleljenek az Ön konkrét elrendezési igényeinek. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Word dokumentum létrehozása Aspose.Words for .NET használatával](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Téglalap alakzat létrehozása Wordben Aspose.Words‑szel – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Word dokumentum létrehozása táblázattal Aspose.Words használatával](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}