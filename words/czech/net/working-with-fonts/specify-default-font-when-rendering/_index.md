---
title: Při vykreslování zadejte výchozí písmo
linktitle: Při vykreslování zadejte výchozí písmo
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak určit výchozí písmo při vykreslování dokumentů aplikace Word pomocí Aspose.Words for .NET. Zajistěte konzistentní vzhled dokumentu napříč platformami.
weight: 10
url: /cs/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Při vykreslování zadejte výchozí písmo

## Zavedení

Zajištění správného vykreslení dokumentů aplikace Word na různých platformách může být problém, zejména pokud jde o kompatibilitu písem. Jedním ze způsobů, jak zachovat konzistentní vzhled, je určit výchozí písmo při vykreslování dokumentů do PDF nebo jiných formátů. V tomto tutoriálu prozkoumáme, jak nastavit výchozí písmo pomocí Aspose.Words pro .NET, aby vaše dokumenty vypadaly skvěle bez ohledu na to, kde jsou zobrazeny.

## Předpoklady

Než se ponoříme do kódu, pojďme si s tímto návodem probrat, co budete muset dodržovat:

- Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi. Můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
- Základní znalost C#: Tento tutoriál předpokládá, že se vyznáte v programování v C#.

## Importovat jmenné prostory

Chcete-li začít, musíte importovat potřebné jmenné prostory. Ty vám umožní přístup ke třídám a metodám potřebným pro práci s Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si rozeberme proces zadávání výchozího písma do snadno srozumitelných kroků.

## Krok 1: Nastavte adresář dokumentů

Nejprve definujte cestu k adresáři dokumentů. Zde budou uloženy vaše vstupní a výstupní soubory.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vložte svůj dokument

Dále načtěte dokument, který chcete vykreslit. V tomto příkladu použijeme soubor s názvem „Rendering.docx“.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Nakonfigurujte nastavení písma

 Vytvořte instanci`FontSettings` a zadejte výchozí písmo. Pokud nelze během vykreslování najít definované písmo, Aspose.Words použije nejbližší dostupný font na počítači.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Krok 4: Použijte nastavení písma na dokument

Přiřaďte dokumentu nakonfigurovaná nastavení písma.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Uložte dokument

Nakonec dokument uložte v požadovaném formátu. V tomto případě jej uložíme jako PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Závěr

Pomocí těchto kroků můžete zajistit, aby se vaše dokumenty aplikace Word vykreslily se zadaným výchozím písmem, a zachovaly si konzistenci na různých platformách. To může být užitečné zejména pro dokumenty široce sdílené nebo prohlížené na systémech s různou dostupností písem.


## FAQ

### Proč zadat výchozí písmo v Aspose.Words?
Zadáním výchozího písma zajistíte, že váš dokument bude vypadat konzistentně na různých platformách, i když původní písma nejsou k dispozici.

### Co se stane, když nebude během vykreslování nalezeno výchozí písmo?
Aspose.Words použije nejbližší dostupné písmo na stroji, aby zachovalo vzhled dokumentu co nejpřesněji.

### Mohu zadat více výchozích písem?
 Ne, můžete zadat pouze jedno výchozí písmo. Náhradu písem pro konkrétní případy však můžete zvládnout pomocí`FontSettings` třída.

### Je Aspose.Words for .NET kompatibilní se všemi verzemi dokumentů aplikace Word?
Ano, Aspose.Words for .NET podporuje širokou škálu formátů dokumentů Word, včetně DOC, DOCX, RTF a dalších.

### Kde mohu získat podporu, pokud narazím na problémy?
 Podporu od komunity Aspose a vývojářů můžete získat na[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
