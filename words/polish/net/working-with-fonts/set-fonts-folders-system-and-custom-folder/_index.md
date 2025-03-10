---
title: Ustaw foldery czcionek, system i niestandardowy folder
linktitle: Ustaw foldery czcionek, system i niestandardowy folder
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak ustawić foldery czcionek systemowych i niestandardowych w dokumentach programu Word za pomocą pakietu Aspose.Words for .NET, aby zapewnić prawidłowe wyświetlanie dokumentów w różnych środowiskach.
weight: 10
url: /pl/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw foldery czcionek, system i niestandardowy folder

## Wstęp

Wyobraź sobie, że tworzysz dokument z unikalnym stylem czcionki, tylko po to, aby dowiedzieć się, że czcionki nie wyświetlają się poprawnie na innym komputerze. Frustrujące, prawda? To właśnie tutaj wkracza konfiguracja folderów czcionek. Dzięki Aspose.Words dla .NET możesz zdefiniować systemowe i niestandardowe foldery czcionek, aby mieć pewność, że Twoje dokumenty zawsze będą wyglądać tak, jak powinny. Przyjrzyjmy się, jak możesz to osiągnąć.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

-  Biblioteka Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, pobierz ją[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: IDE, np. Visual Studio.
- Podstawowa znajomość języka C#: Znajomość języka C# pomoże Ci zrozumieć przykłady kodu.

## Importuj przestrzenie nazw

Najpierw zaimportuj niezbędne przestrzenie nazw do swojego projektu:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Teraz podzielimy ten proces na proste kroki.

## Krok 1: Załaduj dokument

 Aby rozpocząć, załaduj dokument Word do Aspose.Words`Document` obiekt. Ten dokument będzie tym, w którym chcesz ustawić foldery czcionek.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 2: Zainicjuj ustawienia czcionek

 Utwórz nową instancję`FontSettings`Ten obiekt umożliwi Ci zarządzanie źródłami czcionek.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Krok 3: Pobierz źródła czcionek systemowych

Pobierz domyślne źródła czcionek systemowych. Na komputerze z systemem Windows obejmuje to zazwyczaj „Windows\Fonts\"katalog.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Krok 4: Dodaj niestandardowy folder czcionek

Dodaj niestandardowy folder zawierający dodatkowe czcionki. Jest to przydatne, jeśli masz określone czcionki, które nie są zainstalowane w katalogu czcionek systemowych.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Krok 5: Aktualizacja źródeł czcionek

 Konwertuj listę źródeł czcionek z powrotem na tablicę i ustaw ją na`FontSettings` obiekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Krok 6: Zastosuj ustawienia czcionki do dokumentu

 Na koniec zastosuj skonfigurowane`FontSettings` do dokumentu i zapisz go w wybranym formacie, np. PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Wniosek

masz to! Wykonując te kroki, możesz upewnić się, że Twoje dokumenty Word używają właściwych czcionek, niezależnie od tego, czy są to czcionki systemowe, czy niestandardowe przechowywane w określonym katalogu. Ta konfiguracja pomaga zachować integralność wyglądu dokumentu w różnych środowiskach.

## Najczęściej zadawane pytania

### Co się stanie, jeśli czcionki brakuje w folderach systemowych i niestandardowych?

Aspose.Words zastąpi brakującą czcionkę domyślną czcionką, dzięki czemu dokument pozostanie czytelny.

### Czy mogę dodać wiele niestandardowych folderów czcionek?

 Tak, możesz dodać wiele niestandardowych folderów czcionek, powtarzając proces tworzenia`FolderFontSource` obiektów i dodawanie ich do listy źródeł czcionek.

### Czy można używać ścieżek sieciowych do przechowywania niestandardowych folderów czcionek?

 Tak, możesz określić ścieżkę sieciową w`FolderFontSource` konstruktor.

### Jakie formaty plików obsługuje Aspose.Words przy zapisywaniu dokumentów?

Aspose.Words obsługuje różne formaty, w tym DOCX, PDF, HTML i inne.

### Jak postępować w przypadku powiadomień o zamianie czcionek?

 Powiadomienia o zamianie czcionek można obsługiwać za pomocą`FontSettings` klasa`FontSubstitutionWarning`wydarzenie.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
