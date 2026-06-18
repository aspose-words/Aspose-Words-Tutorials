---
category: general
date: 2026-04-10
description: jak nastavit stín na tvaru v C# – naučte se, jak aplikovat vržený stín,
  změnit průhlednost, upravit rozostření a přidat stín tvaru pomocí Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: cs
og_description: jak nastavit stín na tvar v C# – tento tutoriál ukazuje, jak aplikovat
  vržený stín, změnit průhlednost, upravit rozostření a přidat stín tvaru s jasnými
  ukázkami kódu.
og_title: Jak nastavit stín na tvar v C# – kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Automation
title: Jak nastavit stín na tvar v C# – průvodce krok za krokem
url: /cs/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak nastavit stín na tvar v C# – Kompletní průvodce

Už jste se někdy zamysleli **jak nastavit stín** na tvar, když programově vytváříte Word dokument? Nejste sami. Mnoho vývojářů narazí na problém, když potřebují jemný vržený stín pro textové pole, logo nebo výzvu, a dokumentace API je poněkud skromná.  

V tomto tutoriálu projdeme celý proces: od načtení souboru `.docx`, získání prvního `Shape`, až po aplikaci vrženého stínu, úpravu jeho průhlednosti, nastavení poloměru rozostření a nakonec správné umístění. Na konci budete mít znovupoužitelný úryvek, který funguje s Aspose.Words .NET 2023 nebo novějším, a pochopíte *proč* je každá vlastnost důležitá.

## Co budete potřebovat

- **Aspose.Words for .NET** (NuGet package `Aspose.Words`) – knihovna, která poskytuje třídy `Document`, `Shape` a `ShadowFormat`.  
- **.NET 6+** (nebo .NET Framework 4.7.2) – jakékoli moderní runtime stačí.  
- Jednoduchý Word soubor (`input.docx`), který již obsahuje alespoň jeden tvar, například textové pole.  
- Visual Studio, VS Code nebo vaše oblíbené IDE.

To je vše. Žádné další nástroje třetích stran, žádné COM interop, jen čistý C#.

![how to set shadow example](image-placeholder.png){:alt="jak nastavit stín na tvaru ve Word dokumentu"}

## Jak nastavit stín – Přehled

Základní myšlenkou **jak nastavit stín** je manipulovat s objektem `ShadowFormat`, který patří k `Shape`. Představte si `ShadowFormat` jako miniaturu „stylového listu“ pro samotný stín: říká rendereru, zda je stín viditelný, jakou barvu má mít, jak je průhledný, jak je rozostřený a kde se nachází vzhledem k tvaru.  

Níže je *kompletní* spustitelný program. Klidně jej zkopírujte a vložte do konzolové aplikace, stiskněte **F5** a sledujte, jak se stín objeví v uloženém souboru `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Proč jsou tato nastavení důležitá

- **Visible** – Bez zapnutí tohoto příznaku jsou všechny ostatní vlastnosti ignorovány.  
- **Color** – Tmavě šedá napodobuje typický UI vržený stín; můžete použít libovolnou `Color`.  
- **Transparency** – 0,3 poskytuje *jemný* vzhled a zároveň zachovává čitelnost tvaru.  
- **Size** – Ovládá rozostření; hodnota 6 je obvykle dostatečná pro profesionální dojem.  
- **Distance & Angle** – Společně definují *posun*; 2 pt při 45° vytváří jemný diagonální stín.

To je podstata **jak nastavit stín**. Dále rozložíme každý komponent, abyste mohli **aplikovat vržený stín**, **změnit průhlednost**, **upravit rozostření** a **přidat stín tvaru** samostatně.

---

## Apply Drop Shadow to a Shape

Když se lidé ptají „jak **aplikovat vržený stín** v C#?“, často potřebují jen přepínač viditelnosti a barvu. Následující úryvek izoluje tyto dva řádky:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Tip:** Pokud cílíte na starší verze Wordu (2003‑2007), držte se standardních barev. Některé exotické hodnoty ARGB mohou být ignorovány starším renderérem.

---

## Jak změnit průhlednost stínu

Průhlednost je vyjádřena jako **float mezi 0 a 1**. Hodnota **0** znamená zcela neprůhledný stín; **1** ho učiní neviditelným. Většina designérů se drží hodnot **0,2‑0,4** pro přirozený vzhled.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Hraniční případy

- **Negative values** – Aspose.Words je ořízne na 0, ale je lepší vstup validovat.  
- **Values > 1** – Ořízne na 1, čímž efektivně skryje stín.  

Pokud potřebujete, aby uživatelé vybírali procenta, nejprve je převeďte:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Jak upravit rozostření (Size) stínu

Vlastnost **Size** řídí poloměr rozostření. Větší čísla vytvářejí měkčí, rozptýlenější stín. Měří se v bodech (pt), ne v pixelech.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Kdy použít malé vs. velké rozostření

- **Small blur (2‑4 pt)** – Vhodné pro UI‑stylové výzvy, kde chcete ostrý okraj.  
- **Large blur (8‑12 pt)** – Vhodné pro tištěné zprávy nebo když je tvar daleko od pozadí.

---

## Přidat stín tvaru – Umístění a směr

Poslední část **add shape shadow** je posun. Dvě vlastnosti spolupracují:

| Property | Meaning |
|----------|---------|
| **Distance** | Jak daleko je stín od tvaru (v bodech). |
| **Angle**    | Směr posunu (0° = doprava, 90° = dolů, 180° = doleva, 270° = nahoru). |

Příklad, který vytvoří jemný pravý dolní stín:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Můžete experimentovat s úhly, abyste simulovali světlo přicházející z různých směrů. Běžný trik je nechat uživatele vybrat „zdroj světla“ z rozbalovacího seznamu a přiřadit mu hodnotu úhlu.

## Kompletní funkční příklad (všechny kroky dohromady)

Níže je stejný program jako dříve, ale s **dalšími komentáři**, které logiku učiní naprosto jasnou. Zkopírujte jej do `Program.cs` a spusťte; výstupní soubor bude obsahovat textové pole s dokonale nastaveným stínem.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Očekávaný výsledek:** Otevřete `output.docx`. První textové pole zobrazí tmavě šedý, 30 % průhledný stín, který je mírně rozostřený (size = 6) a posunutý o 2 pt pod úhlem 45°. Efekt je jemný, ale patrný — přesně to, co většina UI designérů usiluje.

## Časté otázky a úskalí

- **„Funguje to i s obrázky?“**  
  Ano. Jakýkoli `Shape` — ať už textové pole, obrázek nebo auto‑tvar — má `ShadowFormat`. Stačí nahradit logiku získávání tvaru odpovídajícím indexem nebo názvem.

- **„Co když dokument obsahuje více tvarů?“**  
  Procházejte `doc.GetChildNodes(NodeType.Shape, true)` a aplikujte stejná nastavení na každý. Můžete také filtrovat podle `shape.Name` nebo `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}