---
"description": "Dowiedz się, jak zapisać każdą stronę dokumentu Word jako oddzielny obraz PNG za pomocą Aspose.Words dla .NET, korzystając z naszego szczegółowego przewodnika krok po kroku."
"linktitle": "Wywołanie zwrotne zapisywania strony"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Wywołanie zwrotne zapisywania strony"
"url": "/pl/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wywołanie zwrotne zapisywania strony

## Wstęp

Cześć! Czy kiedykolwiek czułeś potrzebę zapisania każdej strony dokumentu Word jako osobnych obrazów? Może chcesz rozbić duży raport na łatwe do przyswojenia wizualizacje lub może musisz utworzyć miniatury do podglądu. Bez względu na powód, użycie Aspose.Words dla .NET sprawia, że to zadanie staje się proste. W tym przewodniku przeprowadzimy Cię przez proces konfigurowania wywołania zwrotnego zapisywania strony, aby zapisać każdą stronę dokumentu jako pojedynczy obraz PNG. Zanurzmy się w tym!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, pobierz i zainstaluj ze strony [Tutaj](https://releases.aspose.com/words/net/).
2. Visual Studio: powinna działać każda wersja, jednak w tym przewodniku będę korzystać z Visual Studio 2019.
3. Podstawowa znajomość języka C#: Aby móc korzystać z kursu, konieczna jest podstawowa znajomość języka C#.

## Importuj przestrzenie nazw

Najpierw musimy zaimportować niezbędne przestrzenie nazw. Pomaga nam to uzyskać dostęp do wymaganych klas i metod bez konieczności wpisywania pełnej przestrzeni nazw za każdym razem.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Skonfiguruj katalog dokumentów

Dobrze, zacznijmy od zdefiniowania ścieżki do katalogu dokumentów. To tutaj znajduje się Twój dokument Word wejściowy i gdzie będą zapisywane obrazy wyjściowe.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Załaduj swój dokument

Następnie załadujemy dokument, który chcesz przetworzyć. Upewnij się, że Twój dokument („Rendering.docx”) znajduje się w określonym katalogu.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Skonfiguruj opcje zapisywania obrazu

Musimy skonfigurować opcje zapisywania obrazów. W tym przypadku zapisujemy strony jako pliki PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

Tutaj, `PageSet` określa zakres stron do zapisania i `PageSavingCallback` wskazuje na naszą niestandardową klasę wywołania zwrotnego.

## Krok 4: Wdróż funkcję zwrotną zapisywania strony

Teraz zaimplementujemy klasę wywołania zwrotnego, która obsługuje sposób zapisywania każdej strony.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

Ta klasa implementuje `IPageSavingCallback` interfejs i w jego obrębie `PageSaving` metodą definiujemy wzór nazewnictwa dla każdej zapisanej strony.

## Krok 5: Zapisz dokument jako obrazy

Na koniec zapisujemy dokument korzystając z skonfigurowanych opcji.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Wniosek

I masz to! Udało Ci się skonfigurować wywołanie zwrotne zapisywania strony, aby zapisać każdą stronę dokumentu Word jako osobny obraz PNG przy użyciu Aspose.Words dla .NET. Ta technika jest niezwykle przydatna w różnych aplikacjach, od tworzenia podglądów stron po generowanie pojedynczych obrazów stron do raportów. 

Miłego kodowania!

## Najczęściej zadawane pytania

### Czy mogę zapisywać strony w formatach innych niż PNG?  
Tak, możesz zapisywać strony w różnych formatach, takich jak JPEG, BMP i TIFF, zmieniając `SaveFormat` W `ImageSaveOptions`.

### Co zrobić, jeśli chcę zapisać tylko konkretne strony?  
Możesz określić strony, które chcesz zapisać, dostosowując `PageSet` parametr w `ImageSaveOptions`.

### Czy można dostosować jakość obrazu?  
Oczywiście! Możesz ustawić właściwości takie jak `ImageSaveOptions.JpegQuality` aby kontrolować jakość obrazów wyjściowych.

### Jak mogę wydajnie obsługiwać duże dokumenty?  
W przypadku obszernych dokumentów warto rozważyć przetwarzanie stron w partiach, aby efektywnie zarządzać wykorzystaniem pamięci.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Words dla .NET?  
Sprawdź [dokumentacja](https://reference.aspose.com/words/net/) aby uzyskać kompleksowe przewodniki i przykłady.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}