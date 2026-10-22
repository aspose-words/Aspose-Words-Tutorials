---
title: Aktualizuj tytuł wykresu i przełącz widoczność legendy w Wordzie przy użyciu Aspose.Words for .NET
weight: 810
limit:
description: Dowiedz się, jak zmienić tytuł wykresu i kontrolować widoczność legendy w dokumencie Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Dowiedz się, jak zmienić tytuł wykresu i kontrolować widoczność legendy
    w dokumencie Word przy użyciu Aspose.Words for .NET.
  headline: Aktualizuj tytuł wykresu i przełącz widoczność legendy w Wordzie przy
    użyciu Aspose.Words for .NET
  type: TechArticle
- description: Dowiedz się, jak zmienić tytuł wykresu i kontrolować widoczność legendy
    w dokumencie Word przy użyciu Aspose.Words for .NET.
  name: Aktualizuj tytuł wykresu i przełącz widoczność legendy w Wordzie przy użyciu
    Aspose.Words for .NET
  steps:
  - name: Zdefiniuj tytuł wykresu podany przez użytkownika oraz określ, czy legenda
      ma być wyświetlana.
    text: Zdefiniuj tytuł wykresu podany przez użytkownika oraz określ, czy legenda
      ma być wyświetlana.
  - name: Utwórz nowy dokument Word oraz obiekt DocumentBuilder do dodawania treści.
    text: Utwórz nowy dokument Word oraz obiekt DocumentBuilder do dodawania treści.
  - name: Wstaw wykres kolumnowy o wymiarach 432 × 252 pt do dokumentu i sprawdź,
      czy kształt rzeczywiście zawiera wykres.
    text: Wstaw wykres kolumnowy o wymiarach 432 × 252 pt do dokumentu i sprawdź,
      czy kształt rzeczywiście zawiera wykres.
  - name: Pobierz obiekt wykresu, ustaw jego tekst tytułu na wartość podaną przez
      użytkownika i upewnij się, że tytuł jest wyświetlany.
    text: Pobierz obiekt wykresu, ustaw jego tekst tytułu na wartość podaną przez
      użytkownika i upewnij się, że tytuł jest wyświetlany.
  - name: 'Skonfiguruj legendę: wyświetl ją po prawej stronie, jeśli jest to żądane,
      w przeciwnym razie ukryj ją oraz zezwól na nakładanie się legendy na obszar
      wykresu.'
    text: 'Skonfiguruj legendę: wyświetl ją po prawej stronie, jeśli jest to żądane,
      w przeciwnym razie ukryj ją oraz zezwól na nakładanie się legendy na obszar
      wykresu.'
  - name: Zapisz zmodyfikowany dokument na dysku jako CustomChart.docx.
    text: Zapisz zmodyfikowany dokument na dysku jako CustomChart.docx.
  type: HowTo
- questions:
  - answer: Gdy `displayLegend` jest ustawione na `true`, kod ustawia `chartLegend.Position`
      na `LegendPosition.Right`, co powoduje wyświetlenie legendy po prawej stronie
      obszaru wykresu; właściwość `Overlay` pozostaje `true`, więc legenda może nakładać
      się na wykres, oszczędzając miejsce.
    question: Co zmienia ustawienie `displayLegend` na `true` w wygenerowanym wykresie?
  - answer: Ustaw `chartTitle.Show = false` (lub po prostu nie ustawiaj `Show` na
      `true`) po przypisaniu `chartTitle.Text`; tytuł nie zostanie wyrenderowany w
      dokumencie Word.
    question: Jak ukryć tytuł wykresu, jeśli użytkownik go nie poda?
  - answer: Tak — `InsertChart` zwraca obiekt `Shape`, który powinien zawierać wykres,
      ale weryfikacja `HasChart` zapewnia, że kształt faktycznie posiada obiekt `Chart`;
      w przeciwnym razie kod zgłasza `InvalidOperationException`.
    question: Czy po wywołaniu `InsertChart` konieczne jest sprawdzenie `chartContainer.HasChart`?
  - answer: Oczywiście; przypisz dowolną wartość z wyliczenia `LegendPosition` (np.
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) do `chartLegend.Position`,
      aby przemieścić legendę w wybrane miejsce.
    question: Czy mogę umieścić legendę w innym miejscu niż po prawej stronie?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Zmień tytuł wykresu i legendę w Wordzie
og_description: Naucz się ustawiać własny tytuł wykresu i kontrolować wyświetlanie legendy w dokumencie Word przy użyciu Aspose.Words for .NET.
og_image_alt: Poradnik prezentujący kod, który aktualizuje tytuł wykresu i przełącza legendę w dokumencie Word przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktualizuj tytuł wykresu i przełącz widoczność legendy w Wordzie przy użyciu Aspose.Words
Ten samouczek pokazuje, jak programowo modyfikować wykres w dokumencie Word przy użyciu Aspose.Words for .NET. Nauczysz się wstawiać wykres kolumnowy, zamieniać jego tytuł na tekst dostarczony przez użytkownika oraz kontrolować widoczność i nakładanie legendy w zależności od preferencji użytkownika. Te kroki pozwalają dynamicznie dostosowywać prezentację wykresu bez ręcznej edycji.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Co zmienia ustawienie `displayLegend` na `true` w wygenerowanym wykresie?**  
A: Gdy `displayLegend` jest ustawione na `true`, kod ustawia `chartLegend.Position` na `LegendPosition.Right`, co powoduje wyświetlenie legendy po prawej stronie obszaru wykresu; właściwość `Overlay` pozostaje `true`, więc legenda może nakładać się na wykres, oszczędzając miejsce.

**Q: Jak ukryć tytuł wykresu, jeśli użytkownik go nie poda?**  
A: Ustaw `chartTitle.Show = false` (lub po prostu nie ustawiaj `Show` na `true`) po przypisaniu `chartTitle.Text`; tytuł nie zostanie wyrenderowany w dokumencie Word.

**Q: Czy po wywołaniu `InsertChart` konieczne jest sprawdzenie `chartContainer.HasChart`?**  
A: Tak — `InsertChart` zwraca obiekt `Shape`, który powinien zawierać wykres, ale weryfikacja `HasChart` zapewnia, że kształt faktycznie posiada obiekt `Chart`; w przeciwnym razie kod zgłasza `InvalidOperationException`.

**Q: Czy mogę umieścić legendę w innym miejscu niż po prawej stronie?**  
A: Oczywiście; przypisz dowolną wartość z wyliczenia `LegendPosition` (np. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) do `chartLegend.Position`, aby przemieścić legendę w wybrane miejsce.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}