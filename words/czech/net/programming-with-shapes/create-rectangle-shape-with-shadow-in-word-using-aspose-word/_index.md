---
category: general
date: 2026-03-06
description: Vytvořte obdélníkový tvar ve Wordu a přidejte stín tvaru pomocí Aspose.Words.
  Naučte se, jak vložit obdélník do Wordu a jak přidat stín k tvaru v C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: cs
og_description: Vytvořte obdélníkový tvar ve Wordu a přidejte tvaru stín pomocí Aspose.Words.
  Podrobný návod, jak vložit obdélník do Wordu a jak přidat stín k tvaru.
og_title: Vytvořte obdélníkový tvar se stínem ve Wordu pomocí Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Vytvořte obdélníkový tvar se stínem ve Wordu pomocí Aspose.Words
url: /cs/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru s stínem ve Wordu pomocí Aspose.Words

Už jste někdy potřebovali **vytvořit obdélníkový tvar** v dokumentu Word, ale nevedeli jste, jak mu dodat ten profesionální vzhled? Nejste v tom sami — většina vývojářů narazí na stejný problém, když poprvé chtějí přidat vizuální šmrnc do automatizovaných dokumentů. Dobrá zpráva? S Aspose.Words pro .NET můžete **vytvořit obdélníkový tvar** a **přidat stín tvaru** během několika řádků C#.

V tomto tutoriálu vás provedeme přesně **jak vložit obdélník do Wordu**, poté ukážeme **jak přidat stín k tvaru**, aby vynikl ze stránky. Na konci budete mít připravený `Shadow.docx`, který můžete otevřít ve Wordu a uvidíte šedě zbarvený obdélník s jemným vrženým stínem. Žádné externí obrázky, žádné ruční úpravy — pouze kód.

## Co se naučíte

- Přesné C# příkazy potřebné k **vytvoření obdélníkového tvaru** s Aspose.Words.  
- Jak povolit a nakonfigurovat stín pomocí objektu `Shadow`.  
- Proč je každá vlastnost důležitá (např. `Transparency`, `Blur`, `Angle`).  
- Časté úskalí (jednotky, kompatibilita verzí) a rychlé opravy.  
- Kompletní program připravený ke zkopírování a spuštění ještě dnes.

### Požadavky

- .NET 6+ (nebo .NET Framework 4.7+).  
- Aspose.Words pro .NET 23.10 nebo novější (NuGet balíček je `Aspose.Words`).  
- Základní znalost C# a Visual Studio (nebo libovolného IDE, které preferujete).  

Pokud už máte vše připravené, pojďme rovnou na to.

---

## Krok 1: Nastavení projektu a import jmenných prostorů

