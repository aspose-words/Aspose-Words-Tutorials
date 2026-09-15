---
category: general
date: 2026-09-14
description: Naučte se, jak skrýt tvar ve Wordu pomocí C# — včetně kódu pro vytvoření
  dokumentu Word, vložení obdélníkového tvaru do Wordu a programového skrytí tvaru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: cs
lastmod: 2026-09-14
og_description: Jak skrýt tvar ve Wordu pomocí C# — krok za krokem průvodce, který
  také ukazuje, jak vytvořit kód pro dokument Word a vložit obdélníkový tvar.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Jak skrýt tvar ve Word dokumentu pomocí C# kódu
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak skrýt tvar ve Word dokumentu pomocí C# kódu
url: /cs/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak skrýt tvar v dokumentu Word pomocí C# kódu

Pokud potřebujete **jak skrýt tvar** v souboru Word, tento tutoriál ukazuje kompletní řešení. Uvidíte, jak vytvořit dokument Word, vložit obdélníkový tvar, přidat elipsu a skrýt tuto elipsu, aby se při otevření souboru zobrazoval jen obdélník.

Průvodce pokrývá vše, co potřebujete – žádné externí odkazy, jen kód a vysvětlení. Na konci budete schopni vložit skrytou grafiku do libovolného dokumentu Word, který generujete programově.

## Požadavky

- .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.7+)
- Aspose.Words pro .NET (zkušební verze nebo licencovaná)  
  Nainstalujte jej přes NuGet: `dotnet add package Aspose.Words`
- Základní znalost C# a Visual Studio nebo jiného IDE dle vašeho výběru

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte novou konzolovou aplikaci a přidejte potřebné `using` direktivy. Tyto importy vám umožní přístup k třídám `Document`, `DocumentBuilder` a kreslicím třídám potřebným k manipulaci s tvary.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Proč je to důležité** – Import správných jmenných prostorů zabraňuje chybám při kompilaci a zpřístupňuje API pro vytváření tvarů a řízení jejich viditelnosti.

## Krok 2: Vytvoření nového dokumentu Word a builderu

`Document` představuje soubor, zatímco `DocumentBuilder` poskytuje plynulé API pro přidávání obsahu. Toto je první místo, kde aplikujete logiku **jak skrýt tvar**: potřebujete kontext dokumentu, než může existovat jakýkoli tvar.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Vysvětlení** – Objekt `Document` začíná prázdný. `DocumentBuilder` je umístěn na začátku prvního odstavce, připraven vkládat tvary nebo text.

## Krok 3: Vložení viditelného obdélníkového tvaru

Obdélník bude tvarem, který zůstane viditelný po otevření dokumentu. Jeho velikost, pozici a formátování můžete řídit přímo přes objekt tvaru.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Proč tento krok** – Přidání obdélníku demonstruje požadavek **insert rectangle shape word**. Nastavení `FillColor` a `LineColor` usnadní rozpoznání tvaru v konečném dokumentu.

## Krok 4: Vložení elipsy a její skrytí

Nyní přidáte tvar, který chcete skrýt. Vlastnost `Hidden` říká Wordu, aby tvar v UI nevykresloval, i když zůstává součástí struktury dokumentu.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Vysvětlení** – Nastavení `Hidden = true` je jádrem **hide shape in word**. Word tuto značku respektuje během běžného prohlížení a tisku, ale tvar je stále přístupný programově, pokud je potřeba.

## Krok 5: Uložení dokumentu

Nakonec zapíšete dokument na disk. Vyberte složku, do které máte právo zápisu, a dejte souboru jasný název, který odráží účel tutoriálu.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Výsledek** – Otevření `ShapeVisibility.docx` v Microsoft Word ukáže jen světle modrý obdélník. Skrytá elipsa se nezobrazí, což potvrzuje, že jste úspěšně zvládli **jak skrýt tvar** v souboru Word.

## Kompletní funkční příklad

Složení všech útržků dohromady vám poskytne jeden spustitelný program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Očekávaný výstup

- **Vizualizace**: Když otevřete `ShapeVisibility.docx`, uvidíte světle modrý obdélník umístěný blízko levého okraje. Žádná elipsa není viditelná.
- **Programově**: Skrytá elipsa zůstává v XML dokumentu (`<w:drawing>` element) s atributem `w:hidden`, který můžete ověřit rozbalením souboru jako zip a kontrolou `document.xml`.

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| *Mohu skrýt více tvarů?* | Ano. Nastavte `Hidden = true` u každého tvaru, který chcete skrýt. |
| *Budou skryté tvary tisknuty?* | Ve výchozím nastavení Word skryté objekty netiskne. Pokud je potřebujete tisknout, před tiskem odstraňte příznak `Hidden`. |
| *Je vlastnost hidden podporována ve starších verzích Wordu?* | Atribut `Hidden` je součástí standardu Office Open XML a funguje ve Word 2007 a novějších. |
| *Co když potřebuji přepínat viditelnost za běhu?* | Získejte tvar pomocí `document.GetChildNodes(NodeType.Shape, true)` a přepněte vlastnost `Hidden` podle vaší logiky. |

## Profesionální tipy

- **Výkon**: Pokud generujete mnoho dokumentů, znovu použijte jedinou instanci `DocumentBuilder` místo vytváření nové pro každý soubor.
- **Správa verzí**: Ukládejte vygenerované `.docx` soubory do složky pod správou verzí; skryté tvary mohou sloužit jako značky metadat pro následné zpracování.
- **Testování**: Automatizujte rychlý vizuální test konverzí DOCX do PDF pomocí Aspose.Words (`document.Save("out.pdf")`). PDF také skryje elipsu, což potvrzuje, že příznak hidden se přenáší i při převodech formátů.

## Závěr

Nyní víte **jak skrýt tvar** v dokumentu Word pomocí C#. Tutoriál vás provedl vytvořením dokumentu, **insert rectangle shape word**, přidáním elipsy a aplikací příznaku `Hidden` pro dosažení chování **hide shape in word**. S kompletním, spustitelným kódem můžete integrovat skrytou grafiku do jakéhokoli automatizovaného reportingu nebo šablonovacího workflow.

### Další kroky

- Prozkoumejte další vlastnosti tvarů, jako je rotace, stín a obtékání textem.  
- Kombinujte skryté tvary s vlastnostmi vlastního dokumentu pro vložení strojově čitelných dat.  
- Podívejte se na vzory **create word document code** pro tabulky, grafy a obsahové ovládací prvky a rozšiřte tak svou automatizační sadu nástrojů.

Neváhejte experimentovat s různými typy tvarů a nastaveními viditelnosti – váš další projekt automatizace Wordu je jen pár řádků kódu daleko!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}