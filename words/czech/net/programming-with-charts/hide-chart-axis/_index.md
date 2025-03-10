---
title: Skrýt osu grafu v dokumentu aplikace Word
linktitle: Skrýt osu grafu v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak skrýt osu grafu v dokumentu aplikace Word pomocí Aspose.Words for .NET, pomocí našeho podrobného výukového programu krok za krokem.
weight: 10
url: /cs/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skrýt osu grafu v dokumentu aplikace Word

## Zavedení

Vytváření dynamických a vizuálně přitažlivých dokumentů aplikace Word často zahrnuje začlenění tabulek a grafů. Jeden takový scénář může vyžadovat skrytí osy grafu pro čistší prezentaci. Aspose.Words for .NET poskytuje komplexní a snadno použitelné API pro takové úkoly. Tento výukový program vás provede kroky ke skrytí osy grafu v dokumentu aplikace Word pomocí Aspose.Words for .NET.

## Předpoklady

Než se pustíme do výukového programu, ujistěte se, že máte následující předpoklady:

-  Aspose.Words for .NET: Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli IDE, které podporuje vývoj .NET, jako je Visual Studio.
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
- Základní znalost C#: Výhodou bude znalost programovacího jazyka C#.

## Importovat jmenné prostory

Chcete-li začít pracovat s Aspose.Words for .NET, musíte do projektu importovat požadované jmenné prostory. Můžete to udělat takto:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Pojďme si tento proces rozdělit do jednoduchých, snadno pochopitelných kroků.

## Krok 1: Inicializujte Document a DocumentBuilder

První krok zahrnuje vytvoření nového dokumentu aplikace Word a inicializaci objektu DocumentBuilder.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 V tomto kroku definujeme cestu, kam bude dokument uložen. Poté vytvoříme nový`Document` objekt a a`DocumentBuilder` začněte budovat náš dokument.

## Krok 2: Vložte graf

 Dále vložíme do dokumentu graf pomocí`DocumentBuilder` objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Zde vložíme sloupcový graf se zadanými rozměry. The`InsertChart` metoda vrací a`Shape` objekt, který obsahuje graf.

## Krok 3: Vymažte existující sérii

Před přidáním nových dat do grafu musíme vymazat všechny existující řady.

```csharp
chart.Series.Clear();
```

Tento krok zajistí, že všechna výchozí data z grafu budou odstraněna, čímž se uvolní místo pro nová data, která přidáme jako další.

## Krok 4: Přidejte data série

Nyní do grafu přidáme vlastní datovou řadu.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

V tomto kroku přidáme řadu s názvem „Aspose Series 1“ s odpovídajícími kategoriemi a hodnotami.

## Krok 5: Skryjte osu Y

 Chcete-li skrýt osu Y grafu, jednoduše nastavíme`Hidden` vlastnost osy Y k`true`.

```csharp
chart.AxisY.Hidden = true;
```

Tento řádek kódu skrývá osu Y, takže je v grafu neviditelná.

## Krok 6: Uložte dokument

Nakonec dokument uložte do určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Tento příkaz uloží dokument aplikace Word s grafem do zadané cesty.

## Závěr

Gratuluji! Úspěšně jste se naučili, jak skrýt osu grafu v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná knihovna usnadňuje programovou manipulaci s dokumenty Wordu. Podle těchto kroků můžete s minimálním úsilím vytvářet přizpůsobené a profesionálně vypadající dokumenty.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonné API pro vytváření, úpravy, konverzi a manipulaci s dokumenty Wordu v aplikacích .NET.

### Mohu skrýt obě osy X a Y v grafu?
 Ano, můžete skrýt obě osy nastavením`Hidden` majetek obou`AxisX` a`AxisY` na`true`.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Kde najdu další dokumentaci?
 Podrobnou dokumentaci najdete na Aspose.Words pro .NET[zde](https://reference.aspose.com/words/net/).

### Jak mohu získat podporu pro Aspose.Words pro .NET?
 Můžete získat podporu od komunity Aspose[zde](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
