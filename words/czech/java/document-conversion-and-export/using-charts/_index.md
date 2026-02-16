---
date: 2026-02-16
description: Naučte se, jak přidat více sérií do grafů v Aspose.Words pro Java, změnit
  značky os, použít vlastní formát čísel a generovat dokumenty Word s grafy, obsahujícími
  čárové a sloupcové grafy.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Přidat více sérií do grafů v Aspose.Words pro Java
url: /cs/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidání více sérií do grafů v Aspose.Words pro Java

## Úvod do používání grafů v Aspose.Words pro Java

V tomto tutoriálu se naučíte **jak přidat více sérií** do grafu pomocí Aspose.Words pro Java, proč je důležité přizpůsobit značky os a použít vlastní číselný formát, a jak vygenerovat Word dokument bohatý na grafy. Ať už potřebujete čárový graf pro finanční data nebo sloupcový graf pro prodejní čísla, níže uvedené kroky vás provedou tvorbou, stylováním a jemným laděním grafů programově.

## Rychlé odpovědi
- **Jak přidám více sérií?** Použijte `chart.getSeries().add(...)` pro každou sérii, kterou chcete zobrazit.  
- **Mohu změnit značky os?** Ano – použijte `setMajorTickMark()` a `setMinorTickMark()` na objektech osy.  
- **Jaký formát mohu použít pro popisky dat?** Jakýkoli číselný formát kompatibilní s Excelem, např. `"$"#,##0.00` nebo `0.00%`.  
- **Jaké typy grafů jsou podporovány?** Čárový, sloupcový, plošný, bublinový, rozptylový a mnoho dalších pomocí `ChartType`.  
- **Je pro produkci vyžadována licence?** Platná licence Aspose.Words pro Java je potřeba pro plnou funkčnost.

## Co znamená „přidat více sérií“ v grafu?
Přidání více sérií znamená vložení více než jedné datové sady do stejné oblasti grafu, což vám umožní porovnávat různé kategorie nebo časová období vedle sebe. Každá série se zobrazuje jako vlastní čára, sloupec nebo sada značek, čímž čtenářům poskytuje bohatší vizuální příběh.

## Proč použít Aspose.Words pro Java k vytváření Word dokumentů s grafy?
- **Plná kontrola** nad typem grafu, rozvržením a stylem bez nutnosti ručně otevírat Word.  
- **Programové generování** zapadá do automatizovaných pipeline pro reportování.  
- **Cross‑platform** – funguje v jakémkoli prostředí kompatibilním s Javou.  
- **Bohaté API** pro přizpůsobení os, popisků dat a číselných formátů.

## Požadavky
- Java Development Kit (JDK) 8 nebo vyšší.  
- Knihovna Aspose.Words pro Java přidaná do vašeho projektu (Maven/Gradle nebo JAR).  
- Platná licence Aspose pro produkci (volitelná pro hodnocení).

## Postup krok za krokem

### Krok 1: Vytvořte čárový graf a **přidejte více sérií**
Níže je hlavní kód, který vytváří čárový graf, vymaže výchozí sérii a poté přidá tři odlišné série s vlastními popisky dat.

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

> **Pro tip:** Zavolejte `chart.getSeries().add(...)` tolikrát, kolik potřebujete, aby **přidali více sérií** – každé volání vytvoří novou čáru (nebo sloupec, atd.) ve stejném grafu.

### Krok 2: **Vytvořte sloupcový graf** (create column chart java)
Další úryvek ukazuje, jak vložit jednoduchý sloupcový graf, který je užitečný pro porovnání kategorií vedle sebe.

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

### Krok 3: **Změňte značky os** (change axis tick marks)
Přizpůsobení os X a Y zlepšuje čitelnost. Následující kód demonstruje, jak změnit značky, obrátit pořadí a nastavit vlastní průsečíkové body.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Krok 4: **Použijte vlastní číselný formát** (apply custom number format)
Můžete formátovat čísla os nebo popisky dat libovolným vzorem podporovaným Excelem. Níže je stručný příklad, který formátuje osu Y s oddělovačem tisíců.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Krok 5: Vygenerujte finální Word dokument (generate chart word document)
Po nastavení sérií, os a popisků stačí zavolat `doc.save(...)` podle ukázek výše. Výsledný soubor `.docx` obsahuje plně funkční grafy, které lze otevřít a upravit v Microsoft Word.

## Běžné příklady použití
- **Finanční dashboardy** – čárové grafy s více sériemi pro příjmy, výdaje a zisk.  
- **Prodejní zprávy** – sloupcové grafy porovnávající čtvrtletní prodeje napříč regiony.  
- **Sledování projektů** – plošné nebo rozptylové grafy vizualizující postup v čase.  

## Další úpravy grafů
Mimo základy můžete upravovat limity, skrývat osy (`axis.setHidden(true)`), měnit barvy, přidávat legendy a další. Pro úplný seznam možností se podívejte do referenční dokumentace Aspose.Words pro Java API.

## Závěr
V tomto průvodci jsme si ukázali, jak **přidat více sérií** do grafů, vytvořit jak čárové, tak sloupcové grafy, **změnit značky os**, **použít vlastní číselné formáty** a nakonec **vygenerovat Word dokument bohatý na grafy**. S Aspose.Words pro Java máte výkonný, kódem řízený způsob, jak vložit profesionální vizualizace dat přímo do svých dokumentů.

## Často kladené otázky

**Q: Jak mohu přidat více sérií do grafu?**  
A: Zavolejte `chart.getSeries().add()` pro každou sérii, kterou chcete zobrazit. Každé volání vytvoří novou datovou sadu, která se zobrazí jako vlastní čára, sloupec nebo skupina značek.

**Q: Jak mohu formátovat popisky dat pomocí vlastního číselného formátu?**  
A: Přistupte k objektu `DataLabels` série a použijte `getNumberFormat().setFormatCode("váš vzor")`. Formát můžete také propojit se zdrojovou buňkou pomocí `isLinkedToSource(true)`.

**Q: Jak mohu změnit značky os?**  
A: Použijte `setMajorTickMark()` a `setMinorTickMark()` na `ChartAxis`. Možnosti zahrnují `CROSS`, `INSIDE`, `OUTSIDE` a `NONE`.

**Q: Mohu vytvořit jiné typy grafů, jako jsou rozptylové nebo plošné grafy?**  
A: Ano – při volání `builder.insertChart(...)` specifikujte požadovaný `ChartType` (např. `ChartType.SCATTER`, `ChartType.AREA`).

**Q: Jak mohu skrýt osu, kterou nepotřebuji?**  
A: Zavolejte `axis.setHidden(true)` na `ChartAxis`, kterou chcete skrýt.

---

**Poslední aktualizace:** 2026-02-16  
**Testováno s:** Aspose.Words pro Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}