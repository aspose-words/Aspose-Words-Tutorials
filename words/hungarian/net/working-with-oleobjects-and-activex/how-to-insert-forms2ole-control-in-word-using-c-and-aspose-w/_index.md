---
category: general
date: 2026-11-22
description: Tanulja meg, hogyan illesszen be egy Forms2Ole vezérlőt a Word-be C#‑vel.
  Ez a lépésről‑lépésre útmutató a DocumentBuilder, a parancsgomb elhelyezése és a
  .docx mentése témákat fedi le.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: hu
lastmod: 2026-11-22
og_description: Helyezze be a Forms2Ole vezérlőt a Wordbe C#-val. Kövesse ezt az útmutatót
  egy parancsgomb hozzáadásához az Aspose.Words és a DocumentBuilder segítségével.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Forms2Ole vezérlő beszúrása Word-be C#‑val – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan illesszünk Forms2Ole vezérlőt a Wordbe C# és az Aspose.Words használatával
url: /hu/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be Forms2Ole vezérlőt a Word-be C# és Aspose.Words használatával

Ha **Forms2Ole vezérlőt kell beszúrni a Word-be**, ez a tutorial pontosan megmutatja, hogyan teheted meg C#-al. Akár kitölthető sablont építesz, akár űrlapok létrehozását automatizálod, az alábbi megoldás lehetővé teszi, hogy programozottan hozzáadj egy parancsgombot.

Megtanulod, hogyan hozz létre egy üres dokumentumot, hogyan használd a `DocumentBuilder`-t a vezérlő elhelyezéséhez, és hogyan mentsd el az eredményt `.docx` formátumban. A útmutató emellett bemutatja a gyakori buktatókat, például a koordináta-rendszereket és a régebbi Word-verziókkal való kompatibilitást.

## Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+ verzióval is működik)
* Aspose.Words for .NET (NuGet csomag `Aspose.Words`)
* Alapvető C# és a Word objektummodell ismerete
* IDE, például Visual Studio vagy VS Code

## 1. lépés: A projekt beállítása és a névterek importálása

Hozz létre egy új konzolos alkalmazást, és add hozzá az Aspose.Words csomagot:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

`Program.cs`-ben importáld a szükséges névtereket:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Pro tipp:** Használd az Aspose.Words legújabb verzióját, hogy teljes támogatást kapj a `Forms2OleControl` API-hoz.

## 2. lépés: Üres dokumentum létrehozása és a DocumentBuilder inicializálása

A `Document` osztály a Word-fájlt képviseli, míg a `DocumentBuilder` módszereket biztosít a tartalom beszúrásához.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` úgy működik, mint egy kurzor; ez után elkezdheted elhelyezni az elemeket bárhol a dokumentumban.

## 3. lépés: A gomb pozíciójának és méretének meghatározása

A Word a koordinátákat pontban (pt) méri (1 pt ≈ 1/72 in). A `System.Drawing` `Rectangle` struktúrája határozza meg a vezérlő határait.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` a vezérlést az aktuális oldal bal‑felső sarkába helyezi.
* Állítsd be az `x` és `y` értékeket, hogy a gombot máshová helyezd (pl. `new Rectangle(150, 200, 100, 30)`).

## 4. lépés: A Forms2Ole parancsgomb beszúrása

Most használd az `InsertForms2OleControl` metódust a vezérlő hozzáadásához. A metódus a vezérlő típusát, egy nevet és a fent definiált határokat igényli.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

A visszakapott `Forms2OleControl` objektum lehetővé teszi, hogy módosítsd a tulajdonságokat, például `Enabled`, `Visible`, vagy később makrónevet is hozzárendelj.

### Miért használjuk a Forms2Ole-t?

* **Legacy kompatibilitás** – A Forms2Ole vezérlők működnek a Word 97‑2003 (`.doc`) és az újabb `.docx` fájlokban.
* **Makró támogatás** – Képesek VBA makrókat indítani, így ideálisak interaktív sablonokhoz.
* **Pontos elhelyezés** – A tartalomvezérlőkkel ellentétben pontos koordinátákat szabályozhatsz.

## 5. lépés: A dokumentum mentése

Végül írd a fájlt a lemezre. Válassz egy olyan mappát, amelyhez írási jogosultságod van.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Nyisd meg az `output.docx`-et a Microsoft Wordben. Látnod fogsz egy **ClickMe** feliratú gombot az első oldal bal‑felső sarkában. A gombra kattintás a Wordben semmit sem csinál, amíg nem rendelsz hozzá makrót, de a vezérlő teljesen működőképes.

## Gyakori szélhelyzetek kezelése

| Helyzet | Hogyan kezelhető |
|-----------|-------------------|
| **A gomb az oldalról kívül jelenik meg** | Ellenőrizd, hogy a `Rectangle` koordináták az oldal margóin belül vannak-e. Használd a `builder.PageSetup.PageWidth` és `PageHeight` értékeket a biztonságos határok kiszámításához. |
| **A vezérlő nem látható régebbi Word verziókban** | Mentsd a dokumentumot `.doc` formátumban (`doc.Save("output.doc", SaveFormat.Doc)`) a Forms2Ole kompatibilitás biztosítása érdekében a Word 97‑2003 verzióval. |
| **A felirat módosítása szükséges** | Beszúrás után állítsd be a `commandButton.Caption = "Submit";` értéket. |
| **Makró hozzárendelése** | Állítsd be a `commandButton.MacroName = "MyMacro"` értéket; a makrónak léteznie kell a dokumentum VBA projektjében. |
| **Több gomb** | Ismételd meg a 4. lépést különböző `Rectangle` értékekkel és egyedi nevekkel. |

## Teljes, futtatható példa

Összegezve, itt egy önálló program, amelyet másolhatsz, beilleszthetsz és futtathatsz:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Várható kimenet:** A program futtatása után az `output.docx` megnyílik a Wordben, egy kattintható *Click Me!* feliratú gombbal, amely az első oldal bal‑felső sarkában helyezkedik el.

## Következtetés

Most már tudod, hogyan **szúrj be Forms2Ole vezérlőt a Word-be** C# és Aspose.Words használatával. A folyamat magában foglalja egy `Document` létrehozását, egy `Rectangle` pozicionálását, és az `InsertForms2OleControl` meghívását a `DocumentBuilder` segítségével. A teljes kódmintával és a szélhelyzetekre vonatkozó útmutatóval bármely automatizált Word munkafolyamatba beillesztheted a parancsgombokat.

### Következő lépések

* Fedezd fel a többi `ControlType` értéket, például `CheckBox` vagy `OptionButton`.
* Kombináld a Forms2Ole vezérlőket VBA makrókkal interaktív űrlapokhoz.
* Használd a `DocumentBuilder.MoveTo`-t, hogy a gombokat konkrét bekezdésekbe vagy táblázatokba helyezd.
* Tekintsd át az Aspose.Words **Forms2Ole** dokumentációját a fejlett tulajdonságbeállításokért.

Boldog kódolást, és élvezd a gazdagabb Word dokumentumok építését C# és Aspose.Words segítségével!

## Mit érdemes még megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan szúrjunk be OLE parancsgombot egy Word dokumentumba C# használatával](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Hogyan adjunk hozzá ActiveX vezérlőt a Wordhöz Aspose.Words segítségével – lépésről‑lépésre útmutató](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Parancsgomb hozzáadása Word dokumentumhoz Aspose.Words segítségével – Teljes útmutató](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}