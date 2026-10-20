---
title: Dodaj pole formularza typu pole wyboru do dokumentu Word przy użyciu Aspose.Words for .NET
weight: 210
limit:
description: Dowiedz się, jak programowo dodać pole formularza typu pole wyboru do nowego dokumentu Word przy użyciu Aspose.Words for .NET i zapisać plik.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj pole formularza typu pole wyboru do dokumentu Word przy użyciu Aspose.Words
Ten samouczek pokazuje, jak utworzyć nowy dokument Word i użyć DocumentBuilder z Aspose.Words for .NET do wstawienia pola formularza typu pole wyboru. Postępując zgodnie z krokami, zobaczysz dokładny kod potrzebny do dodania interaktywnego elementu, a następnie zapisania dokumentu do pliku. To szybki sposób na programowe tworzenie prostych plików Word z obsługą formularzy.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Co oznacza czwarty argument (0) w metodzie InsertCheckBox?**
A: Określa wizualny rozmiar pola wyboru w punktach; wartość 0 powoduje, że Aspose.Words używa domyślnego rozmiaru.

**Q: Czy mogę wstawić więcej niż jedno pole wyboru o tej samej nazwie?**
A: Nie – każda nazwa pola formularza musi być unikalna; próba wstawienia kolejnego pola wyboru o nazwie "CheckBox" spowoduje wyrzucenie ArgumentException.

**Q: Jak dodać pole wyboru do istniejącego dokumentu zamiast do nowego?**
A: Najpierw załaduj dokument (np. `Document doc = new Document(\"Existing.docx\");`), następnie utwórz DocumentBuilder dla tego dokumentu i wywołaj `InsertCheckBox` w wybranej pozycji kursora.

**Q: Jak mogę odczytać stan wstawionego pola wyboru po zapisaniu dokumentu?**
A: Pobierz pole formularza za pomocą `doc.Range.FormFields[\"CheckBox\"]` i sprawdź jego właściwość `Checked`, aby zobaczyć, czy było zaznaczone.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}