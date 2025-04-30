---
"description": "Dowiedz się, jak przekonwertować dokument Word na obraz indeksowany 1Bpp przy użyciu Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby uzyskać łatwą konwersję."
"linktitle": "Format 1Bpp Indeksowany"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Format 1Bpp Indeksowany"
"url": "/pl/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format 1Bpp Indeksowany

## Wstęp

Czy kiedykolwiek zastanawiałeś się, jak zapisać dokument Worda jako czarno-biały obraz za pomocą zaledwie kilku linijek kodu? Cóż, masz szczęście! Dzisiaj zagłębimy się w sprytny trik z wykorzystaniem Aspose.Words dla .NET, który pozwala konwertować dokumenty na obrazy indeksowane 1Bpp. Ten format jest idealny do niektórych typów archiwizacji cyfrowej, drukowania lub gdy trzeba zaoszczędzić miejsce. Podzielimy każdy krok, aby było to tak proste jak bułka z masłem. Gotowy, aby zacząć? Zanurzmy się!

## Wymagania wstępne

Zanim zabierzemy się do pracy, jest kilka rzeczy, które musisz mieć na miejscu:

- Aspose.Words dla .NET: Upewnij się, że biblioteka jest zainstalowana. Możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne .NET: Visual Studio jest dobrym wyborem, ale możesz używać dowolnego środowiska, w którym czujesz się komfortowo.
- Podstawowa znajomość języka C#: Nie martw się, postaramy się przedstawić to w prosty sposób, jednak odrobina znajomości języka C# okaże się pomocna.
- Dokument Word: Przygotuj przykładowy dokument Word, który chcesz przekonwertować.

## Importuj przestrzenie nazw

Po pierwsze, musimy zaimportować niezbędne przestrzenie nazw. Jest to kluczowe, ponieważ pozwala nam uzyskać dostęp do klas i metod, których potrzebujemy z Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Skonfiguruj katalog dokumentów

Musisz określić ścieżkę do katalogu dokumentu. To jest miejsce, w którym przechowywany jest dokument Word i gdzie zostanie zapisany przekonwertowany obraz.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Załaduj dokument Word

Teraz załadujmy dokument Word do Aspose.Words `Document` obiekt. Ten obiekt reprezentuje plik Word i pozwala na manipulowanie nim.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Skonfiguruj opcje zapisywania obrazu

Następnie musimy skonfigurować `ImageSaveOptions`. Tutaj dzieje się magia. Skonfigurujemy go tak, aby zapisywał obraz w formacie PNG z trybem kolorów indeksowanych 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Określa, że chcemy zapisać dokument jako obraz PNG.
- PageSet(1): Oznacza to, że konwertujemy tylko pierwszą stronę.
- ImageColorMode.BlackAndWhite: Ustawia obraz na czarno-biały.
- ImagePixelFormat.Format1bppIndexed: Ustawia format obrazu na indeksowany 1Bpp.

## Krok 4: Zapisz dokument jako obraz

Na koniec zapisujemy dokument jako obraz za pomocą `Save` metoda `Document` obiekt.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Wniosek

I masz! Za pomocą zaledwie kilku linijek kodu przekształciłeś swój dokument Word w obraz indeksowany 1Bpp za pomocą Aspose.Words dla .NET. Ta metoda jest niezwykle przydatna do tworzenia obrazów o wysokim kontraście i efektywnym wykorzystaniu miejsca z dokumentów. Teraz możesz łatwo zintegrować ją ze swoimi projektami i przepływami pracy. Miłego kodowania!

## Najczęściej zadawane pytania

### Czym jest obraz indeksowany 1Bpp?
Obraz indeksowany 1Bpp (1 bit na piksel) to czarno-biały format obrazu, w którym każdy piksel jest reprezentowany przez pojedynczy bit — 0 lub 1. Format ten jest bardzo oszczędny pod względem miejsca.

### Czy mogę przekonwertować wiele stron dokumentu Word jednocześnie?
Tak, możesz. Modyfikuj `PageSet` nieruchomość w `ImageSaveOptions` aby uwzględnić wiele stron lub cały dokument.

### Czy potrzebuję licencji, aby używać Aspose.Words dla .NET?
Tak, Aspose.Words dla .NET wymaga licencji dla pełnej funkcjonalności. Możesz uzyskać [tymczasowa licencja tutaj](https://purchase.aspose.com/temporary-license/).

### Do jakich innych formatów obrazów mogę przekonwertować mój dokument Word?
Aspose.Words obsługuje różne formaty obrazów, w tym JPEG, BMP i TIFF. Wystarczy zmienić `SaveFormat` w `ImageSaveOptions`.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?
Szczegółową dokumentację można znaleźć na stronie [Strona dokumentacji Aspose.Words dla .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}