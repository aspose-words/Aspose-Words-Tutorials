---
"description": "Dowiedz się, jak ustawić znaki podkreślenia czcionki w dokumentach Worda za pomocą Aspose.Words dla .NET dzięki temu szczegółowemu przewodnikowi krok po kroku. Idealne dla programistów .NET."
"linktitle": "Ustaw znak podkreślenia czcionki"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Ustaw znak podkreślenia czcionki"
"url": "/pl/net/working-with-fonts/set-font-emphasis-mark/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw znak podkreślenia czcionki

## Wstęp

dzisiejszym samouczku zagłębimy się w to, jak ustawić znaki podkreślenia czcionki w dokumencie Word za pomocą Aspose.Words dla .NET. Niezależnie od tego, czy chcesz podkreślić konkretny tekst unikalnym znakiem, czy po prostu wyróżnić pewne słowa, ten przewodnik Ci pomoże. Więc zapnij pasy i zaczynajmy!

## Wymagania wstępne

Zanim zagłębimy się w szczegóły, upewnij się, że spełniasz następujące wymagania wstępne:

- Biblioteka Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Możesz ją pobrać z [Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: działające środowisko programistyczne, takie jak Visual Studio.
- .NET Framework: Upewnij się, że masz zainstalowany .NET Framework.

## Importuj przestrzenie nazw

Aby pracować z Aspose.Words dla .NET, musisz zaimportować niezbędne przestrzenie nazw. Dodaj je na górze pliku kodu:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Teraz podzielmy proces na proste kroki. Dokładnie wykonaj każdy krok, aby ustawić znaki podkreślenia czcionki w dokumencie Word.

## Krok 1: Zainicjuj dokument i DocumentBuilder

Po pierwsze, musisz zainicjować nowy dokument i DocumentBuilder. Klasa DocumentBuilder udostępnia metody wstawiania tekstu i innych elementów do dokumentu.

```csharp
// Ścieżka do katalogu dokumentów 
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Zainicjuj nowy dokument
Document document = new Document();

// Zainicjuj DocumentBuilder za pomocą dokumentu
DocumentBuilder builder = new DocumentBuilder(document);
```

## Krok 2: Ustaw znacznik podkreślenia czcionki

Gdy DocumentBuilder jest gotowy, możesz teraz ustawić znak podkreślenia czcionki. W tym przykładzie użyjemy znaku podkreślenia „UnderSolidCircle”.

```csharp
// Ustaw znak podkreślenia czcionki
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// Napisz tekst ze znakiem podkreślenia
builder.Write("Emphasis text");
builder.Writeln();
```

## Krok 3: Wyczyść formatowanie i dodaj zwykły tekst

Po ustawieniu znaku podkreślenia możesz chcieć dodać zwykły tekst bez żadnego podkreślenia. W tym celu musisz wyczyścić formatowanie.

```csharp
// Wyczyść formatowanie czcionki
builder.Font.ClearFormatting();

// Napisz zwykły tekst
builder.Write("Simple text");
```

## Krok 4: Zapisz dokument

Po dodaniu całego potrzebnego tekstu i formatowania ostatnim krokiem jest zapisanie dokumentu. Określ ścieżkę i nazwę pliku, w którym chcesz zapisać dokument.

```csharp
// Zapisz dokument
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## Wniosek

I masz! Ustawianie wyróżnień czcionki w dokumencie Word za pomocą Aspose.Words dla .NET jest tak proste. Za pomocą zaledwie kilku linijek kodu możesz wyróżnić swój tekst i dodać profesjonalny akcent do swoich dokumentów. Nie wahaj się eksperymentować z różnymi wyróżnieniami i stylami, aby dopasować je do swoich potrzeb.

## Najczęściej zadawane pytania

### Czym są znaki podkreślenia czcionki?

Znaki podkreślenia czcionki to specjalne symbole dodawane do tekstu, aby go wyróżnić. Mogą to być kropki, okręgi i inne znaki dekoracyjne.

### Czy mogę używać innych znaków podkreślenia w Aspose.Words dla .NET?

Tak, Aspose.Words dla .NET obsługuje różne znaki podkreślenia. Możesz zbadać różne opcje, odnosząc się do [dokumentacja](https://reference.aspose.com/words/net/).

### Czy korzystanie z Aspose.Words dla .NET jest bezpłatne?

Aspose.Words dla .NET wymaga licencji dla pełnej funkcjonalności. Możesz otrzymać bezpłatną wersję próbną [Tutaj](https://releases.aspose.com/) lub kup licencję [Tutaj](https://purchase.aspose.com/buy).

### Jak mogę uzyskać pomoc techniczną dotyczącą Aspose.Words dla .NET?

Możesz uzyskać pomoc od społeczności Aspose i zespołu wsparcia, odwiedzając ich stronę [forum wsparcia](https://forum.aspose.com/c/words/8).

### Czy mogę używać Aspose.Words dla .NET z innymi frameworkami .NET?

Tak, Aspose.Words dla .NET jest kompatybilny z różnymi platformami .NET, w tym .NET Core i .NET 5/6.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}