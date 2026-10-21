---
category: general
date: 2026-07-19
description: Rozdziel kawałek wykresu kołowego przy użyciu Aspose.Words dla C#. Dowiedz
  się, jak rozdzielić kawałek koła, dostosować rozmiar otworu w wykresie pierścieniowym
  oraz szybko zmienić punkty danych wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: pl
lastmod: 2026-07-19
og_description: Wysuwaj fragment wykresu kołowego za pomocą Aspose.Words for C#. Ten
  przewodnik pokazuje, jak wysunąć kawałek koła, dostosować rozmiar otworu w wykresie
  pierścieniowym oraz efektywnie zmienić punkty danych wykresu.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Oddziel fragment wykresu kołowego w C# – Poradnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Rozdzielenie segmentu wykresu kołowego w C# z Aspose.Words – pełny przewodnik
url: /pl/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozdzielenie fragmentu wykresu kołowego w C# przy użyciu Aspose.Words – Pełny przewodnik

Zastanawiałeś się kiedyś, jak **explode pie chart slice** w dokumencie Word przy użyciu C#? Nie jesteś jedyny. Niezależnie od tego, czy przygotowujesz prezentację sprzedażową, czy wizualizujesz wyniki ankiety, rozdzielony fragment przyciąga uwagę dokładnie tam, gdzie tego potrzebujesz. W tym tutorialu przeprowadzimy Cię przez cały proces – wczytanie dokumentu, pobranie wykresu, rozdzielenie pierwszego fragmentu, dostosowanie otworu w wykresie pierścieniowym oraz zmianę punktów danych wykresu.

Dodamy także dodatkowe koncepcje, które mogą Cię interesować: **how to explode pie slice**, **adjust doughnut hole size**, oraz **change chart data points**. Bez zbędnych wstępów, gotowe rozwiązanie gotowe do skopiowania i wklejenia.

---

## Co będzie potrzebne

Zanim zaczniemy, upewnij się, że masz:

- **Aspose.Words for .NET** (najświeższą wersję dostępną na dzień 2026‑07‑19). Możesz ją pobrać z NuGet poleceniem `Install-Package Aspose.Words`.
- Projekt **.NET 6+** (lub .NET Framework 4.7.2+, jeśli nadal pracujesz na starszej platformie).
- Plik Word (`Chart.docx`) zawierający wykres kołowy lub pierścieniowy. Jeśli go nie masz, szybko utwórz wykres w Wordzie i zapisz.

To wszystko – żadnych dodatkowych bibliotek, żadnego COM interopu, wyłącznie czysty kod zarządzany.

---

## Rozdzielenie fragmentu wykresu kołowego – implementacja krok po kroku

Poniżej dzielimy zadanie na małe kroki. Każda sekcja ma wyraźny nagłówek, fragment kodu i krótkie wyjaśnienie *dlaczego* robimy to, co robimy.

### Krok 1: Zainstaluj i odwołaj się do Aspose.Words

Najpierw dodaj pakiet Aspose.Words do swojego projektu. W konsoli Menedżera Pakietów:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** Jeśli używasz wbudowanego UI NuGet w Visual Studio, wyszukaj „Aspose.Words” i kliknij Install. Dzięki temu otrzymasz najnowsze poprawki i możliwość pracy z wykresami od razu.

### Krok 2: Wczytaj dokument Word zawierający wykres

Potrzebujemy obiektu `Document`, który wskaże na plik `.docx` z wykresem, który chcesz zmodyfikować.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Dlaczego to ważne:** `Document` jest punktem wejścia dla każdej operacji w Aspose.Words. Sprawdzając obecność wykresów już na początku, unikamy później błędów typu null reference przy próbie rozdzielenia fragmentu.

### Krok 3: Pobierz pierwszy węzeł wykresu

Większość przykładów zakłada pojedynczy wykres, więc pobierzemy pierwszy. Jeśli masz ich więcej, dostosuj indeks odpowiednio.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Uwaga:** Rzutowanie do `Chart` jest bezpieczne po potwierdzeniu, że wykres istnieje. Ten obiekt daje dostęp do serii, punktów danych i ustawień specyficznych dla typu wykresu.

### Krok 4: Rozdziel pierwszy fragment wykresu kołowego

Teraz najważniejsze – **how to explode pie slice**. Ustawimy właściwość `Exploded` pierwszego punktu danych.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Dlaczego to działa:** `Exploded` mówi Wordowi, aby odsunął ten fragment od środka, tworząc klasyczny efekt „rozsypanego koła”. Właściwość jest typu bool, więc ustawienie jej na `true` wystarczy.

