---
date: 2026-02-16
description: Dowiedz się, jak dodać wiele serii do wykresów w Aspose.Words for Java,
  zmienić znaczniki osi, zastosować własny format liczb oraz generować dokumenty Word
  z wykresami liniowymi i kolumnowymi.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Dodaj wiele serii do wykresów w Aspose.Words for Java
url: /pl/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj wiele serii do wykresów w Aspose.Words for Java

## Wprowadzenie do używania wykresów w Aspose.Words for Java

W tym samouczku dowiesz się **jak dodać wiele serii** do wykresu przy użyciu Aspose.Words for Java, dlaczego dostosowywanie znaczników osi i stosowanie własnego formatu liczbowego ma znaczenie oraz jak wygenerować dokument Word bogaty w wykresy. Niezależnie od tego, czy potrzebujesz wykresu liniowego dla danych finansowych, czy wykresu słupkowego dla wyników sprzedaży, poniższe kroki poprowadzą Cię przez tworzenie, stylizowanie i precyzyjne dopasowywanie wykresów programowo.

## Szybkie odpowiedzi
- **Jak dodać wiele serii?** Użyj `chart.getSeries().add(...)` dla każdej serii, którą chcesz wyświetlić.  
- **Czy mogę zmienić znaczniki osi?** Tak – użyj `setMajorTickMark()` i `setMinorTickMark()` na obiektach osi.  
- **Jaki format mogę zastosować do etykiet danych?** Dowolny format liczbowy zgodny z Excelem, np. `"$"#,##0.00` lub `0.00%`.  
- **Jakie typy wykresów są obsługiwane?** Liniowy, słupkowy, obszarowy, bąbelkowy, punktowy i wiele innych za pomocą `ChartType`.  
- **Czy wymagana jest licencja do produkcji?** Wymagana jest ważna licencja Aspose.Words for Java, aby uzyskać pełną funkcjonalność.

## Co oznacza „dodawanie wielu serii” w wykresie?
Dodawanie wielu serii oznacza wstawienie więcej niż jednego zestawu danych do tego samego obszaru wykresu, co pozwala porównać różne kategorie lub okresy czasu obok siebie. Każda seria pojawia się jako własna linia, słupek lub zestaw znaczników, dając czytelnikom bogatszą historię wizualną.

## Dlaczego używać Aspose.Words for Java do generowania dokumentów Word z wykresami?
- **Pełna kontrola** nad typem wykresu, układem i stylizacją bez ręcznego otwierania Worda.  
- **Generowanie programowe** pasuje do zautomatyzowanych potoków raportowania.  
- **Cross‑platform** – działa w każdym środowisku zgodnym z Javą.  
- **Bogate API** do dostosowywania osi, etykiet danych i formatów liczb.

## Prerequisites
- Java Development Kit (JDK) 8 lub nowszy.  
- Biblioteka Aspose.Words for Java dodana do projektu (Maven/Gradle lub JAR).  
- Ważna licencja Aspose do produkcji (opcjonalnie do oceny).

## Przewodnik krok po kroku

### Krok 1: Utwórz wykres liniowy i **dodaj wiele serii**
Poniżej znajduje się podstawowy kod, który tworzy wykres liniowy, usuwa domyślną serię, a następnie dodaje trzy odrębne serie z niestandardowymi etykietami danych.

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

> **Pro tip:** Wywołaj `chart.getSeries().add(...)` tak wiele razy, jak potrzebujesz, aby **dodać wiele serii** – każde wywołanie tworzy nową linię (lub słupek itp.) na tym samym wykresie.

### Krok 2: **Utwórz wykres słupkowy** (create column chart java)
Następny fragment pokazuje, jak wstawić prosty wykres słupkowy, przydatny do porównywania kategorii obok siebie.

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

### Krok 3: **Zmień znaczniki osi** (change axis tick marks)
Dostosowanie osi X i Y poprawia czytelność. Poniższy kod demonstruje, jak zmienić znaczniki, odwrócić kolejność i ustawić własne punkty przecięcia.

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

### Krok 4: **Zastosuj własny format liczbowy** (apply custom number format)
Możesz formatować liczby na osiach lub etykiety danych dowolnym wzorcem obsługiwanym przez Excel. Poniżej znajduje się zwięzły przykład, który formatuje oś Y przy użyciu wzorca z separatorem tysięcy.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Krok 5: Wygeneruj końcowy dokument Word (generate chart word document)
Po skonfigurowaniu serii, osi i etykiet po prostu wywołaj `doc.save(...)`, jak pokazano w powyższych fragmentach. Powstały plik `.docx` zawiera w pełni funkcjonalne wykresy, które można otworzyć i edytować w Microsoft Word.

## Typowe przypadki użycia
- **Panele finansowe** – wykresy liniowe z wieloma seriami dla przychodów, wydatków i zysku.  
- **Raporty sprzedaży** – wykresy słupkowe porównujące kwartalne wyniki sprzedaży w różnych regionach.  
- **Śledzenie projektów** – wykresy obszarowe lub punktowe wizualizujące postęp w czasie.  

## Dodatkowe dostosowania wykresów
Poza podstawami możesz regulować granice, ukrywać osie (`axis.setHidden(true)`), zmieniać kolory, dodawać legendy i wiele więcej. Zapoznaj się z dokumentacją API Aspose.Words for Java, aby poznać pełną listę dostępnych opcji.

## Zakończenie
W tym przewodniku omówiliśmy, jak **dodać wiele serii** do wykresów, tworzyć zarówno wykresy liniowe, jak i słupkowe, **zmienić znaczniki osi**, **zastosować własne formaty liczb** oraz w końcu **wygenerować dokument Word bogaty w wykresy**. Dzięki Aspose.Words for Java masz potężne, kod‑pierwsze rozwiązanie do osadzania profesjonalnych wizualizacji danych bezpośrednio w dokumentach.

## Najczęściej zadawane pytania

**Q: Jak mogę dodać wiele serii do wykresu?**  
A: Wywołaj `chart.getSeries().add()` dla każdej serii, którą chcesz wyświetlić. Każde wywołanie tworzy nowy zestaw danych, który pojawia się jako własna linia, słupek lub grupa znaczników.

**Q: Jak sformatować etykiety danych własnym formatem liczbowym?**  
A: Uzyskaj dostęp do obiektu `DataLabels` serii i użyj `getNumberFormat().setFormatCode("twój wzorzec")`. Możesz także powiązać format ze źródłową komórką za pomocą `isLinkedToSource(true)`.

**Q: Jak mogę zmienić znaczniki osi?**  
A: Użyj `setMajorTickMark()` i `setMinorTickMark()` na obiekcie `ChartAxis`. Dostępne opcje to `CROSS`, `INSIDE`, `OUTSIDE` i `NONE`.

**Q: Czy mogę tworzyć inne typy wykresów, takie jak punktowy lub obszarowy?**  
A: Tak – określ żądany `ChartType` (np. `ChartType.SCATTER`, `ChartType.AREA`) podczas wywoływania `builder.insertChart(...)`.

**Q: Jak ukryć niepotrzebną oś?**  
A: Wywołaj `axis.setHidden(true)` na obiekcie `ChartAxis`, który chcesz ukryć.

---

**Ostatnia aktualizacja:** 2026-02-16  
**Testowano z:** Aspose.Words for Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}