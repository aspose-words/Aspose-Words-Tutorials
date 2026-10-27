---
category: general
date: 2026-08-23
description: Naučte se, jak seskupovat tvary v C# pomocí Aspose.Words. Průvodce také
  popisuje, jak vložit obdélníkový tvar a přidávat tvary do Wordu pro složité dokumenty.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: cs
lastmod: 2026-08-23
og_description: Jak seskupit tvary v C# s Aspose.Words. Sledujte tento kompletní tutoriál,
  jak vložit obdélníkový tvar, přidat tvary do Wordu a efektivně seskupit více tvarů.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Jak seskupit tvary v C# – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Jak seskupit tvary v C# pomocí Aspose.Words
url: /cs/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary v C# pomocí Aspose.Words

Pokud potřebujete **how to group shapes** v dokumentu Word programově, tento tutoriál vám ukáže přesné kroky pomocí Aspose.Words pro .NET. Ať už vytváříte generátor reportů, šablonovací engine nebo nástroj pro diagramy, naučíte se, jak zahájit skupinu, vložit obdélníkový tvar a přidat word‑úroveň obsah tvarů, aniž byste opustili svůj kód.

Také uvidíte, jak **group multiple shapes** dohromady, což je nezbytné, když chcete přesunout, otočit nebo stylovat kolekci objektů jako jedinou entitu. Níže uvedený příklad funguje s nejnovějším vydáním Aspose.Words 24.x a vyžaduje pouze .NET 6 nebo novější.

## Požadavky

- .NET 6 SDK (nebo jakákoli verze .NET podporovaná Aspose.Words)
- Visual Studio 2022 nebo VS Code
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
- Základní znalost C# a objektového modelu Aspose.Words

> **Tip:** Použijte bezplatnou evaluační licenci od Aspose, abyste se vyhnuli omezením vodoznaku během testování.

## Jak seskupit tvary pomocí Aspose.Words

Níže je kompletní spustitelný program, který demonstruje **how to start group**, přidá obdélník a dokončí skupinu. Kód následuje stejný logický tok jako úryvek, který jste poskytli, ale přidává kontext, ošetření chyb a komentáře pro přehlednost.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Proč je každý krok důležitý

| Krok | Účel | Jak souvisí s klíčovými slovy |
|------|------|--------------------------------|
| **Vytvořit nový prázdný dokument** | Poskytuje čisté plátno pro operace s tvary. | Nastavuje scénu pro **add shapes word** později. |
| **Initialize DocumentBuilder** | Builder je hlavní API pro vkládání objektů. | Potřebné před tím, než můžete **how to start group**. |
| **StartGroupShape** | Zahajuje logický kontejner; všechny následující tvary se stávají členy této skupiny. | Přímo odpovídá na **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Umisťuje jednotlivé tvary do skupiny. Volání obdélníku splňuje **insert rectangle shape**; tvar textu splňuje **add shapes word**. | Ukazuje **group multiple shapes**. |
| **EndGroupShape** | Dokončuje skupinu, takže ji můžete přesouvat nebo stylovat jako jednotku. | Dokončuje workflow **how to group shapes**. |

## Vkládání obdélníkového tvaru – podrobnější pohled

Metoda `InsertShape` přijímá výčtový typ `ShapeType`, šířku a výšku. Pro **insert rectangle shape** s vlastním stylem můžete rozšířit příklad:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Proč jej stylovat?** Stylování zajišťuje, že obdélník vynikne, když je skupina později přeřazena. Také ukazuje, že vlastnosti tvaru lze nastavit *před* uzavřením skupiny.

## Přidávání tvarů na úrovni Wordu (add shapes word)

Pokud potřebujete vložit text přímo do tvaru — běžně nazývaného “WordArt” nebo “textové pole” — použijte `ShapeType.TextPlainText`. Po vložení můžete do tvaru zapisovat text pomocí `DocumentBuilder.Writeln` nebo přístupem k vlastnosti `TextBox` tvaru:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Toto splňuje klíčové slovo **add shapes word** a ukazuje, jak může text cestovat se skupinou.

## Seskupování více tvarů – praktické scénáře

Když **group multiple shapes**, můžete je považovat za jeden objekt pro umístění, rotaci nebo škálování. Například po uzavření skupiny můžete přesunout celou skupinu:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Nebo otočit skupinu:

```csharp
group.Rotation = 45; // degrees
```

Tyto operace jsou možné pouze díky tomu, že tvary sdílejí stejnou nadřazenou skupinu.

## Řešení okrajových případů

1. **Nested groups** – Aspose.Words umožňuje skupiny uvnitř skupin. Pro vytvoření vnořené skupiny zavolejte `StartGroupShape` znovu před voláním `EndGroupShape` pro vnitřní skupinu.
2. **Empty groups** – Pokud zahájíte skupinu, ale nikdy nevložíte tvar, `EndGroupShape` stále vytvoří prázdný kontejner. To je neškodné, ale může mírně zvětšit velikost souboru.
3. **Compatibility** – Vygenerovaný DOCX funguje s Word 2010 a novějšími. Starší verze mohou ignorovat metadata skupin, takže vždy testujte s cílovou verzí Wordu.

## Kompletní zdrojový soubor pro referenci

Uložte následující jako `Program.cs` v .NET konzolovém projektu. Kód se zkompiluje a spustí bez úprav.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Očekávaný výstup

Otevřením `GroupedShapes.docx` v Microsoft Word se zobrazí:

- Světle korálový obdélník, elipsa a textové pole — všechny vizuálně spojené dohromady.
- Výběrem jakékoli části skupiny také vybere celou skupinu (objeví se jediný ohraničující rámeček).
- Přesunutí nebo otočení skupiny přesune všechny tři tvary najednou.

## Často kladené otázky

**Q: Mohu seskupit tvary, které již v dokumentu existují?**  
A: Ano. Získejte existující objekty `Shape`, zavolejte `builder.StartGroupShape()`, znovu je vložte pomocí `builder.InsertShape(existingShape)` a poté zavolejte `EndGroupShape()`.

**Q: Ovlivňuje seskupování podkladové XML?**  
A: Aspose.Words přidá prvek `<w:grpSp>`, který obsahuje uzel `<w:sp>` každého tvaru. To je plně v souladu se specifikací Office Open XML.

**Q: Co když potřebuji později rozdělit skupinu?**  
A: Neexistuje přímé API „ungroup“, ale můžete iterovat přes podřízené tvary skupiny (`group.GroupShape.Children`) a zkopírovat je do těla dokumentu.

## Další kroky

Nyní, když víte **how to group shapes**, zvažte prozkoumání těchto souvisejících témat:

- **Apply complex formatting to grouped shapes** – naučte se nastavit gradientní výplně, stínové efekty a styly čar.
- **Export grouped shapes as images** – použijte `Shape.GetShapeRenderer().Save(...)` k rasterizaci skupiny.
- **Create dynamic diagrams** – kombinujte datově řízené umístění se seskupováním pro automatické generování diagramů.

Každý z nich staví na zde představeném základu a pomůže vám vytvořit bohatší, interaktivnější dokumenty Word.

---

*Šťastné programování! Pokud vám tento průvodce přišel užitečný, sdílejte ho s kolegy nebo dejte hvězdičku repozitáři, který obsahuje ukázkový projekt.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vkládání tvarů do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvoření skupinového tvaru v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvoření obdélníkového tvaru ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}