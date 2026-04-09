---
category: general
date: 2026-01-08
description: Vytvořte prázdný dokument Word a naučte se, jak přidat stín k obdélníkovému
  tvaru. Vložte soubory s tvary Word a přidejte stín tvaru v C# pomocí Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: cs
og_description: Vytvořte prázdný dokument Word a zjistěte, jak pomocí C# přidat stín
  k obdélníkovému tvaru. Kompletní kód, vysvětlení a tipy.
og_title: Vytvořte prázdný dokument Word – Přidejte stínovaný obdélníkový tvar
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořte prázdný dokument Word se stínovaným obdélníkovým tvarem – krok za
  krokem průvodce
url: /cs/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření prázdného dokumentu Word s obdélníkovým tvarem se stínem – kompletní tutoriál

Už jste někdy potřebovali **vytvořit prázdné soubory Word** programově a poté je ozdobit pěkným obdélníkem se stínem? Nejste v tom sami. Mnoho vývojářů narazí na problém, když zjistí, že vkládání tvarů a aplikace efektů není tak jednoduché jako psaní textu.

V tomto průvodci projdeme celý proces – od vytvoření prázdného souboru `.docx` po **přidání stínu** k objektu **rectangle shape word**, a nakonec **vložíme obsah shape word** s vylepšeným efektem **add shape shadow**. Na konci budete mít připravený úryvek kódu, který funguje s nejnovější verzí Aspose.Words pro .NET.

## Co budete potřebovat

- **Aspose.Words for .NET** (v24.10 nebo novější) – knihovna, která pohání vše níže.  
- Vývojové prostředí .NET (Visual Studio, Rider nebo `dotnet` CLI).  
- Základní znalost C# – pokud umíte napsat “Hello World”, jste připraveni.  

Nejsou vyžadovány žádné další balíčky NuGet; vše je obsaženo v `Aspose.Words` a `System.Drawing`.

## Krok 1: Vytvoření prázdného dokumentu Word

Prvním krokem je vytvořit prázdný objekt `Document`. Představte si ho jako čisté plátno – podobně jako ručně otevřete nový soubor Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Proč je to důležité:*  
Instance `Document` představuje celý soubor Word. Začít s prázdným dokumentem vám dává plnou kontrolu nad všemi prvky, které později přidáte, od odstavců po tvary.

## Krok 2: Definování obdélníkového tvaru (Rectangle Shape Word)

Nyní potřebujeme tvar, se kterým budeme pracovat. Obdélník je nejjednodušší geometrie a dobře se hodí pro bannery, zástupné symboly nebo jednoduché UI mock‑upy.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Proč je to důležité:*  
Nastavení `Width` a `Height` vám umožňuje kontrolovat vizuální rozměry tvaru. `ShapeType.Rectangle` říká Aspose, aby vykreslil klasický obdélník – ideální pro pozdější ukázku **add shape shadow**.

## Krok 3: Aplikace stínu na tvar (Jak přidat stín)

Stíny dodávají hloubku a způsobují, že plochý obdélník působí jako fyzický objekt. Aspose.Words poskytuje vlastnost `Shadow`, kde můžete upravit barvu, vzdálenost, rozostření a průhlednost.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Proč je to důležité:*  
Každá vlastnost ovlivňuje vizuální náznak:

- **Enabled** – bez tohoto jsou ostatní nastavení ignorována.  
- **Color** – vyberte odstín, který odpovídá tématu vašeho dokumentu.  
- **Distance** – větší hodnoty posunou stín dál od objektu.  
- **BlurRadius** – vyšší čísla udělají stín měkčím.  
- **Transparency** – jemně doladí neprůhlednost pro subtilní efekt.

Neváhejte experimentovat; pro dramatický efekt zvyšte `Distance` na `10` a nastavte `Transparency` na `0.5`.

## Krok 4: Vložení tvaru do dokumentu (Insert Shape Word)

Jakmile je obdélník připraven, potřebujeme místo, kam ho vložit. Nejjednodušší místo je první odstavec těla dokumentu.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Proč je to důležité:*  
`FirstSection.Body.FirstParagraph` je vždy přítomen v novém `Document`. Připojením tvaru zde zajistíte, že se tvar objeví na začátku souboru – užitečné pro záhlaví nebo titulní bannery.

