---
title: Dodaj numery stron do stopki dokumentu Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Dodaj automatycznie aktualizujące się numery stron do primary footer dokumentu Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Dodaj automatycznie aktualizujące się numery stron do primary footer
    dokumentu Word przy użyciu Aspose.Words for .NET.
  headline: Dodaj numery stron do stopki dokumentu Word przy użyciu Aspose.Words for
    .NET
  type: TechArticle
- description: Dodaj automatycznie aktualizujące się numery stron do primary footer
    dokumentu Word przy użyciu Aspose.Words for .NET.
  name: Dodaj numery stron do stopki dokumentu Word przy użyciu Aspose.Words for .NET
  steps:
  - name: Utwórz nowy obiekt Document oraz DocumentBuilder powiązany z nim.
    text: Utwórz nowy obiekt Document oraz DocumentBuilder powiązany z nim.
  - name: Przesuń kursor buildera do primary footer pierwszej sekcji.
    text: Przesuń kursor buildera do primary footer pierwszej sekcji.
  - name: Ustaw wyrównanie akapitu na środek, aby tekst stopki był wyśrodkowany.
    text: Ustaw wyrównanie akapitu na środek, aby tekst stopki był wyśrodkowany.
  - name: Wpisz etykietę "Page " i wstaw pole PAGE, które wyświetla bieżący numer
      strony.
    text: Wpisz etykietę "Page " i wstaw pole PAGE, które wyświetla bieżący numer
      strony.
  - name: Wpisz " of " i wstaw pole NUMPAGES, które pokazuje całkowitą liczbę stron.
    text: Wpisz " of " i wstaw pole NUMPAGES, które pokazuje całkowitą liczbę stron.
  - name: Zapisz dokument jako plik .docx.
    text: Zapisz dokument jako plik .docx.
  type: HowTo
- questions:
  - answer: Nie. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` przenosi buildera
      tylko do primary footer *pierwszej* sekcji, więc pola są wstawiane wyłącznie
      tam.
    question: Jeśli dokument ma więcej niż jedną sekcję, czy ten kod doda numery stron
      do stopki każdej sekcji?
  - answer: Ustaw `builder.ParagraphFormat.Alignment` na inną wartość `ParagraphAlignment`
      (np. `ParagraphAlignment.Right`) przed zapisaniem pól.
    question: Jak mogę zmienić wyrównanie akapitu z numerem strony w stopce?
  - answer: '`InsertField` przyjmuje kod pola i opcjonalny wynik pola; przekazanie
      `null` informuje Aspose.Words, aby Word obliczył wynik w czasie wykonywania.'
    question: Co reprezentuje argument `null` w `InsertField("PAGE", null)`?
  - answer: Tak — zamień `HeaderFooterType.FooterPrimary` na `HeaderFooterType.HeaderPrimary`
      (lub inny typ nagłówka) przed wstawieniem pól.
    question: Czy mogę umieścić te same pola "Page X of Y" w nagłówku zamiast w stopce?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Wstaw automatyczne numery stron w stopce Word
og_description: Krok po kroku kod, który dodaje bieżące numery stron do stopki Word przy użyciu Aspose.Words for .NET.
og_image_alt: Poradnik pokazujący, jak dodać automatyczne numery stron do stopki dokumentu Word przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj numery stron do stopki dokumentu Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak używać Aspose.Words Document i DocumentBuilder do wstawiania automatycznie aktualizujących się numerów stron do primary footer dokumentu Word. Dodając numery stron programowo, zapewniasz spójną paginację w całym pliku bez ręcznej edycji. Przykładowy kod jest gotowy do uruchomienia w środowisku .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Jeśli dokument ma więcej niż jedną sekcję, czy ten kod doda numery stron do stopki każdej sekcji?**  
A: Nie. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` przenosi buildera tylko do primary footer *pierwszej* sekcji, więc pola są wstawiane wyłącznie tam.

**Q: Jak mogę zmienić wyrównanie akapitu z numerem strony w stopce?**  
A: Ustaw `builder.ParagraphFormat.Alignment` na inną wartość `ParagraphAlignment` (np. `ParagraphAlignment.Right`) przed zapisaniem pól.

**Q: Co reprezentuje argument `null` w `InsertField("PAGE", null)`?**  
A: `InsertField` przyjmuje kod pola i opcjonalny wynik pola; przekazanie `null` informuje Aspose.Words, aby Word obliczył wynik w czasie wykonywania.

**Q: Czy mogę umieścić te same pola "Page X of Y" w nagłówku zamiast w stopce?**  
A: Tak — zamień `HeaderFooterType.FooterPrimary` na `HeaderFooterType.HeaderPrimary` (lub inny typ nagłówka) przed wstawieniem pól.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}