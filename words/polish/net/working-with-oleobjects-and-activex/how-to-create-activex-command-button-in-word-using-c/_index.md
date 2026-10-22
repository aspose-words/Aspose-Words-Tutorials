---
category: general
date: 2026-09-21
description: Dowiedz się, jak utworzyć przycisk polecenia ActiveX w dokumencie Word
  przy użyciu Aspose.Words i C#. Przewodnik krok po kroku obejmuje wstawianie, pozycjonowanie
  i zapisywanie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: pl
lastmod: 2026-09-21
og_description: Utwórz przycisk polecenia ActiveX w dokumencie Word przy użyciu C#
  i Aspose.Words. Skorzystaj z tego pełnego samouczka, aby wstawić, ustawić pozycję
  i zapisać przycisk programowo.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Stwórz przycisk polecenia ActiveX w Wordzie w C# – pełny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Jak utworzyć przycisk polecenia ActiveX w programie Word przy użyciu C#
url: /pl/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć przycisk polecenia ActiveX w Wordzie przy użyciu C#

Jeśli potrzebujesz **utworzyć przycisk polecenia ActiveX** wewnątrz pliku Word, ten przewodnik pokaże Ci dokładne kroki. Korzystając z Aspose.Words for .NET możesz dodać, ustawić pozycję i skonfigurować przycisk w pełni z kodu C#.

Programowe wstawianie przycisku ActiveX eliminuje ręczną pracę z interfejsem UI i umożliwia automatyczne generowanie dokumentów dla formularzy, raportów lub interaktywnych szablonów. W tym samouczku nauczysz się, jak używać **DocumentBuilder**, metody **InsertForms2OleControl** oraz powiązanych właściwości, aby uzyskać w pełni funkcjonalny przycisk.

## Czego będziesz potrzebować

* .NET 6.0 SDK lub nowszy (kod działa również z .NET Framework 4.7+)
* Aspose.Words for .NET (pakiet NuGet `Aspose.Words`)
* IDE, np. Visual Studio 2022 lub VS Code
* Podstawowa znajomość C# oraz koncepcji dokumentów Word

Dodatkowa instalacja Office nie jest wymagana, ponieważ Aspose.Words działa niezależnie od Microsoft Word.

## Krok 1: Skonfiguruj projekt C#

Utwórz nowy projekt konsolowy i dodaj pakiet Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Biblioteka `Aspose.Words` udostępnia klasę **DocumentBuilder**, której użyjemy do manipulacji dokumentem.

## Krok 2: Zainicjalizuj dokument i builder

Pierwszy blok kodu tworzy pusty dokument oraz instancję `DocumentBuilder`. Ten obiekt jest punktem wejścia dla wszystkich operacji przetwarzania Worda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:** `DocumentBuilder` utrzymuje bieżącą pozycję kursora, więc każde kolejne wstawienie pojawi się dokładnie tam, gdzie umieścisz kursor.

## Krok 3: Wstaw przycisk polecenia ActiveX

Metoda **InsertForms2OleControl** tworzy kontrolkę ActiveX określonego typu. Tutaj żądamy `CommandButton` i określamy jej rozmiar w punktach (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Wyjaśnienie:**  
* `OleControlType.CommandButton` informuje Aspose.Words, aby utworzyć przycisk zamiast innego typu kontrolki.  
* Metoda zwraca obiekt `Forms2OleControl`, który udostępnia pola pozycjonowania i właściwości.

## Krok 4: Ustaw pozycję przycisku i skonfiguruj jego właściwości

Po wstawieniu możesz przenieść przycisk w dowolne miejsce na stronie oraz nadać mu programową nazwę i widoczny podpis.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Wskazówka:** System współrzędnych zaczyna się w lewym górnym rogu strony. Dostosuj `Left` i `Top`, aby wyrównać przycisk z innymi polami formularza.

## Krok 5: Zapisz dokument

Na koniec zapisz dokument na dysku. Plik będzie zawierał przycisk ActiveX, gotowy do otwarcia w Microsoft Word, gdzie przycisk stanie się interaktywny.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Gdy otworzysz `ActiveXCommandButton.docx` w Wordzie, zobaczysz przycisk oznaczony **Submit** w określonym miejscu. Kliknięcie go w Wordzie wywoła domyślne zachowanie przycisku polecenia (które możesz później dostosować za pomocą VBA lub dodatków Word).

## Pełny, uruchamialny przykład

Połączenie wszystkich elementów daje samodzielny program, który możesz skopiować, wkleić i uruchomić.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Oczekiwany wynik:** Konsola wyświetla *„Document created successfully.”* i folder zawiera teraz `ActiveXCommandButton.docx`. Otwarcie pliku w Microsoft Word pokazuje klikalny przycisk **Submit** umieszczony 100 pt od lewego marginesu i 150 pt od górnej krawędzi strony.

## Częste pułapki i jak ich unikać

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Przycisk pojawia się poza stroną | Wartości `Left`/`Top` przekraczają wymiary strony | Użyj `doc.FirstSection.PageSetup.PageWidth` i `PageHeight`, aby obliczyć bezpieczne współrzędne |
| Przycisk nie jest widoczny w Wordzie | Dokument został zapisany w formacie, który usuwa kontrolki ActiveX (np. `.txt`) | Zawsze zapisuj jako `.docx` lub `.doc` |
| Błąd wykonania `ArgumentOutOfRangeException` | Szerokość lub wysokość jest ustawiona na zero lub wartość ujemną | Upewnij się, że argumenty rozmiaru przekazywane do `InsertForms2OleControl` są liczbami dodatnimi |

## Rozszerzanie rozwiązania

Możesz dalej dostosować przycisk, ustawiając dodatkowe właściwości, takie jak `Enabled`, `Visible`, lub dołączając makro za pomocą VBA. Klasa **Forms2OleControl** pozwala także wstawiać inne kontrolki ActiveX, takie jak pola wyboru (`OleControlType.CheckBox`) czy pola kombi (`OleControlType.ComboBox`).

Jeśli potrzebujesz generować wiele przycisków w pętli, umieść logikę wstawiania w metodzie pomocniczej:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Zakończenie

Teraz wiesz, jak **utworzyć przycisk polecenia ActiveX** w dokumencie Word przy użyciu C# i Aspose.Words. Samouczek obejmował konfigurację projektu, wstawianie przycisku za pomocą `InsertForms2OleControl`, jego pozycjonowanie oraz zapisanie finalnego pliku. Dzięki tej podstawie możesz automatyzować złożone formularze, osadzać interaktywne kontrolki i integrować dokumenty Word z większymi rozwiązaniami .NET.

Następnie, zapoznaj się z powiązanymi tematami, takimi jak pola formularzy **Aspose.Words ActiveX**, zaawansowane stylizowanie **C# DocumentBuilder**, lub programowe dodawanie **kontrolki ActiveX w Wordzie** dla pól wyboru i list rozwijanych. Eksperymentuj z różnymi współrzędnymi i rozmiarami, aby dopasować je do swoich wymagań układu. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Utwórz prostokątny kształt w Wordzie przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Utwórz dokument Word z tabelą przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}