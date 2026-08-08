---
category: general
date: 2026-08-07
description: Jak seskupit tvary ve Wordu s Aspose.Words a přidat tvary do dokumentu
  Word pomocí C#. Postupujte podle tohoto krok‑za‑krokem průvodce pro čistý, znovupoužitelný
  kód.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: cs
lastmod: 2026-08-07
og_description: Jak seskupit tvary ve Wordu pomocí Aspose.Words pro .NET. Tento tutoriál
  vám ukáže, jak přidat tvary do dokumentu Word, seskupit je a uložit soubor pomocí
  přehledného C# kódu.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Jak seskupit tvary ve Wordu – rychlý průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Jak seskupit tvary ve Wordu a přidat tvary do dokumentu Word
url: /cs/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary ve Wordu a přidat tvary do dokumentu Word

Pokud potřebujete **how to group shapes in Word**, tento průvodce vás provede kompletním procesem pomocí Aspose.Words pro .NET. Také se naučíte **add shapes to Word document** pomocí několika řádků C# kódu, takže výsledek je připravený pro jakýkoli reporting nebo templating scénář.

Tutoriál pokrývá vše, co potřebujete: požadované NuGet balíčky, celý zdrojový soubor a vysvětlení, proč je každý krok důležitý. Na konci budete schopni vygenerovat DOCX, který obsahuje obdélník a elipsu sloučené do jediné skupiny tvarů.

## Předpoklady

Než začnete, ujistěte se, že máte:

* .NET 6.0 SDK nebo novější nainstalováno  
* Visual Studio 2022 (nebo jakékoli IDE podporující .NET)  
* Aspose.Words for .NET NuGet package (`Aspose.Words`) – bezplatná zkušební verze funguje pro testování, ale licence odstraňuje vodotisk hodnocení  

Tyto položky jsou jedinými externími závislostmi pro **add shapes to Word document**.

## Jak seskupit tvary ve Wordu

Jádrem řešení je vytvořit jednotlivé tvary, umístit je na stránku a poté je zabalit do `GroupShape`. Následující kroky odrážejí logické pořadí kódu.

### Krok 1: Vytvořte dokument a builder

Objekt `Document` představuje celý soubor DOCX. `DocumentBuilder` poskytuje pohodlné API pro úpravu dokumentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité*: `Document` je kontejner pro všechny elementy Wordu. `DocumentBuilder` sleduje aktuální pozici kurzoru, což je potřeba při následném vložení seskupeného tvaru.

### Krok 2: Přidejte obdélníkový tvar

Obdélník se vytvoří zadáním `ShapeType.Rectangle`. Šířka, výška a umístění jsou nastaveny v bodech (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Proč je to důležité*: Nastavení `StrokeColor` způsobí, že tvar bude viditelný po otevření dokumentu. Můžete také vyplnit tvar pomocí `FillColor`, pokud je požadována plná výplň.

### Krok 3: Přidejte eliptický tvar

Elipsa používá `ShapeType.Ellipse`. Její velikost a pozice jsou nezávislé na obdélníku, což vám umožní řídit finální rozložení skupiny.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Proč je to důležité*: Umístěním elipsy na `Left = 120` se nepřekrývá s obdélníkem, což dělá skupinu vizuálně odlišnou.

### Krok 4: Seskupte oba tvary

`GroupShape` funguje jako kontejner, který zachází s jeho potomky jako s jedním objektem. Toto je klíčová operace pro **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Proč je to důležité*: Seskupení umožňuje přesouvat, měnit velikost nebo otáčet oba tvary najednou. Jakákoli transformace aplikovaná na `groupShape` se propaguje na jeho děti.

### Krok 5: Vložte seskupený tvar do dokumentu

`DocumentBuilder.InsertNode` umístí `GroupShape` na aktuální pozici kurzoru. Protože jsme builder nepřesunuli, skupina se objeví na začátku první stránky.

```csharp
builder.InsertNode(groupShape);
```

*Proč je to důležité*: Vložení uzlu přímo eliminuje potřebu samostatného odstavce nebo buňky tabulky. Skupina se stane součástí toku dokumentu.

### Krok 6: Uložte dokument

Nakonec zapíšete soubor DOCX na disk. Použijte úplnou cestu, do které může vaše aplikace zapisovat.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Proč je to důležité*: `doc.Save` finalizuje všechny změny. Výsledný soubor lze otevřít v Microsoft Word, LibreOffice nebo v jakémkoli prohlížeči podporujícím DOCX.

## Kompletní zdrojový soubor

Zkopírujte níže uvedený kód do nového konzolového projektu (`dotnet new console`) a spusťte jej. Program vytvoří soubor s názvem `GroupShape.docx`, který obsahuje seskupený obdélník a elipsu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Očekávaný výstup

Otevřete `GroupShape.docx`. Uvidíte jediný vizuální objekt, který obsahuje modrý obdélník vlevo a zelenou elipsu vpravo. Výběrem objektu ve Wordu se zvýrazní oba tvary současně – důkaz, že **how to group shapes in Word** byl úspěšný.

## Časté otázky a okrajové případy

* **Mohu přidat více než dva tvary?**  
  Ano. Zavolejte `groupShape.AppendChild` pro každý další `Shape` před vložením skupiny.

* **Co když potřebuji otočit skupinu?**  
  Nastavte `groupShape.RotationAngle = 45;` (úhel ve stupních) po vytvoření skupiny.

* **Musím volat `doc.UpdatePageLayout()`?**  
  Ne pro tento scénář. Rozvržení se automaticky aktualizuje při uložení dokumentu.

* **Jak licence ovlivňuje kód?**  
  S platnou licencí Aspose.Words (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) vygenerovaný dokument neobsahuje žádný evaluační vodotisk.

## Závěr

Nyní víte **how to group shapes in Word** a **add shapes to Word document** pomocí Aspose.Words pro .NET. Tutoriál pokryl vytvoření dokumentu, definování jednotlivých tvarů, jejich seskupení, vložení skupiny a uložení souboru.  

Odtud můžete experimentovat s:

* Přidání textových polí nebo obrázků do skupiny  
* Změna výplňových barev, stylů čar nebo stínových efektů  
* Seskupování tvarů uvnitř tabulek nebo záhlaví  

Tyto rozšíření vám umožní programově vytvářet sofistikované šablony Wordu při zachování čistého a udržovatelného kódu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vytvořit skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vložit tvary do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvořit dokument Word s Aspose.Words – krok za krokem průvodce](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}