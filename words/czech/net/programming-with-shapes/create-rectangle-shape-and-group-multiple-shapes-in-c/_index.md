---
category: general
date: 2026-09-18
description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí C#. Naučte se, jak
  přidat více tvarů, přidat tvary do skupiny a vložit skupinový tvar pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: cs
lastmod: 2026-09-18
og_description: Vytvořte obdélníkový tvar v souboru Word pomocí C#. Tento průvodce
  ukazuje, jak přidat více tvarů, jak je seskupit a jak vložit skupinový tvar pomocí
  Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Vytvořte obdélníkový tvar a seskupte tvary v C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Vytvořte obdélníkový tvar a seskupte více tvarů v C#
url: /cs/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru a seskupení více tvarů v C#

Pokud potřebujete **vytvořit obdélníkový tvar** v dokumentu Word, tento tutoriál ukazuje kompletní řešení. Uvidíte, jak **přidat více tvarů**, **přidat tvary do skupiny** a **vložit skupinový tvar** pomocí Aspose.Words API pro .NET.

Práce s tvary je běžnou požadavkou při programovém generování zpráv, smluv nebo marketingových materiálů. Na konci tohoto průvodce budete mít spustitelnou C# konzolovou aplikaci, která vytvoří soubor `.docx` obsahující obdélník, elipsu a skupinu, která oba tvary drží.

Jediné předpoklady jsou aktuální .NET SDK (6.0 nebo novější) a licencovaná kopie Aspose.Words pro .NET. Žádné další nástroje nejsou vyžadovány.

## Požadavky

- .NET 6.0 SDK nebo novější  
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)  
- Základní znalost syntaxe C#  

Balíček můžete nainstalovat následujícím příkazem:

```bash
dotnet add package Aspose.Words
```

## Krok 1: Vytvoření obdélníkového tvaru s Aspose.Words

Prvním krokem je vytvořit objekt `Shape` typu `Rectangle`. Tento objekt představuje vizuální obdélník, který se objeví v dokumentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Proč je to důležité:** `ShapeType.Rectangle` říká Aspose.Words, aby vykreslil geometrický obdélník. Nastavení `Width` a `Height` určuje jeho velikost v bodech (1 bod = 1/72 palce). Přidání výplně a barvy obrysu dělá tvar viditelným bez potřeby dalšího stylování.

## Krok 2: Přidání více tvarů do dokumentu

Po obdélníku můžete vytvořit libovolný počet dalších tvarů. V tomto příkladu přidáme elipsu, abychom ukázali, jak funguje **přidání více tvarů**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Proč je to důležité:** Každé volání `new Shape` vytvoří nezávislý kreslicí objekt. Vkládáním po sobě vytváříte kolekci tvarů, kterou lze později seskupit nebo umístit jednotlivě.

## Krok 3: Přidání tvarů do skupiny

Seskupování tvarů zjednodušuje správu rozvržení, protože skupina se chová jako jediný uzel. Tento krok ukazuje, jak **přidat tvary do skupiny** pomocí `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Proč je to důležité:** `GroupShape` funguje jako kontejner. Když přesunete, otočíte nebo změníte velikost skupiny, všechny podřízené tvary se automaticky přizpůsobí. Ohraničující rámeček (200 × 200 bodů) definuje souřadnicový prostor pro podřízené tvary.

## Krok 4: Vložení skupinového tvaru do dokumentu

Nyní, když skupina obsahuje obdélník a elipsu, musíte **vložit skupinový tvar** na požadované místo. Builder již umístil prázdnou skupinu, ale můžete ji také vložit jinde, pokud je to potřeba.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Proč je to důležité:** Úprava `Left` a `Top` přesune celou skupinu v rámci stránky. Uložení dokumentu zapíše hierarchii tvarů do souboru `.docx`, který lze otevřít v Microsoft Word, LibreOffice nebo jakémkoli kompatibilním prohlížeči.

## Kompletní spustitelný příklad

Níže je celý program, který kombinuje všechny kroky. Zkopírujte kód do nového konzolového projektu a spusťte jej, aby se vygeneroval soubor `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Očekávaný výstup:**  
Otevření `GroupShapeExample.docx` zobrazí jedinou skupinu obsahující světle‑modrý obdélník a světle‑korálovou elipsu, obě umístěné uvnitř kontejneru 200 × 200 bodů. Skupinu lze v aplikaci Word vybrat jako jeden objekt, což potvrzuje, že **přidání tvarů do skupiny** bylo úspěšné.

## Časté varianty a okrajové případy

| Situace | Doporučená úprava |
|-----------|------------------------|
| Různé typy tvarů (např. `ShapeType.Line`) | Vytvořte tvar s požadovaným `ShapeType` a nastavte jeho geometrii odpovídajícím způsobem. |
| Potřeba otočit tvar | Použijte `shape.Rotation = 45;` (stupně) před přidáním do skupiny. |
| Větší dokumenty s mnoha skupinami | Znovu použijte jedinou instanci `DocumentBuilder`; vyhněte se vytváření nového builderu pro každou skupinu, aby se snížila paměťová zátěž. |
| Ukládání do PDF místo DOCX | Zavolejte `doc.Save("output.pdf", SaveFormat.Pdf);` po vložení skupiny. |

**Tip:** Vždy nastavujte explicitní hodnoty `Left` a `Top` pro skupinu, pokud potřebujete přesné umístění. Pokud je vynecháte, skupina zdědí aktuální pozici kurzoru builderu, což může vést k neočekávaným výsledkům rozvržení.

## Závěr

Nyní víte, jak **vytvořit obdélníkový tvar**, **přidat více tvarů**, **přidat tvary do skupiny** a **vložit skupinový tvar** v dokumentu Word pomocí C#. Kompletní příklad demonstruje celý pracovní postup od vytvoření dokumentu až po uložení finálního souboru.  

Dále prozkoumejte související témata, jako je **umístění tvarů relativně k textu**, **aplikace obtékání textu** a **export seskupených tvarů do PDF**. Tyto rozšíření vám umožní vytvářet sofistikované, programově řízené rozvržení dokumentů s Aspose.Words.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}