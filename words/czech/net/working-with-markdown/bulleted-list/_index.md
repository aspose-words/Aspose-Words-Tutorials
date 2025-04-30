---
"description": "Naučte se, jak vytvářet a upravovat odrážkové seznamy v dokumentech Wordu pomocí Aspose.Words pro .NET s tímto podrobným návodem."
"linktitle": "Seznam s odrážkami"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Seznam s odrážkami"
"url": "/cs/net/working-with-markdown/bulleted-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Seznam s odrážkami

## Zavedení

Jste připraveni ponořit se do světa Aspose.Words pro .NET? Dnes si ukážeme, jak vytvořit seznam s odrážkami ve vašich dokumentech Word. Ať už organizujete nápady, vyjmenováváte položky nebo jen přidáváte do dokumentu trochu struktury, seznamy s odrážkami jsou velmi praktické. Tak pojďme na to!

## Předpoklady

Než se pustíme do samotného programování, ujistěte se, že máte vše potřebné:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ji ještě nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí AC#, jako je Visual Studio.
3. Základní znalost C#: Základní znalost programování v C# vám pomůže se v daném textu orientovat.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Je to jako připravit půdu pro hladký chod našeho kódu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Nyní si celý proces rozdělme na jednoduché a zvládnutelné kroky.

## Krok 1: Vytvořte nový dokument

Dobře, začněme vytvořením nového dokumentu. Tady se začne dít všechna ta magie.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Použití formátu seznamu s odrážkami

Dále použijeme formát seznamu s odrážkami. Tím dokumentu sdělíme, že se chystáme začít s odrážkovým seznamem.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Krok 3: Přizpůsobení seznamu s odrážkami

Zde si přizpůsobíme seznam s odrážkami podle svých představ. V tomto příkladu použijeme jako odrážku pomlčku (-).

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Krok 4: Přidání položek seznamu

Nyní přidejme do našeho seznamu s odrážkami několik položek. Zde můžete být kreativní a přidat jakýkoli potřebný obsah.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Krok 5: Přidání podpoložek

Aby to bylo zajímavější, přidejme pod „Položku 2“ několik podpoložek. To pomůže s organizací podpoložek.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Návrat na hlavní úroveň seznamu
```

## Závěr

A tady to máte! Právě jste vytvořili seznam s odrážkami v dokumentu Wordu pomocí Aspose.Words pro .NET. Je to jednoduchý proces, ale neuvěřitelně výkonný pro organizaci dokumentů. Ať už vytváříte jednoduché seznamy nebo složité vnořené seznamy, Aspose.Words vám pomůže.

Nebojte se experimentovat s různými styly a formáty seznamů podle svých potřeb. Šťastné programování!

## Často kladené otázky

### Mohu v seznamu použít různé symboly odrážek?
   Ano, symboly odrážek si můžete přizpůsobit změnou `NumberFormat` vlastnictví.

### Jak přidám další úrovně odsazení?
   Použijte `ListIndent` metoda pro přidání dalších úrovní a `ListOutdent` aby se vrátili na vyšší úroveň.

### Je možné kombinovat seznamy s odrážkami a číselné seznamy?
   Rozhodně! Mezi formáty odrážek a čísel můžete přepínat pomocí `ApplyNumberDefault` a `ApplyBulletDefault` metody.

### Mohu stylizovat text v položkách seznamu?
   Ano, na text v položkách seznamu můžete použít různé styly, písma a formátování pomocí `Font` majetek `DocumentBuilder`.

### Jak mohu vytvořit seznam s odrážkami s více sloupci?
   Formátování tabulky můžete použít k vytvoření seznamů s více sloupci, kde každá buňka obsahuje samostatný seznam s odrážkami.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}