---
title: Vložit bodový graf do dokumentu aplikace Word
linktitle: Vložit bodový graf do dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vložit bodový graf do aplikace Word pomocí Aspose.Words for .NET. Snadné kroky pro integraci reprezentací vizuálních dat do vašich dokumentů.
weight: 10
url: /cs/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit bodový graf do dokumentu aplikace Word

## Zavedení

V tomto tutoriálu se naučíte, jak využít Aspose.Words pro .NET k vložení bodového grafu do dokumentu aplikace Word. Bodové grafy jsou výkonné vizuální nástroje, které mohou efektivně zobrazovat datové body na základě dvou proměnných, díky čemuž jsou vaše dokumenty poutavější a informativnější.

## Předpoklady

Než se pustíme do vytváření bodových grafů pomocí Aspose.Words pro .NET, ujistěte se, že máte následující předpoklady:

1.  Instalace Aspose.Words pro .NET: Stáhněte a nainstalujte Aspose.Words pro .NET z[zde](https://releases.aspose.com/words/net/).
   
2. Základní znalost C#: Výhodou bude znalost programovacího jazyka C# a frameworku .NET.

## Importovat jmenné prostory

Chcete-li začít, musíte do svého projektu C# importovat potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Nyní si rozeberme proces vkládání bodového grafu do dokumentu aplikace Word pomocí Aspose.Words for .NET:

## Krok 1: Inicializujte Document a DocumentBuilder

 Nejprve inicializujte novou instanci souboru`Document` třída a`DocumentBuilder` třídy, abyste mohli začít vytvářet svůj dokument.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložte bodový graf

 Použijte`InsertChart` metoda`DocumentBuilder` třídy k vložení bodového grafu do dokumentu.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Krok 3: Přidejte datové řady do grafu

Nyní přidejte datové řady do bodového grafu. Tento příklad ukazuje přidání řady se specifickými datovými body.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Krok 4: Uložte dokument

 Nakonec uložte upravený dokument na požadované místo pomocí`Save` metoda`Document` třída.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Závěr

Gratuluji! Úspěšně jste se naučili, jak vložit bodový graf do dokumentu aplikace Word pomocí Aspose.Words for .NET. Bodové grafy jsou vynikajícími nástroji pro vizualizaci datových vztahů a pomocí Aspose.Words je můžete bez námahy integrovat do svých dokumentů a zlepšit tak přehlednost a porozumění.

## FAQ

### Mohu upravit vzhled bodového grafu pomocí Aspose.Words?
Ano, Aspose.Words umožňuje rozsáhlé přizpůsobení vlastností grafu, jako jsou barvy, osy a popisky.

### Je Aspose.Words kompatibilní s různými verzemi aplikace Microsoft Word?
Aspose.Words podporuje různé verze aplikace Microsoft Word a zajišťuje kompatibilitu napříč platformami.

### Poskytuje Aspose.Words podporu pro jiné typy grafů?
Ano, Aspose.Words podporuje širokou škálu typů grafů včetně sloupcových grafů, spojnicových grafů a koláčových grafů.

### Mohu dynamicky aktualizovat data v bodovém grafu programově?
Data grafu můžete aktualizovat dynamicky pomocí volání API Aspose.Words.

### Kde mohu získat další pomoc nebo podporu pro Aspose.Words?
 Pro další pomoc navštivte[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
