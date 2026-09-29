---
title: Wstaw kod kreskowy DataMatrix w dokumencie Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Dodaj kod kreskowy DataMatrix do dokumentu Word programowo przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Dodaj kod kreskowy DataMatrix do dokumentu Word programowo przy użyciu
    Aspose.Words for .NET.
  headline: Wstaw kod kreskowy DataMatrix w dokumencie Word przy użyciu Aspose.Words
    for .NET
  type: TechArticle
- description: Dodaj kod kreskowy DataMatrix do dokumentu Word programowo przy użyciu
    Aspose.Words for .NET.
  name: Wstaw kod kreskowy DataMatrix w dokumencie Word przy użyciu Aspose.Words for
    .NET
  steps:
  - name: Utwórz nowy pusty dokument Word oraz obiekt DocumentBuilder do jego edycji.
    text: Utwórz nowy pusty dokument Word oraz obiekt DocumentBuilder do jego edycji.
  - name: Wstaw pole DISPLAYBARCODE w bieżącej pozycji kursora, co dodaje w dokumencie
      miejsce na pole.
    text: Wstaw pole DISPLAYBARCODE w bieżącej pozycji kursora, co dodaje w dokumencie
      miejsce na pole.
  - name: Ustaw właściwość BarcodeType pola na DataMatrix i podaj ciąg danych do zakodowania.
    text: Ustaw właściwość BarcodeType pola na DataMatrix i podaj ciąg danych do zakodowania.
  - name: Opcjonalnie określ kolory tła i pierwszego planu kodu kreskowego.
    text: Opcjonalnie określ kolory tła i pierwszego planu kodu kreskowego.
  - name: Wywołaj metodę UpdateFields na dokumencie, aby wyrenderować obraz kodu kreskowego
      wewnątrz pola.
    text: Wywołaj metodę UpdateFields na dokumencie, aby wyrenderować obraz kodu kreskowego
      wewnątrz pola.
  - name: Zapisz dokument jako plik .docx.
    text: Zapisz dokument jako plik .docx.
  type: HowTo
- questions:
  - answer: Pole zostanie wstawione, ale `document.UpdateFields()` pozostawi kod kreskowy
      pusty, a Aspose.Words zgłosi `FieldException` wskazujący na nieprawidłowy typ
      kodu kreskowego.
    question: Co się stanie, jeśli przypiszę nieobsługiwaną wartość do `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` renderuje obrazy kodów kreskowych, więc możesz wstawić
      wiele obiektów `FieldDisplayBarcode` i wywołać `document.UpdateFields()` jednorazowo
      na końcu, aby wyrenderować je wszystkie.'
    question: Czy muszę wywoływać `document.UpdateFields()` po każdym wstawieniu kodu
      kreskowego, czy mogę zaktualizować raz po dodaniu wszystkich pól?
  - answer: Obie właściwości oczekują szesnastkowego ciągu RGB poprzedzonego `0x`
      (np. `\"0xFF0000\"` dla czerwonego); każdy inny format zostanie zignorowany,
      a zostaną użyte domyślne kolory.
    question: W jakim formacie powinny być ciągi kolorów dla `BackgroundColor` i `ForegroundColor`?
  - answer: Tak — po prostu ustaw `displayBarcodeField.BarcodeValue` na nowy ciąg
      i ponownie wywołaj `document.UpdateFields()`, aby odświeżyć wyrenderowany obraz.
    question: Czy mogę zmienić ładunek kodu kreskowego po wstawieniu pola?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Wstaw kod kreskowy DataMatrix przy użyciu Aspose.Words
og_description: Dowiedz się, jak dodać kod kreskowy DataMatrix do pliku Word w kilku linijkach kodu .NET.
og_image_alt: Poradnik pokazujący, jak wstawić i wyrenderować kod kreskowy DataMatrix w dokumencie Word przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw kod kreskowy DataMatrix w dokumencie Word przy użyciu Aspose.Words
Za pomocą Aspose.Words for .NET możesz programowo dodać kod kreskowy DataMatrix do dokumentu Word. Ten tutorial pokazuje, jak utworzyć nowy dokument, wstawić pole DISPLAYBARCODE, ustawić jego typ na DataMatrix oraz wyrenderować obraz kodu kreskowego przy użyciu klas Document i DocumentBuilder. Postępuj zgodnie z krokami, aby wygenerować drukowalny kod kreskowy bezpośrednio w pliku .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Co się stanie, jeśli przypiszę nieobsługiwaną wartość do `displayBarcodeField.BarcodeType`?**  
A: Pole zostanie wstawione, ale `document.UpdateFields()` pozostawi kod kreskowy pusty, a Aspose.Words zgłosi `FieldException` wskazujący na nieprawidłowy typ kodu kreskowego.

**Q: Czy muszę wywoływać `document.UpdateFields()` po każdym wstawieniu kodu kreskowego, czy mogę zaktualizować raz po dodaniu wszystkich pól?**  
A: `UpdateFields()` renderuje obrazy kodów kreskowych, więc możesz wstawić wiele obiektów `FieldDisplayBarcode` i wywołać `document.UpdateFields()` jednorazowo na końcu, aby wyrenderować je wszystkie.

**Q: W jakim formacie powinny być ciągi kolorów dla `BackgroundColor` i `ForegroundColor`?**  
A: Obie właściwości oczekują szesnastkowego ciągu RGB poprzedzonego `0x` (np. `\"0xFF0000\"` dla czerwonego); każdy inny format zostanie zignorowany, a zostaną użyte domyślne kolory.

**Q: Czy mogę zmienić ładunek kodu kreskowego po wstawieniu pola?**  
A: Tak — po prostu ustaw `displayBarcodeField.BarcodeValue` na nowy ciąg i ponownie wywołaj `document.UpdateFields()`, aby odświeżyć wyrenderowany obraz.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}