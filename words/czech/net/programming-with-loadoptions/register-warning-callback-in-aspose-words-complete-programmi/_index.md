---
category: general
date: 2026-06-27
description: Zaregistrujte varovný callback v Aspose.Words, abyste zachytili nahrazení
  fontů a problémy s načítáním. Naučte se krok za krokem používat LoadOptions s Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: cs
og_description: Zaregistrujte výstražný callback v Aspose.Words pro sledování substitucí
  fontů a dalších varování při načítání. Postupujte podle tohoto kompletního tutoriálu
  pro robustní implementaci.
og_title: Zaregistrovat varovný callback v Aspose.Words – Kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Zaregistrovat výstražný callback v Aspose.Words – Kompletní programovací průvodce
url: /cs/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrace výstražného zpětného volání v Aspose.Words – kompletní programový průvodce

Už jste se někdy zamýšleli, jak **registrovat výstražné zpětné volání v Aspose.Words**, abyste přesně viděli, které písma jsou nahrazena při načítání dokumentu? Nejste sami. Mnoho vývojářů narazí na problém, když tichá substituce písma zničí rozvržení vygenerovaného PDF nebo souboru Word.  

V tomto tutoriálu vás provedeme praktickým řešením, které nejen registruje výstražné zpětné volání v Aspose.Words, ale také vysvětluje *proč* to chcete dělat, jak zpětné volání funguje pod kapotou a s jakými okrajovými případy se můžete setkat. Na konci budete schopni zaznamenávat každou substituci písma, zachytit další výstrahy při načítání a udržet svůj pipeline pro zpracování dokumentů transparentní.

## Co se naučíte

- Nastavení **LoadOptions** pro řízení chování načítání dokumentu.  
- Registraci **výstražného zpětného volání**, které se spouští při substituci písma a dalších typech výstrah.  
- Načtení DOCX s nakonfigurovanými možnostmi a interpretaci výstupu zpětného volání.  
- Běžné úskalí (chybějící písma, vlastní složky s fonty a úvahy o výkonu).  

