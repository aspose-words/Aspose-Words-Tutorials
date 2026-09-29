---
title: Zastąp dane kodu kreskowego w dokumentach Word przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Dowiedz się, jak wstawić pole DISPLAYBARCODE i zastąpić jego ciąg danych przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Dowiedz się, jak wstawić pole DISPLAYBARCODE i zastąpić jego ciąg danych
    przy użyciu Aspose.Words for .NET.
  headline: Zastąp dane kodu kreskowego w dokumentach Word przy użyciu Aspose.Words
    for .NET
  type: TechArticle
- description: Dowiedz się, jak wstawić pole DISPLAYBARCODE i zastąpić jego ciąg danych
    przy użyciu Aspose.Words for .NET.
  name: Zastąp dane kodu kreskowego w dokumentach Word przy użyciu Aspose.Words for
    .NET
  steps:
  - name: Utwórz nowy obiekt Document oraz DocumentBuilder, aby zbudować jego zawartość.
    text: Utwórz nowy obiekt Document oraz DocumentBuilder, aby zbudować jego zawartość.
  - name: Wstaw pole DISPLAYBARCODE i ustaw jego typ, początkową wartość oraz znaki
      start/stop, a następnie dodaj znak końca linii.
    text: Wstaw pole DISPLAYBARCODE i ustaw jego typ, początkową wartość oraz znaki
      start/stop, a następnie dodaj znak końca linii.
  - name: Wywołaj UpdateFields, aby wyrenderować nowo wstawione pole kodu kreskowego.
    text: Wywołaj UpdateFields, aby wyrenderować nowo wstawione pole kodu kreskowego.
  - name: Użyj silnika Znajdź/Zamień, aby zmienić ciąg danych kodu kreskowego z INIT123
      na NEWVAL.
    text: Użyj silnika Znajdź/Zamień, aby zmienić ciąg danych kodu kreskowego z INIT123
      na NEWVAL.
  - name: Ponownie zaktualizuj pola, aby DISPLAYBARCODE odzwierciedlało nowy ciąg
      danych.
    text: Ponownie zaktualizuj pola, aby DISPLAYBARCODE odzwierciedlało nowy ciąg
      danych.
  - name: Zapisz dokument jako plik .docx.
    text: Zapisz dokument jako plik .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` zmienia tylko podstawowy tekst; wizualny wynik pola DISPLAYBARCODE
      jest odtwarzany tylko po wywołaniu `UpdateFields()`, więc nowy kod kreskowy
      pojawia się w zapisanym dokumencie.'
    question: Dlaczego muszę wywołać `myDocument.UpdateFields()` po wykonaniu `Range.Replace`?
  - answer: Tak, `Document.Range.Replace` działa na całym zakresie dokumentu, więc
      każdy pasujący tekst w innym miejscu zostanie zamieniony, chyba że ograniczysz
      wyszukiwanie za pomocą `FindReplaceOptions` (np. ustawiając konkretny `Range`
      lub używając `.MatchWholeWord`).
    question: Czy wywołanie `Replace(\"INIT123\", \"NEWVAL\", ...)` wpłynie na inne
      wystąpienia „INIT123” poza polem kodu kreskowego?
  - answer: Możesz przypisać nową wartość do `displayBarcode.BarcodeType` w dowolnym
      momencie, ale musisz później wywołać `myDocument.UpdateFields()`, aby zmiana
      została odzwierciedlona w wyrenderowanym kodzie kreskowym.
    question: Czy mogę zmienić typ kodu kreskowego (np. z CODE39 na QR) po wstawieniu
      pola?
  - answer: Gdy `AddStartStopChar` jest ustawione na true, Aspose.Words automatycznie
      dodaje wymagane znaki start/stop (`*`) wokół wartości kodu kreskowego, co jest
      wymagane przez CODE39; ustaw na false, jeśli Twoja symbologia ich nie potrzebuje.
    question: Co robi właściwość `AddStartStopChar = true` dla kodów kreskowych CODE39?
  - answer: Nie są wymagane specjalne ustawienia dla prostego dopasowania dokładnego,
      ale możesz włączyć `.MatchCase` lub `.MatchWholeWord` w `FindReplaceOptions`,
      aby uniknąć przypadkowych częściowych zamian.
    question: Czy muszę konfigurować specjalne opcje w `FindReplaceOptions`, aby bezpiecznie
      zastąpić wartość kodu kreskowego?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Zaktualizuj pole kodu kreskowego w Wordzie przy użyciu Aspose.Words
og_description: Zamień ciąg danych kodu kreskowego i odśwież go natychmiast w pliku Word.
og_image_alt: Zrzut ekranu pokazujący dokument Word z polem DISPLAYBARCODE przed i po zamianie danych przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zastąp dane kodu kreskowego w dokumentach Word przy użyciu Aspose.Words
Ten tutorial demonstruje, jak wstawić pole DISPLAYBARCODE do dokumentu Word, a następnie użyć metody Document.Range.Replace, aby zmienić ciąg danych kodu kreskowego. Po zamianie pole jest odświeżane, dzięki czemu zaktualizowany kod kreskowy pojawia się w zapisanym pliku. Postępuj zgodnie z krokami, aby zobaczyć natychmiastową aktualizację kodu kreskowego bez konieczności ponownego tworzenia pola.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: Dlaczego muszę wywołać `myDocument.UpdateFields()` po wykonaniu `Range.Replace`?**  
A: `Range.Replace` zmienia tylko podstawowy tekst; wizualny wynik pola DISPLAYBARCODE jest odtwarzany tylko po wywołaniu `UpdateFields()`, więc nowy kod kreskowy pojawia się w zapisanym dokumencie.

**Q: Czy wywołanie `Replace(\"INIT123\", \"NEWVAL\", ...)` wpłynie na inne wystąpienia „INIT123” poza polem kodu kreskowego?**  
A: Tak, `Document.Range.Replace` działa na całym zakresie dokumentu, więc każdy pasujący tekst w innym miejscu zostanie zamieniony, chyba że ograniczysz wyszukiwanie za pomocą `FindReplaceOptions` (np. ustawiając konkretny `Range` lub używając `.MatchWholeWord`).

**Q: Czy mogę zmienić typ kodu kreskowego (np. z CODE39 na QR) po wstawieniu pola?**  
A: Możesz przypisać nową wartość do `displayBarcode.BarcodeType` w dowolnym momencie, ale musisz później wywołać `myDocument.UpdateFields()`, aby zmiana została odzwierciedlona w wyrenderowanym kodzie kreskowym.

**Q: Co robi właściwość `AddStartStopChar = true` dla kodów kreskowych CODE39?**  
A: Gdy `AddStartStopChar` jest ustawione na true, Aspose.Words automatycznie dodaje wymagane znaki start/stop (`*`) wokół wartości kodu kreskowego, co jest wymagane przez CODE39; ustaw na false, jeśli Twoja symbologia ich nie potrzebuje.

**Q: Czy muszę konfigurować specjalne opcje w `FindReplaceOptions`, aby bezpiecznie zastąpić wartość kodu kreskowego?**  
A: Nie są wymagane specjalne ustawienia dla prostego dopasowania dokładnego, ale możesz włączyć `.MatchCase` lub `.MatchWholeWord` w `FindReplaceOptions`, aby uniknąć przypadkowych częściowych zamian.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}