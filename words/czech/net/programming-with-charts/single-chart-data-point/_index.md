---
"description": "Naučte se, jak přizpůsobit jednotlivé datové body grafu pomocí Aspose.Words pro .NET v podrobném návodu krok za krokem. Vylepšete své grafy jedinečnými značkami a velikostmi."
"linktitle": "Přizpůsobení jednoho datového bodu v grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přizpůsobení jednoho datového bodu v grafu"
"url": "/cs/net/programming-with-charts/single-chart-data-point/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přizpůsobení jednoho datového bodu v grafu

## Zavedení

Přemýšleli jste někdy, jak můžete zvýraznit své grafy jedinečnými datovými body? Dnes máte štěstí! Ponoříme se do úpravy jednoho datového bodu grafu pomocí Aspose.Words pro .NET. Připoutejte se a vydejte se na projížďku podrobným tutoriálem, který je nejen informativní, ale také zábavný a snadno srozumitelný.

## Předpoklady

Než začneme, ujistěte se, že máte všechny potřebné náležitosti:

- Knihovna Aspose.Words pro .NET: Ujistěte se, že máte nejnovější verzi. [Stáhněte si to zde](https://releases.aspose.com/words/net/).
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
- Základní znalost C#: Základní znalost programování v C# bude užitečná.
- Integrované vývojové prostředí (IDE): Doporučuje se Visual Studio.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory, abychom mohli začít:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

Dobře, začněme inicializací nového dokumentu a DocumentBuilderu. To bude plátno pro náš graf.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Zde, `dataDir` je cesta k adresáři, kam uložíte dokument. `DocumentBuilder` třída pomáhá s tvorbou dokumentu.

## Krok 2: Vložení grafu

Dále vložíme do dokumentu spojnicový graf. Bude to naše hřiště pro úpravu datových bodů.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

Ten/Ta/To `InsertChart` Metoda bere jako parametry typ grafu, šířku a výšku. V tomto případě vkládáme spojnicový graf o šířce 432 a výšce 252.

## Krok 3: Přístup k sérii grafů

Nyní je čas přistupovat k sériím v našem grafu. Graf může mít více sérií a každá série obsahuje datové body.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Zde přistupujeme k prvním dvěma sériím v našem grafu. 

## Krok 4: Úprava datových bodů

A tady se děje ta pravá magie! Pojďme si přizpůsobit konkrétní datové body v naší sérii.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Načítáme datové body z první série. Nyní si tyto body upravíme.

### Přizpůsobení datového bodu 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

Pro `dataPoint00`, nastavujeme explozi (užitečné pro koláčové grafy), měníme symbol značky na kruh a nastavujeme velikost značky na 15.

### Přizpůsobení datového bodu 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

Pro `dataPoint01`, měníme symbol značky na diamant a nastavujeme velikost značky na 20.

### Přizpůsobení datového bodu v sérii 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

Pro třetí datový bod v `series1`, nastavíme invertování, pokud je hodnota záporná, změníme symbol značky na hvězdičku a nastavíme velikost značky na 20.

## Krok 5: Uložte dokument

Nakonec uložte náš dokument se všemi úpravami.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

Tento řádek uloží dokument do vámi zadaného adresáře s názvem `WorkingWithCharts.SingleChartDataPoint.docx`.

## Závěr

tady to máte! Úspěšně jste si upravili jednotlivé datové body v grafu pomocí Aspose.Words pro .NET. Úpravou několika vlastností můžete své grafy učinit mnohem informativnějšími a vizuálně atraktivnějšími. Takže se do toho pusťte a experimentujte s různými značkami a velikostmi, abyste zjistili, co pro vaše data funguje nejlépe.

## Často kladené otázky

### Mohu si přizpůsobit datové body v jiných typech grafů?

Rozhodně! Datové body si můžete přizpůsobit v různých typech grafů, včetně sloupcových grafů, koláčových grafů a dalších. Postup je u všech typů grafů podobný.

### Je možné přidat k datovým bodům vlastní popisky?

Ano, k datovým bodům můžete přidat vlastní popisky pomocí `ChartDataPoint.Label` vlastnost. To vám umožňuje poskytnout více kontextu pro každý datový bod.

### Jak mohu odstranit datový bod z řady?

Datový bod můžete odstranit nastavením jeho viditelnosti na hodnotu false pomocí `dataPoint.IsVisible = false`.

### Mohu použít obrázky jako značky pro datové body?

když Aspose.Words nepodporuje přímé použití obrázků jako značek, můžete si vytvořit vlastní tvary a použít je jako značky.

### Je možné animovat datové body v grafu?

Aspose.Words pro .NET nepodporuje animace datových bodů grafů. Animované grafy však můžete vytvářet pomocí jiných nástrojů a vkládat je do dokumentů Wordu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}