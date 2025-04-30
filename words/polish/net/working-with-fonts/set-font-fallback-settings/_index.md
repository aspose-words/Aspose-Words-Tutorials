---
"description": "Dowiedz się, jak skonfigurować ustawienia Font Fallback w Aspose.Words dla .NET. Ten kompleksowy przewodnik zapewnia, że wszystkie znaki w dokumentach są wyświetlane poprawnie."
"linktitle": "Ustaw ustawienia zapasowej czcionki"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Ustaw ustawienia zapasowej czcionki"
"url": "/pl/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw ustawienia zapasowej czcionki

## Wstęp

Podczas pracy z dokumentami zawierającymi różne elementy tekstowe, takie jak różne języki lub znaki specjalne, kluczowe jest zapewnienie, że te elementy są wyświetlane poprawnie. Aspose.Words for .NET oferuje potężną funkcję o nazwie Font Fallback Settings, która pomaga w definiowaniu reguł zastępowania czcionek, gdy oryginalna czcionka nie obsługuje niektórych znaków. W tym przewodniku pokażemy, jak skonfigurować Font Fallback Settings za pomocą Aspose.Words for .NET w samouczku krok po kroku.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że spełnione są następujące wymagania wstępne:

- Podstawowa znajomość języka C#: Znajomość języka programowania C# i platformy .NET.
- Aspose.Words dla .NET: Pobierz i zainstaluj z [link do pobrania](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: środowisko podobne do Visual Studio, służące do pisania i uruchamiania kodu.
- Przykładowy dokument: Posiadaj przykładowy dokument (np. `Rendering.docx`) gotowe do testów.
- Reguły zapasowe czcionek w formacie XML: Przygotuj plik XML definiujący reguły zapasowe czcionek.

## Importuj przestrzenie nazw

Aby użyć Aspose.Words, musisz zaimportować niezbędne przestrzenie nazw. Umożliwia to dostęp do różnych klas i metod wymaganych do przetwarzania dokumentów.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Krok 1: Zdefiniuj katalog dokumentów

Najpierw zdefiniuj katalog, w którym przechowywany jest Twój dokument. Jest to niezbędne do zlokalizowania i przetworzenia Twojego dokumentu.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Załaduj dokument

Załaduj swój dokument do Aspose.Words `Document` obiekt. Ten krok pozwala na programową pracę z dokumentem.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Skonfiguruj ustawienia czcionek

Utwórz nowy `FontSettings` obiekt i załaduj ustawienia zapasowe czcionki z pliku XML. Ten plik XML zawiera reguły zapasowe czcionki.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Krok 4: Zastosuj ustawienia czcionki do dokumentu

Przypisz skonfigurowane `FontSettings` do dokumentu. Zapewnia to, że reguły zapasowe czcionek zostaną zastosowane podczas renderowania dokumentu.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Zapisz dokument

Na koniec zapisz dokument. Ustawienia zapasowe czcionki zostaną użyte podczas operacji zapisywania, aby zapewnić właściwą zamianę czcionki.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Plik XML: Reguły zapasowe czcionek

Oto przykład, jak powinien wyglądać plik XML definiujący reguły zapasowe czcionek:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Wniosek

Postępując zgodnie z tymi krokami, możesz skutecznie skonfigurować i używać ustawień Font Fallback w Aspose.Words dla .NET. Dzięki temu Twoje dokumenty będą wyświetlać wszystkie znaki poprawnie, nawet jeśli oryginalna czcionka nie obsługuje niektórych znaków. Wdrożenie tych ustawień znacznie poprawi jakość i czytelność Twoich dokumentów.

## Najczęściej zadawane pytania

### P1: Czym jest funkcja Font Fallback?

Font Fallback to funkcja umożliwiająca zamianę czcionek w przypadku, gdy oryginalna czcionka nie obsługuje niektórych znaków, zapewniając tym samym prawidłowe wyświetlanie wszystkich elementów tekstowych.

### P2: Czy mogę określić wiele czcionek zapasowych?

Tak, możesz określić wiele czcionek zapasowych w regułach XML. Aspose.Words sprawdzi każdą czcionkę w podanej kolejności, aż znajdzie taką, która obsługuje dany znak.

### P3: Gdzie mogę pobrać Aspose.Words dla platformy .NET?

Można go pobrać ze strony [Strona pobierania Aspose](https://releases.aspose.com/words/net/).

### P4: Jak utworzyć plik XML zawierający reguły zapasowe czcionek?

Plik XML można utworzyć za pomocą dowolnego edytora tekstu. Powinien on mieć strukturę pokazaną w przykładzie podanym w tym samouczku.

### P5: Czy jest dostępne wsparcie dla Aspose.Words?

Tak, możesz znaleźć wsparcie na [Forum wsparcia Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}