**Předpoklady:** Visual Studio 2022 (nebo jakékoli C# IDE), .NET 6+ runtime a aktivní licence Aspose.Words (bezplatná zkušební verze stačí pro experimentování). Žádné další NuGet balíčky kromě `Aspose.Words` nejsou vyžadovány.

---

![Diagram znázorňující tok registrace výstražného zpětného volání v Aspose.Words a zpracování výstrah o substituci fontů](register-warning-callback-aspose-words.png "diagram registrace výstražného zpětného volání aspose.words")

## Krok 1: Vytvoření LoadOptions – vstupní bod pro zpracování výstrah  

Než může zpětné volání kdykoli spustit, potřebujete instanci **LoadOptions**. Představte si ji jako ovládací panel, který předáte Aspose.Words s požadavkem „načti tento soubor, ale dej mi vědět, pokud něco vypadá špatně.“  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Proč je to důležité:** `LoadOptions` vám umožňuje ladit vše od šifrovacích hesel po adresáře s fonty. Připojením výstražného zpětného volání k tomuto objektu proměníte tichý proces na pozorovatelný.

## Krok 2: Registrace výstražného zpětného volání – zachycení substitucí fontů  

Nyní přichází hvězda celého představení: **výstražné zpětné volání**. Zaregistrujeme anonymní metodu (lambda), kterou Aspose.Words vyvolá pro každou výstrahu při načítání. V rámci zpětného volání filtrujeme `WarningType.FontSubstitution` a vypíšeme přátelskou zprávu.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Tip:** Pokud chcete také zaznamenávat chybějící obrázky nebo nepodporované funkce, přidejte další podmínky `if` kontrolující `args.WarningType`. Tím učiníte vaši **registraci výstražného zpětného volání v Aspose.Words** univerzálním řešením pro všechny diagnostiky načítání.

## Krok 3: Načtení dokumentu pomocí nakonfigurovaných LoadOptions  

Po připojení zpětného volání je dalším krokem jednoduše načíst dokument. Předáte instanci `loadOptions` konstruktoru `Document`. Pokaždé, když Aspose.Words narazí na písmo, které nemůže najít, vaše zpětné volání se spustí a zapíše do konzole.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Spusťte program a uvidíte výstup podobný tomuto:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

To je podstata **registrace výstražného zpětného volání aspose.words** – tříkrokový vzor, který můžete znovu použít v jakémkoli projektu.

## Krok 4: Rozšíření zpětného volání pro reálné scénáře  

### 4.1 Logování do souboru místo do konzole  

V produkci obvykle nechcete spamovat konzoli. Nahraďte `Console.WriteLine` loggerem (např. `Serilog`, `NLog`) nebo zápisem do textového souboru:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Poskytnutí vlastního adresáře s fonty  

Pokud vaše prostředí používá firemní fonty, řekněte Aspose.Words, kde je hledat, než přejde k substituci:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Nyní se zpětné volání spustí *méně* často, protože engine najde správná písma.

### 4.3 Zpracování ne‑fontových výstrah  

Můžete rozšířit rozsah tak, aby zachycoval jakoukoli výstrahu při načítání:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Krok 5: Testování vaší implementace – co očekávat  

### 5.1 Ověření s dokumentem, který má chybějící fonty  

Vytvořte malý DOCX, který odkazuje na písmo neinstalované ve vašem systému (např. „Comic Sans MS“ na Linux serveru). Spusťte načítač; měli byste vidět zprávu o substituci.  

### 5.2 Měření režie  

Zpětné volání přidává zanedbatelnou režii – přibližně několik mikrosekund na výstrahu. Pokud načítáte tisíce dokumentů, můžete hromadit záznamy nebo vypnout zpětné volání pro ne‑kritické běhy.

### 5.3 Okrajové případy  

- **Více substitucí pro stejné písmo:** Aspose.Words může spustit zpětné volání vícekrát, pokud se chybějící písmo objeví na různých stránkách. V případě potřeby deduplikujte ve svém loggeru.  
- **Šifrované dokumenty:** Pokud je DOCX chráněn heslem, musíte také nastavit `loadOptions.Password`. Zpětné volání se i po dešifrování spustí.  
- **Asynchronní načítání:** API je synchronní, ale můžete volání načtení zabalit do `Task.Run` pro zpracování na pozadí; zpětné volání zůstává thread‑safe.

## Běžné úskalí a jak se jim vyhnout  

| Úskalí | Proč se vyskytuje | Řešení |
|--------|-------------------|--------|
| **Žádný výstup** | Zpětné volání nebylo přiřazeno *nebo* `WarningCallback` byl později přepsán. | Ujistěte se, že přiřadíte zpětné volání **jednou** před načtením a po přiřazení `loadOptions` již nepřepisujete. |
| **Výjimka nesprávného přetypování** | Pokus o přetypování výstrahy, která není `FontSubstitutionWarningInfo`. | Vždy před přetypováním zkontrolujte `args.WarningType`. |
| **Zpomalení výkonu** | Synchronous logging na pomalý I/O cíl. | Použijte asynchronní logging frameworky nebo bufferujte zápisy. |
| **Chybějící vlastní fonty** | Adresář s fonty nebyl přidán do `FontSettings`. | Přidejte `SetFontsFolder` podle ukázky v kroku 4.2. |

## Kompletní funkční příklad – zkopírujte a spusťte  

Níže je samostatný program, který můžete vložit do nového projektu Console App. Ukazuje celý tok od začátku do konce.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Očekávaný výstup do konzole** (při chybějících fontech):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Spusťte program a uvidíte přesně, která písma Aspose.Words nahradilo, což vám poskytne úplnou přehlednost o procesu načítání.

---

## Závěr  

Právě jsme prošli **jak registrovat výstražné zpětné volání v Aspose.Words**, proč je to best‑practice pro jakýkoli workflow zpracování dokumentů, a jak rozšířit tento vzor pro logování, vlastní fonty a širší zpracování výstrah. Pouhými třemi řádky kódu proměníte černou skříňku načítání na auditovatelný, laditelný krok – žádné tajemné změny rozvržení.

Co dál? Zkuste kombinovat toto zpětné volání s **Aspose.Words SaveOptions**, abyste zaznamenávali výstrahy jak při načítání, tak při ukládání, nebo připojte zpětné volání k webovému API, které v reálném čase zpracovává nahrané soubory. Můžete také prozkoumat další sekundární klíčová slova, která jsme zmínili – jako *loadoptions font substitution warning* – pro doladění výkonu nebo integraci s monitorovacím panelem.

Máte otázky nebo složitý scénář? Zanechte komentář a pojďme to společně vyřešit. Šťastné programování a ať se vaše PDF vždy vykreslují se správnými fonty!


## Co byste se měli naučit dál?


Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}