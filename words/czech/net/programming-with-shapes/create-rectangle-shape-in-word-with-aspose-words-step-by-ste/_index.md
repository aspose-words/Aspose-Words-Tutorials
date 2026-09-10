---
category: general
date: 2025-12-29
description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí Aspose.Words C#. Naučte
  se nastavit průhlednost tvaru, nastavit barvu stínu a snadno uložit Word dokument.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: cs
og_description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí Aspose.Words C#.
  Tento průvodce ukazuje, jak nastavit průhlednost tvaru, nastavit barvu stínu a uložit
  Word dokument.
og_title: Vytvořte obdélníkový tvar ve Wordu – kompletní tutoriál Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Vytvořte obdélníkový tvar ve Wordu s Aspose.Words – krok za krokem
url: /cs/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru ve Wordu – Kompletní tutoriál Aspose.Words

Už jste někdy potřebovali **vytvořit obdélníkový tvar** v dokumentu Word, ale nevedeli jste, kde začít? Nejste v tom sami; mnoho vývojářů narazí na tento problém při automatizaci reportů nebo faktur. V tomto průvodci vás provedeme přesné kroky, jak vytvořit obdélníkový tvar, nastavit průhlednost tvaru, nastavit barvu stínu a nakonec **uložit dokument Word** pomocí Aspose.Words pro .NET.

Probereme vše od počátečního objektu dokumentu až po finální soubor `.docx` na disku, takže na konci budete schopni **programově vytvořit dokument Word** bez hádání. Žádné externí odkazy, jen samostatné řešení, které můžete zkopírovat‑vložit do svého projektu.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
- Základní znalost syntaxe C#
- IDE podle vašeho výběru (Visual Studio, Rider, VS Code, atd.)

> **Tip:** Pokud používáte bezplatnou zkušební verzi Aspose.Words, knihovna přidá vodoznak do výstupního souboru. Pro produkci budete potřebovat platnou licenci.

## Krok 1: Inicializace dokumentu a builderu

Prvním krokem vytvoříme nový, prázdný dokument Word a `DocumentBuilder`, který nám umožní vkládat obsah. Builder si představte jako virtuální pero, které kreslí na stránku.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Proč je to důležité:** Bez `DocumentBuilder` byste museli manipulovat s nízkoúrovňovým stromem uzlů přímo, což je náchylné k chybám a těžší na čtení.

## Krok 2: Vytvoření obdélníkového tvaru

Nyní skutečně **vytvoříme obdélníkový tvar**. Metoda `InsertShape` přijímá výčtový typ `ShapeType`, šířku a výšku (v bodech). Vrácený objekt `Shape` nám později umožní doladit vizuální vlastnosti.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

V tomto okamžiku je obdélník pevná černá krabice ukotvená k aktuálnímu odstavci. Můžete ji později přesunout, změnit její velikost nebo dokonce otočit, pokud budete potřebovat.

![create rectangle shape with shadow](/images/rectangle-shadow.png "A Word document showing a rectangle shape with a gray shadow")

*Obrázkový alt text: create rectangle shape with shadow in a Word document*

## Krok 3: Nastavení průhlednosti tvaru

Průhlednost je úroveň „průhlednosti“ výplně tvaru. Aspose.Words používá vlastnost `Transparency` v rozmezí od `0.0` (neprůhledný) do `1.0` (zcela průhledný). Zde **nastavíme průhlednost tvaru** na 40 %, aby podkladový text zůstal čitelný.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Okrajový případ:** Pokud potřebujete úplně neviditelný tvar, ale stále chcete, aby se zobrazil stín, nastavte `Transparency` na `1.0` a dejte tvaru nenulovou šířku obrysu.

## Krok 4: Konfigurace stínu

Jemný vržený stín přidává hloubku. **Nastavíme barvu stínu** na středně šedou, upravíme jeho rozostření a posuneme ho o několik bodů vodorovně i svisle.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Proč je to důležité:** Stín, který je příliš ostrý nebo příliš tmavý, může vypadat jako tisková chyba. Upravit `Blur` a `Transparency`, dokud nepůsobí přirozeně.

## Krok 5: Uložení dokumentu Word

Nakonec **uložíme dokument Word** na disk. Metoda `Save` automaticky určuje formát souboru podle přípony; `.docx` je moderní formát OpenXML.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Pokud složka neexistuje, Aspose.Words vyhodí `ArgumentException`. Ujistěte se, že cesta je platná, nebo vytvořte adresář předem.

## Kompletní funkční příklad

Níže je kompletní, připravený program, který spojuje všechny kroky. Zkopírujte jej do nového konzolového projektu a stiskněte **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Očekávaný výsledek

Otevřete `ShadowRectangle.docx` v Microsoft Word. Měli byste vidět světle šedý obdélník s měkkým, mírně posunutým stínem, oba vykreslené s 40 % průhledností. Tvar leží na prázdné stránce, připravený pro další obsah.

## Časté otázky a varianty

**Co když potřebuji jiný tvar?**  
Nahraďte `ShapeType.Rectangle` libovolnou jinou hodnotou výčtu (`Ellipse`, `Triangle`, `Star`, atd.). Zbytek kódu zůstane stejný.

**Mohu změnit barvu obrysu?**  
Ano — použijte `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` a volitelně nastavte `rectangleShape.StrokeWeight = 1.5;`.

**Jak umístit tvar na konkrétní místo na stránce?**  
Nastavte `rectangleShape.WrapType = WrapType.None;` a pak upravte vlastnosti `rectangleShape.Left` a `rectangleShape.Top` (hodnoty jsou v bodech).

**Je možné přidat text uvnitř obdélníku?**  
Rozhodně. Po vytvoření tvaru můžete zavolat `rectangleShape.AppendChild(new Paragraph(document))` a poté přidat `Run` s vaším textem. Nezapomeňte nastavit vlastnosti `rectangleShape.TextBox`, pokud chcete bohatší formátování.

## Profesionální tipy a úskalí

- **Licencujte co nejdříve:** Pokud zapomenete aplikovat licenci, Aspose.Words vloží vodoznak na první stránku, což může během testování zmást.
- **Tip pro výkon:** Při generování mnoha dokumentů ve smyčce znovu použijte jedinou instanci `Document` a po každém uložení zavolejte `document.RemoveAllChildren();`, abyste předešli nadměrnému zatížení GC.
- **Viditelnost stínu:** Na obrazovkách s nízkým rozlišením může jemný stín vypadat neviditelně. Pro ladění zvýšte `Blur` nebo `OffsetX/Y`, poté pro produkci snižte.

## Další kroky

Nyní, když umíte **vytvořit obdélníkový tvar**, **nastavit průhlednost tvaru**, **nastavit barvu stínu** a **uložit dokument Word**, zvažte rozšíření tutoriálu:

- Přidejte více tvarů a seskupte je.
- Vložte obdélník do buňky tabulky pro rozvržení reportu.
- Kombinujte tvar s `DocumentBuilder.InsertHtml` pro překrytí HTML‑stylovaného obsahu.
- Prozkoumejte další vizuální efekty jako `Glow` nebo `Reflection` pro bohatší dokumenty připomínající UI.

Experimentujte, porušujte věci a pak je dolaďte — programová generace dokumentů je hřiště, kde se vizuální design setkává s kódem.

---

*Šťastné programování! Pokud narazíte na nějaké potíže, zanechte komentář níže a společně to vyřešíme.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}