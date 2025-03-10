---
title: Wykryj numerację z odstępami
linktitle: Wykryj numerację z odstępami
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak używać Aspose.Words for .NET do wykrywania numeracji zawierającej spacje w dokumentach zwykłego tekstu i mieć pewność, że Twoje listy będą prawidłowo rozpoznawane.
weight: 10
url: /pl/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wykryj numerację z odstępami

## Wstęp

Aspose.Words dla entuzjastów .NET! Dzisiaj zagłębimy się w fascynującą funkcję, która może sprawić, że obsługa list w dokumentach tekstowych stanie się dziecinnie prosta. Czy kiedykolwiek miałeś do czynienia z plikami tekstowymi, w których niektóre wiersze powinny być listami, ale po załadowaniu do dokumentu Worda po prostu nie wyglądają dobrze? Cóż, mamy w zanadrzu sprytny trik: wykrywanie numeracji z odstępami. Ten samouczek przeprowadzi Cię przez sposób korzystania z`DetectNumberingWithWhitespaces` opcja w Aspose.Words dla .NET zapewniająca prawidłowe rozpoznawanie list, nawet gdy między liczbami i tekstem występuje spacja.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

-  Aspose.Words dla .NET: Można go pobrać ze strony[Wydania Aspose](https://releases.aspose.com/words/net/) strona.
- Środowisko programistyczne: Visual Studio lub inne środowisko IDE C#.
- .NET Framework zainstalowany na Twoim komputerze.
- Podstawowa wiedza o języku C#: Zrozumienie podstaw ułatwi Ci zrozumienie przykładów.

## Importuj przestrzenie nazw

Zanim zaczniesz kodować, upewnij się, że masz zaimportowane niezbędne przestrzenie nazw do swojego projektu. Oto krótki fragment kodu, który pomoże Ci zacząć:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Podzielmy proces na proste, łatwe do opanowania kroki. Każdy krok przeprowadzi Cię przez niezbędny kod i wyjaśni, co się dzieje.

## Krok 1: Zdefiniuj katalog dokumentów

Po pierwsze, ustawmy ścieżkę do katalogu dokumentów. To tutaj będą przechowywane pliki wejściowe i wyjściowe.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Utwórz dokument w formacie zwykłego tekstu

Następnie utworzymy dokument w postaci zwykłego tekstu jako ciąg. Ten dokument będzie zawierał części, które można interpretować jako listy.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Krok 3: Skonfiguruj LoadOptions

 Aby wykryć numerację z odstępami, musimy ustawić`DetectNumberingWithWhitespaces` opcja do`true` w`TxtLoadOptions` obiekt.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Krok 4: Załaduj dokument

 Teraz załadujmy dokument za pomocą`TxtLoadOptions` jako parametr. Zapewnia to, że czwarta lista (z odstępami) zostanie wykryta poprawnie.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Krok 5: Zapisz dokument

Na koniec zapisz dokument w określonym katalogu. Spowoduje to wygenerowanie dokumentu Word z prawidłowo wykrytymi listami.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Wniosek

masz to! Za pomocą zaledwie kilku linijek kodu opanowałeś sztukę wykrywania numeracji z odstępami w dokumentach zwykłego tekstu za pomocą Aspose.Words dla .NET. Ta funkcja może być niezwykle przydatna podczas pracy z różnymi formatami tekstu i zapewniania, że listy są dokładnie reprezentowane w dokumentach Word. Więc następnym razem, gdy natkniesz się na te trudne listy, będziesz dokładnie wiedział, co zrobić.

## Najczęściej zadawane pytania

###  Co to jest`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` jest opcją w`TxtLoadOptions` co pozwala Aspose.Words rozpoznawać listy nawet wtedy, gdy między numeracją a tekstem elementu listy występuje spacja.

### Czy mogę używać tej funkcji w przypadku innych rozgraniczników, np. punktorów i nawiasów?
 Tak, Aspose.Words automatycznie wykrywa listy z typowymi ogranicznikami, takimi jak punkty i nawiasy.`DetectNumberingWithWhitespaces` pomaga szczególnie w przypadku list zawierających spacje.

###  Co się stanie, jeśli nie użyję`DetectNumberingWithWhitespaces`?
Bez tej opcji listy zawierające odstępy między numeracją i tekstem mogłyby nie zostać rozpoznane jako listy, a elementy mogłyby zostać wyświetlone jako zwykłe akapity.

### Czy ta funkcja jest dostępna w innych produktach Aspose?
Ta konkretna funkcja jest dostosowana do środowiska Aspose.Words for .NET i służy do przetwarzania dokumentów Word.

### Jak mogę uzyskać tymczasową licencję na Aspose.Words dla .NET?
 Możesz uzyskać tymczasową licencję od[Licencja tymczasowa Aspose](https://purchase.aspose.com/temporary-license/) strona.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
