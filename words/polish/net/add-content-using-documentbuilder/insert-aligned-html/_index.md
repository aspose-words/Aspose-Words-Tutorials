---
title: Wstaw wyrównany HTML do dokumentu Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Dowiedz się, jak wstawić surowy HTML z wyrównaniem lewym, środkowym lub prawym do dokumentu Word przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wyrównany HTML do dokumentu Word przy użyciu Aspose.Words
Ten interaktywny samouczek pokazuje, jak osadzić surowy HTML w dokumencie Word, kontrolując jego wyrównanie — lewo, środek lub prawo — przy użyciu Aspose.Words for .NET. Korzystając z Document i DocumentBuilder, możesz wstawić ciąg HTML i zastosować żądane wyrównanie akapitu w kilku linijkach kodu. Przykład jest idealny, gdy trzeba zachować formatowanie HTML i precyzyjnie umieścić treść w dokumencie.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Co się stanie, jeśli ciąg HTML przekazany do DocumentBuilder.InsertHtml zawiera tagi, których Aspose.Words nie obsługuje, takie jak <script> lub <iframe>?**
A: Nieobsługiwane tagi są ignorowane; Aspose.Words parsuje tylko podzbiór HTML, który potrafi renderować, więc <script>, <iframe> i podobne elementy są usuwane, a reszta treści jest wstawiana.

**Q: Czy style CSS w linii (np. <span style=\"color:red;\">) zostaną zachowane przy użyciu InsertHtml?**
A: Tak, InsertHtml respektuje wiele właściwości CSS w linii, takich jak color, font‑size i background, konwertując je na odpowiadające formatowanie w Wordzie.

**Q: Czy InsertHtml automatycznie tworzy nowy akapit dla elementów blokowych, takich jak <div> lub <h1>?**
A: Elementy blokowe są mapowane na akapity w Wordzie, więc każdy <div>, <p>, <h1> itp. staje się osobnym akapitem w dokumencie.

**Q: Jak wstawić HTML w określonym miejscu istniejącego dokumentu, zamiast na początku?**
A: Przesuń kursor DocumentBuildera do żądanego węzła (np. builder.MoveToDocumentEnd() lub builder.MoveToParagraph(index)) przed wywołaniem InsertHtml; HTML zostanie wstawiony w bieżącej pozycji kursora.

**Q: Jeśli dokument już zawiera tekst, czy wywołanie InsertHtml nadpisze istniejącą treść?**
A: Nie, InsertHtml wstawia przetworzony HTML w bieżącej pozycji buildera, nie usuwając istniejących węzłów, chyba że jawnie przeniesiesz kursor do nich lub usuniesz je wcześniej.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}