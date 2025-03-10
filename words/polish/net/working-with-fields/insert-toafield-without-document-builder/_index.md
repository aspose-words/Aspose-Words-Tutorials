---
title: Wstaw pole TOA bez tworzenia dokumentów
linktitle: Wstaw pole TOA bez tworzenia dokumentów
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak wstawić pole TOA bez użycia konstruktora dokumentów w Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby skutecznie zarządzać cytatami prawnymi.
weight: 10
url: /pl/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw pole TOA bez tworzenia dokumentów

## Wstęp

Tworzenie pola spisu autorytetów (TOA) w dokumencie Word może przypominać składanie skomplikowanej układanki. Jednak dzięki Aspose.Words dla .NET proces ten staje się płynny i prosty. W tym artykule przeprowadzimy Cię przez kroki wstawiania pola TOA bez użycia kreatora dokumentów, ułatwiając Ci zarządzanie cytowaniami i odniesieniami prawnymi w dokumentach Word.

## Wymagania wstępne

Zanim przejdziemy do samouczka, omówmy podstawowe rzeczy, których będziesz potrzebować:

-  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną najnowszą wersję. Możesz ją pobrać ze strony[Strona internetowa Aspose](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: środowisko IDE zgodne z platformą .NET, np. Visual Studio.
- Podstawowa wiedza o języku C#: Przydatna będzie znajomość podstawowej składni i pojęć języka C#.
- Przykładowy dokument Word: Utwórz lub przygotuj przykładowy dokument, w którym chcesz wstawić pole TOA.

## Importuj przestrzenie nazw

Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw z biblioteki Aspose.Words. Ta konfiguracja zapewnia dostęp do wszystkich klas i metod wymaganych do manipulacji dokumentami.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Podzielmy proces na proste, łatwe do naśladowania kroki. Przeprowadzimy Cię przez każdy etap, wyjaśniając, co robi każdy fragment kodu i jak przyczynia się do tworzenia pola TOA.

## Krok 1: Zainicjuj dokument

 Najpierw musisz utworzyć instancję`Document` Klasa. Ten obiekt reprezentuje dokument Word, nad którym pracujesz.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Ten kod inicjuje nowy dokument Word. Możesz to sobie wyobrazić jako tworzenie pustego płótna, do którego dodasz swoją treść.

## Krok 2: Utwórz i skonfiguruj pole TA

Następnie dodamy pole TA (Table of Authorities). To pole oznacza wpisy, które pojawią się w TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Chcemy wstawić pola TA i TOA w następujący sposób:
// { TA \c 1 \l "Wartość 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Oto szczegółowe informacje:
- Akapit para = nowy Akapit(doc);: Tworzy nowy akapit w dokumencie.
-  FieldTA poleTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Dodaje pole TA do akapitu. The`FieldType.FieldTOAEntry` określa, że jest to pole wprowadzania TOA.
- fieldTA.EntryCategory = "1";: Ustawia kategorię wpisu. Jest to przydatne do kategoryzowania różnych typów wpisów.
- fieldTA.LongCitation = "Value 0";: Określa tekst długiego cytowania. Jest to tekst, który pojawi się w TOA.
- doc.FirstSection.Body.AppendChild(para);: Dołącza akapit z polem TA do treści dokumentu.

## Krok 3: Dodaj pole TOA

Teraz wstawimy rzeczywiste pole TOA, które kompiluje wszystkie wpisy TA do tabeli.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

W tym kroku:
- FieldToa FieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Dodaje pole TOA do akapitu.
- fieldToa.EntryCategory = "1";: Filtruje wpisy, aby uwzględnić tylko te oznaczone kategorią „1”.

## Krok 4: Zaktualizuj pole TOA

Po wstawieniu pola TOA należy je zaktualizować, aby mieć pewność, że odzwierciedla najnowsze wpisy.

```csharp
fieldToa.Update();
```

To polecenie odświeża pole TOA, zapewniając prawidłowe wyświetlanie wszystkich oznaczonych wpisów w tabeli.

## Krok 5: Zapisz dokument

Na koniec zapisz dokument z nowo dodanym polem TOA.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 Ta linia kodu zapisuje dokument do określonego katalogu. Upewnij się, że zastąpiłeś`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą chcesz zapisać plik.

## Wniosek

I masz! Udało Ci się dodać pole TOA do dokumentu Word bez użycia kreatora dokumentów. Wykonując te kroki, możesz sprawnie zarządzać cytowaniami i tworzyć kompleksowe tabele autorytetów w swoich dokumentach prawnych. Aspose.Words dla .NET sprawia, że ten proces jest płynny i wydajny, zapewniając narzędzia do łatwego radzenia sobie ze złożonymi zadaniami związanymi z dokumentami.

## Najczęściej zadawane pytania

### Czy mogę dodać wiele pól TA z różnymi kategoriami?
 Tak, możesz dodać wiele pól TA z różnymi kategoriami, ustawiając`EntryCategory`odpowiednio nieruchomość.

### Jak mogę dostosować wygląd TOA?
Możesz dostosować wygląd TOA, modyfikując właściwości pola TOA, takie jak formatowanie wpisu i etykiety kategorii.

### Czy istnieje możliwość automatycznej aktualizacji pola TOA?
 Chociaż pole TOA można zaktualizować ręcznie za pomocą`Update` Metoda ta, Aspose.Words nie obsługuje obecnie automatycznych aktualizacji po zmianach w dokumencie.

### Czy mogę programowo dodać pola TA w określonych częściach dokumentu?
Tak, możesz dodać pola TA w określonych miejscach, wstawiając je do wybranych akapitów lub sekcji.

### Jak obsługiwać wiele pól TOA w jednym dokumencie?
 Możesz zarządzać wieloma polami TOA, przypisując im różne`EntryCategory` wartości i zapewnienie, że każde pole TOA filtruje wpisy na podstawie swojej kategorii.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
