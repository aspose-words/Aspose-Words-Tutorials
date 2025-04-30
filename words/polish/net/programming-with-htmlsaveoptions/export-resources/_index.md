---
"description": "Dowiedz się, jak eksportować zasoby, takie jak CSS i czcionki, zapisując dokumenty Word jako HTML przy użyciu Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku."
"linktitle": "Zasoby eksportowe"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Zasoby eksportowe"
"url": "/pl/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zasoby eksportowe

## Wstęp

Cześć, kolego entuzjasto technologii! Jeśli kiedykolwiek musiałeś przekonwertować dokumenty Worda na HTML, jesteś we właściwym miejscu. Dzisiaj zanurzamy się w cudowny świat Aspose.Words dla .NET. Ta potężna biblioteka sprawia, że praca z dokumentami Worda programowo staje się dziecinnie prosta. W tym samouczku przeprowadzimy Cię przez kroki eksportowania zasobów, takich jak czcionki i CSS, podczas zapisywania dokumentu Worda jako HTML przy użyciu Aspose.Words dla .NET. Zapnij pasy i ruszaj na przyjemną, pouczającą przejażdżkę!

## Wymagania wstępne

Zanim zagłębimy się w kod, upewnijmy się, że masz wszystko, czego potrzebujesz, aby zacząć. Oto krótka lista kontrolna:

1. Visual Studio: Upewnij się, że masz zainstalowane na swoim komputerze Visual Studio. Możesz je pobrać ze strony [Witryna internetowa Visual Studio](https://visualstudio.microsoft.com/).
2. Aspose.Words dla .NET: Będziesz potrzebować biblioteki Aspose.Words dla .NET. Jeśli jeszcze jej nie masz, pobierz bezpłatną wersję próbną z [Wydania Aspose](https://releases.aspose.com/words/net/) lub kup go od [Sklep Aspose](https://purchase.aspose.com/buy).
3. Podstawowa znajomość języka C#: Podstawowa znajomość języka C# pomoże Ci zrozumieć przykłady kodu.

Zrozumiałeś wszystko? Świetnie! Przejdźmy do importowania niezbędnych przestrzeni nazw.

## Importuj przestrzenie nazw

Aby użyć Aspose.Words dla .NET, musisz uwzględnić odpowiednie przestrzenie nazw w swoim projekcie. Oto, jak to zrobić:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Te przestrzenie nazw są niezbędne do uzyskania dostępu do klas i metod Aspose.Words, których będziemy używać w naszym samouczku.

Omówmy proces eksportowania zasobów podczas zapisywania dokumentu Word jako HTML. Zrobimy to krok po kroku, więc łatwo będzie to zrozumieć.

## Krok 1: Skonfiguruj katalog dokumentów

Po pierwsze, musisz określić ścieżkę do katalogu dokumentów. To jest miejsce, w którym znajduje się dokument Word i gdzie zostanie zapisany plik HTML.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do Twojego katalogu.

## Krok 2: Załaduj dokument Word

Następnie załadujmy dokument Word, który chcesz przekonwertować na HTML. W tym samouczku użyjemy dokumentu o nazwie `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ta linia kodu ładuje dokument ze wskazanego katalogu.

## Krok 3: Skonfiguruj opcje zapisywania HTML

Aby eksportować zasoby, takie jak CSS i czcionki, należy skonfigurować `HtmlSaveOptions`Ten krok jest kluczowy dla zapewnienia, że Twój wynik HTML jest dobrze ustrukturyzowany i zawiera niezbędne zasoby.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/zasoby"
};
```

Przyjrzyjmy się bliżej, co robi każda z opcji:
- `CssStyleSheetType = CssStyleSheetType.External`: Ta opcja określa, że style CSS powinny być zapisywane w zewnętrznym arkuszu stylów.
- `ExportFontResources = true`:Umożliwia eksportowanie zasobów czcionek.
- `ResourceFolder = dataDir + "Resources"`:Określa folder lokalny, w którym będą zapisywane zasoby (takie jak czcionki i pliki CSS).
- `ResourceFolderAlias = "http://example.com/resources"`: Ustawia alias dla folderu zasobów, który będzie używany w pliku HTML.

## Krok 4: Zapisz dokument jako HTML

Po skonfigurowaniu opcji zapisywania ostatnim krokiem jest zapisanie dokumentu jako pliku HTML. Oto jak to zrobić:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Ta linijka kodu zapisuje dokument w formacie HTML wraz z wyeksportowanymi zasobami.

## Wniosek

I masz to! Udało Ci się wyeksportować zasoby, zapisując dokument Worda jako HTML przy użyciu Aspose.Words dla .NET. Dzięki tej potężnej bibliotece programowe przetwarzanie dokumentów Worda staje się dziecinnie proste. Niezależnie od tego, czy pracujesz nad aplikacją internetową, czy po prostu musisz przekonwertować dokumenty do użytku offline, Aspose.Words Ci pomoże.

## Najczęściej zadawane pytania

### Czy mogę eksportować obrazy wraz z czcionkami i CSS?
Tak, możesz! Aspose.Words dla .NET obsługuje również eksportowanie obrazów. Upewnij się tylko, że skonfigurujesz `HtmlSaveOptions` odpowiednio.

### Czy istnieje sposób na osadzenie CSS zamiast stosowania zewnętrznego arkusza stylów?
Oczywiście. Możesz ustawić `CssStyleSheetType` Do `CssStyleSheetType.Embedded` jeśli wolisz osadzone style.

### Jak mogę dostosować nazwę pliku wyjściowego HTML?
Możesz określić dowolną nazwę pliku w `doc.Save` metoda. Na przykład, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Czy Aspose.Words obsługuje inne formaty poza HTML?
Tak, obsługuje różne formaty, w tym PDF, DOCX, TXT i inne. Sprawdź [dokumentacja](https://reference.aspose.com/words/net/) Aby zobaczyć pełną listę.

### Gdzie mogę uzyskać więcej wsparcia i zasobów?
Aby uzyskać więcej pomocy, odwiedź stronę [Forum wsparcia Aspose.Words](https://forum.aspose.com/c/words/8). Szczegółową dokumentację i przykłady można znaleźć również na [Strona internetowa Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}