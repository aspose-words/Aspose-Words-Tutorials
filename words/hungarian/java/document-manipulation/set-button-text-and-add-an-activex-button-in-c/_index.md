---
category: general
date: 2026-10-10
description: Állítsa be a gomb feliratát, és adjon hozzá egy ActiveX gombot C#‑ban
  az Aspose.Words használatával. Tanulja meg, hogyan szúrjon be gombot, hozza létre
  a gombvezérlőt, és testreszabja a feliratot egy Word‑dokumentumban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: hu
lastmod: 2026-10-10
og_description: Állítsa be a gomb szövegét, és adjon hozzá egy ActiveX gombot C#‑ban
  az Aspose.Words segítségével. Kövesse ezt a lépésről‑lépésre útmutatót a gomb beszúrásához,
  a gombvezérlő létrehozásához és a felirat testreszabásához.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: A gomb szövegének beállítása és ActiveX gomb hozzáadása C#‑ban – teljes
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Gomb szövegének beállítása és ActiveX gomb hozzáadása C#‑ban
url: /hu/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gomb szövegének beállítása és ActiveX gomb hozzáadása C#-ban

Ha **gomb szövegét** szeretné beállítani egy ActiveX gombon egy Word dokumentumban, ez az útmutató pontosan megmutatja, hogyan teheti meg. A tutorial végére képes lesz **gomb beszúrására**, **gombvezérlő létrehozására**, és a felirat testreszabására néhány C# sorral.

Az ActiveX vezérlőkkel való munka gyakori, ha interaktív űrlapokat szeretne Word-ben – legyen szó szerződés sablonról, felmérésről vagy belső eszközről. A példa az Aspose.Words for .NET-et használja, egy könyvtárat, amely lehetővé teszi a Word fájlok manipulálását a Microsoft Office telepítése nélkül.

## Előfeltételek

Mielőtt elkezdené, ellenőrizze, hogy rendelkezik-e a következőkkel:

