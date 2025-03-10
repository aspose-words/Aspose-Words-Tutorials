---
title: Srovnání zrnitosti V dokumentu Word
linktitle: Srovnání zrnitosti V dokumentu Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se Porovnat granularitu ve funkci dokumentu Word aplikace Aspose.Words for .NET, která umožňuje porovnávat dokumenty znak po znaku a hlásit provedené změny.
weight: 10
url: /cs/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Srovnání zrnitosti V dokumentu Word

Zde je podrobný průvodce vysvětlující zdrojový kód C# níže, který používá funkci Porovnat granularitu ve wordovém dokumentu Aspose.Words pro .NET.

## Krok 1: Úvod

Funkce Porovnat zrnitost Aspose.Words pro .NET umožňuje porovnávat dokumenty na úrovni znaků. To znamená, že každý znak bude porovnán a změny budou podle toho hlášeny.

## Krok 2: Nastavení prostředí

Než začnete, musíte své vývojové prostředí nastavit tak, aby fungovalo s Aspose.Words for .NET. Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words a že máte vhodný projekt C# pro vložení kódu.

## Krok 3: Přidejte požadovaná sestavení

Chcete-li použít funkci Porovnat granularitu Aspose.Words pro .NET, musíte do projektu přidat potřebná sestavení. Ujistěte se, že máte ve svém projektu správné odkazy na Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Krok 4: Vytvoření dokumentů

V tomto kroku vytvoříme dva dokumenty pomocí třídy DocumentBuilder. Tyto dokumenty budou použity pro srovnání.

```csharp
// Vytvořte dokument A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Vytvořte dokument B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Krok 5: Konfigurace možností porovnání

V tomto kroku nakonfigurujeme možnosti porovnání, abychom určili granularitu porovnání. Zde použijeme granularitu na úrovni znaků.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Krok 6: Porovnání dokumentů

Nyní porovnejme dokumenty pomocí metody Compare třídy Document. Změny budou uloženy v dokumentu A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 The`Compare`metoda porovná dokument A s dokumentem B a uloží změny do dokumentu A. Pro referenci můžete zadat jméno autora a datum porovnání.

## Závěr

V tomto článku jsme prozkoumali funkci Porovnat granularitu Aspose.Words pro .NET. Tato funkce umožňuje porovnávat dokumenty na úrovni znaků a hlásit změny. Tyto znalosti můžete využít k podrobnému porovnávání dokumentů ve svých projektech.

### Ukázka zdrojového kódu pro Comparison Granularity pomocí Aspose.Words for .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Závěr

V tomto tutoriálu jsme prozkoumali funkci Comparison Granularity Aspose.Words for .NET. Tato funkce umožňuje určit úroveň podrobností při porovnávání dokumentů. Výběrem různých úrovní podrobnosti můžete provádět podrobná srovnání na úrovni znaků, slov nebo bloků v závislosti na vašich konkrétních požadavcích. Aspose.Words for .NET poskytuje flexibilní a výkonnou možnost porovnávání dokumentů, což usnadňuje identifikaci rozdílů v dokumentech s různou úrovní granularity.

### FAQ

#### Otázka: Jaký je účel použití funkce Comparison Granularity v Aspose.Words for .NET?

Odpověď: Porovnání granularity v Aspose.Words pro .NET vám umožňuje určit úroveň podrobností při porovnávání dokumentů. Pomocí této funkce můžete porovnávat dokumenty na různých úrovních, například na úrovni znaků, na úrovni slov nebo dokonce na úrovni bloku. Každá úroveň podrobnosti poskytuje ve výsledcích srovnání jinou úroveň podrobností.

#### Otázka: Jak mohu použít srovnávací granularitu v Aspose.Words pro .NET?

Odpověď: Chcete-li použít srovnávací granularitu v Aspose.Words pro .NET, postupujte takto:
1. Nastavte své vývojové prostředí pomocí knihovny Aspose.Words.
2. Přidejte potřebné sestavy do svého projektu odkazem na Aspose.Words.
3.  Vytvořte dokumenty, které chcete porovnat pomocí`DocumentBuilder` třída.
4.  Nakonfigurujte možnosti porovnání vytvořením a`CompareOptions` objekt a nastavení`Granularity` vlastnost na požadovanou úroveň (např.`Granularity.CharLevel` pro srovnání na úrovni postav).
5.  Použijte`Compare`metoda na jednom dokumentu, předání druhého dokumentu a`CompareOptions` objekt jako parametry. Tato metoda porovná dokumenty na základě zadané granularity a uloží změny v prvním dokumentu.

#### Otázka: Jaké jsou dostupné úrovně granularity porovnání v Aspose.Words pro .NET?

Odpověď: Aspose.Words for .NET poskytuje tři úrovně granularity srovnání:
- `Granularity.CharLevel`: Porovnává dokumenty na úrovni znaků.
- `Granularity.WordLevel`: Porovnává dokumenty na úrovni slov.
- `Granularity.BlockLevel`: Porovnává dokumenty na úrovni bloku.

#### Otázka: Jak mohu interpretovat výsledky srovnání s podrobností na úrovni znaků?

Odpověď: Díky granularitě na úrovni znaků je každý znak v porovnávaných dokumentech analyzován na rozdíly. Výsledky porovnání ukáží změny na úrovni jednotlivých postav, včetně přidání, odstranění a úprav.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
