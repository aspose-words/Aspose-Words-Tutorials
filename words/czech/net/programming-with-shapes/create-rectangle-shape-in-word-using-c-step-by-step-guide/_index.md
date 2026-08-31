---
category: general
date: 2026-01-03
description: Vytvořte obdélníkový tvar ve Wordu pomocí C# a přidejte k tvaru stín.
  Naučte se, jak vložit tvar do Wordu, přidat k tvaru stín a programově generovat
  dokumenty Word.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: cs
og_description: Vytvořte obdélníkový tvar ve Wordu pomocí C# a přidejte tvaru stín.
  Postupujte podle tohoto návodu k vložení tvaru do Wordu, nastavení stínů a programovému
  generování dokumentů.
og_title: Vytvořte obdélníkový tvar ve Wordu pomocí C# – kompletní návod
tags:
- C#
- Word Automation
- Aspose.Words
title: Vytvořte obdélníkový tvar ve Wordu pomocí C# – krok za krokem průvodce
url: /cs/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru ve Wordu pomocí C# – Kompletní tutoriál

Už jste někdy potřebovali **create rectangle shape** v dokumentu Word, ale nevedeli jste, kde začít? Nejste sami – mnoho vývojářů narazí na stejný problém, když chtějí **add shadow to shape** pro dokonalý vzhled. V tomto tutoriálu vás provedeme přesné kroky k **insert shape in Word**, aplikaci jemného stínu a nakonec **c# generate word document** souborům, které můžete distribuovat uživatelům.

Probereme vše od nastavení projektu až po ladění vlastností stínu a zakončíme připraveným ukázkovým kódem. Žádné zbytečnosti, jen praktické informace, které vám práci usnadní.

## Co se naučíte

- Jak **create rectangle shape** pomocí Aspose.Words (nebo Open XML) v C#  
- Přesné vlastnosti, které potřebujete k **add shadow to shape** pro hloubku  
- Kde umístit tvar pomocí `DocumentBuilder`  
- Jak uložit soubor, aby se správně otevřel v Microsoft Word  
- Tipy, úskalí a varianty pro reálné scénáře  

### Požadavky

- .NET 6.0 nebo novější (kód funguje na .NET Core i .NET Framework)  
- NuGet balíček, který dokáže manipulovat se soubory Word – použijeme **Aspose.Words for .NET**, protože jeho API je stručné. Pokud dáváte přednost Open XML SDK, koncepty jsou stejné, jen se liší třídy.  
- Visual Studio, VS Code nebo jakékoli C# IDE, které máte rádi  

> **Tip:** Pokud máte omezený rozpočet, Aspose nabízí bezplatnou zkušební verzi, která je ideální pro učení. Stačí při testování nahradit řádek s licencí komentářem.

## Krok 1: Instalace knihovny pro zpracování Wordu

Nejprve přidejte knihovnu do svého projektu. Otevřete terminál ve složce řešení a spusťte:

```bash
dotnet add package Aspose.Words
```

Pokud používáte Open XML SDK, příkaz bude `dotnet add package DocumentFormat.OpenXml`. Zbytek tohoto návodu předpokládá Aspose.Words, ale výměna volání API je jednoduchá.

## Krok 2: Vytvoření nového prázdného dokumentu

