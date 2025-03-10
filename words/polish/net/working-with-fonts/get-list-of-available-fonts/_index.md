---
title: Pobierz listę dostępnych czcionek
linktitle: Pobierz listę dostępnych czcionek
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak uzyskać listę dostępnych czcionek za pomocą Aspose.Words dla .NET w tym szczegółowym samouczku krok po kroku. Zwiększ swoje umiejętności zarządzania czcionkami.
weight: 10
url: /pl/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pobierz listę dostępnych czcionek

## Wstęp

Czy kiedykolwiek miałeś problem z zarządzaniem czcionkami w dokumentach Word? Jeśli jesteś programistą .NET, Aspose.Words for .NET jest tutaj, aby Cię uratować! Ta potężna biblioteka nie tylko pomaga programowo tworzyć i manipulować dokumentami Word, ale także oferuje rozbudowane możliwości zarządzania czcionkami. W tym przewodniku przeprowadzimy Cię przez samouczek krok po kroku, jak uzyskać listę dostępnych czcionek za pomocą Aspose.Words for .NET. Podzielimy to na przyswajalne kroki, aby zapewnić Ci łatwość śledzenia. Więc zanurzmy się i sprawmy, aby zarządzanie czcionkami było dziecinnie proste!

## Wymagania wstępne

Zanim zaczniemy, będziesz potrzebować kilku rzeczy:

-  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/net/).
- Visual Studio: W tym przykładzie jako środowisko programistyczne wykorzystano Visual Studio.
- .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
- Katalog dokumentów: Ścieżka do katalogu, w którym przechowywane są Twoje dokumenty.

## Importuj przestrzenie nazw

Najpierw zaimportuj niezbędne przestrzenie nazw do swojego projektu:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Krok 1: Zainicjuj ustawienia czcionek

Pierwszym krokiem jest zainicjowanie ustawień czcionek. Pozwoli to na zarządzanie źródłami czcionek dla dokumentów.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Ta klasa służy do określania ustawień zastępowania czcionek i źródeł czcionek.
- fontSources: Tworzymy listę istniejących źródeł czcionek na podstawie bieżących ustawień czcionek.

## Krok 2: Zdefiniuj katalog dokumentów

Następnie określ ścieżkę do katalogu dokumentu. To tutaj Aspose.Words będzie szukać czcionek.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Ta zmienna typu string przechowuje ścieżkę do katalogu, w którym znajdują się Twoje czcionki. Zastąp`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką.

## Krok 3: Dodaj niestandardowy folder czcionek

Teraz dodaj nowy folder źródłowy, aby poinstruować Aspose.Words, aby przeszukał ten folder w poszukiwaniu czcionek.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Ta klasa reprezentuje źródło czcionki folderu. Drugi parametr (`true`) wskazuje, czy czcionki mają być wyszukiwane rekurencyjnie w podfolderach.

## Krok 4: Aktualizacja źródeł czcionek

Dodaj niestandardowy folder czcionek do listy istniejących źródeł czcionek i zaktualizuj ustawienia czcionek.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Dodaje niestandardowy folder czcionek do istniejących źródeł czcionek.
- updatedFontSources: Konwertuje listę źródeł czcionek na tablicę.

## Krok 5: Pobierz i wyświetl czcionki

Na koniec pobierz dostępne czcionki i wyświetl ich szczegóły.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Pobiera listę dostępnych czcionek z pierwszego źródła czcionek na zaktualizowanej liście.
-  fontInfo: Instancja`PhysicalFontInfo` zawierające szczegółowe informacje o każdej czcionce.

## Wniosek

Gratulacje! Udało Ci się pobrać listę dostępnych czcionek za pomocą Aspose.Words dla .NET. Ten samouczek przeprowadził Cię przez każdy krok, od inicjalizacji ustawień czcionek do wyświetlania szczegółów czcionek. Dzięki tej wiedzy możesz teraz z łatwością zarządzać czcionkami w dokumentach Word. Pamiętaj, Aspose.Words dla .NET to potężne narzędzie, które może znacznie zwiększyć możliwości przetwarzania dokumentów. Więc idź dalej i odkryj więcej funkcji, aby uczynić proces rozwoju jeszcze bardziej wydajnym.

## Najczęściej zadawane pytania

### Czy mogę używać Aspose.Words dla .NET z innymi frameworkami .NET?
Tak, Aspose.Words dla .NET jest kompatybilny z różnymi platformami .NET, w tym .NET Core i .NET 5+.

### Jak zainstalować Aspose.Words dla .NET?
Można go zainstalować za pomocą Menedżera pakietów NuGet w programie Visual Studio, wyszukując „Aspose.Words”.

### Czy można dodać wiele niestandardowych folderów czcionek?
 Tak, możesz dodać wiele niestandardowych folderów czcionek, tworząc wiele`FolderFontSource` wystąpień i dodawanie ich do listy źródeł czcionek.

### Czy mogę pobrać szczegóły dotyczące czcionki z określonego źródła czcionek?
 Tak, możesz pobrać szczegóły dotyczące czcionki z dowolnego źródła czcionek, określając indeks źródła czcionek w`updatedFontSources` szyk.

### Czy Aspose.Words dla .NET obsługuje podstawianie czcionek?
Tak, obsługuje podstawianie czcionek, co zapewnia prawidłowe wyświetlanie tekstu, nawet jeśli oryginalna czcionka nie jest dostępna.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
