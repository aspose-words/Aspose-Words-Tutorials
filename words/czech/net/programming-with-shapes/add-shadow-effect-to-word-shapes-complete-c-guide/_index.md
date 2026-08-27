---
category: general
date: 2026-02-10
description: Přidejte stínový efekt do tvaru ve Wordu pomocí C#. Naučte se, jak změnit
  barvu stínu, nastavit průhlednost a aplikovat stín na tvar během několika kroků.
draft: false
keywords:
- add shadow effect
- change shadow color
- how to set transparency
- add shape shadow
- apply shadow color
language: cs
og_description: Přidejte stínový efekt k tvaru ve Wordu pomocí C#. Naučte se, jak
  změnit barvu stínu, nastavit průhlednost a aplikovat stín na tvar během několika
  kroků.
og_title: Přidejte stínový efekt k tvarům ve Wordu – kompletní průvodce C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Přidat stínový efekt k tvarům ve Wordu – Kompletní průvodce C#
url: /cs/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/
---

}}

We must keep them unchanged.

Now produce final output with translation.

Let's craft Czech translation.

Be careful with technical terms: keep API, SDK, class names etc. Keep code placeholders unchanged.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání stínového efektu do tvarů Word – Kompletní průvodce v C#

Už jste někdy potřebovali **add shadow effect** do tvaru ve Wordu, ale nevedeli jste, kde začít? Nejste jediní — vývojáři se často ptají: „Jak udělat, aby tvar vypadal o něco víc trojrozměrně?“ Dobrou zprávou je, že s několika řádky C# můžete změnit barvu stínu, nastavit průhlednost a doladit vzhled libovolného tvaru. V tomto tutoriálu projdeme kompletním, spustitelným příkladem, který přesně to dělá, plus několik tipů, které byste si přáli vědět dříve.

Probereme:

* Načtení souboru DOCX, který již obsahuje tvar.  
* Vyhledání tvaru (i když je vnořený ve skupině).  
* Aplikaci stínu — vzdálenost, rozostření, barvu a průhlednost.  
* Ověření výsledku uložením dokumentu.  

Žádná externí dokumentace není potřeba; vše, co potřebujete, je zde. Jedinou podmínkou je reference na **Aspose.Words for .NET** (nebo jakoukoli kompatibilní knihovnu, která vystavuje `Shape.ShadowFormat`). Pokud používáte NuGet, stačí spustit `Install-Package Aspose.Words`. Připravení? Ponořme se do toho.

---

## Prerequisites

| Požadavek | Proč je důležitý |
|-------------|----------------|
| .NET 6.0 nebo novější | Moderní API, lepší výkon |
| Aspose.Words for .NET (nebo ekvivalent) | Poskytuje třídy `Document`, `Shape` a `ShadowFormat` |
| Soubor DOCX (`input.docx`) obsahující alespoň jeden tvar | Tutoriál manipuluje s existujícím tvarem; můžete jej vytvořit v Wordu ručně, pokud je potřeba |

> **Pro tip:** Pokud nemáte tvar po ruce, otevřete Word, vložte jednoduchý obdélník, uložte soubor jako `input.docx` a umístěte jej do složky `Resources` ve vašem projektu.

---

## Step 1 – Load the Word Document and Locate the Shape {#add-shadow-effect-step1}

Nejprve potřebujeme objekt `Document`, který ukazuje na náš zdrojový soubor. Pak načteme první tvar pomocí rekurzivního vyhledávání, aby to fungovalo i v případě, že je tvar uvnitř skupiny.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Step 1: Load the Word document that contains a shape
        Document doc = new Document("Resources/input.docx");

        // Step 2: Retrieve the first shape in the document (searches recursively)
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Continue with shadow settings...
```

**Proč to děláme:**  
* `Document` je vstupní bod do libovolného souboru Word.  
* `GetChild(NodeType.Shape, 0, true)` prochází celý strom uzlů a zajišťuje, že nevynecháme vnořené tvary.  
* Kontrola na `null` zabraňuje `NullReferenceException`, pokud je soubor bez tvarů — okrajový případ, který mnoho začátečníků přehlíží.

---

## Step 2 – Set the Shadow Distance and Blur {#add-shadow-effect-step2}

Stín není jen barva; jeho posunutí a měkkost jsou stejně důležité. Posuneme stín o několik bodů a přidáme jemné rozostření.

```csharp
        // Step 3: Set how far the shadow is offset from the shape
        targetShape.ShadowFormat.Distance = 4.0;   // 4 points offset

        // Step 4: Define the softness of the shadow edges
        targetShape.ShadowFormat.BlurRadius = 2.0; // 2 points blur
```

**Vysvětlení:**  
* **Distance** řídí posunutí v osách X/Y. Hodnota `4.0` posune stín dolů a doprava, napodobujíc světelný zdroj z horního levého rohu.  
* **BlurRadius** určuje, jak rozmazaný je okraj. Nízké číslo udržuje stín ostrý; vyšší číslo vytvoří vzhled měkkého záře.

Pokud potřebujete jiný směr osvětlení, můžete také upravit `ShadowFormat.Angle` (výchozí je 45°).  

---

## Step 3 – Change Shadow Color and Set Transparency {#add-shadow-effect-step3}

Teď přichází zábavná část — změna barvy a částečná průhlednost stínu. Zde vstupují do hry sekundární klíčová slova **change shadow color** a **how to set transparency**.

```csharp
        // Step 5: Choose a colour for the shadow
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color here

        // Step 6: Make the shadow partially transparent (30 % transparent)
        targetShape.ShadowFormat.Transparency = 0.3; // Value between 0 (opaque) and 1 (fully transparent)
