---
category: general
date: 2026-10-26
description: Vytvořte prázdný dokument Word v C# a naučte se vložit skupinu tvarů,
  poté přidejte do skupiny obdélníkový tvar. Tento průvodce krok za krokem popisuje
  seskupování více tvarů.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: cs
lastmod: 2026-10-26
og_description: Vytvořte prázdný dokument Word v C# a podívejte se, jak vložit skupinu,
  poté přidejte obdélníkový tvar. Ovládněte seskupování více tvarů pomocí kompletního
  příkladu kódu.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Vytvořte prázdný dokument Word a seskupte více tvarů – C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit prázdný dokument Word a seskupit více tvarů
url: /cs/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a seskupit více tvarů

Pokud potřebujete **vytvořit prázdný dokument Word** programově, tento tutoriál vám přesně ukáže, jak na to. Uvidíte, jak vložit skupinový tvar a poté **přidat obdélník** do této skupiny, což pokrývá celý pracovní postup od prázdného dokumentu po seskupený výkres.

Práce se soubory Word často zahrnuje uspořádání několika výkresů dohromady – představte si diagram složený z více tvarů. Na konci tohoto průvodce budete schopni **seskupit více tvarů**, vložit **obdélníkový tvar** a pochopit **jak vložit skupinu** a **jak přidat obdélník** čistým a znovupoužitelným způsobem.

## Co budete potřebovat

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
* **Aspose.Words for .NET** NuGet balíček (`Install-Package Aspose.Words`)
* Základní znalost C# a prostředí Visual Studio IDE (funguje jakékoli IDE)

> **Pro tip:** Aspose.Words běží zcela offline; po instalaci balíčku nepotřebujete internetové připojení.

## Krok 1: Vytvořit prázdný dokument Word

Prvním krokem je vytvořit prázdný objekt `Document`. Tento objekt představuje **prázdný dokument Word**, který později obohatíte o tvary.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité:* `Document` bez sekcí nebo odstavců je stále platný soubor .docx. Začít s čistým listem zaručuje, že žádné skryté formátování nezasahuje do tvarů, které později přidáte.

## Krok 2: Vložit skupinový tvar (jak vložit skupinu)

**Skupinový tvar** funguje jako kontejner, který může obsahovat další výkresové objekty. V Aspose.Words jej vytvoříte pomocí `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Proč použít skupinu?* Seskupování vám umožní přesouvat, otáčet nebo měnit velikost několika tvarů jako jedné jednotky. To je nezbytné pro diagramy, kde musí elementy zůstat zarovnané.

## Krok 3: Vložit obdélníkový tvar (vložit obdélníkový tvar)

Nyní přidejte obdélník do dokumentu. Metoda `InsertShape` vrací objekt `Shape`, který můžete později připojit ke skupině.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Proč obdélník?* Obdélníky jsou nejčastějším stavebním blokem pro vývojové diagramy, UI mock‑upy a zástupné grafiky. Rozměry jsou vyjádřeny v bodech (1 pt ≈ 1/72 palce).

## Krok 4: Přidat obdélník do skupiny (jak přidat obdélník)

Tvar vytvořený pomocí `InsertShape` žije přímo v těle dokumentu. Aby se stal součástí skupiny, zavolejte `AppendChild` na objektu `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Co se děje pod kapotou?* `AppendChild` přesune uzel obdélníku z hlavního příběhu dokumentu do interní kolekce skupiny, přičemž zachová jeho velikost a pozici relativně k počátku skupiny.

## Krok 5: Uložit dokument

Nakonec zapište soubor na disk. Výsledný `.docx` můžete otevřít v Microsoft Word a uvidíte seskupený obdélník.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Okrajový případ:** Pokud chcete do stejné skupiny přidat další tvary (např. kruhy, čáry), opakujte **Krok 3** a **Krok 4** pro každý nový tvar před uložením. Skupina automaticky upraví svůj ohraničující rámeček tak, aby zahrnovala všechny podřízené objekty.

## Jak seskupit více tvarů – rozšíření příkladu

Níže je rychlý úryvek, který přidá druhý tvar (elipsu) do stejné skupiny a demonstruje **seskupení více tvarů** v jednom dokumentu.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Když otevřete `GroupedShapeExample.docx`, uvidíte, že obdélník a elipsa se pohybují společně, když v Wordu vyberete skupinu.

## Často kladené otázky a řešení problémů

| Otázka | Odpověď |
|----------|--------|
| **Potřebuji licenci pro Aspose.Words?** | Bezplatná zkušební verze funguje bez licence, ale přidává vodoznak. Pro produkční nasazení použijte licenci, která vodoznak odstraní a odemkne plný výkon. |
| **Mohu umístit tvary přesně?** | Ano. Po vložení tvaru můžete nastavit vlastnosti `Shape.Left`, `Shape.Top`, `Shape.Width` a `Shape.Height`. |
| **Co když se po uložení obdélník zmizí?** | Ujistěte se, že voláte `group.AppendChild(rectangle)` *po* vložení obdélníku. Nejprve se tvar přidá do těla dokumentu a pak se přesune do skupiny. |
| **Je možné seskupovat tvary napříč různými sekcemi?** | Ne. Všechny tvary ve skupině musí patřit do stejného příběhu (sekce). Vytvořte samostatné skupiny pro každou sekci, pokud je to potřeba. |

## Shrnutí

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit skupinu**, **přidat obdélník** a **seskupit více tvarů** pomocí Aspose.Words pro .NET. Kompletní, spustitelný příklad výše můžete zkopírovat do konzolové aplikace a okamžitě spustit.

## Další kroky

* Experimentujte s velikostmi a barvami **obdélníkového tvaru** (`rectangle.FillColor = Color.LightBlue;`).  
* Prozkoumejte další typy tvarů (`ShapeType.Polygon`, `ShapeType.Line`) a obohaťte své diagramy.  
* Naučte se převést finální `.docx` do PDF (`doc.Save("output.pdf");`) pro distribuci.  
* Ponořte se do **jak přidat obdélník** do existujících dokumentů, které již obsahují text – použijte `DocumentBuilder.MoveTo` k umístění skupiny tam, kde ji potřebujete.

Neváhejte upravit kód podle vlastních potřeb pro reportování nebo generování diagramů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Jak vytvořit prázdný dokument Word a seskupit tvary v C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Jak seskupit tvary ve Wordu a přidat tvary do dokumentu Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Jak vytvořit obdélníkový tvar a seskupit tvary ve Wordu s Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}