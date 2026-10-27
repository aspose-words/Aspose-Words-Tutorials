---
category: general
date: 2026-08-10
description: Hozzon létre Word-dokumentumot programozott módon az Aspose.Words segítségével,
  majd adjon hozzá egy ActiveX vezérlő Word gombot. ActiveX parancsgomb beillesztése
  percek alatt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: hu
lastmod: 2026-08-10
og_description: Hozzon létre Word-dokumentumot programozottan az Aspose.Words segítségével,
  majd adjon hozzá egy ActiveX vezérlő Word-gombot. Tanulja meg, hogyan szúrjon be
  gyorsan ActiveX parancsgombot.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Word-dokumentum létrehozása programozottan – ActiveX gomb hozzáadása C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Word-dokumentum létrehozása programozott módon és ActiveX gomb hozzáadása
url: /hu/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum programozott létrehozása és ActiveX gomb hozzáadása

Ha szükséged van **word dokumentum programozott létrehozására**, ez az útmutató végigvezet a teljes folyamaton az Aspose.Words for .NET segítségével. Megtanulod, hogyan **adj hozzá activex vezérlő word** elemeket és **illessz be activex parancsgomb** objektumokat egyetlen, önálló példában.

A Word fájlok kódon keresztüli generálása eltávolítja a Microsoft Word megnyitásának manuális lépését, lehetővé téve jelentések, számlák vagy adat‑alapú szerződések automatikus létrehozását. A tutorial végére egy kész‑használatra készen álló C# konzolalkalmazást kapsz, amely egy `.docx` fájlt hoz létre, benne egy interaktív ActiveX CommandButton‑nal.

## Előkövetelmények

* .NET 6.0 SDK vagy újabb (a kód .NET Framework 4.6+‑tal is működik)
* Visual Studio 2022 vagy bármely IDE, amely támogatja a .NET fejlesztést
* Érvényes Aspose.Words for .NET licenc (a teszteléshez használhatod az ingyenes értékelő kulcsot)
* Alapvető ismeretek a C# szintaxisról és a COM/ActiveX vezérlők koncepciójáról

> **Pro tipp:** Ha azt tervezed, hogy a generált dokumentumot olyan felhasználóknak osztod ki, akiknek nincs telepítve a Word, ágyazd be az ActiveX vezérlő futtatási fájljait a `.docx` mellé, vagy biztosíts egy makró‑engedélyezett sablont.

## Word dokumentum programozott létrehozása – kezdeti beállítás

Először add hozzá az Aspose.Words NuGet csomagot a projektedhez:

```bash
dotnet add package Aspose.Words
```

Ezután hozz létre egy új konzolprojektet (ha még nincs):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Nyisd meg a generált `Program.cs` fájlt – a teljes megoldással fogjuk lecserélni a tartalmát alább.

## 1. lépés: Névterek importálása és a licenc beállítása

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Miért fontos*: Az `Aspose.Words.Drawing` importálása hozzáférést biztosít a `Forms2OleControl` osztályhoz, amely egy ActiveX vezérlőt reprezentál egy Word dokumentumban. A licenc korai beállítása megakadályozza a futásidejű figyelmeztetéseket a termelésben.

## 2. lépés: Üres dokumentum és DocumentBuilder létrehozása

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` objektum a `.docx` fájl memóriában lévő reprezentációja. A `DocumentBuilder` úgy működik, mint egy kurzor, amelyet a dokumentumban mozgatva helyezhetsz el elemeket.

## 3. lépés: ActiveX CommandButton vezérlő beszúrása

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` egy OLE objektumot hoz létre, amelyet a Word ActiveX vezérlőként kezel. A koordináta rendszer pontokat használ (1 pont = 1/72 hüvelyk), ami megegyezik a Word elrendezési motorjával.

## 4. lépés: A gomb feliratának és opcionális tulajdonságainak beállítása

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

A `Caption` tulajdonság beállítása a leggyakoribb módja a gomb címkézésének. Ha azt szeretnéd, hogy a gomb egy VBA makrót hajtson végre, rendeld hozzá a makró nevét az `OnAction`‑hez. Ez az útmutató a vizuális részre koncentrál; a makró integráció a „Következő lépések” szakaszban van tárgyalva.

## 5. lépés: Dokumentum mentése

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

A program futtatásakor egy konzolos üzenetet látsz, amely megerősíti, hogy az `ActiveX_CommandButton.docx` a lemezre íródott.

### Teljes forráskód (másolásra kész)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

A kódrészlet futtatása egy Word fájlt hoz létre, amely egy kattintható **ActiveX command button**‑t tartalmaz. Nyisd meg a fájlt a Microsoft Wordben, válts **Tervező módra** (Fejlesztő fül → Tervező mód), és a gomb pontosan ott jelenik meg, ahol elhelyezted.

## 6. lépés: Az eredmény ellenőrzése

1. Nyisd meg az `ActiveX_CommandButton.docx` fájlt a Microsoft Wordben.
2. Engedélyezd a **Developer** fület, ha nem látható (`File → Options → Customize Ribbon → check Developer`).
3. Kattints a **Design Mode**‑ra. A gombnak meg kell jelennie a “Submit” felirattal.
4. Ha hozzáadtál egy `OnAction` makrót, kattints a gombra a Tervező mód kikapcsolt állapotában a makró aktiválásához.

Ha a gomb nem jelenik meg, ellenőrizd, hogy a Word biztonsági beállításai engedélyezik-e az ActiveX vezérlőket (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Gyakori kérdések és szélhelyzetek

| Kérdés | Válasz |
|----------|--------|
| **Can I insert other ActiveX types?** | Igen. `Forms2OleControlType` enum tartalmazza a `CheckBox`, `OptionButton`, `ComboBox`, stb. Cseréld le a `CommandButton`‑t a kívánt enum értékre |

## Mit érdemes legközelebb megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészletet tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Word dokumentum létrehozása fejléc és lábléc használatával az Aspose.Words segítségével](/words/english/net/header-footer-formatting/create-header-footer/)
- [Beágyazott kép beszúrása Word dokumentumba az Aspose.Words használatával](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}