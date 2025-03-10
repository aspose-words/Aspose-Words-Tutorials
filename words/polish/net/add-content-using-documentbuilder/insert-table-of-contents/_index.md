---
title: Wstaw spis treści do dokumentu Word
linktitle: Wstaw spis treści do dokumentu Word
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak wstawić spis treści w programie Word za pomocą Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby płynnie poruszać się po dokumencie.
weight: 10
url: /pl/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw spis treści do dokumentu Word

## Wstęp
tym samouczku dowiesz się, jak skutecznie dodawać spis treści (TOC) do dokumentów Word za pomocą Aspose.Words dla .NET. Ta funkcja jest niezbędna do organizowania i nawigacji po długich dokumentach, zwiększania czytelności i zapewniania szybkiego przeglądu sekcji dokumentu.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

- Podstawowa znajomość języka C# i środowiska .NET.
- Na Twoim komputerze zainstalowano program Visual Studio.
-  Biblioteka Aspose.Words dla .NET. Jeśli jeszcze jej nie zainstalowałeś, możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/net/).

## Importuj przestrzenie nazw

Aby rozpocząć, zaimportuj niezbędne przestrzenie nazw do swojego projektu C#:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Podzielmy ten proces na jasne kroki:

## Krok 1: Zainicjuj dokument Aspose.Words i DocumentBuilder

 Najpierw zainicjuj nowy Aspose.Words`Document` obiekt i`DocumentBuilder` pracować z:

```csharp
// Zainicjuj dokument i DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Wstaw spis treści

 Teraz wstaw spis treści za pomocą`InsertTableOfContents` metoda:

```csharp
// Wstaw spis treści
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Krok 3: Rozpocznij tworzenie zawartości dokumentu na nowej stronie

Aby zapewnić właściwe formatowanie, zacznij pisać właściwą treść dokumentu na nowej stronie:

```csharp
// Wstaw podział strony
builder.InsertBreak(BreakType.PageBreak);
```

## Krok 4: Ustrukturyzuj swój dokument za pomocą nagłówków

Zorganizuj zawartość dokumentu, stosując odpowiednie style nagłówków:

```csharp
// Ustaw style nagłówków
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## Krok 5: Aktualizacja i uzupełnienie spisu treści

Zaktualizuj spis treści, aby odzwierciedlał strukturę dokumentu:

```csharp
// Zaktualizuj pola spisu treści
doc.UpdateFields();
```

## Krok 6: Zapisz dokument

Na koniec zapisz dokument w określonym katalogu:

```csharp
// Zapisz dokument
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Wniosek

Dodawanie spisu treści za pomocą Aspose.Words dla .NET jest proste i znacznie zwiększa użyteczność dokumentów. Postępując zgodnie z tymi krokami, możesz sprawnie organizować i poruszać się po złożonych dokumentach.

## Najczęściej zadawane pytania

### Czy mogę dostosować wygląd spisu treści?
Tak, możesz dostosować wygląd i zachowanie spisu treści przy użyciu interfejsów API Aspose.Words for .NET.

### Czy Aspose.Words obsługuje automatyczną aktualizację pól?
Tak, Aspose.Words pozwala na dynamiczną aktualizację pól, takich jak spis treści, na podstawie zmian w dokumencie.

### Czy mogę wygenerować wiele spisów treści w jednym dokumencie?
Aspose.Words umożliwia generowanie wielu spisów treści z różnymi ustawieniami w ramach jednego dokumentu.

### Czy Aspose.Words jest kompatybilny z różnymi wersjami programu Microsoft Word?
Tak, Aspose.Words zapewnia zgodność z różnymi wersjami formatów Microsoft Word.

### Gdzie mogę znaleźć dodatkową pomoc i wsparcie dla Aspose.Words?
 Aby uzyskać dalszą pomoc, odwiedź stronę[Forum Aspose.Words](https://forum.aspose.com/c/words/8) lub sprawdź[oficjalna dokumentacja](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
