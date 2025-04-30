---
"description": "Dowiedz się, jak wstawiać i konfigurować pola scalania w dokumentach programu Word za pomocą pakietu Aspose.Words dla platformy .NET, korzystając z tego kompleksowego samouczka krok po kroku."
"linktitle": "Wstaw pole scalania za pomocą DOM"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Wstaw pole scalania za pomocą DOM"
"url": "/pl/net/working-with-fields/insert-merge-field-using-dom/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw pole scalania za pomocą DOM

## Wstęp

Jeśli pracujesz z przetwarzaniem dokumentów w .NET, prawdopodobnie natknąłeś się na Aspose.Words. Ta potężna biblioteka oferuje szeroki wachlarz funkcji do programowego manipulowania dokumentami Word. W tym samouczku skupimy się na jednej konkretnej funkcji: wstawianiu pola scalania przy użyciu Document Object Model (DOM) w Aspose.Words dla .NET. Ten przewodnik przeprowadzi Cię przez każdy krok, od konfiguracji środowiska po wstawianie i aktualizowanie pola scalania w dokumencie Word.

## Wymagania wstępne

Zanim zagłębisz się w kod, upewnij się, że masz wszystko, czego potrzebujesz, aby móc korzystać z tego samouczka.

1. Podstawowa znajomość języka C#: Powinieneś swobodnie posługiwać się programowaniem w języku C#.
2. Zainstalowany program Visual Studio: Upewnij się, że na Twoim komputerze zainstalowany jest program Visual Studio lub inne środowisko IDE języka C#.
3. Aspose.Words dla .NET: Pobierz i zainstaluj najnowszą wersję Aspose.Words dla .NET ze strony [Wydania](https://releases.aspose.com/words/net/).
4. Ważna licencja: Jeśli nie masz licencji, możesz ją uzyskać [licencja tymczasowa](https://purchase.aspose.com/temporary-license/) do oceny.

## Krok 1: Skonfiguruj swój projekt

Zacznijmy od utworzenia nowego projektu w programie Visual Studio.

1. Otwórz program Visual Studio.
2. Utwórz nowy projekt: Przejdź do Plik > Nowy > Projekt. Wybierz aplikację konsolową C#.
3. Nazwij swój projekt: Nadaj projektowi znaczącą nazwę i kliknij Utwórz.

## Krok 2: Zainstaluj Aspose.Words

Aby użyć Aspose.Words, musisz dodać go do swojego projektu. Można to zrobić za pomocą NuGet Package Manager.

1. Otwórz Menedżera pakietów NuGet: kliknij prawym przyciskiem myszy swój projekt w Eksploratorze rozwiązań, a następnie wybierz opcję Zarządzaj pakietami NuGet.
2. Wyszukaj Aspose.Words: W Menedżerze pakietów NuGet wyszukaj „Aspose.Words”.
3. Zainstaluj pakiet: Kliknij Zainstaluj, aby dodać Aspose.Words do swojego projektu.

## Krok 3: Importuj przestrzenie nazw

Aby zacząć używać Aspose.Words, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Oto, jak możesz to zrobić:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Krok 4: Zainicjuj swój dokument

Teraz gdy wszystko jest już skonfigurowane, utwórzmy nowy dokument Word i zainicjujmy DocumentBuilder.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Utwórz dokument i DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 5: Przesuń kursor do określonego akapitu

Następnie musimy przenieść kursor do konkretnego akapitu w dokumencie, w którym chcemy wstawić pole scalania.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Krok 6: Wstaw pole scalania

Wstawianie pola scalania jest proste. Użyjemy `InsertField` metoda `DocumentBuilder` klasa.

```csharp
// Wstaw pole scalania.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Krok 7: Skonfiguruj pole scalania

Po wstawieniu pola korespondencji seryjnej możesz ustawić różne właściwości, aby skonfigurować je według swoich potrzeb.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Krok 8: Zaktualizuj i zapisz dokument

Na koniec zaktualizuj pole, aby mieć pewność, że wszystkie ustawienia zostały zastosowane, i zapisz dokument.

```csharp
// Zaktualizuj pole.
field.Update();

// Zapisz dokument.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Wniosek

Wykonując te kroki, możesz łatwo wstawiać i konfigurować pola scalania w dokumencie Word za pomocą Aspose.Words dla .NET. Ten samouczek obejmuje podstawowe kroki od konfiguracji środowiska do zapisania ostatecznego dokumentu. Dzięki Aspose.Words możesz zautomatyzować złożone zadania przetwarzania dokumentów, dzięki czemu Twoje aplikacje .NET będą bardziej wydajne i wydajne.

## Najczęściej zadawane pytania

###  Czym jest pole scalania?
Pole scalania to symbol zastępczy w dokumencie, który można dynamicznie zastąpić danymi ze źródła danych, takiego jak baza danych lub plik CSV.

###  Czy mogę używać Aspose.Words za darmo?
Aspose.Words oferuje bezpłatną wersję próbną, którą możesz pobrać [Tutaj](https://releases.aspose.com/). Do długoterminowego użytkowania należy zakupić licencję.

###  Jak uzyskać tymczasową licencję na Aspose.Words?
Licencję tymczasową można uzyskać na stronie internetowej Aspose [Tutaj](https://purchase.aspose.com/temporary-license/).

### Jakie wersje .NET są obsługiwane przez Aspose.Words?
Aspose.Words obsługuje wiele wersji platformy .NET, w tym .NET Framework, .NET Core i .NET Standard.

###  Gdzie mogę znaleźć dokumentację API dla Aspose.Words?
Dokumentacja API jest dostępna [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}