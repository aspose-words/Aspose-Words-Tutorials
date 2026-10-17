---
title: Dodaj pole formularza Combo Box do dokumentu Word przy użyciu Aspose.Words for .NET
weight: 310
limit:
description: Dowiedz się, jak dodać pole formularza combo box z predefiniowanymi elementami do dokumentu Word przy użyciu Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj pole formularza Combo Box do dokumentu Word przy użyciu Aspose.Words
Ten samouczek demonstruje, jak używać DocumentBuilder z Aspose.Words for .NET do tworzenia nowego dokumentu Word i wstawiania pola formularza typu combo box wypełnionego predefiniowanymi elementami. Postępując zgodnie z kodem krok po kroku, zobaczysz, jak skonfigurować opcje combo boxa, a następnie zapisać dokument do użycia w formularzach interaktywnych.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: Co reprezentuje tablica `items` przekazywana do `InsertComboBox`?**
A: Określa listę ciągów znaków, które pojawiają się jako wybieralne opcje w rozwijanym menu combo boxa.

**Q: Jak mogę zmienić, który element jest domyślnie wybrany po otwarciu dokumentu?**
A: Ustaw trzeci argument (`selectedIndex`) metody `InsertComboBox` na indeks zerowy pożądanego domyślnego elementu (np. `2` dla "Three").

**Q: Czy można umieścić combo box w określonym miejscu w dokumencie?**
A: Tak — przesuń kursor `DocumentBuilder` do żądanego miejsca, używając metod takich jak `MoveToParagraph`, `InsertParagraph` lub `Write` przed wywołaniem `InsertComboBox`.

**Q: Jaki format pliku jest tworzony przez ten kod i czy może być otwarty w starszych wersjach Worda?**
A: Kod zapisuje plik `.docx`, który może być otwarty w Word 2007 i nowszych wersjach, a także w każdej aplikacji obsługującej format OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}