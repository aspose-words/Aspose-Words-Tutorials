---
category: general
date: 2026-06-27
description: Naučte se zachytávat varování o nahrazení písma v Javě pomocí Aspose.Words.
  Tento krok‑za‑krokem tutoriál také pokrývá zpětná volání varování a použití LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: cs
og_description: Zachyťte varování o nahrazování písem v Javě pomocí Aspose.Words.
  Postupujte podle tohoto návodu k nastavení zpětných volání varování, použití LoadOptions
  a zpracování chybějících písem.
og_title: Zachycení varování o substituci písma v Javě – tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Zachycení upozornění na nahrazení fontů v Javě s Aspose.Words – Kompletní průvodce
url: /cs/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachycení varování o náhradě fontů v Javě s Aspose.Words – Kompletní průvodce

Už jste někdy potřebovali **zachytit varování o náhradě fontů** při načítání DOCX, který používá exotické typy písma? Nejste v tom sami. V mnoha reálných projektech—například automatizovaných generátorech zpráv nebo dávkových konvertorech dokumentů—chybějící fonty spouštějí tiché náhrady, které mohou narušit věrnost rozvržení.  

Naštěstí vám Aspose.Words poskytuje čistý způsob, jak naslouchat těmto varováním. V tomto tutoriálu vás provedeme konfigurací **LoadOptions**, nastavením **Aspose.Words warning callback** a výpisem každého *varování o náhradě fontu* do konzole. Na konci přesně vědět, kdy byl font vyměněn a jak na to programově reagovat.

> **Co získáte:** plně spustitelný úryvek Java kódu, vysvětlení *proč* je každá část důležitá a tipy pro zvládání okrajových případů, jako jsou vlastní složky s fonty.

## Požadavky a co budete potřebovat

Before we dive in, make sure you have:

- Java 8 nebo novější nainstalované (kód funguje také s Java 11+).
- Nejnovější Aspose.Words for Java JAR (stáhněte z oficiálního webu nebo Maven Central).
- DOCX soubor, který odkazuje na fonty neinstalované ve vašem systému (např. *font‑rich.docx* naleznete v demo sadě Aspose).
- Přijatelné IDE (IntelliJ IDEA, Eclipse nebo i VS Code s rozšířeními pro Java).

Kromě Aspose.Words nejsou vyžadovány žádné externí knihovny a příklad běží v jednoduché metodě `main`.

## Krok 1: Nastavení LoadOptions – Vstupní bod pro vlastní načítání

`LoadOptions` je konfigurační objekt Aspose.Words, který knihovně říká *jak* dokument načíst. Ve výchozím nastavení tiše nahrazuje chybějící fonty, ale můžete toto chování změnit pomocí varovacího callbacku.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Proč je to důležité:** Bez `LoadOptions` se dokument načte tiše a ztratíte přehled o chybějících fontech. Vytvořením instance získáte háček do varovacího systému.

## Krok 2: Definování varovacího callbacku pro *zachycení varování o náhradě fontů*

