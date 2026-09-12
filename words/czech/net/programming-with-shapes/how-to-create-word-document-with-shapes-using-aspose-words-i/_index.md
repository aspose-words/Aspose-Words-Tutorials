---
category: general
date: 2026-09-11
description: Naučte se, jak vytvořit dokument Word, přidat obdélníkový tvar a nastavit
  rozměry tvaru pomocí Aspose.Words. Krok za krokem průvodce v C# pro přesné nastavení
  velikosti tvaru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: cs
lastmod: 2026-09-11
og_description: Vytvořte Word dokument pomocí Aspose.Words v C#. Tento průvodce ukazuje,
  jak přidat obdélníkový tvar, nastavit velikost tvaru a programově spravovat rozměry
  tvaru.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Vytvořte dokument Word se tvary – tutoriál Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Jak vytvořit dokument Word s tvary pomocí Aspose.Words v C#
url: /cs/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument s tvary pomocí Aspose.Words v C#

Pokud potřebujete **vytvořit Word dokument**, který obsahuje vlastní grafiku, můžete to provést kompletně v kódu. Tento tutoriál vás provede vytvořením souboru Word, přidáním obdélníkového tvaru a řízením každého rozměru tvaru. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného .NET projektu.

Naučíte se, jak **přidat obdélníkový tvar**, **nastavit velikost tvaru** a **nastavit rozměry tvaru** uvnitř seskupeného kontejneru. Příklad používá Aspose.Words 13.9, ale koncepty platí i pro pozdější verze. Předchozí zkušenost s Aspose drawing API není vyžadována – stačí základní znalost C#.

## Požadavky

- .NET 6.0 nebo novější nainstalováno  
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)  
- IDE, například Visual Studio 2022 (funguje jakýkoli editor podporující C#)  

Mít tyto nástroje připravené vám umožní okamžitě spustit kód bez další konfigurace.

## Krok 1: Inicializace dokumentu a builderu – základy vytváření Word dokumentu

Prvním krokem je vytvořit objekt `Document` a `DocumentBuilder`. `Document` představuje samotný soubor, zatímco `DocumentBuilder` poskytuje plynulé API pro vkládání obsahu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:**  
Vytvoření dokumentu předem vám poskytne čisté plátno. Kurzor builderu začíná v prvním odstavci, což je místo, kde později **vytvoříme tvary ve Wordu**.

## Krok 2: Vytvoření GroupShape pro uložení více grafiky

`GroupShape` funguje jako kontejner; můžete přesunout, otočit nebo změnit velikost celé skupiny jako jedné jednotky. Zde definujeme šířku a výšku kontejneru v bodech (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Proč je to důležité:**  
Seskupování tvarů zjednodušuje správu rozvržení. Pokud později potřebujete přidat další tvary (např. kruhy nebo textová pole), zdědí pozici a měřítko skupiny.

## Krok 3: Vytvoření obdélníkového tvaru a nastavení jeho rozměrů

Nyní přidáme skutečný obdélník. Konstruktor `Shape` vyžaduje odkaz na dokument a typ tvaru. Po vytvoření explicitně **nastavíme velikost tvaru** a **nastavíme rozměry tvaru**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Proč je to důležité:**  
Určení šířky, výšky, levého a horního okraje vám poskytuje pixel‑dokonalou kontrolu nad tvarem. To je nezbytné, když dokument musí odpovídat designové specifikaci nebo tištěnému formuláři.

## Krok 4: Sestavení skupiny připojením obdélníku

Připojení obdélníku k `GroupShape` ho učiní podřízeným uzlem. Můžete přidat tolik podřízených uzlů, kolik potřebujete, před vložením skupiny do dokumentu.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:**  
Pokud plánujete přidat druhý tvar, vytvořte jej stejným způsobem a zavolejte `group.AppendChild(secondShape)`. Všechny podřízené uzly sdílejí souřadnicový systém skupiny.

## Krok 5: Vložení seskupeného tvaru do dokumentu a uložení

Po úplném sestavení skupiny ji vložíme do aktuálního odstavce. Vlastnost `CurrentParagraph` builderu poskytuje přímý přístup k podkladovému stromu uzlů.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Proč je to důležité:**  
Připojení skupiny k odstavci zajistí, že se tvar zobrazí v řadě s tokem textu. Uložení dokumentu dokončuje operaci **vytvořit Word dokument**.

## Běžné varianty a okrajové případy

| Scénář | Úprava |
|----------|------------|
| **Různá orientace stránky** | Nastavte `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` před vytvořením skupiny. |
| **Více obdélníků** | Vytvořte další objekty `Shape` a pro každý zavolejte `group.AppendChild(newRect)`. |
| **Dynamická velikost na základě obsahu** | Vypočítejte šířku/výšku z rozměrů obrázku nebo textových metrik a poté přiřaďte `rectangle.Width` / `rectangle.Height`. |
| **Export do PDF** | Po `doc.Save` zavolejte `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Kompatibilita se staršími verzemi Wordu** | Uložte pomocí `SaveFormat.Doc` místo `Docx` pro kompatibilitu s Word 97‑2003. |

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny `using` direktivy, vstupní bod `Main` a komentáře, které vysvětlují každý řádek.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Očekávaný výstup:**  
Když otevřete *GroupShape.docx*, první stránka zobrazí šedě ohraničený obdélník umístěný 50 pt od levého/ horního okraje, přičemž samotný obdélník je posunut o 10 pt uvnitř skupiny. Rozměry odpovídají hodnotám nastaveným v kódu.

## Závěr

Nyní víte, jak **vytvořit Word dokument**, **přidat obdélníkový tvar** a přesně **nastavit velikost tvaru** a **nastavit rozměry tvaru** pomocí Aspose.Words. Přístup se seskupenými tvary udržuje rozvržení flexibilní a připravené na budoucí rozšíření, jako jsou další grafiky nebo textová pole.

Dále prozkoumejte související témata, jako je **vytváření tvarů ve Wordu** pro kruhy, šipky nebo vlastní SVG cesty, a naučte se, jak **nastavit barvu výplně tvaru** nebo **aplikovat rotaci**. Experimentujte s různými jednotkami, abyste viděli, jak Word vykresluje body oproti centimetrům, a integrujte kód do větších pipeline pro generování dokumentů.

Šťastné programování a neváhejte tento vzor přizpůsobit jakémukoli scénáři automatizovaného reportování nebo vyplňování formulářů, na který narazíte!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvořit prázdný Word dokument se stínovaným obdélníkovým tvarem – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutoriál stínování tvaru v Aspose.Words – Přidat stín k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}