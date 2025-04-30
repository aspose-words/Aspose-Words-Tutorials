---
"description": "Naučte se porovnávat granularitu v dokumentech Word v Aspose.Words pro .NET, která umožňuje porovnávat dokumenty znak po znaku a hlásit provedené změny."
"linktitle": "Porovnání granularity v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Porovnání granularity v dokumentu Word"
"url": "/cs/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Porovnání granularity v dokumentu Word

Zde je podrobný návod, který vysvětluje zdrojový kód C# níže, jenž využívá funkci porovnání granularity v dokumentu Word v Aspose.Words pro .NET.

## Krok 1: Úvod

Funkce Porovnání granularity v Aspose.Words pro .NET umožňuje porovnávat dokumenty na úrovni znaků. To znamená, že každý znak bude porovnán a změny budou odpovídajícím způsobem nahlášeny.

## Krok 2: Nastavení prostředí

Než začnete, je třeba nastavit vývojové prostředí pro práci s Aspose.Words pro .NET. Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words a vhodný projekt v jazyce C# pro vložení kódu.

## Krok 3: Přidání požadovaných sestav

Chcete-li používat funkci Porovnání granularity v Aspose.Words pro .NET, musíte do projektu přidat potřebné sestavy. Ujistěte se, že máte v projektu správné odkazy na Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Krok 4: Vytvoření dokumentů

tomto kroku vytvoříme dva dokumenty pomocí třídy DocumentBuilder. Tyto dokumenty budou použity pro porovnání.

```csharp
// Vytvořte dokument A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Vytvořte dokument B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Krok 5: Konfigurace možností porovnání

V tomto kroku nakonfigurujeme možnosti porovnání a určíme granularitu porovnání. Zde použijeme granularitu na úrovni znaků.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Krok 6: Porovnání dokumentů

Nyní porovnejme dokumenty pomocí metody Compare třídy Document. Změny se uloží do dokumentu A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

Ten/Ta/To `Compare` Metoda porovná dokument A s dokumentem B a uloží změny do dokumentu A. Pro referenci můžete zadat jméno autora a datum porovnání.

## Závěr

V tomto článku jsme prozkoumali funkci Porovnání granularity v Aspose.Words pro .NET. Tato funkce umožňuje porovnávat dokumenty na úrovni znaků a hlásit změny. Tyto znalosti můžete využít k provádění podrobného porovnávání dokumentů ve vašich projektech.

### Ukázkový zdrojový kód pro porovnání granularity pomocí Aspose.Words pro .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Závěr

V tomto tutoriálu jsme prozkoumali funkci granularity porovnání v Aspose.Words pro .NET. Tato funkce umožňuje určit úroveň detailů při porovnávání dokumentů. Výběrem různých úrovní granularity můžete provádět detailní porovnání na úrovni znaků, slov nebo bloků v závislosti na vašich specifických požadavcích. Aspose.Words pro .NET poskytuje flexibilní a výkonnou funkci porovnávání dokumentů, která usnadňuje identifikaci rozdílů v dokumentech s různou úrovní granularity.

### Často kladené otázky

#### Otázka: Jaký je účel použití granularity porovnání v Aspose.Words pro .NET?

A: Granularita porovnání v Aspose.Words pro .NET umožňuje určit úroveň detailů při porovnávání dokumentů. Díky této funkci můžete porovnávat dokumenty na různých úrovních, například na úrovni znaků, slov nebo dokonce bloků. Každá úroveň granularity poskytuje jinou úroveň detailů ve výsledcích porovnání.

#### Otázka: Jak mohu v Aspose.Words pro .NET použít granularitu porovnání?

A: Chcete-li v Aspose.Words pro .NET použít funkci Comparison Granularity, postupujte takto:
1. Nastavte si vývojové prostředí pomocí knihovny Aspose.Words.
2. Přidejte do projektu potřebné sestavy odkazem na Aspose.Words.
3. Vytvořte dokumenty, které chcete porovnat, pomocí `DocumentBuilder` třída.
4. Nakonfigurujte možnosti porovnání vytvořením `CompareOptions` objekt a nastavení `Granularity` vlastnost na požadovanou úroveň (např. `Granularity.CharLevel` pro porovnání na úrovni znaků).
5. Použijte `Compare` metodu na jednom dokumentu, předání druhého dokumentu a `CompareOptions` objekt jako parametry. Tato metoda porovná dokumenty na základě zadané granularity a uloží změny do prvního dokumentu.

#### Otázka: Jaké jsou dostupné úrovně granularity porovnání v Aspose.Words pro .NET?

A: Aspose.Words pro .NET nabízí tři úrovně granularity porovnání:
- `Granularity.CharLevel`Porovnává dokumenty na úrovni znaků.
- `Granularity.WordLevel`Porovnává dokumenty na úrovni slov.
- `Granularity.BlockLevel`Porovnává dokumenty na úrovni bloků.

#### Otázka: Jak mohu interpretovat výsledky porovnání s granularitou na úrovni znaků?

A: Při granularitě na úrovni znaků se u každého znaku v porovnávaných dokumentech analyzuje rozdíl. Výsledky porovnání ukážou změny na úrovni jednotlivých znaků, včetně přidání, odstranění a úprav.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}