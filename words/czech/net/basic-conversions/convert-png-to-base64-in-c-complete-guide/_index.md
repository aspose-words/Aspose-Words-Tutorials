---
category: general
date: 2026-02-13
description: Rychle převést PNG na Base64 v C# – naučte se, jak zakódovat obrázek
  do base64, vložit obrázek do HTML pomocí base64 a zkopírovat stream do paměti pro
  webové projekty.
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: cs
og_description: Rychle převést PNG na Base64 v C#. Tento tutoriál ukazuje, jak zakódovat
  obrázek do base64, vložit obrázek do HTML jako base64 a zkopírovat stream do paměti.
og_title: Převod PNG na Base64 v C# – Kompletní průvodce
tags:
- C#
- image-processing
- data-uri
title: Převod PNG na Base64 v C# – Kompletní průvodce
url: /cs/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Převod PNG na Base64 v C# – Kompletní průvodce

Už jste někdy potřebovali **convert PNG to Base64**, ale nebyli jste si jisti, kde začít? Nejste v tom sami; mnoho vývojářů narazí na tuto překážku, když se snaží vložit obrázky přímo do HTML nebo CSS. Dobrou zprávou je, že řešení je poměrně jednoduché, jakmile znáte správné kroky.

V tomto tutoriálu projdeme kompletním, spustitelným příkladem, který **base64 encode image** data, ukáže vám, jak **embed image html base64** pomocí data‑URI, a dokonce vysvětlí nejlepší způsob, jak **copy stream to memory** bez úniku prostředků. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného .NET projektu.

## Co se naučíte

- Jak ověřit příponu souboru nezávisle na velikosti písmen.  
- Nejbezpečnější vzor pro převod **image stream to base64** pomocí `MemoryStream`.  
- Vytvoření správného data‑URI, které prohlížeče rozumí.  
- Vyčištění původního proudu, aby aplikace zůstala úsporná.  

Nejsou potřeba žádné externí knihovny – stačí třídy BCL, které jsou součástí .NET. Pokud jste obeznámeni se základy C# a máte projekt, který již zpracovává nahrávání souborů, můžete začít.

---

![Diagram ukazující tok od souboru PNG k Base64 data‑URI – převod png na base64](https://example.com/convert-png-to-base64-diagram.png "příklad převodu png na base64")

## Převod PNG na Base64 – krok za krokem

Níže rozdělujeme proces do pěti logických kroků. Každý nadpis odráží část skládačky, což vám (a AI asistentům) usnadní najít přesně tu část, kterou potřebujete.

### Krok 1: Ověřte, že zdroj je PNG (nezávisle na velikosti písmen)

Než zbytečně spotřebujeme paměť, ověříme, že přicházející soubor je skutečně PNG. Příznak `StringComparison.OrdinalIgnoreCase` zvládne jakoukoli kombinaci velkých a malých písmen v příponě.

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*Proč je to důležité:* Pokus o zakódování souboru, který není obrázkem (nebo JPEG) jako PNG, může výstup poškodit a rozbít data‑URI, které později vložíte.

### Krok 2: Zkopírujte proud do paměti

Přicházející `Stream` (např. z obsluhy nahrávání) musí být plně přečten. Použití příkazu `using var` zaručuje, že buffer bude automaticky uvolněn, což udržuje **copy stream to memory** čistý.

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*Tip:* Pokud pracujete s velmi velkými soubory, zvažte `CopyToAsync` s rozumnou velikostí bufferu, aby nedocházelo k blokování vláken.

### Krok 3: Zakódujte obrázek do Base64

Nyní, když jsou bajty obrázku v `memory`, můžeme je převést na řetězec Base64. To je jádro **base64 encode image**.

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*Co se děje?* `Convert.ToBase64String` přijímá pole bajtů a vrací textovou reprezentaci, kterou prohlížeče mohou dekódovat zpět na binární data.

### Krok 4: Vytvořte Data‑URI pro HTML/CSS

Data‑URI vám umožní vložit obrázek přímo do značky, čímž odstraníte další HTTP požadavky. Formát je `data:[<mediatype>][;base64],<data>`.

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

Když později vykreslíte `args.ResourceFilePath` uvnitř značky `<img src="...">`, prohlížeč zobrazí PNG okamžitě.

### Krok 5: Uvolněte původní proud

Protože je obrázek nyní reprezentován data‑URI, původní `Stream` již není potřeba. Nastavením na `null` pomůžete garbage collectoru uvolnit podkladový socket nebo souborový handle.

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*Hraniční případ:* Pokud budete potřebovat původní soubor později (např. pro uložení na disk), tento krok přeskočte a uchovejte odkaz jinde.

---

## Kompletní funkční příklad

Složení všech částí dohromady dává kompaktní metodu, kterou můžete vložit do libovolné třídy zpracovávající nahrané zdroje.

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**Očekávaný výstup:** Po spuštění `ProcessPng` obsahuje `args.ResourceFilePath` řetězec, který vypadá takto:

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Nyní můžete tento řetězec vložit přímo do značky `<img>`:

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

Obrázek se zobrazí okamžitě, bez jakéhokoli dalšího síťového provozu.

---

## Časté otázky a hraniční případy

### Co když je PNG obrovské?

Velké obrázky mohou výrazně zvýšit využití paměti, protože celý soubor žije v `MemoryStream`. Pro soubory větší než několik megabajtů zvažte streamování převodu na Base64 po částech nebo změnu velikosti obrázku před kódováním.

### Můžu to udělat asynchronně?

Určitě. Nahraďte `CopyTo` za `CopyToAsync` a označte metodu jako `async Task`. Tím uvolníte vlákno požadavku ASP.NET, dokud I/O nedokončí.

```csharp
await args.Stream.CopyToAsync(memory);
```

### Funguje to i s jinými formáty obrázků?

Kód sám o sobě není závislý na formátu; stačí upravit MIME typ v data‑URI (`image/jpeg`, `image/gif` atd.) a podle toho změnit kontrolu přípony.

### Jak elegantně ošetřit chyby?

Zabalte celý blok do `try/catch` a zaznamenejte výjimku. Pokud jste ve webovém API, vraťte 400 Bad Request s užitečnou zprávou.

---

## Závěr

Nyní víte, jak **convert PNG to Base64** v C# od začátku až do konce. Tutoriál pokryl ověření typu souboru, bezpečné kopírování proudu do paměti, provedení **base64 encode image**, vytvoření správného **embed image html base64** data‑URI a úklid prostředků.  

Od tady můžete zkoumat dynamické změny velikosti obrázků, cachování generovaných data‑URI nebo dokonce generování SVG placeholderů. Ať zvolíte cokoli, vzor uvedený výše poslouží jako pevný základ pro jakýkoli scénář, kde potřebujete převést **image stream to base64** a vložit jej přímo do značky.

Máte na tento workflow nějaký vlastní nápad? Možná pracujete s WebAssembly nebo Blazorem – neváhejte sdílet své experimenty v komentářích. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}