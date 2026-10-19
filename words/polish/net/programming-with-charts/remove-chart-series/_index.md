---
title: Usuwanie serii wykresu z dokumentu Word przy użyciu Aspose.Words for .NET
weight: 510
limit:
description: Dowiedz się, jak usunąć określoną serię danych z wykresu kolumnowego w dokumencie Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Dowiedz się, jak usunąć określoną serię danych z wykresu kolumnowego
    w dokumencie Word przy użyciu Aspose.Words for .NET.
  headline: Usuwanie serii wykresu z dokumentu Word przy użyciu Aspose.Words for .NET
  type: TechArticle
- description: Dowiedz się, jak usunąć określoną serię danych z wykresu kolumnowego
    w dokumencie Word przy użyciu Aspose.Words for .NET.
  name: Usuwanie serii wykresu z dokumentu Word przy użyciu Aspose.Words for .NET
  steps:
  - name: Utwórz nowy dokument Word oraz powiązany z nim obiekt DocumentBuilder.
    text: Utwórz nowy dokument Word oraz powiązany z nim obiekt DocumentBuilder.
  - name: Wstaw wykres kolumnowy o rozmiarze 432×252 punktów i uzyskaj obiekt Chart
      do dalszej manipulacji.
    text: Wstaw wykres kolumnowy o rozmiarze 432×252 punktów i uzyskaj obiekt Chart
      do dalszej manipulacji.
  - name: Zdefiniuj indeks zerowy serii, którą należy usunąć (druga seria).
    text: Zdefiniuj indeks zerowy serii, którą należy usunąć (druga seria).
  - name: Jeśli indeks jest prawidłowy, wywołaj metodę RemoveAt na kolekcji Series
      wykresu, aby usunąć tę serię.
    text: Jeśli indeks jest prawidłowy, wywołaj metodę RemoveAt na kolekcji Series
      wykresu, aby usunąć tę serię.
  - name: Zapisz zaktualizowany dokument do pliku .docx.
    text: Zapisz zaktualizowany dokument do pliku .docx.
  type: HowTo
- questions:
  - answer: Sprawdzenie `if` (`targetSeriesIdx < columnChart.Series.Count`) nie powiedzie
      się, więc `RemoveAt` nigdy nie zostanie wywołane i wykres pozostanie niezmieniony.
    question: Co się stanie, jeśli przekażę indeks równy liczbie serii w wykresie?
  - answer: Tak, po wywołaniu `columnChart.Series.RemoveAt` legenda jest odtwarzana,
      aby odzwierciedlić pozostałe serie, więc usunięty wpis znika z legendy.
    question: Czy usunięcie serii automatycznie aktualizuje legendę wykresu?
  - answer: Kod działa dla każdego typu wykresu, który obsługuje kolekcję `Series`;
      wystarczy zmienić `ChartType.Column` na żądany typ przy wstawianiu wykresu.
    question: Czy mogę użyć tego samego kodu do usunięcia serii z wykresu liniowego
      lub kołowego?
  - answer: Wykres bez serii jest nadal prawidłowym obiektem `Shape` i zostanie zapisany,
      ale w wynikowym dokumencie będzie wyglądał na pusty.
    question: Jeśli usunę jedyną serię w wykresie, czy wykres nadal zostanie poprawnie
      zapisany?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Usuwanie serii wykresu w dokumencie Word
og_description: Przewodnik krok po kroku, jak usunąć serię danych z wykresu Word przy użyciu Aspose.Words for .NET.
og_image_alt: Poradnik pokazujący, jak usunąć określoną serię danych z wykresu kolumnowego w dokumencie Word przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usuwanie serii wykresu z dokumentu Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak utworzyć dokument Word, dodać wykres kolumnowy przy użyciu DocumentBuilder, a następnie usunąć określoną serię danych z tego wykresu metodą ChartSeriesCollection.RemoveAt. Po zakończeniu będziesz mieć zapisany dokument z usuniętą niechcianą serią, co daje precyzyjną kontrolę nad zawartością wykresu bezpośrednio z kodu .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Co się stanie, jeśli przekażę indeks równy liczbie serii w wykresie?**  
A: Sprawdzenie `if` (`targetSeriesIdx < columnChart.Series.Count`) nie powiedzie się, więc `RemoveAt` nigdy nie zostanie wywołane i wykres pozostanie niezmieniony.

**Q: Czy usunięcie serii automatycznie aktualizuje legendę wykresu?**  
A: Tak, po wywołaniu `columnChart.Series.RemoveAt` legenda jest odtwarzana, aby odzwierciedlić pozostałe serie, więc usunięty wpis znika z legendy.

**Q: Czy mogę użyć tego samego kodu do usunięcia serii z wykresu liniowego lub kołowego?**  
A: Kod działa dla każdego typu wykresu, który obsługuje kolekcję `Series`; wystarczy zmienić `ChartType.Column` na żądany typ przy wstawianiu wykresu.

**Q: Jeśli usunę jedyną serię w wykresie, czy wykres nadal zostanie poprawnie zapisany?**  
A: Wykres bez serii jest nadal prawidłowym obiektem `Shape` i zostanie zapisany, ale w wynikowym dokumencie będzie wyglądał na pusty.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}