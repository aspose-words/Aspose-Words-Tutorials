---
category: general
date: 2026-08-04
description: Utwórz pusty dokument Word i wstaw przycisk polecenia przy użyciu Aspose.Words.
  Dowiedz się, jak ustawić rozmiar przycisku i dodać przycisk klikalny w C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: pl
lastmod: 2026-08-04
og_description: Utwórz pusty dokument Word przy użyciu Aspose.Words i wstaw przycisk
  poleceń. Ten przewodnik pokazuje, jak ustawić rozmiar przycisku, dodać przycisk
  klikalny i zapisać plik.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Utwórz pusty dokument Word i dodaj przycisk polecenia – pełny tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Utwórz pusty dokument Word z przyciskiem polecenia – przewodnik krok po kroku
url: /pl/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word z przyciskiem polecenia – przewodnik krok po kroku

Jeśli potrzebujesz **utworzyć pusty dokument Word**, który zawiera interaktywny przycisk, ten samouczek pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words dla .NET. Nauczysz się **wstawiać przycisk polecenia**, dostosowywać jego wygląd i sprawić, by był klikalny — wszystko w kilku linijkach C#.

Poradnik obejmuje wszystko, od konfiguracji projektu po zapisanie finalnego pliku, dzięki czemu możesz skopiować‑wkleić pełne rozwiązanie do własnej aplikacji. Po drodze wyjaśnimy także, jak **dodać przycisk klikalny**, **ustawić rozmiar przycisku** i **utworzyć przycisk polecenia** programowo.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy zainstalowany.
* Visual Studio 2022 (lub dowolne IDE obsługujące .NET).
* Pakiet NuGet Aspose.Words dla .NET (`Aspose.Words` wersja 23.12 lub nowsza).
* Podstawowa znajomość C# i programowania obiektowego.

Nie są wymagane dodatkowe zestawy Office Interop, ponieważ Aspose.Words działa całkowicie niezależnie od Microsoft Word.

## Krok 1: Konfiguracja projektu .NET

Utwórz aplikację konsolową, która będzie hostować kod automatyzacji Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

To polecenie tworzy nowy folder `WordButtonDemo` z gotowym do uruchomienia plikiem `Program.cs` oraz dodaje bibliotekę Aspose.Words.

## Krok 2: Utworzenie pustego dokumentu Word

Pierwszą operacją jest **utworzyć pusty dokument Word**. Aspose.Words udostępnia klasę `Document`, która reprezentuje pusty plik Word od razu po utworzeniu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Utworzenie pustego dokumentu daje czyste płótno, na którym możesz dodawać akapity, tabele lub, w tym przypadku, przycisk polecenia OLE.

## Krok 3: Inicjalizacja DocumentBuilder

`DocumentBuilder` jest pomocnikiem, który pozwala wstawiać zawartość do dokumentu. Musisz go podłączyć do dokumentu, który właśnie utworzyłeś.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder utrzymuje bieżącą pozycję kursora, więc każde kolejne wstawienie odbywa się dokładnie tam, gdzie tego oczekujesz.

## Krok 4: Wstawienie przycisku polecenia

Teraz **wstawiamy przycisk polecenia** (obiekt OLE `Forms2OleControl`) do dokumentu. Metoda `InsertForms2OleControl` wymaga trzech argumentów:

1. ProgID kontrolki OLE – `"CommandButton"` dla standardowego przycisku.
2. `Rectangle`, który definiuje **ustawić rozmiar przycisku** oraz pozycję.
3. Podpis, który pojawia się na przycisku.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Gdy dokument zostanie otwarty w Wordzie, przycisk zachowuje się jak każda natywna kontrolka formularza — możesz go kliknąć, a Word uruchomi powiązane makro (jeśli istnieje). Spełnia to wymaganie **dodać przycisk klikalny**.

### Dlaczego używać Forms2OleControl?

`Forms2OleControl` osadza obiekt OLE bezpośrednio w pliku DOCX, zachowując właściwości kontrolki bez potrzeby używania zestawu Word Interop. To najpewniejszy sposób na **utworzyć przycisk polecenia**, który działa we wszystkich wersjach Worda.

