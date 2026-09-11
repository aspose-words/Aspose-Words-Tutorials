---
title: Wstaw wyrównany HTML do dokumentu Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Dowiedz się, jak wstawić HTML o określonym wyrównaniu do dokumentu Word przy użyciu Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wyrównany HTML do dokumentu Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak używać DocumentBuilder z Aspose.Words for .NET do osadzania znaczników HTML w dokumencie Word i kontrolowania ich wyrównania. Zobaczysz, jak wstawić HTML, ustawić wyrównanie akapitu (lewe, środkowe lub prawe) oraz zapisać powstały dokument. Przykład jest idealny dla programistów, którzy muszą zachować formatowanie w stylu web przy generowaniu plików Word programowo.

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

**Q: Czy InsertHtml można użyć do dodania HTML do istniejącego dokumentu Word, a nie do nowego?**  
A: Tak. Utwórz Document z istniejącego pliku, ustaw kursor DocumentBuilder w miejscu, w którym ma zostać wstawiony HTML (np. przy użyciu builder.MoveToDocumentEnd()), a następnie wywołaj builder.InsertHtml z Twoim kodem HTML.

**Q: Jakie atrybuty HTML są respektowane przez InsertHtml pod kątem wyrównania?**  
A: InsertHtml respektuje atrybut \"align\" w elementach blokowych, takich jak &lt;p&gt;, &lt;div&gt; i tagi nagłówków, stosując odpowiednie wyrównanie akapitu w powstałym dokumencie Word.

**Q: Co się stanie, jeśli ciąg HTML zawiera nieobsługiwane tagi lub CSS?**  
A: Nieobsługiwane tagi są pomijane, a ich wewnętrzny tekst wstawiany jako zwykły tekst; style CSS w linii, których Aspose.Words nie rozpoznaje, również są ignorowane, więc renderowany jest tylko obsługiwany podzbiór HTML.

**Q: Czy muszę zamknąć DocumentBuilder przed zapisaniem dokumentu?**  
A: Nie jest wymagane jawne zamknięcie; po wstawieniu HTML możesz od razu wywołać doc.Save z żądaną nazwą pliku i formatem, a zasoby buildera zostaną zwolnione automatycznie.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}