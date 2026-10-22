---
title: Ustaw jednolite etykiety danych w wykresie słupkowym przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Naucz się tworzyć wykres słupkowy w Wordzie i stosować jednolity rozmiar czcionki oraz kolor etykiet danych we wszystkich seriach przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naucz się tworzyć wykres słupkowy w Wordzie i stosować jednolity rozmiar
    czcionki oraz kolor etykiet danych we wszystkich seriach przy użyciu Aspose.Words
    for .NET.
  headline: Ustaw jednolite etykiety danych w wykresie słupkowym przy użyciu Aspose.Words
    for .NET
  type: TechArticle
- description: Naucz się tworzyć wykres słupkowy w Wordzie i stosować jednolity rozmiar
    czcionki oraz kolor etykiet danych we wszystkich seriach przy użyciu Aspose.Words
    for .NET.
  name: Ustaw jednolite etykiety danych w wykresie słupkowym przy użyciu Aspose.Words
    for .NET
  steps:
  - name: Utwórz nowy pusty dokument Word oraz obiekt DocumentBuilder do jego edycji.
    text: Utwórz nowy pusty dokument Word oraz obiekt DocumentBuilder do jego edycji.
  - name: Wstaw wykres słupkowy o wymiarach 500×300 do dokumentu i pobierz jego obiekt
      Chart.
    text: Wstaw wykres słupkowy o wymiarach 500×300 do dokumentu i pobierz jego obiekt
      Chart.
  - name: Usuń domyślną przykładową serię, którą Aspose.Words dodaje do nowego wykresu.
    text: Usuń domyślną przykładową serię, którą Aspose.Words dodaje do nowego wykresu.
  - name: Zdefiniuj etykiety kategorii i dodaj dwie serie danych (Item Alpha i Item
      Beta) wraz z ich wartościami do wykresu.
    text: Zdefiniuj etykiety kategorii i dodaj dwie serie danych (Item Alpha i Item
      Beta) wraz z ich wartościami do wykresu.
  - name: Ustaw podstawowy rozmiar czcionki i kolor, które zostaną zastosowane do
      wszystkich etykiet danych.
    text: Ustaw podstawowy rozmiar czcionki i kolor, które zostaną zastosowane do
      wszystkich etykiet danych.
  - name: Włącz etykiety danych dla każdej serii, wyświetl wartość liczbową i zastosuj
      wcześniej określony rozmiar czcionki oraz kolor.
    text: Włącz etykiety danych dla każdej serii, wyświetl wartość liczbową i zastosuj
      wcześniej określony rozmiar czcionki oraz kolor.
  - name: Zapisz dokument jako plik .docx.
    text: Zapisz dokument jako plik .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` tworzy wykres z domyślną przykładową serią; jej usunięcie
      usuwa ten placeholder, dzięki czemu wykres wyświetla tylko serie, które dodasz
      (`Item Alpha` i `Item Beta`).'
    question: Dlaczego muszę wywołać `chart.Series.Clear()` przed dodaniem własnych
      serii?
  - answer: Zastąp `Color.White` dowolną wartością `System.Drawing.Color`, np. `Color.Black`
      lub `Color.FromArgb(255, 30, 144, 255)`; nowy kolor jest stosowany poprzez `series.DataLabels.Font.Color`
      wewnątrz pętli.
    question: Jak mogę zmienić kolor etykiety danych na inny niż biały?
  - answer: Etykiety danych zostaną ukryte, więc zastosowane ustawienia czcionki będą
      niewidoczne; musisz pozostawić `HasDataLabels` ustawione na `true`, aby etykiety
      (i ich styl) były wyświetlane.
    question: Co się stanie, jeśli ustawiam `series.HasDataLabels = false` po skonfigurowaniu
      rozmiaru czcionki i koloru?
  - answer: Tak — każda `ChartSeries` ma własny obiekt `DataLabels`, więc każda seria
      dodana po początkowej pętli musi również mieć ustawione `HasDataLabels`, `ShowValue`
      oraz właściwości czcionki, co można zrobić ponownie iterując pętlą lub wydzielając
      stylizację do metody pomocniczej.
    question: Czy muszę ponownie przejść pętlą po seriach, jeśli później w kodzie
      dodam kolejną serię?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Zastosuj jednolite etykiety danych w wykresie Word
og_description: Szybko nadaj wszystkim etykietom wykresu ten sam rozmiar czcionki i kolor przy użyciu Aspose.Words for .NET.
og_image_alt: Poradnik przedstawiający dokument Word z wykresem słupkowym, w którym wszystkie etykiety danych mają ten sam rozmiar czcionki i kolor, utworzony przy użyciu Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw jednolite etykiety danych w wykresie słupkowym przy użyciu Aspose.Words
Ten samouczek pokazuje, jak wygenerować dokument Word, wstawić wykres słupkowy i dodać własne serie danych przy użyciu Aspose.Words for .NET. Następnie demonstruje, jak zdefiniować domyślny rozmiar czcionki i kolor etykiet danych, aby każda seria w wykresie wyświetlała identyczne etykiety. Stosując jeden styl, zapewniasz spójny wygląd wizualny całego wykresu.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Dlaczego muszę wywołać `chart.Series.Clear()` przed dodaniem własnych serii?**  
A: `InsertChart` tworzy wykres z domyślną przykładową serią; jej usunięcie usuwa ten placeholder, dzięki czemu wykres wyświetla tylko serie, które dodasz (`Item Alpha` i `Item Beta`).

**Q: Jak mogę zmienić kolor etykiety danych na inny niż biały?**  
A: Zastąp `Color.White` dowolną wartością `System.Drawing.Color`, np. `Color.Black` lub `Color.FromArgb(255, 30, 144, 255)`; nowy kolor jest stosowany poprzez `series.DataLabels.Font.Color` wewnątrz pętli.

**Q: Co się stanie, jeśli ustawiam `series.HasDataLabels = false` po skonfigurowaniu rozmiaru czcionki i koloru?**  
A: Etykiety danych zostaną ukryte, więc zastosowane ustawienia czcionki będą niewidoczne; musisz pozostawić `HasDataLabels` ustawione na `true`, aby etykiety (i ich styl) były wyświetlane.

**Q: Czy muszę ponownie przejść pętlą po seriach, jeśli później w kodzie dodam kolejną serię?**  
A: Tak — każda `ChartSeries` ma własny obiekt `DataLabels`, więc każda seria dodana po początkowej pętli musi również mieć ustawione `HasDataLabels`, `ShowValue` oraz właściwości czcionki, co można zrobić ponownie iterując pętlą lub wydzielając stylizację do metody pomocniczej.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}