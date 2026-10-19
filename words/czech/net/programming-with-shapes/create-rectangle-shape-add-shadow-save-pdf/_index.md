---
category: general
date: 2026-02-24
description: Vytvořte obdélníkový tvar v C# pomocí Aspose.Words, přidejte tvaru stín
  a uložte dokument jako PDF. Naučte se, jak přidat stín a během několika minut uložit
  PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: cs
og_description: Vytvořte obdélníkový tvar v C# s Aspose.Words, poté přidejte stín
  k tvaru a uložte dokument jako PDF – kompletní, krok‑za‑krokem průvodce.
og_title: Vytvořte obdélníkový tvar, přidejte stín a uložte PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Vytvořte obdélníkový tvar, přidejte stín a uložte PDF
url: /cs/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte obdélníkový tvar, přidejte stín a uložte jako PDF

Už jste někdy potřebovali **vytvořit obdélníkový tvar** v dokumentu Word a zároveň chtěli pěkný vržený stín a výstup do PDF? Nejste v tom sami. V mnoha projektech zaměřených na reporty nebo generování faktur dělá vizuální dokonalost — například jemný stín — rozdíl mezi „dalším souborem“ a „dokumentem profesionální úrovně“.

V tomto tutoriálu si projdeme přesně to: pomocí **Aspose.Words for .NET** vytvoříme obdélníkový tvar, přidáme k němu stín a nakonec **uložíme dokument jako PDF**. Na konci budete mít připravenou konzolovou aplikaci v C#, která vygeneruje PDF s vybarveným obdélníkem, a pochopíte, jak upravit stín nebo změnit možnosti exportu.

## Co budete potřebovat

- .NET 6 SDK (nebo jakákoli novější verze .NET) — API funguje stejně i na .NET Framework 4.x.  
- NuGet balíček **Aspose.Words for .NET** (`Aspose.Words`) — nainstalujte jej pomocí `dotnet add package Aspose.Words`.  
- Editor kódu — Visual Studio, VS Code nebo Rider budou stačit.  

Žádné další licenční kroky pro tento příklad; režim bezplatného hodnocení stačí k zobrazení PDF výstupu.

## Krok 1: Nastavte projekt a importujte jmenné prostory

Nejprve vytvoříme konzolový projekt a přineseme třídy, které budeme potřebovat.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Proč je to důležité:* `Document` a `DocumentBuilder` nám poskytují plátno, zatímco `Shape` a `ShadowFormat` umožňují kreslit a stylovat obdélník. Importování těchto typů hned na začátku udržuje pozdější kód přehledný.

## Krok 2: **Vytvořte obdélníkový tvar** s požadovanými rozměry

Nyní skutečně vytvoříme prázdný dokument a vložíme obdélník. Všimněte si, že metoda `InsertShape` vrací objekt `Shape`, který můžeme okamžitě stylovat.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Vysvětlení*: Velikost je vyjádřena v bodech (1 pt = 1/72 in). Přizpůsobte čísla podle svého rozvržení. Také tvaru přiřadíme světle‑modrou výplň, aby stín dobře vynikl.

## Krok 3: **Přidejte stín k tvaru** — doladěte efekt

Stín není jen „zapnuto/vypnuto“. Můžete řídit jeho barvu, rozostření, vzdálenost, směr a dokonce i průhlednost. Zde je praktická konfigurace, která funguje dobře pro většinu reportů.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Proč byste mohli změnit tyto hodnoty:*  
- **BlurRadius** — zvyšte pro snový efekt, snižte pro ostrý okraj.  
- **Direction** — 0° směřuje doprava, 90° dolů, 180° doleva atd. Otočte podle rozvržení stránky.  
- **Transparency** — nastavte na `0` pro plný stín, `0.5` pro poloprůhledný atd.

### Jak přidat stín — alternativní přístupy

Pokud potřebujete **vícevrstvý stín** (např. tmavší vnější stín a světlejší vnitřní), můžete vytvořit druhý tvar, posunout jej a nastavit jiný `ShadowFormat`. Nebo pro rychlý vzhled „bez rozostření“ nastavte `BlurRadius = 0`.