* .NET 6.0 SDK vagy újabb telepítve  
* Visual Studio 2022 (vagy bármely C#‑ot támogató IDE)  
* Aspose.Words for .NET licenc (az ingyenes értékelő verzió elegendő a tanuláshoz)  

Ezen felül szükség van a `Aspose.Words` NuGet csomagra való hivatkozásra:

```bash
dotnet add package Aspose.Words
```

## Hogyan szúrjunk be gombot egy Word dokumentumba

Az első lépés egy új `Document` és egy `DocumentBuilder` létrehozása. A builder a belépési pont a tartalom hozzáadásához, beleértve az ActiveX vezérlőket is.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:** A `Document` a teljes .docx fájlt képviseli, míg a `DocumentBuilder` magas szintű metódusokat biztosít, mint például az `InsertParagraph` és az `InsertFormField`. Egy tiszta dokumentummal kezdve biztosítható, hogy a gomb pontosan ott jelenik meg, ahol szeretné.

## Gombvezérlő létrehozása a Forms2OleControl segítségével

Most létrehozzuk a tényleges gombvezérlőt. A `Forms2OleControl` az az osztály, amelyet az Aspose.Words minden ActiveX objektumhoz használ, és a `COMMANDBUTTON` típus kattintható gombként jelenik meg a Word-ben.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Magyarázat:**  
* Az `InsertForms2OleControl` a megadott koordinátákon helyezi el a vezérlőt.  
* A méret pontokban van definiálva (1 pont = 1/72 hüvelyk). Ezeket a számokat módosíthatja, hogy illeszkedjenek a elrendezéséhez.

## ActiveX vezérlő hozzáadása és egyedi név megadása

Minden ActiveX objektumnak egyedi névvel kell rendelkeznie, hogy később hivatkozni tudjon rá (például VBA‑ban eseménykezeléskor).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tipp:** Kerülje a szóközöket és speciális karaktereket a névben; a Word a nevet azonosítóként kezeli a belső űrlapmodellben.

## Gomb szövegének (feliratának) beállítása az ActiveX gombon

Itt jön a kulcsszó, **set button text** szerepbe. A `Caption` tulajdonság határozza meg a felhasználók által a gombon látható címkét.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

A feliratot a dokumentum mentése előtt bármikor megváltoztathatja. Ha később lokalizálni szeretné a felhasználói felületet, egyszerűen hívja újra a `SetCaption`‑t egy másik karakterlánccal.

## Dokumentum mentése és az eredmény ellenőrzése

Végül írja a dokumentumot a lemezre. A fájl megnyitása a Microsoft Wordben megmutatja a gombot a testreszabott felirattal.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Várható kimenet:** Amikor megnyitja a *ActiveXButton.docx* fájlt a Wordben, egy a megadott koordinátákra pozícionált gombot lát, amelynek felirata **Click Me**. A gomb kattintása az alapértelmezett Word parancsgomb viselkedést váltja ki (amelyet később VBA‑val testreszabhat).

![Set button text example](https://example.com/activex-button.png){alt="Gomb szövegének beállítása példája"}

## ActiveX gomb hozzáadása és események kezelése (opcionális)

Ha a gombnak egyedi műveletet kell végrehajtania, hozzáadhat egy VBA makrót, amely a `Click` eseményre reagál. A makrót programozottan be lehet injektálni, de ez meghaladja a tutorial kereteit. A lényeg, hogy a gomb már jelen van, a felirata be van állítva – készen áll bármely általad választott eseménykezelésre.

## Gyakori hibák és elkerülésük módjai

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| A gomb el van helyezve rosszul | A koordináták pontban, nem pixelben vannak | Konvertálja a pixelértékeket pontokra (`points = pixels * 72 / DPI`) |
| A felirat nem változik a mentés után | `SetCaption` a `Save` után lett meghívva | Mindig a `doc.Save` **előtt** állítsa be a feliratot |
| A vezérlő nem látható régebbi Word verziókban | Egyes régi Word kiadások nem támogatják teljesen az ActiveX‑et | Tesztelje a cél Word verzióban; fallbackként használjon `CheckBox` vagy `DropDownList` elemet |
| Licencfigyelmeztetés a kimenetben | Az értékelő licenc lejárt | Érvényes Aspose.Words licenc alkalmazása: `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Teljes, futtatható példa

Az alábbiakban a teljes programot találja, amelyet másolhat, beilleszthet és futtathat. Tartalmazza az összes szükséges `using` direktívát, és bemutatja a teljes munkafolyamatot a dokumentum létrehozásától a mentésig.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Futtassa a programot a `dotnet run` paranccsal. A végrehajtás után nyissa meg a *ActiveXButton.docx* fájlt, hogy ellenőrizze, a gomb felirata **Click Me**‑re van állítva.

## Összefoglaló

* Megtanulta, hogyan **set button text**‑et állítson be egy ActiveX gombon az Aspose.Words segítségével.  
* Látta a pontos lépéseket a **how to insert button**, **create button control**, és **add activex control** végrehajtásához egy Word dokumentumban.  
* Most már rendelkezik egy újrahasználható kódrészlettel, amelyet bármely űrlap‑alapú Word automatizálási projekthez adaptálhat.

## Következő lépések

* Fedezze fel a `Forms2OleControlType` további értékeit, például a `CHECKBOX` vagy `LISTBOX` típusokat, hogy gazdagabb űrlapokat építsen.  
* Kombinálja a gombot egy VBA makróval, amely számításokat vagy adatellenőrzést végez.  
* Használja az Aspose.Words `FormField` API‑ját a felhasználói bevitel olvasásához a dokumentum kitöltése után.

Kísérletezzen a mérettel, pozícióval és felirattal, hogy megfeleljen a tervezési követelményeinek. Ha problémába ütközik, az Aspose.Words dokumentáció részletes referenciákat nyújt minden, ebben a tutorialban használt osztályhoz.

Boldog kódolást!


## Mit érdemes legközelebb megtanulni?


Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutató technikáira épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeiben.

- [Üres Word dokumentum létrehozása Aspose.Words használatával – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Árnyék hozzáadása alakzathoz Word-ben az Aspose.Words segítségével – Lépésről‑lépésre](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Oldalszámok hozzáadása egy Word dokumentum láblécéhez Aspose.Words for .NET használatával](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}