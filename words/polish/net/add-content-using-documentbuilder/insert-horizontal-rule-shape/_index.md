---
title: Wstaw kształt poziomej linii w dokumencie Word przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Naucz się dodawać kształt poziomej linii do dokumentu Word przy użyciu Aspose.Words for .NET i DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw kształt poziomej linii w dokumencie Word przy użyciu Aspose.Words
W tym tutorialu dowiesz się, jak programowo wstawić kształt poziomej linii do dokumentu Word przy użyciu Aspose.Words for .NET. Korzystając z klas Document i DocumentBuilder tworzymy nowy dokument, dodajemy akapit tekstu, a następnie umieszczamy kształt poziomej linii w wybranym miejscu. Pozioma linia zapewnia wizualny separator, który może być przydatny przy podziałach sekcji lub podkreślaniu.

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

**Q: Gdzie dokładnie metoda `builder.InsertHorizontalRule()` umieszcza linię w dokumencie?**  
A: `InsertHorizontalRule` wstawia kształt poziomej linii w bieżącą pozycję kursora `DocumentBuilder`; jeśli chcesz, aby znajdował się w osobnym wierszu, wywołaj `builder.Writeln()` przed wstawieniem.

**Q: Czy mogę zmienić grubość, kolor lub szerokość wstawionej poziomej linii?**  
A: `InsertHorizontalRule` dodaje domyślnie sformatowaną linię i nie udostępnia opcji formatowania; aby dostosować te właściwości, musisz ręcznie wstawić `Shape` (np. `builder.InsertShape(ShapeType.HorizontalLine)`) i następnie ustawić jego właściwości `LineFormat`.

**Q: Czy można dodać więcej niż jedną poziomą linię w tym samym dokumencie?**  
A: Tak — po prostu wywołuj `builder.InsertHorizontalRule()` za każdym razem, gdy potrzebujesz nowej linii; każde wywołanie tworzy osobny kształt w bieżącej pozycji buildera.

**Q: Czy pozioma linia będzie widoczna po otwarciu zapisanego pliku .docx w programie Microsoft Word?**  
A: Zdecydowanie; linia jest zapisywana jako kształt w pliku .docx, więc Word wyświetla ją dokładnie tak, jak wygląda w wygenerowanym dokumencie.

**Q: Co się stanie, jeśli folder `dataDir` nie istnieje przed wywołaniem `doc.Save(...)`?**  
A: `doc.Save` zgłosi `DirectoryNotFoundException`; upewnij się, że docelowy katalog istnieje lub utwórz go programowo przed zapisem.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}