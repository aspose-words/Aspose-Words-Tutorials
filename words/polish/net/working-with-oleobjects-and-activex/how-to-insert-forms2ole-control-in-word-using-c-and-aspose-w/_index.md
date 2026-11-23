---
category: general
date: 2026-11-22
description: Naucz się wstawiać kontrolkę Forms2Ole w Wordzie przy użyciu C#. Ten
  przewodnik krok po kroku obejmuje DocumentBuilder, umieszczanie przycisku polecenia
  oraz zapisywanie pliku .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: pl
lastmod: 2026-11-22
og_description: Wstaw kontrolkę Forms2Ole w Wordzie przy użyciu C#. Skorzystaj z tego
  przewodnika, aby dodać przycisk polecenia przy użyciu Aspose.Words i DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Wstaw kontrolkę Forms2Ole w Wordzie przy użyciu C# – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak wstawić kontrolkę Forms2Ole w Wordzie przy użyciu C# i Aspose.Words
url: /pl/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić kontrolkę Forms2Ole w Wordzie przy użyciu C# i Aspose.Words

Jeśli potrzebujesz **wstawić kontrolkę Forms2Ole w Wordzie**, ten tutorial pokazuje dokładnie, jak to zrobić w C#. Niezależnie od tego, czy tworzysz szablon do wypełniania, czy automatyzujesz tworzenie formularzy, poniższe rozwiązanie pozwala programowo dodać przycisk polecenia.

Nauczysz się, jak utworzyć pusty dokument, użyć `DocumentBuilder` do umieszczenia kontrolki i zapisać wynik jako `.docx`. Poradnik obejmuje także typowe pułapki, takie jak systemy współrzędnych i kompatybilność ze starszymi wersjami Worda.

## Wymagania wstępne

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
* Aspose.Words for .NET (pakiet NuGet `Aspose.Words`)
* Podstawowa znajomość C# i modelu obiektowego Worda
* IDE, takie jak Visual Studio lub VS Code

## Krok 1: Konfiguracja projektu i importowanie przestrzeni nazw

Utwórz nową aplikację konsolową i dodaj pakiet Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

W `Program.cs` zaimportuj wymagane przestrzenie nazw:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Porada:** Użyj najnowszej wersji Aspose.Words, aby uzyskać pełne wsparcie dla API `Forms2OleControl`.

## Krok 2: Utworzenie pustego dokumentu i zainicjowanie DocumentBuilder

Klasa `Document` reprezentuje plik Word, natomiast `DocumentBuilder` udostępnia metody do wstawiania treści.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` działa jak kursor; po tej linii możesz zacząć umieszczać elementy w dowolnym miejscu dokumentu.

## Krok 3: Definiowanie pozycji i rozmiaru przycisku

Word mierzy współrzędne w punktach (1 pt ≈ 1/72 cala). Struktura `Rectangle` z `System.Drawing` opisuje granice kontrolki.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` umieszcza kontrolkę w lewym górnym rogu bieżącej strony.
* Dostosuj `x` i `y`, aby przenieść przycisk w inne miejsce (np. `new Rectangle(150, 200, 100, 30)`).

## Krok 4: Wstawienie przycisku polecenia Forms2Ole

Teraz użyj `InsertForms2OleControl`, aby dodać kontrolkę. Metoda wymaga typu kontrolki, nazwy oraz granic określonych powyżej.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Zwrócony obiekt `Forms2OleControl` pozwala modyfikować właściwości takie jak `Enabled`, `Visible`, a nawet później przypisać nazwę makra.

### Dlaczego używać Forms2Ole?

* **Kompatybilność wsteczna** – Kontrolki Forms2Ole działają w Word 97‑2003 (`.doc`) oraz nowszych plikach `.docx`.
* **Obsługa makr** – Mogą wywoływać makra VBA, co czyni je idealnymi dla interaktywnych szablonów.
* **Precyzyjne położenie** – W przeciwieństwie do kontrolek treści, masz kontrolę nad dokładnymi współrzędnymi.

## Krok 5: Zapisanie dokumentu

Na koniec zapisz plik na dysku. Wybierz folder, do którego masz prawo zapisu.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Otwórz `output.docx` w Microsoft Word. Zobaczysz przycisk oznaczony **ClickMe** w lewym górnym rogu pierwszej strony. Kliknięcie go w Wordzie nie zrobi nic, dopóki nie przypiszesz makra, ale kontrolka jest w pełni funkcjonalna.

## Obsługa typowych przypadków brzegowych

| Situation | How to address it |
|-----------|-------------------|
| **Przycisk pojawia się poza stroną** | Sprawdź, czy współrzędne `Rectangle` mieszczą się w marginesach strony. Użyj `builder.PageSetup.PageWidth` i `PageHeight`, aby obliczyć bezpieczne granice. |
| **Kontrolka niewidoczna w starszych wersjach Worda** | Zapisz dokument jako `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) aby zapewnić kompatybilność Forms2Ole z Word 97‑2003. |
| **Potrzeba zmiany podpisu** | Po wstawieniu ustaw `commandButton.Caption = "Submit";`. |
| **Przypisanie makra** | Ustaw `commandButton.MacroName = "MyMacro"`; makro musi istnieć w projekcie VBA dokumentu. |
| **Wiele przycisków** | Powtórz Krok 4 z różnymi wartościami `Rectangle` i unikalnymi nazwami. |

## Pełny, uruchamialny przykład

Łącząc wszystko razem, oto samodzielny program, który możesz skopiować, wkleić i uruchomić:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Oczekiwany wynik:** Po uruchomieniu programu `output.docx` otwiera się w Wordzie z przyciskiem oznaczonym *Click Me!* umieszczonym w lewym górnym rogu pierwszej strony.

## Zakończenie

Teraz wiesz, jak **wstawić kontrolkę Forms2Ole w Wordzie** przy użyciu C# i Aspose.Words. Proces polega na utworzeniu `Document`, ustawieniu `Rectangle` i wywołaniu `InsertForms2OleControl` za pomocą `DocumentBuilder`. Dzięki pełnemu przykładowi kodu i wskazówkom dotyczącym przypadków brzegowych możesz integrować przyciski poleceń w dowolnym zautomatyzowanym przepływie pracy Word.

### Kolejne kroki

* Zbadaj inne wartości `ControlType`, takie jak `CheckBox` lub `OptionButton`.
* Połącz kontrolki Forms2Ole z makrami VBA, aby tworzyć interaktywne formularze.
* Użyj `DocumentBuilder.MoveTo`, aby umieszczać przyciski w konkretnych akapitach lub tabelach.
* Przejrzyj dokumentację Aspose.Words **Forms2Ole** w celu zaawansowanych ustawień właściwości.

Miłego kodowania i ciesz się tworzeniem bogatszych dokumentów Word przy użyciu C# i Aspose.Words!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak wstawić przycisk polecenia OLE w dokumencie Word przy użyciu C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [jak dodać kontrolkę ActiveX w Wordzie przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Dodaj przycisk polecenia do dokumentu Word przy użyciu Aspose.Words – kompletny przewodnik](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}