---
category: general
date: 2026-09-11
description: Samouczek edycji etykiety wykresu pokazujący, jak zmienić pozycję etykiety
  wykresu, dostosować etykietę danych wykresu, ukryć nazwę kategorii wykresu oraz
  wyświetlić wartość etykiety wykresu przy użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: pl
lastmod: 2026-09-11
og_description: Samouczek edycji etykiet wykresu prowadzi Cię przez zmianę pozycji
  etykiety wykresu, dostosowywanie etykiety danych wykresu, ukrywanie nazwy kategorii
  wykresu oraz wyświetlanie wartości etykiety wykresu przy użyciu Aspose.Words dla
  .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Samouczek edycji etykiet wykresu – dostosuj etykiety wykresów w Wordzie
  w C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Edycja etykiet wykresu – modyfikowanie etykiet wykresu w Wordzie w C#
url: /pl/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Samouczek edycji etykiet wykresu – modyfikowanie etykiet wykresu Word w C#

Jeśli potrzebujesz **samouczka edycji etykiet wykresu** dla dokumentu Word, ten przewodnik pokaże Ci dokładnie, jak zmienić pozycję etykiety wykresu, dostosować etykietę danych wykresu, ukryć nazwę kategorii wykresu i wyświetlić wartość etykiety wykresu przy użyciu Aspose.Words for .NET. Zobaczysz kompletny, gotowy do uruchomienia przykład, który możesz wkleić do dowolnego projektu C#.

Praca z etykietami wykresów jest częstym wymogiem przy generowaniu raportów, faktur lub pulpitów nawigacyjnych programowo. Ten samouczek obejmuje każdy krok — od wczytania dokumentu po zapisanie zmian — abyś mógł tworzyć dopracowane wykresy bez ręcznej edycji.

## Prerequisites

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 lub nowszy zainstalowany  
* Ważną licencję Aspose.Words for .NET (lub tymczasowy klucz ewaluacyjny)  
* Visual Studio 2022 lub dowolne IDE kompatybilne z C#  
* Plik Word (`Chart.docx`) zawierający przynajmniej jeden wykres  

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Step 1: Set up the project and import namespaces

Utwórz nową aplikację konsolową i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Otwórz `Program.cs` i zaimportuj wymagane przestrzenie nazw:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Te przestrzenie nazw dają dostęp do klasy `Document` służącej do obsługi plików Word oraz klas `Chart` umożliwiających manipulację elementami wykresu.

## Step 2: Load the Word document that contains a chart

Pierwsza wykonywalna linia wczytuje dokument źródłowy. Zastąp `YOUR_DIRECTORY` rzeczywistą ścieżką, w której znajduje się `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Wczytanie dokumentu tworzy jego reprezentację w pamięci, którą możesz przeglądać i modyfikować.

## Step 3: Retrieve the first chart in the document

Wykresy są przechowywane jako węzły podrzędne typu `NodeType.Chart`. Metoda `GetChild` przeszukuje drzewo dokumentu i zwraca wykres, który chcesz edytować.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Jeśli dokument zawiera wiele wykresów, możesz zmienić indeks, aby wybrać inny.

## Step 4: Access and customize the data label of the first series

Każda seria wykresu ma obiekt `DataLabel`, który kontroluje wygląd etykiety. Poniższy kod demonstruje cztery kluczowe dostosowania wymagane w samouczku.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Dlaczego te ustawienia mają znaczenie**

* `DataLabelPosition.Center` przenosi etykietę z domyślnej pozycji poza punktem do środka punktu danych, co ułatwia odczyt wykresu przy gęsto rozmieszczonych punktach.  
* Ustawienie własnego `Separator` pozwala kontrolować, jak nazwa serii, wartość i inne części są łączone.  
* Ukrycie nazwy kategorii (`ShowCategoryName = false`) zmniejsza bałagan wizualny, gdy kategoria jest już widoczna na osi.  
* Włączenie `ShowValue` zapewnia wyświetlenie rzeczywistej wartości danych, co często jest wymagane w raportach finansowych lub statystycznych.

## Step 5: Save the modified document

Po dostosowaniu właściwości etykiet, zapisz zmiany do nowego pliku:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Nowy plik (`CustomLabelChart.docx`) zawiera ten sam układ wykresu, ale z wyglądem etykiet, który zdefiniowałeś.

## Full source code

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Skopiuj go do `Program.cs`, dostosuj ścieżki plików i uruchom projekt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Expected result

Otwórz `CustomLabelChart.docx` w Microsoft Word. Powinieneś zobaczyć etykietę pierwszej serii wykresu wyśrodkowaną na każdym punkcie danych, wyświetlającą tylko wartość liczbową i używającą „; ” jako separatora. Nazwy kategorii nie będą już wyświetlane obok wartości.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Co zrobić, jeśli dokument nie zawiera wykresu?** | Przykład sprawdza, czy wykres jest `null` i kończy działanie z odpowiednim komunikatem w konsoli. |
| **Czy mogę edytować etykiety wielu serii?** | Tak. Przejdź pętlą po `chart.Series` i zastosuj te same ustawienia `DataLabel` dla każdej `Series[i].DataLabel`. |
| **Jak zmienić styl czcionki etykiety?** | Użyj `label.Font` (np. `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Czy `DataLabelPosition.Center` jest obsługiwane we wszystkich typach wykresów?** | Większość wykresów 2‑D ją obsługuje. W wykresach 3‑D niektóre pozycje mogą być ignorowane przez Word. |
| **Czy potrzebna jest licencja na Aspose.Words?** | Tryb ewaluacyjny działa, ale dodaje znak wodny. Licencja usuwa znak wodny i odblokowuje pełną funkcjonalność. |

## Pro tips

* **Przetwarzanie wsadowe:** Umieść logikę wczytywania i zapisywania w metodzie przyjmującej ścieżki wejścia i wyjścia. Ułatwi to przetwarzanie dziesiątek dokumentów w pętli.  
* **Wydajność:** Ponownie używaj jednej instancji `Document` przy modyfikacji wielu wykresów w tym samym pliku, aby uniknąć wielokrotnego I/O.  
* **Testowanie:** Zweryfikuj zmiany etykiet, automatyzując porównanie wizualne (np. przy użyciu bezgłowego podglądu Word), jeśli musisz asertywnie sprawdzać wynik w pipeline CI.

## Next steps

Teraz, gdy opanowałeś podstawy **samouczka edycji etykiet wykresu**, rozważ dalsze eksploracje:

* **Change chart label position** dla innych serii lub różnych typów wykresów  
* **Customize chart data label** – formatowanie liczb, kolory czcionek lub wypełnienia tła  
* **Hide chart category name** przy jednoczesnym wyświetlaniu nazwy serii w wykresach wieloseriiowych  
* **Show chart label value** razem z wartościami procentowymi w wykresach kołowych  

Te tematy pogłębią Twoją kontrolę nad estetyką wykresów w Wordzie i przygotują Cię do zaawansowanych scenariuszy raportowych.

---

*Miłego kodowania! Jeśli ten samouczek okazał się przydatny, podziel się nim z zespołem lub przyczyń się do ulepszeń na GitHubie.*

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}