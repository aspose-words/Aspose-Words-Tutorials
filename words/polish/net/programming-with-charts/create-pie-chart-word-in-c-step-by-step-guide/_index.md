---
category: general
date: 2026-08-07
description: Szybko utwórz wykres kołowy w C#. Dowiedz się, jak wstawić wykres kołowy,
  dodać etykiety danych, wyświetlić procenty na wykresie oraz dostosować etykiety
  danych wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: pl
lastmod: 2026-08-07
og_description: Utwórz wykres kołowy w programie Word w C# przy użyciu Aspose.Words.
  Ten samouczek pokazuje, jak wstawić wykres kołowy, dodać etykiety danych oraz wyświetlić
  procenty, jednocześnie dostosowując etykiety danych wykresu.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Utwórz wykres kołowy w C# – kompletny poradnik
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Tworzenie wykresu kołowego w C# – przewodnik krok po kroku
url: /pl/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie wykresu kołowego w Wordzie w C# – przewodnik krok po kroku

Jeśli potrzebujesz **create pie chart word** dokumentów w C#, ten przewodnik zapewnia kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz, jak **insert pie chart**, **add data labels pie** oraz **show percentage chart**, jednocześnie **customize chart data labels**, aby uzyskać dopracowany wygląd.

Generowanie wykresów programowo oszczędza czas potrzebny na ręczną edycję, szczególnie gdy raporty lub pulpity nawigacyjne muszą być tworzone automatycznie. W poniższych sekcjach dowiesz się wszystkiego, co potrzebne, aby osadzić w pełni opisany wykres kołowy w pliku Word przy użyciu Aspose.Words dla .NET.

## Wymagania wstępne i konfiguracja

* Zainstalowany .NET 6.0 SDK lub nowszy.  
* Ważna licencja Aspose.Words for .NET (lub tymczasowy klucz ewaluacyjny).  
* Visual Studio 2022 (lub dowolne IDE obsługujące C#).  

Add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Jeśli planujesz generować wiele wykresów, włącz tryb **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) dla lepszej wydajności.

## Tworzenie wykresu kołowego w Wordzie przy użyciu Aspose.Words

Pierwszym ważnym krokiem jest utworzenie pustego dokumentu Word oraz obiektu `DocumentBuilder`. Ten obiekt steruje wszystkimi późniejszymi wstawieniami.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Dlaczego to ważne*: `Document` reprezentuje cały plik `.docx`, natomiast `DocumentBuilder` udostępnia płynne API do dodawania akapitów, tabel i wykresów. Rozpoczęcie od czystego dokumentu zapewnia, że żadne ukryte formatowanie nie zakłóci układu wykresu.

## Wstawienie wykresu kołowego do dokumentu

Teraz umieszczamy wykres kołowy o żądanym rozmiarze. Metoda `InsertChart` zwraca obiekt `Chart`, który możemy dalej konfigurować.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Dlaczego to ważne*: Flaga `ChartType.Pie` informuje Aspose.Words, aby wygenerował wykres kołowy. Szerokość (`400`) i wysokość (`300`) podane są w punktach, co daje precyzyjną kontrolę nad rozmiarem wizualnym.

## Wypełnienie wykresu danymi

Wykres kołowy wymaga przynajmniej jednej serii wartości liczbowych. Tutaj dodajemy trzy kategorie: „Apples”, „Bananas” i „Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Dlaczego to ważne*: Każde wywołanie `AddCategory` tworzy segment. Wartość liczbowa określa rozmiar segmentu, a etykieta staje się nazwą kategorii wyświetlaną po włączeniu etykiet danych.

## Dodanie etykiet danych do wykresu kołowego i wyświetlenie procentów

Aby wykres był informacyjny, włączamy etykiety danych, umieszczamy je na zewnątrz segmentów i prosimy Aspose.Words o wyświetlenie zarówno nazwy kategorii, jak i procentu.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Dlaczego to ważne*: Ustawienie `Position` na `OutsideEnd` poprawia czytelność, szczególnie gdy segmenty są małe. Włączenie `ShowCategoryName` i `ShowPercentage` spełnia wymaganie **show percentage chart** oraz realizuje cel **add data labels pie**.

## Dalsza personalizacja etykiet danych wykresu (opcjonalnie)

