---
category: general
date: 2026-03-30
description: Naučte se, jak nastavit stín na tvaru ve Wordu pomocí C#. Tento průvodce
  také ukazuje, jak přidat stín tvaru, upravit průhlednost tvaru a přidat stín obdélníku.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: cs
og_description: Jak nastavit stín na tvar ve Wordu v C#? Postupujte podle tohoto krok‑za‑krokem
  průvodce a přidejte stín tvaru, upravte průhlednost tvaru a přidejte stín obdélníku.
og_title: Jak nastavit stín na tvar ve Wordu – C# tutoriál
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Jak nastavit stín na tvar ve Wordu – C# tutoriál
url: /cs/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit stín na tvar ve Wordu – C# tutoriál

Už jste se někdy zamysleli **jak nastavit stín** na tvar uvnitř dokumentu Wordu, aniž byste museli manipulovat s uživatelským rozhraním? Nejste v tom sami. V mnoha zprávách nebo marketingových prezentacích jemný drop‑shadow (vržený stín) způsobí, že se obdélník vynikne, a provedení toho programově ušetří hodiny.

V tomto průvodci projdeme kompletním, připraveným příkladem, který nejen ukazuje **jak nastavit stín**, ale také zahrnuje **add shape shadow**, **adjust shape transparency** a dokonce **add rectangle shadow** pro ty klasické zvýrazňovací rámečky. Na konci budete mít soubor Word (`output.docx`), který vypadá profesionálně, a pochopíte, proč je každá vlastnost důležitá.

## Požadavky

- .NET 6+ (nebo .NET Framework 4.7.2) s C# kompilátorem  
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)  
- Základní znalost C# a objektového modelu Wordu  

Žádné další knihovny nejsou potřeba — vše je součástí Aspose.Words.

---

## Jak nastavit stín na tvar ve Wordu v C#

Níže je kompletní zdrojový soubor. Uložte jej jako `Program.cs` a spusťte z vašeho IDE nebo pomocí `dotnet run`. Kód načte existující `.docx`, najde první tvar (ve výchozím nastavení obdélník), zapne jeho stín, upraví několik vizuálních parametrů a výsledek uloží.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Co uvidíte** – Obdélník nyní má černý drop‑shadow, který je 30 % průhledný, posunutý o 5 pt doprava a dolů, s jemným rozostřením. Otevřete `output.docx` ve Wordu a ověřte.

## Úprava průhlednosti tvaru – Proč je to důležité

Průhlednost není jen estetický parametr; ovlivňuje čitelnost. Hodnota 0,0 dělá stín zcela neprůhledný, zatímco 1,0 jej úplně skryje. Ve výše uvedeném úryvku jsme použili `0.3` k dosažení jemného efektu, který funguje na světlých i tmavých pozadích. Klidně experimentujte:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Pamatujte, že **adjust shape transparency** lze také použít na výplň tvaru, pokud potřebujete samotný obdélník poloprůhledný.

## Přidání stínu tvaru k různým objektům

Kód, který jsme použili, cílí na objekt `Shape`, ale stejné vlastnosti `ShadowFormat` existují i u objektů **Image**, **Chart** a dokonce **TextBox**. Zde je rychlý vzor, který můžete zkopírovat a vložit:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Ať už **add shape shadow** přidáváte k logu nebo dekorativní ikoně, přístup zůstává stejný.

## Jak přidat stín k libovolnému tvaru – Okrajové případy

1. **Tvar bez ohraničujícího rámečku** – Některé tvary ve Wordu (např. volně kreslené čáry) nepodporují stíny. Pokus o nastavení `ShadowFormat.Visible` selže tiše. Zkontrolujte `shape.IsShadowSupported`, pokud potřebujete bezpečnost.  
2. **Starší verze Wordu** – Vlastnosti stínu odpovídají funkcím Word 2007+. Pokud musíte podporovat Word 2003, stín bude při otevření souboru ignorován.  
3. **Více stínů** – Aspose.Words v současnosti podporuje jeden stín na tvar. Pokud potřebujete dvojitý efekt, duplikujte tvar, posuňte jej a aplikujte různé nastavení stínu.

## Přidání stínu obdélníku – Praktický případ

Představte si, že generujete čtvrtletní zprávu a každá záhlaví sekce je barevný obdélník. Přidání **add rectangle shadow** dodá stránce vzhled „karty“. Kroky jsou identické jako v základním příkladu; jen se ujistěte, že cílový tvar je skutečně obdélník (`shape.ShapeType == ShapeType.Rectangle`). Pokud potřebujete vytvořit obdélník od nuly, podívejte se na úryvek níže:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Spuštěním celého programu s tímto doplněním získáte nový obdélník, který již obsahuje požadovaný efekt **add rectangle shadow**.

---

![Word shape with shadow](placeholder-image.png){alt="jak nastavit stín na tvar ve Wordu"}

*Obrázek: Obdélník po aplikaci nastavení stínu.*

## Rychlé shrnutí (Bodový tahák)

- **Načtěte** dokument pomocí `new Document(path)`.  
- **Najděte** tvar pomocí `doc.GetChild(NodeType.Shape, index, true)`.  
- **Povolte** stín: `shape.ShadowFormat.Visible = true;`.  
- **Nastavte** barvu pomocí libovolného `System.Drawing.Color`.  
- **Upravte** průhlednost (`0.0–1.0`) pro řízení opacity.  
- **OffsetX / OffsetY** posouvají stín horizontálně/vertikálně (body).  
- **BlurRadius** změkčuje okraj — vyšší hodnoty = rozmazanější stín.  
- **Uložte** soubor a otevřete jej ve Wordu, abyste viděli výsledek.

## Co vyzkoušet dál?

- **Dynamické barvy** — načtěte barvu stínu z motivu nebo vstupu uživatele.  
- **Podmíněné stíny** — aplikujte stín jen když šířka tvaru překročí určitou hranici.  
- **Dávkové zpracování** — projděte všechny tvary v dokumentu a automaticky **add shape shadow**.

Pokud jste šli krok za krokem, nyní víte **jak nastavit stín**, jak **upravit průhlednost tvaru** a jak **add rectangle shadow** pro profesionální vzhled. Klidně experimentujte, rozbíjejte věci a pak je opravujte — programování je nejlepší učitel.

---

*Šťastné kódování! Pokud vám tento tutoriál pomohl, zanechte komentář nebo se podělte o své vlastní triky se stíny. Čím více se od sebe navzájem učíme, tím hezčí naše Word dokumenty budou.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}