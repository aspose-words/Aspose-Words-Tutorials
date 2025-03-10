---
title: Dodaj tekstowy znak wodny z określonymi opcjami
linktitle: Dodaj tekstowy znak wodny z określonymi opcjami
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak dodać tekstowy znak wodny z określonymi opcjami do dokumentów Word za pomocą Aspose.Words dla .NET. Łatwo dostosuj czcionkę, rozmiar, kolor i układ.
weight: 10
url: /pl/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj tekstowy znak wodny z określonymi opcjami

## Wstęp

Znaki wodne mogą być stylowym i funkcjonalnym dodatkiem do dokumentów Word, służąc do oznaczania dokumentów jako poufnych lub dodawania osobistego akcentu. W tym samouczku pokażemy, jak dodać tekstowy znak wodny do dokumentu Word przy użyciu Aspose.Words dla .NET. Zanurzymy się w konkretnych opcjach, które możesz skonfigurować, takich jak rodzina czcionek, rozmiar czcionki, kolor i układ. Na koniec będziesz w stanie dostosować znak wodny swojego dokumentu do swoich dokładnych potrzeb. Więc chwyć swój edytor kodu i zacznijmy!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz przygotowane następujące rzeczy:

1.  Biblioteka Aspose.Words dla .NET: Będziesz potrzebować zainstalowanej biblioteki Aspose.Words. Jeśli jeszcze tego nie zrobiłeś, możesz ją pobrać z[Link do pobrania Aspose.Words](https://releases.aspose.com/words/net/).
2. Podstawowe zrozumienie języka C#: Ten samouczek będzie używał języka C# jako języka programowania. Podstawowe zrozumienie składni języka C# będzie pomocne.
3. Środowisko programistyczne .NET: Upewnij się, że masz skonfigurowane środowisko programistyczne (np. Visual Studio), w którym możesz tworzyć i uruchamiać aplikacje .NET.

## Importuj przestrzenie nazw

Aby pracować z Aspose.Words, musisz uwzględnić niezbędne przestrzenie nazw w swoim projekcie. Oto, co musisz zaimportować:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Krok 1: Skonfiguruj swój dokument

 Najpierw musisz załadować dokument, z którym chcesz pracować. W tym samouczku użyjemy przykładowego dokumentu o nazwie`Document.docx`. Upewnij się, że ten dokument znajduje się w określonym katalogu.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 W tym kroku zdefiniujesz katalog, w którym znajduje się Twój dokument i załadujesz go do instancji`Document` klasa.

## Krok 2: Skonfiguruj opcje znaku wodnego

Następnie skonfiguruj opcje dla swojego znaku wodnego. Możesz dostosować różne aspekty, takie jak rodzina czcionek, rozmiar czcionki, kolor i układ. Skonfigurujmy te opcje.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Oto, co robi każda z opcji:
- `FontFamily`: Określa czcionkę tekstu znaku wodnego.
- `FontSize`: Ustawia rozmiar tekstu znaku wodnego.
- `Color`: Definiuje kolor tekstu znaku wodnego.
- `Layout`:Określa orientację znaku wodnego (poziomą lub ukośną).
- `IsSemitrasparent`: Ustawia, czy znak wodny jest półprzezroczysty.

## Krok 3: Dodaj tekst znaku wodnego

Teraz zastosuj znak wodny do dokumentu, używając wcześniej skonfigurowanych opcji. W tym kroku ustawisz tekst znaku wodnego na „Test” i zastosujesz zdefiniowane opcje.

```csharp
doc.Watermark.SetText("Test", options);
```

Ta linijka kodu dodaje do dokumentu znak wodny z tekstem „Test”, stosując określone opcje.

## Krok 4: Zapisz dokument

Na koniec zapisz dokument z zastosowanym nowym znakiem wodnym. Możesz zapisać go pod nową nazwą, aby uniknąć nadpisania oryginalnego dokumentu.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Ten fragment kodu zapisuje zmodyfikowany dokument w tym samym katalogu pod nową nazwą pliku.

## Wniosek

Dodawanie tekstowego znaku wodnego do dokumentów Word za pomocą Aspose.Words dla .NET to prosty proces, gdy podzielisz go na łatwe do opanowania kroki. Postępując zgodnie z tym samouczkiem, nauczyłeś się, jak skonfigurować różne opcje znaku wodnego, w tym czcionkę, rozmiar, kolor, układ i przezroczystość. Dzięki tym umiejętnościom możesz teraz dostosować swoje dokumenty, aby lepiej spełniały Twoje potrzeby lub zawierały istotne informacje, takie jak poufność lub branding.

 Jeśli masz jakiekolwiek pytania lub potrzebujesz dalszej pomocy, możesz zapoznać się z[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/) lub odwiedź[Forum wsparcia Aspose](https://forum.aspose.com/c/words/8) Aby uzyskać więcej pomocy.

## Najczęściej zadawane pytania

### Czy mogę użyć różnych czcionek w znaku wodnym?

 Tak, możesz wybrać dowolną czcionkę zainstalowaną w systemie, określając`FontFamily` nieruchomość w`TextWatermarkOptions`.

### Jak zmienić kolor znaku wodnego?

 Możesz zmienić kolor znaku wodnego, ustawiając`Color` nieruchomość w`TextWatermarkOptions` do każdego`System.Drawing.Color` wartość.

### Czy można dodać do dokumentu wiele znaków wodnych?

Aspose.Words obsługuje dodawanie jednego znaku wodnego na raz. Aby dodać wiele znaków wodnych, musisz je utworzyć i zastosować sekwencyjnie.

### Czy mogę zmienić położenie znaku wodnego?

 Ten`WatermarkLayout`właściwość określa orientację, ale precyzyjne regulacje pozycjonowania nie są obsługiwane bezpośrednio. Może być konieczne użycie innych technik w celu dokładnego umiejscowienia.

### A co jeśli potrzebuję półprzezroczystego znaku wodnego?

 Ustaw`IsSemitrasparent`nieruchomość do`true` aby Twój znak wodny był półprzezroczysty.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