### Krok 5: Dostosuj rozmiar otworu w wykresie pierścieniowym (jeśli to wykres pierścieniowy)

Jeśli Twój wykres jest pierścieniowy, możesz **adjust doughnut hole size**. Rozmiar otworu podawany jest jako procent promienia wykresu.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Co oznacza liczba:** Wartość `30` oznacza, że wewnętrzny okrąg zajmuje 30 % całkowitego promienia, pozostawiając grubszą zewnętrzną obręcz.

### Krok 6: Zmień punkty danych wykresu (opcjonalnie)

Czasami trzeba **change chart data points** – np. zaktualizowałeś liczby i chcesz, aby wizualizacja odzwierciedlała nowe wartości.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Dlaczego to robisz:** Zmiana wartości punktu danych automatycznie przelicza procenty fragmentów, utrzymując wykres aktualny bez ręcznej edycji w Wordzie.

### Krok 7: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany na dysku. Możesz nadpisać oryginał lub utworzyć nowy plik – jak wolisz.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Wskazówka:** Użyj `SaveFormat.Docx`, jeśli chcesz być explicite, ale `Save(string)` automatycznie wykrywa format na podstawie rozszerzenia pliku.

---

## Oczekiwany rezultat

Po otwarciu `FormattedChart.docx` w Microsoft Word powinieneś zobaczyć:

- Pierwszy fragment wykresu kołowego **rozsypany** na zewnątrz.
- Jeśli wykres jest pierścieniowy, centralny otwór zajmuje teraz **30 %** promienia.
- Wszystkie zmodyfikowane punkty danych odzwierciedlają nowe wartości, które ustawiłeś.

Poniżej przykładowa ilustracja, jak wygląda rozdzielony fragment (obraz wyłącznie w celach ilustracyjnych).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Alt text:* **exploded pie chart slice** pokazujący odsunięty segment w dokumencie Word.

---

## Częste pytania i sytuacje brzegowe

**Co jeśli wykres nie jest kołowy ani pierścieniowy?**  
Kod sprawdza `ChartType` przed zastosowaniem `Exploded` lub `HoleSize`. Dla wykresów słupkowych, liniowych czy powierzchniowych te właściwości po prostu nie istnieją, więc logika pomija je bezpiecznie.

**Czy mogę rozdzielić wiele fragmentów?**  
Oczywiście. Przejdź pętlą po `chart.PieChartData.Series[0].DataPoints` i ustaw `Exploded = true` dla dowolnych indeksów, które chcesz.

**Czy muszę martwić się o formaty liczb zależne od kultury?**  
Aspose.Words przechowuje wartości liczbowe jako `double`, niezależnie od ustawień regionalnych, więc nie masz problemów z przecinkami vs kropkami.

**A co z wykresami osadzonymi w nagłówkach/stopkach?**  
Użyj `doc.GetChildNodes(NodeType.Chart, true)`, aby pobrać wszystkie wykresy, a następnie sprawdź `ParentNode` każdego węzła, aby określić jego położenie. Ta sama logika rozdzielenia działa.

---

## Podsumowanie

Masz teraz gotowe, gotowe do skopiowania rozwiązanie, jak **explode pie chart slice** przy użyciu Aspose.Words w C#. Przeanalizowaliśmy cały przepływ – od wczytania dokumentu, pobrania wykresu, rozdzielenia fragmentu, **adjusting doughnut hole size**, po **changing chart data points** i zapisania pliku.

Śmiało eksperymentuj: rozdziel inny fragment, zmień rozmiar otworu na 45 %, lub zaktualizuj kilka punktów danych jednocześnie. API Aspose.Words sprawia, że te zmiany są bezbolesne, a efekty widoczne od razu po otwarciu pliku Word.

---

### Co dalej?

- **Stylizuj rozdzielony fragment** (zmień kolor wypełnienia, obramowanie lub dodaj etykietę danych). Szukaj „Aspose.Words chart formatting”.
- **Automatyzuj przetwarzanie wsadowe** wielu dokumentów – przeiteruj folder, rozdziel fragmenty i zapisz nowe wersje.
- **Połącz z Aspose.Slides**, jeśli potrzebujesz tego samego wykresu w prezentacji PowerPoint.

Masz więcej pytań dotyczących manipulacji wykresami lub chcesz zagłębić się w inne typy wykresów? zostaw komentarz poniżej i powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletny, działający kod oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}