---
title: Włącz Wyłącz podstawianie czcionek
linktitle: Włącz Wyłącz podstawianie czcionek
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak włączyć lub wyłączyć podstawianie czcionek w dokumentach Word za pomocą Aspose.Words dla .NET. Upewnij się, że Twoje dokumenty wyglądają spójnie na wszystkich platformach.
weight: 10
url: /pl/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Włącz Wyłącz podstawianie czcionek

## Wstęp

Czy kiedykolwiek znalazłeś się w sytuacji, w której starannie wybrane czcionki w dokumencie Worda są zastępowane podczas przeglądania na innym komputerze? Denerwujące, prawda? Dzieje się tak z powodu podstawiania czcionek, procesu, w którym system zastępuje brakującą czcionkę dostępną czcionką. Ale nie martw się! Dzięki Aspose.Words dla .NET możesz łatwo zarządzać i kontrolować podstawianie czcionek. W tym samouczku przeprowadzimy Cię przez kroki włączania lub wyłączania podstawiania czcionek w dokumentach Worda, zapewniając, że Twoje dokumenty zawsze będą wyglądać dokładnie tak, jak chcesz.

## Wymagania wstępne

Zanim przejdziemy do dalszych kroków, upewnijmy się, że masz wszystko, czego potrzebujesz:

-  Aspose.Words dla .NET: Pobierz najnowszą wersję[Tutaj](https://releases.aspose.com/words/net/).
- Visual Studio: dowolna wersja obsługująca .NET.
- Podstawowa znajomość języka C#: Ułatwi Ci to zrozumienie przykładów kodowania.

## Importuj przestrzenie nazw

Aby rozpocząć, upewnij się, że masz niezbędne przestrzenie nazw zaimportowane do swojego projektu. Dodaj je na górze pliku C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Teraz podzielimy ten proces na proste i łatwe do opanowania kroki.

## Krok 1: Skonfiguruj swój projekt

Najpierw skonfiguruj nowy projekt w Visual Studio i dodaj odwołanie do biblioteki Aspose.Words for .NET. Jeśli jeszcze tego nie zrobiłeś, pobierz ją z[Strona internetowa Aspose](https://releases.aspose.com/words/net/).

## Krok 2: Załaduj swój dokument

Następnie załaduj dokument, z którym chcesz pracować. Oto jak to zrobić:

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Zastępować`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do katalogu dokumentów. Ten kod ładuje dokument do pamięci, dzięki czemu możesz nim manipulować.

## Krok 3: Skonfiguruj ustawienia czcionek

 Teraz utwórzmy`FontSettings` obiekt do zarządzania ustawieniami substytucji czcionek:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Krok 4: Ustaw domyślną zamianę czcionek

Ustaw domyślną zamianę czcionki na czcionkę swojego wyboru. Ta czcionka zostanie użyta, jeśli oryginalna czcionka nie będzie dostępna:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

W tym przykładzie używamy czcionki Arial jako domyślnej.

## Krok 5: Wyłącz podstawianie informacji o czcionkach

Aby wyłączyć podstawianie informacji o czcionkach, dzięki czemu system nie będzie mógł zastąpić brakujących czcionek dostępnymi, użyj następującego kodu:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Krok 6: Zastosuj ustawienia czcionki do dokumentu

Teraz zastosuj te ustawienia do swojego dokumentu:

```csharp
doc.FontSettings = fontSettings;
```

## Krok 7: Zapisz swój dokument

Na koniec zapisz zmodyfikowany dokument. Możesz go zapisać w dowolnym formacie. W tym samouczku zapiszemy go jako PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Wniosek

I masz to! Wykonując te kroki, możesz łatwo kontrolować podmianę czcionek w dokumentach Word za pomocą Aspose.Words dla .NET. Dzięki temu dokumenty zachowują zamierzony wygląd i styl, niezależnie od tego, gdzie są wyświetlane.

## Najczęściej zadawane pytania

### Czy mogę używać czcionek innych niż Arial jako zamienników?

 Oczywiście! Możesz określić dowolną czcionkę dostępną w systemie, zmieniając nazwę czcionki w`DefaultFontName` nieruchomość.

### Co się stanie, jeśli określona domyślna czcionka nie będzie dostępna?

Jeśli domyślna czcionka nie jest dostępna, Aspose.Words użyje mechanizmu zapasowego w celu znalezienia odpowiedniej czcionki zamiennika.

### Czy mogę ponownie włączyć funkcję podstawiania czcionek po jej wyłączeniu?

 Tak, możesz przełączać`Enabled` własność`FontInfoSubstitution` powrót do`true` Jeśli chcesz ponownie włączyć podstawianie czcionek.

### Czy istnieje sposób sprawdzenia, które czcionki są zastępowane?

Tak, Aspose.Words udostępnia metody rejestrowania i śledzenia zastępowania czcionek, dzięki czemu można zobaczyć, które czcionki są zastępowane.

### Czy mogę użyć tej metody do innych formatów dokumentów niż DOCX?

Zdecydowanie! Aspose.Words obsługuje różne formaty i możesz zastosować te ustawienia czcionek do dowolnego obsługiwanego formatu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
