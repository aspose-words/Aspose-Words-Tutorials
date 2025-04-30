---
"description": "Dowiedz się, jak wstawić pływający obraz do dokumentu Word za pomocą Aspose.Words dla .NET dzięki temu szczegółowemu przewodnikowi krok po kroku. Idealne do ulepszania dokumentów."
"linktitle": "Wstaw obraz pływający do dokumentu Word"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Wstaw obraz pływający do dokumentu Word"
"url": "/pl/net/add-content-using-documentbuilder/insert-floating-image/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw obraz pływający do dokumentu Word

## Wstęp

Wyobraź sobie tworzenie oszałamiającego raportu lub propozycji, w której obrazy są idealnie rozmieszczone, aby uzupełnić tekst. Dzięki Aspose.Words dla .NET możesz to osiągnąć bez wysiłku. Ta biblioteka zapewnia potężne funkcje do manipulacji dokumentami, co czyni ją rozwiązaniem dla programistów. W tym samouczku skupimy się na wstawianiu pływającego obrazu za pomocą klasy DocumentBuilder. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten przewodnik przeprowadzi Cię przez każdy krok.

## Wymagania wstępne

Zanim przejdziemy do konkretów, upewnijmy się, że masz wszystko, czego potrzebujesz, aby zacząć:

1. Aspose.Words dla .NET: Bibliotekę można pobrać ze strony [Strona wydań Aspose](https://releases.aspose.com/words/net/).
2. Visual Studio: dowolna wersja obsługująca programowanie .NET.
3. Podstawowa wiedza o języku C#: Przydatna będzie znajomość podstaw programowania w języku C#.
4. Plik obrazu: Plik obrazu, który chcesz wstawić, np. logo lub zdjęcie.

## Importuj przestrzenie nazw

Aby użyć Aspose.Words w swoim projekcie, musisz zaimportować niezbędne przestrzenie nazw. Można to zrobić, dodając następujące wiersze na górze pliku C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Mając te wymagania wstępne i przestrzenie nazw za sobą, możemy rozpocząć nasz samouczek.

Podzielmy proces wstawiania pływającego obrazu do dokumentu Word na łatwe do opanowania kroki. Każdy krok zostanie szczegółowo wyjaśniony, aby zapewnić, że będziesz mógł go śledzić bez żadnych przeszkód.

## Krok 1: Skonfiguruj swój projekt

Najpierw utwórz nowy projekt C# w Visual Studio. Możesz wybrać aplikację konsolową dla uproszczenia.

1. Otwórz program Visual Studio i utwórz nowy projekt.
2. Wybierz „Aplikacja konsolowa (.NET Core)” i kliknij „Dalej”.
3. Nazwij swój projekt i wybierz lokalizację, w której chcesz go zapisać. Kliknij „Utwórz”.
4. Zainstaluj Aspose.Words dla .NET za pomocą NuGet Package Manager. Kliknij prawym przyciskiem myszy swój projekt w Solution Explorer, wybierz „Manage NuGet Packages” i wyszukaj „Aspose.Words”. Zainstaluj najnowszą wersję.

## Krok 2: Zainicjuj dokument i DocumentBuilder

Teraz gdy Twój projekt jest już skonfigurowany, zainicjujmy obiekty Document i DocumentBuilder.

1. Utwórz nową instancję `Document` klasa:

```csharp
Document doc = new Document();
```

2. Zainicjuj obiekt DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten `Document` obiekt reprezentuje dokument Worda, a `DocumentBuilder` pomaga w dodawaniu do niego treści.

## Krok 3: Zdefiniuj ścieżkę obrazu

Następnie określ ścieżkę do pliku obrazu. Upewnij się, że obraz jest dostępny z katalogu projektu.

Zdefiniuj katalog obrazu i nazwę pliku obrazu:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą przechowywany jest Twój obraz.

## Krok 4: Wstaw obraz pływający

Gdy wszystko jest już skonfigurowane, wstawmy obraz pływający do dokumentu.

Użyj `InsertImage` metoda `DocumentBuilder` klasa do wstawiania obrazu:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Oto co oznacza każdy parametr:
- `imagePath`:Ścieżka do pliku obrazu.
- `RelativeHorizontalPosition.Margin`:Pozycja pozioma względem marginesu.
- `100`:Odchylenie poziome od marginesu (w punktach).
- `RelativeVerticalPosition.Margin`:Pozycja pionowa względem marginesu.
- `100`:Odchylenie pionowe od marginesu (w punktach).
- `200`: Szerokość obrazu (w punktach).
- `100`:Wysokość obrazu (w punktach).
- `WrapType.Square`:Styl otaczania obrazu tekstem.

## Krok 5: Zapisz dokument

Na koniec zapisz dokument w wybranej lokalizacji.

1. Podaj ścieżkę do pliku wyjściowego:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Zapisz dokument:

```csharp
doc.Save(outputPath);
```

Twój dokument Word z pływającym obrazkiem jest już gotowy!

## Wniosek

Wstawianie pływającego obrazu do dokumentu Word za pomocą Aspose.Words dla .NET to prosty proces, gdy jest podzielony na łatwe do opanowania kroki. Postępując zgodnie z tym przewodnikiem, możesz dodawać profesjonalnie wyglądające obrazy do swoich dokumentów, zwiększając ich atrakcyjność wizualną. Aspose.Words zapewnia solidne API, które sprawia, że manipulacja dokumentami jest dziecinnie prosta, niezależnie od tego, czy pracujesz nad raportami, propozycjami czy jakimkolwiek innym typem dokumentu.

## Najczęściej zadawane pytania

### Czy mogę wstawiać wiele obrazów za pomocą Aspose.Words dla .NET?

Tak, możesz wstawić wiele obrazów, powtarzając `InsertImage` metodę dla każdego obrazu o pożądanych parametrach.

### Jak zmienić położenie obrazu?

Możesz dostosować `RelativeHorizontalPosition`, `RelativeVerticalPosition`i parametry przesunięcia, aby ustawić obraz w żądanym położeniu.

### Jakie inne typy owijania są dostępne dla obrazów?

Aspose.Words obsługuje różne typy zawijania, takie jak: `Inline`, `TopBottom`, `Tight`, `Through`więcej. Możesz wybrać ten, który najlepiej pasuje do układu Twojego dokumentu.

### Czy mogę używać różnych formatów obrazów?

Tak, Aspose.Words obsługuje szeroką gamę formatów obrazów, w tym JPEG, PNG, BMP i GIF.

### Jak mogę uzyskać bezpłatną wersję próbną Aspose.Words dla .NET?

Możesz otrzymać bezpłatną wersję próbną [Strona z bezpłatną wersją próbną](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}