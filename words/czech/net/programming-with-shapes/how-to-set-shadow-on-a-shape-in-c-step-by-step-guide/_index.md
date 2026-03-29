---
category: general
date: 2026-03-28
description: Jak nastavit stín na tvaru v C# s Aspose.Words – přidat stín k tvaru,
  aplikovat stín a přizpůsobit vzhled.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: cs
og_description: Jak rychle nastavit stín na tvar v C#. Naučte se přidat stín k tvaru,
  aplikovat stín a upravit rozostření, vzdálenost a úhel.
og_title: Jak nastavit stín na tvar v C# – kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: Jak nastavit stín na tvar v C# – krok za krokem
url: /cs/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit stín na tvar v C# – Kompletní programovací průvodce

Už jste se někdy zamysleli **jak nastavit stín** na tvar při programovém vytváření dokumentů Word? Nejste v tom sami. V mnoha zprávách, prezentacích nebo letácích může jemný stín zvýraznit grafiku, aniž by působila nevkusně. Dobrá zpráva? S Aspose.Words pro .NET můžete přidat stín k tvaru během několika řádků kódu.

V tomto tutoriálu projdeme celý proces: načtení DOCX, získání prvního tvaru a následné **apply shadow to shape** — včetně barvy, rozostření, vzdálenosti a úhlu. Na konci budete mít připravený úryvek kódu, který můžete vložit do libovolného C# projektu. Žádné další knihovny, žádná skrytá magie.

## Co budete potřebovat

- **Aspose.Words for .NET** (verze 23.9 nebo novější) – knihovna, která usnadňuje manipulaci s Wordem.  
- Vývojové prostředí .NET (Visual Studio 2022, Rider nebo CLI).  
- Vzorek DOCX, který již obsahuje alespoň jeden tvar (obdélník, obrázek nebo SmartArt postačí).  

Pokud vám něco chybí, stáhněte NuGet balíček pomocí `Install-Package Aspose.Words` a vytvořte jednoduchý Word soubor s ručně vloženým tvarem – jen pro demonstraci.

## Krok 1: Načtení dokumentu (připravit přidání stínu)

Prvním krokem je otevřít zdrojový soubor. Zde začne operace **add shadow to shape**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **Proč je to důležité:** Načtení dokumentu vám poskytne objekt `Document`, který vlastní všechny uzly, včetně tvarů. Bez něj není co upravovat.

## Krok 2: Získání cílového tvaru (vyberte ten správný)

Dále najdeme tvar, který chceme stylovat. V tomto příkladu získáme první tvar v prvním odstavci, ale můžete upravit dotaz pro libovolnou kolekci uzlů.

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **Tip:** `GetChildNodes(NodeType.Shape, true)` prochází podstrom rekurzivně, což zajišťuje, že nevynecháte vnořené tvary jako WordArt.

## Krok 3: Přístup k objektu ShadowFormat (kde se děje magie)

Každý `Shape` má vlastnost `ShadowFormat`. Tento objekt řídí viditelnost, barvu, rozostření, vzdálenost a úhel — všechny ovládací prvky, které potřebujete k **apply shadow to shape**.

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Proč používáme `ShadowFormat`:** Abstrahuje podkladovou XML reprezentaci, takže můžete ladit stíny, aniž byste museli pracovat s čistým OpenXML.

## Krok 4: Zviditelnění stínu a výběr barvy (Add Shadow to Shape)

Stín se neobjeví, dokud nenastavíte `Visible` na `true`. Poté můžete vybrat libovolnou `System.Drawing.Color`. Zde používáme středně šedou, ale klidně experimentujte.

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **Častá chyba:** Zapomenutí povolit `Visible` vede k tichým selháním — váš tvar zůstane beze změny, i když jste nastavili ostatní vlastnosti.

## Krok 5: Nastavení vzhledu – rozostření, vzdálenost a úhel (jemné doladění vzhledu)

Nyní upravujeme vizuální dopad. `BlurRadius` změkčuje hrany, `Distance` posouvá stín od tvaru a `Angle` určuje směr světelného zdroje.

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **Hraniční případ:** Pokud nastavíte zápornou vzdálenost, stín se objeví *uvnitř* tvaru, což může být užitečné pro efekty reliéfu.

## Krok 6: Uložení aktualizovaného dokumentu (zobrazit výsledek)

Nakonec zapište změny zpět na disk. Můžete přepsat původní soubor nebo vytvořit nový.

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

Spuštěním programu vznikne `output-with-shadow.docx`. Otevřete jej v Microsoft Word a všimnete si, že vybraný tvar nyní má jemný šedý stín nasměrovaný pod úhlem 45°, rozostřený na 5 pt a posunutý o 3 pt.

![Diagram ukazující aplikovaný stín na tvar](https://example.com/images/shadow-diagram.png "Diagram ukazující aplikovaný stín na tvar")

*Alt text: Diagram ukazující aplikovaný stín na tvar* – tento obrázek ilustruje efekt před/po.

## Jak přidat stín – běžné varianty a hraniční případy

I když jsou základní kroky jednoduché, reálné scénáře často vyžadují úpravy. Níže jsou uvedeny některé situace „co‑když“, se kterými se můžete setkat.

### 1. Více tvarů, různé stíny

Pokud váš dokument obsahuje několik grafických prvků, projděte kolekci tvarů a přiřaďte každému tvaru jedinečné nastavení stínu.

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. Průhledné stíny

Aspose.Words vám umožňuje nastavit alfa kanál pomocí `Color.FromArgb(alpha, r, g, b)`. Použijte nízkou hodnotu alfy (např. 50) pro jemný, poloprůhledný efekt.

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. Odstranění stínu

Někdy potřebujete po aplikaci stín vypnout. Jednoduše nastavte `Visible` na `false`.

```csharp
        shadow.Visible = false;
```

### 4. Problémy s kompatibilitou

Funkce stínů použité zde jsou podporovány ve Wordu 2007 + (formát DOCX). Pokud cílíte na starší binární formát `.doc`, může být stín ignorován, protože formát postrádá potřebné XML elementy. V takových případech zvažte uložení jako DOCX nebo použití náhradního vizuálního prvku.

## Shrnutí: Co jsme dosáhli

- **Načten** DOCX pomocí Aspose.Words.  
- **Získal** první tvar z dokumentu.  
- **Přistoupil** k jeho objektu `ShadowFormat`.  
- **Povolil** stín, nastavil barvu, poloměr rozostření, vzdálenost a úhel.  
- **Uložil** nový soubor, který viditelně ukazuje efekt.  

Všechny tyto kroky dohromady odpovídají na **how to set shadow** na tvar, a zároveň vám ukazují, jak **add shadow to shape**, **apply shadow to shape**, a dokonce **how to add shadow** v složitějších scénářích.

## Další kroky a související témata

Nyní, když ovládáte stylování stínů, můžete chtít prozkoumat:

- **Gradientové výplně** pro tvary (`Shape.FillFormat.GradientFill`).  
- **Textové efekty** jako záře nebo odraz (`TextEffect`).  
- **Programové vkládání nových tvarů** (`doc.FirstSection.Body.AppendChild(new Shape(...))`).  
- **Export do PDF** při zachování stínů (`doc.Save("output.pdf")`).  

Každé z těchto témat staví na stejných principech objektového modelu, které jsme zde použili, takže se budete cítit jako doma.

---

*Šťastné programování! Pokud narazíte na problém, zanechte komentář níže nebo si prohlédněte dokumentaci Aspose.Words API pro podrobnější informace.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}