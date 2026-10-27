---
category: general
date: 2026-09-08
description: Naučte se, jak vytvořit prázdný dokument Word, vložit obdélníkový tvar
  a seskupit více tvarů pomocí C#. Postupujte podle tohoto průvodce krok za krokem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: cs
lastmod: 2026-09-08
og_description: Vytvořte prázdný dokument Word, vložte obdélníkový tvar a seskupte
  více tvarů v C#. Tento tutoriál vás provede celým procesem.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Vytvořte prázdný dokument Word se seskupenými tvary v C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Jak vytvořit prázdný dokument Word se seskupenými tvary
url: /cs/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word se seskupenými tvary

Pokud potřebujete **vytvořit prázdný dokument Word**, který obsahuje vlastní grafiku, tento průvodce vám přesně ukáže, jak na to. Naučíte se **vložit obdélníkový tvar**, **seskupit více tvarů** a **přidat tvary do skupiny** pomocí Aspose.Words pro .NET.

Prázdný dokument vám poskytuje čisté plátno a seskupování tvarů vám umožní je přesouvat, měnit jejich velikost nebo otáčet jako jedním celkem. Tento tutoriál pokrývá každý krok – od inicializace dokumentu po uložení finálního souboru – takže můžete kód zkopírovat do svého projektu a okamžitě vidět výsledky.

## Co budete potřebovat

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
* Platná licence Aspose.Words pro .NET (bezplatná zkušební verze funguje pro testování)
* IDE, například Visual Studio 2022 nebo Visual Studio Code
* Základní znalost syntaxe C#

Žádné další NuGet balíčky nejsou vyžadovány kromě `Aspose.Words`.

## Jak vytvořit prázdný dokument Word

Prvním krokem je vytvořit objekt `Document`. Tento objekt představuje prázdný soubor `.docx`, který můžete upravovat pomocí `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Konstruktor `Document` vytvoří **prázdný dokument Word** v paměti. `DocumentBuilder` poskytuje plynulé API pro vkládání textu, obrázků a kreslicích objektů.

## Vložení obdélníkového tvaru do dokumentu

Dále přidejte obdélníkový tvar. Obdélník bude prvním potomkem skupiny, kterou vytvoříme později.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Volání `InsertShape` s `ShapeType.Rectangle` **vloží obdélníkový tvar** na aktuální pozici kurzoru. Šířka a výška jsou vyjádřeny v bodech (1 pt ≈ 1/72 in).

## Seskupení více tvarů dohromady

`GroupShape` funguje jako kontejner. Všechny podřízené tvary uvnitř skupiny se pohybují a transformují společně. Nejprve vytvořte skupinu a poté přidejte obdélník, který jsme právě vytvořili.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Metoda `InsertGroupShape` umístí prázdnou skupinu na kurzor builderu. Připojením obdélníku **seskupíme více tvarů** – obdélník se stane součástí interní kolekce uzlů skupiny.

## Přidání tvarů do skupiny a uložení souboru

Nyní přidejte druhý tvar – elipsu – aby bylo ukázáno, jak více objektů sdílí stejný kontejner. Poté dokument uložte.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Volání `InsertShape` **přidá tvary do skupiny**, když připojíte vrácený `Shape` k `GroupShape`. Uložení `Document` zapíše soubor `.docx`, který můžete otevřít v Microsoft Word, LibreOffice nebo v jakémkoli kompatibilním prohlížeči.

### Očekávaný výsledek

Když otevřete *GroupShapeDemo.docx*, uvidíte prázdnou stránku se seskupeným objektem, který obsahuje světle modrý obdélník a růžovou elipsu. Výběrem skupiny můžete přesunout oba tvary najednou, což potvrzuje, že **seskupení více tvarů** fungovalo podle očekávání.

## Proč používat GroupShape?

* **Atomární transformace** – Škálování, otáčení nebo přesun skupiny ovlivňuje všechny podřízené jednotně.
* **Logická organizace** – Udržuje související grafiku pohromadě, což usnadňuje údržbu struktury dokumentu.
* **Výkon** – Renderování jednoho kontejneru je často rychlejší než zpracování mnoha nezávislých tvarů.

Pokud budete později potřebovat upravit jeden podřízený tvar, můžete jej získat z `group.ChildNodes` podle indexu nebo podle jeho vlastnosti `Name`.

## Běžné varianty a okrajové případy

| Scenario                                 | How to adapt the code                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Různé typy tvarů**                | Nahraďte `ShapeType.Rectangle` nebo `ShapeType.Ellipse` libovolným jiným `ShapeType` |
| **Přidání textu uvnitř tvaru**           | Použijte `Shape.TextPath.Text = "Hello"` po vložení tvaru                    |
| **Nastavení úhlu rotace**             | `group.Rotation = 45;` (stupně)                                                 |
| **Uložení jako PDF místo DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Aplikace okraje na skupinu**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Profesionální tipy

* **Pojmenujte své tvary** – `rectangle.Name = "MyRect";` usnadňuje jejich pozdější vyhledání.
* **Používejte relativní umístění** – Nastavte `group.RelativeHorizontalPosition` na `RelativeHorizontalPosition.Page`, pokud chcete, aby skupina zůstala ukotvena k okrajům stránky.
* **Uvolňujte prostředky** – Zabalte `Document` do bloku `using`, když pracujete ve větších aplikacích, aby se rychle uvolnila neřízená paměť.

## Kompletní zdrojový kód pro rychlé kopírování

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Zkopírujte kód do nového konzolového projektu, obnovte NuGet balíček `Aspose.Words` a spusťte. Výstupní soubor se objeví ve složce projektu `bin/Debug/net6.0` (nebo ekvivalentní).

## Další kroky

Nyní, když můžete **vytvořit prázdný dokument Word**, **vložit obdélníkový tvar** a **seskupit více tvarů**, můžete zkoumat:

* Přidání **textových polí** do skupiny pro vytvoření popsaných diagramů.
* Exportování seskupené grafiky do obrázku pomocí `doc.Save("image.png", SaveFormat.Png)`.
* Kombinování skupin s tabulkami pro bohatě formátované zprávy.

Experimentujte s různými vlastnostmi tvarů, hierarchiemi skupin a formáty exportu, abyste plně využili kreslicí možnosti Aspose.Words.

--- 

*Pamatujte*: seskupování tvarů je výkonný způsob, jak udržet vaše dokumenty Word přehledné a váš kód udržovatelný. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření obdélníkového tvaru ve Wordu pomocí C# – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vkládání tvarů do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvoření skupinového tvaru v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}