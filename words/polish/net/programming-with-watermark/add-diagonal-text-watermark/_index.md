---
title: Utwórz ukośny znak wodny tekstowy z niestandardową czcionką w dokumencie Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Kod krok po kroku, aby dodać ukośny znak wodny tekstowy z niestandardową czcionką do pliku Word .docx przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Kod krok po kroku, aby dodać ukośny znak wodny tekstowy z niestandardową
    czcionką do pliku Word .docx przy użyciu Aspose.Words for .NET.
  headline: Utwórz ukośny znak wodny tekstowy z niestandardową czcionką w dokumencie
    Word przy użyciu Aspose.Words for .NET
  type: TechArticle
- description: Kod krok po kroku, aby dodać ukośny znak wodny tekstowy z niestandardową
    czcionką do pliku Word .docx przy użyciu Aspose.Words for .NET.
  name: Utwórz ukośny znak wodny tekstowy z niestandardową czcionką w dokumencie Word
    przy użyciu Aspose.Words for .NET
  steps:
  - name: Utwórz nową pustą instancję dokumentu Word o nazwie `document`.
    text: Utwórz nową pustą instancję dokumentu Word o nazwie `document`.
  - name: Skonfiguruj `watermarkSettings` z czcionką Arial 48 pt w szarym kolorze,
      układem ukośnym i nieprzezroczystym renderowaniem.
    text: Skonfiguruj `watermarkSettings` z czcionką Arial 48 pt w szarym kolorze,
      układem ukośnym i nieprzezroczystym renderowaniem.
  - name: Zastosuj znak wodny tekstowy \"Private\" do `document` przy użyciu wcześniej
      zdefiniowanych ustawień.
    text: Zastosuj znak wodny tekstowy \"Private\" do `document` przy użyciu wcześniej
      zdefiniowanych ustawień.
  - name: Zdefiniuj ścieżkę pliku, w której zostanie zapisany dokument z znakiem wodnym.
    text: Zdefiniuj ścieżkę pliku, w której zostanie zapisany dokument z znakiem wodnym.
  - name: Zapisz zmodyfikowany `document` w określonej ścieżce jako plik .docx.
    text: Zapisz zmodyfikowany `document` w określonej ścieżce jako plik .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` określa, czy znak wodny jest renderowany z częściową
      przezroczystością; ustawienie na `false` sprawia, że znak wodny jest w pełni
      nieprzezroczysty, natomiast `true` stosuje domyślny efekt półprzezroczysty.'
    question: Co kontroluje flaga **IsSemitrasparent** w `TextWatermarkOptions`?
  - answer: Tak — ustaw właściwość `Layout` na `WatermarkLayout.Horizontal` (lub inną
      wartość wyliczeniową) przed wywołaniem `document.Watermark.SetText`.
    question: Czy mogę zmienić orientację znaku wodnego na poziomą zamiast ukośnej?
  - answer: Word przełączy się na domyślną czcionkę dla znaku wodnego, więc tekst
      nadal będzie widoczny, ale może wyglądać inaczej niż zamierzony styl.
    question: Co się stanie, jeśli określona `FontFamily` (np. \"Arial\") nie jest
      zainstalowana na docelowym komputerze?
  - answer: Wczytaj istniejący plik za pomocą `Document document = new Document(\"Existing.docx\");`,
      następnie skonfiguruj `TextWatermarkOptions` i wywołaj `document.Watermark.SetText`,
      jak pokazano.
    question: Czy można dodać znak wodny do istniejącego pliku `.docx` zamiast tworzyć
      nowy?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Dodaj ukośny znak wodny tekstowy z niestandardową czcionką
og_description: Naucz się w kilka minut osadzić pochyły znak wodny tekstowy z własną czcionką w pliku Word.
og_image_alt: Poradnik pokazujący, jak dodać ukośny znak wodny tekstowy z niestandardową czcionką do dokumentu Word przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz ukośny znak wodny tekstowy z niestandardową czcionką w dokumencie Word przy użyciu Aspose.Words
Ten tutorial przeprowadza Cię przez proces tworzenia nowego dokumentu Word, konfigurowania ukośnego znaku wodnego tekstowego z wybranymi ustawieniami czcionki, zastosowania go za pomocą API Document.Watermark.SetText oraz zapisania wyniku jako plik .docx. Po zakończeniu będziesz mieć profesjonalnie oznaczony znakami wodnymi dokument, który prezentuje Twoją markę lub własność. Krok po kroku przygotowany kod jest gotowy do skopiowania do dowolnego projektu .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Co kontroluje flaga **IsSemitrasparent** w `TextWatermarkOptions`?**  
A: `IsSemitrasparent` określa, czy znak wodny jest renderowany z częściową przezroczystością; ustawienie na `false` sprawia, że znak wodny jest w pełni nieprzezroczysty, natomiast `true` stosuje domyślny efekt półprzezroczysty.

**Q: Czy mogę zmienić orientację znaku wodnego na poziomą zamiast ukośnej?**  
A: Tak — ustaw właściwość `Layout` na `WatermarkLayout.Horizontal` (lub inną wartość wyliczeniową) przed wywołaniem `document.Watermark.SetText`.

**Q: Co się stanie, jeśli określona `FontFamily` (np. \"Arial\") nie jest zainstalowana na docelowym komputerze?**  
A: Word przełączy się na domyślną czcionkę dla znaku wodnego, więc tekst nadal będzie widoczny, ale może wyglądać inaczej niż zamierzony styl.

**Q: Czy można dodać znak wodny do istniejącego pliku `.docx` zamiast tworzyć nowy?**  
A: Wczytaj istniejący plik za pomocą `Document document = new Document(\"Existing.docx\");`, następnie skonfiguruj `TextWatermarkOptions` i wywołaj `document.Watermark.SetText`, jak pokazano.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}