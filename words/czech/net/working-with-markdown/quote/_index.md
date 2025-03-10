---
title: Citovat
linktitle: Citovat
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se přidávat uvozovky a vnořené blokové uvozovky do dokumentů aplikace Word pomocí Aspose.Words for .NET. Postupujte podle tohoto podrobného průvodce vytvořením hlavního dokumentu.
weight: 10
url: /cs/net/working-with-markdown/quote/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Citovat

## Zavedení

Zasekli jste se někdy při pokusu o přidání uvozovek do dokumentu aplikace Word pomocí .NET? Může to být pořádný problém, ne? Ale nebojte se, protože dnes vám ukážu, jak zvládnout umění vkládání uvozovek do dokumentů pomocí Aspose.Words pro .NET. Na konci tohoto tutoriálu budete vytvářet dokumenty jako profesionál!

Aspose.Words for .NET je neuvěřitelná knihovna, se kterou je práce s dokumenty Wordu hračkou. Ať už jste zkušený vývojář nebo teprve začínáte, tato příručka vás provede vším, co potřebujete vědět o přidávání uvozovek, včetně vnořených blokových uvozovek, a to způsobem, který je poutavý a snadno sledovatelný. Takže, pojďme se ponořit!

## Předpoklady

Než začneme, je potřeba mít připraveno několik věcí:

-  Aspose.Words for .NET: Můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Ujistěte se, že máte nainstalované Visual Studio nebo jakékoli jiné .NET IDE.
- Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti o programování v C#.

Máte vše připraveno? Velký! Pojďme se pustit do toho zbytečného importu jmenných prostorů a nastavení našeho projektu.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory pro práci s Aspose.Words. To je docela jednoduché. Stačí přidat následující pomocí direktiv v horní části souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Tyto jmenné prostory vám poskytují přístup ke třídám a metodám, které budete potřebovat k manipulaci s dokumenty aplikace Word. Nyní rozeberme příklad do zvládnutelných kroků.

## Krok 1: Vytvořte instanci DocumentBuilder

 Chcete-li začít, musíme vytvořit instanci souboru`DocumentBuilder` třída. Tato třída nám umožňuje přidávat obsah do našeho dokumentu.

```csharp
// K přidání obsahu do dokumentu použijte tvůrce dokumentů.
DocumentBuilder builder = new DocumentBuilder();
```

 The`DocumentBuilder` class je vaší bránou k vytváření a přizpůsobení vašeho dokumentu. Berte to jako kouzelnou hůlku pro vytváření dokumentů aplikace Word!

## Krok 2: Přidejte blokovou nabídku

Dále do našeho dokumentu přidáme základní blockquote. Ve výchozím nastavení dokument ukládá styl blockquote pro první úroveň. Zde je fragment kódu, jak toho dosáhnout:

```csharp
// Ve výchozím nastavení dokument ukládá styl blockquote pro první úroveň.
builder.ParagraphFormat.StyleName = "Quote";
builder.Writeln("Blockquote");
```

Tento kód nastaví styl odstavce na "Citace" a zapíše do dokumentu blokovou citaci. Jednoduché, že?

## Krok 3: Vytvořte styly pro vnořené úrovně

Nyní to trochu okořeníme vytvořením stylů pro vnořené úrovně blockquote. Tady jsou věci zajímavé. Vytvoříme nový styl a jeho základní styl nastavíme na "Citovat":

```csharp
// Vytvářejte styly pro vnořené úrovně prostřednictvím dědičnosti stylů.
Style quoteLevel2 = builder.Document.Styles.Add(StyleType.Paragraph, "Quote1");
builder.ParagraphFormat.Style = quoteLevel2;
builder.Document.Styles["Quote1"].BaseStyleName = "Quote";
builder.Writeln("1. Nested blockquote");
```

Tento fragment kódu vytvoří nový styl nazvaný „Citace1“, nastaví jeho základní styl na „Citace“ a zapíše vnořenou blokovou citaci. Nyní máte ve svém dokumentu vnořenou nabídku!

## Závěr

A tady to máte! Právě jste vytvořili dokument aplikace Word s uvozovkami a vnořenými blokovými uvozovkami pomocí Aspose.Words for .NET. Není to úžasné? Pomocí těchto jednoduchých kroků můžete nyní svým dokumentům dodat nádech elegance pomocí krásně formátovaných uvozovek. Pamatujte, že cvičení dělá mistra, takže pokračujte v experimentování a zdokonalujte své dovednosti.

## FAQ

### Co je Aspose.Words for .NET?

Aspose.Words for .NET je výkonná knihovna pro práci s dokumenty Wordu v aplikacích .NET. Umožňuje vytvářet, upravovat a převádět dokumenty aplikace Word programově.

### Mohu používat Aspose.Words pro .NET zdarma?

Aspose.Words for .NET můžete vyzkoušet zdarma s dočasnou licencí. Můžete to získat[zde](https://purchase.aspose.com/temporary-license/).

### Existuje podrobná dokumentace pro Aspose.Words pro .NET?

 Ano, můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).

### Jak získám podporu pro Aspose.Words for .NET?

 Pro podporu můžete navštívit fórum Aspose.Words[zde](https://forum.aspose.com/c/words/8).

### Kde si mohu stáhnout Aspose.Words pro .NET?

 Aspose.Words for .NET si můžete stáhnout z[zde](https://releases.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
