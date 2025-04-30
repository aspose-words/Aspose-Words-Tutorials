---
"description": "Naučte se, jak získat řádkování písma pomocí Aspose.Words pro .NET v tomto podrobném návodu. Ideální pro vývojáře."
"linktitle": "Získat řádkování písma"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Získat řádkování písma"
"url": "/cs/net/working-with-fonts/get-font-line-spacing/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Získat řádkování písma

## Zavedení

Aspose.Words pro .NET je výkonná knihovna, která umožňuje programově vytvářet, manipulovat a převádět dokumenty Wordu. Jedním z běžných úkolů, které můžete potřebovat provést, je načtení řádkování konkrétního písma v dokumentu. V tomto tutoriálu vás krok za krokem provedeme tímto procesem a zajistíme, abyste řádkování písma snadno získali pomocí Aspose.Words pro .NET. 

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte splněny následující předpoklady:

1. Knihovna Aspose.Words pro .NET: Stáhněte a nainstalujte nejnovější verzi z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte nastavené IDE, jako je Visual Studio.
3. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti programování v C#.

## Importovat jmenné prostory

Nejprve je třeba do projektu v C# importovat potřebné jmenné prostory. Tyto jmenné prostory vám umožní přístup k funkcím Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Pojďme si rozebrat proces nastavení řádkování písma do jednoduchých a snadno zvládnutelných kroků.

## Krok 1: Vytvořte nový dokument

Prvním krokem je vytvoření nové instance dokumentu Word pomocí Aspose.Words pro .NET.

```csharp
Document doc = new Document();
```

## Krok 2: Inicializace nástroje DocumentBuilder

Dále musíme inicializovat `DocumentBuilder` objekt. Tento objekt nám pomůže konstruovat a manipulovat s obsahem dokumentu.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Nastavení vlastností písma

Nyní nastavíme vlastnosti písma pro text, který chceme vložit. V tomto příkladu použijeme písmo „Calibri“.

```csharp
builder.Font.Name = "Calibri";
```

## Krok 4: Napište text do dokumentu

Použití `DocumentBuilder` objektu, napište do dokumentu nějaký text. Tento text použije vlastnosti písma, které jsme nastavili v předchozím kroku.

```csharp
builder.Writeln("Sample Text");
```

## Krok 5: Načtení objektu písma

Abychom získali řádkování, potřebujeme přistupovat k objektu písma textu, který jsme právě přidali. Toho lze dosáhnout procházením struktury dokumentu až k prvnímu odstavci.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Krok 6: Získejte řádkování

Nakonec z objektu font načteme řádkování a vypíšeme ho do konzole.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Závěr

A tady to máte! Načtení řádkování písma pomocí Aspose.Words pro .NET je jednoduché, když si ho rozdělíte do těchto jednoduchých kroků. Ať už vytváříte nový dokument nebo pracujete s existujícím, Aspose.Words poskytuje všechny nástroje, které potřebujete k efektivní správě vlastností písma.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, manipulovat a převádět dokumenty Wordu pomocí C#.

### Mohu používat Aspose.Words pro .NET v jiných jazycích .NET?
Ano, Aspose.Words pro .NET můžete použít s jakýmkoli jazykem .NET, včetně VB.NET a F#.

### Jak si mohu stáhnout Aspose.Words pro .NET?
Nejnovější verzi Aspose.Words pro .NET si můžete stáhnout z [zde](https://releases.aspose.com/words/net/).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete získat bezplatnou zkušební verzi od [zde](https://releases.aspose.com/).

### Kde najdu dokumentaci k Aspose.Words pro .NET?
Dokumentace k Aspose.Words pro .NET je k dispozici. [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}