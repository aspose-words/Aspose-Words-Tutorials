---
category: general
date: 2026-11-22
description: Programově vytvořit dokument Word v C# a vložit obdélníkový tvar, vložit
  více tvarů a zapsat tvary do Wordu pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: cs
lastmod: 2026-11-22
og_description: Programově vytvořit dokument Word v C# vložením obdélníkového tvaru,
  vložením více tvarů a zápisem tvarů do Wordu pomocí Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Programově vytvořit Word dokument s tvary v C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Programově vytvořit Word dokument s tvary v C#
url: /cs/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programaticky vytvořit Word dokument s tvary v C#

Pokud potřebujete **programaticky vytvořit Word dokument**, který obsahuje vlastní grafiku, tento průvodce vám ukáže, jak to provést pomocí Aspose.Words pro .NET. Naučíte se vložit obdélníkový tvar, přidat další tvary, seskupit je a nakonec zapsat tvary do Wordu – vše během několika řádků C#.

Vytvoření Word souboru s grafikou již nevyžaduje ruční úpravy nebo makro skripty. Na konci tohoto tutoriálu budete mít znovupoužitelnou metodu, která vytvoří soubor `.docx` obsahující obdélník a elipsu seskupené dohromady, připravené pro další zpracování nebo reportování.

## Co budete potřebovat

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)
- IDE jako Visual Studio 2022 (každý editor, který dokáže kompilovat C#, je v pořádku)

> **Pro tip:** Nainstalujte balíček pomocí příkazu CLI `dotnet add package Aspose.Words` předtím, než začnete kódovat.

## Programatické vytvoření Word dokumentu – přehled

Celkový tok se skládá ze tří logických fází:

1. **Inicializujte** nový `Document` a `DocumentBuilder`.  
2. **Vložte více tvarů** (obdélník a elipsu) a umístěte je do `GroupShape`.  
3. **Zapište tvary do Wordu** uložením `Document` do souboru `.docx`.

Každá fáze je v níže uvedeném kroku samostatně zabalena, takže můžete kód zkopírovat a vložit přímo do svého projektu.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Programaticky vytvořit Word dokument se seskupenými tvary"}

## Krok 1: Inicializace dokumentu a builderu

`Document` třída představuje celý Word soubor, zatímco `DocumentBuilder` poskytuje plynulé API pro přidávání obsahu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč je to důležité:* Vytvoření `Document` jako první vám poskytne čisté plátno. `DocumentBuilder` sleduje aktuální vkládací bod, což je nezbytné, když později připojujete tvary k hierarchii odstavců.

## Krok 2: Vložení kontejneru skupinového tvaru

`GroupShape` vám umožní zacházet s několika jednotlivými tvary jako s jednou jednotkou. To je užitečné, když je chcete přesouvat nebo měnit jejich velikost společně.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Vysvětlení:* `InsertGroupShape` vloží prázdný kontejner a automaticky jej nastaví jako aktuální tvar. Všechny následné vkládání tvarů bude přidáno do tohoto kontejneru, dokud skupinu neuzavřete.

## Vložení obdélníkového tvaru

Nyní přidáme první grafiku – obdélník. Tím splňujeme požadavek **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Obdélník dědí kontext formátování skupiny, takže se zobrazí uvnitř `GroupShape`. V případě potřeby můžete později nastavit barvu čáry, výplň nebo text.

## Vložení více tvarů

Pro předvedení schopnosti **insert multiple shapes** přidáme elipsu hned za obdélníkem. Můžete pokračovat v přidávání libovolného počtu tvarů (např. trojúhelníků, hvězd) před uzavřením skupiny.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

V tomto okamžiku skupina obsahuje dva odlišné tvary: obdélník a elipsu. Protože sdílejí stejného rodiče, můžete je přesouvat jako jednotku.

## Krok 3: Připojení skupinového tvaru k hierarchii odstavců

Word dokumenty ukládají obsah do stromu odstavců. Aby byl skupinový tvar viditelný v konečném souboru, musíme jej připojit k aktuálnímu odstavci.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Proč je tento krok nutný:* Bez připojení skupiny k odstavci existují tvary pouze v paměti a při uložení dokumentu jsou vynechány.

## Krok 4: Uložení dokumentu – zápis tvarů do Wordu

Nakonec uložíme `Document` z paměti na disk. Tím splníme cíl **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Když otevřete `GroupShape.docx` v Microsoft Wordu, uvidíte obdélník a elipsu seskupené dohromady, přesně tak, jak kód vložil.

### Očekávaný výstup

- Soubor pojmenovaný **GroupShape.docx** umístěný ve výstupní složce projektu.
- Uvnitř Word souboru: jeden odstavec obsahující seskupený obdélník (100 pt × 50 pt) a elipsu (80 pt × 40 pt). Výběrem libovolného tvaru vyberete celou skupinu.

## Řešení běžných okrajových případů

| Situace | Doporučení |
|-----------|----------------|
| **Různé DPI nebo velikost stránky** | Explicitně nastavte `builder.PageSetup.PaperSize` před vložením tvarů, aby nedošlo k neočekávanému škálování. |
| **Potřeba přesně umístit tvary** | Použijte `builder.MoveTo` k přesunutí vkládacího bodu, poté nastavte vlastnosti `groupShape.Left` a `groupShape.Top` (hodnoty jsou v bodech). |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument – vložit obdélníkový tvar a stín v C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Vytvořit Word dokument programaticky a seskupit tvary v C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programaticky vytvořit Word dokument se skupinovým tvarem](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}