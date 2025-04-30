---
"description": "Dowiedz się, jak dodać prefiks nazwy klasy CSS podczas zapisywania dokumentów Word jako HTML przy użyciu Aspose.Words dla .NET. Zawiera przewodnik krok po kroku, fragmenty kodu i często zadawane pytania."
"linktitle": "Dodaj prefiks nazwy klasy CSS"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Dodaj prefiks nazwy klasy CSS"
"url": "/pl/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj prefiks nazwy klasy CSS

## Wstęp

Witamy! Jeśli zanurzasz się w świat Aspose.Words dla .NET, czeka Cię gratka. Dzisiaj pokażemy, jak dodać prefiks nazwy klasy CSS podczas zapisywania dokumentu Word jako HTML przy użyciu Aspose.Words dla .NET. Ta funkcja jest bardzo przydatna, gdy chcesz uniknąć konfliktów nazw klas w plikach HTML.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

- Aspose.Words dla .NET: Jeśli jeszcze tego nie zainstalowałeś, [pobierz tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Visual Studio lub inne środowisko IDE C#.
- Dokument Word: Będziemy używać dokumentu o nazwie `Rendering.docx`. Umieść go w katalogu swojego projektu.

## Importuj przestrzenie nazw

Najpierw upewnij się, że masz niezbędne przestrzenie nazw zaimportowane do swojego projektu C#. Dodaj je na górze pliku kodu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

A teraz przejdźmy do przewodnika krok po kroku!

## Krok 1: Skonfiguruj swój projekt

Zanim zaczniemy dodawać prefiks nazwy klasy CSS, skonfigurujmy nasz projekt.

### Krok 1.1: Utwórz nowy projekt

Uruchom program Visual Studio i utwórz nowy projekt aplikacji konsoli. Nazwij go w chwytliwy sposób, np. `AsposeCssPrefixExample`.

### Krok 1.2: Dodaj Aspose.Words dla .NET

Jeśli jeszcze tego nie zrobiłeś, dodaj Aspose.Words dla .NET do swojego projektu za pomocą NuGet. Po prostu otwórz konsolę NuGet Package Manager i uruchom:

```bash
Install-Package Aspose.Words
```

Świetnie! Teraz jesteśmy gotowi, aby zacząć kodowanie.

## Krok 2: Załaduj swój dokument

Pierwszą rzeczą, którą musimy zrobić, jest załadowanie dokumentu Word, który chcemy przekonwertować na format HTML.

### Krok 2.1: Zdefiniuj ścieżkę dokumentu

Ustaw ścieżkę do katalogu dokumentów. Na potrzeby tego samouczka załóżmy, że dokument znajduje się w folderze o nazwie `Documents` w katalogu Twojego projektu.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Krok 2.2: Załaduj dokument

Teraz załadujmy dokument za pomocą Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Skonfiguruj opcje zapisywania HTML

Następnie musimy skonfigurować opcje zapisu HTML, aby uwzględnić prefiks nazwy klasy CSS.

### Krok 3.1: Utwórz opcje zapisu HTML

Utwórz instancję `HtmlSaveOptions` obiekt i ustaw typ arkusza stylów CSS na `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Krok 3.2: Ustaw prefiks nazwy klasy CSS

Teraz ustawmy `CssClassNamePrefix` do żądanego prefiksu. W tym przykładzie użyjemy `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Krok 4: Zapisz dokument jako HTML

Na koniec zapiszmy dokument jako plik HTML ze skonfigurowanymi opcjami.


Określ ścieżkę do pliku wyjściowego HTML i zapisz dokument.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Krok 5: Sprawdź wynik

Po uruchomieniu projektu przejdź do `Documents` folder. Powinieneś znaleźć plik HTML o nazwie `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`. Otwórz ten plik w edytorze tekstu lub przeglądarce, aby sprawdzić, czy klasy CSS mają prefiks `pfx_`.

## Wniosek

I masz! Postępując zgodnie z tymi krokami, pomyślnie dodałeś prefiks nazwy klasy CSS do swojego wyjścia HTML przy użyciu Aspose.Words dla .NET. Ta prosta, ale potężna funkcja może pomóc Ci utrzymać czyste i bezkonfliktowe style w Twoich dokumentach HTML.

## Najczęściej zadawane pytania

### Czy mogę używać innego prefiksu dla każdej operacji zapisu?
Tak, możesz dostosować prefiks za każdym razem, gdy zapisujesz dokument, zmieniając `CssClassNamePrefix` nieruchomość.

### Czy ta metoda obsługuje inline CSS?
Ten `CssClassNamePrefix` Właściwość działa z zewnętrznym CSS. W przypadku inline CSS będziesz potrzebować innego podejścia.

### Jak mogę dodać inne opcje zapisu HTML?
Możesz skonfigurować różne właściwości `HtmlSaveOptions` aby dostosować wyjście HTML. Sprawdź [dokumentacja](https://reference.aspose.com/words/net/) po więcej szczegółów.

### Czy można zapisać kod HTML do strumienia?
Oczywiście! Możesz zapisać dokument do strumienia, przekazując obiekt strumienia do `Save` metoda.

### Gdzie mogę uzyskać pomoc, jeśli wystąpią problemy?
Możesz uzyskać wsparcie od [Forum Aspose](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}