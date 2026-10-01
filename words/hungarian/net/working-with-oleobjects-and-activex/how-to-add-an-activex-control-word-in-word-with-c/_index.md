---
category: general
date: 2026-09-30
description: Adj hozzá egy ActiveX vezérlőelemet egy Word dokumentumhoz C#-ban. Tanuld
  meg, hogyan szúrj be egy ActiveX gombot, adj hozzá egy parancsgombot, és tedd kattinthatóvá.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: hu
lastmod: 2026-09-30
og_description: Adj hozzá egy ActiveX vezérlőt egy Word dokumentumhoz C#-al. Kövesd
  ezt a teljes útmutatót az ActiveX gomb beszúrásához, egy parancsgomb hozzáadásához,
  és hogy kattintható legyen.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: ActiveX vezérlő hozzáadása Word dokumentumokhoz – lépésről lépésre C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Hogyan adjon hozzá egy ActiveX vezérlőt a Wordben C#‑al
url: /hu/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjon hozzá ActiveX vezérlő szót a Word dokumentumhoz C#‑al

Ha be kell ágyaznia egy **ActiveX vezérlő szót** egy Microsoft Word fájlba, ez az útmutató pontosan megmutatja, hogyan teheti meg. Látni fog egy teljes, futtatható példát, amely egy kattintható gombot szúr be, elmenti a dokumentumot, és a legújabb Aspose.Words for .NET‑et használja.

ActiveX vezérlő szó hozzáadásával interaktív űrlapokat, egyedi párbeszédablakokat vagy egyszerű UI elemeket hozhat létre, amelyek úgy viselkednek, mint a natív Word vezérlők. Akár egy szerződés sablont épít, amely felhasználói interakciót igényel, akár egy jelentést, amelynek “Futtatás” gombra van szüksége, az alábbi lépések mindent lefednek, amire szüksége van.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik a következőkkel:

