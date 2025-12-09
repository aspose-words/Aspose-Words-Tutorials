---
category: general
date: 2025-12-08
description: Rychle přidejte stín k tvaru pomocí Aspose.Words. Naučte se, jak vytvořit
  dokument Word pomocí Aspose, jak přidat stín k tvaru a jak nastavit průhlednost
  stínu v C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: cs
og_description: Přidejte stín k tvaru v souboru Word pomocí Aspose.Words. Tento krok‑za‑krokem
  průvodce ukazuje, jak vytvořit dokument, přidat tvar a nastavit průhlednost stínu.
og_title: Přidat stín k tvaru – Aspose.Words C# tutoriál
tags:
- Aspose.Words
- C#
- Word Automation
title: Přidat stín k tvaru v dokumentu Word – Kompletní průvodce Aspose.Words
url: /czech/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Přidání stínu k tvaru – Kompletní průvodce Aspose.Words

Už jste někdy potřebovali **přidat stín k tvaru** v souboru Word, ale nebyli jste si jisti, které volání API použít? Nejste v tom sami. Mnoho vývojářů narazí na problém, když poprvé zkusí dát obdélníku nebo jakémukoli kreslenému prvku správný vržený stín, zejména při práci s Aspose.Words pro .NET.

V tomto tutoriálu projdeme vše, co potřebujete vědět: od **vytvoření Word dokumentu pomocí Aspose** po nastavení stínu, úpravu jeho rozostření, vzdálenosti, úhlu a dokonce **aplikaci průhlednosti stínu**. Na konci budete mít připravený spustitelný C# program, který vytvoří soubor `.docx` s pěkně stínovaným obdélníkem – bez ručního ladění ve Wordu.

---

## Co se naučíte

- Jak nastavit projekt Aspose.Words ve Visual Studio.  
- Přesné kroky k **vytvoření Word dokumentu pomocí Aspose** a vložení tvaru.  
- **Jak přidat stín k tvaru** s úplnou kontrolou nad rozostřením, vzdáleností, úhlem a průhledností.  
- Tipy pro řešení běžných problémů (např. chybějící licence, nesprávné jednotky).  
- Kompletní ukázkový kód ke zkopírování a vložení, který můžete spustit ještě dnes.

> **Předpoklady:** .NET 6+ (nebo .NET Framework 4.7.2+), platná licence Aspose.Words (nebo bezplatná zkušební verze) a základní znalost C#.

## Krok 1 – Nastavte svůj projekt a přidejte Aspose.Words

Nejprve. Otevřete Visual Studio, vytvořte novou **Console App (.NET Core)** a přidejte NuGet balíček Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Pokud máte soubor licence (`Aspose.Words.lic`), zkopírujte jej do kořenového adresáře projektu a načtěte jej při spuštění. Tím se vyhnete vodoznaku, který se objevuje v režimu bezplatného hodnocení.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

## Krok 2 – Vytvořte nový prázdný dokument