Aspose.Words vysílá varovné události přes rozhraní `IWarningCallback`. Implementujte jej inline (nebo jako samostatnou třídu) a filtrujte podle `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Vysvětlení:**  
- `info.getWarningType()` vám říká kategorii varování.  
- `WarningType.FONT_SUBSTITUTION` je hodnota výčtu, o kterou nám jde.  
- `info.getDescription()` obsahuje lidsky čitelnou zprávu, např. *„Font 'Comic Sans MS' nebyl nalezen, byl nahrazen fontem 'Arial'.“*  

Tisknutím popisu **zachytíte varování o náhradě fontů** v reálném čase.

## Krok 3: Načtení dokumentu pomocí nakonfigurovaných LoadOptions

Jakmile je callback nastaven, načtěte svůj DOCX. Varovací callback se spustí automaticky během parsování.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Nahraďte `YOUR_DIRECTORY` skutečnou cestou k vašemu testovacímu souboru. Když se spustí konstruktor `Document`, jakýkoli chybějící font spustí dříve definovaný callback a na konzoli uvidíte zprávy o náhradě.

## Krok 4: Ověření načteného dokumentu (volitelné, ale užitečné)

Po načtení můžete chtít ověřit integritu dokumentu—počet stránek, extrakci textu atd. Tento krok není nutný pro zachycení varování, ale pomůže vám vidět dopad náhrad.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Pokud byl font nahrazen, rozvržení se může mírně posunout; kontrola počtu stránek může odhalit takové změny.

## Krok 5: Pokročilé – Programové zpracování nahrazených fontů

Někdy nechcete jen zaznamenat varování—můžete potřebovat vložit náhradní font nebo upravit stylování. Níže je rychlý vzor, který můžete použít.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Nasměrováním Aspose.Words na složku, která obsahuje originální fonty, můžete *zabránit* náhradě úplně. Pokud složka chybí, varovací callback stále zachytí událost a poskytne vám náhradní strategii.

## Kompletní funkční příklad

Spojením všech částí získáte kompletní, připravený k spuštění program:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Očekávaný výstup do konzole** (když je detekován chybějící font):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Pokud jsou všechny fonty přítomny, callback zůstane tichý—nic se nevytiskne, což je přesně to, co byste očekávali.

## Časté úskalí a profesionální tipy

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Callback se nikdy nespustí** | Zapomněli jste připojit callback k `LoadOptions` **nebo** použili výchozí konstruktor `Document` bez předání `loadOptions`. | Vždy zavolejte `loadOptions.setWarningCallback(...)` **a** použijte přetížený konstruktor `new Document(path, loadOptions)`. |
| **Příliš mnoho varování zaplňuje log** | Velké dokumenty s mnoha chybějícími fonty generují varování pro každou náhradu. | Dále filtrujte kontrolou `info.getDescription()` na konkrétní názvy fontů, nebo agregujte varování do seznamu pro pozdější zpracování. |
| **Nahrazené fonty ovlivňují rozvržení** | Náhradní font může mít jiné metriky (velikost, rozestupy). | Poskytněte vlastní složku s fonty (viz Krok 5) nebo po načtení upravte styl dokumentu. |
| **Běh na serveru bez grafického rozhraní** | Výchozí náhrada fontu může spoléhat na systémové fonty, které na serveru nejsou nainstalovány. | Distribuujte potřebné fonty s aplikací a nasměrujte `FontSettings` na tuto složku. |

## Často kladené otázky

**Q: Funguje to i s PDF nebo jinými formáty?**  
A: Ano. Varovací callback je nezávislý na formátu; spouští se pro jakýkoli typ dokumentu, který Aspose.Words načítá (DOC, DOCX, RTF, HTML, atd.). Jediný rozdíl je v množině varování, která se může objevit.

**Q: Mohu zachytit i jiné typy varování, například varování o *rozlišení obrázku*?**  
A: Rozhodně. V metodě `warning` zkontrolujte `info.getWarningType()` na jiné hodnoty výčtu, jako je `WarningType.IMAGE_RESOLUTION`. Pak je můžete zpracovat podle potřeby.

**Q: Co když potřebuji seznam nahrazených fontů po načtení dokumentu?**  
A: Uložte každé `info.getDescription()` do `List<String>` uvnitř callbacku. Po načtení budete mít kolekci, kterou můžete zaznamenat, odeslat do monitorovací služby nebo použít k spuštění rutiny pro stažení fontů.

## Závěr

Nyní víte **jak zachytit varování o náhradě fontů** v Javě pomocí Aspose.Words, proč je každá část důležitá a jak rozšířit řešení pro reálné scénáře. Využitím `LoadOptions`, `Aspose.Words warning callback` a volitelných `FontSettings` získáte úplný přehled o chybějících fontech a můžete udržet spolehlivé pipeline pro konverzi dokumentů.

Jste připraveni na další krok? Zkuste nahradit `System.out.println` loggerem jako SLF4J, nebo integrovat seznam varování do UI, které uživatele upozorní před dokončením dávkové konverze. Můžete také prozkoumat **Aspose.Words warning callback** pro jiné typy varování, jako jsou *nepodporované funkce* nebo *varování o vysokém rozlišení obrázku*.

Šťastné programování a ať vaše PDF už nikdy netrpí nečekanými výměnami fontů!

![Snímek obrazovky zobrazující výstup do konzole zachycených varování o náhradě fontů](image-placeholder.png "zachycení varování o náhradě fontů")


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Povolení varování o náhradě fontů v Aspose.Words – Kompletní průvodce](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Jak nastavit LoadOptions v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak vytvořit PDF dokumenty s Aspose.Words pro Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}