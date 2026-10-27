---
category: general
date: 2026-06-20
description: Rychle přidejte stín k tvaru a naučte se, jak změnit průhlednost stínu,
  přidat stín k tvaru a aplikovat rozostřený stín pomocí Aspose.Words pro .NET.
draft: false
keywords:
- add shadow to shape
- how to change shadow transparency
- how to add shape shadow
- how to apply blur shadow
language: cs
og_description: Přidejte stín k tvaru v souboru Word, zjistěte, jak změnit průhlednost
  stínu, přidejte stín tvaru a aplikujte rozostřený stín s přehlednými příklady kódu.
og_title: Přidání stínu k tvaru – krok za krokem C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  headline: Add Shadow to Shape in Word Documents – Complete C# Guide
  type: TechArticle
- description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  name: Add Shadow to Shape in Word Documents – Complete C# Guide
  steps:
  - name: What if the shape has no existing shadow object?
    text: Aspose.Words automatically creates a `Shadow` object when you first access
      `targetShape.Shadow`. No extra initialization is required.
  - name: Does this work with other shape types, like circles or pictures?
    text: Absolutely. The shadow API is shape‑agnostic. Just retrieve the appropriate
      `Shape` node, and the same properties apply.
  - name: How to make the shadow invisible again?
    text: Set `targetShape.Shadow.Visible = false;` or simply omit the shadow configuration.
  - name: Compatibility with older .NET versions?
    text: The code uses only features available in Aspose.Words 23.x and .NET Standard
      2.0+, so it runs on .NET Framework 4.6.1 and newer.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
- Shapes
title: Přidání stínu k tvaru v dokumentech Word – kompletní průvodce C#
url: /cs/net/programming-with-shapes/add-shadow-to-shape-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání stínu do tvaru v dokumentech Word – Kompletní průvodce v C#

Už jste se někdy zamýšleli, jak **přidat stín do tvaru** v souboru Word bez manipulace s uživatelským rozhraním? Nejste v tom sami. Mnoho vývojářů potřebuje programově vylepšit estetiku dokumentu a dobrá zpráva je, že Aspose.Words to dělá hračkou.

V tomto tutoriálu projdeme přesné kroky k **přidání stínu do tvaru**, ukážeme vám **jak změnit průhlednost stínu**, pokryjeme **jak přidat stín tvaru** v různých scénářích a dokonce vysvětlíme **jak aplikovat rozostřený stín** pro profesionální efekt hloubky. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného .NET projektu.

## Co se naučíte

- Načíst DOCX, najít tvar a nakonfigurovat jeho vlastnosti stínu.
- Upravit neprůhlednost stínu pomocí `Transparency`.
- Aplikovat rozostření a posun pro vytvoření realistického vrženého stínu.
- Uložit upravený dokument a ověřit výsledek.
- Tipy pro práci s více tvary, různými typy tvarů a okrajovými případy.

> **Předpoklady:** .NET 6 nebo novější, Aspose.Words pro .NET (NuGet balíček `Aspose.Words`) a základní znalost C#. Žádné UI nástroje nejsou potřeba.

![add shadow to shape example](image.png){ alt="příklad přidání stínu do tvaru" }

## Krok 1: Nastavte projekt a načtěte dokument

Než budete moci **přidat stín do tvaru**, potřebujete objekt dokumentu, se kterým budete pracovat. Tento krok je jednoduchý, ale nezbytný – bez načtení souboru není co upravovat.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load an existing DOCX that already contains a shape (e.g., a rectangle)
Document document = new Document(@"C:\Docs\input.docx");
```

*Proč je to důležité:*  
`Document` je vstupní bod pro všechny operace Aspose.Words. Načtením souboru hned na začátku zajistíte, že jakákoli následná manipulace s tvarem proběhne na správném stromu uzlů.

## Krok 2: Získejte cílový tvar

Nyní, když je dokument v paměti, musíme najít tvar, který chceme vylepšit. Pokud máte více tvarů, můžete upravit index nebo použít sofistikovanější selektor.

```csharp
// Grab the first shape in the document – change the index if needed
Shape targetShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
```

> **Tip:** Použijte `document.GetChild(NodeType.Shape, index, true)` pro rekurzivní vyhledávání. Pokud potřebujete konkrétní tvar podle jména, podívejte se na `targetShape.Name`.

## Krok 3: Aktivujte stín a nastavte jeho základní barvu

Stín se nezobrazí, pokud není viditelný a nemá barvu. Dáme mu jemnou tmavě šedou, která dobře funguje na světlých pozadích.

```csharp
// Make sure the shadow is turned on
targetShape.Shadow.Visible = true;

// Choose a neutral color for the shadow
targetShape.Shadow.Color = Color.DarkGray;
```

*Vysvětlení:*  
Nastavení `Visible` na `true` aktivuje efekt, zatímco `Color.DarkGray` poskytuje neutrální tón, který nezasahuje do většiny témat dokumentu.

## Krok 4: Jak změnit průhlednost stínu

Průhlednost je klíčová pro přirozený vzhled stínu. Hodnota `0` je zcela neprůhledná; `1` je úplně neviditelná. Zde je návod, **jak změnit průhlednost stínu** na 30 %:

```csharp
// 30 % transparent (0.3 means 30 % see‑through)
targetShape.Shadow.Transparency = 0.3;
```

*Proč 0,3?*  
30 % průhledný stín napodobuje reálné osvětlení, aniž by přehlušil hrany tvaru. Můžete experimentovat – `0.5` dává měkčí vzhled, zatímco `0.1` stín zesílí.

## Krok 5: Jak aplikovat rozostřený stín pro hloubku

Ostrý, tvrdý stín vypadá plochě. Přidání rozostření mu dodá hloubku. Zde odpovídáme na otázku **jak aplikovat rozostřený stín** v kódu.

```csharp
// Define the blur radius (in points). Larger values = softer shadow.
targetShape.Shadow.BlurRadius = 5;   // 5 pt blur

