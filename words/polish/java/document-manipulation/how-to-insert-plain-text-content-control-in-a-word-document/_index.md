---
category: general
date: 2026-10-26
description: Naucz się wstawiać kontrolkę treści zwykłego tekstu przy użyciu Aspose.Words
  w C#. Przewodnik krok po kroku obejmujący StructuredDocumentTag, tytuły i identyfikatory
  tagów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: pl
lastmod: 2026-10-26
og_description: Wstaw kontrolkę zawartości tekstu zwykłego przy użyciu Aspose.Words
  w C#. Postępuj zgodnie z tym przewodnikiem, aby dodać tytuły, identyfikatory tagów
  i dostosować wygląd.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Wstaw kontrolkę zawartości tekstu zwykłego w Wordzie przy użyciu C# – kompletny
  przewodnik
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak wstawić kontrolkę zawartości zwykłego tekstu w dokumencie Word przy użyciu
  C#
url: /pl/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw kontrolkę zawartości tekstu zwykłego w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **wstawić kontrolkę zawartości tekstu zwykłego** do pliku Word, ten samouczek pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words dla .NET. Niezależnie od tego, czy tworzysz usługę generowania dokumentów, czy automatyzujesz tworzenie formularzy, poniższe kroki pozwolą Ci dodać wielokrotnego użytku, edytowalny obszar, który użytkownicy końcowi mogą wypełniać.

Nauczysz się, jak utworzyć `Document`, użyć `DocumentBuilder` do umieszczenia plain‑text Structured Document Tag (SDT), ustawić przyjazny tytuł i przypisać unikalny identyfikator tagu. Poradnik wyjaśnia również typowe warianty — takie jak zmiana wyglądu lub zagnieżdżanie kontrolek — abyś mógł dostosować rozwiązanie do dowolnego projektu.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
- Ważna licencja Aspose.Words dla .NET (lub darmowy klucz ewaluacyjny)
- Visual Studio 2022 lub dowolne IDE kompatybilne z C#
- Podstawowa znajomość składni C#

> **Wskazówka:** Jeśli używasz darmowej wersji ewaluacyjnej, pamiętaj, że dokument wyjściowy będzie zawierał znak wodny. Wersja licencjonowana usuwa go automatycznie.

## Jak wstawić kontrolkę zawartości tekstu zwykłego przy użyciu Aspose.Words

Rdzeń rozwiązania to proces składający się z trzech kroków:

1. **Utwórz `Document` i `DocumentBuilder`.**  
2. **Wstaw plain‑text Structured Document Tag (SDT) z domyślnym wyglądem.**  
3. **Przypisz tytuł i identyfikator tagu do SDT.**  

Każdy krok jest wyjaśniony poniżej, wraz z kompletnym, gotowym do uruchomienia kodem.

### Krok 1: Zainicjalizuj dokument i builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` udostępnia metody takie jak `InsertParagraph`, `InsertImage` oraz, co kluczowe w tym samouczku, `InsertStructuredDocumentTag`. Ich wstępna inicjalizacja daje Ci płótno, na którym możesz umieścić **kontrolkę zawartości tekstu zwykłego**.

### Krok 2: Wstaw kontrolkę zawartości tekstu zwykłego (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` instruuje Aspose.Words, aby utworzyć **kontrolkę zawartości tekstu zwykłego**, która zachowuje się jak proste pole tekstowe, które użytkownicy mogą edytować. `SdtAppearance.Default` renderuje kontrolkę z delikatnym tłem, co wyraźnie wskazuje w dokumencie, że obszar jest edytowalny.

> **Dlaczego używać `SdtAppearance.Default`?**  
> Domyślny wygląd jest najbardziej uniwersalnie kompatybilnym stylem we wszystkich wersjach Worda. Jeśli potrzebujesz wyglądu bez obramowania, możesz później przełączyć na `SdtAppearance.Hidden`.

