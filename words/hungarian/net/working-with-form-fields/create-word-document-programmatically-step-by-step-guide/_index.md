---
category: general
date: 2026-08-04
description: Hozzon létre Word-dokumentumot programozottan C#-ban. Tanulja meg, hogyan
  adhat hozzá programozottan parancsgombot az Aspose.Words segítségével néhány lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: hu
lastmod: 2026-08-04
og_description: Word dokumentum létrehozása programozott módon az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan lehet programozottan parancsgombot hozzáadni, beállítani,
  és elmenteni a fájlt.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Word dokumentum létrehozása programozottan – teljes C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word-dokumentum létrehozása programozottan – lépésről lépésre útmutató
url: /hu/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum programozott létrehozása – teljes C# útmutató

Ha **programozott módon szeretnél Word dokumentumot létrehozni**, ez az útmutató pontosan megmutatja, hogyan teheted ezt meg az Aspose.Words for .NET segítségével. Néhány C# sorral generálhatsz egy üres `.docx` fájlt, **programozott módon hozzáadhatsz parancsgomb** vezérlőket, beállíthatod azok tulajdonságait, és elmentheted az eredményt.  

Az alábbi lépések mindent lefednek a projekt beállításától a szélhelyzetek kezeléséig, így a kódot egyszerűen átmásolhatod a saját alkalmazásodba, és módosítás nélkül futtathatod.

## Mit fogsz elérni

* Új Word dokumentum inicializálása kizárólag memóriában.  
* **Programozott módon hozzáadni parancsgomb** OLE vezérlőket tetszőleges helyen és méretben.  
* A gomb feliratának, belső nevének és egyéb OLE tulajdonságainak beállítása.  
* A generált dokumentum mentése lemezre vagy streambe további feldolgozáshoz.

### Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑vel is működik).  
* Érvényes Aspose.Words for .NET licenc (vagy ingyenes értékelő verzió).  
* Alapvető ismeretek C#‑ban és Visual Studio‑ban (vagy bármely kedvenc IDE‑ben).  

> **Pro tipp:** Ha licenc nélkül futtatod a példát, az Aspose.Words egy kis értékelő vízjelet ad az első oldalra.

## 1. lépés: A projekt beállítása és a szükséges névterek importálása

Hozz létre egy új Console App‑ot (vagy integráld egy meglévő szolgáltatásba), és add hozzá az Aspose.Words NuGet csomagot:

```bash
dotnet add package Aspose.Words
```

Ezután importáld a szükséges névtereket a `.cs` fájlod tetején:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ezek az importok hozzáférést biztosítanak a `Document`, `DocumentBuilder`, `Forms2OleControl` és a pozicionáláshoz használt `RectangleF` struktúrához.

## 2. lépés: Új Word dokumentum inicializálása

Az első művelet minden **programozott Word dokumentum létrehozása** munkafolyamatban egy `Document` objektum példányosítása. Ez az objektum csak memóriában létezik, amíg kifejezetten el nem mented.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` úgy működik, mint egy kurzor, amely nyomon követi, hová kerül a következő elem. Ennek használata tömör kódot eredményez, és tükrözi azt a módot, ahogyan közvetlenül a Wordben írnál.

## 3. lépés: Parancsgomb OLE vezérlő beszúrása

Az Aspose.Words biztosítja az `InsertForms2OleControl` metódust OLE objektumok, például parancsgombok, jelölőnégyzetek vagy kombinált listák beágyazásához. A metódus három argumentumot igényel:

1. A `ControlType` enum értéke (itt `CommandButton`).  
2. Egy `RectangleF`, amely meghatározza a vezérlő X‑Y pozícióját és szélesség‑magasságát (pontban mérve, ahol 72 pt = 1 inch).  
3. Opcionálisan további OLE tulajdonságok (az alap gombhoz nem szükséges).  

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Miért működik:** Az `InsertForms2OleControl` egy OLE konténert hoz létre a dokumentumban, és visszaad egy `Forms2OleControl` burkolót. A burkoló lehetővé teszi, hogy az alatta lévő OLE objektumot (a tényleges gombot) manipuláld anélkül, hogy alacsony szintű COM interop‑tal kellene foglalkoznod.

## 4. lépés: A gomb feliratának és belső nevének beállítása

Beszúrás után általában szeretnél egy felhasználó számára látható címkét és egy belső azonosítót adni a gombnak, amelyet a makró vagy kiegészítő később hivatkozhat.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` a gombon megjelenő szöveg a Word felhasználói felületén.  
* `Name` a programozási azonosító, amelyet a VBA vagy külső automatizációs szkriptek használnak.

