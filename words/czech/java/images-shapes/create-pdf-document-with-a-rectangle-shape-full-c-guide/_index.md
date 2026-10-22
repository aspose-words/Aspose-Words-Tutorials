---
category: general
date: 2026-03-25
description: Vytvořte PDF dokument v C# a naučte se, jak přidat obdélníkový tvar,
  nastavit barvu výplně, upravit velikost tvaru a nastavit průhlednost tvaru během
  několika kroků.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: cs
og_description: Vytvořte PDF dokument v C# a zjistěte, jak přidat obdélník, nastavit
  jeho barvu výplně, velikost a průhlednost pro dokonalý výstup PDF.
og_title: Vytvořte PDF dokument s obdélníkovým tvarem – C# tutoriál
tags:
- C#
- PDF
- Aspose.Words
title: Vytvořte PDF dokument s obdélníkovým tvarem – kompletní průvodce C#
url: /cs/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření PDF dokumentu s obdélníkovým tvarem – Kompletní průvodce v C#

Už jste někdy potřebovali **vytvořit PDF dokument**, který obsahuje vlastní tvar, ale nevedeli jste, kde začít? Nejste v tom sami. Ať už vytváříte generátor reportů nebo marketingový leták, schopnost programově nakreslit obdélník, nastavit jeho barvu výplně, upravit jeho velikost a dokonce nastavit průhlednost může vaše PDF vypadat mnohem profesionálněji.

> **Pro tip:** Stejný přístup funguje i s jinými typy tvarů (elipsa, čára atd.) — stačí vyměnit `ShapeType.RECTANGLE` za ten, který potřebujete.

## Co budete potřebovat

| Požadavek | Proč je to důležité |
|--------------|----------------|
| **.NET 6+** (nebo .NET Framework 4.6+) | Knihovna Aspose.Words cílí na moderní runtime. |
| **Aspose.Words for .NET** NuGet balíček | Poskytuje třídy `Document`, `Shape`, `ShadowEffect` a související. |
| **C# IDE** (Visual Studio, Rider, VS Code) | Usnadňuje ladění a spuštění ukázky. |
| **Základní znalost C#** | Porozumíte syntaxi bez nutnosti hlubokého ponoru. |

Knihovnu můžete nainstalovat pomocí příkazové řádky:

```bash
dotnet add package Aspose.Words
```

A to je vše — žádné další DLL, žádné nativní závislosti. Jakmile je balíček na místě, kód níže se zkompiluje a spustí.

## Postupná implementace

Níže rozdělíme proces do pěti logických kroků. Každý krok má jasný nadpis (aby jej AI modely mohly indexovat) a krátký kódový blok, který můžete zkopírovat a vložit přímo.

### ## 1. Vytvoření PDF dokumentu a příprava plátna

Prvním krokem je vytvořit instanci `Document`. Považujte ji za prázdné plátno, které se nakonec stane vaším PDF souborem.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Proč?** `Document` obsahuje všechny sekce, odstavce a tvary. Začátek s čistým objektem zaručuje, že v dokumentu nebudou skryté artefakty z předchozích běhů.

### ## 2. Přidání obdélníkového tvaru – nastavení barvy výplně a velikosti tvaru

Nyní vytvoříme obdélník, nastavíme mu jasně žlutou výplň a definujeme jeho rozměry. Tím pokryjeme jak **přidání obdélníkového tvaru**, tak **nastavení barvy výplně** a **nastavení velikosti tvaru**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Poznámka:** Šířka/výška jsou měřeny v bodech (1 bod = 1/72 palce). Přizpůsobte tato čísla tak, aby vyhovovala vašemu rozvržení.

### ## 3. Aplikace vnějšího stínu a nastavení průhlednosti tvaru

Stíny přidávají hloubku a řízení jejich opacity je podstatou **nastavení průhlednosti tvaru**. Níže nakonfigurujeme šedý vnější stín s 30 % průhledností.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Proč nastavit průhlednost?** 30 % průhledný stín vypadá decentně a zabraňuje tomu, aby obdélník na stránce vypadal „plochě“.

### ## 4. Vložení tvaru do těla dokumentu

Nyní vložíme obdélník do prvního odstavce první sekce dokumentu. Tento krok vše propojí.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Speciální případ:** Pokud potřebujete tvar na nové stránce, přidejte před připojením tvaru řádek `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;`.

### ## 5. Uložení dokumentu jako PDF soubor

Nakonec uložíme strukturu v paměti do fyzického PDF souboru. Soubor bude zapsán do složky, kterou určíte.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Po spuštění programu se objeví soubor s názvem `shadow.pdf`. Po otevření uvidíte žlutý obdélník s měkkým šedým stínem posunutým o 4 body — přesně to, co náš kód popisuje.

> **Očekávaný výstup:** Jednostránkový PDF, kde je obdélník umístěn blízko levého horního rohu stránky, vyplněn žlutě, velikosti 200 × 100 bodů a s poloprůhledným vnějším stínem.

## Kompletní funkční příklad (připravený ke zkopírování)

Níže je celý zdrojový soubor, připravený k vložení do nového konzolového projektu.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** Nahraďte `YOUR_DIRECTORY` absolutní cestou jako `C:\Temp` nebo relativní cestou jako `.\output`. Program vytvoří složku, pokud ještě neexistuje.

## Často kladené otázky (FAQ)

**Q: Můžu změnit pozici obdélníku na stránce?**  
A: Určitě. Nastavte `rectangle.Left` a `rectangle.Top` (obě měřeno v bodech) před připojením k odstavci.

**Q: Co když potřebuji průhlednou výplň místo průhledného stínu?**  
A: Použijte `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — první argument je alfa kanál (0‑255), kde 128 dává přibližně 50 % průhlednost.

**Q: Funguje to s .NET Core?**  
A: Ano. Aspose.Words podporuje .NET Standard 2.0+, takže můžete spustit stejný kód na .NET 6, .NET 7 nebo .NET Framework 4.6+.

**Q: Jak mohu přidat více tvarů?**  
A: Stačí opakovat kroky 2‑4 pro každý tvar, případně je vložit do různých odstavců nebo sekcí.

## Závěr

Právě jsme **vytvořili PDF dokument** od nuly, **přidali obdélníkový tvar**, **nastavili jeho barvu výplně**, **definovali jeho velikost** a **upravili průhlednost tvaru**, abychom dosáhli vylepšeného stínového efektu. Ukázkový kód je samostatný, běží za méně než minutu a demonstruje základní koncepty, které budete potřebovat pro složitější rozvržení PDF.

Jste připraveni na další výzvu? Zkuste nahradit obdélník tvarem se zaoblenými rohy, vložit obrázek dovnitř tvaru nebo automaticky vygenerovat obsah. Stejné API vám umožní vrstvit text, obrázky a vektory — možnosti jsou neomezené.

Pokud se vám tento průvodce hodil, dejte mu hvězdičku na GitHubu, sdílejte ho s kolegou nebo zanechte komentář s vašimi vlastními variantami. Šťastné programování!

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}