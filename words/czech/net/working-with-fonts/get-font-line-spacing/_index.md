---
title: Získejte řádkování písma
linktitle: Získejte řádkování písma
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak získat řádkování písma pomocí Aspose.Words for .NET, pomocí tohoto podrobného návodu. Ideální pro vývojáře.
weight: 10
url: /cs/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Získejte řádkování písma

## Zavedení

Aspose.Words for .NET je výkonná knihovna, která umožňuje programově vytvářet, manipulovat a převádět dokumenty aplikace Word. Jedním z běžných úkolů, které možná budete muset provést, je načtení řádkování konkrétního písma v dokumentu. V tomto tutoriálu vás provedeme procesem krok za krokem a zajistíme, že můžete snadno získat řádkování písma pomocí Aspose.Words for .NET. 

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte splněny následující předpoklady:

1.  Aspose.Words for .NET Library: Stáhněte a nainstalujte nejnovější verzi z[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte nastavené IDE jako Visual Studio.
3. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti o programování v C#.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory do vašeho projektu C#. Tyto jmenné prostory vám umožní přístup k funkcím Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Pojďme si rozdělit proces získávání řádkování písma do jednoduchých, zvládnutelných kroků.

## Krok 1: Vytvořte nový dokument

Prvním krokem je vytvoření nové instance dokumentu Word pomocí Aspose.Words for .NET.

```csharp
Document doc = new Document();
```

## Krok 2: Inicializujte DocumentBuilder

Dále musíme inicializovat`DocumentBuilder` objekt. Tento objekt nám pomůže vytvořit a manipulovat s obsahem dokumentu.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Nastavte vlastnosti písma

Nyní nastavíme vlastnosti písma pro text, který chceme vložit. Pro tento příklad použijeme font "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## Krok 4: Napište text do dokumentu

 Pomocí`DocumentBuilder` objekt, napište do dokumentu nějaký text. Tento text bude používat vlastnosti písma, které jsme nastavili v předchozím kroku.

```csharp
builder.Writeln("Sample Text");
```

## Krok 5: Načtěte objekt písma

Abychom získali řádkování, musíme získat přístup k objektu písma textu, který jsme právě přidali. To lze provést procházením struktury dokumentu na první běh odstavce.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Krok 6: Získejte řádkování

Nakonec načteme řádkování z objektu písma a vytiskneme jej do konzole.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Závěr

tady to máte! Získání řádkování písma pomocí Aspose.Words for .NET je jednoduché, když jej rozdělíte do těchto jednoduchých kroků. Ať už vytváříte nový dokument nebo pracujete se stávajícím, Aspose.Words poskytuje všechny nástroje, které potřebujete k efektivní správě vlastností písem.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty Wordu programově pomocí C#.

### Mohu používat Aspose.Words pro .NET v jiných jazycích .NET?
Ano, Aspose.Words pro .NET můžete používat s jakýmkoli jazykem .NET, včetně VB.NET a F#.

### Jak si mohu stáhnout Aspose.Words pro .NET?
 Nejnovější verzi Aspose.Words pro .NET si můžete stáhnout z[zde](https://releases.aspose.com/words/net/).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi od[zde](https://releases.aspose.com/).

### Kde najdu dokumentaci k Aspose.Words pro .NET?
 K dispozici je dokumentace pro Aspose.Words for .NET[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
