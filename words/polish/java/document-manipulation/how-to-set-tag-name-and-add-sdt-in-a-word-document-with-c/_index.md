---
category: general
date: 2026-09-08
description: Ustaw nazwę tagu i utwórz kontrolkę zawartości (SDT) w dokumencie Word
  przy użyciu C#. Dowiedz się, jak dodać SDT, zapisać tekst w tagu i zmodyfikować
  dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: pl
lastmod: 2026-09-08
og_description: Ustaw nazwę tagu i utwórz kontrolkę zawartości (SDT) w dokumencie
  Word przy użyciu C#. Postępuj zgodnie z tym przewodnikiem krok po kroku, aby dodać
  SDT, wpisać tekst do tagu i zmodyfikować dokument.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Ustaw nazwę znacznika i dodaj SDT w dokumencie Word – przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak ustawić nazwę tagu i dodać SDT w dokumencie Word przy użyciu C#
url: /pl/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić nazwę tagu i dodać SDT w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **ustawić nazwę tagu** dla StructuredDocumentTag (SDT) podczas pracy z plikami Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz kompletny, gotowy do uruchomienia przykład, który **tworzy kontrolkę zawartości**, zapisuje tekst do tagu i **modyfikuje dokument Word** od początku do końca.

Programiści często pytają, *„jak dodać sdt* do istniejącego .docx i następnie *zapisać tekst do tagu*?” – odpowiedź leży w użyciu API Aspose.Words for .NET. Po zakończeniu tego samouczka będziesz w stanie otworzyć plik Word, wstawić plain‑text SDT, ustawić jego nazwę tagu, wypełnić go zawartością i zapisać zmiany bez pozostawiania niezwolnionych zasobów.

## Wymagania wstępne

* Zainstalowany .NET 6.0 lub nowszy.
* Ważna licencja Aspose.Words for .NET (lub możesz pracować z wersją ewaluacyjną).
* Visual Studio 2022 (lub dowolne IDE obsługujące C#).
* Dokument Word jako wejście (`input.docx`) umieszczony w folderze, do którego możesz odwołać się w kodzie.

## Krok 1: Konfiguracja projektu i importowanie przestrzeni nazw

Utwórz nowy projekt aplikacji konsolowej i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Następnie dodaj niezbędne dyrektywy `using` na początku pliku `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Te przestrzenie nazw dają dostęp do klas `Document`, `DocumentBuilder` oraz `StructuredDocumentTag`, które są niezbędne do **modyfikacji dokumentu Word**.

## Krok 2: Załaduj istniejący dokument Word

Pierwszą operacją jest załadowanie pliku, który chcesz edytować. Ten krok jest wymagany w każdym scenariuszu, w którym **modyfikujesz zawartość dokumentu Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Dlaczego najpierw ładujemy dokument** – Obiekt `Document` reprezentuje cały pakiet .docx w pamięci. Dopiero po załadowaniu możesz bezpiecznie wstawiać nowe węzły, takie jak SDT.

## Krok 3: Wstaw StructuredDocumentTag (SDT) i ustaw jego nazwę tagu

Teraz odpowiadamy na kluczowe pytanie: **jak dodać sdt** i **ustawić nazwę tagu**. Używamy `DocumentBuilder.InsertStructuredDocumentTag` z `SdtType.PlainText`. Drugi argument to nazwa tagu, którą możesz później odwołać programowo lub poprzez interfejs Worda.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Wyjaśnienie** – `InsertStructuredDocumentTag` zwraca instancję `StructuredDocumentTag`. Przekazując `"MyTag"` **ustawiamy nazwę tagu** bezpośrednio w momencie tworzenia. Jeśli będziesz musiał zmienić ją później, możesz przypisać nową wartość do `sdt.Tag`.

## Krok 4: Zapisz tekst do nowo utworzonego tagu

Po utworzeniu SDT zazwyczaj chcesz **zapisać tekst do tagu**, aby użytkownicy widzieli tekst zastępczy lub domyślną zawartość. Metoda `SetText` robi dokładnie to.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Dlaczego używać SetText** – Bezpośrednie przypisanie do właściwości `Text` zastąpiłoby całą hierarchię węzłów. `SetText` bezpiecznie aktualizuje wewnętrzny tekst kontrolki zawartości, zachowując jej strukturę.

## Krok 5: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany do nowego pliku. To kończy przepływ pracy **modyfikacji dokumentu Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Kiedy otworzysz `output.docx` w Microsoft Word, zobaczysz kontrolkę plain‑text oznaczoną **MyTag**, zawierającą tekst „Sample content”. Kontrolka może być edytowana ręcznie, a nazwa tagu pozostaje dostępna w narzędziach deweloperskich Worda.

## Pełny kod źródłowy

Poniżej znajduje się kompletny, samodzielny program. Skopiuj go do `Program.cs` i uruchom; nie są wymagane dodatkowe fragmenty kodu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Oczekiwany wynik w konsoli

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Jak wygląda wynikowy plik Word

![Dokument Word pokazujący kontrolkę zawartości o nazwie MyTag z tekstem „Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Przykład ustawienia nazwy tagu w dokumencie Word"}

*Zrzut ekranu ilustruje SDT z **nazwą tagu** ustawioną na *MyTag* oraz widocznym wbudowanym tekstem.*

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak sobie z tym poradzić |
|----------|--------------------------|
| **Utwórz rich‑text SDT** | Użyj `SdtType.RichText` zamiast `PlainText`. |
| **Ustaw inną nazwę tagu po wstawieniu** | `sdt.Tag = "NewTag";` – możesz ponownie przypisać nazwę tagu w dowolnym momencie. |
| **Dodaj SDT wewnątrz konkretnego akapitu** | Przesuń kursor buildera (`builder.MoveToParagraph(index)`) przed wywołaniem `InsertStructuredDocumentTag`. |
| **Wiele SDT w tym samym dokumencie** | Powtórz kroki 3‑4 dla każdej kontrolki; każda może mieć unikalną nazwę tagu. |
| **Praca z dokumentami zabezpieczonymi** | Upewnij się, że dokument jest odbezpieczony (`doc.Unprotect()`) przed wstawieniem SDT. |

## Profesjonalne wskazówki dla solidnej automatyzacji Word

* **Licencja na wczesnym etapie** – Wywołaj `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` na początku `Main`, aby uniknąć znaków wodnych wersji ewaluacyjnej.
* **Zwalnianie obiektów** – Owiń `Document` w blok `using`, jeśli celujesz w .NET Framework, aby zapewnić zwolnienie uchwytów plików.
* **Walidacja istnienia tagu** – Podczas późniejszego odczytu dokumentu użyj `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`, aby znaleźć tagi po właściwości `Tag`.
* **Wydajność** – Dla dużych dokumentów ładuj tylko wymagane sekcje używając `LoadOptions` z `LoadFormat.Docx` i `LoadFormat.Auto`.  

## Zakończenie

Teraz wiesz, jak **ustawić nazwę tagu**, **utworzyć kontrolkę zawartości**, **zapisać tekst do tagu** i **modyfikować dokument Word** przy użyciu C#. Pełny przykład demonstruje standardowy wzorzec **jak dodać sdt** i bezpiecznie zachować zmiany.

Stąd

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dodaj zawartość przy użyciu Document Builder w Aspose.Words dla .NET](/words/english/net/add-content-using-document-builder/)
- [Dokument Word – Jak usunąć zawartość](/words/english/net/remove-content/)
- [Utwórz dokument Word przy użyciu Aspose.Words – Przewodnik krok po kroku](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}