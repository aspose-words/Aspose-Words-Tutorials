---
category: general
date: 2026-09-05
description: Utwórz dokument Word przy użyciu Aspose.Words C# i dowiedz się, jak wstawić
  przycisk polecenia ActiveX, ustawić rozmiar przycisku oraz dodać interaktywną funkcjonalność
  przycisku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: pl
lastmod: 2026-09-05
og_description: Utwórz dokument Word w C# i wstaw przycisk polecenia ActiveX. Ten
  samouczek pokazuje, jak ustawić rozmiar przycisku i dodać interaktywne funkcje przycisku.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Utwórz dokument Word z przyciskiem polecenia ActiveX w C# – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Jak utworzyć dokument Word z przyciskiem polecenia ActiveX w C#
url: /pl/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word z przyciskiem polecenia ActiveX w C#

Jeśli potrzebujesz **utworzyć dokument Word** programowo i osadzić klikalny element interfejsu użytkownika, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Korzystając z Aspose.Words for .NET możesz **utworzyć dokument Word**, **dodać przycisk polecenia** i kontrolować jego wygląd — wszystko bez otwierania Microsoft Word.

Nauczysz się **jak wstawiać kontrolki ActiveX**, **ustawiać rozmiar przycisku** oraz sprawić, by przycisk zachowywał się jak interaktywny element UI. Nie wymagana jest wcześniejsza znajomość COM ani VBA; wystarczy środowisko programistyczne .NET oraz biblioteka Aspose.Words.

## Co osiągniesz

* **Utwórz dokument Word** od podstaw w C#.
* **Wstaw przycisk polecenia ActiveX** (klasyczna kontrolka „Click Me”).
* **Ustaw rozmiar przycisku** i pozycję precyzyjnie.
* Opcjonalnie dodaj prostą logikę **interaktywnego przycisku** (np. placeholder makra).
* Zapisz plik jako `.docx`, który można otworzyć w Microsoft Word lub dowolnym kompatybilnym przeglądarce.

### Wymagania wstępne

