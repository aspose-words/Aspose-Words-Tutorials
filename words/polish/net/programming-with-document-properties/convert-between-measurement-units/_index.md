---
title: Konwersja między jednostkami miary
linktitle: Konwersja między jednostkami miary
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak konwertować jednostki miary w Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby ustawić marginesy dokumentu, nagłówki i stopki w calach i punktach.
weight: 10
url: /pl/net/programming-with-document-properties/convert-between-measurement-units/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konwersja między jednostkami miary

## Wstęp

Cześć! Czy jesteś programistą pracującym z dokumentami Worda przy użyciu Aspose.Words dla .NET? Jeśli tak, często musisz ustawiać marginesy, nagłówki lub stopki w różnych jednostkach miary. Konwersja między jednostkami, takimi jak cale i punkty, może być trudna, jeśli nie znasz funkcjonalności biblioteki. W tym kompleksowym samouczku przeprowadzimy Cię przez proces konwersji między jednostkami miary przy użyciu Aspose.Words dla .NET. Zanurzmy się i uprośćmy te konwersje!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1.  Biblioteka Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, pobierz ją[Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub inne środowisko IDE zgodne z platformą .NET.
3. Podstawowa wiedza o języku C#: Zrozumienie podstaw języka C# ułatwi Ci naukę.
4.  Licencja Aspose: Opcjonalna, ale zalecana do pełnej funkcjonalności. Możesz uzyskać tymczasową licencję[Tutaj](https://purchase.aspose.com/temporary-license/).

## Importuj przestrzenie nazw

Najpierw musisz zaimportować niezbędne przestrzenie nazw. Jest to kluczowe dla dostępu do klas i metod udostępnianych przez Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

Omówmy proces konwersji jednostek miary w Aspose.Words dla .NET. Wykonaj poniższe szczegółowe kroki, aby skonfigurować i dostosować marginesy i odległości w dokumencie.

## Krok 1: Utwórz nowy dokument

Najpierw musisz utworzyć nowy dokument za pomocą Aspose.Words.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Inicjuje nowy dokument Word i`DocumentBuilder` aby ułatwić tworzenie i formatowanie treści.

## Krok 2: Dostęp do ustawień strony

 Aby ustawić marginesy, nagłówki i stopki, należy uzyskać dostęp do`PageSetup` obiekt.

```csharp
PageSetup pageSetup = builder.PageSetup;
```

Dzięki temu uzyskujesz dostęp do różnych właściwości ustawień strony, takich jak marginesy, odległość nagłówka i odległość stopki.

## Krok 3: Konwersja cali na punkty

 Aspose.Words domyślnie używa punktów jako jednostki miary. Aby ustawić marginesy w calach, musisz przekonwertować cale na punkty za pomocą`ConvertUtil.InchToPoint` metoda.

```csharp
pageSetup.TopMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.BottomMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.LeftMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.RightMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.HeaderDistance = ConvertUtil.InchToPoint(0.2);
pageSetup.FooterDistance = ConvertUtil.InchToPoint(0.2);
```

Oto opis działania każdego wiersza:
- Ustawia górny i dolny margines na 1 cal (przeliczony na punkty).
- Ustawia marginesy lewy i prawy na 1,5 cala (w punktach).
- Ustawia odległość nagłówka i stopki na 0,2 cala (przeliczone na punkty).

## Krok 4: Zapisz dokument

Na koniec zapisz dokument, aby mieć pewność, że wszystkie zmiany zostaną zastosowane.

```csharp
doc.Save("ConvertedDocument.docx");
```

Zapisuje dokument z określonymi marginesami i odległościami w punktach.

## Wniosek

I masz! Udało Ci się przekonwertować i ustawić marginesy i odległości w dokumencie Word za pomocą Aspose.Words dla .NET. Postępując zgodnie z tymi krokami, możesz łatwo obsługiwać różne konwersje jednostek, dzięki czemu proces dostosowywania dokumentu będzie dziecinnie prosty. Eksperymentuj z różnymi ustawieniami i odkrywaj rozległe funkcjonalności, jakie oferuje Aspose.Words. Miłego kodowania!

## Najczęściej zadawane pytania

### Czy mogę przekonwertować inne jednostki, np. centymetry, na punkty przy użyciu Aspose.Words?
 Tak, Aspose.Words udostępnia metody takie jak`ConvertUtil.CmToPoint` do zamiany centymetrów na punkty.

### Czy do korzystania z Aspose.Words dla .NET potrzebna jest licencja?
Chociaż możesz używać Aspose.Words bez licencji, niektóre zaawansowane funkcje mogą być ograniczone. Uzyskanie licencji zapewnia pełną funkcjonalność.

### Jak zainstalować Aspose.Words dla .NET?
 Można go pobrać ze strony[strona internetowa](https://releases.aspose.com/words/net/) i postępuj zgodnie z instrukcją instalacji.

### Czy mogę ustawić różne jednostki dla różnych sekcji dokumentu?
 Tak, możesz dostosować marginesy i inne ustawienia dla różnych sekcji, korzystając z`Section` klasa.

### Jakie inne funkcje oferuje Aspose.Words?
 Aspose.Words obsługuje szeroki zakres funkcji, w tym konwersję dokumentów, scalanie korespondencji i rozbudowane opcje formatowania. Sprawdź[dokumentacja](https://reference.aspose.com/words/net/) Aby uzyskać więcej szczegółów.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
