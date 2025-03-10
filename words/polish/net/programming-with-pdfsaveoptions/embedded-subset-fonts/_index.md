---
title: Osadź podzbiory czcionek w dokumencie PDF
linktitle: Osadź podzbiory czcionek w dokumencie PDF
second_title: Aspose.Words API przetwarzania dokumentów
description: Zmniejsz rozmiar pliku PDF, osadzając tylko niezbędne podzbiory czcionek za pomocą Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby skutecznie zoptymalizować pliki PDF.
weight: 10
url: /pl/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Osadź podzbiory czcionek w dokumencie PDF

## Wstęp

Czy zauważyłeś kiedyś, że niektóre pliki PDF są dużo większe od innych, nawet jeśli zawierają podobną treść? Winowajcą często są czcionki. Osadzanie czcionek w pliku PDF zapewnia, że wygląda on tak samo na każdym urządzeniu, ale może również zwiększyć rozmiar pliku. Na szczęście Aspose.Words dla .NET oferuje przydatną funkcję osadzania tylko niezbędnych podzbiorów czcionek, dzięki czemu pliki PDF są szczupłe i wydajne. Ten samouczek przeprowadzi Cię przez ten proces krok po kroku.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

-  Aspose.Words dla .NET: Można go pobrać[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko .NET: Upewnij się, że posiadasz działające środowisko programistyczne .NET.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# ułatwi Ci zrozumienie tematu.

## Importuj przestrzenie nazw

Aby użyć Aspose.Words dla .NET, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Dodaj je na górze pliku C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Załaduj dokument

 Najpierw musimy załadować dokument Word, który chcemy przekonwertować do formatu PDF. Robi się to za pomocą`Document` Klasa udostępniona przez Aspose.Words.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Ten fragment kodu ładuje dokument znajdujący się pod adresem`dataDir` . Upewnij się, że wymienisz`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do dokumentu.

## Krok 2: Skonfiguruj opcje zapisywania pliku PDF

 Następnie konfigurujemy`PdfSaveOptions` aby zapewnić, że osadzone zostaną tylko niezbędne podzbiory czcionek. Poprzez ustawienie`EmbedFullFonts` Do`false`, informujemy Aspose.Words, aby osadzał wyłącznie glify używane w dokumencie.

```csharp
// Wyjściowy plik PDF będzie zawierał podzbiory czcionek użytych w dokumencie.
// W czcionkach PDF uwzględniono wyłącznie znaki użyte w dokumencie.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Ten mały, ale istotny krok pomaga znacząco zmniejszyć rozmiar pliku PDF.

## Krok 3: Zapisz dokument jako PDF

 Na koniec zapisujemy dokument w formacie PDF za pomocą`Save` metoda, stosując skonfigurowaną`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 Ten kod wygeneruje plik PDF o nazwie`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` w określonym katalogu, z osadzonymi tylko niezbędnymi podzbiorami czcionek.

## Wniosek

masz to! Postępując zgodnie z tymi prostymi krokami, możesz skutecznie zmniejszyć rozmiar plików PDF, osadzając tylko niezbędne podzbiory czcionek za pomocą Aspose.Words dla .NET. To nie tylko oszczędza miejsce na dysku, ale także zapewnia szybsze czasy ładowania i lepszą wydajność, szczególnie w przypadku dokumentów z rozbudowanymi czcionkami.

## Najczęściej zadawane pytania

### Dlaczego w pliku PDF warto osadzać wyłącznie podzbiory czcionek?
Osadzanie wyłącznie niezbędnych podzbiorów czcionek może znacząco zmniejszyć rozmiar pliku PDF bez pogorszenia wyglądu i czytelności dokumentu.

### Czy w razie potrzeby mogę powrócić do osadzania pełnych czcionek?
 Tak, możesz. Po prostu ustaw`EmbedFullFonts`nieruchomość do`true` w`PdfSaveOptions`.

### Czy Aspose.Words dla .NET obsługuje inne funkcje optymalizacji plików PDF?
Oczywiście! Aspose.Words dla .NET oferuje szereg opcji optymalizacji plików PDF, w tym kompresję obrazu i usuwanie nieużywanych obiektów.

### Jakie typy czcionek można osadzać w podzbiorach za pomocą Aspose.Words dla .NET?
Aspose.Words dla platformy .NET obsługuje osadzanie podzbiorów dla wszystkich czcionek TrueType używanych w dokumencie.

### Jak mogę sprawdzić, które czcionki są osadzone w moim pliku PDF?
Możesz otworzyć plik PDF w programie Adobe Acrobat Reader i sprawdzić właściwości na karcie Czcionki, aby zobaczyć osadzone czcionki.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
