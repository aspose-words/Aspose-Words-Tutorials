---
category: general
date: 2026-06-02
description: Wyświetl legendę wykresu w dokumencie Word przy użyciu C#. Dowiedz się,
  jak dodać legendę, zastosować gotowy styl wykresu i dostosować wygląd wykresów w
  Wordzie w kilka minut.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: pl
og_description: Pokaż legendę wykresu w dokumencie Word od razu. Ten przewodnik przeprowadzi
  Cię przez dodawanie legendy, stosowanie gotowego stylu wykresu i obsługę przypadków
  brzegowych.
og_title: Pokaż legendę wykresu w Word – Pełny samouczek C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Wyświetlanie legendy wykresu w Wordzie przy użyciu C# – Kompletny przewodnik
  krok po kroku
url: /pl/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pokaż legendę wykresu w Wordzie przy użyciu C# – Kompletny przewodnik krok po kroku

Zastanawiałeś się kiedyś **jak dodać legendę** do wykresu znajdującego się w dokumencie Word? Nie jesteś jedyny. W wielu raportach brak legendy sprawia, że dane wyglądają zagadkowo, a naprawienie tego nie powinno być uciążliwe.  

W tym samouczku **pokażemy legendę wykresu** w pliku Word przy użyciu Aspose.Words for .NET, zastosujemy gotowy styl wykresu i zapewnimy, że legenda pojawi się dokładnie tam, gdzie jej potrzebujesz. Po zakończeniu będziesz mieć gotowy do uruchomienia przykład, który możesz wstawić do dowolnego projektu C#.

## Co obejmuje ten przewodnik

Przejdziemy przez cały proces:

1. Wczytaj istniejący plik *.docx*, który już zawiera wykres.  
2. Pobierz pierwszy wykres (lub dowolny wykres, który chcesz).  
3. **Zastosuj gotowy styl wykresu**, aby nadać wizualizacji profesjonalny wygląd.  
4. **Pokaż legendę wykresu**, umieść ją po prawej stronie i obsłuż szczególne przypadki, takie jak wykresy Waterfall.  
5. Zapisz zmodyfikowany dokument.

Bez zewnętrznych narzędzi, bez ręcznego manipulowania interfejsem UI — tylko czysty kod. Jedynym wymogiem wstępnym jest odwołanie do pakietu NuGet Aspose.Words (wersja 23.10 lub nowsza) oraz podstawowa znajomość C#.

---

## Wymagania wstępne

- .NET 6.0 lub nowszy (przykład działa również z .NET Framework 4.7.2).  
- Biblioteka Aspose.Words for .NET zainstalowana (`Install-Package Aspose.Words`).  
- Plik Word (`input.docx`), który już zawiera co najmniej jeden wykres.  
- Visual Studio, Rider lub dowolne IDE, którego używasz.

---

## Krok 1: Przygotuj projekt i wczytaj dokument

Najpierw utwórz aplikację konsolową (lub wstaw kod do istniejącego projektu). Dodaj dyrektywy `using` i wczytaj plik `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Dlaczego to ważne:** Wczytanie dokumentu jest podstawą. Bez instancji `Document` nie możesz uzyskać dostępu do obiektów wykresu, które udostępnia Aspose.Words.

---

## Krok 2: Pobierz docelowy wykres

Wykresy są przechowywane jako węzły w drzewie dokumentu. Metoda `GetChild` wykonuje głębokie wyszukiwanie, umożliwiając pobranie pierwszego wykresu, niezależnie od tego, gdzie się znajduje (nagłówek, treść, stopka itp.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Wskazówka:** Jeśli masz wiele wykresów, zmień indeks `0` na `1`, `2`, … lub iteruj przez `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Krok 3: Zastosuj gotowy styl wizualny

Estetyczny wykres często zaczyna się od stylu. Aspose.Words dostarcza dziesiątki wbudowanych stylów; `ChartStyle.Style12` to czysta, nowoczesna opcja.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Jak to działa:** Właściwość `Style` odnosi się do wbudowanych stylów wykresów Word, które widzisz w interfejsie użytkownika. Wybranie gotowego stylu oszczędza ręczne ustawianie kolorów, czcionek i znaczników.

---

## Krok 4: Włącz legendę i ustaw jej pozycję

Teraz najważniejszy element — **pokaż legendę wykresu**. Włączamy legendę, a następnie przypinamy ją po prawej stronie wykresu.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Dlaczego po prawej?** Umieszczenie legendy po prawej stronie pozostawia szeroki obszar danych, co jest szczególnie przydatne w wykresach słupkowych lub kolumnowych.

