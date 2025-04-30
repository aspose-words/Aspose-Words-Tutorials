---
"description": "Naučte se, jak skrýt osu grafu v dokumentu Word pomocí Aspose.Words pro .NET v našem podrobném návodu krok za krokem."
"linktitle": "Skrýt osu grafu v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Skrýt osu grafu v dokumentu Word"
"url": "/cs/net/programming-with-charts/hide-chart-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skrýt osu grafu v dokumentu Word

## Zavedení

Vytváření dynamických a vizuálně atraktivních dokumentů Word často zahrnuje začlenění grafů a tabulek. Jeden takový scénář může vyžadovat skrytí osy grafu pro přehlednější prezentaci. Aspose.Words pro .NET poskytuje komplexní a snadno použitelné API pro takové úkoly. Tento tutoriál vás provede kroky, jak skrýt osu grafu v dokumentu Word pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíme do tutoriálu, ujistěte se, že máte následující předpoklady:

- Aspose.Words pro .NET: Můžete si jej stáhnout z [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli IDE, které podporuje vývoj v .NET, například Visual Studio.
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
- Základní znalost C#: Znalost programovacího jazyka C# bude výhodou.

## Importovat jmenné prostory

Abyste mohli začít pracovat s Aspose.Words pro .NET, musíte do projektu importovat požadované jmenné prostory. Zde je návod, jak to udělat:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Rozdělme si proces na jednoduché a snadno sledovatelné kroky.

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

Prvním krokem je vytvoření nového dokumentu Word a inicializace objektu DocumentBuilder.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

V tomto kroku definujeme cestu, kam bude dokument uložen. Poté vytvoříme novou `Document` objekt a `DocumentBuilder` objekt pro zahájení tvorby našeho dokumentu.

## Krok 2: Vložení grafu

Dále vložíme do dokumentu graf pomocí `DocumentBuilder` objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

Zde vložíme sloupcový graf se zadanými rozměry. `InsertChart` metoda vrací `Shape` objekt, který obsahuje graf.

## Krok 3: Vymazat existující sérii

Než do grafu přidáme nová data, musíme vymazat všechny existující řady.

```csharp
chart.Series.Clear();
```

Tento krok zajistí, že veškerá výchozí data v grafu budou odstraněna a uvolní místo pro nová data, která přidáme dále.

## Krok 4: Přidání dat série

Nyní si do grafu přidejme vlastní datovou řadu.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

tomto kroku přidáme sérii s názvem „Aspose Series 1“ s odpovídajícími kategoriemi a hodnotami.

## Krok 5: Skrytí osy Y

Chcete-li skrýt osu Y grafu, jednoduše nastavíme `Hidden` vlastnost osy Y k `true`.

```csharp
chart.AxisY.Hidden = true;
```

Tento řádek kódu skryje osu Y, takže je v grafu neviditelná.

## Krok 6: Uložte dokument

Nakonec uložte dokument do zadaného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Tento příkaz uloží dokument aplikace Word s grafem do zadané cesty.

## Závěr

Gratulujeme! Úspěšně jste se naučili, jak skrýt osu grafu v dokumentu Word pomocí knihovny Aspose.Words pro .NET. Tato výkonná knihovna usnadňuje programovou manipulaci s dokumenty Word. Dodržováním těchto kroků můžete s minimálním úsilím vytvářet přizpůsobené a profesionálně vypadající dokumenty.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonné API pro vytváření, úpravy, převod a manipulaci s dokumenty Word v aplikacích .NET.

### Mohu v grafu skrýt osy X i Y?
Ano, obě osy můžete skrýt nastavením `Hidden` majetek obou `AxisX` a `AxisY` na `true`.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Kde najdu další dokumentaci?
Podrobnou dokumentaci k Aspose.Words pro .NET naleznete na stránce [zde](https://reference.aspose.com/words/net/).

### Jak mohu získat podporu pro Aspose.Words pro .NET?
Podporu můžete získat od komunity Aspose [zde](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}