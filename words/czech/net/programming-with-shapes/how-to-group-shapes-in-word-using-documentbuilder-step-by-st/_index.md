---
category: general
date: 2026-09-08
description: Naučte se seskupovat tvary ve Wordu pomocí DocumentBuilderu, vytvořit
  prázdný dokument Word a vložit obdélníkový tvar pomocí několika řádků kódu v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: cs
lastmod: 2026-09-08
og_description: Seskupování tvarů ve Wordu pomocí DocumentBuilderu. Tento tutoriál
  ukazuje, jak vytvořit prázdný dokument Word, vložit obdélníkový tvar a sloučit tvary
  do GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Seskupení tvarů ve Wordu pomocí DocumentBuilder – kompletní příklad v C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak seskupit tvary ve Wordu pomocí DocumentBuilder – průvodce krok za krokem
url: /cs/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary ve Wordu pomocí DocumentBuilder – krok za krokem průvodce

Pokud potřebujete **seskupit tvary ve Wordu** programově, tento tutoriál ukazuje kompletní řešení v C#. Uvidíte, jak **vytvořit prázdný Word dokument**, použít **DocumentBuilder** a **vložit obdélníkový tvar** před jeho seskupením s elipsou. Výsledkem je jediný `GroupShape`, který můžete přesouvat, měnit jeho velikost nebo stylovat jako jeden objekt.

Tento průvodce pokrývá vše, co potřebujete vědět k vytvoření Word dokumentu se seskupenou grafikou pomocí knihovny Aspose.Words pro .NET. Na konci článku budete mít spustitelný projekt, který vytvoří `GroupedShapes.docx` obsahující obdélník a elipsu sloučené do jednoho tvaru.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7.2+)
- NuGet balíček Aspose.Words pro .NET (`Aspose.Words`) – verze 23.12 nebo novější
- IDE pro C#, např. Visual Studio 2022 nebo Visual Studio Code
- Základní znalost syntaxe C# a objektově orientovaného programování

> **Tip:** Nainstalujte NuGet balíček z příkazové řádky, abyste udrželi svůj projekt přehledný:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Krok 1: Vytvořit prázdný Word dokument

Prvním krokem je vytvořit objekt `Document`, který představuje prázdný Word soubor, a `DocumentBuilder`, který umožňuje přidávat obsah.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Proč je to důležité:** `Document` poskytuje kontejner souboru, zatímco `DocumentBuilder` nabízí plynulé API pro vkládání textu, obrázků a tvarů. Bez `DocumentBuilder` byste museli manipulovat s uzlovým stromem dokumentu ručně, což je náchylné k chybám.

## Krok 2: Vložit obdélníkový tvar

Obdélník je běžný stavební prvek diagramů. Použijte `InsertShape` s `ShapeType.Rectangle` a zadejte šířku a výšku v bodech (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Proč je to důležité:** Nastavení `Left` a `Top` umístí obdélník přesně na stránku, což je nezbytné, když jej později seskupíte s dalšími tvary. Metoda `InsertShape` automaticky přidá tvar do aktuálního odstavce.

## Krok 3: Vložit eliptický tvar

Dále přidejte elipsu, která bude umístěna vedle obdélníku.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Proč je to důležité:** Použití jiného `ShapeType` ukazuje, jak může stejné API `DocumentBuilder` vytvářet různé grafiky. Umístění elipsy tak, aby se překrývala s obdélníkem, zdůrazní efekt seskupení.

## Krok 4: Seskupit oba tvary

`GroupShape` funguje jako kontejner. Přidáním obdélníku a elipsy jako podřízených objektů se chovají jako jeden objekt.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Proč je to důležité:** Vlastnost `Bounds` říká Wordu, kde se skupina nachází na stránce. Přidáním podřízených tvarů zachováte jejich individuální formátování a umožníte kolektivní transformace (přesun, otočení, změna velikosti).

## Krok 5: Uložit dokument

Nakonec dokument zapíšete na disk. Cestu můžete změnit na libovolnou složku.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Když otevřete `GroupedShapes.docx` v Microsoft Wordu, uvidíte obdélník a elipsu seskupené dohromady. Výběrem skupiny zvýrazníte oba tvary, což vám umožní je táhnout nebo měnit jejich velikost jako jeden celek.

### Očekávaný výstup

- Word soubor pojmenovaný **GroupedShapes.docx**
- První stránka obsahuje **obdélník** (100 pt × 50 pt) na pozici (50, 50)
- **Elipsu** (80 pt × 80 pt) na pozici (200, 70)
- Oba tvary jsou součástí **GroupShape** s ohraničujícím rámečkem 300 pt × 200 pt

## Běžné varianty a okrajové případy

| Scenario | Adjustment |
|----------|------------|
| **Různá velikost stránky** | Nastavte `document.Sections[0].PageSetup.PageWidth` a `PageHeight` před vložením tvarů. |
| **Více než dva tvary** | Vytvořte další objekty `Shape` a pro každý zavolejte `groupShape.AppendChild(newShape)`. |
| **Použít barvu výplně** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Otočit skupinu** | `groupShape.Rotation = 45;` (degrees) |
| **Exportovat do PDF** | Po uložení DOCX zavolejte `document.Save("GroupedShapes.pdf");` |

## Kompletní zdrojový kód (připravený ke spuštění)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Zkopírujte kód do nového konzolového projektu, obnovte NuGet balíček Aspose.Words a spusťte. Konzole potvrdí umístění souboru a otevření souboru zobrazí seskupenou grafiku.

## Závěr

Nyní víte **jak seskupit tvary ve Wordu** pomocí Aspose.Words `DocumentBuilder`. Tutoriál vás provedl vytvořením **prázdného Word dokumentu**, **vložením obdélníkového tvaru**, přidáním elipsy a jejich sloučením do `GroupShape`. S tímto základem můžete vytvářet bohatší diagramy, vývojové diagramy nebo vlastní grafiku přímo z C#.

### Co dál?

- Prozkoumejte **jak používat DocumentBuilder** pro tabulky, záhlaví a zápatí.
- Kombinujte techniky **insert rectangle shape Word** s textovými poli pro anotované diagramy.
- Použijte **create blank word doc** jako šablonu pro automatizovanou tvorbu reportů.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit skupinový tvar ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vložit tvary do Word dokumentů pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}