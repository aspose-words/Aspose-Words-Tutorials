---
title: Eksportuj nagłówek, stopkę i zakładki dokumentu Word do dokumentu PDF
linktitle: Eksportuj nagłówek, stopkę i zakładki dokumentu Word do dokumentu PDF
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak eksportować zakładki nagłówka i stopki z dokumentu Word do pliku PDF za pomocą Aspose.Words dla .NET, korzystając z naszego przewodnika krok po kroku.
weight: 10
url: /pl/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Eksportuj nagłówek, stopkę i zakładki dokumentu Word do dokumentu PDF

## Wstęp

Konwersja dokumentów Word do PDF to typowe zadanie, zwłaszcza gdy chcesz udostępniać lub archiwizować dokumenty, zachowując ich formatowanie. Czasami te dokumenty zawierają ważne zakładki w nagłówkach i stopkach. W tym samouczku przeprowadzimy Cię przez proces eksportowania tych zakładek z dokumentu Word do PDF przy użyciu Aspose.Words dla .NET.

## Wymagania wstępne

Zanim przejdziemy do konkretów, upewnij się, że masz następujące rzeczy:

- Aspose.Words dla .NET: Musisz mieć zainstalowany Aspose.Words dla .NET. Możesz go pobrać z[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Skonfiguruj swoje środowisko programistyczne. Możesz użyć Visual Studio lub dowolnego innego IDE zgodnego z .NET.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest wymagana, aby móc śledzić przykłady kodu.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#. Dodaj te wiersze na górze pliku kodu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Podzielmy ten proces na łatwe do wykonania kroki.

## Krok 1: Zainicjuj dokument

Pierwszym krokiem jest załadowanie dokumentu Word. Oto jak to zrobić:

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

W tym kroku po prostu podasz ścieżkę do katalogu dokumentów i załadujesz dokument Word.

## Krok 2: Skonfiguruj opcje zapisywania pliku PDF

Następnie należy skonfigurować opcje zapisu w formacie PDF, aby mieć pewność, że zakładki w nagłówkach i stopkach zostaną prawidłowo wyeksportowane.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Tutaj konfigurujemy`PdfSaveOptions` . Ten`DefaultBookmarksOutlineLevel` właściwość ustawia poziom konspektu dla zakładek i`HeaderFooterBookmarksExportMode` Właściwość ta zapewnia, że eksportowane jest tylko pierwsze wystąpienie zakładek w nagłówkach i stopkach.

## Krok 3: Zapisz dokument jako PDF

Na koniec zapisz dokument w formacie PDF, korzystając z skonfigurowanych opcji.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

W tym kroku zapiszesz dokument w określonej ścieżce z wybranymi przez siebie opcjami.

## Wniosek

masz to! Wykonując te kroki, możesz łatwo eksportować zakładki z nagłówków i stopek dokumentu Word do pliku PDF przy użyciu Aspose.Words dla .NET. Ta metoda zapewnia, że ważne pomoce nawigacyjne w dokumencie są zachowywane w formacie PDF, ułatwiając czytelnikom nawigację po dokumencie.

## Najczęściej zadawane pytania

### Czy mogę wyeksportować wszystkie zakładki z dokumentu Word do pliku PDF?

 Tak, możesz. W`PdfSaveOptions`, jeśli zajdzie taka potrzeba, możesz dostosować ustawienia tak, aby uwzględnić wszystkie zakładki.

### A co jeśli chcę wyeksportować zakładki również z treści dokumentu?

 Możesz skonfigurować`OutlineOptions` W`PdfSaveOptions` aby uwzględnić zakładki z treści dokumentu.

### Czy w pliku PDF można dostosować poziomy zakładek?

 Oczywiście! Możesz dostosować`DefaultBookmarksOutlineLevel` właściwość umożliwiająca ustawienie różnych poziomów obrysu zakładek.

### Jak postępować z dokumentami bez zakładek?

Jeśli Twój dokument nie ma zakładek, plik PDF zostanie wygenerowany bez żadnego zarysu zakładek. Upewnij się, że dokument zawiera zakładki, jeśli potrzebujesz ich w pliku PDF.

### Czy mogę użyć tej metody do innych typów dokumentów, np. DOCX lub RTF?

Tak, Aspose.Words dla platformy .NET obsługuje różne typy dokumentów, w tym DOCX, RTF i inne.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
