---
category: general
date: 2025-12-25
description: Jak přidat stín v C# pomocí jednoduchého příkladu kódu. Naučte se nastavit
  vzdálenost stínu, přizpůsobit barvu a vytvořit hloubku pro vaši grafiku.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: cs
og_description: Jak přidat stín v C# je vysvětleno krok za krokem. Postupujte podle
  průvodce a nastavte vzdálenost stínu, barvu a rozostření pro profesionálně vypadající
  tvary.
og_title: Jak přidat stín v C# – Kompletní průvodce programováním
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: Jak přidat stín v C# – Kompletní programovací průvodce
url: /cs/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat stín v C# – Kompletní programovací průvodce

Jak přidat stín v C# je častá potřeba, když chcete, aby vaše grafika vypadala živěji. V tomto tutoriálu projdeme přesné kroky, jak nastavit stín tvaru, včetně nastavení vzdálenosti stínu, úpravy rozostření a výběru správné barvy.  

Pokud jste někdy zírali na plochý obdélník a pomysleli si „tady by se hodil trochu hloubky“, jste na správném místě. Začneme s prázdným dokumentem, přidáme tvar a skončíme s vylepšeným stínem, který vypadá, jako by ho vytvořil designér. Žádné zbytečnosti, jen praktický, spustitelný příklad, který můžete dnes zkopírovat‑vložit.

## Co se naučíte

- Vytvořit nový dokument a programově vložit tvar.  
- Použít měkké rozostření na stín tvaru.  
- **Jak nastavit vzdálenost stínu**, aby se stín přirozeně posunul.  
- Vybrat barvu stínu, která funguje na libovolném pozadí.  
- Uložit výsledek jako PDF (nebo jakýkoli jiný požadovaný formát).  

### Předpoklady

- .NET 6.0 nebo novější (kód funguje s .NET Core i .NET Framework).  
- Aspose.Words pro .NET (bezplatná zkušební verze nebo licencovaná verze).  
- Základní znalost syntaxe C#.  

To je vše—žádné další knihovny, žádná magie. Pojďme na to.

![Příklad tvaru s měkkým černým stínem – jak přidat stín](https://example.com/placeholder-shadow.png "příklad jak přidat stín")

## Krok 1: Nastavení projektu a import jmenných prostorů

Nejprve vytvořte novou konzolovou aplikaci (nebo jakýkoli projekt C#) a přidejte NuGet balíček Aspose.Words:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Nyní otevřete `Program.cs` a načtěte požadované jmenné prostory:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **Tip:** Pokud používáte Visual Studio, IDE vám bude navrhovat `using` direktivy, jakmile začnete psát `Document`.

## Krok 2: Vytvořit nový dokument a přidat tvar

S připravenými knihovnami můžeme vytvořit objekt `Document` a umístit jednoduchý obdélník na první stránku.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

Proč obdélník? Je to neutrální plátno, které umožňuje posoudit efekt stínu bez rušivých elementů. Můžete nahradit `ShapeType.Rectangle` za `Ellipse` nebo `Star`—logika stínu zůstane stejná.

## Krok 3: Jak přidat stín – aplikovat rozostření, vzdálenost a barvu

Nyní přichází jádro tutoriálu: **jak přidat stín** k tomuto obdélníku. Aspose.Words poskytuje objekt `Shadow` u každého tvaru, který umožňuje ladit rozostření, vzdálenost a barvu.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Všimněte si komentáře `// 3b) Set the shadow's offset distance`. Tento řádek přímo odpovídá na **jak nastavit vzdálenost stínu**. Úpravou `shadow.Distance` řídíte vizuální mezeru mezi tvarem a jeho stínem, čímž napodobujete světelný zdroj umístěný pod určitým úhlem.

### Proč tyto hodnoty?

- **Blur = 5.0** – Jemné rozostření zabraňuje tvrdému siluetě, ale stále je viditelné.  
- **Distance = 3.0** – Udržuje stín dostatečně blízko, aby vypadal, že ho vrhá samotný tvar.  
- **Color = Black** – Zaručuje kontrast na světlých i tmavých pozadích.  

Klidně tyto hodnoty upravte; API přijímá libovolnou hodnotu typu `double`.

## Krok 4: Uložit dokument a ověřit výsledek

Po nastavení stínu soubor jednoduše zapíšeme na disk. Aspose.Words může exportovat do mnoha formátů; PDF je běžná volba pro sdílení.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

Otevřete `ShadowedShape.pdf` a měli byste vidět šedý obdélník s měkkým černým stínem mírně posunutým dolů‑vpravo. Pokud se stín jeví příliš slabý, zvyšte `shadow.Blur` nebo `shadow.Distance` a spusťte program znovu.

## Často kladené otázky a okrajové případy

### Co když potřebuji průhledný stín?

Použijte ARGB barvu s alfa kanálem menším než 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### Můžu použít stejný stín na více tvarů?

Určitě. Vytvořte pomocnou metodu:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Pak zavolejte `ApplyStandardShadow(rectangle);` pro každý tvar, který přidáte.

### Funguje to se staršími verzemi .NET Framework?

Ano. Aspose.Words 22.9+ podporuje .NET Framework 4.5 a vyšší. Stačí upravit soubor projektu podle potřeby.

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat do `Program.cs`. Překládá se a spustí ihned (za předpokladu, že je nainstalován NuGet balíček).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Spusťte program:

```bash
dotnet run
```

V adresáři projektu najdete `ShadowedShape.pdf`. Otevřete jej libovolným PDF prohlížečem a ověřte, že stín vypadá podle popisu.

## Závěr

Probrali jsme **jak přidat stín** k tvaru v C# od začátku až po konec a ukázali **jak nastavit vzdálenost stínu** spolu s rozostřením a barvou. Pouhých pár řádků kódu může vašim grafikám dodat profesionální, trojrozměrný vzhled—bez nutnosti externích designových nástrojů.

Nyní, když ovládáte základy, vyzkoušejte experimentovat:

- Změňte barvu stínu na jemnou modrou pro chladnější dojem.  
- Zvyšte rozostření pro snový, rozptýlený efekt.  
- Použijte stejnou techniku na grafy, obrázky nebo textová pole.  

Každá variace posiluje stejné základní koncepty, takže se rychle zorientujete v přizpůsobování stínů pro jakýkoli scénář.  

Máte další otázky? Zanechte komentář a šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}