## Krok 4: **Uložte dokument jako PDF** — finální export

S připraveným obdélníkem a jeho stínem je posledním krokem zapsat soubor jako PDF. Aspose.Words provádí konverzi interně; stačí zavolat `Save` s požadovaným formátem.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tip*: Pokud potřebujete řídit kompatibilitu PDF (PDF/A, PDF/X) nebo vložit fonty, použijte přetíženou metodu:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

To je podstata **jak uložit PDF** v kostce.

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat do `Program.cs`. Překompiluje se a spustí tak, jak je (jen se ujistěte, že výstupní složka existuje).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Očekávaný výsledek

Otevřete vygenerovaný soubor `ShadowRectangle.pdf`. Uvidíte jedinou stránku se světle‑modrým obdélníkem, měkkým šedým stínem posunutým o 45° dolů‑doprava a čistými okraji. PDF by mělo být čitelné v libovolném moderním prohlížeči (Adobe Acrobat, Edge, Chrome).

![Vytvořit obdélníkový tvar se stínem v PDF](/images/shadow-rectangle.png "Vytvořit obdélníkový tvar se stínem")

*(Alt text obrázku obsahuje primární klíčové slovo pro SEO.)*

## Často kladené otázky a řešení okrajových případů

**Co když se stín v PDF neukáže?**  
Ujistěte se, že používáte aktuální verzi Aspose.Words (≥23.3). Starší verze měly chybu, kde některé vlastnosti stínu byly při konverzi do PDF ignorovány.

**Mohu změnit barvu stínu, aby odpovídala mé značce?**  
Ano — stačí nahradit `System.Drawing.Color.Gray` libovolnou barvou, např. `Color.FromArgb(128, 0, 0, 255)` pro poloprůhlednou modrou.

**Jak přidám stín k jiným tvarům (elipsa, hvězda atd.)?**  
`ShadowFormat` funguje pro jakýkoli objekt `Shape`. Po vytvoření tvaru získáte jeho `ShadowFormat` a nastavíte požadované vlastnosti.

**Co s DPI nebo škálovacími problémy?**  
Renderování PDF respektuje velikost tvaru v bodech. Pokud potřebujete výstup vyššího rozlišení (pro tisk), upravte rozměry tvaru nebo nastavte `PdfSaveOptions.ImageResolution`.

**Mohu exportovat do jiných formátů, např. PNG?**  
Ano — stačí zavolat `document.Save("output.png", SaveFormat.Png)`. Stín bude vykreslen stejným způsobem.

## Profesionální tipy a osvědčené postupy

- **Znovu použijte builder**: Pokud přidáváte více tvarů, udržujte jedinou instanci `DocumentBuilder`; je to levnější než vytvářet mnoho nových.
- **Dávkové ukládání**: Při generování mnoha PDF ve smyčce opakovaně používejte stejný objekt `PdfSaveOptions`, abyste se vyhnuli zbytečným alokacím.
- **Testování**: Vždy po uložení PDF otevřete a ověřte, že se stín zobrazuje podle očekávání. Některé prohlížeče stíny vykreslují mírně odlišně; Adobe Acrobat je nejspolehlivější referencí.
- **Výkon**: U velkých dokumentů vypněte automatické zalomení stránky při `DocumentBuilder.InsertShape` nastavením `builder.PageSetup.DifferentFirstPageHeaderFooter = false`, pokud to nepotřebujete.

## Závěr

Probrali jsme vše, co potřebujete k **vytvoření obdélníkového tvaru**, **přidání stínu k tvaru** a **uložení dokumentu jako PDF** pomocí Aspose.Words for .NET. Kód je stručný, koncepty jsou vysvětleny a nyní máte solidní základ pro experimentování s dalšími tvary, styly stínů a možnostmi exportu.  

Další kroky? Zkuste nahradit obdélník za zaoblený —

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}