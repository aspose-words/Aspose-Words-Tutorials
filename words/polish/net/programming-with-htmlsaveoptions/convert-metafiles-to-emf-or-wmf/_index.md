---
"description": "Przewodnik krok po kroku dotyczący konwersji metaplików do formatów EMF lub WMF podczas konwersji dokumentu do formatu HTML za pomocą Aspose.Words dla .NET."
"linktitle": "Konwertuj metapliki do formatu EMF lub WMF"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Konwertuj metapliki do formatu EMF lub WMF"
"url": "/pl/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konwertuj metapliki do formatu EMF lub WMF

## Wstęp

Witamy w kolejnym głębokim zanurzeniu w świat Aspose.Words dla .NET. Dzisiaj zajmiemy się sprytnym trikiem: konwersją obrazów SVG do formatów EMF lub WMF w dokumentach Word. Może to brzmieć trochę technicznie, ale nie martw się. Pod koniec tego samouczka będziesz w tym profesjonalistą. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz pracę z Aspose.Words dla .NET, ten przewodnik przeprowadzi Cię przez wszystko, co musisz wiedzieć, krok po kroku.

## Wymagania wstępne

Zanim zagłębimy się w kod, upewnijmy się, że wszystko jest skonfigurowane. Oto, czego potrzebujesz:

1. Aspose.Words for .NET Library: Upewnij się, że masz najnowszą wersję. Jeśli jej nie masz, możesz ją pobrać z [Tutaj](https://releases.aspose.com/words/net/).
2. .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
3. Środowisko programistyczne: IDE, takie jak Visual Studio, ułatwi Ci życie.
4. Podstawowa znajomość języka C#: Nie musisz być ekspertem, ale podstawowa znajomość języka będzie pomocna.

Masz wszystko? Świetnie! Zaczynajmy.

## Importuj przestrzenie nazw

Po pierwsze, musimy zaimportować niezbędne przestrzenie nazw. Jest to kluczowe, ponieważ informuje nasz program, gdzie znaleźć klasy i metody, których będziemy używać.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Te przestrzenie nazw obejmują wszystko, od podstawowych funkcji systemowych po konkretną funkcjonalność Aspose.Words, która będzie nam potrzebna w tym samouczku.

## Krok 1: Skonfiguruj katalog dokumentów

Zacznijmy od zdefiniowania ścieżki do katalogu dokumentów. To tutaj zostanie zapisany dokument Word po konwersji metaplików.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą chcesz zapisać dokument.

## Krok 2: Utwórz ciąg HTML za pomocą SVG

Następnie potrzebujemy ciągu HTML zawierającego obraz SVG, który chcemy przekonwertować. Oto prosty przykład:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' szerokość='500' wysokość='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Ten fragment kodu HTML zawiera podstawowy kod SVG z napisem „Witaj, świecie!”.

## Krok 3: Załaduj HTML za pomocą opcji ConvertSvgToEmf

Teraz używamy `HtmlLoadOptions` aby określić, jak chcemy obsługiwać obrazy SVG w HTML. Ustawienie `ConvertSvgToEmf` Do `true` zapewnia konwersję obrazów SVG do formatu EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Ten fragment kodu tworzy nowy `Document` obiekt, ładując do niego ciąg HTML przy użyciu określonych opcji ładowania.

## Krok 4: Ustaw HtmlSaveOptions dla formatu metapliku

Aby zapisać dokument w odpowiednim formacie metapliku, używamy `HtmlSaveOptions`Tutaj ustawiamy `MetafileFormat` Do `HtmlMetafileFormat.Png`, ale możesz to zmienić na `Emf` Lub `Wmf` w zależności od Twoich potrzeb.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Krok 5: Zapisz dokument

Na koniec zapisujemy dokument korzystając z podanych opcji zapisu.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Dokument zostanie zapisany w określonym katalogu, a format metapliku zostanie przekonwertowany zgodnie z definicją.

## Wniosek

masz to! Postępując zgodnie z tymi krokami, pomyślnie przekonwertowałeś obrazy SVG do formatów EMF lub WMF w dokumentach Word za pomocą Aspose.Words dla .NET. Ta metoda jest przydatna do zapewnienia zgodności i zachowania integralności wizualnej dokumentów na różnych platformach. Miłego kodowania!

## Najczęściej zadawane pytania

### Czy mogę konwertować inne formaty obrazów za pomocą tej metody?
Tak, możesz konwertować różne formaty obrazów, odpowiednio dostosowując opcje ładowania i zapisywania.

### Czy konieczne jest użycie konkretnej wersji .NET Framework?
Aspose.Words for .NET obsługuje wiele wersji .NET Framework, ale zawsze warto używać najnowszej wersji w celu uzyskania najlepszej zgodności i funkcji.

### Jaka jest zaleta konwersji SVG do EMF lub WMF?
Konwersja formatu SVG do formatu EMF lub WMF zapewnia, że grafika wektorowa zostanie zachowana i prawidłowo renderowana w środowiskach, które mogą nie w pełni obsługiwać format SVG.

### Czy mogę zautomatyzować ten proces dla wielu dokumentów?
Oczywiście! Możesz przejść przez wiele plików HTML, stosując ten sam proces, aby zautomatyzować konwersję do przetwarzania wsadowego.

### Gdzie mogę znaleźć więcej materiałów i pomocy dla Aspose.Words dla .NET?
Można znaleźć kompleksową dokumentację [Tutaj](https://reference.aspose.com/words/net/) i uzyskaj wsparcie od społeczności Aspose [Tutaj](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}