Nejprve vytvořte novou konzolovou aplikaci (nebo použijte existující) a přidejte NuGet balíček Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Nyní přidejte požadované jmenné prostory do souboru `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Tip:** Pokud cílíte na .NET 6+, můžete povolit globální `using` direktivy, abyste se vyhnuli opakování těchto řádků v každém souboru.

---

## Krok 2: **Vytvoření obdélníkového tvaru** v prázdném dokumentu Word

Začneme s čerstvým objektem `Document` a `DocumentBuilder`, který jej upravuje. Metoda `InsertShape` builderu je místem, kde se děje kouzlo.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Proč 200 × 100 bodů? Ve Wordu jeden bod odpovídá 1/72 palce, takže obdélník má přibližně 2,8 × 1,4 palce — dostatečně velký, aby byl vidět, ale ne přehnaně. Můžete tyto hodnoty změnit podle svého rozvržení; jen pamatujte, že se měří v **bodech**, ne v pixelech.

---

## Krok 3: **Přidání stínu k tvaru** — konfigurace vzhledu

Nyní, když máme obdélník, přidáme mu decentní šedý stín. Objekt `Shadow` patří k `Shape` a poskytuje několik užitečných vlastností.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Co jednotlivé vlastnosti dělají

| Vlastnost | Efekt | Typické hodnoty |
|-----------|------|-----------------|
| **Enabled** | Zapíná/vypíná stín | `true` nebo `false` |
| **Color** | Základní barva stínu | libovolná `System.Drawing.Color` |
| **Transparency** | Průhlednost (0 = plná, 1 = neviditelná) | 0.0 – 1.0 |
| **Blur** | Měkčení okraje | 0 – 10 (vyšší = měkčí) |
| **Distance** | Vzdálenost mezi tvarem a stínem | 0 – 20 bodů |
| **Angle** | Směr, ze kterého světlo přichází | 0 – 360 stupňů |
| **Size** | Měřítko stínu vzhledem k tvaru | 0 – 200 % |

> **Proč se tímto nastavením zabývat?**  
> Jemné doladění stínu vám umožní splnit firemní grafické směrnice (např. decentní 20 % průhlednost pro profesionální vzhled) bez nutnosti používat externí grafické editory.

---

## Krok 4: Uložení dokumentu a ověření výsledku

Nakonec zapíšeme soubor na disk. Můžete zvolit libovolnou složku; jen nahraďte `YOUR_DIRECTORY` skutečnou cestou.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Otevřete `Shadow.docx` v Microsoft Word a měli byste vidět šedý obdélník s jemným vrženým stínem posunutým pod úhlem 45°. Tento vizuální prvek dává tvaru dojem „zvednutého“ ze stránky — právě to, co očekáváte od profesionální zprávy nebo faktury.

---

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat a vložit do `Program.cs`. Žádné části nechybí; program se přeloží a spustí tak, jak je.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Očekávaný výstup

- **Soubor:** `Shadow.docx` umístěný ve složce, odkud se projekt spouští.  
- **Vzhled:** Jeden obdélník uprostřed stránky, výchozí bílá výplň a šedý stín posunutý o 4 body doprava a dolů, mírně rozostřený pro přirozený vzhled.

---

## Často kladené otázky a okrajové případy

### 1. Co když potřebuji jinou jednotku (např. centimetry)?

Aspose.Words pracuje v bodech, ale můžete převést centimetry na body pomocí jednoduchého vzorce:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Funguje to se staršími verzemi Aspose.Words?

API `Shadow` bylo zavedeno ve verzi 14.0. Pokud používáte starší verzi, budete muset provést upgrade přes NuGet. Zbytek kódu (vytváření tvarů) je stabilní již mnoho let, takže nenarazíte na zásadní změny.

### 3. Můžu přidat stín i k jiným tvarům (např. kruhům)?

Určitě — každý objekt `Shape` má vlastnost `Shadow`. Stačí nahradit `ShapeType.Rectangle` za `ShapeType.Ellipse` nebo `ShapeType.Cloud` a použít stejná nastavení stínu.

### 4. Co když potřebuji barevný stín (např. modrý pro značku)?

Vyměňte `Color.Gray` za libovolnou `Color`, kterou chcete:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Nezapomeňte upravit `Transparency`, aby barva nebyla příliš dominantní.

---

## 🎨 Vizualizační souhrn

![vytvořit obdélníkový tvar se stínem ve Wordu pomocí Aspose.Words](image-placeholder.png "vytvořit obdélníkový tvar se stínem ve Wordu pomocí Aspose.Words")

*Alt text: vytvořit obdélníkový tvar se stínem ve Wordu pomocí Aspose.Words*

Ukázkový snímek (placeholder) zobrazuje finální dokument — pouze obdélník a jeho jemný šedý stín.

---

## Závěr

Nyní už víte, jak **vytvořit obdélníkový tvar** v Word souboru, **přidat stín tvaru** a doladit každý vizuální aspekt pomocí Aspose.Words pro .NET. Krátký program, který jsme vytvořili, pokrývá celý workflow — od

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}