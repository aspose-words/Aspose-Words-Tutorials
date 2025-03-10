---
title: Utwórz nagłówek i stopkę
linktitle: Utwórz nagłówek i stopkę
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak dodawać i dostosowywać nagłówki i stopki w dokumentach Word za pomocą Aspose.Words dla .NET. Ten przewodnik krok po kroku zapewnia profesjonalne formatowanie dokumentów.
weight: 10
url: /pl/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz nagłówek i stopkę

## Wstęp

Dodawanie nagłówków i stopek do dokumentów może zwiększyć ich profesjonalizm i czytelność. Dzięki Aspose.Words dla .NET możesz łatwo tworzyć i dostosowywać nagłówki i stopki do dokumentów Word. W tym samouczku przeprowadzimy Cię przez proces krok po kroku, zapewniając, że będziesz mógł bezproblemowo wdrożyć te funkcje.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

-  Aspose.Words dla .NET: Pobierz i zainstaluj z[link do pobrania](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: takie jak Visual Studio, do pisania i uruchamiania kodu.
- Podstawowa wiedza o języku C#: zrozumienie języka C# i platformy .NET.
- Przykładowy dokument: Przykładowy dokument służący do stosowania nagłówków i stopek lub tworzenia nowego dokumentu, tak jak pokazano w samouczku.

## Importuj przestrzenie nazw

Najpierw musisz zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do klas i metod Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Krok 1: Zdefiniuj katalog dokumentów

Zdefiniuj katalog, w którym zostanie zapisany Twój dokument. Pomaga to w efektywnym zarządzaniu ścieżką.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Krok 2: Utwórz nowy dokument

 Utwórz nowy dokument i`DocumentBuilder`aby ułatwić dodawanie treści.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Skonfiguruj ustawienia strony

Skonfiguruj ustawienia strony, w tym to, czy pierwsza strona ma mieć inny nagłówek/stopkę.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Krok 4: Dodaj nagłówek do pierwszej strony

Przejdź do sekcji nagłówka pierwszej strony i skonfiguruj tekst nagłówka.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Krok 5: Dodaj nagłówek główny

Przejdź do głównej sekcji nagłówka i wstaw obraz oraz tekst.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Wstaw obraz do nagłówka
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Krok 6: Dodaj główną stopkę

Przejdź do głównej sekcji stopki i utwórz tabelę, aby sformatować zawartość stopki.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Dodaj numerację stron
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Krok 7: Dodaj zawartość i podziały stron

Przejdź na koniec dokumentu, dodaj podział strony i utwórz nową sekcję z innymi ustawieniami strony.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Krok 8: Skopiuj nagłówki i stopki z poprzedniej sekcji

Jeśli chcesz ponownie wykorzystać nagłówki i stopki z poprzedniej sekcji, skopiuj je i zastosuj niezbędne modyfikacje.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Wniosek

Wykonując te kroki, możesz skutecznie dodawać i dostosowywać nagłówki i stopki w dokumentach Word za pomocą Aspose.Words dla .NET. Poprawia to wygląd i profesjonalizm dokumentu, czyniąc go bardziej czytelnym i angażującym.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?

Aspose.Words for .NET to biblioteka umożliwiająca programistom tworzenie, edycję i konwertowanie dokumentów Word programowo w aplikacjach .NET.

### Czy mogę dodać obrazy do nagłówka lub stopki?

 Tak, możesz łatwo dodać obrazy do nagłówka lub stopki, korzystając z`DocumentBuilder.InsertImage` metoda.

### Jak ustawić różne nagłówki i stopki dla pierwszej strony?

 Możesz ustawić różne nagłówki i stopki dla pierwszej strony, używając`DifferentFirstPageHeaderFooter` własność`PageSetup` klasa.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words?

 Pełną dokumentację można znaleźć na stronie[Strona dokumentacji API Aspose.Words](https://reference.aspose.com/words/net/).

### Czy jest dostępne wsparcie dla Aspose.Words?

 Tak, Aspose oferuje wsparcie poprzez swoje[forum wsparcia](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