// Offset determines where the shadow falls relative to the shape.
targetShape.Shadow.OffsetX = 3;      // 3 pt to the right
targetShape.Shadow.OffsetY = 3;      // 3 pt downwards
```

*Co se děje?*  
`BlurRadius` změkčuje hrany, zatímco `OffsetX/Y` umisťují stín, jako by světelný zdroj byl nahoře vlevo. Přizpůsobte tato čísla podle svého designu.

## Krok 6: Jak přidat stín tvaru k více tvarům (volitelné)

Pokud dokument obsahuje několik tvarů, pravděpodobně budete chtít **přidat stín tvaru** ke každému z nich. Jednoduchá smyčka to zařídí:

```csharp
// Iterate over every shape in the document
foreach (Shape shape in document.GetChildNodes(NodeType.Shape, true))
{
    shape.Shadow.Visible = true;
    shape.Shadow.Color = Color.DarkGray;
    shape.Shadow.Transparency = 0.3;
    shape.Shadow.BlurRadius = 5;
    shape.Shadow.OffsetX = 3;
    shape.Shadow.OffsetY = 3;
}
```

*Pro tip:*  
Pokud chcete ovlivnit jen obdélníky, v cyklu zkontrolujte `shape.ShapeType == ShapeType.Rectangle`.

## Krok 7: Uložte upravený dokument

Všechny těžké operace jsou hotové – nyní změny uložte. Můžete přepsat původní soubor nebo zapsat do nového umístění.

```csharp
// Save to a new file to keep the original untouched
document.Save(@"C:\Docs\output.docx");
```

Když otevřete `output.docx` ve Wordu, uvidíte obdélník (nebo jakýkoli jiný tvar, který jste cílovali) s jemným, poloprůhledným, rozostřeným stínem.

## Často kladené otázky a okrajové případy

### Co když tvar nemá existující objekt stínu?
Aspose.Words automaticky vytvoří objekt `Shadow`, když poprvé přistoupíte k `targetShape.Shadow`. Žádná další inicializace není potřeba.

### Funguje to i s jinými typy tvarů, jako jsou kruhy nebo obrázky?
Ano. API pro stín je nezávislé na typu tvaru. Stačí získat odpovídající uzel `Shape` a stejné vlastnosti použijete.

### Jak znovu učinit stín neviditelným?
Nastavte `targetShape.Shadow.Visible = false;` nebo jednoduše vynechejte konfiguraci stínu.

### Kompatibilita se staršími verzemi .NET?
Kód používá jen funkce dostupné v Aspose.Words 23.x a .NET Standard 2.0+, takže běží na .NET Framework 4.6.1 a novějším.

## Kompletní funkční příklad

Zde je kompletní, připravený program, který spojuje všechny kroky dohromady:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load the document that contains the shape
        Document doc = new Document(@"C:\Docs\input.docx");

        // Retrieve the first shape (e.g., a rectangle) from the document
        Shape rect = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // Enable shadow and set its basic properties
        rect.Shadow.Visible = true;
        rect.Shadow.Color = Color.DarkGray;

        // How to change shadow transparency – 30 % transparent
        rect.Shadow.Transparency = 0.3;

        // How to apply blur shadow – add depth with blur and offset
        rect.Shadow.BlurRadius = 5;   // 5 pt blur radius
        rect.Shadow.OffsetX = 3;      // horizontal offset
        rect.Shadow.OffsetY = 3;      // vertical offset

        // Save the modified document
        doc.Save(@"C:\Docs\output.docx");
    }
}
```

**Očekávaný výstup:** Otevřete `output.docx` a uvidíte původní obdélník nyní vykreslený s tmavě šedým, 30 % průhledným, rozostřeným stínem mírně posunutým dolů a doprava.

## Závěr

Probrali jsme vše, co potřebujete k **programatickému přidání stínu do tvaru**, od načtení souboru po ladění průhlednosti a rozostření. Nyní víte **jak změnit průhlednost stínu**, **jak přidat stín tvaru** napříč více elementy a **jak aplikovat rozostřený stín** pro dokonalý vzhled.

Jste připraveni na další krok? Vyzkoušejte experimentovat s:

- Různými barvami stínu (`Color.Black`, `Color.FromArgb(128, 0, 0, 0)`) pro temnější efekty.
- Dynamickými posuny založenými na velikosti tvaru, aby se zachovala proporce.
- Kombinací stínů s gradienty nebo odrazy pro pokročilé stylování.

Neváhejte zanechat komentář, pokud narazíte na potíže, a šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Aspose.Words tutoriál stínu tvaru – Přidání stínu do tvaru Word v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Vytvoření Word dokumentu v Javě – Přidání obdélníkového tvaru s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Přidání skupinového tvaru](/words/english/net/programming-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}