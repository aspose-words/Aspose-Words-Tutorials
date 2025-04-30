---
"description": "Dowiedz się, jak zablokować proporcje kształtów w dokumentach Word za pomocą Aspose.Words dla .NET. Postępuj zgodnie z tym przewodnikiem krok po kroku, aby zachować proporcje obrazów i kształtów."
"linktitle": "Zablokowany współczynnik proporcji"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Zablokowany współczynnik proporcji"
"url": "/pl/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zablokowany współczynnik proporcji

## Wstęp

Czy kiedykolwiek zastanawiałeś się, jak zachować idealne proporcje obrazów i kształtów w dokumentach Word? Czasami musisz upewnić się, że obrazy i kształty nie zostaną zniekształcone podczas zmiany rozmiaru. W tym miejscu przydaje się blokowanie współczynnika proporcji. W tym samouczku pokażemy, jak ustawić współczynnik proporcji kształtów w dokumentach Word za pomocą Aspose.Words dla .NET. Podzielimy to na łatwe do wykonania kroki, upewniając się, że możesz zastosować te umiejętności w swoich projektach z pewnością siebie.

## Wymagania wstępne

Zanim zagłębimy się w kod, omówmy, co będzie potrzebne, aby zacząć:

- Biblioteka Aspose.Words dla .NET: Musisz mieć zainstalowaną bibliotekę Aspose.Words dla .NET. Jeśli jeszcze tego nie zrobiłeś, możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Upewnij się, że masz skonfigurowane środowisko programistyczne .NET. Visual Studio jest popularnym wyborem.
- Podstawowa wiedza o języku C#: Przydatna będzie pewna znajomość programowania w języku C#.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw. Te przestrzenie nazw zapewnią nam dostęp do klas i metod, których potrzebujemy do pracy z dokumentami i kształtami Worda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Skonfiguruj katalog dokumentów

Zanim zaczniemy manipulować kształtami, musimy utworzyć katalog, w którym będą przechowywane nasze dokumenty. Dla uproszczenia użyjemy symbolu zastępczego `YOUR DOCUMENT DIRECTORY`. Zastąp to rzeczywistą ścieżką do katalogu dokumentów.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Utwórz nowy dokument

Następnie utworzymy nowy dokument Word za pomocą Aspose.Words. Ten dokument będzie naszym płótnem do dodawania kształtów i obrazów.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tutaj tworzymy instancję `Document` klasa i użyj `DocumentBuilder` aby pomóc nam w tworzeniu treści dokumentu.

## Krok 3: Wstaw obraz

Teraz wstawmy obraz do naszego dokumentu. Użyjemy `InsertImage` metoda `DocumentBuilder` klasa. Upewnij się, że masz obraz w określonym katalogu.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Zastępować `dataDir + "Transparent background logo.png"` ze ścieżką do pliku obrazu.

## Krok 4: Zablokuj proporcje obrazu

Po wstawieniu obrazu możemy zablokować jego współczynnik proporcji. Zablokowanie współczynnika proporcji zapewnia, że proporcje obrazu pozostaną stałe podczas zmiany rozmiaru.

```csharp
shape.AspectRatioLocked = true;
```

Ustawienie `AspectRatioLocked` Do `true` zapewnia zachowanie oryginalnych proporcji obrazu.

## Krok 5: Zapisz dokument

Na koniec zapiszemy dokument w określonym katalogu. Ten krok zapisze wszystkie zmiany, które wprowadziliśmy do pliku dokumentu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Wniosek

Gratulacje! Udało Ci się nauczyć, jak ustawić proporcje kształtów w dokumentach Word za pomocą Aspose.Words dla .NET. Postępując zgodnie z tymi krokami, możesz mieć pewność, że Twoje obrazy i kształty zachowają swoje proporcje, dzięki czemu Twoje dokumenty będą wyglądać profesjonalnie i dopracowane. Możesz swobodnie eksperymentować z różnymi obrazami i kształtami, aby zobaczyć, jak funkcja blokowania proporcji działa w różnych scenariuszach.

## Najczęściej zadawane pytania

### Czy mogę odblokować proporcje obrazu po jego zablokowaniu?
Tak, możesz odblokować współczynnik proporcji, ustawiając `shape.AspectRatioLocked = false`.

### Co się stanie, jeśli zmienię rozmiar obrazu o zablokowanych proporcjach?
Obraz zostanie proporcjonalnie zmieniony, zachowując oryginalny stosunek szerokości do wysokości.

### Czy mogę zastosować to do innych kształtów niż obrazy?
Oczywiście! Funkcja blokowania proporcji może być stosowana do dowolnego kształtu, w tym prostokątów, okręgów i innych.

### Czy Aspose.Words dla .NET jest kompatybilny z .NET Core?
Tak, Aspose.Words dla .NET obsługuje zarówno .NET Framework, jak i .NET Core.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?
Można znaleźć kompleksową dokumentację [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}