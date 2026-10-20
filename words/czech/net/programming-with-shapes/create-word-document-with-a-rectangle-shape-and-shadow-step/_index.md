---
category: general
date: 2026-03-01
description: Vytvořte dokument Word pomocí Aspose.Words a naučte se, jak přidat obdélníkový
  tvar, jak přidat stín, jak nastavit průhlednost a jak vytvořit tvar – vše v C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: cs
og_description: Vytvořte Word dokument pomocí Aspose.Words v C#. Naučte se, jak přidat
  obdélníkový tvar, aplikovat vnější stín a nastavit průhlednost během několika kroků.
og_title: Vytvořte dokument Word s obdélníkovým tvarem a stínem – průvodce
tags:
- Aspose.Words
- C#
- Document Generation
title: Vytvořte Word dokument s obdélníkovým tvarem a stínem – krok za krokem
url: /cs/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu s obdélníkovým tvarem a stínem – krok za krokem průvodce

Už jste někdy potřebovali **vytvořit Word dokument**, který obsahuje vlastní stylovaný obdélník? Možná vytváříte šablonu zprávy a chcete jemný drop‑shadow, aby rozložení vyniklo. Nejste jediní – vývojáři se neustále ptají: „Jak přidat obdélníkový tvar a stín programově?“ Dobrou zprávou je, že s Aspose.Words to můžete udělat během několika řádků.

V tomto tutoriálu projdeme celý proces: od vytvoření prázdného Word souboru, přes přidání obdélníkového tvaru, až po nastavení vnějšího stínu s průhledností. Na konci budete mít připravený `Shadow.docx`, který můžete otevřít ve Wordu a okamžitě vidět výsledek. Žádné externí nástroje, žádné složité XML – jen čistý C# kód a srozumitelná vysvětlení.

## Co se naučíte

- **Jak vytvořit shape** objekty ve Word dokumentu pomocí Aspose.Words.
- **Jak přidat rectangle shape** do odstavce, aniž byste narušili existující obsah.
- **Jak přidat shadow** (vnější stín) a ovládat jeho barvu, posun, rozostření a průhlednost.
- **Jak nastavit transparency** na stín, aby vypadal profesionálně.
- Tipy, úskalí a varianty, které můžete potřebovat v reálných projektech.

### Požadavky

- .NET 6.0 nebo novější (API funguje také s .NET Framework 4.6+).
- Aspose.Words pro .NET nainstalovaný přes NuGet (`Install-Package Aspose.Words`).
- Základní znalost syntaxe C# – nic složitého, jen běžné `using` příkazy a vytváření objektů.

> **Pro tip:** Pokud používáte Visual Studio, povolte „nullable reference types“, abyste včas zachytili potenciální chyby s null‑referencemi.

## Krok 1 – Vytvoření prázdného Word dokumentu

Pro **vytvořit Word dokument** začínáme třídou `Document`. Představte si ji jako prázdné plátno; později můžete přidávat sekce, odstavce, tabulky nebo tvary.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Proč potřebujeme čerstvou instanci `Document`? Protože každý tvar, odstavec nebo styl žije uvnitř modelu objektů dokumentu (DOM). Začátek s čistým dokumentem zaručuje, že přidaný obdélník nebude kolidovat s existujícím obsahem.

## Krok 2 – Definice obdélníkového tvaru

