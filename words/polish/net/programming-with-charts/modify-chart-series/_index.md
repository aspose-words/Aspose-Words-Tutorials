---
title: Aktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words for .NET
weight: 610
limit:
description: Naucz się modyfikować punkty danych serii wykresu w dokumencie Word i odświeżać wykres przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naucz się modyfikować punkty danych serii wykresu w dokumencie Word
    i odświeżać wykres przy użyciu Aspose.Words for .NET.
  headline: Aktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words
    for .NET
  type: TechArticle
- description: Naucz się modyfikować punkty danych serii wykresu w dokumencie Word
    i odświeżać wykres przy użyciu Aspose.Words for .NET.
  name: Aktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words for
    .NET
  steps:
  - name: Utwórz nowy Document, wstaw wykres słupkowy przy użyciu DocumentBuilder
      i zapisz go jako plik początkowy.
    text: Utwórz nowy Document, wstaw wykres słupkowy przy użyciu DocumentBuilder
      i zapisz go jako plik początkowy.
  - name: Otwórz zapisany plik i zlokalizuj kształt wykresu, aby uzyskać istniejący
      obiekt Chart.
    text: Otwórz zapisany plik i zlokalizuj kształt wykresu, aby uzyskać istniejący
      obiekt Chart.
  - name: Wyczyść wartości pierwszej serii i dodaj nowe punkty, a następnie dostosuj
      drugą serię, usuwając jej pierwszy punkt i dodając nowy.
    text: Wyczyść wartości pierwszej serii i dodaj nowe punkty, a następnie dostosuj
      drugą serię, usuwając jej pierwszy punkt i dodając nowy.
  - name: Zapisz zmodyfikowany dokument do nowego pliku zawierającego zaktualizowany
      wykres.
    text: Zapisz zmodyfikowany dokument do nowego pliku zawierającego zaktualizowany
      wykres.
  type: HowTo
- questions:
  - answer: Użyj `document.GetChildNodes(NodeType.Shape, true)`, aby pobrać wszystkie
      kształty, a następnie przefiltruj je za pomocą `s.HasChart` i wybierz pierwszy
      (lub ten, którego potrzebujesz) – to zapobiega wybieraniu niepowiązanych obrazów
      lub pól tekstowych.
    question: Jak mogę niezawodnie zlokalizować kształt wykresu w dokumencie, który
      może zawierać inne kształty?
  - answer: '`ClearValues()` usuwa istniejące punkty danych; bez tego nowe punkty
      są dopisywane do starych, co może powodować duplikaty kategorii lub nieprawidłowe
      sumy.'
    question: Dlaczego muszę wywołać `ClearValues()` przed dodaniem nowych punktów
      do serii?
  - answer: Użyj `FromString`, gdy kategorie osi X wykresu są tekstowe (np. "Group
      A"), oraz `FromDouble`, gdy oś oczekuje wartości liczbowych, takich jak daty
      lub pomiary.
    question: Kiedy powinienem używać `ChartXValue.FromString` zamiast `ChartXValue.FromDouble`
      dla wartości osi X?
  - answer: Próba uzyskania dostępu do nieistniejącej serii powoduje wyrzucenie `ArgumentOutOfRangeException`;
      zawsze sprawdzaj `existingChart.Series.Count` przed odwołaniem się do konkretnego
      indeksu.
    question: Co się stanie, jeśli wykres ma tylko jedną serię i spróbuję uzyskać
      dostęp do `existingChart.Series[1]`?
  - answer: Zapisanie `openedDoc` jest wystarczające, ponieważ jest to instancja dokumentu
      zawierająca zmodyfikowany wykres; oryginalny `document` został użyty jedynie
      do stworzenia początkowego pliku.
    question: Czy muszę ponownie zapisać oryginalny `document` po modyfikacji wykresu,
      czy zapisanie `openedDoc` jest wystarczające?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Edytuj dane serii wykresu w Wordzie
og_description: Przewodnik krok po kroku, jak zmienić wartości serii wykresu w pliku Word przy użyciu Aspose.Words for .NET.
og_image_alt: Poradnik pokazujący dokument Word z wykresem słupkowym przed i po zaktualizowaniu danych serii przy użyciu Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak utworzyć dokument Word zawierający wykres słupkowy, następnie ponownie otworzyć plik, pobrać istniejące serie wykresu, zmodyfikować ich punkty danych i zapisać dokument, aby wykres wyświetlał nowe wartości. Postępuj zgodnie z kodem krok po kroku, aby zobaczyć, jak proste jest programowe dostosowanie danych wykresu przy użyciu Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: Jak mogę niezawodnie zlokalizować kształt wykresu w dokumencie, który może zawierać inne kształty?**  
A: Użyj `document.GetChildNodes(NodeType.Shape, true)`, aby pobrać wszystkie kształty, a następnie przefiltruj je za pomocą `s.HasChart` i wybierz pierwszy (lub ten, którego potrzebujesz) – to zapobiega wybieraniu niepowiązanych obrazów lub pól tekstowych.

**Q: Dlaczego muszę wywołać `ClearValues()` przed dodaniem nowych punktów do serii?**  
A: `ClearValues()` usuwa istniejące punkty danych; bez tego nowe punkty są dopisywane do starych, co może powodować duplikaty kategorii lub nieprawidłowe sumy.

**Q: Kiedy powinienem używać `ChartXValue.FromString` zamiast `ChartXValue.FromDouble` dla wartości osi X?**  
A: Użyj `FromString`, gdy kategorie osi X wykresu są tekstowe (np. "Group A"), oraz `FromDouble`, gdy oś oczekuje wartości liczbowych, takich jak daty lub pomiary.

**Q: Co się stanie, jeśli wykres ma tylko jedną serię i spróbuję uzyskać dostęp do `existingChart.Series[1]`?**  
A: Próba uzyskania dostępu do nieistniejącej serii powoduje wyrzucenie `ArgumentOutOfRangeException`; zawsze sprawdzaj `existingChart.Series.Count` przed odwołaniem się do konkretnego indeksu.

**Q: Czy muszę ponownie zapisać oryginalny `document` po modyfikacji wykresu, czy zapisanie `openedDoc` jest wystarczające?**  
A: Zapisanie `openedDoc` jest wystarczające, ponieważ jest to instancja dokumentu zawierająca zmodyfikowany wykres; oryginalny `document` został użyty jedynie do stworzenia początkowego pliku.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}