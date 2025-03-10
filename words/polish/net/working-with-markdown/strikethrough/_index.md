---
title: Przekreślenie
linktitle: Przekreślenie
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak stosować formatowanie przekreślone do tekstu za pomocą Aspose.Words dla .NET dzięki naszemu przewodnikowi krok po kroku. Udoskonal swoje umiejętności przetwarzania dokumentów.
weight: 10
url: /pl/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przekreślenie

## Wstęp

Witamy w tym szczegółowym przewodniku dotyczącym stosowania formatowania przekreślonego do tekstu za pomocą Aspose.Words dla .NET. Jeśli chcesz udoskonalić swoje umiejętności przetwarzania dokumentów i dodać tekstowi wyjątkowego charakteru, jesteś we właściwym miejscu. Zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

-  Aspose.Words dla .NET: Pobierz[Tutaj](https://releases.aspose.com/words/net/).
- .NET Framework: Upewnij się, że w systemie jest zainstalowany .NET Framework.
- Środowisko programistyczne: IDE, np. Visual Studio.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest konieczna.

## Importuj przestrzenie nazw

Na początek musisz zaimportować niezbędne przestrzenie nazw. Są one niezbędne do uzyskania dostępu do biblioteki Aspose.Words i jej funkcji.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Zainicjuj DocumentBuilder

 Ten`DocumentBuilder` class to potężne narzędzie w Aspose.Words, które umożliwia łatwe dodawanie treści do dokumentu.

```csharp
// Zainicjuj DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Ustaw właściwość przekreślenia

Teraz zastosujmy właściwość przekreślenia do naszego tekstu. Wiąże się to z ustawieniem`StrikeThrough` własność`Font` oponować`true`.

```csharp
// Przekreśl tekst.
builder.Font.StrikeThrough = true;
```

## Krok 3: Napisz tekst z przekreśleniem

 Po ustawieniu właściwości przekreślenia możemy teraz dodać nasz tekst.`Writeln` Metoda doda tekst do dokumentu.

```csharp
// Napisz tekst przekreślając go.
builder.Writeln("This text will be StrikeThrough");
```

## Wniosek

I masz! Udało Ci się dodać formatowanie przekreślenia do tekstu za pomocą Aspose.Words dla .NET. Ta potężna biblioteka otwiera świat możliwości przetwarzania i dostosowywania dokumentów. Niezależnie od tego, czy tworzysz raporty, listy czy jakikolwiek inny rodzaj dokumentu, opanowanie tych funkcji niewątpliwie zwiększy Twoją produktywność i jakość Twoich wyników.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka do przetwarzania dokumentów, która umożliwia programistom programistyczne tworzenie, modyfikowanie i konwertowanie dokumentów Word.

### Czy mogę używać Aspose.Words dla .NET w projekcie komercyjnym?
 Tak, możesz używać Aspose.Words dla .NET w projektach komercyjnych. Aby uzyskać opcje zakupu, odwiedź stronę[kup stronę](https://purchase.aspose.com/buy).

### Czy jest dostępna bezpłatna wersja próbna Aspose.Words dla .NET?
 Tak, możesz pobrać bezpłatną wersję próbną[Tutaj](https://releases.aspose.com/).

### Jak uzyskać pomoc techniczną dotyczącą Aspose.Words dla platformy .NET?
Możesz uzyskać wsparcie od społeczności Aspose i ekspertów na[forum wsparcia](https://forum.aspose.com/c/words/8).

### Czy mogę zastosować inne opcje formatowania tekstu, używając Aspose.Words dla .NET?
Oczywiście! Aspose.Words dla .NET obsługuje szeroki zakres opcji formatowania tekstu, w tym pogrubienie, kursywę, podkreślenie i wiele innych.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
