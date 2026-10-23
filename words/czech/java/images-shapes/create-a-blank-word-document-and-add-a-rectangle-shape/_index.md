---
category: general
date: 2026-10-23
description: Vytvořte prázdný dokument Word, přidejte obdélníkový tvar a skryjte tvar
  ve Wordu pomocí Aspose.Words. Krok za krokem kód pro vývojáře .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: cs
lastmod: 2026-10-23
og_description: Vytvořte prázdný dokument Word, přidejte obdélníkový tvar a skryjte
  tvar ve Wordu pomocí Aspose.Words. Postupujte podle kompletního příkladu v C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Vytvořte prázdný dokument Word a přidejte skrytý obdélníkový tvar
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Vytvořte prázdný dokument Word a přidejte obdélníkový tvar
url: /cs/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a přidejte obdélníkový tvar

Pokud potřebujete **vytvořit prázdný dokument Word**, tento průvodce vám ukáže, jak to provést pomocí Aspose.Words pro .NET. Také se naučíte **jak vložit tvar**—konkrétně obdélník—a **skrýt tvar ve Wordu**, aby neovlivňoval rozvržení.

Tutoriál prochází každý řádek kódu, vysvětluje, proč je každý krok důležitý, a pokrývá běžné úskalí, jako je viditelnost skrytých tvarů v různých režimech zobrazení Wordu. Na konci budete mít plně funkční soubor `.docx`, který obsahuje skrytý obdélníkový tvar, který můžete později odhalit nebo programově manipulovat.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
- Vývojové prostředí, například Visual Studio 2022 nebo VS Code s rozšířeními C#
- Základní znalost syntaxe C# a konceptů dokumentů Word

Další instalace Office není vyžadována, protože Aspose.Words funguje zcela v paměti.

## Vytvořte prázdný dokument Word

Prvním krokem je vytvořit prázdný objekt `Document`. Tento objekt představuje soubor Word, který zatím neobsahuje žádné sekce, odstavce ani obsah.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Proč je to důležité:**  
Prázdný `Document` vám poskytuje čisté plátno. Pokud začnete z existující šablony, skryté tvary mohou zdědit nechtěné styly. Začátek od nuly zajišťuje, že obdélníkový tvar, který později přidáte, bude jediný obsah, který ovládáte.

## Přidejte obdélníkový tvar do dokumentu

Dále potřebujeme `DocumentBuilder` k umístění obsahu do dokumentu. Metoda `InsertShape` builderu je standardní způsob **vložení tvaru** objektů, jako jsou obdélníky, kruhy nebo vlastní kresby.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Proč je to důležité:**  
`InsertShape` vrací objekt `Shape`, který můžete dále konfigurovat (barva, styl čáry atd.). Rozměry jsou udávány v bodech (1 bod = 1/72 palce), což odpovídá internímu měřicímu systému Wordu.

### Volitelné: stylizovat obdélník (volitelné)

Pokud chcete, aby obdélník měl viditelný okraj, když jej později odhalíte, můžete nastavit jeho tloušťku čáry a barvu:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Tyto řádky jsou volitelné, protože tvar bude skrytý v dalším kroku.

## Skryjte tvar ve Wordu

Word umožňuje skrytí tvarů z rozvržení, přičemž zůstávají součástí objektového modelu dokumentu. Nastavení vlastnosti `Hidden` na `true` způsobí, že tvar bude neviditelný v normálním zobrazení, ale stále jej lze vybrat pomocí API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Proč je to důležité:**  
Skrytý tvar je užitečný pro ukládání metadat, zástupných objektů pro pozdější zpracování nebo podmíněného obsahu, který odhalíte jen za určitých okolností (např. při generování finální zprávy). Tvar zůstává v souboru, takže jej můžete programově později odkrýt pomocí `rectangleShape.Hidden = false;`.

## Uložte dokument

Nakonec zapište dokument na disk. Přípona souboru určuje formát Wordu; `.docx` je moderní formát Open XML.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Výsledek:**  
Otevření `HiddenShape.docx` v Microsoft Word ukáže prázdnou stránku. Obdélník není viditelný, ale pokud přejdete na **Domů → Vybrat → Panel výběru**, uvidíte v seznamu tvar a můžete přepínat jeho viditelnost.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny potřebné `using` direktivy a komentáře.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výstup:**  

- Konzole vypíše cestu uložení.  
- `HiddenShape.docx` se otevře jako prázdná stránka ve Wordu.  
- Obdélníkový tvar existuje, ale je skrytý; můžete jej ověřit přes *Panel výběru* nebo programově nastavením `Hidden = false` a znovu otevřením souboru.

## Časté otázky a okrajové případy

| Question | Answer |
|----------|--------|
| **Mohu skrýt jiné typy tvarů?** | Ano. Jakýkoli `Shape` (např. `ShapeType.Ellipse`, `ShapeType.Picture`) podporuje vlastnost `Hidden`. |
| **Zvýší skrytý tvar velikost souboru?** | Nárůst je zanedbatelný (pár kilobajtů), protože data tvaru jsou uložena jako XML v balíčku `.docx`. |
| **Co když potřebuji, aby se tvar zobrazoval jen v náhledu tisku?** | Použijte vlastnost `Shape.IsPrint` místo `Hidden`. Nastavením `IsPrint = false` skryjete tvar z tištěného výstupu, ale zůstane viditelný na obrazovce. |
| **Jak tvar později odkrýt?** | Načtěte dokument, najděte tvar (např. podle `Shape.Name`), pak nastavte `shape.Hidden = false;` a uložte. |
| **Funguje to s formátem .doc (binárním)?** | Ano, Aspose.Words může uložit do `.doc` pomocí `document.Save("file.doc");`. Skrytý příznak je zachován. |

## Profesionální tipy

- **Pojmenujte své tvary**: `rectangleShape.Name = "PlaceholderRectangle";` usnadní pozdější vyhledání pomocí `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Dávkové zpracování**: Pokud potřebujete přidat skryté tvary do mnoha dokumentů, zabalte kód do metody a znovu použijte instanci `DocumentBuilder`.
- **Výkon**: Vytvoření tvaru je levné, ale časté ukládání velkých dokumentů může být omezeno I/O. Zvažte použití `MemoryStream` pro mezilehlé zpracování.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **přidat obdélníkový tvar** a **skrýt tvar ve Wordu** pomocí Aspose.Words pro .NET. Tato technika vám umožní vložit neviditelné zástupce, které můžete později odhalit nebo manipulovat, což je užitečné pro dynamické generování zpráv, podmíněný obsah a šablonování dokumentů.

Další kroky, které můžete prozkoumat:

- Nahraďte obdélník obrázkem nebo grafem pomocí `ShapeType.Picture`.
- Použijte **jak vložit tvar** v sekcích hlavičky/patičky pro zástupce ve stylu vodoznaku.
- Kombinujte skryté tvary s validací dat založenou na **přidání obdélníkového tvaru** (např. ukládání JSON do vlastnosti `AlternativeText` tvaru).

Šťastné programování a nebojte se experimentovat s dalšími typy tvarů a možnostmi viditelnosti, aby vyhovovaly vašim potřebám automatizace dokumentů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}