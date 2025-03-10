---
title: Přizpůsobte jeden datový bod grafu v grafu
linktitle: Přizpůsobte jeden datový bod grafu v grafu
second_title: Aspose.Words API pro zpracování dokumentů
description: V podrobném podrobném průvodci se dozvíte, jak upravit jednotlivé datové body grafu pomocí Aspose.Words for .NET. Vylepšete své grafy jedinečnými značkami a velikostmi.
weight: 10
url: /cs/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přizpůsobte jeden datový bod grafu v grafu

## Zavedení

Přemýšleli jste někdy nad tím, jak můžete nechat své grafy vyskakovat pomocí jedinečných datových bodů? No, dnes je váš šťastný den! Ponoříme se do přizpůsobení jednoho datového bodu grafu pomocí Aspose.Words pro .NET. Připoutejte se na projížďku pomocí podrobného tutoriálu, který je nejen informativní, ale také zábavný a snadno sledovatelný.

## Předpoklady

Než začneme, ujistěte se, že máte všechny náležitosti na svém místě:

-  Aspose.Words for .NET Library: Ujistěte se, že máte nejnovější verzi.[Stáhněte si jej zde](https://releases.aspose.com/words/net/).
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
- Základní porozumění C#: Základní znalost programování C# bude užitečná.
- Integrované vývojové prostředí (IDE): Doporučuje se Visual Studio.

## Importovat jmenné prostory

Nejprve naimportujme potřebné jmenné prostory, abychom se rozběhli:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Inicializujte Document a DocumentBuilder

Dobře, začněme tím, že inicializujeme nový dokument a DocumentBuilder. Toto bude plátno pro náš graf.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde,`dataDir` je cesta k adresáři, kam uložíte dokument. The`DocumentBuilder` class pomáhá při vytváření dokumentu.

## Krok 2: Vložte graf

Dále vložíme do dokumentu spojnicový graf. Toto bude naše hřiště pro přizpůsobení datových bodů.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 The`InsertChart` metoda bere jako parametry typ grafu, šířku a výšku. V tomto případě vkládáme spojnicový graf o šířce 432 a výšce 252.

## Krok 3: Přístup k řadě grafů

Nyní je čas na přístup k sérii v našem grafu. Graf může mít více řad a každá řada obsahuje datové body.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Zde se dostáváme k prvním dvěma sériím v našem grafu. 

## Krok 4: Přizpůsobte datové body

Tady se děje kouzlo! Pojďme si přizpůsobit konkrétní datové body v rámci naší řady.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Načítáme datové body z první série. Nyní přizpůsobíme tyto body.

### Přizpůsobit datový bod 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Pro`dataPoint00`, nastavujeme explozi (užitečné pro koláčové grafy), měníme symbol značky na kruh a nastavujeme velikost značky na 15.

### Přizpůsobit datový bod 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Pro`dataPoint01`, změníme symbol značky na diamant a nastavíme velikost značky na 20.

### Přizpůsobte datový bod v sérii 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 Pro třetí datový bod v`series1`, nastavíme jej na invertování, pokud je hodnota záporná, změníme symbol značky na hvězdičku a nastavíme velikost značky na 20.

## Krok 5: Uložte dokument

Nakonec uložme náš dokument se všemi úpravami.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Tento řádek uloží dokument do vámi zadaného adresáře s názvem`WorkingWithCharts.SingleChartDataPoint.docx`.

## Závěr

tady to máte! Úspěšně jste přizpůsobili jednotlivé datové body v grafu pomocí Aspose.Words for .NET. Vyladěním několika vlastností můžete své grafy učinit mnohem informativnějšími a vizuálně přitažlivějšími. Takže pokračujte a experimentujte s různými značkami a velikostmi, abyste zjistili, co nejlépe vyhovuje vašim datům.

## FAQ

### Mohu přizpůsobit datové body v jiných typech grafů?

Absolutně! Datové body v různých typech grafů, včetně sloupcových grafů, koláčových grafů a dalších, můžete přizpůsobit. Proces je u různých typů grafů podobný.

### Je možné k datovým bodům přidat vlastní štítky?

 Ano, k datovým bodům můžete přidat vlastní štítky pomocí`ChartDataPoint.Label` vlastnictví. To vám umožní poskytnout více kontextu pro každý datový bod.

### Jak mohu odstranit datový bod ze série?

 Datový bod můžete odstranit nastavením jeho viditelnosti na hodnotu false using`dataPoint.IsVisible = false`.

### Mohu použít obrázky jako značky pro datové body?

Přestože Aspose.Words nepodporuje použití obrázků přímo jako značek, můžete vytvořit vlastní tvary a použít je jako značky.

### Je možné animovat datové body v grafu?

Aspose.Words for .NET nepodporuje animaci pro datové body grafu. Můžete však vytvářet animované grafy pomocí jiných nástrojů a vkládat je do dokumentů aplikace Word.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
