---
category: general
date: 2026-03-27
description: Vytvořte dokument Word v C# a naučte se, jak přidat tvar, aplikovat na
  něj stín a nastavit vzdálenost stínu. Krok za krokem průvodce pro Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: cs
og_description: Vytvořte Word dokument v C# s obdélníkovým tvarem a vlastním stínem.
  Postupujte podle tohoto kompletního tutoriálu, abyste nastavili vzdálenost stínu
  a jeho styl.
og_title: Vytvořte Word dokument v C# – Přidejte tvar se stínem
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořit Word dokument v C# – Přidat tvar se stínem
url: /cs/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu C# – Přidání tvaru se stínem

Už jste někdy potřebovali **create word document c#**, který obsahuje pěkně stylovaný obdélník? Možná vytváříte šablonu zprávy a chcete jemný drop‑shadow, aby rozložení vyniklo. V tomto tutoriálu vás provedeme přesně tím – jak přidat tvar, aplikovat stín na tvar a dokonce doladit vzdálenost stínu pomocí Aspose.Words.

Začneme s prázdným dokumentem, vložíme obdélník, přiřadíme mu přednastavený stín a nakonec soubor uložíme. Na konci budete mít připravený .docx, který můžete otevřít ve Wordu a okamžitě vidět efekt. Žádné externí nástroje, jen čistý C# kód.

## Požadavky

- .NET 6 (nebo jakýkoli recentní .NET Framework) nainstalován.
- Visual Studio 2022 nebo VS Code s rozšířením C#.
- NuGet balíček Aspose.Words pro .NET (`Aspose.Words` verze 23.12 nebo novější).  
  Můžete jej přidat pomocí Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

To je vše – žádné další DLL ani COM interop nejsou potřeba.

## Krok 1: Inicializace nového dokumentu a builderu – *create word document c#* Základy

Nejprve potřebujeme objekt `Document`, který představuje Word soubor, a `DocumentBuilder` pro jeho úpravu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Proč je tento krok důležitý:** Třída `Document` je kontejner pro všechny části Wordu (stránky, styly, obrázky). Builder je high‑level API, které abstrahuje nízkoúrovňovou manipulaci s uzly, což usnadňuje **create word document c#** bez přímé práce s XML.

## Krok 2: Vložení obdélníkového tvaru – *how to create rectangle*  

Nyní umístíme obdélník na stránku. Velikost je vyjádřena v bodech (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** Pokud potřebujete jiný tvar, stačí zaměnit `ShapeType.Rectangle` za `ShapeType.Ellipse`, `ShapeType.Triangle` atd. Stejný kód funguje pro **how to add shape** libovolného typu.

## Krok 3: Aplikace přednastaveného stínu a jeho doladění – *apply shadow to shape*  

Aspose.Words obsahuje několik přednastavených formátů stínů. Použijeme `Preset1` a poté přizpůsobíme vzdálenost, rozostření, průhlednost a barvu.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Proč přizpůsobovat stín?** Vlastnost `Distance` určuje, jak daleko je stín od obdélníku – představte si to jako „zvednutí“, které vidíte v 3‑D renderingu. Změna `BlurRadius` změkčuje hrany, zatímco `Transparency` vám umožní vytvořit jemný, profesionální vzhled. Toto splňuje požadavek **set shadow distance** a ukazuje, jak **apply shadow to shape** flexibilně.

## Krok 4: Uložení dokumentu – *create word document c#* Dokončení

Nakonec zapíšeme dokument na disk. Přizpůsobte cestu ke složce, do které máte právo zapisovat.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Otevřete výsledný soubor v Microsoft Word a uvidíte světle modrý obdélník s měkkým šedým stínem posunutým o 5 pt. To je vizuální důkaz, že jste úspěšně **create word document c#** s upraveným tvarem.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# příklad ukazující obdélník se stínem"}

## Volitelné variace a okrajové případy

| Scénář | Co změnit | Proč je to důležité |
|----------|----------------|----------------|
| **Různý styl stínu** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Poskytuje dramatickejší vzhled bez dalšího kódu. |
| **Žádný preset – vlastní stín** | Vynechejte `Format` a nastavte `OffsetX`, `OffsetY` ručně. | Plná kontrola nad směrem a hloubkou. |
| **Více tvarů** | Zavolejte `builder.InsertShape` znovu před uložením. | Užitečné pro složité šablony s ikonami, logy atd. |
| **Kompatibilita se staršími verzemi Aspose** | Použijte třídu `ShadowEffect` (k dispozici ve verzi v20.x). | Zajišťuje, že váš kód běží na starších projektech. |
| **Ukládání jako PDF** | `document.Save("ShadowShape.pdf");` | Stejný rendering stínu se objeví v PDF výstupu. |

> **Často kladená otázka:** *Co když se stín ve Wordu neobjeví?*  
> Ujistěte se, že používáte recentní verzi Aspose.Words (≥ 22.9). Starší verze měly omezenou podporu stínů. Také ověřte, že dokument je otevřen v recentní verzi Wordu (2016+).

## Kompletní funkční příklad

Níže je kompletní program připravený ke zkopírování a vložení. Obsahuje všechny `using` direktivy, komentáře a ošetření chyb pro plynulý zážitek.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Spusťte program, přejděte do `C:\Temp\ShadowShape.docx` a uvidíte obdélník s přesně nastaveným stínem.

## Shrnutí a další kroky

- Nyní víte, jak **create word document c#**, vložit obdélník a **apply shadow to shape** s vlastním **set shadow distance**.  
- Příklad používá Aspose.Words, který abstrahuje složitosti OpenXML a zaručuje konzistentní vykreslování napříč verzemi Wordu.  
- Chcete jít dál? Zkuste kombinovat více tvarů, přidat text uvnitř obdélníku nebo exportovat stejný dokument jako PDF a podívat se, jak se stín přenáší.

### Související témata, která můžete prozkoumat

- **How to add shape** do záhlaví/patičky pro branding.  
- Použití **Aspose.Words** k programovému vkládání grafů a tabulek.  
- Přizpůsobení **shadow effects** na obrázcích místo vektorových tvarů.  
- Automatizace hromadného generování dokumentů pro faktury nebo certifikáty.

Neváhejte experimentovat, rozbít kód a pak ho znovu postavit – to je nejrychlejší způsob, jak si koncepty osvojit. Pokud narazíte na problém, zanechte komentář níže nebo si prohlédněte oficiální dokumentaci Aspose.Words pro podrobnější informace o API.

Šťastné programování a užívejte si, jak vaše Word soubory vypadají o něco uhlazeněji!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}