---
category: general
date: 2026-08-17
description: Hogyan adjunk hozzá ActiveX vezérlőket és illesszünk be egy kördiagramot
  egy Word dokumentumba az Aspose.Words segítségével. Egy szelet kiemelése és mentése
  DOCX formátumban néhány lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: hu
lastmod: 2026-08-17
og_description: Hogyan adhatunk hozzá ActiveX vezérlőket, szúrhatunk be kördiagramot,
  szétrobbanthatunk egy szeletet, és menthetünk DOCX formátumban az Aspose.Words segítségével
  – teljes lépésről lépésre útmutató.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Hogyan adjon hozzá ActiveX-et, és szúrjon be egy kördiagramot egy Word-dokumentumba
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Hogyan adjon hozzá ActiveX-et, és szúrjon be egy kördiagramot egy Word-dokumentumba
url: /hu/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjon hozzá ActiveX-et és szúrjon be egy kördiagramot egy Word dokumentumba

Ha **hogyan adjon hozzá ActiveX** vezérlőket és ágyazzon be egy diagramot egy Word dokumentumba, ez a bemutató egy teljes, futtatható megoldást mutat. Az Aspose.Words segítségével elhelyezhet egy ActiveX **CommandButton**-t, létrehozhat egy kördiagramot, kiemelhet egy szeletet, és végül **DOCX-ként menthet** csak néhány C# sorral.

Az alábbi szakaszokban megtekintheti minden szükséges importot, egy teljes kódlistát, valamint azt, hogy miért fontos az egyes lépések. A végére képes lesz interaktív vezérlőket és vizuális adatokat integrálni bármely programból generált .docx fájlba.

## Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.7+ esetén is működik)
* Aspose.Words for .NET csomag (elérhető a NuGet-en keresztül)
* Fejlesztői környezet, például Visual Studio 2022 vagy VS Code
* Alapvető ismeretek a C#-ról és a Word objektummodellről

Nem szükséges további harmadik féltől származó diagramkönyvtár – az Aspose.Words beépített diagramkészítést biztosít.

## ActiveX vezérlők hozzáadása az Aspose.Words segítségével

Az ActiveX vezérlők lehetővé teszik interaktív UI elemek közvetlen beágyazását egy Word fájlba. Ebben az útmutatóban egy **CommandButton**-t adunk hozzá, amely később VBA kóddal összekapcsolható.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Miért működik ez:**  
`InsertForms2OleControl` egy OLE konténert hoz létre, amelyet a Word felhasználói felület ActiveX vezérlőként ismer fel. A vezérlő típusának `CommandButton`-ra állítása és felirat megadása azt standard gombként viselkedővé teszi, amikor a felhasználó megnyitja a fájlt Wordben.

## Kördiagram beillesztése és szelet kiemelése

A diagramok hasznosak az adatok vizualizálásához a dokumentum elhagyása nélkül. Az alábbi lépések bemutatják, **hogyan szúrjon be diagramot**, és különösen egy **kördiagramot**, amelynek az első szelete ki van emelve.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Miért emeljük ki a szeletet:**  
A `SetExplode(0, true)` hívás azt mondja az Aspose.Words-nek, hogy az első adatpontot eltolja, így a néző szemét arra a szegmensre irányítja. Ez gyakori technika a prezentációkban a kulcsfontosságú érték kiemelésére.

## Mentés DOCX formátumban

Az ActiveX gomb és a diagram hozzáadása után a dokumentumot lemezre kell menteni. Ez a lépés bemutatja a **save as DOCX** használatát a szabványos módszerrel.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

A `Output.docx` fájl most már egy interaktív gombot, egy kiemelt szelettel rendelkező kördiagramot tartalmaz, és további pluginek nélkül nyitható meg a Microsoft Wordben.

## Teljes futtatható példa

Mindent összevonva, itt egy önálló program, amelyet bemásolhat egy konzolos alkalmazásba és azonnal futtathat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Várt eredmény:**  
A `Output.docx` megnyitása Wordben egy *Click Me* feliratú gombot és egy kördiagramot mutat, ahol az első szelet (January) el van tolva a többitől. A gomb készen áll a VBA eseménykezelésre, a diagram pedig szerkeszthető a Word beépített diagrameszközeivel.

## Gyakori kérdések és szélhelyzetek

* **Hozzáadhatok más ActiveX típusokat?**  
  Igen. Cserélje le a `Forms2OleControlType.CommandButton`-t bármely értékre a `Forms2OleControlType` enumerációból (pl. `CheckBox`, `OptionButton`). Ugyanaz a beszúrási minta érvényes.

* **Mi van, ha másik diagramtípust szeretnék?**  
  Használja a `ChartType.Bar`, `ChartType.Line` stb. értékeket az `InsertChart` hívásban. A **how to insert chart** lépés változatlan marad; csak az enumerációs érték változik.

* **Hogyan szabályozhatom a kiemelt szelet méretét?**  
  Az Aspose.Words jelenleg bináris kiemelési jelzőt (true/false) támogat. Finomabb vezérléshez (pl. eltolás távolsága) a mentés után az alap OOXML-t kell módosítani.

* **Kompatibilis-e a dokumentum a régebbi Word verziókkal?**  
  A DOCX formátumba mentés biztosítja a kompatibilitást a Word 2007 és újabb verziókkal. Word 2003 esetén a `SaveFormat.Doc`-ra váltás lehetséges, de az ActiveX támogatás korlátozott ebben a formátumban.

* **Szükséges-e hivatkozni a `System.Drawing`-ra?**  
  Nem. Minden rajzobjektumot az Aspose.Words biztosít, így az egyetlen szükséges NuGet csomag a `Aspose.Words`.

## Következtetés

Most már tudja, **hogyan adjon hozzá ActiveX-et**, **hogyan szúrjon be egy kördiagramot**, **hogyan emelje ki a körszeletet**, és **hogyan mentse DOCX-ként** az Aspose.Words for .NET segítségével. A teljes példa minden lépést lefed a dokumentum létrehozásától a végleges mentésig, és elmagyarázza az egyes API hívások mögötti logikát.

Ezután érdemes lehet:

* VBA makrók hozzáadása, amelyek a CommandButton kattintására reagálnak (**how to insert chart** és az adatfrissítések automatizálása)
* A diagram megjelenésének testreszabása (színek, adatcímkék) a vállalati arculathoz igazítva
* További ActiveX vezérlők beágyazása, például **ComboBox** vagy **ListBox** a gazdagabb űrlapokhoz

Kísérletezzen bátran a kóddal, cserélje le a mintaadatokat, és integrálja a megoldást saját dokumentum‑generálási folyamatába. Boldog kódolást!

## Mit kellene legközelebb megtanulnod?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Oszlopdiagram beillesztése Wordben az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-column-chart/)
- [Egyszerű oszlopdiagram beillesztése Wordben az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Buborékdiagram beillesztése Wordben az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}