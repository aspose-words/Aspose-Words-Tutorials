---
category: general
date: 2026-08-17
description: OleControlType.CommandButton példát beszúrni Word-be az Aspose.Words
  használatával. Tanulja meg, hogyan adhat hozzá űrlapvezérlőket egy Word-dokumentumhoz
  programozottan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: hu
lastmod: 2026-08-17
og_description: Helyezze be az OleControlType.CommandButton példát a Wordbe az Aspose.Words
  segítségével. Kövesse ezt az útmutatót a űrlapvezérlők Word dokumentumba való hozzáadásához.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: OleControlType.CommandButton példa beszúrása Wordben
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: OleControlType.CommandButton példa beszúrása Wordbe
url: /hu/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OleControlType.CommandButton példa beszúrása Word-be

Ha **insert OleControlType.CommandButton example**-t szeretne beszúrni egy Word fájlba, ez az útmutató megmutatja, hogyan teheti. Megtanulja, **hogyan adjon űrlapvezérlőket egy Word dokumentumhoz** az Aspose.Words használatával, egy teljes, futtatható C# programmal.

Az űrlapvezérlők, például az ActiveX gombok lehetővé teszik interaktív Word sablonok létrehozását—hasznos szerződésekhez, kérdőívekhez vagy belső eszközökhöz. Az alábbi lépések mindent lefednek a projekt beállításától a gomb helyes megjelenésének ellenőrzéséig a mentett `.docx` fájlban.

## Előkövetelmények

- .NET 6.0 SDK vagy újabb telepítve  
- Visual Studio 2022 (vagy bármely C# IDE)  
- Aspose.Words for .NET licenc vagy egy ingyenes ideiglenes licenc  
- Alapvető ismeretek a C# és a Word fájlok koncepcióiról  

> **Pro tipp:** Ha az ingyenes próbaverziót használja, helyezze a licencfájlt ugyanabba a mappába, mint a futtatható állomány, és töltse be a `Main` elején.

## 1. lépés: Új konzolos projekt létrehozása és az Aspose.Words hozzáadása

Nyisson egy terminált, és futtassa:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Ez létrehoz egy tiszta projektet, és letölti a legújabb Aspose.Words csomagot, amely biztosítja a `Document`, `DocumentBuilder` és `InsertForms2OleControl` API-kat, amelyek a **insert OleControlType.CommandButton example**-hez szükségesek.

## 2. lépés: Írja meg a teljes programot

Hozzon létre vagy cserélje le a `Program.cs`-t a következő kóddal. Tartalmazza az összes szükséges `using` direktívát, a licenc betöltését, és az eredeti részletben bemutatott négylépéses munkafolyamatot.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Miért fontos minden sor

* **License loading** – biztosítja, hogy ne legyen korlátozva az értékelési korlátozások által.  
* **`Document doc = new Document();`** – létrehozza a tárolót az összes Word tartalom számára; ez a **insert OleControlType.CommandButton example** alapja.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – folyékony API-t biztosít szöveg, kép és vezérlők hozzáadásához.  
* **`InsertForms2OleControl`** – a központi metódus, amely megvalósítja, **hogyan adjon űrlapvezérlőket egy Word dokumentumhoz**. Az `OleControlType.CommandButton` enum érték azt mondja az Aspose.Words-nek, hogy hozzon létre egy ActiveX gombot.  
* **`new Rectangle(100, 100, 80, 30)`** – a gombot 100 pt-re helyezi a bal és felső margótól, 80 pt szélességgel és 30 pt magassággal. Igazítsa ezeket a számokat a saját elrendezéséhez.  
* **`doc.Save`** – a .docx fájlt a lemezre írja; a fájl most már tartalmazza a beágyazott gombot.

## 3. lépés: A program felépítése és futtatása

A projekt mappájából futtassa:

```bash
dotnet run
```

A konzolon a következő üzenetet kell látnia:

```
Document saved to ActiveXButton.docx
```

Nyissa meg az `ActiveXButton.docx`-t a Microsoft Wordben. Egy **ClickMe** feliratú gombot fog látni, amely nagyjából az oldal közepén helyezkedik el. A gomb megnyomása az alapértelmezett ActiveX viselkedést indítja el (ami általában semmit sem csinál, hacsak nem csatol makrót).

![insert olecontroltype.commandbutton példa](/images/activex-button.png "ActiveX CommandButton beillesztve egy Word dokumentumba")

*Kép alternatív szövege:* insert olecontroltype.commandbutton példa – egy ActiveX CommandButton, amely egy Word dokumentumban jelenik meg.

## 4. lépés: A gomb testreszabása (opcionális)

Az alap **insert OleControlType.CommandButton example** egy alapértelmezett gombot hoz létre. Módosíthatja a feliratát, betűtípusát, vagy akár makrót is csatolhat az alatta lévő OLE objektum szerkesztésével. Az alábbiakban egy tömör módja látható a gomb feliratának módosítására a beszúrás után:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Megjegyzés:** Az OLE tulajdonságok közvetlen manipulálása az alatta lévő COM interfész megértését igényli. A legtöbb esetben az alapértelmezett felirat elegendő.

## 5. lépés: Gyakori buktatók és azok elkerülése

| Probléma | Miért fordul elő | Javítás |
|----------|------------------|---------|
| A gomb nem jelenik meg Wordben | A dokumentum `.docx`-ként lett mentve, de egy olyan megjelenítőben nyitották meg, amely eltávolítja az OLE vezérlőket (pl. Google Docs). | Nyissa meg a fájlt a Microsoft Wordben vagy a Word Onlineban szerkesztési jogosultsággal. |
| Futásidejű hiba `ArgumentOutOfRangeException` | A `Rectangle` koordináták a lap margóin kívül vannak. | Használjon értékeket a lap méretén belül (pl. 0‑500 A4-hez). |
| Licenckivétel | A próbaverzió licencje 30 nap után lejár. | Töltsön be egy érvényes licencfájlt, vagy kérjen meghosszabbított próbaverziót az Aspose-tól. |

## 6. lépés: Hogyan illeszkedik ez a példa nagyobb automatizálási projektekbe

Amikor nagy léptékben kell **how to add form controls to Word document**-et végrehajtani — például több száz szerződés sablon generálásakor — csomagolja a beszúrási logikát egy újrahasználható metódusba:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Ezután meghívhatja az `AddCommandButton`-t ciklusokban, amelyek adat sorokat dolgoznak fel, biztosítva, hogy minden generált dokumentum egyedi nevű gombot tartalmazzon (pl. `Approve_001`, `Approve_002`).

## Következtetés

Most már rendelkezik egy teljes **insert OleControlType.CommandButton example** példával, amely bemutatja, **hogyan adjon űrlapvezérlőket egy Word dokumentumhoz** az Aspose.Words for .NET használatával. Az útmutató lefedte a projekt beállítását, a teljes forráskódot, a testreszabási tippeket és a gyakori hibaelhárítási lépéseket.

Innen tovább felfedezheti:

- Más vezérlő típusok hozzáadása, például **CheckBox** vagy **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- A gomb VBA makróhoz kötése a gazdagabb interaktivitás érdekében.  
- PDF-ek generálása ugyanabból a dokumentumból a űrlapmezők megőrzésével.

Kísérletezzen különböző méretekkel, pozíciókkal és vezérlőnevekkel, hogy megfeleljen a konkrét felhasználási esetnek. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Combo Box űrlapmező beszúrása Word dokumentumba](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Check Box űrlapmező beszúrása Word dokumentumba](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Szöveges bemenet űrlapmező beszúrása Word dokumentumba](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}