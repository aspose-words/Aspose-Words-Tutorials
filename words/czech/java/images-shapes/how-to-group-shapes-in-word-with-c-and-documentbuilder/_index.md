---
category: general
date: 2026-10-04
description: Naučte se, jak seskupovat tvary ve Wordu pomocí C#. Tento průvodce ukazuje,
  jak vložit obdélníkový tvar, seskupit více tvarů a programově vytvořit prázdný soubor
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: cs
lastmod: 2026-10-04
og_description: Seskupování tvarů ve Wordu pomocí C#. Postupujte podle tohoto průvodce
  krok za krokem pro vložení obdélníkového tvaru, seskupení více tvarů a vytvoření
  prázdného souboru Word pomocí DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Seskupování tvarů ve Wordu pomocí C# – kompletní tutoriál DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Jak seskupit tvary ve Wordu pomocí C# a DocumentBuilder
url: /cs/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary ve Wordu pomocí C# a DocumentBuilder

Pokud potřebujete **seskupit tvary ve Wordu** z C# aplikace, tento tutoriál vám přesně ukáže, jak na to. Uvidíte, jak *vložit obdélníkový tvar*, spojit několik kreslení do jedné skupiny a nakonec **vytvořit prázdný soubor Word**, který obsahuje seskupené objekty.

Práce s tvary je běžnou požadavkem při programovém generování zpráv, faktur nebo vlastních šablon. Na konci tohoto průvodce budete mít znovupoužitelný útržek kódu, který můžete vložit do libovolného .NET projektu, který odkazuje na Aspose.Words.

## Co se naučíte

- Vytvořit prázdný dokument Word od nuly.  
- Vložit obdélníkový tvar a elipsu pomocí `DocumentBuilder`.  
- **Seskupit více tvarů** do `GroupShape`.  
- Použít **append child to group** k vytvoření hierarchie.  
- Uložit soubor na disk a ověřit výsledek.

Předchozí zkušenost s Aspose.Words není vyžadována, ale měli byste mít základní pochopení C# a .NET vývoje.

## Požadavky

| Požadavek | Důvod |
|-------------|--------|
| .NET 6.0 nebo novější | Poskytuje runtime pro C# kód. |
| Aspose.Words pro .NET (nejnovější verze) | Dodává `Document`, `DocumentBuilder` a třídy tvarů. |
| IDE jako Visual Studio 2022 (nebo VS Code) | Usnadňuje kompilaci a spuštění příkladu. |
| Oprávnění k zápisu do složky na vašem počítači | Potřebné pro volání `doc.save`. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Seskupení tvarů ve Wordu – krok za krokem průvodce

Níže je kompletní spustitelný program. Každá sekce je podrobně vysvětlena, abyste pochopili **proč** je kód napsán takto, nejen **co** dělá.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Proč je každý krok důležitý

1. **Vytvořit prázdný soubor Word** – Začátek s čistým dokumentem zaručuje, že žádné skryté formátování neovlivní umístění tvarů.  
2. **Inicializovat DocumentBuilder** – `DocumentBuilder` abstrahuje manipulaci s uzly na nízké úrovni, což vám umožní soustředit se na rozvržení.  
3. **Vložit jednotlivé tvary** – Nejprve potřebujete samostatné objekty (`insert rectangle shape` a elipsu), než je můžete seskupit. Nastavení `Left` a `Top` zajišťuje, že se objeví vedle sebe.  
4. **Seskupit více tvarů** – Vytvořením `GroupShape` a použitím **append child to group** přeměníte dva nezávislé kresby na jedinou logickou jednotku. Přesunutí nebo změna velikosti skupiny ovlivní oba podřízené objekty současně.  
5. **Uložit dokument** – Konečný soubor `GroupedShapes.docx` lze otevřít v Microsoft Word a ověřit, že obdélník a elipsa jsou skutečně seskupeny (vyberete jeden a oba se pohybují společně).

### Očekávaný výstup

Otevřete `GroupedShapes.docx` v Microsoft Word:

- Uvidíte obdélník a elipsu umístěné vedle sebe.  
- Výběrem kterékoli z tvarů se zvýrazní oba, což potvrzuje, že patří do stejné skupiny.  
- Skupinu lze táhnout, měnit její velikost nebo formátovat jako jeden objekt.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Diagram seskupeného obdélníku a elipsy uvnitř dokumentu Word"}

*Snímek obrazovky ilustruje finální seskupené tvary.*

---

## Vložení obdélníkového tvaru – přizpůsobení velikosti a stylu

Pokud potřebujete obdélník s konkrétní barvou výplně nebo okrajem, upravte objekt `Shape` po vložení:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Tyto vlastnosti jsou součástí třídy `Shape` a fungují pro jakýkoli typ tvaru, nejen pro obdélníky. Úprava stylu před **append child to group** zajišťuje, že skupina zdědí vizuální vlastnosti, které jste nastavili.

---

## Seskupení více tvarů – práce s více než dvěma objekty

Příklad seskupuje obdélník a elipsu, ale můžete přidat libovolný počet tvarů:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Tip:** Po vytvoření komplexní skupiny můžete uzamknout její rozvržení, aby se zabránilo nechtěným změnám:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – pořadí má význam

Pořadí, ve kterém voláte `AppendChild`, určuje Z‑order (který tvar je nahoře). Ve vzorku je nejprve přidán obdélník, pak elipsa, takže elipsa překrývá obdélník, pokud se protínají. Přeskupení je tak jednoduché jako zavolat `RemoveChild` a znovu přidat:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Vytvoření prázdného souboru Word – znovupoužitelná pomocná metoda

Pokud vaše aplikace často potřebuje nový dokument, zabalte logiku vytvoření:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Pak můžete nahradit řádek `new Document()` v hlavním programu voláním `CreateBlankWordFile()`. Tím se demonstruje koncept **create blank word file** způsobem, který lze znovu použít.

---

## Časté úskalí a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|-------|----------------|-----|
| Tvary se zobrazují mimo stránku | Výchozí hodnoty `Left`/`Top` jsou 0, což umístí tvar na okraj. | Explicitně nastavte `Left` a `Top` po vložení. |
| Skupina ztrácí formátování | Změna podřízeného tvaru po jeho přidání do skupiny může rozbít rozvržení skupiny. | Použijte všechny vizuální vlastnosti **před** voláním `AppendChild`. |
| Uložený soubor je prázdný | `DocumentBuilder` nebyl nikdy použit k přidání uzlu, nebo `doc.Save` byl zavolán na jinou instanci `Document`. | Ověřte, že ukládáte stejný `Document`, který jste vytvořili. |
| Varování o kompatibilitě ve Wordu | Používání novějších funkcí tvarů, které nejsou podporovány |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s krok za krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vložit tvary do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}