```

**Proč je to důležité:**  
* `Color.DarkGray` je bezpečná výchozí hodnota, která funguje na světlých i tmavých pozadích. Klidně ji nahraďte `Color.FromArgb(255, 0, 0, 0)` pro čistou černou nebo libovolnou vlastní ARGB hodnotu.  
* Nastavení `Transparency` na `0.3` vám poskytne 30 % průhlednost — dost na naznačení hloubky, aniž by zakrývalo tvar pod ním.  

**Okrajový případ:** Některé starší verze Wordu ignorují průhlednost u určitých typů tvarů (např. WordArt). Pokud si všimnete, že stín zůstává plně neprůhledný, zkuste nejprve převést tvar na obrázek.

---

## Step 4 – Save and Verify the Result {#add-shadow-effect-step4}

Po doladění stínu zapíšeme dokument zpět na disk. Otevření souboru ve Wordu by mělo odhalit jemný, barevný, poloprůhledný stín kolem tvaru.

```csharp
        // Step 7: Save the modified document
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

**Kontrolní seznam ověření:**

1. Otevřete `output_with_shadow.docx` v Microsoft Word.  
2. Klikněte na tvar → Formát → Efekty tvaru → Stín.  
3. Měli byste vidět tmavě šedý stín, posunutý o ~4 pt, rozostřený a 30 % průhledný.

Pokud něco vypadá špatně, zkontrolujte vlastnosti `ShadowFormat` — zejména `Distance` a `Transparency`.  

---

## Common Variations and What‑If Scenarios {#add-shadow-effect-variations}

### Adding a Shadow to Multiple Shapes

Pokud potřebujete **add shape shadow** ke každému tvaru v dokumentu, nahraďte načítání jednoho tvaru smyčkou:

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Distance = 5.0;
            shp.ShadowFormat.BlurRadius = 3.0;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.4;
        }
```

### Using a Custom Colour with Alpha

Někdy chcete, aby samotná barva stínu byla poloprůhledná. Kombinujte `Color.FromArgb` s `Transparency` pro vrstvený efekt:

```csharp
        // Semi‑transparent blue shadow
        targetShape.ShadowFormat.Color = Color.FromArgb(180, 0, 0, 255); // 180/255 ≈ 70% opacity
        targetShape.ShadowFormat.Transparency = 0.2; // Additional 20% transparency
```

### Handling Shapes Inside a Group

Seskupené tvary jsou uloženy jako uzel `GroupShape`. Rekurzivní vyhledávání, které jsme použili (`true` flag), už do skupin proniká, ale pokud potřebujete zacházet se skupinou jako s jedinou entitou, přetypujte na `GroupShape` a iterujte jeho `ChildNodes`.

```csharp
        GroupShape group = targetShape.ParentNode as GroupShape;
        if (group != null)
        {
            foreach (Shape inner in group.GetChildNodes(NodeType.Shape, true))
            {
                // Apply same shadow settings to each inner shape
                inner.ShadowFormat = targetShape.ShadowFormat.Clone();
            }
        }
```

---

## Pro Tips & Pitfalls {#add-shadow-effect-tips}

* **Pro tip:** Když experimentujete, nastavte `ShadowFormat.Visible = true` explicitně. Některá API skryjí stín, dokud se nezmění nějaká vlastnost.  
* **Dejte si pozor na:** Nastavení Wordu „No Outline“ může způsobit, že stín vypadá odtrženě. Ujistěte se, že styl čáry tvaru je viditelný, pokud chcete, aby stín doplňoval tvar.  
* **Poznámka o výkonu:** Aktualizace tisíců tvarů ve velkém dokumentu může být pomalá. Proveďte změny dávkově a na konci zavolejte `doc.UpdatePageLayout()`.  
* **Kompatibilita:** Aspose.Words 23.10+ plně podporuje vlastnosti stínu pro DOCX, ale starší verze mohou ignorovat `BlurRadius`. Vždy testujte s verzí knihovny, kterou distribuujete.

---

## Full Working Example {#add-shadow-effect-complete}

Níže je kompletní, připravený k zkopírování a vložení program. Obsahuje všechny `using` direktivy, ošetření chyb a komentáře.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the document that already contains a shape.
        Document doc = new Document("Resources/input.docx");

        // Retrieve the first shape (recursively searches groups).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Apply shadow distance and blur.
        targetShape.ShadowFormat.Distance = 4.0;      // Offset from shape
        targetShape.ShadowFormat.BlurRadius = 2.0;   // Soft edges

        // Change shadow color and set transparency.
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;     // How to set transparency (30%)

        // Save the modified document.
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

Spuštěním tohoto programu vznikne `output_with_shadow.docx` s **add shadow effect**, o který jste požádali. Otevřete soubor a uvidíte pěkně rozostřený, tmavě šedý stín, který je 30 % průhledný — přesně tak, jak byste očekávali u profesionální prezentace.

---

## Conclusion

Právě jsme ukázali, jak **add shadow effect** aplikovat na tvar ve Wordu pomocí C#. Načtením dokumentu, vyhledáním tvaru, úpravou vlastností `ShadowFormat` a uložením souboru získáte plnou kontrolu nad **change shadow color**, **how to set transparency** a **add shape shadow** během několika minut.  

Dále můžete **apply shadow color** podmíněně — například tmavší stíny pro větší tvary nebo různé barvy podle vstupu uživatele. Nebo prozkoumat další vizuální vylepšení, jako je záře, odraz nebo 3‑D řezby. Stejný vzor `ShadowFormat` funguje i pro tyto funkce, takže jste dobře připraveni tuto ukázku dále rozšířit.

Máte otázky nebo narazíte na podivný okrajový případ? Zanechte komentář níže a pojďme to společně vyřešit. Šťastné kódování a ať vaše dokumenty vždy získají ten extra nádech hloubky!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}