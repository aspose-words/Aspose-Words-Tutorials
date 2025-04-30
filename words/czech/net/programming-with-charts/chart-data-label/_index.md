---
"description": "Naučte se, jak přizpůsobit popisky dat grafů pomocí Aspose.Words pro .NET v podrobném návodu. Ideální pro vývojáře .NET."
"linktitle": "Přizpůsobení popisku dat grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přizpůsobení popisku dat grafu"
"url": "/cs/net/programming-with-charts/chart-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přizpůsobení popisku dat grafu

## Zavedení

Hledáte způsob, jak vylepšit své .NET aplikace dynamickými a přizpůsobitelnými funkcemi pro zpracování dokumentů? Aspose.Words pro .NET by mohla být přesně ta správná odpověď! V této příručce se podrobně ponoříme do úpravy popisků dat grafů pomocí Aspose.Words pro .NET, výkonné knihovny pro vytváření, úpravy a převod dokumentů Word. Ať už jste zkušený vývojář, nebo teprve začínáte, tento tutoriál vás provede každým krokem a zajistí, že pochopíte, jak tento nástroj efektivně používat.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Visual Studio: Nainstalujte Visual Studio 2019 nebo novější.
2. .NET Framework: Ujistěte se, že máte .NET Framework 4.0 nebo novější.
3. Aspose.Words pro .NET: Stáhněte a nainstalujte Aspose.Words pro .NET z [odkaz ke stažení](https://releases.aspose.com/words/net/).
4. Základní znalost C#: Znalost programování v C# je nezbytná.
5. Platný řidičský průkaz: Získejte [dočasná licence](https://purchase.aspose.com/temporary-license/) nebo si jeden zakoupit od [koupit odkaz](https://purchase.aspose.com/buy).

## Importovat jmenné prostory

Chcete-li začít, musíte do svého projektu v C# importovat potřebné jmenné prostory. Tento krok je klíčový, protože vám zajistí přístup ke všem třídám a metodám poskytovaným Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

Abychom mohli vytvářet a manipulovat s dokumenty Wordu, musíme nejprve inicializovat instanci třídy `Document` třída a `DocumentBuilder` objekt.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Vysvětlení

- Dokument doc: Vytvoří novou instanci třídy Document.
- Tvůrce DocumentBuilder: Tvůrce DocumentBuilder pomáhá s vkládáním obsahu do objektu Document.

## Krok 2: Vložení grafu

Dále vložíme do dokumentu sloupcový graf pomocí `DocumentBuilder` objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Vysvětlení

- Tvar tvaru: Představuje graf jako tvar v dokumentu.
- builder.InsertChart(ChartType.Bar, 432, 252): Vloží sloupcový graf se zadanými rozměry.

## Krok 3: Přístup k sérii grafů

Pro přizpůsobení popisků dat potřebujeme nejprve přístup k řadě v grafu.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Vysvětlení

- ChartSeries series0: Načte první sérii grafu, kterou upravíme.

## Krok 4: Úprava popisků dat

Popisky dat lze přizpůsobit tak, aby zobrazovaly různé informace. Nakonfigurujeme je tak, aby zobrazovaly legendu, název řady a hodnotu, zatímco název kategorie a procento budou skryté.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Vysvětlení

- Popisky kolekce ChartDataLabelCollection: Přistupuje k popiskům dat v řadě.
- labels.ShowLegendKey: Zobrazí klíč legendy.
- labels.ShowLeaderLines: Zobrazuje vodicí čáry pro datové popisky umístěné daleko vně datových bodů.
- labels.ShowCategoryName: Skryje název kategorie.
- labels.ShowPercentage: Skryje procentuální hodnotu.
- labels.ShowSeriesName: Zobrazí název série.
- labels.ShowValue: Zobrazí hodnotu datových bodů.
- labels.Separator: Nastaví oddělovač pro popisky dat.

## Krok 5: Uložte dokument

Nakonec uložte dokument do zadaného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Vysvětlení

- doc.Save: Uloží dokument se zadaným názvem do zadaného adresáře.

## Závěr

Gratulujeme! Úspěšně jste upravili popisky dat grafu pomocí knihovny Aspose.Words pro .NET. Tato knihovna nabízí robustní řešení pro programovou práci s dokumenty Word, což vývojářům usnadňuje vytváření sofistikovaných a dynamických aplikací pro zpracování dokumentů. Ponořte se do… [dokumentace](https://reference.aspose.com/words/net/) prozkoumat další funkce a možnosti.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům programově vytvářet, upravovat a převádět dokumenty Wordu.

### Jak nainstaluji Aspose.Words pro .NET?
Můžete si jej stáhnout a nainstalovat z [odkaz ke stažení](https://releases.aspose.com/words/net/)Řiďte se přiloženými pokyny k instalaci.

### Mohu si Aspose.Words pro .NET vyzkoušet zdarma?
Ano, můžete získat [bezplatná zkušební verze](https://releases.aspose.com/) nebo a [dočasná licence](https://purchase.aspose.com/temporary-license/) k vyhodnocení produktu.

### Je Aspose.Words pro .NET kompatibilní s .NET Core?
Ano, Aspose.Words pro .NET je kompatibilní s .NET Core, .NET Standard a .NET Framework.

### Kde mohu získat podporu pro Aspose.Words pro .NET?
Můžete navštívit [fórum podpory](https://forum.aspose.com/c/words/8) za pomoc a podporu od komunity a odborníků Aspose.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}