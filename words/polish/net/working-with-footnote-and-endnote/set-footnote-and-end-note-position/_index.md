---
"description": "Dowiedz się, jak ustawiać położenie przypisów dolnych i końcowych w dokumentach programu Word za pomocą narzędzia Aspose.Words dla platformy .NET, korzystając z tego szczegółowego przewodnika krok po kroku."
"linktitle": "Ustaw pozycję przypisu dolnego i końcowego"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Ustaw pozycję przypisu dolnego i końcowego"
"url": "/pl/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw pozycję przypisu dolnego i końcowego

## Wstęp

Jeśli pracujesz z dokumentami Worda i musisz skutecznie zarządzać przypisami dolnymi i końcowymi, Aspose.Words for .NET jest Twoją biblioteką docelową. Ten samouczek przeprowadzi Cię przez ustawianie pozycji przypisów dolnych i końcowych w dokumencie Worda przy użyciu Aspose.Words for .NET. Podzielimy każdy krok, aby ułatwić śledzenie i wdrażanie.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że posiadasz następujące rzeczy:

- Biblioteka Aspose.Words dla .NET: Można ją pobrać ze strony [Tutaj](https://releases.aspose.com/words/net/).
- Visual Studio: każda nowsza wersja będzie działać dobrze.
- Podstawowa wiedza o języku C#: Zrozumienie podstaw ułatwi Ci naukę.

## Importuj przestrzenie nazw

Najpierw zaimportuj niezbędne przestrzenie nazw do swojego projektu C#:

```csharp
using System;
using Aspose.Words;
```

## Krok 1: Załaduj dokument Word

Aby rozpocząć, musisz załadować dokument Word do obiektu Aspose.Words Document. Pozwoli ci to manipulować zawartością dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

W tym kodzie zamień `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, gdzie znajduje się Twój dokument.

## Krok 2: Ustaw pozycję przypisu

Następnie ustawisz pozycję przypisów. Aspose.Words dla .NET pozwala na pozycjonowanie przypisów na dole strony lub pod tekstem.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Tutaj ustawiliśmy przypisy tak, aby pojawiały się pod tekstem. Jeśli wolisz, aby znajdowały się na dole strony, użyj `FootnotePosition.BottomOfPage`.

## Krok 3: Ustaw położenie przypisu końcowego

Podobnie możesz ustawić pozycję przypisów końcowych. Przypisy końcowe mogą być umieszczone na końcu sekcji lub na końcu dokumentu.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

W tym przykładzie przypisy końcowe są umieszczane na końcu każdej sekcji. Aby umieścić je na końcu dokumentu, użyj `EndnotePosition.EndOfDocument`.

## Krok 4: Zapisz dokument

Na koniec zapisz dokument, aby zastosować zmiany. Upewnij się, że określiłeś prawidłową ścieżkę pliku i nazwę dla dokumentu wyjściowego.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Ten wiersz zapisuje zmodyfikowany dokument w podanym katalogu.

## Wniosek

Ustawianie pozycji przypisów dolnych i końcowych w dokumentach Word za pomocą Aspose.Words dla .NET jest proste, gdy znasz już kroki. Postępując zgodnie z tym przewodnikiem, możesz dostosować swoje dokumenty do swoich potrzeb, zapewniając, że przypisy dolne i końcowe będą umieszczone dokładnie tam, gdzie chcesz.

## Najczęściej zadawane pytania

### Czy mogę ustawić różne pozycje dla poszczególnych przypisów dolnych i końcowych?

Nie, Aspose.Words dla platformy .NET ustala położenie wszystkich przypisów dolnych i końcowych w dokumencie w jednolity sposób.

### Czy Aspose.Words dla .NET jest kompatybilny ze wszystkimi wersjami dokumentów Word?

Tak, Aspose.Words dla .NET obsługuje szeroką gamę formatów dokumentów Word, w tym DOC, DOCX, RTF i inne.

### Czy mogę używać Aspose.Words dla .NET z innymi językami programowania?

Aspose.Words for .NET jest przeznaczony dla aplikacji .NET, ale można go używać z dowolnym językiem obsługiwanym przez platformę .NET, takim jak C#, VB.NET itp.

### Czy jest dostępna bezpłatna wersja próbna Aspose.Words dla .NET?

Tak, możesz otrzymać bezpłatną wersję próbną [Tutaj](https://releases.aspose.com/).

### Gdzie mogę znaleźć bardziej szczegółową dokumentację Aspose.Words dla .NET?

Dostępna jest szczegółowa dokumentacja [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}