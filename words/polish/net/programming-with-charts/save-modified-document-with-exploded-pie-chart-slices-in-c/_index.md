---
category: general
date: 2026-10-13
description: 'Zapisz zmodyfikowany dokument po dostosowaniu wykresu kołowego: rozdzielenie
  fragmentów, zmiana kąta pierwszego fragmentu oraz wyświetlenie etykiet procentowych
  w C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: pl
lastmod: 2026-10-13
og_description: Zapisz zmodyfikowany dokument po dostosowaniu wykresu kołowego w C#.
  Dowiedz się, jak wyodrębnić fragmenty wykresu kołowego, zmienić kąt pierwszego fragmentu
  i wyświetlić etykiety procentowe.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Zapisz zmodyfikowany dokument z wyodrębnionymi fragmentami wykresu kołowego
  – przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Zapisz zmodyfikowany dokument z wyodrębnionymi fragmentami wykresu kołowego
  w C#
url: /pl/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisz zmodyfikowany dokument z wybuchniętymi kawałkami wykresu kołowego w C#

Jeśli potrzebujesz **save modified document** po dostosowaniu wykresu kołowego w Wordzie, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Nauczysz się wybuchać kawałki wykresu kołowego, zmienić kąt pierwszego kawałka oraz wyświetlić etykiety procentowe — wszystko przy kilku linijkach kodu C#.

Dostosowywanie wykresów jest powszechnym wymogiem przy programowym generowaniu raportów, faktur lub pulpitów nawigacyjnych. Po zakończeniu tego samouczka będziesz w stanie wczytać plik DOCX, zmodyfikować wygląd wykresu i **save modified document** gotowy do dystrybucji.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 lub nowszy (bezpłatna wersja próbna lub licencjonowana kopia)
- Plik Word (`input.docx`) zawierający pojedynczy wykres kołowy
- Visual Studio 2022 lub dowolne IDE C#

> **Wskazówka:** Pakiet NuGet Aspose.Words dodaje się poleceniem `dotnet add package Aspose.Words`.

## Krok 1: Wczytaj dokument Word zawierający wykres

Pierwszym krokiem jest otwarcie źródłowego pliku DOCX. Klasa `Document` reprezentuje cały plik Word w pamięci.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Wczytanie dokumentu daje pełny dostęp do każdego węzła, w tym kształtów zawierających wykresy.

## Krok 2: Pobierz pierwszy kształt wykresu z dokumentu

Wykresy są przechowywane wewnątrz węzłów `Shape`. Możesz zlokalizować pierwszy wykres przy pomocy `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Jeśli dokument zawiera wiele wykresów, dostosuj indeks (`0`) lub iteruj po kolekcji. Ta linia zapewnia, że masz referencję do obiektu `Chart`, który będziesz modyfikować.

## Krok 3: Wybuchnij kawałki wykresu kołowego

Wybuchnięcie kawałka oddziela go od reszty koła, co ułatwia odczyt wykresu. Właściwość `Explode` działa na całą serię.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Ustawienie `Explode` na `true` **explodes pie chart slices** dla całej serii, co jest przydatne, gdy chcesz, aby każdy kawałek się wyróżniał.

## Krok 4: Zmień kąt pierwszego kawałka

Czasami potrzebujesz, aby pierwszy kawałek zaczynał się pod niestandardowym kątem, na przykład aby dopasować go do wytycznych projektowych.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Właściwość `FirstSliceAngle` **changes first slice** orientację, obracając całe koło tak, aby pierwszy kawałek zaczynał się od 30 stopni.

## Krok 5: Pokaż etykiety procentowe na kawałkach wykresu kołowego

Wyświetlanie liczbowego udziału każdego kawałka jest często wymagane w raportach. Flaga `DataLabel.ShowPercentage` włącza wartości procentowe.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Ten krok **show percentage labels** bezpośrednio na wykresie, co również spełnia wymóg **display percentages pie**.

## Krok 6: Zapisz zmodyfikowany dokument

Po zastosowaniu wszystkich modyfikacji, zachowaj zmiany w nowym pliku. Metoda `Save` zapisuje zaktualizowany DOCX na dysku.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Teraz masz **save modified document**, które zawiera wybuchnięty wykres kołowy, obrócony pierwszy kawałek i widoczne etykiety procentowe.

![Zapisz zmodyfikowany dokument pokazujący wybuchnięty wykres kołowy](/images/pie-chart-exploded.png "Zapisz zmodyfikowany dokument z wybuchniętymi kawałkami wykresu kołowego i etykietami procentowymi")

*Zrzut ekranu ilustruje ostateczny wynik po zapisaniu dokumentu.*

## Pełny, działający przykład

Łącząc wszystkie elementy, oto kompletny program, który możesz skopiować i wkleić do projektu konsolowego:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Oczekiwany wynik

Otwarcie `output.docx` wyświetli wykres kołowy, w którym:

- Każdy kawałek jest lekko oddzielony (**exploded pie chart slices**)
- Pierwszy kawałek zaczyna się z przesunięciem 30 stopni (**change first slice**)
- Każdy kawałek pokazuje swój udział jako procent (**show percentage labels**, **display percentages pie**)
- Plik został **save modified document** bez modyfikacji oryginału.

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|--------|
| **Co jeśli dokument nie zawiera wykresu?** | Kod sprawdza `null` po wywołaniu `GetChild`. Jeśli wykres nie istnieje, możesz go dodać programowo lub przerwać działanie z wyraźnym komunikatem. |
| **Czy mogę wybuchnąć tylko pojedynczy kawałek?** | Tak. Użyj `chart.PieChart.Series[0].DataPoints[i].Explosion = true;`, gdzie `i` jest indeksem kawałka. |
| **Jak zmienić format etykiety (np. wyświetlić wartość + %)?** | Ustaw `chart.PieChart.DataLabel.ShowValue = true;` i opcjonalnie `chart.PieChart.DataLabel.ShowPercentage = true;`, aby połączyć oba. |
| **Czy styl wykresu jest zachowany po zapisaniu?** | Aspose.Words zachowuje wszystkie style, w tym kolory i czcionki, gdy wykonujesz **save modified document**. |
| **Czy mogę przetwarzać wiele wykresów w tym samym pliku?** | Iteruj po wszystkich węzłach `Shape` przy użyciu `NodeType.Shape` i filtruj po `shape.HasChart`. Zastosuj te same kroki do każdego wykresu. |

## Zakończenie

Teraz wiesz, jak **save modified document** po programowym dostosowaniu wykresu kołowego w Wordzie. Poradnik obejmował wybuchnięcie kawałków wykresu kołowego, zmianę kąta pierwszego kawałka oraz wyświetlanie etykiet procentowych — spełniając wymagania **show percentage labels**, **explode pie chart slices**, **display percentages pie** i **change first slice**.

Następnie rozważ:

- Dodawanie serii danych dynamicznie (`chart.Series.Add(...)`)  
- Dostosowywanie położenia legendy i tytułów wykresu  
- Konwertowanie DOCX na PDF przy zachowaniu stylu wykresu  

Śmiało eksperymentuj z różnymi kątami, ustawieniami wybuchu lub formatami etykiet, aby dopasować je do potrzeb raportowania. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak zapisać edytowany dokument w C# z Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Wstaw wykres kolumnowy w dokumencie Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}