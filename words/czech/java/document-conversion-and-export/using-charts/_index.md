---
date: 2025-12-13
description: Naučte se, jak vytvořit sloupcový graf a formátovat popisky dat grafu
  pomocí Aspose.Words pro Javu. Prozkoumejte přidávání více sérií, změnu typu osy
  a skrytí osy grafu.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Jak vytvořit sloupcový graf pomocí Aspose.Words pro Javu
url: /cs/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java

V tomto tutoriálu **vytvoříte sloupcové grafy** přímo v dokumentech Word pomocí Aspose.Words pro Java. Provedeme vás tvorbou různých typů grafů, přidáváním více sérií, formátováním popisků dat v grafu, změnou typu osy a dokonce skrytím osy grafu, pokud potřebujete čistší vzhled. Na konci budete mít solidní, připravený přístup pro vkládání bohatých grafů do vašich dokumentů.

## Rychlé odpovědi
- **Jaká třída se primárně používá pro vytvoření grafu?** `DocumentBuilder` s metodou `insertChart`.
- **Která metoda přidává novou sérii?** `chart.getSeries().add(...)`.
- **Jak formátovat popisky dat v grafu?** Použijte `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Mohu skrýt osu?** Ano, zavolejte `setHidden(true)` na objekt osy.
- **Potřebuji licenci pro Aspose.Words?** Licence je vyžadována pro produkční použití; je k dispozici bezplatná zkušební verze.

## Co je sloupcový graf a proč jej použít?

Sloupcový graf zobrazuje kategorická data jako svislé pruhy, což ho činí ideálním pro porovnávání hodnot napříč skupinami (prodej podle regionu, měsíční výdaje atd.). V Java aplikacích umožňuje generování sloupcového grafu pomocí Aspose.Words vložit tyto vizualizace přímo do souborů Word / DOCX bez nutnosti Excelu nebo externích nástrojů.

## Jak vytvořit sloupcový graf

Níže je jednoduchý příklad, který vytvoří základní sloupcový graf. Kód je identický s původním úryvkem – přidali jsme jen vysvětlující komentáře, aby byl snazší na pochopení.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Přidání více sérií

Můžete **přidat více sérií** do sloupcového grafu opakovaným voláním `chart.getSeries().add(...)`, jak je ukázáno výše. Každá série může mít vlastní sadu kategorií a hodnot, což vám umožní porovnávat několik datových sad vedle sebe.

## Jak vytvořit čárový graf s vlastním popiskem dat

Pokud potřebujete místo sloupcového grafu čárový graf, platí stejný postup. Tento příklad také ukazuje **formátování popisků dat v grafu** s různými číselnými formáty.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Přidání popisků dat

Volání `series1.hasDataLabels(true)` **přidá popisky dat** k sérii, zatímco `setShowValue(true)` zobrazí skutečné hodnoty přímo v grafu.

## Jak změnit typ osy a přizpůsobit vlastnosti osy

Změna typu osy (např. z datumové na kategorickou) vám umožní řídit, jak jsou datové body vykresleny. Tento úryvek také ukazuje, jak **skrýt osu grafu**, pokud preferujete minimalistický design.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Změna typu osy

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **změní typ osy** z datumové na kategorickou, což vám dává plnou kontrolu nad umístěním popisků.

## Jak formátovat popisky dat v grafu (číselné formáty)

Můžete aplikovat číselné formátování přímo na osu nebo popisky dat. Tento příklad formátuje čísla na ose Y s oddělovačem tisíců.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Další úpravy grafu

Mimo základy můžete upravovat hranice, nastavit intervaly mezi popisky, skrýt konkrétní osy a další. Pro úplný seznam vlastností se podívejte do dokumentace API Aspose.Words pro Java.

## Často kladené otázky

**Q: Jak mohu přidat více sérií do grafu?**  
A: Použijte `chart.getSeries().add()` pro každou sérii, kterou chcete zobrazit. Každé volání může poskytnout jedinečný název, pole kategorií a pole hodnot.

**Q: Jak formátovat popisky dat v grafu s vlastním číselným formátem?**  
A: Získejte objekt `DataLabels` série a zavolejte `getNumberFormat().setFormatCode("váš formát")`. Můžete také propojit formát se zdrojovou buňkou pomocí `isLinkedToSource(true)`.

**Q: Jak mohu skrýt osu grafu?**  
A: Zavolejte `setHidden(true)` na objekt `ChartAxis`, který chcete skrýt (např. `chart.getAxisY().setHidden(true)`).

**Q: Jaký je nejlepší způsob, jak změnit typ osy?**  
A: Použijte `setCategoryType(AxisCategoryType.CATEGORY)` pro kategorické osy nebo `AxisCategoryType.DATE` pro datumové osy.

**Q: Jak přidat popisky dat k sérii?**  
A: Aktivujte je pomocí `series.hasDataLabels(true)` a poté nastavte viditelnost pomocí `series.getDataLabels().setShowValue(true)`.

## Závěr

Probrali jsme vše, co potřebujete k **vytvoření sloupcových grafů** pomocí Aspose.Words pro Java – od vložení základních grafů a přidání více sérií, přes formátování popisků dat, změnu typu osy, až po skrytí os grafu pro čistý vzhled. Začleňte tyto techniky do svých reportovacích nebo dokumentačních pipeline, abyste dodali profesionální, daty podložené Word dokumenty.

---

**Poslední aktualizace:** 2025-12-13  
**Testováno s:** Aspose.Words pro Java 24.12 (nejnovější)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}