### Opcionális: Makró hozzárendelése a gombhoz

Ha azt tervezed, hogy a gomb kattintásakor VBA makrót futtass, csatolhatod a makró nevét:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Szélhelyzet:** Ha a cél dokumentumot olyan gépen nyitják meg, ahol nincs a makró, a Word biztonsági figyelmeztetést jelenít meg. Mindig írd alá a makrókat, vagy tájékoztasd a felhasználókat a szükséges beállításokról.

## 5. lépés: A dokumentum mentése

A fájlt lemezre, egy `MemoryStream`‑be vagy közvetlenül egy web API válaszobjektumba is írhatod. A legegyszerűbb megközelítés egy konzolos demóhoz, ha egy helyi mappába mented:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Az eredményül kapott `.docx` a Microsoft Wordben megnyílik egy működő parancsgombbal, amely a „Click Me” feliratot mutatja. A gomb kattintása elindítja a hozzárendelt makrót (ha van), vagy egyszerűen egy alapértelmezett üzenetet jelenít meg.

## Teljes működő példa

Másold a következő programot a `Program.cs` fájlba, és futtasd. Bemutatja a teljes **programozott Word dokumentum létrehozása** folyamatot, beleértve a hibakezelést is.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Várt eredmény:** A `CommandButton.docx` megnyitása Wordben egy „Click Me” feliratú gombot mutat. A gomb fölé húzva megjelenik a `cmdClickMe` név a tulajdonságok panelen.

## Gyakori kérdések és hibaelhárítás

| Kérdés | Válasz |
|----------|--------|
| *Hozzáadhatok a gombot egy meglévő dokumentumhoz?* | Igen. Töltsd be a fájlt a `new Document("Existing.docx")` segítségével, majd használd ugyanazt az `InsertForms2OleControl` hívást. |
| *Milyen egységet használ a `RectangleF`?* | Pontok (1 inch = 72 pt). Állítsd be az értékeket a gomb pontos pozicionálásához. |
| *Működni fog a gomb a Word for Mac‑on?* | Az OLE vezérlők csak a Windows Wordben támogatottak. Mac‑en a gomb statikus képként jelenik meg. |
| *Szükségem van licencre a termelésben való használathoz?* | A kereskedelmi licenc eltávolítja az értékelő vízjeleket és feloldja a teljes funkcionalitást. |
| *Hogyan változtathatom meg a gomb méretét a beszúrás után?* | Módosítsd a `commandButton.Width` és `commandButton.Height` értékeket, vagy szúrd be újra egy új `RectangleF`‑el. |

## A megoldás bővítése

Most, hogy tudod, hogyan **programozott módon adj hozzá parancsgomb** vezérlőket, felfedezheted a kapcsolódó témákat:

* **Más űrlapvezérlők beszúrása** – használd a `ControlType.CheckBox`, `ControlType.OptionButton` stb. (magában foglalja a *Aspose.Words InsertForms2OleControl* másodlagos kulcsszót).  
* **A dokumentum feltöltése dinamikus adatokkal** – adatbázisból származó adatokat egyesíts táblákba vagy levélösszevonási mezőkbe.  
* **Exportálás PDF‑be** – a gomb hozzáadása után hívd meg a `doc.Save("output.pdf", SaveFormat.Pdf)` metódust a PDF verzió előállításához (kapcsolódik a *C# Word automation* témához).  

## Összegzés

Most már egy teljes, termelésre kész mintát rendelkezel a **programozott Word dokumentum létrehozásához** és a **programozott módon parancsgomb hozzáadásához** az Aspose.Words for .NET használatával. Az útmutató lefedte a projekt beállítását, a dokumentum inicializálását, az OLE gomb beszúrását, a tulajdonságok konfigurálását és a fájl mentését. Nyugodtan adaptáld a kódot más űrlapvezérlők beszúrásához, makrók csatolásához, vagy a logika integrálásához webszolgáltatásokba vagy háttérfeladatokba.

Boldog kódolást, és élvezd a Word dokumentumok automatizálását!

## Mit érdemes következőként megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Aspose.Words‑szal – lépésről‑lépésre útmutató](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Word dokumentum létrehozása táblázattal Aspose.Words használatával](/words/english/net/add-content-using-document-builder/build-table/)
- [Csoport alakzat létrehozása Word dokumentumban Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}