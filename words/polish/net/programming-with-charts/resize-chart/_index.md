---
title: Proporcjonalne skalowanie wykresu przy zmianie rozmiaru strony w Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Dowiedz się, jak automatycznie zmieniać rozmiar wykresu kolumnowego w Word przy zmianie dokumentu na A4, używając Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Dowiedz się, jak automatycznie zmieniać rozmiar wykresu kolumnowego
    w Word przy zmianie dokumentu na A4, używając Aspose.Words for .NET.
  headline: Proporcjonalne skalowanie wykresu przy zmianie rozmiaru strony w Word
    przy użyciu Aspose.Words for .NET
  type: TechArticle
- description: Dowiedz się, jak automatycznie zmieniać rozmiar wykresu kolumnowego
    w Word przy zmianie dokumentu na A4, używając Aspose.Words for .NET.
  name: Proporcjonalne skalowanie wykresu przy zmianie rozmiaru strony w Word przy
    użyciu Aspose.Words for .NET
  steps:
  - name: Utwórz nowy obiekt Document oraz DocumentBuilder, aby go edytować.
    text: Utwórz nowy obiekt Document oraz DocumentBuilder, aby go edytować.
  - name: Wstaw wykres kolumnowy o rozmiarze 432×252 punktów i uzyskaj jego obiekt
      Chart.
    text: Wstaw wykres kolumnowy o rozmiarze 432×252 punktów i uzyskaj jego obiekt
      Chart.
  - name: Ustaw tekst tytułu wykresu na "Quarterly Revenue" i spraw, aby był widoczny.
    text: Ustaw tekst tytułu wykresu na "Quarterly Revenue" i spraw, aby był widoczny.
  - name: Zapisz dokument do pliku, zachowując oryginalny rozmiar wykresu.
    text: Zapisz dokument do pliku, zachowując oryginalny rozmiar wykresu.
  - name: Zmień rozmiar papieru dokumentu na A4 i odśwież układ.
    text: Zmień rozmiar papieru dokumentu na A4 i odśwież układ.
  - name: Oblicz nową szerokość wykresu równą 80 % szerokości strony, zachowując pierwotny
      współczynnik proporcji.
    text: Oblicz nową szerokość wykresu równą 80 % szerokości strony, zachowując pierwotny
      współczynnik proporcji.
  - name: Jeśli kształt zawiera wykres, zastosuj obliczoną szerokość i wysokość, aby
      go przeskalować.
    text: Jeśli kształt zawiera wykres, zastosuj obliczoną szerokość i wysokość, aby
      go przeskalować.
  - name: Zapisz dokument po przeskalowaniu wykresu, aby odzwierciedlić nowy rozmiar
      strony.
    text: Zapisz dokument po przeskalowaniu wykresu, aby odzwierciedlić nowy rozmiar
      strony.
  type: HowTo
- questions:
  - answer: Tak. Zmiana `docBuilder.PageSetup.PaperSize` nie powoduje automatycznej
      korekty istniejących kształtów, więc musisz samodzielnie przeliczyć i przypisać
      `chartContainer.Width` oraz `Height`, jak pokazano.
    question: Czy muszę ręcznie zmienić rozmiar wykresu po zmianie rozmiaru papieru
      dokumentu?
  - answer: Przechowuje `originalAspectRatio = chartContainer.Height / chartContainer.Width`,
      a następnie oblicza `newChartHeight = newChartWidth * originalAspectRatio` po
      ustaleniu nowej szerokości.
    question: Jak kod zachowuje pierwotny współczynnik szerokości do wysokości wykresu
      podczas zmiany rozmiaru?
  - answer: '`UpdatePageLayout()` wymusza ponowne przeliczenie wymiarów stron przez
      silnik układu, zapewniając, że `docBuilder.PageSetup.PageWidth` odzwierciedla
      nową szerokość A4 przed ponownym obliczeniem rozmiaru wykresu.'
    question: Dlaczego po ustawieniu rozmiaru papieru na A4 wywoływane jest `myDoc.UpdatePageLayout()`?
  - answer: Warunek `if (chartContainer.HasChart)` zapobiega przypisaniu `Width` i
      `Height`, gdy wykres nie jest obecny, unikając wyjątku w czasie wykonywania.
    question: Co się stanie, jeśli wstawiony kształt nie zawiera faktycznie wykresu?
  - answer: Oczywiście — zamień mnożnik `0.8` na dowolną proporcję, którą preferujesz;
      reszta logiki skalowania nadal zachowa pierwotny współczynnik proporcji.
    question: Czy mogę zmienić współczynnik skalowania 80 % na inną wartość?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Zmień rozmiar wykresu w Word przy przełączaniu na A4
og_description: Utrzymaj proporcje wykresu, automatycznie zmieniając jego rozmiar po przełączeniu dokumentu na A4.
og_image_alt: Zrzut ekranu pokazujący wykres kolumnowy automatycznie dopasowany do dokumentu Word w formacie A4 przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Proporcjonalne skalowanie wykresu przy zmianie rozmiaru strony w Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak wstawić wykres kolumnowy do dokumentu Word, przełączyć rozmiar strony dokumentu na A4 i sprawić, aby wykres automatycznie zmieniał rozmiar, pozostając proporcjonalnym do nowej szerokości strony. Postępując zgodnie z krokami, zobaczysz, jak wykres dostosowuje swoje wymiary bez ręcznego skalowania, zapewniając spójny układ w różnych formatach stron.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Czy muszę ręcznie zmienić rozmiar wykresu po zmianie rozmiaru papieru dokumentu?**  
A: Tak. Zmiana `docBuilder.PageSetup.PaperSize` nie powoduje automatycznej korekty istniejących kształtów, więc musisz samodzielnie przeliczyć i przypisać `chartContainer.Width` oraz `Height`, jak pokazano.

**Q: Jak kod zachowuje pierwotny współczynnik szerokości do wysokości wykresu podczas zmiany rozmiaru?**  
A: Przechowuje `originalAspectRatio = chartContainer.Height / chartContainer.Width`, a następnie oblicza `newChartHeight = newChartWidth * originalAspectRatio` po ustaleniu nowej szerokości.

**Q: Dlaczego po ustawieniu rozmiaru papieru na A4 wywoływane jest `myDoc.UpdatePageLayout()`?**  
A: `UpdatePageLayout()` wymusza ponowne przeliczenie wymiarów stron przez silnik układu, zapewniając, że `docBuilder.PageSetup.PageWidth` odzwierciedla nową szerokość A4 przed ponownym obliczeniem rozmiaru wykresu.

**Q: Co się stanie, jeśli wstawiony kształt nie zawiera faktycznie wykresu?**  
A: Warunek `if (chartContainer.HasChart)` zapobiega przypisaniu `Width` i `Height`, gdy wykres nie jest obecny, unikając wyjątku w czasie wykonywania.

**Q: Czy mogę zmienić współczynnik skalowania 80 % na inną wartość?**  
A: Oczywiście — zamień mnożnik `0.8` na dowolną proporcję, którą preferujesz; reszta logiki skalowania nadal zachowa pierwotny współczynnik proporcji.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}