Jakmile je knihovna připravena, můžeme **create rectangle shape** zahájením s čistým objektem `Document`. Považujte to za čerstvé plátno.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` nám poskytuje vysoce‑úrovňový způsob vkládání obsahu, aniž bychom se museli ponořit do nízko‑úrovňových stromů uzlů.

## Krok 3: Vložení obdélníkového tvaru

S builderem v ruce můžeme **insert shape in Word**. Metoda `InsertShape` přijímá typ tvaru a jeho rozměry (šířka, výška) v bodech.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

V tomto okamžiku se obdélník objeví v dokumentu, ale vypadá poněkud plochý. Zde přichází na řadu další krok.

## Krok 4: Přidání stínu k tvaru

Stíny dodávají tvaru pocit hloubky. Objekt `Shadow` nám umožňuje jemně nastavit rozostření, vzdálenost, úhel, barvu a průhlednost. Níže je kompletní konfigurace, která funguje dobře pro většinu reportů.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Proč tyto hodnoty?**  
- **BlurRadius** `5.0` udržuje okraj hladký, aniž by vypadal rozmazaně.  
- **Distance** `4.0` posouvá stín právě natolik, aby byl patrný.  
- **Angle** `45` napodobuje přirozené osvětlení z horního levého rohu, běžná konvence UI.  
- **Transparency** `0.3` zabraňuje tomu, aby stín přehlušil výplň tvaru.

Pokud potřebujete dramatický efekt, zvýšte `BlurRadius` a snižte `Transparency`. Pro jemné, téměř neviditelné zvýšení, tyto hodnoty obrátíte.

## Krok 5: Uložení dokumentu

Nakonec zapíšete soubor na disk. Metoda `Save` detekuje formát podle přípony souboru, takže `.docx` vám poskytne moderní formát Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Otevřete `ShadowRectangle.docx` v Microsoft Word a uvidíte ostrý obdélník s jemným stínem – přesně to, co jste chtěli, když jste se ptali „**how to add shape**“ s profesionálním vzhledem.

![Vytvoření obdélníkového tvaru se stínem ve Wordu](placeholder-image.png "Vytvoření obdélníkového tvaru se stínem ve Wordu")

*Text alternativy obrázku: create rectangle shape with shadow in Word*

## Kompletní funkční příklad

Spojením všech částí získáte kompletní, připravený ke spuštění program. Zkopírujte a vložte do konzolové aplikace a stiskněte **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Očekávaný výsledek

- Vygenerovaný `ShadowRectangle.docx` obsahuje **jeden obdélníkový tvar** uprostřed místa, kde byl kurzor umístěn.  
- Obdélník zobrazuje **jemný, 30 % průhledný černý stín** posunutý pod úhlem 45°.  
- Žádný další obsah není přidán, takže soubor zůstává lehký a snadno vložitelný do větších reportů.

## Časté otázky a okrajové případy

### Co když potřebuji jiný tvar?

Nahraďte `ShapeType.Rectangle` libovolnou jinou hodnotou výčtu `ShapeType` (např. `Ellipse`, `Triangle`). API pro stín funguje stejným způsobem, takže můžete znovu použít konfiguraci.

### Jak změním barvu výplně?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Můžu přidat tvar do konkrétního odstavce?

Ano. Přesuňte `DocumentBuilder` na cílový odstavec pomocí `builder.MoveToParagraph(index)` před voláním `InsertShape`. Tím zajistíte, že se tvar objeví přesně tam, kde ho potřebujete.

### Co starší formáty Wordu (.doc)?

Stačí změnit příponu:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Funkce stínu je podporována ve Word 2003 a novějších, takže efekt stále uvidíte.

### Použití Open XML SDK místo Aspose?

Kroky zůstávají: vytvořte `WordprocessingDocument`, přidejte element `Drawing`, nastavte vlastnosti `<a:shadow>`. XML je podrobnější, ale stejné koncepty (velikost, rozostření, vzdálenost, úhel) platí.

## Tipy, jak se vyhnout úskalím

- **Nezapomeňte na licenci**, pokud používáte placenou verzi Aspose; jinak se zobrazí vodoznak.  
- **Jednotky jsou body**, ne pixely. Jeden typický pixel na obrazovce ≈ 0.75 pt, takže rozměry upravte odpovídajícím způsobem.  
- **Vlastnosti stínu jsou ignorovány**, pokud je `WrapType` tvaru nastaven na `Inline`. Použijte `WrapType = WrapType.Square` pro plovoucí tvary, které respektují vykreslování stínu.  
- **Ukládání na síťové úložiště** může vyžadovat správná oprávnění; vždy nejprve otestujte cestu.

## Závěr

Nyní víte, jak **create rectangle shape** v dokumentu Word pomocí C#, **add shadow to shape** a **c# generate word document** soubory, které vypadají profesionálně hned po vytvoření. Základní kroky – instalace knihovny, vytvoření instance `Document`, vložení tvaru, nastavení stínu a uložení – jsou snadno zapamatovatelné a přizpůsobitelné i pro jiné tvary, barvy nebo dokonce dynamická data.

Co dál? Zkuste vrstvit více tvarů, vkládat obrázky nebo generovat kompletní report s tabulkami a grafy. Můžete také prozkoumat podmíněné formátování – měnit intenzitu stínu podle hodnot dat – aby vaše dokumenty nebyly jen funkční, ale i vizuálně poutavé.

Klidně experimentujte a pokud narazíte na podivnosti, zanechte komentář níže. Šťastné programování a ať vaše Word dokumenty vždy mají ten dokonalý vržený stín!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}