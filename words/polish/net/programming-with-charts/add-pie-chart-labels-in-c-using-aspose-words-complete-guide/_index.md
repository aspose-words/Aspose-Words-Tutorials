---
category: general
date: 2026-07-20
description: Dodaj etykiety wykresu kołowego za pomocą Aspose.Words dla .NET. Dowiedz
  się, jak zmienić etykiety wykresu kołowego, wyświetlać etykiety procentowe oraz
  szybko aktualizować etykiety serii wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: pl
lastmod: 2026-07-20
og_description: Dodaj etykiety wykresu kołowego w C# przy użyciu Aspose.Words. Opanuj
  zmianę etykiet wykresu kołowego, wyświetlanie etykiet procentowych oraz aktualizację
  etykiet serii wykresu w kilku prostych krokach.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Dodaj etykiety wykresu kołowego w C# – Pełny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Dodawanie etykiet wykresu kołowego w C# przy użyciu Aspose.Words – Kompletny
  przewodnik
url: /pl/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodawanie etykiet wykresu kołowego w C# przy użyciu Aspose.Words – Kompletny przewodnik

Potrzebujesz **dodać etykiety wykresu kołowego** do dokumentu Word przy użyciu C#? Dzięki Aspose.Words możesz bez wysiłku **zmienić etykiety wykresu kołowego** i **wyświetlić procenty wykresu kołowego** bezpośrednio w pliku — bez ręcznej edycji w Wordzie.  

W tym samouczku przeprowadzimy Cię przez dokładne kroki, aby **wyświetlić etykiety procentowe**, przemieścić je oraz nawet **zaktualizować etykiety serii wykresu** dla danych dynamicznych. Po zakończeniu będziesz mieć fragment kodu, który możesz wstawić do dowolnego projektu .NET.

> **Szybki podgląd:** Po zastosowaniu tego przewodnika, otwarcie zapisanego pliku `.docx` pokaże wykres kołowy, w którym każdy segment ma etykietę z procentem, umieszczoną na zewnątrz segmentu dla maksymalnej czytelności.

---

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (najbardziej aktualna wersja na 2026 rok). Możesz go pobrać z NuGet: `Install-Package Aspose.Words`.
- Dokument **Word**, który już zawiera wykres kołowy lub pierścieniowy (nazwijmy go `Chart.docx`).
- Podstawowa znajomość **C#** oraz Visual Studio (lub Twojego ulubionego IDE).

To wszystko — bez dodatkowych bibliotek, bez COM interop, tylko czysty kod zarządzany.

---

## Dodawanie etykiet wykresu kołowego – Pełna implementacja

Poniżej znajduje się **kompletny, działający** program konsolowy w C#, który wczytuje dokument, modyfikuje pierwszy wykres kołowy i zapisuje wynik. Każda linia jest skomentowana, abyś rozumiał **dlaczego** robimy to, co robimy, a nie tylko **co**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Oczekiwany rezultat

Otwórz `ChartWithCustomLabels.docx` w Microsoft Word. Powinieneś zobaczyć wykres kołowy **z etykietami procentowymi umieszczonymi na zewnątrz każdego segmentu**. Etykiety wyglądają mniej więcej tak: „35 %”, „20 %” itd., co sprawia, że wykres jest od razu zrozumiały.

---

## Zmiana etykiet wykresu kołowego: pozycjonowanie i formatowanie

Jeśli potrzebujesz jedynie **zmienić etykiety wykresu kołowego** bez wyświetlania procentów, możesz dostosować właściwość `Position` do jednej z następujących:

| Enum Pozycji | Efekt wizualny |
|--------------|----------------|
| `InsideEnd`   | Etykiety znajdują się wewnątrz segmentu, tuż przy krawędzi. |
| `Center`      | Etykiety pojawiają się w środku segmentu (dobry wybór dla małych wykresów). |
| `OutsideEnd`  | Etykiety są na zewnątrz segmentu, połączone linią prowadzącą (nasze domyślne ustawienie). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Wskazówka:** `OutsideEnd` działa najlepiej, gdy wykres ma wiele segmentów; zapobiega nakładaniu się tekstu.

---

## Wyświetlanie etykiet procentowych na wykresie kołowym

Właściwość `ShowPercentage` jest **flagią boolowską**. Ustawienie jej na `true` informuje Aspose.Words, aby obliczył udział każdego segmentu na podstawie źródła danych.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Możesz również połączyć ją z `ShowValue`, jeśli potrzebujesz zarówno surowych liczb **jak i** procentów:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Gdy obie flagi są włączone, etykieta wygląda tak: „45 % (120)”.

---

## Aktualizacja etykiet serii wykresu dla danych dynamicznych

Często generujesz wykresy w locie — np. miesięczna sprzedaż lub wyniki ankiet. Aby **zaktualizować etykiety serii wykresu** programowo, zmodyfikuj kolekcję `Series` przed manipulacją etykietami danych:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Ten fragment kodu pokazuje, jak **zaktualizować etykiety serii wykresu** dla dowolnej serii, nie tylko pierwszej. Jest przydatny przy tworzeniu raportów łączących dane rzeczywiste i prognozowane.

---

## Przypadki brzegowe i typowe pułapki

| Sytuacja | Na co zwrócić uwagę | Rozwiązanie |
|----------|---------------------|-------------|
| **Wykres nie jest kołowy/pierścieniowy** | `Position` może nie mieć widocznego efektu. | Sprawdź, czy `chart.Type` to `ChartType.Pie` lub `ChartType.Doughnut`. |
| **Nie znaleziono wykresu** | `GetChild` zwraca `null`. | Dodaj warunek zabezpieczający (patrz kod) i zaloguj pomocną wiadomość. |
| **Starsza wersja Worda** | Niektóre funkcje etykiet są ignorowane. | Zapisz jako `.docx` (nowoczesny format), aby zapewnić pełne wsparcie. |
| **Duża liczba segmentów** | Etykiety mogą się nakładać nawet przy `OutsideEnd`. | Rozważ zmniejszenie liczby segmentów lub zwiększenie rozmiaru wykresu. |

---

## Pełny działający przykład (kopiuj‑wklej)

Poniżej znajduje się **cały program**, który możesz skopiować do nowego projektu konsolowego. Po prostu zamień `YOUR_DIRECTORY` na folder zawierający `Chart.docx`.



## Co warto nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}