---

## Krok 5: Obsługa wykresów Waterfall (przypadek specjalny)

Wykresy Waterfall zachowują się nieco inaczej; legenda może być domyślnie ukryta. Poniższy warunek zabezpieczający zapewnia, że legenda jest widoczna, gdy typ wykresu to Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Uwaga dotycząca przypadków brzegowych:** Niektóre starsze wersje Word ignorują `HasLegend` dla wykresów Waterfall, więc jawne ustawienie `Legend.Show` zapewnia widoczność.

---

## Krok 6: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany na dysku. Możesz nadpisać oryginalny plik lub utworzyć nowy.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Uruchomienie programu wygeneruje `output.docx` z widoczną legendą po prawej stronie, stylizowaną przy użyciu `Style12`. Otwórz plik w Wordzie, aby zweryfikować rezultat.

---

## Pełny działający przykład (wszystkie kroki razem)

Poniżej znajduje się kompletny, gotowy do uruchomienia kod. Skopiuj i wklej go do `Program.cs` (lub dowolnego pliku C#) i dostosuj ścieżki plików.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Oczekiwany wynik:** Otwierając `output.docx` zobaczysz oryginalny wykres z legendą wyrównaną do prawej, stylizowaną nowoczesnym `Style12`. Wszystkie serie danych są wyraźnie oznaczone, co sprawia, że wykres jest od razu zrozumiały.

---

## Najczęściej zadawane pytania (FAQ)

### Jak dodać legendę do konkretnego wykresu (nie pierwszego)?

Zastąp indeks `0` w `GetChild(NodeType.Chart, 0, true)` pozycją zerową docelowego wykresu lub przeiteruj wszystkie węzły wykresów:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Czy mogę umieścić legendę na dole zamiast po prawej?

Oczywiście. Wystarczy zmienić wartość wyliczenia `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Co zrobić, gdy wykres już ma legendę, ale chcę ją ukryć?

Ustaw `HasLegend` na `false`:

```csharp
chart.HasLegend = false;
```

### Czy to działa z Word 2010, 2016 i nowszymi wersjami?

Tak. Aspose.Words abstrahuje wersję Worda, więc ten sam kod działa we wszystkich nowoczesnych plikach .docx.

---

## Profesjonalne wskazówki i typowe pułapki

- **Pro tip:** Po zastosowaniu stylu możesz nadal dostosowywać poszczególne elementy (kolory, etykiety danych) za pomocą kolekcji `Chart.Series`. Styl zapewnia solidną bazę.
- **Uwaga:** Jeśli wykres znajduje się w komórce tabeli, legenda może być przycięta. Rozważ zwiększenie rozmiaru wykresu (`chart.Width`, `chart.Height`) przed ustawieniem legendy.
- **Uwaga dotycząca wydajności:** Wczytywanie dużych dokumentów (setki MB) może być pamięcio‑intensywne. Użyj `LoadOptions` z `LoadFormat.Docx`, aby zmniejszyć obciążenie, jeśli potrzebujesz jedynie manipulacji wykresem.

---

## Kolejne kroki

Teraz, gdy wiesz **jak dodać legendę** i **zastosować gotowy styl wykresu** w Wordzie, możesz zbadać:

- **Niestandardowe kolory wykresu** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Formatowanie etykiet danych** (`chart.Series[i].HasDataLabel = true`).  
- **Eksportowanie wykresu jako obrazu** (`chart.ToImage()`), przydatne przy osadzaniu w innych miejscach.  

Każdy z tych tematów opiera się na tym samym modelu obiektowym, więc krzywa uczenia się będzie łagodna.

---

## Zakończenie

Zademonstrowaliśmy czyste, kompleksowe rozwiązanie dla **pokazania legendy wykresu** w dokumencie Word przy użyciu C#. Ładując dokument, pobierając wykres, stosując gotowy styl, włączając legendę i obsługując specyfikę wykresów Waterfall, otrzymujesz dopracowany wykres gotowy do każdego raportu biznesowego.  

Śmiało eksperymentuj z innymi wartościami `ChartStyle` lub pozycjami legendy — Twoje wizualizacje danych zasługują na najlepszą prezentację. Jeśli napotkasz problemy, zostaw komentarz poniżej; szczęśliwego kodowania!

## Co warto nauczyć się dalej?

Podane poniżej samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletny działający kod z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstaw wykres kolumnowy w dokumencie Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Ukryj oś wykresu w dokumencie Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Korzystanie z Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}