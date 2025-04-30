---
"description": "Dowiedz się, jak skonfigurować funkcję jednostek miary w Aspose.Words dla platformy .NET, aby zachować formatowanie dokumentu podczas konwersji ODT."
"linktitle": "Jednostka miary"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Jednostka miary"
"url": "/pl/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jednostka miary

## Wstęp

Czy kiedykolwiek musiałeś przekonwertować dokumenty Worda do różnych formatów, ale potrzebowałeś konkretnej jednostki miary dla swojego układu? Niezależnie od tego, czy masz do czynienia z calami, centymetrami czy punktami, zapewnienie, że dokument zachowuje integralność podczas procesu konwersji, jest kluczowe. W tym samouczku pokażemy, jak skonfigurować funkcję jednostki miary w Aspose.Words dla .NET. Ta potężna funkcja zapewnia, że formatowanie dokumentu zostanie zachowane dokładnie tak, jak potrzebujesz podczas konwersji do formatu ODT (Open Document Text).

## Wymagania wstępne

Zanim zagłębisz się w kod, musisz wykonać kilka czynności:

1. Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną najnowszą wersję Aspose.Words dla .NET. Jeśli jeszcze jej nie masz, możesz ją pobrać z [Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: środowisko IDE, takie jak Visual Studio, umożliwiające pisanie i wykonywanie kodu C#.
3. Podstawowa wiedza o języku C#: Zrozumienie podstaw języka C# pomoże Ci zrozumieć treść samouczka.
4. Dokument Word: Przygotuj przykładowy dokument Word, którego możesz użyć do konwersji.

## Importuj przestrzenie nazw

Zanim zaczniemy kodować, upewnijmy się, że mamy zaimportowane niezbędne przestrzenie nazw. Dodaj te dyrektywy using na górze pliku kodu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Skonfiguruj katalog dokumentów

Najpierw musisz zdefiniować ścieżkę do katalogu dokumentów. To jest miejsce, w którym znajduje się dokument Word i gdzie zostanie zapisany przekonwertowany plik.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Zastępować `"YOUR DOCUMENTS DIRECTORY"` z rzeczywistą ścieżką do Twojego katalogu. Dzięki temu Twój kod będzie wiedział, gdzie znaleźć Twój dokument Word.

## Krok 2: Załaduj dokument Word

Następnie musisz załadować dokument Word, który chcesz przekonwertować. Można to zrobić za pomocą `Document` klasa z Aspose.Words.

```csharp
// Załaduj dokument Word
Document doc = new Document(dataDir + "Document.docx");
```

Upewnij się, że dokument Word o nazwie „Dokument.docx” znajduje się w określonym katalogu.

## Krok 3: Skonfiguruj jednostkę miary

Teraz skonfigurujmy jednostkę miary dla konwersji ODT. To tutaj dzieje się magia. Skonfigurujemy `OdtSaveOptions` używać cali jako jednostki miary.

```csharp
// Konfiguracja opcji tworzenia kopii zapasowej z funkcją „Jednostka miary”
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

W tym przykładzie ustawiamy jednostkę miary na cale. Możesz również wybrać inne jednostki, takie jak `OdtSaveMeasureUnit.Centimeters` Lub `OdtSaveMeasureUnit.Points` w zależności od Twoich wymagań.

## Krok 4: Konwertuj dokument do formatu ODT

Na koniec przekonwertujemy dokument Word do formatu ODT, korzystając z skonfigurowanego `OdtSaveOptions`.

```csharp
// Konwertuj dokument do formatu ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Ta linia kodu zapisuje przekonwertowany dokument w określonym katalogu z zastosowaną nową jednostką miary.

## Wniosek

masz to! Wykonując te kroki, możesz łatwo skonfigurować funkcję jednostki miary w Aspose.Words dla .NET, aby mieć pewność, że układ dokumentu zostanie zachowany podczas konwersji. Niezależnie od tego, czy pracujesz z calami, centymetrami czy punktami, ten samouczek pokazał Ci, jak z łatwością przejąć kontrolę nad formatowaniem dokumentu.

## Często zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to potężna biblioteka do programowej pracy z dokumentami Word. Umożliwia ona programistom tworzenie, modyfikowanie, konwertowanie i przetwarzanie dokumentów Word bez konieczności korzystania z programu Microsoft Word.

### Czy mogę używać innych jednostek miary niż cale?
Tak, Aspose.Words dla .NET obsługuje inne jednostki miary, takie jak centymetry i punkty. Możesz określić żądaną jednostkę za pomocą `OdtSaveMeasureUnit` wyliczenie.

### Czy jest dostępna bezpłatna wersja próbna Aspose.Words dla .NET?
Tak, możesz pobrać bezpłatną wersję próbną Aspose.Words dla .NET ze strony [Tutaj](https://releases.aspose.com/).

### Gdzie mogę znaleźć dokumentację Aspose.Words dla .NET?
Pełną dokumentację Aspose.Words dla .NET można uzyskać pod adresem [ten link](https://reference.aspose.com/words/net/).

### Jak mogę uzyskać pomoc techniczną dotyczącą Aspose.Words dla .NET?
Aby uzyskać pomoc, możesz odwiedzić forum Aspose.Words pod adresem [ten link](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}