## Krok 5: Dostosowanie przycisku (opcjonalnie)

Możesz chcieć **ustawić rozmiar przycisku** dokładniej lub zmienić dodatkowe właściwości, takie jak czcionka czy kolor tła. Aspose.Words udostępnia podlegający obiekt OLE, co pozwala na dalsze modyfikacje.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Jeśli potrzebujesz innego rozmiaru, po prostu dostosuj wartości `Rectangle` w Kroku 4. Współrzędne są mierzone w punktach (1 pt = 1/72 cala), więc `120` odpowiada mniej więcej 1,67 cali szerokości.

## Krok 6: Zapisanie dokumentu

Na koniec zapisz dokument na dysku. Powstały plik zawiera **pusty dokument Word** z w pełni funkcjonalnym przyciskiem polecenia.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Gdy otworzysz `CommandButtonDemo.docx` w Microsoft Word, zobaczysz przycisk oznaczony „Click Me”. Kliknięcie przycisku wyświetli domyślny dialog makra, chyba że dołączysz własne makro.

## Pełny kod źródłowy

Poniżej znajduje się pełny program, który możesz skopiować do `Program.cs`. Zawiera wszystkie opisane powyżej kroki i kompiluje się bez modyfikacji.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Oczekiwany wynik

Uruchomienie programu generuje `CommandButtonDemo.docx`. Otwarcie pliku w Wordzie pokazuje:

* Jedną stronę zawierającą przycisk oznaczony **Click Me**.
* Przycisk zachowuje **ustawić rozmiar przycisku** (120 × 30 punktów).
* Kliknięcie przycisku wywołuje domyślne zachowanie przycisku polecenia w Wordzie, potwierdzając, że operacja **dodać przycisk klikalny** zakończyła się sukcesem.

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|--------|
| **Czy to działa z plikami .doc?** | Tak. Zmień rozszerzenie pliku w `doc.Save("file.doc")`. Kontrolka OLE jest również przechowywana w starszym formacie binarnym. |
| **Co zrobić, jeśli potrzebuję wielu przycisków?** | Wywołaj `InsertForms2OleControl` wielokrotnie, dostosowując `Rectangle` dla każdego nowego przycisku, aby uniknąć nakładania się. |
| **Czy mogę dołączyć makro do przycisku?** | Sam przycisk nie zawiera kodu makra. Musisz dodać makro VBA do dokumentu ręcznie lub za pomocą kolekcji `Modules` obiektu `Document`. |
| **Czy przycisk jest widoczny przy eksporcie do PDF?** | Podczas eksportu DOCX do PDF przy użyciu Aspose.Words przycisk jest renderowany jako statyczny obraz, a nie interaktywna kontrolka. |
| **Jakie wersje Worda są obsługiwane?** | Przycisk OLE działa w Word 2007 i nowszych, ponieważ opiera się na standardowej specyfikacji Forms2.0. |

## Podsumowanie

Teraz wiesz, jak **utworzyć pusty dokument Word**, **wstawić przycisk polecenia**, **dodać przycisk klikalny** oraz **ustawić rozmiar przycisku** przy użyciu Aspose.Words dla .NET. Pełny przykład demonstruje przepływ pracy **utworzyć przycisk polecenia** od początku do końca, dając solidne podstawy do bardziej zaawansowanych zadań automatyzacji Word.

## Kolejne kroki

* Zbadaj inne kontrolki OLE (np. `CheckBox`, `ListBox`) zmieniając ProgID w `InsertForms2OleControl`.
* Połącz przycisk z makrem VBA, aby wykonywać niestandardowe akcje po kliknięciu przez użytkownika.
* Użyj `DocumentBuilder` z Aspose.Words, aby dodać dodatkową zawartość, taką jak tabele, obrazy lub przypisy, przed wstawieniem przycisku.
* Eksperymentuj z wartościami **ustawić rozmiar przycisku**, aby dopasować je do wymagań układu dokumentu.

Miłego kodowania i przyjemnego tworzenia bogatszych dokumentów Word z interaktywnymi kontrolkami!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Utwórz pusty dokument Word z kształtem prostokąta z cieniowaniem – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Utwórz dokument Word przy użyciu Aspose.Words dla .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}