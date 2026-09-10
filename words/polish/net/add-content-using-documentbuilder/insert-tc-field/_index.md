---
title: Dodaj pole TC do dokumentu Word przy użyciu Aspose.Words for .NET
weight: 310
limit:
description: Dowiedz się, jak wstawić pole TC do nowego dokumentu Word przy użyciu Aspose.Words for .NET i DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj pole TC do dokumentu Word przy użyciu Aspose.Words
W tym interaktywnym samouczku nauczysz się, jak programowo dodać pole TC — ukryty znacznik używany przez funkcje indeksowania i spisu treści w programie Word — do świeżo utworzonego dokumentu przy użyciu Aspose.Words for .NET. Korzystając z DocumentBuilder, możesz umieścić pole dokładnie tam, gdzie jest potrzebne, a następnie zapisać plik, gotowy do dalszego przetwarzania.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Co właściwie robi pole "TC" wstawione przez `builder.InsertField("TC \"Entry Text\" \\f t")` w dokumencie Word?**
A: Tworzy wpis w spisie treści z widocznym tekstem "Entry Text" i oznacza go jako wpis TC (Table of Contents), który Word może później wykorzystać przy generowaniu spisu treści.

**Q: Jaki jest cel przełącznika `\f t` w łańcuchu pola TC?**
A: Przełącznik `\f t` instruuje Word, aby traktował wpis jako zwykły tekst (a nie jako nagłówek) i aby uwzględnił go w spisie treści podczas jego tworzenia.

**Q: Czy mogę wstawić wiele pól TC z różnymi tekstami wpisów, używając tej samej instancji `DocumentBuilder`?**
A: Tak; wystarczy ponownie wywołać `builder.InsertField` z innym łańcuchem, np. `builder.InsertField("TC \"Another Entry\" \\f t")`, a każde wywołanie wstawia nowe pole TC w bieżącej pozycji kursora.

**Q: Jeśli potrzebuję, aby tekst wpisu był dynamiczny (np. z zmiennej), jak powinienem sformatować wywołanie `InsertField`?**
A: Zbuduj łańcuch pola przy użyciu interpolacji ciągów lub `String.Format`, na przykład: `string entry = "Chapter 1"; builder.InsertField($"TC \"{entry}\" \\f t");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}