| Wymaganie | Powód |
|-----------|-------|
| .NET 6.0 lub nowszy | Zapewnia środowisko uruchomieniowe dla kodu C#. |
| Aspose.Words for .NET (najnowsza wersja) | Dostarcza API `Document`, `DocumentBuilder` i `Forms2OleControl` używane w przykładzie. |
| Visual Studio 2022 (lub dowolne IDE C#) | Ułatwia kompilację i uruchomienie przykładu. |
| Podstawowa znajomość C# | Potrzebna do zrozumienia przepływu kodu. |

> **Wskazówka:** Jeśli używasz wersji próbnej Aspose.Words, upewnij się, że przed uruchomieniem kodu ustawisz licencję, aby uniknąć znaków wodnych wersji ewaluacyjnej.

## Jak utworzyć dokument Word – ogólny przepływ pracy

Proces składa się z czterech logicznych kroków:

1. **Zainicjalizuj nowy dokument** i `DocumentBuilder`, aby go edytować.  
2. **Wstaw przycisk polecenia ActiveX** przy użyciu `InsertForms2OleControl`.  
3. **Skonfiguruj przycisk** – etykietę, rozmiar i pozycję.  
4. **Zapisz** dokument na dysku.

![Dokument Word z przyciskiem ActiveX](/images/activex-button.png "Zrzut ekranu dokumentu Word zawierającego przycisk polecenia ActiveX utworzony w C#")

## Jak wstawić przycisk polecenia ActiveX

Część **jak wstawić activex** zaczyna się od metody `InsertForms2OleControl`. Ta metoda tworzy kontrolkę opartą na COM, którą Word traktuje jako obiekt ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Dlaczego to działa:** `OleControlType.CommandButton` instruuje Aspose.Words, aby utworzyć klasyczny przycisk w stylu VB. Rozmiar i położenie są wyrażane w punktach (1 punkt = 1/72 cala), co zapewnia precyzyjną kontrolę nad układem.

## Jak dodać przycisk polecenia i ustawić rozmiar przycisku

Po wstawieniu kontrolki możesz dostosować jej właściwości wizualne. Krok **dodaj przycisk polecenia** obejmuje również **ustawienie rozmiaru przycisku**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explanation:**  

* `Caption` to etykieta wyświetlana na przycisku.  
* `Width` i `Height` pozwalają **ustawić rozmiar przycisku** po początkowym wstawieniu — przydatne, gdy rozmiar zależy od danych w czasie wykonywania.  
* `Left` i `Top` przestawiają kontrolkę bez ponownego tworzenia dokumentu.

> **Typowy błąd:** Zapomnienie o użyciu punktów zamiast pikseli spowoduje, że przycisk będzie za mały lub za duży. Zawsze konwertuj wartości w pikselach (`px * 72 / DPI`), jeśli zaczynasz od pomiarów ekranu.

## Jak dodać interaktywny przycisk (opcjonalnie)

Przycisk ActiveX może wykonywać makro po kliknięciu, ale osadzanie kodu VBA z C# wykracza poza zakres czystego przepływu pracy Aspose.Words. Zamiast tego możesz dodać właściwość placeholder, którą Word rozpozna jako nazwę makra.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Gdy użytkownik otworzy wygenerowany plik `.docx` w Wordzie, kliknięcie przycisku spróbuje uruchomić `MyMacroName`. Jeśli makro nie istnieje, Word poprosi użytkownika o jego utworzenie.

**Dlaczego możesz to użyć:** W formularzach korporacyjnych, gdzie makro wypełnia pola, kod C# musi jedynie umieścić przycisk; logika makra znajduje się w projekcie VBA dokumentu.

## Zapisz dokument i zweryfikuj wynik

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Oczekiwany wynik:** Otwierając `CommandButton.docx` w Microsoft Word zobaczysz przycisk oznaczony **Click Me**, umieszczony 100 pt od lewego marginesu i 120 pt od góry. Wymiary przycisku to **200 pt × 80 pt**. Kliknięcie przycisku wywołuje placeholder makra (jeśli istnieje).

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który łączy wszystkie elementy. Skopiuj go do nowego projektu aplikacji konsolowej, dodaj pakiet NuGet Aspose.Words i uruchom.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Uruchom program, a następnie otwórz wygenerowany plik. Zobaczysz **interaktywny przycisk** gotowy do dalszej personalizacji.

## Najczęściej zadawane pytania

| Pytanie | Odpowiedź |
|----------|-----------|
| **Czy to działa z .NET Core?** | Tak. Aspose.Words obsługuje .NET Standard, więc ten sam kod działa na .NET 5/6/7. |
| **Czy mogę używać innych kontrolek ActiveX (np. CheckBox)?** | Oczywiście. Zamień `OleControlType.CommandButton` na `OleControlType.CheckBox`, `OleControlType.OptionButton` itp. |
| **Co zrobić, jeśli potrzebuję większego przycisku na stronie w orientacji poziomej?** | Dostosuj proporcjonalnie właściwości `Width`, `Height`, `Left` i `Top`. Pamiętaj, że punkty pozostają takie same niezależnie od orientacji strony. |
| **Czy makro jest wymagane, aby przycisk był klikalny?** | Nie. Przycisk jest w pełni funkcjonalny jako element UI; makro dodaje jedynie niestandardowe zachowanie po kliknięciu. |

## Podsumowanie

Teraz wiesz, jak **utworzyć dokument Word** przy użyciu Aspose.Words, **dodać przycisk polecenia**, **ustawić rozmiar przycisku** i opcjonalnie powiązać przycisk z makrem, aby uzyskać zachowanie **dodawania interaktywnego przycisku**. To podejście pozwala automatyzować tworzenie formularzy, generować dynamiczne raporty lub budować prototypy interfejsu UI oparte na Wordzie bezpośrednio z C#.

Następnie możesz zgłębić:

* **Jak wstawić pola wyboru ActiveX** do formularzy ankietowych.  
* **Jak dodać treść sformatowanego tekstu** wokół przycisku przy użyciu `DocumentBuilder`.  
* **Jak zabezpieczyć dokument** zachowując funkcjonalność przycisku.  

Śmiało eksperymentuj z różnymi typami kontrolek, rozmiarami i nazwami makr, aby dopasować je do swojego konkretnego scenariusza. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Wstaw obrazek w linii w dokumencie Word przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Utwórz dokument Word z tabelą przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}