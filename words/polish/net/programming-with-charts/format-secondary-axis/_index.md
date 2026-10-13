---
title: Formatuj drugą oś Y jako walutę w wykresie Word przy użyciu Aspose.Words for .NET
weight: 710
limit:
description: Dowiedz się, jak dodać i sformatować drugą oś Y jako walutę w wykresie liniowym Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Dowiedz się, jak dodać i sformatować drugą oś Y jako walutę w wykresie
    liniowym Word przy użyciu Aspose.Words for .NET.
  headline: Formatuj drugą oś Y jako walutę w wykresie Word przy użyciu Aspose.Words
    for .NET
  type: TechArticle
- description: Dowiedz się, jak dodać i sformatować drugą oś Y jako walutę w wykresie
    liniowym Word przy użyciu Aspose.Words for .NET.
  name: Formatuj drugą oś Y jako walutę w wykresie Word przy użyciu Aspose.Words for
    .NET
  steps:
  - name: Utwórz nowy pusty dokument Word oraz obiekt DocumentBuilder do jego edycji.
    text: Utwórz nowy pusty dokument Word oraz obiekt DocumentBuilder do jego edycji.
  - name: Wstaw wykres liniowy o rozmiarze 450×250 punktów do dokumentu i pobierz
      jego obiekt Chart.
    text: Wstaw wykres liniowy o rozmiarze 450×250 punktów do dokumentu i pobierz
      jego obiekt Chart.
  - name: Usuń domyślną serię zastępczą, którą Aspose dodaje do nowego wykresu.
    text: Usuń domyślną serię zastępczą, którą Aspose dodaje do nowego wykresu.
  - name: Zdefiniuj etykiety kwartałów i dodaj główną serię danych z przykładowymi
      wartościami do wykresu.
    text: Zdefiniuj etykiety kwartałów i dodaj główną serię danych z przykładowymi
      wartościami do wykresu.
  - name: Utwórz drugą grupę serii typu Line i przypisz ją do grupy osi drugorzędnej.
    text: Utwórz drugą grupę serii typu Line i przypisz ją do grupy osi drugorzędnej.
  - name: Ukryj drugą oś X, aby widoczna była tylko druga oś Y.
    text: Ukryj drugą oś X, aby widoczna była tylko druga oś Y.
  - name: Pokaż tytuł drugiej osi Y i ustaw jego tekst na "Sales (USD)".
    text: Pokaż tytuł drugiej osi Y i ustaw jego tekst na "Sales (USD)".
  - name: Ustaw format liczbowy drugiej osi Y na wzorzec walutowy z dwoma miejscami
      po przecinku i odłącz go od formatowania źródła.
    text: Ustaw format liczbowy drugiej osi Y na wzorzec walutowy z dwoma miejscami
      po przecinku i odłącz go od formatowania źródła.
  - name: Dodaj pomocniczą serię do grupy drugorzędnej, dostarczając dane, które będą
      wykreślone względem drugiej osi Y.
    text: Dodaj pomocniczą serię do grupy drugorzędnej, dostarczając dane, które będą
      wykreślone względem drugiej osi Y.
  - name: Zapisz gotowy dokument do pliku o nazwie ProfitChart.docx w bieżącym katalogu.
    text: Zapisz gotowy dokument do pliku o nazwie ProfitChart.docx w bieżącym katalogu.
  type: HowTo
- questions:
  - answer: Wykres zachowa domyślną serię zastępczą, którą wstawia Aspose.Words, więc
      Twoja niestandardowa "Main Series" pojawi się obok niechcianych punktów danych.
    question: Co się stanie, jeśli pominę wywołanie `lineChart.Series.Clear()`?
  - answer: Ustaw `secondarySeriesGroup.AxisX.Hidden = false;` (lub po prostu pomiń
      linię, która ustawia ją na `true`).
    question: Jak mogę wyświetlić drugą oś X zamiast ją ukrywać?
  - answer: Tak – zmień ciąg formatu, np. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"€#,##0.00\";` dla euro lub dostosuj wzorzec do swojego regionu.
    question: Czy mogę użyć innego symbolu waluty lub formatu dla drugiej osi Y?
  - answer: Gdy `IsLinkedToSource` jest ustawione na true, oś dziedziczy format liczbowy
      z podstawowego źródła danych, nadpisując wszelkie własne `FormatCode`; ustawienie
      go na false wymusza użycie podanego przez Ciebie formatu.
    question: Dlaczego muszę ustawić `IsLinkedToSource = false` przy stosowaniu własnego
      formatu liczbowego?
  - answer: Tak, przypisz `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (lub `Right` dla domyślnego) aby kontrolować, po której stronie oś jest rysowana.
    question: Czy można przenieść drugą oś Y na lewą stronę wykresu?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatuj drugą oś wykresu jako walutę
og_description: Dowiedz się, jak dodać drugą oś Y do wykresu liniowego Word i stylizować ją jako walutę z dwoma miejscami po przecinku.
og_image_alt: Zrzut ekranu przedstawiający wykres liniowy Word z drugą osią Y sformatowaną jako waluta przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatuj drugą oś Y jako walutę w wykresie Word przy użyciu Aspose.Words
W tym samouczku zobaczysz, jak zbudować dokument Word, wstawić wykres liniowy, dodać drugą oś Y, sformatować tę oś jako walutę z dwoma miejscami po przecinku oraz powiązać z nią drugą serię danych przy użyciu Aspose.Words for .NET. Formatowanie drugiej osi jako waluty pozwala wyraźnie przedstawić dane finansowe obok serii głównej. Postępuj zgodnie z kodem krok po kroku, aby zobaczyć wykres renderowany bezpośrednio w wygenerowanym dokumencie.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Co się stanie, jeśli pominę wywołanie `lineChart.Series.Clear()`?**  
A: Wykres zachowa domyślną serię zastępczą, którą wstawia Aspose.Words, więc Twoja niestandardowa "Main Series" pojawi się obok niechcianych punktów danych.

**Q: Jak mogę wyświetlić drugą oś X zamiast ją ukrywać?**  
A: Ustaw `secondarySeriesGroup.AxisX.Hidden = false;` (lub po prostu pomiń linię, która ustawia ją na `true`).

**Q: Czy mogę użyć innego symbolu waluty lub formatu dla drugiej osi Y?**  
A: Tak – zmień ciąg formatu, np. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"€#,##0.00\";` dla euro lub dostosuj wzorzec do swojego regionu.

**Q: Dlaczego muszę ustawić `IsLinkedToSource = false` przy stosowaniu własnego formatu liczbowego?**  
A: Gdy `IsLinkedToSource` jest ustawione na true, oś dziedziczy format liczbowy z podstawowego źródła danych, nadpisując wszelkie własne `FormatCode`; ustawienie go na false wymusza użycie podanego przez Ciebie formatu.

**Q: Czy można przenieść drugą oś Y na lewą stronę wykresu?**  
A: Tak, przypisz `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (lub `Right` dla domyślnego) aby kontrolować, po której stronie oś jest rysowana.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}