Nyní skutečně **vytvoříme Word dokument pomocí Aspose**. Tento objekt bude sloužit jako plátno pro náš tvar.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` třída je vstupním bodem pro vše ostatní – odstavce, sekce a samozřejmě kreslené objekty.

## Krok 3 – Vložte obdélníkový tvar

Když je dokument připraven, můžeme přidat tvar. Zde volíme jednoduchý obdélník, ale stejná logika funguje i pro kruhy, čáry nebo vlastní mnohoúhelníky.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Proč tvar?** V Aspose.Words objekt `Shape` může obsahovat text, obrázky nebo sloužit jen jako dekorativní prvek. Přidání stínu k tvaru je mnohem jednodušší než pokus o manipulaci s rámečkem obrázku.

## Krok 4 – Nastavte stín (Přidání stínu k tvaru)

Toto je jádro tutoriálu – **jak přidat stín k tvaru** a jemně doladit jeho vzhled. Vlastnost `ShadowFormat` vám dává plnou kontrolu.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Co dělá každá vlastnost

| Vlastnost | Efekt | Typické hodnoty |
|----------|--------|----------------|
| **Visible** | Zapíná nebo vypíná stín. | `true` / `false` |
| **Blur** | Změkčuje hrany stínu. | `0` (hard) to `10` (very soft) |
| **Distance** | Posouvá stín od tvaru. | `1`–`5` points is common |
| **Angle** | Řídí směr posunu. | `0`–`360` degrees |
| **Transparency** | Způsobí, že stín je částečně průhledný. | `0` (opaque) to `1` (invisible) |

> **Hraniční případ:** Pokud nastavíte `Transparency` na `1`, stín zmizí úplně – užitečné pro programové přepínání.

## Krok 5 – Přidejte tvar do dokumentu

Nyní připojíme tvar k prvnímu odstavci těla dokumentu. Aspose automaticky vytvoří odstavec, pokud neexistuje.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Pokud váš dokument již obsahuje obsah, můžete tvar vložit na libovolný uzel pomocí `InsertAfter` nebo `InsertBefore`.

## Krok 6 – Uložte dokument

Nakonec zapíšete soubor na disk. Můžete zvolit libovolný podporovaný formát (`.docx`, `.pdf`, `.odt` atd.), ale pro tento tutoriál zůstaneme u nativního formátu Word.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Otevřete výsledný `ShadowedShape.docx` v Microsoft Word a uvidíte obdélník s měkkým, 45‑stupňovým stínem, který je 30 % průhledný – přesně tak, jak jsme nakonfigurovali.

## Kompletní funkční příklad

Níže je **kompletní, připravený ke zkopírování a vložení** program, který zahrnuje všechny výše uvedené kroky. Uložte jej jako `Program.cs` a spusťte pomocí `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Očekávaný výstup:** Soubor pojmenovaný `ShadowedShape.docx` obsahující jeden obdélník s jemným, poloprůhledným vrženým stínem natočeným pod úhlem 45°.

## Variace a pokročilé tipy

### Změna barvy stínu

Ve výchozím nastavení stín dědí barvu výplně tvaru, ale můžete nastavit vlastní barvu:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Více tvarů s různými stíny

Pokud potřebujete několik tvarů, stačí opakovat kroky vytvoření a konfigurace. Nezapomeňte každému tvaru přiřadit jedinečný název, pokud je budete později odkazovat.

### Export do PDF se zachovanými stíny

Aspose.Words zachovává efekty stínů při ukládání do PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Běžné úskalí

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Stín není viditelný | `ShadowFormat.Visible` ponechán jako `false` | Nastavte na `true`. |
| Stín vypadá příliš tvrdě | `Blur` nastaven na `0` | Zvyšte `Blur` na 3–6. |
| Stín zmizí v PDF | Použití staré verze Aspose.Words (< 22.9) | Aktualizujte na nejnovější knihovnu. |

## Závěr

Probrali jsme **jak přidat stín k tvaru** pomocí Aspose.Words, od inicializace dokumentu po jemné doladění rozostření, vzdálenosti, úhlu a **aplikaci průhlednosti stínu**. Kompletní příklad ukazuje čistý, připravený na produkci přístup, který můžete přizpůsobit libovolnému tvaru nebo rozložení dokumentu.

Máte otázky ohledně **create word document using aspose** pro složitější scénáře – například tabulky se stíny nebo dynamicky generované tvary? Zanechte komentář níže nebo se podívejte na související tutoriály o zpracování obrázků a formátování odstavců v Aspose.Words.

Šťastné programování a užijte si, že vašim Word dokumentům přidáte ten extra vizuální lesk! 

--- 

![příklad přidání stínu k tvaru](shadowed_shape.png "příklad přidání stínu k tvaru")

{{< layout-end >}}

{{< layout-end >}}