---
"description": "Dowiedz się, jak dodawać kod ogrodzony i ciągi informacyjne do dokumentów Word za pomocą Aspose.Words dla .NET. W zestawie przewodnik krok po kroku. Udoskonal swoje umiejętności formatowania dokumentów."
"linktitle": "Kod ogrodzony"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Kod ogrodzony"
"url": "/pl/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kod ogrodzony

## Wstęp

Cześć, kolego programisto! Dzisiaj zanurzamy się w świat Aspose.Words dla .NET, aby opanować sztukę dodawania kodu ogrodzonego i kodu ogrodzonego z ciągami informacyjnymi do dokumentów Word. Wyobraź sobie swój dokument Word jako płótno, a Ty, artysta, będziesz malował z precyzją doświadczonego programisty. Dzięki Aspose.Words zyskujesz możliwość programowego ulepszania dokumentów za pomocą ustrukturyzowanych, sformatowanych bloków kodu, dzięki czemu Twoje dokumenty techniczne będą lśnić profesjonalizmem i przejrzystością.

## Wymagania wstępne

Zanim przejdziemy do samouczka, upewnijmy się, że masz wszystko, czego potrzebujesz:

- Podstawowa znajomość języka C#: Ogólna znajomość języka C# pomoże Ci szybko zrozumieć podstawowe koncepcje.
- Aspose.Words dla .NET: Musisz mieć zainstalowany Aspose.Words dla .NET. Jeśli jeszcze go nie masz, pobierz go [Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Visual Studio lub inne środowisko programistyczne C#, z którym czujesz się pewnie.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw. To tak, jakbyś zebrał wszystkie swoje narzędzia przed rozpoczęciem projektu.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Teraz przeanalizujmy ten proces krok po kroku.

## Krok 1: Konfigurowanie projektu

Zanim będziemy mogli tworzyć piękne, sformatowane bloki kodu w dokumencie programu Word, musimy skonfigurować nowy projekt w programie Visual Studio.

1. Utwórz nowy projekt: Otwórz program Visual Studio i utwórz nową aplikację konsolową C#.
2. Dodaj Aspose.Words Odniesienie: Zainstaluj Aspose.Words za pomocą Menedżera pakietów NuGet. Możesz to zrobić, klikając prawym przyciskiem myszy na swój projekt w Eksploratorze rozwiązań, wybierając „Zarządzaj pakietami NuGet” i wyszukując Aspose.Words.

## Krok 2: Zainicjuj DocumentBuilder

Teraz, gdy Twój projekt jest już skonfigurowany, zainicjujmy DocumentBuilder, który będzie naszym głównym narzędziem służącym do dodawania treści do dokumentu Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 3: Utwórz styl dla kodu ogrodzonego

Aby dodać kod ogrodzony, najpierw musimy utworzyć styl. Pomyśl o tym jako o ustawieniu motywu dla naszego bloku kodu.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Krok 4: Dodaj kod ogrodzony do dokumentu

Mając już gotowy styl, możemy dodać do dokumentu ogrodzony blok kodu.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Krok 5: Utwórz styl dla kodu Fenced z ciągiem informacyjnym

Czasami możesz chcieć określić język programowania lub dodać dodatkowe informacje do swojego bloku kodu. Stwórzmy styl dla tego.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Krok 6: Dodaj kod ogrodzony z ciągiem informacyjnym do dokumentu

Teraz dodajmy ogrodzony blok kodu z ciągiem informacyjnym wskazującym, że jest to kod C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Wniosek

Gratulacje! Właśnie dodałeś ogrodzone bloki kodu i ogrodzone kody z ciągami informacyjnymi do swoich dokumentów Word za pomocą Aspose.Words dla .NET. To tylko wierzchołek góry lodowej. Dzięki Aspose.Words możesz zautomatyzować i ulepszyć przetwarzanie dokumentów do nowych wyżyn. Kontynuuj eksplorację i miłego kodowania!

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programistom programowe tworzenie, edytowanie i konwertowanie dokumentów Word.

### Czy mogę używać Aspose.Words z innymi językami programowania?
Aspose.Words obsługuje przede wszystkim języki .NET, ale dostępne są wersje dla języków Java, Python i innych.

### Czy korzystanie z Aspose.Words jest bezpłatne?
Aspose.Words to produkt komercyjny, ale możesz pobrać bezpłatną wersję próbną [Tutaj](https://releases.aspose.com/) aby poznać jego funkcje.

### Jak mogę uzyskać pomoc dotyczącą Aspose.Words?
Możesz uzyskać wsparcie od społeczności i deweloperów Aspose [Tutaj](https://forum.aspose.com/c/words/8).

### Jakie inne funkcje oferuje Aspose.Words?
Aspose.Words oferuje szeroką gamę funkcji, w tym konwersję dokumentów, generowanie dokumentów na podstawie szablonów, raportowanie i wiele innych.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}