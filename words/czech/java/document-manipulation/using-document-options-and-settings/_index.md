---
date: 2026-01-16
description: Naučte se zvýrazňovat pravopisné chyby ve Wordu pomocí Aspose.Words pro
  Javu a zjistěte, jak nastavit počet znaků na řádek, přizpůsobit možnosti zobrazení
  a vyčistit styly.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Zvýraznit pravopisné chyby ve Wordu pomocí Aspose.Words Java
url: /cs/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání možností a nastavení dokumentu v Aspose.Words pro Java

## Úvod do používání možností a nastavení dokumentu v Aspose.Words pro Java

V tomto komplexním průvodci se naučíte **jak zvýraznit pravopisné chyby ve Wordu** pomocí Aspose.Words pro Java a zároveň ovládnout související nastavení, jako jsou možnosti zobrazení, rozvržení stránky a čištění stylů. Ať už jste zkušený vývojář nebo teprve začínáte, níže uvedené příklady vám pomohou vytvořit robustní dokumenty, které jsou si vědomy chyb a fungují napříč verzemi Wordu.

## Rychlé odpovědi
- **Jak mohu zvýraznit pravopisné chyby ve Wordu?** Použijte `setShowSpellingErrors(true)` na objektu `Document`.  
- **Mohu také zobrazit gramatické chyby?** Ano – zavolejte `setShowGrammaticalErrors(true)`.  
- **Jaká metoda nastavuje počet znaků na řádek?** `getPageSetup().setCharactersPerLine(int)`.  
- **Které API optimalizuje pro konkrétní verzi Wordu?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Existuje způsob, jak vyčistit nepoužívané styly?** Použijte `CleanupOptions` s `setUnusedStyles(true)` a zavolejte `doc.cleanup(options)`.

## Jak zvýraznit pravopisné chyby ve Wordu?

Aspose.Words usnadňuje zapnutí zvýraznění pravopisných chyb. Když je dokument otevřen v Microsoft Wordu, nesprávně napsaná slova se zobrazí se známou červenou podtržítkou, což uživatelům okamžitě pomáhá odhalit problémy.

## Jak nastavit počet znaků na řádek

Řízení počtu znaků na řádek je nezbytné pro rozvržení s pevnou šířkou (např. výpisy kódu nebo starší formuláře). Třída `PageSetup` poskytuje `setCharactersPerLine(int)`, která vám umožní tento hodnotu přesně definovat.

## Jak zobrazit gramatické chyby

Vedle pravopisu můžete také povolit zobrazování gramatických chyb. To je užitečné při tvorbě obsahu, který musí splňovat stylové příručky, nebo při vytváření nástrojů pro korekturu.

## Optimalizace dokumentů pro kompatibilitu

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Jedním klíčovým aspektem správy dokumentů je zajištění kompatibility s různými verzemi Microsoft Wordu. Aspose.Words pro Java poskytuje jednoduchý způsob, jak optimalizovat dokumenty pro konkrétní verze Wordu. Ve výše uvedeném příkladu optimalizujeme dokument pro Word 2016, čímž zajišťujeme bezproblémovou kompatibilitu.

## Identifikace gramatických a pravopisných chyb

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Přesnost je při práci s dokumenty naprosto zásadní. Aspose.Words pro Java vám umožňuje zvýraznit gramatické a pravopisné chyby ve vašich dokumentech, což zefektivňuje korekturu a úpravy.

## Čištění nepoužívaných stylů a seznamů

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Efektivní správa stylů a seznamů v dokumentu je nezbytná pro udržení konzistence dokumentu. Aspose.Words pro Java vám umožňuje vyčistit nepoužívané styly a seznamy, čímž zajišťuje přehlednou a uspořádanou strukturu dokumentu.

## Odstraňování duplicitních stylů

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Duplicitní styly mohou vést k záměně a nekonzistenci ve vašich dokumentech. S Aspose.Words pro Java můžete snadno odstranit duplicitní styly, čímž zachováte jasnost a soudržnost dokumentu.

## Přizpůsobení možností zobrazení dokumentu

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Přizpůsobení způsobu, jakým jsou dokumenty zobrazovány, je klíčové. Aspose.Words pro Java vám umožňuje nastavit různé možnosti zobrazení, jako je rozvržení stránky a procento přiblížení, aby se zvýšila čitelnost dokumentu.

## Konfigurace nastavení stránky dokumentu

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Přesné nastavení stránky je zásadní pro formátování dokumentu. Aspose.Words pro Java vám umožňuje nastavit režimy rozvržení, **znaky na řádek** a řádky na stránku, čímž zajistí, že vaše dokumenty budou vizuálně atraktivní.

## Nastavení jazyků úprav

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Jazyky úprav hrají důležitou roli při zpracování dokumentů. S Aspose.Words pro Java můžete nastavit a přizpůsobit jazyky úprav tak, aby vyhovovaly jazykovým potřebám vašeho dokumentu.

## Závěr

V tomto průvodci jsme se ponořili do různých možností a nastavení dokumentu dostupných v Aspose.Words pro Java. Od optimalizace a zobrazování chyb po čištění stylů a možnosti zobrazení, tato výkonná knihovna nabízí rozsáhlé možnosti pro správu a přizpůsobení vašich dokumentů.

## Často kladené otázky

### Jak optimalizovat dokument pro konkrétní verzi Wordu?

Pro optimalizaci dokumentu pro konkrétní verzi Wordu použijte metodu `optimizeFor` a uveďte požadovanou verzi. Například pro optimalizaci pro Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Jak mohu zvýraznit gramatické a pravopisné chyby v dokumentu?

Můžete povolit zobrazování gramatických a pravopisných chyb v dokumentu pomocí následujícího kódu:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Jaký je účel čištění nepoužívaných stylů a seznamů?

Čištění nepoužívaných stylů a seznamů pomáhá udržet čistou a uspořádanou strukturu dokumentu. Odstraňuje zbytečný nepořádek, čímž zlepšuje čitelnost a konzistenci dokumentu.

### Jak mohu odstranit duplicitní styly z dokumentu?

Aby bylo možné odstranit duplicitní styly z dokumentu, použijte metodu `cleanup` s nastavenou volbou `duplicateStyle` na `true`. Zde je příklad:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Jak přizpůsobit možnosti zobrazení dokumentu?

Můžete přizpůsobit možnosti zobrazení dokumentu pomocí třídy `ViewOptions`. Například pro nastavení typu zobrazení na rozvržení stránky a přiblížení na 50 %:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Další tipy a běžné úskalí

- **Povolte kontrolu pravopisu i gramatiky**, pokud potřebujete komplexní korekturu. Zapomenutí jednoho z příznaků (`setShowGrammaticalErrors` nebo `setShowSpellingErrors`) může nechat chyby neodhalené.  
- **Při nastavování znaků na řádek** mějte na paměti, že hodnota interaguje s vybraným fontem a okraji stránky. Otestujte s reálným rozvržením dokumentu, abyste předešli neočekávaným zalomením řádků.  
- **Operace čištění jsou nevratné** na původním souboru. Vždy pracujte s kopií nebo použijte verzování, aby byl originální styl zachován.  
- **Preference jazyků úprav** ovlivňují chování kontroly pravopisu. Pokud cílíte na vícejazyčné dokumenty, přidejte všechny relevantní jazyky do `LanguagePreferences`.

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}