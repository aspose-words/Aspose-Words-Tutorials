---
category: general
date: 2026-08-14
description: Jak seskupit tvary v dokumentu Word pomocí C#. Naučte se vytvořit dokument
  Word, vložit obdélníkový tvar, seskupit tvary ve Wordu a uložit dokument jako docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: cs
lastmod: 2026-08-14
og_description: Jak seskupit tvary v dokumentu Word pomocí C#. Sledujte tento kompletní
  návod, jak vytvořit soubor Word, vložit obdélníkový tvar, seskupit tvary ve Wordu
  a uložit výsledek jako docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Jak seskupit tvary v dokumentu Word pomocí C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Jak seskupit tvary v dokumentu Word pomocí C#
url: /cs/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary v dokumentu Word pomocí C#

Pokud potřebujete **seskupit tvary** v dokumentu Word, tento návod vám ukáže přesné kroky pomocí C# a knihovny Aspose.Words. Uvidíte, jak vytvořit Word dokument, vložit obdélníkový tvar, seskupit tvary ve Wordu a nakonec **uložit dokument jako docx** — vše v jednom spustitelném programu.

Vytváření a manipulace s tvary je častý požadavek při programovém generování zpráv, smluv nebo marketingových brožur. Na konci tohoto tutoriálu budete mít znovupoužitelný úryvek kódu, který můžete vložit do libovolného .NET projektu.

## Předpoklady

Než začnete, ujistěte se, že máte:

- .NET 6.0 nebo novější nainstalovaný  
- Visual Studio 2022 (nebo jakékoli IDE podporující .NET)  
- Licenci Aspose.Words pro .NET (nebo bezplatnou zkušební verzi)  
- Základní znalosti syntaxe C#  

Žádné další NuGet balíčky nejsou potřeba kromě `Aspose.Words`.

## Jak seskupit tvary v dokumentu Word

Jádrem řešení je pětikrokový proces. Každý krok je podrobně vysvětlen a kompletní zdrojový kód je uveden na konci článku.

### Krok 1: Vytvořit nový prázdný dokument

První věc, kterou uděláte, když chcete **vytvořit Word dokument** programově, je vytvořit objekt `Document`. Tento objekt představuje celý soubor .docx v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:** `DocumentBuilder` je vysoceúrovňový pomocník, který vám umožní vkládat text, tabulky a tvary, aniž byste museli ručně manipulovat se stromem uzlů.

### Krok 2: Vložit obdélníkový tvar

Pro demonstraci **vložit obdélníkový tvar** použijeme metodu `InsertShape`. Obdélník bude první člen skupiny.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Proč je to důležité:** Tvary jsou umístěny relativně k bodu vložení. Nastavení barvy výplně vám pomůže tvar vidět po otevření výsledného dokumentu.

### Krok 3: Vložit eliptický tvar

Dále **vložíme eliptický tvar** (API jej nazývá `Ellipse`). To bude druhý člen skupiny.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Proč je to důležité:** Vložením elipsy okamžitě po obdélníku skončí oba tvary ve stejném odstavci, což později usnadní jejich seskupení.

### Krok 4: Seskupit obdélník a elipsu

Nyní odpovídáme na hlavní otázku **jak seskupit tvary** v dokumentu Word. Aspose.Words poskytuje `AppendGroupShape` pro vytvoření kontejneru skupiny a poté na tomto kontejneru zavoláte `Group()`.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Proč je to důležité:** Jakmile jsou seskupeny, jakákoli transformace (přesun, změna velikosti, otočení) aplikovaná na `groupedShape` automaticky ovlivní jak obdélník, tak elipsu. To je nezbytné pro zachování konzistence rozvržení ve generovaných dokumentech.

### Krok 5: Uložit dokument jako soubor DOCX

Posledním krokem je **uložit dokument jako docx**. Můžete zvolit libovolnou cestu; v příkladu je použita zástupná hodnota `"YOUR_DIRECTORY"`, kterou byste měli nahradit skutečnou složkou.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Proč je to důležité:** Uložení jako DOCX zachovává metadata o seskupení, takže po otevření souboru v Microsoft Word uvidíte obdélník a elipsu jako jeden objekt.

## Kompletní, spustitelný příklad

Níže je kompletní program, který kombinuje všech pět kroků. Zkopírujte jej do nového konzolového projektu, obnovte NuGet balíček Aspose.Words a spusťte.

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
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Očekávaný výstup

Když otevřete `groupedShapes.docx` v Microsoft Word, uvidíte světlemodrý obdélník a světlekorálovou elipsu spojené dohromady. Kliknutím na kterýkoli tvar vyberete oba, což vám umožní je přesouvat nebo měnit jejich velikost jako jeden celek.

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Mohu seskupit více než dva tvary?** | Ano. Předáte libovolný počet objektů `Shape` metodě `AppendGroupShape`. Metoda přijímá pole, takže můžete kolekci vytvářet dynamicky. |
| **Co když potřebuji, aby byla skupina ukotvena v buňce tabulky?** | Vložte tvary do odstavce buňky a poté zavolejte `AppendGroupShape` na tomto odstavci. Skupina zdědí ukotvení buňky. |
| **Ovlivňuje seskupení podkladové XML?** | Aspose.Words zapíše prvek `<w:grpSp>`, který obsahuje podřízené tvary. Word jej rozpozná jako skupinu a zachová relativní umístění. |
| **Jak skupinu později rozdělit?** | Zavolejte `groupedShape.Ungroup()`; metoda vrátí jednotlivé tvary, které můžete dále samostatně manipulovat. |
| **Má seskupení dopad na výkon při velkém počtu tvarů?** | Samotné seskupení je nenáročné, ale renderování velmi velkých skupin (stovky tvarů) může zvýšit velikost souboru. Zvažte zploštění obrázků, pokud se velikost stane problémem. |

## Profesionální tipy

- **Nastavte explicitní pozice** (`Left`, `Top`), pokud potřebujete před seskupením přesné zarovnání.  
- **Použijte `Shape.WrapType = WrapType.Inline`**, když chcete, aby se skupina chovala jako prvek odstavce místo plovoucího objektu.  
- **Aplikujte styl čáry** na skupinu (`groupedShape.LineFormat`), abyste celé kolekci dali okraj.  
- **Znovu použijte skupinu**: po zavolání `Group()` můžete klonovat `groupedShape` a vložit klon na jiné místo v dokumentu.

## Další kroky

Nyní, když už víte **jak seskupit tvary** v dokumentu Word, můžete prozkoumat související témata, jako jsou:

- **Vložit obdélníkový tvar** s vlastním textem nebo obrázky uvnitř tvaru.  
- **Vytvořit složité diagramy** vnořením skupin (seskupit skupinu).  
- **Exportovat dokument jako PDF** při zachování seskupení tvarů (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Každé z těchto témat staví na stejných základech, které jsou zde popsány, takže jste dobře připraveni rozšířit svůj toolkit pro automatizaci Wordu.

## Závěr

Tento tutoriál demonstroval **jak seskupit tvary** v dokumentu Word pomocí C#. Naučili jste se **vytvořit Word dokument**, **vložit obdélníkový tvar**, **seskupit tvary ve Wordu** a nakonec **uložit dokument jako docx**. S kompletním, spustitelným příkladem a praktickými tipy můžete začlenit seskupování tvarů do jakéhokoli workflow generování dokumentů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}