Nyní **jak vytvořit shape** obdélník. Konstruktor `Shape` přijímá vlastnící dokument a typ tvaru. Také nastavíme šířku a výšku v bodech (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Možná se ptáte: „Mohu místo bodů použít centimetry?“ API akceptuje jen body, ale můžete převést: `points = centimeters * 28.35`. Tento malý převod je užitečný, když zarovnáváte tvary k okrajům stránky.

## Krok 3 – Přidání vnějšího stínu a nastavení průhlednosti

Zde se děje kouzlo: **jak přidat shadow** a **jak nastavit transparency** na tento stín. Vlastnost `ShadowFormat` vám dává plnou kontrolu.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Proč tato nastavení?**  
- **Transparency** umožňuje, aby textura podkladové stránky prosvítala, což zabraňuje příliš těžkému vzhledu stínu.  
- **OffsetX/Y** vytváří iluzi, že tvar je zvednutý nad stránkou.  
- **BlurRadius** změkčuje hrany – bez něj by byl stín tvrdým obdélníkem, což vypadá nepřirozeně.  

Pokud potřebujete dramatický efekt, zvyšte `OffsetX/Y` na 10 a `BlurRadius` na 8. Naopak pro jemný nádech nechte hodnoty na 2 a 2.

## Krok 4 – Vložení tvaru do dokumentu

Nyní **přidáme rectangle shape** do prvního odstavce dokumentu. Pokud dokument neobsahuje žádný obsah, `FirstParagraph` se vytvoří automaticky.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Co když chcete tvar uvnitř konkrétní buňky tabulky nebo pozdějšího odstavce? Stačí najít ten uzel (`doc.GetChild(NodeType.Paragraph, index, true)`) a zavolat na něj `AppendChild`. Stejný objekt tvaru lze klonovat, pokud potřebujete více kopií.

## Krok 5 – Uložení dokumentu

Nakonec **vytvoříme Word dokument** na disku. Použijte cestu, která vyhovuje vašemu prostředí; příklad používá zástupný text.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Když otevřete `Shadow.docx` v Microsoft Word, uvidíte světle šedý obdélník s měkkým vnějším stínem posunutým dolů a doprava. Průhlednost stínu 30 % zajišťuje, že nebude dominovat stránce.

![Create word document with a shadowed rectangle shape](image.png "Vytvořit Word dokument s obdélníkovým tvarem se stínem")

*Image alt text: vytvořit Word dokument s obdélníkovým tvarem se stínem*

## Kompletní, připravený k spuštění kód

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Žádné chybějící části, žádné „viz dokumentace pro více informací“.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Očekávaný výsledek

- Soubor pojmenovaný **Shadow.docx** se objeví ve cílové složce.  
- Po otevření ve Wordu se zobrazí obdélník (200 × 100 pt) s tmavě šedým vnějším stínem.  
- Stín je posunut o 5 pt horizontálně i vertikálně, je rozostřený a má 30 % průhlednost.

## Časté otázky a okrajové případy

| Question | Answer |
|----------|--------|
| **Mohu změnit barvu stínu, aby odpovídala mé značce?** | Samozřejmě – stačí nahradit `System.Drawing.Color.DarkGray` libovolnou `Color`, kterou preferujete, např. `Color.FromArgb(255, 0, 120, 215)` pro modrý akcent. |
| **Co když potřebuji vnitřní stín místo vnějšího?** | Nastavte `ShadowFormat.Style = ShadowStyle.InnerShadow`. Ostatní vlastnosti se chovají stejně. |
| **Je průhlednost podporována ve starších verzích Wordu?** | Ano. Aspose.Words zapíše odpovídající XML, které Word 2007+ rozumí. Starší verze mohou hodnotu průhlednosti ignorovat, ale stín se stále zobrazí. |
| **Mohu přidat více tvarů s různými stíny?** | Jistě – vytvořte nové instance `Shape`, nakonfigurujte každý stín samostatně a připojte je k požadovaným uzlům. |
| **Jaký je dopad na výkon při stovkách tvarů?** | Vytváření mnoha tvarů může zvýšit spotřebu paměti. Znovu použijte jednu instanci `Document` a tvary přidávejte v cyklu; uvolněte dočasné objekty, pokud narazíte na tlak na paměť. |

## Tipy pro reálné projekty

- **Batch generation:** Při generování zpráv pro mnoho uživatelů vytvořte jedinou šablonu `Document` a klonujte ji pro každou iteraci. Nahraďte zástupné znaky před připojením tvarů.  
- **Dynamic sizing:** Použijte rozměry stránky (`document.FirstSection.PageSetup.PageWidth`) k výpočtu velikosti tvaru relativně k stránce, což zajistí konzistentní rozvržení napříč různými formáty papíru.  
- **Testing:** Vždy otevřete vygenerovaný `.docx` ve Wordu po změně parametrů stínu. Vizuální zpětná vazba je rychlejší než hádání čísel.

## Další kroky

Nyní, když už víte **jak přidat rectangle shape**, **jak přidat shadow** a **jak nastavit transparency**, můžete zkoumat:

- Přidání **gradient fills** do tvarů (`Shape.FillFormat`).  
- Vkládání **pictures** do tvarů pro efekty vodoznaku.  
- Použití **tables** k zarovnání více stínovaných tvarů do mřížky.  
- Export stejného dokumentu do PDF (`document.Save("output.pdf")`) při zachování stínů.

Každý z těchto kroků staví na stejných základních konceptech, takže se budete cítit jistě při rozšiřování kódu.

### Shrnutí

Začali jsme **vytvořením Word dokumentu** s Aspose.Words, poté **jak vytvořit shape** obdélník, aplikovali **jak přidat shadow**, upravili **jak nastavit transparency** a výsledek uložili. Celý proces zapadá do kompaktního, znovupoužitelného vzoru, který můžete přizpůsobit libovolnému automatizačnímu scénáři.

Neváhejte experimentovat – měňte barvy, hrajte si s posuny nebo skládáním několika tvarů dohromady. Když narazíte na problém, vraťte se k výše uvedeným sekcím; jsou navrženy jako rychlá reference. Šťastné programování a ať vaše dokumenty vždy vypadají profesionálně!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}