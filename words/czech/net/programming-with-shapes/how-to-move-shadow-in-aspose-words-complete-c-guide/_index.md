---
category: general
date: 2026-05-01
description: Jak přesunout stín na tvaru v Aspose.Words pomocí C#. Naučte se přidat
  stín k tvaru, změnit rozostření, nastavit průhlednost a otočit stín během několika
  minut.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: cs
og_description: Jak přesunout stín na tvaru v Aspose.Words pomocí C#. Tento tutoriál
  vám ukáže, jak přidat stín k tvaru, změnit rozostření, nastavit průhlednost a otáčet
  stín.
og_title: Jak přesunout stín v Aspose.Words – Kompletní průvodce C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Jak přesunout stín v Aspose.Words – kompletní průvodce C#
url: /cs/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přesunout stín v Aspose.Words – Kompletní průvodce v C#

Už jste se někdy zamysleli, **jak přesunout stín** na tvar uvnitř dokumentu Word, aniž byste Word otevírali ručně? V mé každodenní práci jsem často potřeboval programově upravit stín tvaru — ať už pro vylepšenou zprávu nebo dynamickou šablonu. Dobrá zpráva? S Aspose.Words to zvládnete během několika řádků a zároveň se naučíte **přidat stín k tvaru**, **jak změnit rozostření**, **jak nastavit průhlednost** a **jak otočit stín** najednou.

V tomto tutoriálu projdeme reálný scénář: načteme existující DOCX, který už obsahuje tvar, upravíme pozici, měkkost, neprůhlednost a směr stínu a nakonec výsledek uložíme. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného .NET projektu, a pochopíte, proč je každá vlastnost důležitá.

## Požadavky – Co potřebujete před začátkem

- **Aspose.Words for .NET** (verze 23.12 nebo novější). Můžete jej získat z NuGet pomocí `Install-Package Aspose.Words`.
- Vývojové prostředí .NET 6+ (Visual Studio, VS Code, Rider — co vám vyhovuje).
- Vstupní soubor Word (`input.docx`), který již obsahuje alespoň jeden tvar (obdélník, kruh nebo obrázek stačí).
- Základní znalost syntaxe C# — nic složitého.

Pokud vám něco chybí, na chvíli zastavte a nainstalujte knihovnu; zbytek průvodce předpokládá, že balíček je již referencován.

## Krok 1: Načtení dokumentu a získání cílového tvaru – **Jak přesunout stín** začíná zde

Prvním krokem je načíst zdrojový dokument a najít tvar, který chceme upravit. Aspose.Words zachází s každým objektem (odstavci, tabulkami, tvary) jako s uzlem ve stromu, takže jej můžeme dotazovat přímo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Proč je to důležité:** Načíst dokument jen jednou a znovu použít stejnou instanci `Document` je efektivní. Volání `GetChild` je bezpečné, protože vrátí `null`, pokud je index mimo rozsah, což nám umožní elegantně ošetřit chybějící tvary.

## Krok 2: Úprava poloměru rozostření – Ovládněte **Jak změnit rozostření**

Měkký stín vypadá profesionálně, zatímco tvrdý okraj může působit levně. Vlastnost `BlurRadius` řídí měkkost v bodech (1 pt ≈ 1/72 palce). Zvýšíme ji na 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Tip:** Výchozí rozostření je 0,5 pt. Hodnota nad 5 pt je obvykle patrná, ale dejte pozor, aby nebyla příliš velká — může způsobit, že se tvar bude jevit odtržený od stránky.

## Krok 3: Nastavení průhlednosti – Odpověď na **Jak nastavit průhlednost**

Průhlednost určuje, jak moc je stín průhledný. Hodnota `0` znamená plně neprůhledný; `1` znamená zcela neviditelný. Pro decentní efekt použijeme `0.3` (30 % průhlednosti).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Proč by vás to mohlo zajímat:** Pokud je tvar tmavý, plně neprůhledný stín může zahltit podkladový text. Úprava průhlednosti zachová čitelnost dokumentu a zároveň přidá hloubku.

## Krok 4: Posunutí stínu – Jádro **Jak přesunout stín**

Vlastnost `Distance` určuje, jak daleko je stín odsazen od tvaru, měřeno v bodech. Větší vzdálenost posune stín dál, čímž vytvoří dramatický efekt.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **Co když potřebujete jen malý posun?** Nastavením `Distance` na `0` získáte stín přímo za tvarem, což se hodí pro efekty embosování.

## Krok 5: Otočení světelného zdroje – Řešení **Jak otočit stín**

Stíny nejsou jen přímo dolů; následují úhel světelného zdroje. Vlastnost `Angle` (ve stupních) otáčí stín kolem tvaru. Nakloníme ho o 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Rychlý experiment:** Zkuste `90` pro pravostranný stín nebo `-30` pro levostranný. Změna je okamžitá.

## Krok 6: Uložení dokumentu – Výsledek **Přidat stín k tvaru**

Po úpravě stínu dokument zapíšeme zpět na disk. Můžete přepsat originál nebo vytvořit nový soubor; příklad používá nový výstupní soubor.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Očekávaný výstup:** Otevřete `output.docx`. Stín tvaru bude měkčí, mírně odsazený, poloprůhledný a natočený o 45°. Pokud jej porovnáte vedle `input.docx`, rozdíl bude nepopiratelný.

### Kompletní funkční příklad (připravený ke zkopírování)

Níže je celý program v jednom bloku. Vložte jej do nového konzolového projektu, nahraďte `YOUR_DIRECTORY` skutečnou cestou ke složce a spusťte.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Často kladené otázky a okrajové případy

### Co když dokument obsahuje více tvarů?

Můžete projít všechny tvary ve smyčce:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Mohu přidat stín k tvaru, který jej zatím nemá?

Ano. Objekt `ShadowFormat` je vždy přítomen; stačí jej povolit:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Funguje to i s obrázky a SmartArt?

Ano. Každý uzel, který dědí z `Shape` — včetně obrázků, grafů a SmartArt — exponuje `ShadowFormat`. Stejné vlastnosti platí.

### Jak ovládat barvu stínu?

Použijte vlastnost `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Problémy s kompatibilitou?

Aspose.Words 23.12+ podporuje .NET 6, .NET Core 3.1 a .NET Framework 4.6.2+. Ukázané API je stabilní napříč těmito verzemi.

## Závěr

Právě jsme prošli **jak přesunout stín** na tvar pomocí Aspose.Words a zároveň jsme ukázali **přidat stín k tvaru**, **jak změnit rozostření**, **jak nastavit průhlednost** a **jak otočit stín**. Kompletní, spustitelný příklad vám umožní během několika sekund upravit stín libovolného tvaru a dodat dokumentům profesionální vzhled, aniž byste kdykoli otevírali Word.

Jste připraveni na další krok? Zkuste kombinovat tyto úpravy stínu s **podmíněným formátováním** — například aplikovat výraznější stín jen na nadpisy nebo na grafy, které překročí určitou velikost. Nebo prozkoumejte **gradientní výplně** samotného tvaru pro opravdu poutavý design.

Pokud narazíte na potíže, zanechte komentář níže. Šťastné programování a ať vaše stíny vždy dopadnou tam, kde chcete!

![Diagram ukazující efekt přesunu stínu na tvar – příklad jak přesunout stín](https://example.com/images/shadow-demo.png "příklad jak přesunout stín")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}