* .NET 6.0 SDK vagy újabb (a kód .NET Framework 4.8‑al is működik)
* Visual Studio 2022 (vagy bármely IDE, amely támogatja a C#‑t)
* Aspose.Words for .NET telepítve (`dotnet add package Aspose.Words`)
* Alapvető C# ismeretek és Word dokumentum struktúra

> **Pro tipp:** Az `InsertForms2OleControl` metódus csak a régi “Forms 2.0” vezérlőkkel működik, amelyek a Word által az űrlapmezőkhöz használt ActiveX vezérlők. Ha újabb Office verziókat céloz meg, a vezérlő továbbra is helyesen jelenik meg az asztali kliensben.

## 1. lépés: A projekt beállítása és névtér importálása

Hozzon létre egy új konzolos projektet, és adja hozzá a szükséges `using` utasításokat. Ez biztosítja, hogy a fordító megtalálja a `Document`, `DocumentBuilder` és `OleControlType` osztályokat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Az `Aspose.Words` névtér magas szintű API‑kat biztosít a Word feldolgozásához, míg az `Aspose.Words.Drawing` tartalmazza az `OleControlType` felsorolást, amely a kívánt ActiveX vezérlő típusának megadásához szükséges.

## 2. lépés: A forrás Word dokumentum betöltése

Először egy módosítani kívánt Word fájlt kell megnyitnia. Az alábbi kód betölti az `input.docx` fájlt egy ön által megadott mappából.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Ha a fájl nem létezik, az Aspose.Words `FileNotFoundException`‑t dob. Ha szeretne elegáns hibakezelést, csomagolja a hívást egy `try/catch` blokkba.

## 3. lépés: DocumentBuilder létrehozása a dokumentum szerkesztéséhez

A `DocumentBuilder` a szöveg, kép és vezérlők beszúrásáért felelős munkagépe. Egy kurzort tart, amely azt a helyet jelöli, ahová a következő elem kerül.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Alapértelmezés szerint a builder kurzora az első szakasz elején helyezkedik el. Mozgathatja a `MoveToDocumentEnd()` vagy `MoveToParagraph(index)` metódusokkal, ha máshová szeretné a gombot.

## 4. lépés: ActiveX CommandButton vezérlő beszúrása

Most jön a tutorial középpontja: egy **ActiveX vezérlő szó** beszúrása, amely kattintható gombként jelenik meg. Az `InsertForms2OleControl` metódus két argumentumot vár – a vezérlő típusát és egy feliratot (vagy nevet) a vezérlőhöz.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Miért használjuk az `OleControlType.CommandButton`‑t?**  
  Ez azt mondja a Wordnek, hogy hozzon létre egy klasszikus Forms 2.0 parancsgombot, amely feliratot jelenít meg, és később makróhoz vagy VBA‑szkripthez csatlakoztatható.

* **Mit csinál a felirat?**  
  A `"ClickMe"` karakterlánc a gomb látható szövegévé válik. Bármire módosítható, ami illik a felhasználói felületéhez.

### A gomb beszúrása egy adott helyre

Ha a gombot egy konkrét bekezdés után szeretné, előbb mozgassa a builder‑t:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## 5. lépés: A módosított dokumentum mentése

A vezérlő beszúrása után mentse a változtatásokat egy új fájlba (vagy írja felül az eredetit).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Amikor megnyitja az `output.docx`‑et a Word asztali verziójában, a **ClickMe** (vagy a megadott felirat, például **Submit**) felirattal ellátott gombot fogja látni. Alapértelmezés szerint a tervező módban a gomb kattintása nem csinál semmit; később makrót rendelhet hozzá a Word “Developer” (Fejlesztő) lapján.

## Teljes, futtatható példa

Az alábbi önálló program bemutatja a teljes munkafolyamatot. Másolja be egy új konzolos alkalmazás `Program.cs` fájljába, és futtassa.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Várt kimenet

* A konzol kiírja a sikerüzenetet a kimeneti útvonallal.
* Az `output.docx` megnyitásakor egy **ClickMe** gomb jelenik meg azon a helyen, ahol a builder beszúrta.
* A gomb kiválasztható, átméretezhető, vagy makróhoz rendelhető a Word **Developer → Design Mode** (Fejlesztő → Tervező mód) segítségével.

## Gyakori kérdések és speciális esetek kezelése

| Kérdés | Válasz |
|----------|--------|
| **Hogyan szúrhatok be ActiveX gombot a fejlécre/láblécre?** | A builder‑t mozgassa a fejlécre/láblécre a `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` hívással, mielőtt meghívná az `InsertForms2OleControl`‑t. |
| **Mi van, ha jelölőnégyzetet szeretnék gomb helyett?** | Használja az `OleControlType.CheckBox`‑t, és adjon meg egy feliratot, például `"Agree"`. |
| **Működik a gomb a Word Online‑ban?** | Nem. A Word Online nem támogatja a régi Forms 2.0 ActiveX vezérlőket. A gomb csak az asztali kliensben jelenik meg. |
| **Be tudom-e állítani a gomb méretét programból?** | Beszúrás után szerezze meg a `Shape` objektumot a `builder.CurrentParagraph.Runs[0].GetShape()`‑vel, és állítsa be a `Width`/`Height` értékeket. |
| **Lehet-e makrót hozzárendelni kódból?** | Az Aspose.Words nem biztosít makró szerkesztési lehetőséget. A dokumentumot Wordben kell megnyitni, és manuálisan makrót csatolni, vagy az Office Interop API‑t használni. |

## Tippek a termelésben való használathoz

* **Kerülje a keményen kódolt útvonalakat** – használjon `Path.Combine`‑t és konfigurációs fájlokat.
* **A `Document` erőforrás felszabadítása** – nagy fájlok esetén csomagolja `using` blokkba, hogy a memória időben felszabaduljon.
* **Ellenőrizze a kimenetet** – programból ellenőrizheti, hogy a dokumentum tartalmaz‑e `OleControl` típusú alakzatot a `doc.GetChildNodes(NodeType.Shape, true)` iterálásával.
* **Biztonsági megjegyzés** – az ActiveX vezérlők kódot futtathatnak a kliens gépen. Csak megbízható felhasználóknak terjessze a dokumentumot, és fontolja meg a digitális aláírások használatát.

## Összegzés

Most már tudja, hogyan adjon hozzá egy **ActiveX vezérlő szót** egy Word dokumentumhoz C#‑al. Dokumentum betöltésével, `DocumentBuilder` létrehozásával, `InsertForms2OleControl`‑dal egy parancsgomb beszúrásával és a fájl mentésével automatizálhatja az interaktív Word űrlapok létrehozását. Kísérletezzen más `OleControlType` értékekkel, helyezze a vezérlőket fejlécekbe vagy táblázatokba, és kombinálja őket makrókkal a gazdagabb felhasználói élményért.

---

*Következő lépések*: fedezze fel **hogyan szúrjon be más típusú ActiveX** vezérlőket, tanulja meg **hogyan adjon hozzá parancsgomb eseménykezelőket VBA‑val**, és olvassa el a **ActiveX gomb beszúrása** legjobb gyakorlatait a kereszt‑platform kompatibilitás érdekében.


## Mit érdemes még tanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [OLE objektumok és ActiveX vezérlők beágyazása Word dokumentumokba](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Combo Box űrlapmező hozzáadása Word dokumentumhoz Aspose.Words for .NET‑el](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Check Box űrlapmező hozzáadása Word dokumentumhoz Aspose.Words for .NET‑el](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}