---
title: Wstaw kształt linii poziomej w dokumencie Word przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Przewodnik krok po kroku, jak wstawić kształt linii poziomej do dokumentu Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw kształt linii poziomej w dokumencie Word przy użyciu Aspose.Words
Dowiedz się, jak używać Aspose.Words for .NET do wstawiania kształtu linii poziomej do dokumentu Word. Ten tutorial przeprowadza Cię przez tworzenie nowego dokumentu, dodawanie linii tekstu, umieszczanie kształtu linii poziomej przy pomocy DocumentBuilder oraz zapisywanie pliku. Linia pozioma zapewnia prosty wizualny separator dla Twojej treści.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Czy mogę zmienić wygląd (kolor, grubość) linii poziomej wstawionej za pomocą DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule tworzy wbudowany kształt linii poziomej z domyślnym formatowaniem; aby zmodyfikować jego wygląd, należy pobrać wstawiony obiekt Shape (builder.CurrentParagraph.LastChild) i dostosować jego właściwości LineFormat.

**Q: Co się stanie, jeśli wywołam InsertHorizontalRule() po akapicie, który już kończy się znakiem końca linii?**
A: Metoda wstawia linię jako osobny akapit, więc poprzedzający znak końca linii po prostu tworzy pusty akapit przed linią; linia nadal pojawi się w osobnym wierszu.

**Q: Czy można wstawić więcej niż jedną linię poziomą w tym samym dokumencie przy użyciu DocumentBuilder?**
A: Tak, każde wywołanie builder.InsertHorizontalRule() dodaje nowy kształt linii poziomej w bieżącej pozycji kursora, umożliwiając umieszczenie wielu linii w całym dokumencie.

**Q: Czy InsertHorizontalRule() działa przy zapisywaniu dokumentu do formatów innych niż DOCX, np. PDF?**
A: Linia pozioma jest przechowywana jako kształt w modelu dokumentu, więc przy zapisie do PDF, XPS lub innych obsługiwanych formatów jest prawidłowo renderowana w wyniku.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}