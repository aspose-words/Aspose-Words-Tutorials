---
category: general
date: 2026-09-21
description: Vytvořte prázdný dokument Word pomocí Aspose.Words, nastavte velikost
  tvaru, jeho pozici, barvu a uložte soubor docx v jednom kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: cs
lastmod: 2026-09-21
og_description: Vytvořte prázdný dokument Word, nastavte velikost tvaru, pozici tvaru,
  barvu tvaru a uložte soubor docx pomocí Aspose.Words během několika minut.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Vytvořte prázdný dokument Word a přidejte barevné tvary – průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Vytvořte prázdný dokument Word a přidejte barevné tvary pomocí Aspose.Words
url: /cs/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a přidejte barevné tvary pomocí Aspose.Words

Pokud potřebujete **vytvořit prázdný dokument Word** programově, tento návod vám ukáže, jak na to s Aspose.Words. Naučíte se **nastavit velikost tvaru**, **nastavit pozici tvaru**, **nastavit barvu tvaru** a nakonec **uložit soubor docx** aniž byste opustili své IDE.

Práce se soubory Word v C# často znamená manipulaci s nízkoúrovňovými voláními OpenXML, ale Aspose.Words abstrahuje tuto složitost. Na konci tohoto tutoriálu budete mít plně funkční `.docx`, který obsahuje seskupený tvar složený ze dvou barevných obdélníků – ideální pro zprávy, certifikáty nebo vlastní šablony.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
- Aspose.Words pro .NET 23.9 nebo novější (instalace přes NuGet: `Install-Package Aspose.Words`)
- Základní znalost C# a Visual Studio (nebo jakéhokoli editoru C#)

Žádný existující soubor Word není vyžadován; tutoriál začíná **vytvořením prázdného dokumentu Word** od nuly.

## Vytvoření prázdného dokumentu Word pomocí Aspose.Words

Prvním krokem je vytvořit instanci objektu `Document`. Tento objekt představuje prázdný soubor Word v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` je zpočátku prázdný, což je přesně to, co potřebujete při **vytváření prázdného dokumentu Word**. `builder` bude později použit k vložení skupiny tvarů na aktuální pozici kurzoru.

## Nastavení velikosti tvaru a vytvoření GroupShape

`GroupShape` funguje jako kontejner, který může obsahovat více jednotlivých tvarů. Nejprve definujte celkové rozměry kontejneru.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Zde **nastavujeme velikost tvaru** pro samotnou skupinu (300 × 200). Stejné názvy vlastností (`Width`, `Height`) jsou použity pro každý podřízený tvar, což vám poskytuje detailní kontrolu nad každým prvkem.

## Přidání prvního obdélníku a nastavení barvy tvaru

Nyní přidejte obdélník do skupiny a nastavte mu barvu pozadí.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Vlastnost `FillColor` **nastavuje barvu tvaru**. Použití `System.Drawing.Color` vám umožní vybrat libovolnou předdefinovanou nebo vlastní ARGB hodnotu.

## Přidání druhého obdélníku, nastavení jeho velikosti, pozice a barvy

Druhý obdélník ukazuje, jak **nastavit pozici tvaru** relativně ke skupině a jak změnit jeho barvu.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Protože šířka skupiny je 300 bodů, dva 120‑bodové obdélníky se pohodlně vejdou s mezerou 30 bodů. Pokud potřebujete jiný rozvrh, upravte `Left` a `Top`.

## Vložení GroupShape do dokumentu

Po úplném nastavení skupiny ji umístěte na aktuální pozici kurzoru.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` zapíše tvar přímo do těla dokumentu a zachová přesnou **nastavenou pozici tvaru**, kterou jste definovali dříve.

## Uložení souboru docx

Posledním krokem je uložit dokument na disk. Toto demonstruje operaci **uložit soubor docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Po spuštění programu otevřete `GroupShape.docx` v Microsoft Word. Měli byste vidět prázdnou stránku se seskupeným tvarem obsahujícím dva barevné obdélníky umístěné vedle sebe.

### Očekávaný výstup

- Jednostránkový soubor `.docx`.
- Stránka obsahuje skupinový tvar umístěný 100 bodů od levého a horního okraje.
- Uvnitř skupiny je světle-modrý obdélník vlevo a světle-korálový obdélník vpravo, každý o rozměrech 120 × 80 bodů.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Žádné další soubory nejsou vyžadovány.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spuštěním tohoto programu vytvoříte přesně dokument popsaný výše, který splňuje všechny čtyři cíle: **vytvořit prázdný dokument Word**, **nastavit velikost tvaru**, **nastavit pozici tvaru**, **nastavit barvu tvaru** a **uložit soubor docx**.

## Běžné varianty a okrajové případy

| Scenario | Co změnit | Proč je to důležité |
|----------|-----------|--------------------|
| **Different shape types** | Nahraďte `ShapeType.Rectangle` za `ShapeType.Ellipse`, `ShapeType.Triangle` atd. | Umožňuje vytvořit složitější grafiku bez externích obrázků. |
| **Dynamic dimensions** | Vypočítejte `Width` a `Height` z uživatelského vstupu nebo konfiguračních souborů. | Zajišťuje, že řešení je použitelné napříč více šablonami dokumentů. |
| **Saving as PDF** | Zavolejte `document.Save("output.pdf", SaveFormat.Pdf);` | Pokud příjemci potřebují needitovatelný formát, PDF je bezpečná volba. |
| **Adding text inside a shape** | Vytvořte tvar `TextBox` a nastavte `TextBox.Text`. | Užitečné pro tvorbu označených štítků nebo vysvětlivek. |
| **Multiple groups on one page** | Opakujte kroky 2‑5 s různými hodnotami `Left`/`Top`. | Umožňuje vytvořit dashboardy nebo rozvržení s více sekcemi. |

### Pro tip

Když potřebujete tvarům přesně zarovnat, použijte před vložením skupiny vlastnost `ShapeBase.WrapType = WrapType.Inline`. Tím se skupina chová jako odstavec a zabraňuje neočekávanému obtékání textu.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word** pomocí Aspose.Words, **nastavit velikost tvaru**, **nastavit pozici tvaru**, **nastavit barvu tvaru** a **uložit soubor docx**. Kompletní příklad ukazuje čistý, znovupoužitelný vzor pro přidávání seskupené grafiky do jakéhokoli projektu automatizace Word.

From here you can explore:

- Přidání dalších tvarů nebo obrázků do stejného `GroupShape` (variace **set shape size**, **set shape color**).
- Použití `ShapeBase.Rotation` k otáčení obdélníků pro dekorativní efekty.
- Exportování stejného dokumentu jako PDF nebo HTML pro širší distribuci (alternativa **save docx file**).

Neváhejte experimentovat s různými barvami, velikostmi a logikou rozvržení, aby vyhovovaly vašim konkrétním potřebám reportování nebo šablonování. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření skupinového tvaru v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvoření obdélníkového tvaru ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriál stínování tvaru v Aspose.Words – Přidání stínu k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}