Możesz chcieć zmienić czcionkę, dodać linię prowadzącą lub ukryć legendę. Poniższy fragment kodu demonstruje typowe modyfikacje:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Dlaczego to ważne*: Dostosowanie wyglądu etykiet zapewnia, że wykres pasuje do wytycznych stylu dokumentu. Usunięcie legendy zmniejsza bałagan wizualny, gdy etykiety danych już przekazują te same informacje.

## Zapisanie dokumentu z dostosowanym wykresem

Na koniec zapisz dokument na dysku. Wybierz ścieżkę, do której masz uprawnienia zapisu.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Po otwarciu `ChartWithCustomLabels.docx` w Microsoft Word zobaczysz wykres kołowy, w którym każdy segment jest oznaczony nazwą kategorii i procentem, umieszczony na zewnątrz segmentu i sformatowany przy użyciu niestandardowych ustawień czcionki.

### Oczekiwany wynik

| Segment | Wartość | Procent | Etykieta wyświetlana w Wordzie |
|---------|---------|---------|--------------------------------|
| Apples  | 40      | 40 %    | Apples – 40 %                  |
| Bananas | 35      | 35 %    | Bananas – 35 %                 |
| Cherries| 25      | 25 %    | Cherries – 25 %                |

Wykres powinien wyglądać podobnie do ilustracji poniżej:

![Dokument Word wyświetlający wykres kołowy z etykietami procentowymi na zewnątrz każdego segmentu](pie-chart-word.png "Przykład tworzenia wykresu kołowego w Wordzie")

*Tekst alternatywny obrazu zawiera główne słowo kluczowe dla SEO.*

## Obsługa wielu serii i przypadków brzegowych

Podstawowy przykład używa jednej serii, co jest typowe dla wykresu kołowego. Jeśli potrzebujesz wyświetlić wiele serii (np. porównując dwa lata), musisz:

1. Wywołać `chart.Series.Add()` dla każdej dodatkowej serii.  
2. Upewnić się, że każda seria używa tych samych kategorii; w przeciwnym razie Aspose.Words zgłosi `ArgumentException`.  
3. Opcjonalnie ustawić `labels.ShowSeriesName = true`, aby odróżnić segmenty.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Gdy istnieje wiele serii, wykres automatycznie renderuje się jako **clustered pie** (zwany także „pie of pies”). Przejrzyj wynik, aby upewnić się, że etykiety pozostają czytelne.

## Typowe pułapki i jak ich unikać

| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| Etykiety nakładają się na segmenty | Mały obszar wykresu lub wiele kategorii | Zwiększ wymiary wykresu (`InsertChart(width, height)`) lub zmień `Position` na `InsideEnd`. |
| Procenty nie sumują się do 100 % | Błędy zaokrągleń w danych | Użyj `labels.ShowPercentage = true` (Aspose.Words automatycznie normalizuje). |
| Wykres wyświetla się pusty w Wordzie | Brak licencji lub przekroczony limit czasu wersji ewaluacyjnej | Upewnij się, że ważna licencja Aspose.Words jest załadowana przed utworzeniem dokumentu. |
| Kolory czcionki różnią się od motywu Worda | Niestandardowa czcionka ustawiona w kodzie | Usuń niestandardowe ustawienia czcionki lub dopasuj kolory do motywu Worda (`System.Drawing.Color.Black`). |

## Pełny kod źródłowy (do uruchomienia)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Uruchomienie programu generuje `ChartWithCustomLabels.docx`, który zawiera przykład **create pie chart word** spełniający wszystkie wymagania wymienione w samouczku.

## Zakończenie

Teraz wiesz, jak **create pie chart word** dokumenty w C# przy użyciu Aspose.Words. Przewodnik obejmował wstawianie wykresu kołowego, **add data labels pie**, **show percentage chart** oraz **customize chart data labels**, aby uzyskać profesjonalny, oparty na danych plik Word.

Od tego momentu możesz zgłębiać powiązane tematy, takie jak **insert pie chart** w istniejących akapitach, generowanie wykresów **bar** lub **line**, czy automatyzacja masowego tworzenia raportów z różnymi zestawami danych. Eksperymentuj z różnymi pozycjami etykiet, stylami czcionek i konfiguracjami wieloserii, aby dostosować wynik do swoich konkretnych potrzeb raportowych.

Miłego tworzenia wykresów!

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dostosuj etykietę danych wykresu](/words/english/net/programming-with-charts/chart-data-label/)
- [Ustaw domyślne opcje dla etykiet danych w wykresie](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Wstaw wykres kolumnowy w dokumencie Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}