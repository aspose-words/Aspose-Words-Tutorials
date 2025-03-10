---
title: Komentarz kotwicy
linktitle: Komentarz kotwicy
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak dodawać komentarze kotwicowe w dokumentach Worda za pomocą Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby wydajnie współpracować nad dokumentami.
weight: 10
url: /pl/net/working-with-comments/anchor-comment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Komentarz kotwicy

## Wstęp

Czy kiedykolwiek znalazłeś się w sytuacji, w której musiałeś programowo dodać komentarze do określonych sekcji tekstu w dokumencie Word? Wyobraź sobie, że współpracujesz nad dokumentem ze swoim zespołem i musisz wyróżnić pewne części komentarzami, aby inni mogli je przejrzeć. W tym samouczku zagłębimy się w sposób wstawiania komentarzy kotwicowych w dokumentach Word za pomocą Aspose.Words dla .NET. Podzielimy proces na proste kroki, dzięki czemu będziesz mógł łatwo śledzić i wdrażać je w swoich projektach.

## Wymagania wstępne

Zanim zaczniemy, upewnijmy się, że masz wszystko, czego potrzebujesz:

-  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words. Możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: dowolne środowisko programistyczne .NET, np. Visual Studio.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# pomoże Ci z łatwością wykonywać poniższe kroki.

Przyjrzyjmy się teraz przestrzeniom nazw, które będziesz musiał zaimportować w ramach tego zadania.

## Importuj przestrzenie nazw

Na początek upewnij się, że importujesz niezbędne przestrzenie nazw do swojego projektu. Oto wymagane przestrzenie nazw:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.CommentRangeStart;
using Aspose.Words.CommentRangeEnd;
```

Mając już za sobą wymagania wstępne i przestrzenie nazw, możemy przejść do przyjemniejszej części: omówienia procesu krok po kroku.

## Krok 1: Utwórz nowy dokument

Najpierw utwórzmy nowy dokument Word. Będzie on służył jako płótno dla naszych komentarzy.

```csharp
// Zdefiniuj katalog, w którym zostanie zapisany dokument
string dataDir = "YOUR DOCUMENT DIRECTORY";        

// Utwórz instancję klasy Document
Document doc = new Document();
```

 W tym kroku inicjujemy nowy`Document` obiekt, który będzie używany do dodawania naszych komentarzy.

## Krok 2: Dodaj tekst do dokumentu

Następnie dodamy trochę tekstu do dokumentu. Ten tekst będzie celem naszych komentarzy.

```csharp
// Utwórz pierwszy akapit i uruchom
Paragraph para1 = new Paragraph(doc);
Run run1 = new Run(doc, "Some ");
Run run2 = new Run(doc, "text ");
para1.AppendChild(run1);
para1.AppendChild(run2);
doc.FirstSection.Body.AppendChild(para1);

// Utwórz drugi akapit i uruchom
Paragraph para2 = new Paragraph(doc);
Run run3 = new Run(doc, "is ");
Run run4 = new Run(doc, "added ");
para2.AppendChild(run3);
para2.AppendChild(run4);
doc.FirstSection.Body.AppendChild(para2);
```

 Tutaj tworzymy dwa akapity z tekstem. Każdy fragment tekstu jest zamknięty w`Run` obiekt, który następnie jest dodawany do akapitów.

## Krok 3: Utwórz komentarz

Teraz utwórzmy komentarz, który dodamy do naszego tekstu.

```csharp
// Utwórz nowy komentarz
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
comment.SetText("Comment text.");
```

 W tym kroku tworzymy`Comment` obiekt i dodaj akapit oraz ciąg z tekstem komentarza.

## Krok 4: Zdefiniuj zakres komentarzy

Aby zakotwiczyć komentarz w określonym tekście, musimy zdefiniować początek i koniec zakresu komentarza.

```csharp
// Zdefiniuj CommentRangeStart i CommentRangeEnd
CommentRangeStart commentRangeStart = new CommentRangeStart(doc, comment.Id);
CommentRangeEnd commentRangeEnd = new CommentRangeEnd(doc, comment.Id);

// Wstaw CommentRangeStart i CommentRangeEnd do dokumentu
run1.ParentNode.InsertAfter(commentRangeStart, run1);
run3.ParentNode.InsertAfter(commentRangeEnd, run3);

// Dodaj komentarz do dokumentu
commentRangeEnd.ParentNode.InsertAfter(comment, commentRangeEnd);
```

 Tutaj tworzymy`CommentRangeStart` I`CommentRangeEnd` obiektów, łącząc je z komentarzem poprzez jego ID. Następnie wstawiamy te zakresy do dokumentu, skutecznie zakotwiczając nasz komentarz do określonego tekstu.

## Krok 5: Zapisz dokument

Na koniec zapiszmy nasz dokument w podanym katalogu.

```csharp
// Zapisz dokument
doc.Save(dataDir + "WorkingWithComments.AnchorComment.doc");
```

Ten krok powoduje zapisanie dokumentu z zakotwiczonym komentarzem w określonym katalogu.

## Wniosek

I masz to! Udało Ci się nauczyć, jak dodawać komentarze kotwiczące do określonych sekcji tekstu w dokumencie Word za pomocą Aspose.Words dla .NET. Ta technika jest niezwykle przydatna do współpracy nad dokumentami, umożliwiając łatwe wyróżnianie i komentowanie określonych części tekstu. Niezależnie od tego, czy pracujesz nad projektem ze swoim zespołem, czy przeglądasz dokumenty, ta metoda zwiększy Twoją produktywność i usprawni Twój przepływ pracy.

## Najczęściej zadawane pytania

### Jaki jest cel stosowania komentarzy kotwicowych w dokumentach Word?
Komentarze kotwiczące służą do wyróżniania i komentowania określonych fragmentów tekstu, co ułatwia przekazywanie opinii i współpracę nad dokumentami.

### Czy mogę dodać wiele komentarzy do tej samej sekcji tekstowej?
Tak, możesz dodać wiele komentarzy do tej samej sekcji tekstowej, definiując wiele zakresów komentarzy.

### Czy korzystanie z Aspose.Words dla .NET jest bezpłatne?
 Aspose.Words dla .NET oferuje bezpłatną wersję próbną, którą można pobrać[Tutaj](https://releases.aspose.com/) Aby uzyskać pełną funkcjonalność, możesz zakupić licencję[Tutaj](https://purchase.aspose.com/buy).

### Czy mogę dostosować wygląd komentarzy?
Podczas gdy Aspose.Words koncentruje się na funkcjonalności, wygląd komentarzy w dokumentach Worda jest generalnie kontrolowany przez sam Word.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?
 Szczegółową dokumentację można znaleźć[Tutaj](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
