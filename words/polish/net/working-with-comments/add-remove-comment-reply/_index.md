---
title: Dodaj Usuń Komentarz Odpowiedz
linktitle: Dodaj Usuń Komentarz Odpowiedz
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak dodawać i usuwać odpowiedzi na komentarze w dokumentach programu Word przy użyciu Aspose.Words dla platformy .NET. Ulepsz współpracę nad dokumentami dzięki temu przewodnikowi krok po kroku.
weight: 10
url: /pl/net/working-with-comments/add-remove-comment-reply/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj Usuń Komentarz Odpowiedz

## Wstęp

Praca z komentarzami i ich odpowiedziami w dokumentach Word może znacznie usprawnić proces przeglądu dokumentów. Dzięki Aspose.Words for .NET możesz zautomatyzować te zadania, dzięki czemu Twój przepływ pracy będzie bardziej wydajny i usprawniony. Ten samouczek przeprowadzi Cię przez dodawanie i usuwanie odpowiedzi na komentarze, zapewniając przewodnik krok po kroku, jak opanować tę funkcję.

## Wymagania wstępne

Zanim zagłębisz się w kod, upewnij się, że masz następujące elementy:

-  Aspose.Words dla .NET: Pobierz i zainstaluj z[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Visual Studio lub inne środowisko IDE obsługujące platformę .NET.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest niezbędna.

## Importuj przestrzenie nazw

Aby rozpocząć, zaimportuj niezbędne przestrzenie nazw do swojego projektu C#:

```csharp
using System;
using Aspose.Words;
```

## Krok 1: Załaduj swój dokument Word

Najpierw musisz załadować dokument Word zawierający komentarze, którymi chcesz zarządzać. W tym przykładzie zakładamy, że masz dokument o nazwie „Comments.docx” w swoim katalogu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

## Krok 2: Uzyskaj dostęp do pierwszego komentarza

Następnie przejdź do pierwszego komentarza w dokumencie. Ten komentarz będzie celem dodawania i usuwania odpowiedzi.

```csharp
Comment comment = (Comment)doc.GetChild(NodeType.Comment, 0, true);
```

## Krok 3: Usuń istniejącą odpowiedź

Jeśli komentarz ma już odpowiedzi, możesz chcieć usunąć jedną. Oto jak możesz usunąć pierwszą odpowiedź komentarza:

```csharp
comment.RemoveReply(comment.Replies[0]);
```

## Krok 4: Dodaj nową odpowiedź

Teraz dodajmy nową odpowiedź do komentarza. Możesz określić nazwisko autora, inicjały, datę i godzinę odpowiedzi oraz tekst odpowiedzi.

```csharp
comment.AddReply("John Doe", "JD", new DateTime(2017, 9, 25, 12, 15, 0), "New reply");
```

## Krok 5: Zapisz zaktualizowany dokument

Na koniec zapisz zmodyfikowany dokument w swoim katalogu.

```csharp
doc.Save(dataDir + "WorkingWithComments.AddRemoveCommentReply.docx");
```

## Wniosek

Zarządzanie odpowiedziami na komentarze w dokumentach Word programowo może zaoszczędzić Ci dużo czasu i wysiłku, zwłaszcza w przypadku obszernych recenzji. Aspose.Words dla .NET sprawia, że proces ten jest prosty i wydajny. Postępując zgodnie z krokami opisanymi w tym przewodniku, możesz łatwo dodawać i usuwać odpowiedzi na komentarze, ulepszając swoje doświadczenie współpracy nad dokumentami.

## Najczęściej zadawane pytania

### Jak dodać wiele odpowiedzi do jednego komentarza?

 Możesz dodać wiele odpowiedzi do jednego komentarza, dzwoniąc pod numer`AddReply` wielokrotnie na tym samym obiekcie komentarza.

### Czy mogę dostosować dane autora do każdej odpowiedzi?

 Tak, możesz określić imię i nazwisko autora, inicjały oraz datę i godzinę każdej odpowiedzi, korzystając z`AddReply` metoda.

### Czy można usunąć wszystkie odpowiedzi z komentarza jednocześnie?

Aby usunąć wszystkie odpowiedzi, należy przejść przez pętlę`Replies` Zbierz komentarze i usuń każdy z nich osobno.

### Czy mogę uzyskać dostęp do komentarzy w konkretnej sekcji dokumentu?

 Tak, możesz poruszać się po sekcjach dokumentu i uzyskiwać dostęp do komentarzy w każdej sekcji, korzystając z`GetChild` metoda.

### Czy Aspose.Words dla platformy .NET obsługuje inne funkcje związane z komentarzami?

Tak, Aspose.Words for .NET zapewnia szerokie wsparcie dla różnych funkcji związanych z komentarzami, w tym dodawanie nowych komentarzy, ustawianie właściwości komentarzy i wiele innych.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
