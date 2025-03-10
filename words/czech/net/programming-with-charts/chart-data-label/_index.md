---
title: Přizpůsobit štítek dat grafu
linktitle: Přizpůsobit štítek dat grafu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přizpůsobit štítky dat grafu pomocí Aspose.Words for .NET v podrobném průvodci. Ideální pro .NET vývojáře.
weight: 10
url: /cs/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přizpůsobit štítek dat grafu

## Zavedení

Chcete vylepšit své aplikace .NET dynamickými a přizpůsobenými možnostmi zpracování dokumentů? Aspose.Words pro .NET může být právě vaší odpovědí! V této příručce se ponoříme hluboko do přizpůsobení štítků dat grafu pomocí Aspose.Words for .NET, výkonné knihovny pro vytváření, úpravy a převod dokumentů aplikace Word. Ať už jste zkušený vývojář nebo teprve začínáte, tento tutoriál vás provede každým krokem a zajistí, že pochopíte, jak tento nástroj efektivně využívat.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Visual Studio: Nainstalujte Visual Studio 2019 nebo novější.
2. .NET Framework: Ujistěte se, že máte .NET Framework 4.0 nebo novější.
3.  Aspose.Words for .NET: Stáhněte si a nainstalujte Aspose.Words for .NET z[odkaz ke stažení](https://releases.aspose.com/words/net/).
4. Základní znalost C#: Znalost programování v C# je nezbytná.
5.  Platná licence: Získejte a[dočasná licence](https://purchase.aspose.com/temporary-license/) nebo koupit jeden od[koupit odkaz](https://purchase.aspose.com/buy).

## Importovat jmenné prostory

Chcete-li začít, musíte do projektu C# importovat potřebné jmenné prostory. Tento krok je zásadní, protože zajišťuje, že máte přístup ke všem třídám a metodám poskytovaným Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Krok 1: Inicializujte Document a DocumentBuilder

Abychom mohli vytvářet a manipulovat s dokumenty Wordu, musíme nejprve inicializovat instanci souboru`Document` třída a a`DocumentBuilder` objekt.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Vysvětlení

- Dokument dokumentu: Vytvoří novou instanci třídy Document.
- Tvůrce DocumentBuilder: Nástroj DocumentBuilder pomáhá při vkládání obsahu do objektu Document.

## Krok 2: Vložte graf

 Dále do dokumentu vložíme sloupcový graf pomocí`DocumentBuilder` objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Vysvětlení

- Tvar tvaru: Představuje graf jako tvar v dokumentu.
- builder.InsertChart(ChartType.Bar, 432, 252): Vloží sloupcový graf se zadanými rozměry.

## Krok 3: Přístup k řadě grafů

Chcete-li upravit štítky dat, musíme nejprve získat přístup k řadě v grafu.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Vysvětlení

- ChartSeries series0: Načte první řadu grafu, kterou přizpůsobíme.

## Krok 4: Přizpůsobte štítky dat

Datové štítky lze přizpůsobit tak, aby zobrazovaly různé informace. Nakonfigurujeme štítky tak, aby zobrazovaly klíč legendy, název série a hodnotu a zároveň skryly název kategorie a procento.

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

- Štítky ChartDataLabelCollection: Přistupuje k štítkům dat řady.
- labels.ShowLegendKey: Zobrazí klíč legendy.
- labels.ShowLeaderLines: Zobrazuje odkazové čáry pro datové štítky umístěné daleko mimo datové body.
- labels.ShowCategoryName: Skryje název kategorie.
- labels.ShowPercentage: Skryje procentuální hodnotu.
- labels.ShowSeriesName: Zobrazuje název série.
- labels.ShowValue: Zobrazuje hodnotu datových bodů.
- labels.Separator: Nastavuje oddělovač pro štítky dat.

## Krok 5: Uložte dokument

Nakonec dokument uložte do určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Vysvětlení

- doc.Save: Uloží dokument se zadaným názvem do poskytnutého adresáře.

## Závěr

 Gratuluji! Úspěšně jste přizpůsobili štítky dat grafu pomocí Aspose.Words pro .NET. Tato knihovna nabízí robustní řešení pro programovou manipulaci s dokumenty Word, což vývojářům usnadňuje vytváření sofistikovaných a dynamických aplikací pro zpracování dokumentů. Ponořte se do[dokumentace](https://reference.aspose.com/words/net/) prozkoumat další funkce a možnosti.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty aplikace Word programově.

### Jak nainstaluji Aspose.Words for .NET?
 Můžete si jej stáhnout a nainstalovat z[odkaz ke stažení](https://releases.aspose.com/words/net/). Postupujte podle dodaných pokynů k instalaci.

### Mohu vyzkoušet Aspose.Words pro .NET zdarma?
 Ano, můžete získat a[zkušební verze zdarma](https://releases.aspose.com/) nebo a[dočasná licence](https://purchase.aspose.com/temporary-license/)hodnotit produkt.

### Je Aspose.Words for .NET kompatibilní s .NET Core?
Ano, Aspose.Words for .NET je kompatibilní s .NET Core, .NET Standard a .NET Framework.

### Kde mohu získat podporu pro Aspose.Words pro .NET?
 Můžete navštívit[fórum podpory](https://forum.aspose.com/c/words/8) za pomoc a pomoc od komunity Aspose a odborníků.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