Pokud potřebujete tvar vložit jinam, můžete najít konkrétní `Paragraph` nebo `Run` a použít `InsertAfter` nebo `InsertBefore`.

## Krok 5: Uložení souboru Word

Posledním krokem je uložení dokumentu v paměti na disk. Vyberte složku, do které máte právo zápisu, a dejte souboru smysluplný název.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Proč je to důležité:*  
Volání `Save` zapíše plně kompatibilní soubor `.docx`. Otevřete jej v Microsoft Word, LibreOffice nebo jakémkoli prohlížeči a uvidíte obdélník s jemným šedým stínem – přesně tak, jak jsme nastavili.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny `using` direktivy, vytvoření tvaru, konfiguraci stínu, vložení a uložení.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výstup:**  
Otevřete `ShadowedRectangle.docx` a uvidíte světle šedý obdélník umístěný uprostřed horní části stránky s jemným stínem posunutým o 5 pt. Žádný další text, jen tvar – přesně to, co kód vytvoří.

## Časté otázky a okrajové případy

### Co když potřebuji jiný tvar?

Nahraďte `ShapeType.Rectangle` libovolnou jinou hodnotou výčtu `ShapeType` (`Ellipse`, `Triangle`, `Star` atd.). Vlastnosti stínu fungují stejným způsobem.

### Můžu přidat více stínů?

Aspose.Words podporuje pouze jeden stín na tvar. Pokud potřebujete vrstvené efekty, vytvořte dva překrývající se tvary s různými nastaveními stínu.

### Jak to funguje na .NET Core?

Stejné API funguje na .NET 6/7/8. Stačí zajistit, že odkazujete na balíček **Aspose.Words.NETCore** (nebo standardní balíček, který je nyní multiplatformní).

### Je `System.Drawing` stále podporován na Linuxu?

`System.Drawing.Common` je od .NET 6 pouze pro Windows. Pro multiplatformní projekty použijte `Aspose.Drawing` (samostatný NuGet) nebo se držte barev definovaných přímo v `Aspose.Words`.

### Co DPI škálování?

Rozměry tvaru jsou v bodech (1 pt = 1/72 palce). Pokud potřebujete velikost přesně v pixelech pro konkrétní DPI, vypočítejte body jako `pixels * 72 / dpi`.

## Profesionální tipy a úskalí

- **Pro tip:** Nastavte `rectangleShape.WrapType = WrapType.Inline;`, pokud chcete, aby se tvar plynule řadil s textem místo toho, aby plaval nad ním.  
- **Pozor na:** Zapomenutí povolit stín (`Enabled = true`). Ostatní nastavení budou tiše ignorována.  
- **Poznámka k výkonu:** Přidávání mnoha tvarů v úzké smyčce může být pomalé. Sesbírejte je do jedné `Section` a na konci zavolejte `document.UpdatePageLayout()`.  
- **Kontrola verze:** API pro stín bylo zavedeno v Aspose.Words 20.2. Pokud používáte starší verzi, aktualizujte ji, aby nebyly chybějící vlastnosti.

## Závěr

Vytvořili jsme **prázdný dokument Word**, vytvořili **rectangle shape word**, naučili se **jak přidat stín** a nakonec **vložit obsah shape word** s vylepšeným efektem **add shape shadow** – vše pomocí Aspose.Words pro .NET.

Úryvek je plně spustitelný, funguje na Windows i multiplatformním .NET a lze jej rozšířit na další tvary, barvy nebo dokonce animované GIFy. Dále můžete zkoumat přidání textu uvnitř obdélníku, aplikaci gradientových výplní nebo generování celého reportu s více stylizovanými tvary.

Máte další nápady? Zkuste vyměnit šedý stín za modrý, zvýšit rozostření pro snový vzhled nebo zkombinovat několik tvarů do vlastního loga. Limit neexistuje a nyní máte stavební bloky, jak to provést.

Šťastné programování a ať vaše dokumenty vždy vypadají ostře (s právě takovým množstvím stínu)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}