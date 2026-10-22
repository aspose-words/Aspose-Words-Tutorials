---
title: Dodaj komentarz z hiperłączem i wyeksportuj jako adnotację PDF przy użyciu Aspose.Words for .NET
weight: 110
limit:
description: Naucz się dodawać komentarz z hiperłączem w pliku Word i eksportować go jako adnotację PDF przy użyciu Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naucz się dodawać komentarz z hiperłączem w pliku Word i eksportować
    go jako adnotację PDF przy użyciu Aspose.Words for .NET.
  headline: Dodaj komentarz z hiperłączem i wyeksportuj jako adnotację PDF przy użyciu
    Aspose.Words for .NET
  type: TechArticle
- description: Naucz się dodawać komentarz z hiperłączem w pliku Word i eksportować
    go jako adnotację PDF przy użyciu Aspose.Words for .NET.
  name: Dodaj komentarz z hiperłączem i wyeksportuj jako adnotację PDF przy użyciu
    Aspose.Words for .NET
  steps:
  - name: Utwórz nowy pusty obiekt Document oraz DocumentBuilder, aby na nim pracować.
    text: Utwórz nowy pusty obiekt Document oraz DocumentBuilder, aby na nim pracować.
  - name: Wpisz linię widocznego tekstu, która będzie gospodarzem nadchodzącego komentarza.
    text: Wpisz linię widocznego tekstu, która będzie gospodarzem nadchodzącego komentarza.
  - name: Utwórz obiekt Comment autorstwa Jane Doe i dołącz go do pierwszego akapitu
      dokumentu.
    text: Utwórz obiekt Comment autorstwa Jane Doe i dołącz go do pierwszego akapitu
      dokumentu.
  - name: Wewnątrz komentarza dodaj akapit i wstaw niebieskie, podkreślone hiperłącze
      do witryny Aspose.Words Library.
    text: Wewnątrz komentarza dodaj akapit i wstaw niebieskie, podkreślone hiperłącze
      do witryny Aspose.Words Library.
  - name: Skonfiguruj dokument, aby renderował komentarze jako adnotacje PDF i odśwież
      układ.
    text: Skonfiguruj dokument, aby renderował komentarze jako adnotacje PDF i odśwież
      układ.
  - name: Utwórz folder "Output" w bieżącym katalogu, aby przechowywać wygenerowany
      plik PDF.
    text: Utwórz folder "Output" w bieżącym katalogu, aby przechowywać wygenerowany
      plik PDF.
  - name: Zapisz przygotowany dokument jako plik PDF przy użyciu PdfSaveOptions.
    text: Zapisz przygotowany dokument jako plik PDF przy użyciu PdfSaveOptions.
  - name: Sprawdź, czy plik PDF istnieje i zawiera dane, a następnie wyświetl wynik
      w konsoli.
    text: Sprawdź, czy plik PDF istnieje i zawiera dane, a następnie wyświetl wynik
      w konsoli.
  type: HowTo
- questions:
  - answer: Trzeci parametr `InsertHyperlink` określa, czy link ma być traktowany
      jako pole; ustawienie go na `false` wstawia zwykłe hiperłącze, które działa
      w adnotacji PDF bez potrzeby kodu pola.
    question: Co kontroluje trzeci argument (`false`) w metodzie `InsertHyperlink`?
  - answer: Ustaw `myDocument.LayoutOptions.CommentDisplayMode` na `CommentDisplayMode.ShowInBalloons`
      przed wywołaniem `Save`; wówczas PDF będzie zawierał komentarz jako zwykły komentarz
      Word, a nie jako adnotację.
    question: Jak sprawić, aby komentarz wyświetlał się jako dymek w dokumencie Word
      zamiast jako adnotacja PDF?
  - answer: Tak — każdy `Comment`, który dodasz do akapitu, może zawierać własne wywołanie
      `InsertHyperlink`, a wszystkie hiperłącza zostaną zachowane jako oddzielne adnotacje
      PDF po zapisaniu dokumentu.
    question: Jeśli dodam więcej niż jeden komentarz, czy każde hiperłącze będzie
      działać w wyeksportowanym PDF?
  - answer: Otwórz wygenerowany PDF, znajdź adnotację komentarza (zwykle wyświetlaną
      jako ikona notatki), kliknij ją, aby ujawnić tekst komentarza, a następnie kliknij
      niebieskie podkreślone łącze; powinno ono otworzyć docelowy adres URL w przeglądarce
      internetowej.
    question: Jak zweryfikować, że hiperłącze wewnątrz komentarza faktycznie działa
      po wygenerowaniu PDF?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Wstaw komentarz z hiperłączem i wyeksportuj do PDF
og_description: Naucz się osadzać klikalny link w komentarzu Word i przekształcać go w adnotację PDF.
og_image_alt: Poradnik pokazujący, jak dodać komentarz z klikalnym hiperłączem do dokumentu Word i wyeksportować go jako adnotację PDF przy użyciu Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj komentarz z hiperłączem i wyeksportuj jako adnotację PDF przy użyciu Aspose.Words
W tym samouczku zobaczysz, jak utworzyć dokument Word, wstawić komentarz zawierający klikalne hiperłącze do zewnętrznej witryny, skonfigurować ten komentarz tak, aby wyświetlał się jako adnotacja PDF, wyeksportować dokument do PDF oraz zweryfikować powstały plik PDF. Krok po kroku kod pozwala dodać bogate, zawierające linki komentarze i zachować je podczas konwersji do PDF, co ułatwia udostępnianie interaktywnych notatek czytelnikom.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Co kontroluje trzeci argument (`false`) w metodzie `InsertHyperlink`?**  
A: Trzeci parametr `InsertHyperlink` określa, czy link ma być traktowany jako pole; ustawienie go na `false` wstawia zwykłe hiperłącze, które działa w adnotacji PDF bez potrzeby kodu pola.

**Q: Jak sprawić, aby komentarz wyświetlał się jako dymek w dokumencie Word zamiast jako adnotacja PDF?**  
A: Ustaw `myDocument.LayoutOptions.CommentDisplayMode` na `CommentDisplayMode.ShowInBalloons` przed wywołaniem `Save`; wówczas PDF będzie zawierał komentarz jako zwykły komentarz Word, a nie jako adnotację.

**Q: Jeśli dodam więcej niż jeden komentarz, czy każde hiperłącze będzie działać w wyeksportowanym PDF?**  
A: Tak — każdy `Comment`, który dodasz do akapitu, może zawierać własne wywołanie `InsertHyperlink`, a wszystkie hiperłącza zostaną zachowane jako oddzielne adnotacje PDF po zapisaniu dokumentu.

**Q: Jak zweryfikować, że hiperłącze wewnątrz komentarza faktycznie działa po wygenerowaniu PDF?**  
A: Otwórz wygenerowany PDF, znajdź adnotację komentarza (zwykle wyświetlaną jako ikona notatki), kliknij ją, aby ujawnić tekst komentarza, a następnie kliknij niebieskie podkreślone łącze; powinno ono otworzyć docelowy adres URL w przeglądarce internetowej.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}