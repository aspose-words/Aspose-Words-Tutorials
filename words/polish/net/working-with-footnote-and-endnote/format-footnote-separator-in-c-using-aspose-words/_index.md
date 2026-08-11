---
category: general
date: 2026-08-10
description: Formatuj separator przypisu w C# przy użyciu Aspose.Words, aby dostosować
  linie przypisów i przypisów końcowych. Naucz się formatowania przypisów w C# w kilka
  minut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: pl
lastmod: 2026-08-10
og_description: Formatuj separator przypisu w C# przy użyciu Aspose.Words. Skorzystaj
  z tego samouczka, aby szybko i niezawodnie stylizować separatory przypisów i przypisów
  końcowych.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Format separatora przypisu w C# – kompletny przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formatuj separator przypisu w C# przy użyciu Aspose.Words
url: /pl/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatuj separator przypisu w C# przy użyciu Aspose.Words

Jeśli potrzebujesz **sformatować separator przypisu** w dokumencie Word, ten przewodnik pokaże Ci, jak to zrobić przy użyciu Aspose.Words dla .NET. Zobaczysz kompletny, gotowy do uruchomienia przykład, który zmienia wyrównanie i kolor akapitu separatora, oraz nauczysz się, jak zastosować tę samą technikę do separatorów przypisów końcowych.

Samouczek obejmuje każdy krok — od wczytania pliku źródłowego po zapis zmodyfikowanego dokumentu — dzięki czemu możesz skopiować‑wkleić kod do własnego projektu bez dodatkowych poszukiwań.

## Czego będziesz potrzebować

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
* Ważna licencja Aspose.Words dla .NET (bezpłatna wersja próbna działa w celach oceny)
* Plik Word zawierający przynajmniej jeden przypis lub przypis końcowy (np. `Footnotes.docx`)
* Visual Studio 2022 lub dowolne IDE C#, które preferujesz

Posiadanie tych elementów pozwala skupić się na logice **formatowania przypisów w C#** zamiast na konfiguracji środowiska.

## Krok 1: Wczytaj dokument zawierający przypisy i przypisy końcowe

Pierwszą operacją jest utworzenie obiektu `Document`, który wskazuje na Twój plik źródłowy. Aspose.Words odczytuje cały pakiet DOCX do pamięci, dając pełny dostęp do węzłów przypisów i przypisów końcowych.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Dlaczego to ważne*: Wczytanie dokumentu jest warunkiem wstępnym dla każdej manipulacji. Jeśli ścieżka do pliku jest nieprawidłowa, Aspose.Words zgłasza `FileNotFoundException`, więc zweryfikuj ścieżkę przed kontynuacją.

## Krok 2: Pobierz węzły separatora i separatora kontynuacji

Separatory przypisów i przypisów końcowych są przechowywane jako specjalne węzły w kolekcjach `Footnotes` i `Endnotes`. Każda kolekcja udostępnia właściwości `Separator` i `ContinuationSeparator`, które zwracają referencję do obiektu `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Dlaczego to ważne*: Węzeł `Separator` reprezentuje linię, która wizualnie oddziela główny tekst od bloku przypisu. Uzyskując referencję, możesz zmodyfikować format akapitu, czcionkę lub nawet całkowicie zastąpić węzeł.

## Krok 3: Zmień wizualny styl separatora przypisu

W większości dokumentów Word separator jest pojedynczym akapitem zawierającym myślnik lub gwiazdkę. Poniższy kod sprawdza, czy separator jest typu `Paragraph` i, jeśli tak, centruje go oraz zmienia kolor tekstu na szary.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Stylowanie separatora kontynuacji (opcjonalnie)

Separator kontynuacji pojawia się, gdy przypis rozciąga się na wiele stron. Możesz go stylizować w podobny sposób:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Dlaczego to ważne*: Wyrównanie separatora poprawia czytelność, a zmiana koloru odróżnia go od zwykłego tekstu akapitu. Możesz zamienić `ParagraphAlignment.Center` na `Left` lub `Right`, aby dopasować się do wytycznych projektowych dokumentu.

## Krok 4: Zapisz zmodyfikowany dokument

Po zastosowaniu pożądanego stylu zapisz dokument z powrotem na dysk. Możesz nadpisać oryginalny plik lub utworzyć nową wersję.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Gdy otworzysz `Footnotes_Styled.docx` w programie Microsoft Word, separator przypisu będzie wyśrodkowany i szary, dokładnie tak jak określono w kodzie.

## Zaawansowane warianty

### Formatowanie separatora przypisu końcowego

Jeśli Twój dokument używa również przypisów końcowych, możesz zastosować tę samą logikę do kolekcji `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Użycie własnego ciągu znaków jako separatora

Czasami chcesz, aby separator był serią gwiazdek (`***`). Zastąp istniejące fragmenty nowym fragmentem:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Obsługa dokumentów bez węzła separatora

Rzadki przypadek brzegowy to dokument, który pomija węzeł separatora (np. gdy autor go usunął). W takiej sytuacji `document.Footnotes.Separator` zwraca `null`. Zabezpiecz się przed tym:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Typowe pułapki i jak ich unikać

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Separator is not a `Paragraph`** | Niektóre szablony Word używają `Table` lub `Shape` jako separatora. | Sprawdź typ węzła przy pomocy `is Paragraph` przed rzutowaniem. |
| **`Runs` collection is empty** | Separator może być pustym akapitem. | Zweryfikuj, czy `Runs.Count > 0` przed dostępem do `Runs[0]`. |
| **License not applied** | Bez licencji Aspose.Words wstawia znak wodny i może ograniczać użycie API. | Wywołaj `License license = new License(); license.SetLicense("Aspose.Words.lic");` na początku programu. |
| **Saving to a read‑only folder** | Metoda `Save` zgłasza `UnauthorizedAccessException`. | Upewnij się, że docelowy katalog ma uprawnienia do zapisu. |

Rozwiązanie tych problemów we wczesnym etapie zapobiega wyjątkom w czasie wykonywania i zapewnia płynne doświadczenie **modyfikacji separatora przypisu**.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się samodzielna aplikacja konsolowa, która demonstruje każdy krok omówiony powyżej. Skopiuj kod do nowego projektu .NET console, zamień ścieżki do plików i uruchom go.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Oczekiwany wynik**  

When you open `Footnotes_Styled.docx`:

* Linia separatora przypisu jest wyśrodkowana pod głównym tekstem.
* Jej kolor jest jasnoszary, co czyni go wizualnie odróżniającym.
* Jeśli dokument zawiera przypisy końcowe, ich separatory są również wyśrodkowane i szare (lub łamowe

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Przetwarzanie tekstu z przypisami i przypisami końcowymi](/words/english/net/working-with-footnote-and-endnote/)
- [Ustaw pozycję przypisu i przypisu końcowego](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Praca z przypisami i przypisami końcowymi](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}