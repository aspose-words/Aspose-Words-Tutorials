---
"description": "Naučte se, jak zadat výchozí písmo při vykreslování dokumentů Word pomocí Aspose.Words pro .NET. Zajistěte konzistentní vzhled dokumentu napříč platformami."
"linktitle": "Zadání výchozího písma při vykreslování"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zadání výchozího písma při vykreslování"
"url": "/cs/net/working-with-fonts/specify-default-font-when-rendering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zadání výchozího písma při vykreslování

## Zavedení

Zajištění správného vykreslování dokumentů Word na různých platformách může být náročné, zejména s ohledem na kompatibilitu písem. Jedním ze způsobů, jak zachovat konzistentní vzhled, je zadat výchozí písmo při vykreslování dokumentů do PDF nebo jiných formátů. V tomto tutoriálu se podíváme na to, jak nastavit výchozí písmo pomocí Aspose.Words pro .NET, aby vaše dokumenty vypadaly skvěle bez ohledu na to, kde se prohlížejí.

## Předpoklady

Než se pustíme do kódu, pojďme si v tomto tutoriálu ukázat, co je potřeba dodržovat:

- Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi. Můžete si ji stáhnout [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí pro .NET.
- Základní znalost C#: Tento tutoriál předpokládá, že máte zkušenosti s programováním v C#.

## Importovat jmenné prostory

Pro začátek je potřeba importovat potřebné jmenné prostory. Ty vám umožní přístup ke třídám a metodám potřebným pro práci s Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si rozdělme proces zadávání výchozího písma na snadno sledovatelné kroky.

## Krok 1: Nastavení adresáře dokumentů

Nejprve definujte cestu k adresáři s dokumenty. Zde budou uloženy vaše vstupní a výstupní soubory.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vložte dokument

Dále načtěte dokument, který chcete vykreslit. V tomto příkladu použijeme soubor s názvem „Rendering.docx“.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Konfigurace nastavení písma

Vytvořte instanci `FontSettings` a zadejte výchozí písmo. Pokud definované písmo nelze během vykreslování nalézt, Aspose.Words použije nejbližší dostupné písmo na počítači.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Krok 4: Použití nastavení písma v dokumentu

Přiřaďte nakonfigurované nastavení písma k dokumentu.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Uložte dokument

Nakonec dokument uložte v požadovaném formátu. V tomto případě jej uložíme jako PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Závěr

Dodržením těchto kroků zajistíte, že se vaše dokumenty Wordu budou vykreslovat s určeným výchozím písmem a zachová se tak konzistence napříč různými platformami. To může být obzvláště užitečné pro dokumenty sdílené široce nebo zobrazované na systémech s různou dostupností písem.


## Často kladené otázky

### Proč v Aspose.Words zadávat výchozí písmo?
Zadáním výchozího písma zajistíte, že se dokument bude zobrazovat konzistentně na různých platformách, a to i v případě, že původní písma nejsou k dispozici.

### Co se stane, když se během vykreslování nenajde výchozí písmo?
Aspose.Words použije nejbližší dostupné písmo na počítači, aby co nejvěrněji zachoval vzhled dokumentu.

### Mohu zadat více výchozích písem?
Ne, můžete zadat pouze jedno výchozí písmo. V konkrétních případech však můžete provést nahrazení písma pomocí `FontSettings` třída.

### Je Aspose.Words pro .NET kompatibilní se všemi verzemi dokumentů Wordu?
Ano, Aspose.Words pro .NET podporuje širokou škálu formátů dokumentů Word, včetně DOC, DOCX, RTF a dalších.

### Kde mohu získat podporu, pokud narazím na problémy?
Podporu od komunity Aspose a vývojářů můžete získat na [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}