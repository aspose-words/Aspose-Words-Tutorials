---
title: Formatuj drugą oś X i ustaw jednostki wyświetlania na tysiące w wykresach liniowych Word przy użyciu Aspose.Words dla .NET
weight: 710
limit:
description: Utwórz wykres liniowy w Word, dodaj drugą oś X, ustaw jej jednostkę wyświetlania na tysiące i zastosuj niestandardowy format liczbowy przy użyciu Aspose.Words dla .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Utwórz wykres liniowy w Word, dodaj drugą oś X, ustaw jej jednostkę
    wyświetlania na tysiące i zastosuj niestandardowy format liczbowy przy użyciu
    Aspose.Words dla .NET.
  headline: Formatuj drugą oś X i ustaw jednostki wyświetlania na tysiące w wykresach
    liniowych Word przy użyciu Aspose.Words dla .NET
  type: TechArticle
- description: Utwórz wykres liniowy w Word, dodaj drugą oś X, ustaw jej jednostkę
    wyświetlania na tysiące i zastosuj niestandardowy format liczbowy przy użyciu
    Aspose.Words dla .NET.
  name: Formatuj drugą oś X i ustaw jednostki wyświetlania na tysiące w wykresach
    liniowych Word przy użyciu Aspose.Words dla .NET
  steps:
  - name: Utwórz nowy obiekt Document oraz DocumentBuilder, aby rozpocząć budowanie
      pliku Word.
    text: Utwórz nowy obiekt Document oraz DocumentBuilder, aby rozpocząć budowanie
      pliku Word.
  - name: Wstaw wykres liniowy o rozmiarze 500×300 do dokumentu i uzyskaj obiekt Chart.
    text: Wstaw wykres liniowy o rozmiarze 500×300 do dokumentu i uzyskaj obiekt Chart.
  - name: Usuń domyślną serię demonstracyjną, którą Aspose.Words dodaje automatycznie.
    text: Usuń domyślną serię demonstracyjną, którą Aspose.Words dodaje automatycznie.
  - name: Zdefiniuj tablicę etykiet kategorii, które będą użyte na osi X.
    text: Zdefiniuj tablicę etykiet kategorii, które będą użyte na osi X.
  - name: Dodaj główną serię danych o nazwie "Main Data", używając etykiet i wartości.
    text: Dodaj główną serię danych o nazwie "Main Data", używając etykiet i wartości.
  - name: Utwórz drugą grupę serii typu Line i przypisz ją do grupy osi drugorzędnej.
    text: Utwórz drugą grupę serii typu Line i przypisz ją do grupy osi drugorzędnej.
  - name: Ustaw jednostkę wyświetlania drugiej osi X na tysiące, aby wartości były
      wyświetlane w K.
    text: Ustaw jednostkę wyświetlania drugiej osi X na tysiące, aby wartości były
      wyświetlane w K.
  - name: Zastosuj niestandardowy format liczbowy "#,##0.0" do etykiet znaczników
      drugiej osi X.
    text: Zastosuj niestandardowy format liczbowy "#,##0.0" do etykiet znaczników
      drugiej osi X.
  - name: Opcjonalnie dodaj pomocniczą serię danych do drugiej grupy.
    text: Opcjonalnie dodaj pomocniczą serię danych do drugiej grupy.
  - name: Zapisz dokument jako plik .docx.
    text: Zapisz dokument jako plik .docx.
  type: HowTo
- questions:
  - answer: Nie – ustawienia `AxisX` należą do `ChartSeriesGroup`, więc możesz ustawić
      `secondaryGroup.AxisX.DisplayUnit.Unit` i `secondaryGroup.AxisX.NumberFormat.FormatCode`
      przed lub po dodaniu serii; konfiguracja zostanie zastosowana do osi grupy w
      obu przypadkach.
    question: Czy muszę dodać drugą serię przed ustawieniem jednostki wyświetlania
      i formatu liczbowego na drugiej osi X?
  - answer: Tak – przypisz dowolną wartość `AxisBuiltInUnit`, np. `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;`, aby wyświetlać wartości osi w milionach zamiast
      w tysiącach.
    question: Czy mogę użyć innej wbudowanej jednostki, np. milionów, dla drugiej
      osi X?
  - answer: Nie – kod formatu jest stosowany tylko do osi, którą modyfikujesz (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      więc pierwsza oś X zachowuje domyślne formatowanie.
    question: Czy niestandardowy format "#,##0.0" wpłynie na etykiety pierwszej osi
      X?
  - answer: Wykres będzie zawierał domyślną serię demonstracyjną oprócz dodanych przez
      Ciebie, co może spowodować dodatkowe linie i niezgodne kategorie; wyczyszczenie
      kolekcji zapewnia, że pojawią się tylko zamierzone dane.
    question: Co się stanie, jeśli zapomnę wyczyścić serię demonstracyjną za pomocą
      `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatuj drugą oś X i ustaw jednostki na tysiące
og_description: Dodaj drugą oś X do wykresu liniowego w Word i sformatuj jej etykiety w tysiącach przy użyciu niestandardowego wzoru.
og_image_alt: Poradnik pokazujący, jak dodać drugą oś X do wykresu liniowego w Word i sformatować jej etykiety, aby wyświetlały jednostki w tysiącach, przy użyciu Aspose.Words dla .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatuj drugą oś X i ustaw jednostki wyświetlania na tysiące w wykresach liniowych Word przy użyciu Aspose.Words dla .NET
Ten samouczek przeprowadza Cię krok po kroku przez tworzenie dokumentu Word zawierającego wykres liniowy, dodawanie drugiej osi X oraz konfigurowanie tej osi tak, aby wyświetlała wartości w tysiącach. Dowiesz się także, jak zastosować niestandardowy format liczbowy do etykiet drugiej osi, co daje precyzyjną kontrolę nad prezentacją danych. Postępuj zgodnie z instrukcjami, aby zwiększyć czytelność wykresów wieloosiowych w raportach Word.

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

**Q: Czy muszę dodać drugą serię przed ustawieniem jednostki wyświetlania i formatu liczbowego na drugiej osi X?**  
A: Nie – ustawienia `AxisX` należą do `ChartSeriesGroup`, więc możesz ustawić `secondaryGroup.AxisX.DisplayUnit.Unit` i `secondaryGroup.AxisX.NumberFormat.FormatCode` przed lub po dodaniu serii; konfiguracja zostanie zastosowana do osi grupy w obu przypadkach.

**Q: Czy mogę użyć innej wbudowanej jednostki, np. milionów, dla drugiej osi X?**  
A: Tak – przypisz dowolną wartość `AxisBuiltInUnit`, np. `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;`, aby wyświetlać wartości osi w milionach zamiast w tysiącach.

**Q: Czy niestandardowy format "#,##0.0" wpłynie na etykiety pierwszej osi X?**  
A: Nie – kod formatu jest stosowany tylko do osi, którą modyfikujesz (`secondaryGroup.AxisX.NumberFormat.FormatCode`), więc pierwsza oś X zachowuje domyślne formatowanie.

**Q: Co się stanie, jeśli zapomnę wyczyścić serię demonstracyjną za pomocą `lineChart.Series.Clear();`?**  
A: Wykres będzie zawierał domyślną serię demonstracyjną oprócz dodanych przez Ciebie, co może spowodować dodatkowe linie i niezgodne kategorie; wyczyszczenie kolekcji zapewnia, że pojawią się tylko zamierzone dane.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}