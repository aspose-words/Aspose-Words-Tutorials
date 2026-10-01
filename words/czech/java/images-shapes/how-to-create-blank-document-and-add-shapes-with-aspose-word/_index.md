---
category: general
date: 2026-09-30
description: Vytvořte prázdný dokument a vložte obdélníkový tvar, elipsu a seskupte
  více tvarů v C# pomocí Aspose.Words. Naučte se, jak vkládat tvary a jak vytvořit
  skupinu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: cs
lastmod: 2026-09-30
og_description: Vytvořte prázdný dokument v C# a naučte se, jak vkládat tvary a seskupovat
  více tvarů pomocí Aspose.Words. Postupujte podle krok‑za‑krokem tutoriálu.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Vytvořte prázdný dokument a seskupte tvary v C# – průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Jak vytvořit prázdný dokument a přidat tvary pomocí Aspose.Words v C#
url: /cs/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument a přidat tvary pomocí Aspose.Words v C#

Pokud potřebujete **vytvořit prázdný dokument** a naplnit jej grafikou, tento průvodce vám ukáže přesně jak. Uvidíte, jak **vložit obdélníkový tvar**, přidat další kreslicí objekty a poté **seskupit více tvarů**, aby se chovaly jako jediná jednotka.

Práce s tvary je běžná požadavek při generování smluv, certifikátů nebo vlastních reportů. V tomto tutoriálu se naučíte kompletní workflow, od inicializace dokumentu až po uložení finálního souboru, pomocí Aspose.Words API pro .NET.

## Předpoklady

Než začnete, ujistěte se, že máte:

* .NET 6.0 (nebo novější) SDK nainstalované  
* Platnou licenci Aspose.Words pro .NET (pro tento příklad stačí bezplatná zkušební verze)  
* IDE, například Visual Studio 2022 nebo Visual Studio Code  

Žádné další NuGet balíčky nejsou potřeba nad rámec `Aspose.Words`.

## Jak vytvořit prázdný dokument a pracovat s tvary

Prvním krokem je vytvořit objekt `Document`. Tento objekt představuje Word soubor v paměti a poskytuje přístup k `DocumentBuilder`, který je hlavním nástrojem pro vkládání obsahu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Proč je to důležité:** Prázdný dokument vám dává čisté plátno. `DocumentBuilder` udržuje aktuální vkládací bod, takže každý tvar, který přidáte, je automaticky umístěn na správnou stránku.

## Vložit obdélníkový tvar a další tvary

Dále přidáme obdélník a elipsu. Oba volání používají stejnou metodu `InsertShape`, která je doporučeným způsobem **jak vložit tvary** v Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Metoda `InsertShape` automaticky umístí tvar na aktuální pozici kurzoru.* Pokud potřebujete přesné umístění, můžete po vložení upravit `Shape.Left` a `Shape.Top`.

## Seskupit více tvarů do jednoho objektu

Nyní spojíme obdélník a elipsu do jedné logické entity. Seskupování je užitečné, když chcete přesunout nebo změnit velikost několika tvarů najednou.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Jak to funguje:** `InsertGroupShape` vytvoří kontejner, který se chová jako jakýkoli jiný `Shape`. Voláním `AppendChild` přesunete existující tvary do kontejneru, který automaticky aktualizuje jejich relativní souřadnice.

### Praktický tip

Pokud později potřebujete **jak vytvořit skupinu** programově pro více než dva tvary, jednoduše opakujte `AppendChild` pro každou další instanci `Shape`. Skupina může obsahovat libovolný počet kreslicích objektů, včetně obrázků, textových polí nebo dokonce dalších skupin.

## Kompletní příklad – jak vložit tvary a uložit dokument

Níže je kompletní, spustitelný program, který demonstruje každý krok, o kterém jsme dosud mluvili. Po spuštění kódu vznikne soubor `ShapesDemo.docx` obsahující obdélník, elipsu a seskupený tvar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výstup:** Otevření `ShapesDemo.docx` v Microsoft Word zobrazí jednu stránku s modrým obdélníkem, zelenou elipsou a okolním šedým okrajem, který představuje skupinu. Přesunutí skupiny přesune oba tvary najednou, což potvrzuje úspěšnost operace **seskupit více tvarů**.

## Často kladené otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| *Co když potřebuji tvary na konkrétní stránce?* | Zavolejte `builder.MoveToDocumentEnd();` před vložením tvarů, nebo použijte `builder.MoveToSection(sectionIndex);` pro cílení na konkrétní sekci. |
| *Mohu přidat text uvnitř seskupeného tvaru?* | Ano. Vytvořte `Shape` typu `ShapeType.TextBox`, nastavte jeho text a poté jej `AppendChild` přidejte do `GroupShape`. |
| *Používají se pro rozměry tvarů body nebo pixely?* | Aspose.Words používá **body** (1 pt = 1/72 palce). To zajišťuje konzistentní velikost napříč tiskárnami a displeji. |
| *Jak změnit rotaci skupiny?* | Nastavte `groupShape.RotationAngle = 45;` (stupně). Všechny podřízené tvary se otočí kolem počátku skupiny. |

## Závěr

Nyní víte, jak **vytvořit prázdný dokument**, **vložit obdélníkový tvar**, **jak vložit tvary** jako elipsy a **seskupit více tvarů** do jednoho objektu pomocí Aspose.Words pro .NET. Kompletní ukázkový kód demonstruje doporučený přístup a výše uvedené tipy vám pomohou přizpůsobit řešení složitějším scénářům, jako je přidání textových polí nebo otáčení skupin.

Jste připraveni objevovat dál? Zkuste přidat obrázkový tvar do skupiny, experimentujte s různými barvami výplně nebo vygenerujte vícestránkový report, kde každá stránka obsahuje vlastní seskupený diagram. Stejné principy platí, takže můžete tento vzor rozšířit na jakýkoli projekt automatizace dokumentů.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}