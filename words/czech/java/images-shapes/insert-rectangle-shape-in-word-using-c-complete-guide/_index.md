---
category: general
date: 2026-08-04
description: Vložte obdélníkový tvar do dokumentu Word pomocí C#. Naučte se, jak seskupovat
  tvary ve Wordu, uložit dokument jako docx a použít DocumentBuilder pro pokročilé
  rozvržení.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: cs
lastmod: 2026-08-04
og_description: Vložte obdélníkový tvar do souboru Word pomocí C# a poté seskupte
  tvary pro pokročilé rozvržení. Tento tutoriál také pokrývá ukládání dokumentu jako
  docx a efektivní používání třídy DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Vložení obdélníkového tvaru do Wordu – průvodce krok za krokem v C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Vložení obdélníkového tvaru ve Wordu pomocí C# – kompletní průvodce
url: /cs/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení obdélníkového tvaru ve Wordu pomocí C# – kompletní průvodce

Pokud potřebujete **vložit obdélníkový tvar** do dokumentu Word pomocí C#, tento tutoriál vám ukáže přesně jak. Také se naučíte **jak seskupit tvary** ve Wordu, **uložit dokument jako docx** a **jak použít Builder** pro čistý a udržovatelný kód.

Práce s tvary je častý požadavek při generování zpráv, certifikátů nebo vlastních rozvržení programově. Na konci tohoto průvodce budete mít plně spustitelný příklad, který vytvoří obdélník, přidá elipsu, seskupí je a uloží výsledek jako soubor DOCX.

## Předpoklady

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější nainstalovaný  
* Visual Studio 2022 (nebo jakékoli IDE podporující C#)  
* Knihovnu **Aspose.Words for .NET** (k dispozici přes NuGet)  

Knihovnu můžete přidat následujícím příkazem:

```bash
dotnet add package Aspose.Words
```

## Vložení obdélníkového tvaru pomocí DocumentBuilder

Prvním krokem je vytvořit nový `Document` a `DocumentBuilder`. Builder poskytuje fluent API pro vkládání obsahu, včetně tvarů.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

Instance `DocumentBuilder` je hlavní objekt, který použijete k **vložením obdélníkového tvaru** a dalších elementů. Sleduje aktuální pozici kurzoru v dokumentu, takže jakékoli vložení proběhne přesně tam, kde to potřebujete.

## Jak vložit obdélníkový tvar

S připraveným builderem zavolejte `InsertShape`. Zadejte `ShapeType`, šířku a výšku v bodech (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Proč je to důležité*: Nastavení `FillColor` a `StrokeColor` dává obdélníku vizuální odlišení, což pomáhá při pozdějším seskupování s dalšími tvary.

## Jak seskupit tvary ve Wordu

Seskupování tvarů vám umožní přesouvat, otáčet nebo formátovat více objektů jako jeden celek. Po vložení obdélníku přidejte další tvar (v tomto příkladu elipsu) a poté vytvořte `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Volání `InsertGroupShape` vytvoří zástupný objekt, který může obsahovat libovolný počet podřízených tvarů. Připojením obdélníku a elipsy efektivně **seskupíte tvary ve Wordu**. Skupina se chová jako jeden tvar – můžete ji přemístit, aplikovat okraj nebo změnit velikost, aniž byste ovlivnili vnitřní rozvržení jednotlivých podtvarů.

### Profesionální tip

Po seskupení můžete změnit pozici skupiny relativně k stránce:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Uložení dokumentu jako docx

Jakmile jsou tvary uspořádány, je potřeba soubor uložit. Metoda `Document.Save` automaticky určuje formát podle přípony souboru. Pro **uložení dokumentu jako docx** předávejte cestu končící na `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Spuštěním programu vznikne `output.docx`. Otevřete soubor v Microsoft Word a uvidíte světle modrý obdélník a světle korálovou elipsu seskupené dohromady. Můžete kliknout na skupinu a přesunout ji jako jeden objekt.

## Jak efektivně používat DocumentBuilder

`DocumentBuilder` není jen vkladač tvarů; také pracuje s textem, tabulkami, záhlavími a zápatími. Když kombinujete tvorbu tvarů s textem, nezapomeňte resetovat kurzor, pokud potřebujete vložit obsah jinde:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Udržování explicitního stavu builderu zabraňuje nechtěným přepisům a usnadňuje údržbu kódu.

## Okrajové případy a varianty

| Situace | Doporučený přístup |
|-----------|----------------------|
| **Více než dva tvary** | Vložte každý tvar a poté zavolejte `AppendChild` pro každý tvar před uložením. |
| **Vnořené skupiny** | Vytvořte skupinu, přidejte tvary a poté vložte tuto skupinu do dalšího `GroupShape`. |
| **Různé jednotky měření** | Použijte `builder.ConvertPixelsToPoints`, pokud máte rozměry v pixelech. |
| **Kompatibilita se staršími verzemi Wordu** | Uložte jako `.doc` změnou přípony; většina funkcí tvarů stále funguje. |

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat a vložit do nového konzolového projektu. Žádné další úryvky kódu nejsou potřeba.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Očekávaný výsledek**: Otevřením `output.docx` uvidíte světle modrý obdélník a světle korálovou elipsu seskupené dohromady, umístěné 150 pt od levého okraje a 100 pt od horního okraje. Titulek se zobrazí pod skupinou.

## Závěr

Nyní víte, jak **vložit obdélníkový tvar** do souboru Word pomocí C#, **jak seskupit tvary ve Wordu** a **jak uložit dokument jako docx** s pomocí Aspose.Words `DocumentBuilder`. Ovládnutím těchto kroků můžete vytvářet složitá rozvržení – certifikáty, zprávy nebo vlastní formuláře – kompletně pomocí kódu.

Dále prozkoumejte související témata, jako je **přidávání textových polí**, **práce s tabulkami** nebo **export do PDF**. Každé z nich staví na stejných základech `DocumentBuilder`, které jste právě procvičili.

Jste připraveni automatizovat své Word dokumenty? Zkuste rozšířit příklad o další tvary, aplikovat gradienty nebo iterovat přes data a vygenerovat kompletní zprávu během jednoho spuštění. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}