### Krok 3: Ustaw tytuł i identyfikator tagu

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) pojawia się w panelu *Content Controls* w Wordzie, pomagając użytkownikom końcowym zrozumieć przeznaczenie pola.  
- **Tag** (`sdt.Tag`) jest identyfikatorem skierowanym do deweloperów, który możesz później odpytać za pomocą `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** zapewnia szary podpowiedźowy tekst, poprawiając doświadczenie użytkownika.

Pełny fragment kodu powyżej tworzy samodzielny program, który możesz skompilować i uruchomić. Po wykonaniu, `output.docx` będzie zawierał jedną kontrolkę zawartości tekstu zwykłego z tytułem *MyTag* i tagiem *TagId*.

![Diagram pokazujący wstawianie kontrolki zawartości tekstu zwykłego w dokumencie Word](image.png){alt="wstaw kontrolkę zawartości tekstu zwykłego"}

## Zrozumienie StructuredDocumentTag (SDT) i jego właściwości

**Structured Document Tag** (SDT) jest podstawowym modelem obiektowym dla kontrolek zawartości w Wordzie. Najważniejsze właściwości przy wstawianiu kontrolki tekstu zwykłego to:

| Właściwość | Cel | Typowe wartości |
|------------|-----|-----------------|
| `SdtType` | Określa typ kontrolki (tekst zwykły, tekst sformatowany, obraz itp.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Styl wizualny kontrolki | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Nazwa czytelna dla człowieka wyświetlana w panelu *Content Controls* | Any short string |
| `Tag` | Identyfikator odczytywany maszynowo używany w kodzie | Alphanumeric string |
| `PlaceholderName` | Tekst wyświetlany, gdy kontrolka jest pusta | Custom hint text |

Gdy ustawisz `SdtType.PlainText`, Word ogranicza zawartość do zwykłych znaków, zapobiegając formatowaniu sformatowanemu. Dzięki temu kontrolka jest idealna dla prostych pól formularza, takich jak *Name*, *Email* lub *Phone Number*.

### Warianty, które mogą być potrzebne

| Scenariusz | Zmiana kodu |
|------------|-------------|
| **Brak cieniowania wizualnego** (bez obramowania) | Use `SdtAppearance.Hidden` instead of `Default`. |
| **Pole tylko do odczytu** | After insertion, set `sdt.LockContentControl = true`. |
| **Wstępne wypełnienie danymi** | Set `sdt.Text = "John Doe";` after creating the tag. |
| **Wiele kontrolek w tabeli** | Insert the SDT inside a table cell using `builder.InsertCell();` before the `InsertStructuredDocumentTag` call. |

## Częste pułapki i jak ich unikać

1. **Zapomnienie o ustawieniu tytułu** – Word nadal utworzy kontrolkę, ale użytkownicy nie zobaczą znaczącego opisu w panelu *Content Controls*. Zawsze przypisuj `sdt.Title`.  
2. **Użycie niewłaściwego `SdtType`** – Jeśli potrzebujesz tekstu zwykłego, a przypadkowo wybierzesz `RichText`, kontrolka pozwoli na formatowanie, co może zepsuć dalsze przetwarzanie. Sprawdź dwukrotnie wartość wyliczenia.  
3. **Zapisywanie do folderu tylko do odczytu** – Wywołanie `doc.Save` spowoduje rzucenie `UnauthorizedAccessException`. Upewnij się, że docelowy katalog jest zapisywalny lub użyj `Path.GetTempPath()` do testów.  
4. **Licencja nie zastosowana** – Bez ważnej licencji, dokument wyjściowy zawiera znak wodny wersji ewaluacyjnej. Zastosuj licencję wcześnie w programie:

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się cały program, gotowy do skopiowania i wklejenia do nowego projektu konsolowego.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Oczekiwany wynik:** Otwierając `output.docx` w Microsoft Word zobaczysz linię tekstu *“Please fill in the following field:”* followed by a light‑gray boxed region labeled *MyTag*. Placeholder *Enter your text here* pojawia się w jasnoszarym kolorze, dopóki użytkownik nie wpisze tekstu.

## Zakończenie

Teraz wiesz, jak **wstawić kontrolkę zawartości tekstu zwykłego** do dokumentu Word przy użyciu Aspose.Words dla .NET. Samouczek obejmował inicjalizację `Document`, wstawianie `StructuredDocumentTag` typu `PlainText` oraz dostosowywanie jego tytułu, tagu i placeholdera. Rozumiejąc opcje `SdtAppearance` oraz typowe pułapki, możesz pewnie tworzyć formularze, szablony i automatyczne raporty, które opierają się na edytowalnych kontrolkach zawartości.

### Co dalej?

- Zbadaj inne typy SDT, takie jak `RichText` lub `ComboBox` dla list rozwijanych.  
- Połącz wiele kontrolek zawartości w tabelach lub powtórz je przy użyciu `RepeatingSection`.  
- Użyj `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`, aby programowo odczytywać lub modyfikować wartości kontrolek.

Śmiało eksperymentuj z wcześniej pokazanymi wariantami i włącz ten wzorzec do większych potoków generowania dokumentów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć kontrolkę zawartości w C# przy użyciu Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Utwórz nowy dokument Word i wstaw kontrolkę zawartości w C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Dodaj zawartość przy użyciu Document Builder w Aspose.Words dla .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}