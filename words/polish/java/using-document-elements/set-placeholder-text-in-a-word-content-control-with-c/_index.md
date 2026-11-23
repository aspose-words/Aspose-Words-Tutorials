---
category: general
date: 2026-11-22
description: Ustaw tekst zastępczy w kontrolce zawartości Word przy użyciu C#. Dowiedz
  się, jak utworzyć niestandardowy znacznik, wstawić kontrolkę tekstu zwykłego i dodać
  tekst zastępczy do znacznika za pomocą Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: pl
lastmod: 2026-11-22
og_description: Ustaw tekst zastępczy w kontrolce zawartości Word przy użyciu C#.
  Ten samouczek pokazuje, jak utworzyć niestandardowy znacznik, wstawić kontrolkę
  zwykłego tekstu i dodać tekst zastępczy do znacznika, aby zwiększyć interaktywność
  dokumentu.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Ustaw tekst zastępczy w kontrolce zawartości Word – przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Ustaw tekst zastępczy w kontrolce zawartości Word za pomocą C#
url: /pl/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw tekst zastępczy w kontrolce zawartości Word przy użyciu C#

Jeśli potrzebujesz **ustawić tekst zastępczy** w dokumencie Word programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Korzystając z Aspose.Words for .NET możesz utworzyć niestandardowy znacznik, wstawić kontrolkę tekstu zwykłego i dodać tekst zastępczy do znacznika, aby dokument był gotowy do wprowadzania danych przez użytkownika.

W tym samouczku dowiesz się, jak **utworzyć niestandardowy znacznik**, **wstawić kontrolkę zawartości** oraz **dodać tekst zastępczy do znacznika**, zachowując kod zwięzły i gotowy do produkcji. Nie są wymagane żadne zewnętrzne narzędzia — wystarczy projekt .NET i biblioteka Aspose.Words.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy zainstalowany  
* Ważna licencja Aspose.Words for .NET (lub darmowy klucz ewaluacyjny)  
* Podstawowa znajomość C# i Visual Studio (lub dowolnego wybranego IDE)

Poniższe sekcje zakładają, że utworzyłeś projekt konsolowy o nazwie `WordPlaceholderDemo`.

## Krok 1: Zainstaluj Aspose.Words

Dodaj pakiet NuGet do swojego projektu:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Użyj flagi `--version`, aby zablokować pakiet do najnowszej stabilnej wersji (np. `Aspose.Words.NET 24.9`).

## Krok 2: Załaduj dokument źródłowy i utwórz `DocumentBuilder`

Pierwszą rzeczą, którą robisz, jest załadowanie istniejącego pliku `.docx` (lub utworzenie nowego pustego dokumentu) oraz zainicjowanie `DocumentBuilder`. Builder zapewnia płynne API do wstawiania kontrolek i tekstu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten kod **przygotowuje** wstawienie kontrolki zawartości. `DocumentBuilder` działa bezpośrednio na obiekcie `doc`, więc wszelkie wprowadzone zmiany są automatycznie odzwierciedlane.

## Krok 3: Utwórz niestandardowy znacznik (StructuredDocumentTag)

W Wordzie *niestandardowy znacznik* nazywany jest **StructuredDocumentTag (SDT)**. Można go traktować jako kontrolkę zawartości, która posiada unikalny identyfikator. Utworzenie go jest sednem kroku **create custom tag**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

Metoda `InsertStructuredDocumentTag` przyjmuje dwa argumenty:

1. Typ kontrolki (`PlainText` w tym przypadku).  
2. Ciąg znaków, który jednoznacznie identyfikuje znacznik (`"MyTag"`).  

Używając **custom tag**, możesz później programowo zlokalizować lub manipulować kontrolką.

## Krok 4: Ustaw tytuł dla dostępności

Tytuł poprawia dostępność i ułatwia znalezienie kontrolki w interfejsie Worda.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

Właściwość `Title` jest opcjonalna, ale jej dodanie jest dobrą praktyką, gdy **add placeholder to tag**, aby zapewnić lepsze doświadczenie użytkownika.

## Krok 5: Dodaj tekst zastępczy do znacznika

Teraz nadchodzi główny cel: **set placeholder text**. Ten tekst pojawia się, gdy kontrolka jest pusta, wskazując użytkownikowi, co wpisać.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

Właściwość `PlaceholderText` jest dokładnie tym, czego potrzebujesz, aby **add placeholder to tag**. Działa jak szara wskazówka, którą widzisz w nowoczesnych polach formularzy.

## Krok 6: Zapisz zmodyfikowany dokument

Po skonfigurowaniu kontrolki zapisz dokument z powrotem na dysk.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Gdy otworzysz `output.docx` w Microsoft Word, zobaczysz kontrolkę tekstu zwykłego oznaczoną „CustomerName” z tekstem zastępczym „Enter name…”. Kliknięcie wewnątrz kontrolki usuwa tekst zastępczy, umożliwiając użytkownikowi wpisanie.

### Oczekiwany wynik

* Plik Word (`output.docx`) zawierający jedną kontrolkę tekstu zwykłego.  
* Kontrolka wyświetla tekst zastępczy „Enter name…”, dopóki użytkownik nie wpisze czegokolwiek.  
* Identyfikator znacznika kontrolki to `MyTag`, który możesz później odpytać przy użyciu `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Krok 7: Jak wstawić kontrolkę zawartości w innym miejscu (zaawansowane)

Jeśli potrzebujesz **how to insert content control** w określonym miejscu — na przykład po konkretnym akapicie — użyj metody `MoveTo` przed wstawieniem znacznika:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Ten fragment kodu demonstruje **insert plain text control** wielokrotnie w tym samym dokumencie.

## Typowe pułapki i jak ich uniknąć

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Placeholder nie jest widoczny | Kontrolka już zawiera tekst (nawet spację) | Upewnij się, że `sdt.Text` jest pusty przed ustawieniem `PlaceholderText`. |
| Kolizja identyfikatora znacznika | Ponowne użycie tej samej nazwy znacznika (`MyTag`) w tym samym dokumencie | Używaj unikalnych identyfikatorów dla każdego `StructuredDocumentTag`. |
| Wyjątek licencyjny | Uruchamianie bez ważnej licencji Aspose.Words | Zastosuj plik licencji (`license.SetLicense("Aspose.Words.lic")`) na początku `Main`. |
| Dokument nie został zapisany | Zapomnienie o wywołaniu `doc.Save` lub użycie ścieżki tylko do odczytu | Sprawdź, czy ścieżka wyjściowa jest zapisywalna i wywołaj `doc.Save`. |

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do `Program.cs`. Zawiera wszystkie kroki — **create custom tag**, **how to insert content control**, **add placeholder to tag** oraz **insert plain text control** — w jednej spójnej sekwencji.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Uruchom program poleceniem `dotnet run`. Po wykonaniu otwórz `output.docx`, aby zweryfikować, że obie kontrolki wyświetlają swoje odpowiednie teksty zastępcze.

## Kolejne kroki

* **Dostosuj wygląd** – użyj `sdt.Font`, aby zmienić rozmiar czcionki, kolor lub styl wewnątrz kontrolki.  
* **Powiąż z danymi XML** – zbadaj `sdt.XmlMapping`, jeśli potrzebujesz, aby kontrolka mapowała

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}