---
title: Wstaw pole TC w dokumencie Word przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Dowiedz się, jak wstawić pole TC z własnym tekstem do dokumentu Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw pole TC w dokumencie Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak używać Aspose.Words for .NET do wstawienia pola TC (Table of Contents) do nowo utworzonego dokumentu Word. Korzystając z DocumentBuilder, możesz dodać pole TC z niestandardowym tekstem wpisu, co jest przydatne przy tworzeniu indeksu przeszukiwalnego dla spisu treści. Przykład również demonstruje zapisywanie dokumentu na dysku.

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

**Q: Co oznacza przełącznik "\f t" w kodzie pola TC?**
A: Przełącznik "\f t" instruuje Word, aby traktował wpis jako wpis tabeli, co powoduje jego pojawienie się w spisie treści wygenerowanym przy użyciu przełącznika \f.

**Q: Jak mogę zmienić tekst wyświetlany w polu TC?**
A: Zastąp "Entry Text" w wywołaniu InsertField dowolnym ciągiem znaków, np. builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Czy mogę wstawić wiele pól TC w tym samym dokumencie?**
A: Tak; po prostu wywołaj builder.InsertField z różnymi tekstami wpisów w wybranych miejscach przed zapisaniem dokumentu.

**Q: Czy ten kod działa dla formatów innych niż .docx, np. .pdf?**
A: W przykładzie dokument jest zapisywany jako .docx, ale Aspose.Words może zapisywać do innych formatów (np. .pdf) poprzez zmianę rozszerzenia pliku w doc.Save i upewnienie się, że odpowiedni format wyjściowy jest obsługiwany.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}