---
title: Povolit Zakázat nahrazování písem
linktitle: Povolit Zakázat nahrazování písem
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak povolit nebo zakázat nahrazování písem v dokumentech aplikace Word pomocí Aspose.Words for .NET. Zajistěte, aby vaše dokumenty vypadaly konzistentně na všech platformách.
weight: 10
url: /cs/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolit Zakázat nahrazování písem

## Zavedení

Ocitli jste se někdy v situaci, kdy jsou vaše pečlivě vybraná písma v dokumentu aplikace Word nahrazena při zobrazení na jiném počítači? Nepříjemné, že? To se děje kvůli substituci písem, což je proces, kdy systém nahradí chybějící písmo dostupným písmem. Ale nebojte se! S Aspose.Words for .NET můžete snadno spravovat a ovládat nahrazování písem. V tomto tutoriálu vás provedeme kroky, jak povolit nebo zakázat nahrazování písem v dokumentech aplikace Word, aby vaše dokumenty vždy vypadaly tak, jak chcete.

## Předpoklady

Než se ponoříte do kroků, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Stáhněte si nejnovější verzi[zde](https://releases.aspose.com/words/net/).
- Visual Studio: Jakákoli verze podporující .NET.
- Základní znalost C#: To vám pomůže sledovat spolu s příklady kódování.

## Importovat jmenné prostory

Chcete-li začít, ujistěte se, že máte do projektu importovány potřebné jmenné prostory. Přidejte je do horní části souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si tento proces rozdělíme do jednoduchých, zvládnutelných kroků.

## Krok 1: Nastavte svůj projekt

Nejprve nastavte nový projekt v sadě Visual Studio a přidejte odkaz na knihovnu Aspose.Words for .NET. Pokud jste tak ještě neučinili, stáhněte si jej z[Aspose webové stránky](https://releases.aspose.com/words/net/).

## Krok 2: Vložte svůj dokument

Dále načtěte dokument, se kterým chcete pracovat. Postup je následující:

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři dokumentů. Tento kód načte dokument do paměti, abyste s ním mohli manipulovat.

## Krok 3: Nakonfigurujte nastavení písma

 Nyní vytvoříme a`FontSettings` objekt pro správu nastavení nahrazování písem:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Krok 4: Nastavte výchozí náhradu písma

Nastavte výchozí nahrazování písma na písmo podle vašeho výběru. Toto písmo se použije, pokud původní písmo není k dispozici:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

V tomto příkladu používáme jako výchozí písmo Arial.

## Krok 5: Zakažte nahrazování informací o písmu

Chcete-li zakázat nahrazování informací o písmech, které brání systému nahrazovat chybějící písma dostupnými, použijte následující kód:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Krok 6: Použijte nastavení písma na dokument

Nyní použijte tato nastavení na váš dokument:

```csharp
doc.FontSettings = fontSettings;
```

## Krok 7: Uložte dokument

Nakonec upravený dokument uložte. Můžete jej uložit v libovolném formátu. Pro tento tutoriál jej uložíme jako PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Závěr

A tady to máte! Pomocí následujících kroků můžete snadno ovládat nahrazování písem v dokumentech aplikace Word pomocí Aspose.Words for .NET. To zajistí, že si vaše dokumenty zachovají svůj zamýšlený vzhled a dojem, bez ohledu na to, kde jsou zobrazeny.

## FAQ

### Mohu pro nahrazování použít jiná písma než Arial?

 Absolutně! Jakékoli písmo dostupné ve vašem systému můžete určit změnou názvu písma v souboru`DefaultFontName` vlastnictví.

### Co se stane, když zadané výchozí písmo není k dispozici?

Pokud výchozí písmo není k dispozici, Aspose.Words použije systémový záložní mechanismus k nalezení vhodné náhrady.

### Mohu po vypnutí znovu povolit nahrazování písem?

 Ano, můžete přepínat`Enabled` vlastnictví`FontInfoSubstitution` zpět k`true` pokud chcete znovu povolit nahrazování písem.

### Existuje způsob, jak zkontrolovat, která písma jsou nahrazována?

Ano, Aspose.Words poskytuje metody pro protokolování a sledování nahrazování písem, což vám umožňuje vidět, která písma jsou nahrazována.

### Mohu tuto metodu použít pro jiné formáty dokumentů kromě DOCX?

Rozhodně! Aspose.Words podporuje různé formáty a tato nastavení písma můžete použít na jakýkoli podporovaný formát.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
