---
category: general
date: 2026-10-07
description: Vytvořte prázdný dokument Word v C# a naučte se přidávat obdélníkový
  tvar, vkládat obrázkový tvar a seskupovat více tvarů pro dynamické reporty.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: cs
lastmod: 2026-10-07
og_description: Vytvořte prázdný dokument Word v C# pomocí Aspose.Words. Naučte se,
  jak přidat obdélníkový tvar, vložit obrázkový tvar a seskupit více tvarů pro profesionální
  dokumenty.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Vytvořte prázdný dokument Word a seskupte tvary v C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit prázdný dokument Word a seskupit tvary v C#
url: /cs/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a seskupit tvary v C#

Pokud potřebujete **vytvořit prázdný dokument Word** programově, tento návod vám přesně ukáže, jak na to. Uvidíte, jak **přidat obdélníkový tvar**, **vložit obrazový tvar** a **seskupit více tvarů**, aby se chovaly jako jeden objekt, když později **přidáte obrázek do Wordu**.

Práce se soubory Word z kódu může působit zastrašujícím dojmem, ale Aspose.Words proces zjednodušuje. Na konci tohoto tutoriálu budete mít znovupoužitelný úryvek C#, který vygeneruje čistý, prázdný soubor Word obsahující seskupený obdélník a logo. Výsledek můžete vložit do faktur, zpráv nebo jakéhokoli automatizovaného pracovního postupu s dokumenty.

## Požadavky

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+).  
* Platná licence Aspose.Words pro .NET nebo bezplatný evaluační klíč.  
* Soubor s obrázkem (např. `logo.png`) umístěný ve složce, na kterou můžete odkazovat z kódu.  
* Visual Studio 2022 nebo jakékoli IDE kompatibilní s C#.

Kromě `Aspose.Words` nejsou vyžadovány žádné další balíčky NuGet.

## Jak vytvořit prázdný dokument Word pomocí Aspose.Words

Prvním krokem je vždy **vytvořit prázdný dokument Word**. Tento objekt bude hostovat všechny následné tvary.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` představuje celý soubor `.docx`. V tomto okamžiku je soubor prázdný, což splňuje požadavek na *vytvoření prázdného dokumentu Word*.

## Vytvoření kontejneru pro seskupení více tvarů

Seskupování tvarů vám umožní je společně přesouvat, otáčet nebo měnit jejich velikost. Aspose.Words poskytuje třídu `GroupShape` pro tento účel.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Obdélník `Bounds` určuje, kde se skupina objeví na stránce. Umístěním skupiny do prvního odstavce zajistíte, že **vytvořený prázdný dokument Word** bude okamžitě obsahovat vizuální kontejner.

## Jak přidat obdélníkový tvar do skupiny

Běžným požadavkem je **přidat obdélníkový tvar** jako pozadí nebo okraj. Následující kód vytvoří obdélník a přidá jej do dříve definované skupiny.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Protože obdélník žije uvnitř `GroupShape`, bude se pohybovat společně s jakýmikoli dalšími tvary, které později přidáte. To je jádro funkčnosti **seskupit více tvarů**.

## Jak vložit obrazový tvar do skupiny

Dále **vložíte obrazový tvar** (logo) a umístíte jej vedle obdélníku. To demonstruje pracovní postup **přidat obrázek do Wordu**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Metoda `SetImage` načte soubor a vloží jej přímo do dokumentu Word, čímž zajistí, že obrázek zůstane i po přesunutí zdrojového souboru. Tím je dokončen krok **vložit obrazový tvar** a splněn požadavek **přidat obrázek do Wordu**.

## Uložení dokumentu

Nakonec soubor uložte na disk. Uložený soubor obsahuje prázdný dokument, seskupený obdélník a vložené logo.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Když otevřete `GroupShape.docx` v Microsoft Word, uvidíte jedinou skupinu, která obsahuje světle šedý obdélník a logo umístěné vedle sebe. Výběrem jakékoli části skupiny můžete přesunout nebo změnit velikost celé kolekce, což dokazuje, že tvary jsou skutečně **seskupeny**.

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat, vložit a spustit. Nahraďte `YOUR_DIRECTORY` absolutní nebo relativní cestou, která existuje na vašem počítači.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Očekávaný výstup

* Soubor s názvem `GroupShape.docx` umístěný v `YOUR_DIRECTORY`.  
* Po otevření souboru ve Wordu se zobrazí jediná vizuální skupina obsahující šedý obdélník vlevo a `logo.png` vpravo.  
* Výběrem jakékoli části vizuální skupiny můžete přesunout nebo změnit velikost celé kolekce, což potvrzuje, že tvary jsou správně **seskupeny**.

## Časté otázky a řešení okrajových případů

| Question | Answer |
|---|---|
| **Mohu přidat více než dva tvary do stejné skupiny?** | Ano. Pro každý další `Shape` zavolejte `group.AppendChild(yourShape)`. Skupina může obsahovat libovolný počet kreslicích objektů. |
| **Co když chybí soubor s obrázkem?** | `SetImage` vyhodí `FileNotFoundException`. Zabalte volání do bloku try‑catch a poskytněte náhradní řešení (např. zástupný tvar). |
| **Je potřeba nastavit `WrapType` pro tvary?** | Ve výchozím nastavení jsou tvary inline. Pokud potřebujete plovoucí chování, nastavte `picture.WrapType = WrapType.Inline;` nebo jiný režim zalamování před přidáním do skupiny. |
| **Jak velikost dokumentu ovlivňuje hranice skupiny?** | Obdélník `Bounds` je definován v bodech (1 pt ≈ 1/72 in). Upravit velikost, pokud umístíte skupinu na jiný rozvrh stránky (např. A4 vs. Letter). |
| **Mohu znovu použít stejnou skupinu v jiném dokumentu?** | Ano. Klonujte skupinu pomocí `GroupShape cloned = (GroupShape)group.Clone(true);` a vložte ji do jiného `Document`. |

## Profesionální tipy

* **Znovu použijte `DocumentBuilder`** pro přidání textu před nebo za skupinu. Automaticky respektuje aktuální pozici kurzoru.  
* **Nastavte `Shape.StrokeColor`**, pokud potřebujete viditelný okraj kolem obdélníku.  
* **Používejte PNG s vysokým rozlišením** pro logo, aby nedocházelo k pixelaci při 

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}