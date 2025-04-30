---
"description": "Dowiedz się, jak ustawić kierunek tekstu dokumentu w programie Word za pomocą Aspose.Words dla .NET dzięki temu przewodnikowi krok po kroku. Idealne do obsługi języków pisanych od prawej do lewej."
"linktitle": "Kierunek tekstu dokumentu"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Kierunek tekstu dokumentu"
"url": "/pl/net/programming-with-txtloadoptions/document-text-direction/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kierunek tekstu dokumentu

## Wstęp

Podczas pracy z dokumentami Word, zwłaszcza tymi zawierającymi wiele języków lub wymagającymi specjalnego formatowania, ustawienie kierunku tekstu może być kluczowe. Na przykład, w przypadku języków pisanych od prawej do lewej, takich jak hebrajski lub arabski, może być konieczne odpowiednie dostosowanie kierunku tekstu. W tym przewodniku pokażemy, jak ustawić kierunek tekstu dokumentu za pomocą Aspose.Words dla .NET. 

## Wymagania wstępne

Zanim zagłębimy się w kod, upewnij się, że masz następujące elementy:

- Biblioteka Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Możesz ją pobrać ze strony [Strona internetowa Aspose](https://releases.aspose.com/words/net/).
- Visual Studio: środowisko programistyczne do pisania i wykonywania kodu C#.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# będzie przydatna, ponieważ będziemy pisać kod.

## Importuj przestrzenie nazw

Na początek musisz zaimportować niezbędne przestrzenie nazw do pracy z Aspose.Words w swoim projekcie. Oto, jak możesz to zrobić:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

Te przestrzenie nazw zapewniają dostęp do klas i metod niezbędnych do manipulowania dokumentami programu Word.

## Krok 1: Określ ścieżkę do katalogu dokumentów

Najpierw ustaw ścieżkę do miejsca, w którym znajduje się Twój dokument. Jest to kluczowe dla prawidłowego ładowania i zapisywania plików.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` rzeczywistą ścieżką, pod którą przechowywany jest Twój dokument.

## Krok 2: Utwórz TxtLoadOptions z ustawieniem kierunku dokumentu

Następnie musisz utworzyć instancję `TxtLoadOptions` i ustawiłem `DocumentDirection` Właściwość. Informuje Aspose.Words, jak obsługiwać kierunek tekstu w dokumencie.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

W tym przykładzie używamy `DocumentDirection.Auto` aby Aspose.Words automatycznie określiło kierunek na podstawie zawartości.

## Krok 3: Załaduj dokument

Teraz załaduj dokument za pomocą `Document` klasa i wcześniej zdefiniowane `loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

Tutaj, `"Hebrew text.txt"` jest nazwą twojego pliku tekstowego. Upewnij się, że ten plik istnieje w twoim określonym katalogu.

## Krok 4: Dostęp i sprawdzenie dwukierunkowego formatowania akapitu

Aby sprawdzić, czy kierunek tekstu jest ustawiony poprawnie, należy otworzyć pierwszy akapit dokumentu i sprawdzić jego formatowanie dwukierunkowe.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

Ten krok jest przydatny przy debugowaniu i sprawdzaniu, czy kierunek tekstu w dokumencie został zastosowany zgodnie z oczekiwaniami.

## Krok 5: Zapisz dokument z nowymi ustawieniami

Na koniec zapisz dokument, aby zastosować i zapisać zmiany.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

Tutaj, `"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` jest nazwą pliku wyjściowego. Upewnij się, że wybierzesz nazwę odzwierciedlającą zmiany, które wprowadziłeś.

## Wniosek

Ustawianie kierunku tekstu w dokumentach Word to prosty proces dzięki Aspose.Words dla .NET. Wykonując te kroki, możesz łatwo skonfigurować sposób, w jaki dokument obsługuje tekst od prawej do lewej lub od lewej do prawej. Niezależnie od tego, czy pracujesz z dokumentami wielojęzycznymi, czy potrzebujesz sformatować kierunek tekstu dla określonych języków, Aspose.Words zapewnia solidne rozwiązanie, które spełni Twoje potrzeby.

## Najczęściej zadawane pytania

### Co to jest `DocumentDirection` nieruchomość wykorzystana do?

Ten `DocumentDirection` nieruchomość w `TxtLoadOptions` określa kierunek tekstu w dokumencie. Można go ustawić na `DocumentDirection.Auto`, `DocumentDirection.LeftToRight`, Lub `DocumentDirection.RightToLeft`.

### Czy mogę ustawić kierunek tekstu dla konkretnych akapitów, a nie dla całego dokumentu?

Tak, możesz ustawić kierunek tekstu dla konkretnych akapitów za pomocą `ParagraphFormat.Bidi` nieruchomość, ale `TxtLoadOptions.DocumentDirection` Właściwość ustawia domyślny kierunek dla całego dokumentu.

### Jakie formaty plików są obsługiwane do ładowania za pomocą `TxtLoadOptions`?

`TxtLoadOptions` jest używany głównie do ładowania plików tekstowych (.txt). W przypadku innych formatów plików należy używać innych klas, takich jak `DocLoadOptions` Lub `DocxLoadOptions`.

### Jak radzić sobie z dokumentami zawierającymi mieszane kierunki tekstu?

W przypadku dokumentów z mieszanymi kierunkami tekstu może być konieczne formatowanie na podstawie akapitu. Użyj `ParagraphFormat.Bidi` właściwość umożliwiająca dostosowanie kierunku każdego akapitu według potrzeb.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Words dla .NET?

Więcej szczegółów znajdziesz tutaj [Dokumentacja Aspose.Words dla .NET](https://reference.aspose.com/words/net/). Możesz również zapoznać się z dodatkowymi zasobami, takimi jak [Link do pobrania](https://releases.aspose.com/words/net/), [Kupić](https://purchase.aspose.com/buy), [Bezpłatna wersja próbna](https://releases.aspose.com/), [Licencja tymczasowa](https://purchase.aspose.com/temporary-license/), I [Wsparcie](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}