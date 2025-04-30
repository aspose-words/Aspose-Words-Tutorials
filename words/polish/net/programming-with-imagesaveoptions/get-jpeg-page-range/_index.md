---
"description": "Konwertuj określone strony dokumentów Word do formatu JPEG z niestandardowymi ustawieniami za pomocą Aspose.Words dla .NET. Dowiedz się, jak krok po kroku dostosować jasność, kontrast i rozdzielczość."
"linktitle": "Pobierz zakres stron Jpeg"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Pobierz zakres stron Jpeg"
"url": "/pl/net/programming-with-imagesaveoptions/get-jpeg-page-range/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Pobierz zakres stron Jpeg

## Wstęp

Konwersja dokumentów Word na obrazy może być niezwykle użyteczna, niezależnie od tego, czy tworzysz miniatury, przeglądasz dokumenty online, czy udostępniasz treści w bardziej dostępnym formacie. Dzięki Aspose.Words dla .NET możesz łatwo konwertować określone strony dokumentów Word na format JPEG, dostosowując różne ustawienia, takie jak jasność, kontrast i rozdzielczość. Przyjrzyjmy się krok po kroku, jak to osiągnąć!

## Wymagania wstępne

Zanim zaczniemy, będziesz potrzebować kilku rzeczy:

- Aspose.Words dla .NET: Upewnij się, że masz zainstalowany Aspose.Words dla .NET. Możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: środowisko programistyczne AC#, takie jak Visual Studio.
- Przykładowy dokument: Dokument Word do pracy. Możesz użyć dowolnego pliku .docx w tym samouczku.
- Podstawowa wiedza z zakresu języka C#: Znajomość programowania w języku C#.

Kiedy już to wszystko przygotujemy, możemy zaczynać!

## Importuj przestrzenie nazw

Aby użyć Aspose.Words dla .NET, musisz zaimportować niezbędne przestrzenie nazw na początku kodu. Dzięki temu masz dostęp do wszystkich klas i metod wymaganych do manipulacji dokumentami.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Załaduj swój dokument

Najpierw musimy załadować dokument Word, który chcemy przekonwertować. Załóżmy, że nasz dokument nazywa się `Rendering.docx` i znajduje się w katalogu określonym przez symbol zastępczy `YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Ten kod inicjuje ścieżkę do dokumentu i ładuje go do Aspose.Words `Document` obiekt.

## Krok 2: Skonfiguruj ImageSaveOptions

Następnie skonfigurujemy `ImageSaveOptions` aby określić, jak chcemy, aby nasz JPEG był generowany. Obejmuje to ustawienie zakresu stron, jasności obrazu, kontrastu i rozdzielczości.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Konwertuj tylko pierwszą stronę
options.ImageBrightness = 0.3f;   // Ustaw jasność
options.ImageContrast = 0.7f;     // Ustaw kontrast
options.HorizontalResolution = 72f; // Ustaw rozdzielczość
```

## Krok 3: Zapisz dokument jako JPEG

Na koniec zapisujemy dokument jako plik JPEG, używając zdefiniowanych przez nas ustawień.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

Ten kod zapisuje pierwszą stronę `Rendering.docx` jako obraz JPEG z określonymi ustawieniami jasności, kontrastu i rozdzielczości.

## Wniosek

I masz! Udało Ci się przekonwertować określoną stronę dokumentu Word na obraz JPEG z niestandardowymi ustawieniami przy użyciu Aspose.Words dla .NET. Ten proces można dostosować do różnych potrzeb, niezależnie od tego, czy przygotowujesz obrazy do witryny, tworzysz podglądy dokumentów, czy też nie.

## Najczęściej zadawane pytania

### Czy mogę konwertować wiele stron jednocześnie?
Tak, możesz określić zakres stron za pomocą `PageSet` nieruchomość w `ImageSaveOptions`.

### Jak dostosować jakość obrazu?
Jakość pliku JPEG można dostosować za pomocą `JpegQuality` nieruchomość w `ImageSaveOptions`.

### Czy mogę zapisać obraz w innych formatach?
Tak, Aspose.Words obsługuje różne formaty obrazów, takie jak PNG, BMP i TIFF. Zmień `SaveFormat` W `ImageSaveOptions` odpowiednio.

### Czy istnieje sposób na podgląd obrazu przed zapisaniem?
Konieczne będzie osobne zaimplementowanie mechanizmu podglądu, ponieważ Aspose.Words nie zapewnia wbudowanej funkcji podglądu.

### Jak uzyskać tymczasową licencję na Aspose.Words?
Możesz poprosić o [tymczasowa licencja tutaj](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}