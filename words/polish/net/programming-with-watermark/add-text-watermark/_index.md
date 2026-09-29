---
title: Dodaj czerwony przekątny znak wodny tekstowy do dokumentów Word przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Automatycznie zastosuj czerwony przekątny znak wodny tekstowy do każdego pliku Word generowanego w partii przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Automatycznie zastosuj czerwony przekątny znak wodny tekstowy do każdego
    pliku Word generowanego w partii przy użyciu Aspose.Words for .NET.
  headline: Dodaj czerwony przekątny znak wodny tekstowy do dokumentów Word przy użyciu
    Aspose.Words for .NET
  type: TechArticle
- description: Automatycznie zastosuj czerwony przekątny znak wodny tekstowy do każdego
    pliku Word generowanego w partii przy użyciu Aspose.Words for .NET.
  name: Dodaj czerwony przekątny znak wodny tekstowy do dokumentów Word przy użyciu
    Aspose.Words for .NET
  steps:
  - name: Utwórz folder "GeneratedReports", w którym będą zapisywane pliki wyjściowe.
    text: Utwórz folder "GeneratedReports", w którym będą zapisywane pliki wyjściowe.
  - name: Rozpocznij pętlę, która wygeneruje trzy oddzielne dokumenty.
    text: Rozpocznij pętlę, która wygeneruje trzy oddzielne dokumenty.
  - name: Utwórz nowy pusty obiekt dokumentu Word.
    text: Utwórz nowy pusty obiekt dokumentu Word.
  - name: Użyj DocumentBuilder, aby zapisać w dokumencie linię tytułu i opis.
    text: Użyj DocumentBuilder, aby zapisać w dokumencie linię tytułu i opis.
  - name: Zdefiniuj wygląd znaku wodnego, w tym czcionkę, rozmiar, kolor i układ przekątny.
    text: Zdefiniuj wygląd znaku wodnego, w tym czcionkę, rozmiar, kolor i układ przekątny.
  - name: Zastosuj skonfigurowany czerwony przekątny znak wodny z tekstem "PROTECTED"
      w dokumencie.
    text: Zastosuj skonfigurowany czerwony przekątny znak wodny z tekstem "PROTECTED"
      w dokumencie.
  - name: Zapisz oznaczony znak wodny dokument w folderze "GeneratedReports" pod unikalną
      nazwą pliku.
    text: Zapisz oznaczony znak wodny dokument w folderze "GeneratedReports" pod unikalną
      nazwą pliku.
  - name: Zamknij pętlę po przetworzeniu bieżącego dokumentu.
    text: Zamknij pętlę po przetworzeniu bieżącego dokumentu.
  type: HowTo
- questions:
  - answer: IsSemitrasparent określa, czy znak wodny jest renderowany z częściową
      przezroczystością; ustawienie jej na **true** sprawia, że tekst jest półprzezroczysty,
      dzięki czemu zawartość pod nim pozostaje bardziej czytelna.
    question: Co kontroluje opcja **IsSemitrasparent** i jaki efekt ma ustawienie
      jej na **true**?
  - answer: Tak — ustaw właściwość **Layout** na **WatermarkLayout.Horizontal** w
      **TextWatermarkOptions** przed wywołaniem **document.Watermark.SetText**.
    question: Czy mogę zmienić orientację znaku wodnego na poziomą zamiast przekątnej?
  - answer: Fragment kodu tworzy nową instancję **Document**, ale możesz otworzyć
      dowolny istniejący plik (np. `new Document("Existing.docx")`) i następnie wywołać
      **document.Watermark.SetText**, aby zastosować ten sam znak wodny.
    question: Czy ten kod doda znak wodny do istniejącego pliku Word, czy tylko do
      nowo tworzonych dokumentów?
  - answer: Przypisz własny kolor za pomocą **Color.FromArgb(red, green, blue)** do
      właściwości **Color** w **TextWatermarkOptions**, np. `Color = Color.FromArgb(128,
      0, 128)` dla fioletowego.
    question: Jak mogę użyć własnego koloru RGB dla znaku wodnego zamiast predefiniowanego
      **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Dodaj czerwony przekątny znak wodny tekstowy do dokumentów Word
og_description: Zobacz, jak automatycznie zastosować czerwony przekątny znak wodny do każdego dokumentu Word w partii przy użyciu Aspose.Words.
og_image_alt: Poradnik pokazujący, jak dodać czerwony przekątny znak wodny tekstowy do dokumentów Word przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj czerwony przekątny znak wodny tekstowy do dokumentów Word przy użyciu Aspose.Words
Ten tutorial demonstruje, jak automatycznie osadzić czerwony przekątny znak wodny tekstowy w każdym dokumencie Word tworzonym podczas generowania raportów wsadowych. Korzystając z klas Document i DocumentBuilder biblioteki Aspose.Words for .NET, znak wodny jest stosowany programowo w trakcie tworzenia plików, zapewniając, że każdy dokument zawiera tę samą identyfikację marki lub informację poufności bez ręcznego wysiłku.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Co kontroluje opcja **IsSemitrasparent** i jaki efekt ma ustawienie jej na **true**?**  
A: IsSemitrasparent określa, czy znak wodny jest renderowany z częściową przezroczystością; ustawienie jej na **true** sprawia, że tekst jest półprzezroczysty, dzięki czemu zawartość pod nim pozostaje bardziej czytelna.

**Q: Czy mogę zmienić orientację znaku wodnego na poziomą zamiast przekątnej?**  
A: Tak — ustaw właściwość **Layout** na **WatermarkLayout.Horizontal** w **TextWatermarkOptions** przed wywołaniem **document.Watermark.SetText**.

**Q: Czy ten kod doda znak wodny do istniejącego pliku Word, czy tylko do nowo tworzonych dokumentów?**  
A: Fragment kodu tworzy nową instancję **Document**, ale możesz otworzyć dowolny istniejący plik (np. `new Document("Existing.docx")`) i następnie wywołać **document.Watermark.SetText**, aby zastosować ten sam znak wodny.

**Q: Jak mogę użyć własnego koloru RGB dla znaku wodnego zamiast predefiniowanego **Color.Red**?**  
A: Przypisz własny kolor za pomocą **Color.FromArgb(red, green, blue)** do właściwości **Color** w **TextWatermarkOptions**, np. `Color = Color.FromArgb(128, 0, 128)` dla fioletowego.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}