---
category: general
date: 2026-04-01
description: Zapněte varování o fontech při načítání dokumentů Word pomocí Aspose.Words.
  Naučte se zachytit události nahrazení fontu pomocí C# LoadOptions a nastavení fontů.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: cs
og_description: Povolit upozornění na písmo při načítání dokumentů Word pomocí Aspose.Words.
  Tento tutoriál ukazuje, jak zachytit události nahrazení písma v C#.
og_title: Povolit varování o fontech v Aspose.Words – Kompletní průvodce C#
tags:
- Aspose.Words
- C#
- Font Management
title: Povolit varování o písmu v Aspose.Words – Kompletní průvodce C#
url: /cs/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolení varování o písmu v Aspose.Words – Kompletní C# průvodce

Už jste se někdy zamysleli, proč se Word dokument najednou zobrazuje jinak, když jej načtete programově? **Enable Font Warnings** a okamžitě zjistíte, kdy Aspose.Words nahradí chybějící písmo náhradním. V tomto tutoriálu projdeme praktickým příkladem, který nejen zachytí tyto substituce, ale také vysvětlí *proč* se stávají.

Probereme vše, co potřebujete k zahájení: požadovaný NuGet balíček, přesnou konfiguraci `LoadOptions` a přehledný výstup do konzole, který vám řekne, která písma byla nahrazena. Na konci budete mít robustní, znovupoužitelný vzor pro **C# document processing**, který funguje s libovolnou verzí Aspose.Words.

## Co se naučíte

- Jak vytvořit instanci `LoadOptions`, která sleduje změny písem.  
- Účel události `SubstitutionWarning` a jak ji připojit.  
- Kompletní, spustitelný ukázkový kód, který vypisuje jasná varování do konzole.  
- Tipy pro zpracování okrajových případů, jako jsou dokumenty obsahující pouze standardní písma.  

Předchozí zkušenost s Aspose.Words není vyžadována – stačí základní znalost C# a .NET.

---

![diagram povolení varování o písmu](placeholder-image.png "Diagram povolení varování o písmu")

*Alt text: diagram povolení varování o písmu zobrazující tok událostí, když je chybějící písmo nahrazeno.*

## Krok 1: Nastavení LoadOptions a povolení varování o písmu

Prvním, co potřebujete, je objekt `LoadOptions`. Tento kontejner říká Aspose.Words, jak má zacházet se souborem, který se chystáte načíst. Přiřazením nové instance `FontSettings` otevřete dveře událostem souvisejícím s písmy.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Proč je to důležité:**  
Pokud vynecháte přiřazení `FontSettings`, Aspose.Words stále nahradí chybějící písma, ale nedostanete žádné oznámení. Mechanismus varování žije uvnitř `FontSettings`, takže jeho inicializace je *klíčová* pro náš cíl.

> **Tip:** Můžete také nasměrovat `FontSettings` na vlastní složku s fonty pomocí `SetFontsFolder`. Tím snížíte počet varování, která uvidíte, protože Aspose.Words dokáže skutečně najít chybějící typy písma.

## Krok 2: Přihlášení k události SubstitutionWarning (nahrazení písma)

Nyní, když existuje objekt `FontSettings`, připojíme se k jeho události `SubstitutionWarning`. Tato událost se spustí **každýkrát**, když Aspose.Words nahradí požadované písmo něčím jiným.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Proč je to důležité:**  
Bez tohoto posluchače nebudete mít přehled o procesu substituce. Řádek v konzoli vám poskytne rychlý auditní záznam, což je zvláště užitečné během automatizovaných sestavení nebo při generování PDF pro odvětví s přísnými požadavky na shodu.

> **Často kladená otázka:** *Co když chci varování potlačit?*  
> Můžete jednoduše odpojit obslužnou rutinu nebo nastavit `FontSettings.SubstitutionWarning += null;`. Přesto je obvykle nejbezpečnější ponechat varování, protože tiché substituce mohou vést k problémům s rozvržením.

## Krok 3: Načtení dokumentu s nakonfigurovanými možnostmi (C# document processing)

S připraveným systémem varování je načtení dokumentu jednoduché. Předáte instanci `LoadOptions` konstruktoru `Document` a Aspose.Words udělá zbytek.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Proč je to důležité:**  
Objekt `LoadOptions` je mostem mezi surovým souborem a infrastrukturou varování. Pokud jej vynecháte, dokument se načte tiše a jakákoli chybějící písma budou nahrazena bez záznamu.

> **Okrajový případ:** Některé dokumenty vkládají přesné soubory písem, které potřebují. V takovém scénáři se žádné varování neobjeví, protože Aspose.Words najde vložené písmo. Výše uvedený kód stále funguje; v konzoli uvidíte jen prázdný výstup.

## Krok 4: Ověření výstupu a běžné úskalí

Spusťte program z příkazového řádku nebo debuggeru v IDE. Pokud zdrojový dokument obsahuje písmo, které není nainstalováno na počítači (nebo není dostupné ve vlastní složce s fonty), uvidíte řádky jako:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Pokud se nic nevytiští, je to buď:

1. Všechna písma byla nalezena, **nebo**  
2. Obslužná rutina `SubstitutionWarning` nebyla správně připojena (zkontrolujte krok 2).

### Proč dochází k substitucím písem?

- **Chybějící systémové písmo:** OS nemá požadovaný typ písma.  
- **Nepodporovaný formát písma:** Aspose.Words umí číst TrueType a OpenType, ale ne každý proprietární formát.  
- **Licenční omezení:** Některá komerční písma blokují vkládání, což nutí použít náhradní písmo.

Pochopení *proč* vám pomůže rozhodnout, zda chybějící písma zahrnout do aplikace, nebo upravit stylování dokumentu.

## Bonus: Řízení náhradního písma

Pokud chcete, aby každé chybějící písmo nahradilo konkrétní rodina (např. „Calibri“), můžete nastavit globální pravidlo substituce:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Konzole vás bude i nadále varovat, ale vizuální výsledek bude konzistentní napříč všemi chybějícími písmy.

---

## Shrnutí

- **Enable Font Warnings** vytvořením `LoadOptions` s čerstvým `FontSettings`.  
- Připojte událost `SubstitutionWarning`, abyste získali upozornění v reálném čase vždy, když je písmo nahrazeno.  
- Načtěte dokument pomocí nakonfigurovaných možností a případně jej uložte do PDF, abyste viděli vizuální efekt.  
- Diagnostikujte, proč k substituci došlo, a v případě potřeby vynutí konkrétní náhradní písmo.

Právě jste přidali bezpečnostní síť do vašeho workflow **Aspose.Words**, která zabraňuje tichým změnám rozvržení. Dále můžete prozkoumat **font settings** jako `DefaultFontName` nebo se ponořit do možností **document rendering**, abyste doladili výstup PDF.

---

### Co vyzkoušet dál?

- **Prozkoumejte další funkce FontSettings**: `SetFontsFolder`, `LoadFontSources` a `DefaultFontName`.  
- **Kombinujte varování s logovacími frameworky** (Serilog, NLog) pro diagnostiku úrovně produkce.  
- **Experimentujte s různými formáty dokumentů** (`.doc`, `.rtf`, `.html`), abyste viděli, jak každý zachází s chybějícími písmy.  

Máte otázky nebo zvláštní scénář? Zanechte komentář níže a šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}