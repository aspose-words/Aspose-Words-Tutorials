---
category: general
date: 2026-01-03
description: Jak detekovat písma v Aspose.Words a zpracovávat varování pomocí nastavení
  písma Aspose – krok za krokem průvodce pro vývojáře.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: cs
og_description: Jak detekovat písma v Aspose.Words a nastavit upozornění pomocí nastavení
  písma Aspose. Naučte se celý pracovní postup během několika minut.
og_title: Jak detekovat písma v Aspose.Words – Zpracování varování
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak detekovat písma v Aspose.Words – Zpracování varování a nastavení
url: /cs/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak detekovat písma v Aspose.Words – Zpracování varování a nastavení

Už jste se někdy zamýšleli **jak detekovat písma** v dokumentu Word, než se dostane do produkce? Nejste jediní. Chybějící písma mohou způsobit noční můry s rozvržením a bez řádných varování můžete odeslat poškozený PDF nebo DOCX, aniž byste si toho všimli.  

V tomto tutoriálu si projdeme **jak detekovat písma** pomocí Aspose.Words, ukážeme **jak zpracovat varování** a vyladíme **Aspose nastavení písem**, abyste mohli **konfigurovat varování** přesně tak, jak potřebujete. Na konci budete mít připravený úryvek kódu, který vypíše každou substituci, kterou Aspose provede, a budete vědět, jak jej přizpůsobit pro své projekty.

## Požadavky

- .NET 6+ (nebo .NET Framework 4.6+).  
- Aspose.Words pro .NET nainstalovaný přes NuGet (`Install-Package Aspose.Words`).  
- Soubor Word, který úmyslně odkazuje na chybějící písmo (např. *DocumentWithMissingFonts.docx*).  

Pokud už máte vše připravené, skvělé – pojďme na to.

![snímek obrazovky detekce písem](https://example.com/detect-fonts.png "příklad výstupu detekce písem")

## Jak detekovat písma pomocí Aspose.Words

Prvním krokem je říci Aspose.Words, že vás zajímají události substituce písem. To se provede poskytnutím vlastního callbacku pro varování přes **Aspose nastavení písem**. Callback dostane objekt `WarningInfo` pro každou substituci, což vám umožní **detekovat písma** za běhu.

### Krok 1: Vytvořte třídu pro callback varování

Implementujte rozhraní `IWarningCallback`. V metodě `Warning` filtrujte podle `WarningType.FontSubstitution` a zaznamenejte podrobnosti.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Tip:** Řetězec `info.Description` obsahuje jak název chybějícího písma, tak i náhradní písmo, které Aspose vybral. Můžete jej rozparsovat, pokud potřebujete strukturovanou zprávu.

### Krok 2: Nakonfigurujte LoadOptions s Aspose nastavením písem

Vytvořte instanci `LoadOptions`, připojte čerstvý objekt `FontSettings` a nastavte `WarningCallback` na handler, který jsme právě vytvořili. Tím řeknete Aspose, **jak konfigurovat varování**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Pokud máte soukromou složku s písmy, můžete ji přidat takto:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Tento řádek ukazuje další aspekt **aspose nastavení písem** – určujete přesně, kde Aspose hledá písma, než se rozhodne provést substituci.

### Krok 3: Načtěte dokument a spustěte callback

Nyní načtěte cílový dokument s `loadOptions`. Jakmile Aspose parsuje soubor, každé chybějící písmo spustí handler varování, čímž **detekuje písma** za běhu.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Po spuštění programu uvidíte výstup podobný tomuto:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Krok 4: (Volitelné) Shromažďujte varování pro pozdější použití

Pokud potřebujete uložit data o substitucích pro zprávu, upravte handler tak, aby akumuloval zprávy v seznamu.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Později můžete `handler.Substitutions` zapsat do JSON souboru, odeslat jej do logovací služby nebo zobrazit v uživatelském rozhraní.

### Krok 5: Ověřte výsledek programově

Někdy chcete potvrdit, že *neproběhla* žádná substituce (např. v CI buildu). Zde je rychlá kontrola:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Tento úryvek demonstruje **jak zpracovat varování** deterministickým způsobem a dává vám plnou kontrolu nad pipeline sestavení.

## Často kladené otázky (a okrajové případy)

**Co když potřebuji ignorovat určité substituce?**  
Můžete přidat podmíněnou logiku uvnitř `Warning` a jednoduše vrátit bez logování pro písma, která považujete za přijatelné.

**Mohu potlačit všechna varování a získat jen booleovský výsledek?**  
Ano – nastavte `loadOptions.WarningCallback = null` a pak po načtení prozkoumejte `doc.FontInfo` (i když přijdete o podrobný log).

**Funguje to i při konverzi do PDF?**  
Rozhodně. Stejný mechanismus varování se spustí, když zavoláte `doc.Save("out.pdf")`. Callback zachytí všechny výměny písem provedené během konverze.

**Má to dopad na výkon?**  
Zátěž je minimální – jen několik dalších volání metod na každé chybějící písmo. U velkých dávkách můžete chtít výsledek kešovat.

## Shrnutí: Co jsme probrali

- **Jak detekovat písma** implementací vlastního `IWarningCallback`.  
- **Jak zpracovat varování** pomocí `LoadOptions.WarningCallback`.  
- Ladění **Aspose nastavení písem** (přidání vlastních složek s písmy, povolení/zakázání varování).  
- **Jak konfigurovat varování** pro okamžitý výstup do konzole i pozdější analýzu.  

S těmito částmi můžete sebejistě zpracovávat Word dokumenty, zajistit, že chybějící písma jsou označena, a udržet výstup konzistentní napříč prostředími.

## Další kroky

- Prozkoumejte `FontSettings.SubstitutionSettings` pro podrobnější kontrolu (např. mapování konkrétních chybějících písem na vybrané náhrady).  
- Kombinujte tento přístup s Aspose.PDF pro generování PDF, která zachovají přesnou typografii.  
- Automatizujte kontrolu varování v CI/CD pipeline, aby se blokovaly vydání obsahující problémy s písmy – ideální pro týmy, které **zpracovávají varování** jako součást kvality.

Máte další otázky ohledně **aspose nastavení písem** nebo potřebujete pomoc s integrací do větší služby? Zanechte komentář níže a šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}