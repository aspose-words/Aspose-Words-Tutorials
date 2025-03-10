---
title: Uzyskaj zamiennik bez sufiksów
linktitle: Uzyskaj zamiennik bez sufiksów
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak zarządzać podmianą czcionek bez sufiksów w Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby mieć pewność, że Twoje dokumenty będą wyglądać idealnie za każdym razem.
weight: 10
url: /pl/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uzyskaj zamiennik bez sufiksów

## Wstęp

Witamy w tym kompleksowym przewodniku dotyczącym zarządzania podmianą czcionek za pomocą Aspose.Words dla .NET. Jeśli kiedykolwiek miałeś problemy z czcionkami, które nie wyświetlały się poprawnie w Twoich dokumentach, trafiłeś we właściwe miejsce. Ten samouczek przeprowadzi Cię przez proces krok po kroku, aby sprawnie obsługiwać podmianę czcionek bez sufiksów.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że posiadasz następujące rzeczy:

- Podstawowa wiedza o języku C#: Zrozumienie programowania w języku C# ułatwi śledzenie i wdrażanie kolejnych kroków.
-  Biblioteka Aspose.Words dla .NET: Pobierz i zainstaluj bibliotekę ze strony[link do pobrania](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Skonfiguruj środowisko programistyczne, takie jak Visual Studio, aby pisać i uruchamiać kod.
-  Przykładowy dokument: Przykładowy dokument (np.`Rendering.docx`) do wykorzystania w trakcie tego samouczka.

## Importuj przestrzenie nazw

Najpierw musimy zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do klas i metod udostępnianych przez Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Krok 1: Zdefiniuj katalog dokumentów

Na początek określ katalog, w którym znajduje się Twój dokument. Pomaga to w zlokalizowaniu dokumentu, nad którym chcesz pracować.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Skonfiguruj obsługę ostrzeżeń o podstawieniu

Następnie musimy skonfigurować obsługę ostrzeżeń, która powiadomi nas, gdy podczas przetwarzania dokumentu nastąpi zamiana czcionek. Jest to kluczowe dla wychwytywania i obsługi wszelkich problemów z czcionkami.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Krok 3: Dodaj niestandardowe źródła czcionek

W tym kroku dodamy niestandardowe źródła czcionek, aby mieć pewność, że Aspose.Words może zlokalizować i użyć prawidłowych czcionek. Jest to szczególnie przydatne, jeśli masz określone czcionki zapisane w niestandardowych katalogach.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

W tym kodzie:
-  Pobieramy aktualne źródła czcionek i dodajemy nowe`FolderFontSource` wskazując na nasz katalog niestandardowych czcionek (`C:\\MyFonts\\`).
- Następnie aktualizujemy źródła czcionek o tę nową listę.

## Krok 4: Zapisz dokument

Na koniec zapisz dokument po zastosowaniu ustawień zamiany czcionek. W tym samouczku zapiszemy go jako plik PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Krok 5: Utwórz klasę obsługi ostrzeżeń

 Aby skutecznie obsługiwać ostrzeżenia, utwórz niestandardową klasę, która implementuje`IWarningCallback` interfejs. Ta klasa będzie przechwytywać i rejestrować wszelkie ostrzeżenia dotyczące zamiany czcionek.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

W tej klasie:
-  Ten`Warning`Metoda wychwytuje ostrzeżenia związane z podmianą czcionek.
-  Ten`FontWarnings` kolekcja przechowuje te ostrzeżenia w celu dalszej kontroli lub rejestrowania.

## Wniosek

Opanowałeś już proces obsługi podmiany czcionek bez sufiksów za pomocą Aspose.Words dla .NET. Ta wiedza zapewni, że Twoje dokumenty zachowają zamierzony wygląd, niezależnie od czcionek dostępnych w systemie. Eksperymentuj z różnymi ustawieniami i źródłami, aby w pełni wykorzystać moc Aspose.Words.

## Najczęściej zadawane pytania

### Jak mogę używać czcionek z wielu niestandardowych katalogów?

 Możesz dodać wiele`FolderFontSource` przypadki do`fontSources` wypisz i zaktualizuj odpowiednio źródła czcionek.

### Gdzie mogę pobrać bezpłatną wersję próbną Aspose.Words dla platformy .NET?

 Darmową wersję próbną możesz pobrać ze strony[Strona z bezpłatną wersją próbną](https://releases.aspose.com/).

###  Czy mogę obsługiwać wiele typów ostrzeżeń za pomocą`IWarningCallback`?

 Tak,`IWarningCallback` Interfejs umożliwia obsługę różnych typów ostrzeżeń, nie tylko dotyczących zamiany czcionek.

### Gdzie mogę uzyskać pomoc dotyczącą Aspose.Words?

 Aby uzyskać pomoc, odwiedź stronę[Forum wsparcia Aspose.Words](https://forum.aspose.com/c/words/8).

### Czy można kupić licencję tymczasową?

 Tak, możesz uzyskać tymczasową licencję od[tymczasowa strona licencji](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
