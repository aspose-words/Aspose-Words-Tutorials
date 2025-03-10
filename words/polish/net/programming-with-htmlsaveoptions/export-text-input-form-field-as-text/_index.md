---
title: Eksportuj pole formularza wprowadzania tekstu jako tekst
linktitle: Eksportuj pole formularza wprowadzania tekstu jako tekst
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak eksportować pola formularza wprowadzania tekstu jako zwykły tekst za pomocą Aspose.Words dla platformy .NET dzięki temu kompleksowemu przewodnikowi krok po kroku.
weight: 10
url: /pl/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Eksportuj pole formularza wprowadzania tekstu jako tekst

## Wstęp

Więc zanurzasz się w świat Aspose.Words dla .NET? Świetny wybór! Jeśli chcesz dowiedzieć się, jak eksportować pole formularza wprowadzania tekstu jako tekst, jesteś we właściwym miejscu. Niezależnie od tego, czy dopiero zaczynasz, czy szlifujesz swoje umiejętności, ten przewodnik przeprowadzi Cię przez wszystko, co musisz wiedzieć. Zaczynajmy, dobrze?

## Wymagania wstępne

Zanim przejdziemy do szczegółów, upewnijmy się, że masz wszystko, czego potrzebujesz, aby wszystko poszło gładko:

-  Aspose.Words dla .NET: Pobierz i zainstaluj najnowszą wersję z[Tutaj](https://releases.aspose.com/words/net/).
- IDE: Visual Studio lub dowolne środowisko programistyczne C#.
- Podstawowa wiedza o języku C#: Zrozumienie podstawowej składni języka C# i koncepcji programowania obiektowego.
- Dokument: Przykładowy dokument programu Word (`Rendering.docx`) z polami formularza do wprowadzania tekstu.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw. Są one jak klocki, które sprawiają, że wszystko działa bezproblemowo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

No dobrze, teraz gdy mamy już przygotowane przestrzenie nazw, możemy przystąpić do działania!

## Krok 1: Konfiguracja projektu

Zanim przejdziemy do kodu, upewnijmy się, że nasz projekt jest poprawnie skonfigurowany.

## Tworzenie projektu

1. Otwórz program Visual Studio: Zacznij od otwarcia programu Visual Studio lub preferowanego środowiska programistycznego C#.
2.  Utwórz nowy projekt: Przejdź do`File > New > Project` . Wybierać`Console App (.NET Core)` lub jakikolwiek inny odpowiedni typ projektu.
3.  Nazwij swój projekt: Nadaj swojemu projektowi znaczącą nazwę, np.`AsposeWordsExportExample`.

## Dodawanie Aspose.Words

1.  Zarządzanie pakietami NuGet: Kliknij prawym przyciskiem myszy swój projekt w Eksploratorze rozwiązań i wybierz`Manage NuGet Packages`.
2.  Wyszukaj Aspose.Words: W Menedżerze pakietów NuGet wyszukaj`Aspose.Words`.
3.  Zainstaluj Aspose.Words: Kliknij`Install` aby dodać bibliotekę Aspose.Words do swojego projektu.

## Krok 2: Załaduj dokument Word

Teraz, gdy nasz projekt jest już skonfigurowany, załadujmy dokument Word zawierający pola formularza wprowadzania tekstu.

1. Określ katalog dokumentu: Zdefiniuj ścieżkę do katalogu, w którym przechowywany jest Twój dokument.
2.  Załaduj dokument: Użyj`Document` klasa, aby załadować dokument Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Przygotuj katalog eksportowy

Zanim wyeksportujemy, upewnijmy się, że nasz katalog eksportu jest gotowy. To tutaj zostanie zapisany nasz plik HTML i obrazy.

1. Zdefiniuj katalog eksportu: Określ ścieżkę, w której zostaną zapisane wyeksportowane pliki.
2. Sprawdź i wyczyść katalog: Upewnij się, że katalog istnieje i jest pusty.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Krok 4: Skonfiguruj opcje zapisywania

Tutaj dzieje się magia. Musimy skonfigurować nasze opcje zapisu, aby wyeksportować pole formularza wprowadzania tekstu jako zwykły tekst.

1.  Utwórz opcje zapisu: Zainicjuj nowy`HtmlSaveOptions` obiekt.
2.  Ustaw opcję eksportu tekstu: Skonfiguruj`ExportTextInputFormFieldAsText`nieruchomość do`true`.
3. Ustaw folder obrazów: Zdefiniuj folder, w którym będą zapisywane obrazy.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Krok 5: Zapisz dokument jako HTML

Na koniec zapiszmy dokument Word jako plik HTML, korzystając z skonfigurowanych opcji zapisu.

1. Zdefiniuj ścieżkę wyjściową: Określ ścieżkę, w której zostanie zapisany plik HTML.
2.  Zapisz dokument: Użyj`Save` metoda`Document`klasa służąca do eksportowania dokumentu.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Wniosek

I masz! Udało Ci się wyeksportować pole formularza wprowadzania tekstu jako zwykły tekst za pomocą Aspose.Words dla .NET. Ten przewodnik powinien dać Ci jasne, krok po kroku podejście do wykonania tego zadania. Pamiętaj, praktyka czyni mistrza, więc eksperymentuj z różnymi opcjami i ustawieniami, aby zobaczyć, co jeszcze możesz zrobić za pomocą Aspose.Words.

## Najczęściej zadawane pytania

### Czy mogę eksportować inne typy pól formularzy, korzystając z tej samej metody?

 Tak, możesz eksportować inne typy pól formularza, konfigurując różne właściwości`HtmlSaveOptions` klasa.

### A co jeśli mój dokument zawiera obrazy?

 Obrazy zostaną zapisane w określonym folderze obrazów. Upewnij się, że ustawiłeś`ImagesFolder` nieruchomość w`HtmlSaveOptions`.

### Czy potrzebuję licencji na Aspose.Words?

 Tak, możesz otrzymać bezpłatną wersję próbną[Tutaj](https://releases.aspose.com/) lub kup licencję[Tutaj](https://purchase.aspose.com/buy).

### Czy mogę dostosować eksportowany kod HTML?

 Oczywiście! Aspose.Words udostępnia różne opcje dostosowywania wyjścia HTML. Zapoznaj się z[dokumentacja](https://reference.aspose.com/words/net/) Aby uzyskać więcej szczegółów.

### Czy Aspose.Words jest kompatybilny z .NET Core?

Tak, Aspose.Words jest kompatybilny z .NET Core, .NET Framework i innymi platformami .NET.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
