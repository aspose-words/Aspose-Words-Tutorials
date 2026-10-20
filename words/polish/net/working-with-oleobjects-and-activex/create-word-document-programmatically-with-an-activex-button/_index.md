---
category: general
date: 2026-10-20
description: Utwórz dokument Word programowo i dodaj przycisk polecenia przy użyciu
  Aspose.Words. Dowiedz się, jak wstawić kontrolkę ActiveX i ustawić napis przycisku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: pl
lastmod: 2026-10-20
og_description: Utwórz dokument Word programowo i osadź przycisk polecenia ActiveX.
  Ten samouczek wyjaśnia, jak wstawić kontrolkę i ustawić jej podpis przy użyciu Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Utwórz dokument Word programowo – dodaj przycisk ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Utwórz dokument Word programowo przy użyciu przycisku ActiveX
url: /pl/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie dokumentu Word programowo z przyciskiem ActiveX

Utwórz dokument Word programowo przy użyciu Aspose.Words, a następnie dodaj przycisk polecenia, który użytkownicy mogą kliknąć. Ten przewodnik przeprowadzi Cię przez wstawianie kontrolki ActiveX, konfigurowanie jej właściwości oraz zapisanie wyniku jako pliku **.docx**.

Zobaczysz kompletny, gotowy do uruchomienia przykład, który możesz skopiować do aplikacji konsolowej. Po zakończeniu tutorialu będziesz w stanie wygenerować plik Word zawierający w pełni funkcjonalny przycisk polecenia oraz zrozumiesz, jak **add command button**, **add activex control**, **insert activex button** i **set button caption** bez opuszczania kodu C#.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 SDK lub nowszy zainstalowany  
* Visual Studio 2022 (lub dowolne IDE obsługujące C#)  
* Plik licencji Aspose.Words for .NET (bezpłatna wersja próbna działa w tym przykładzie)  
* Podstawową znajomość C# i systemu projektów .NET  

Nie są wymagane dodatkowe pakiety NuGet poza **Aspose.Words**, ponieważ obsługa ActiveX jest wbudowana w bibliotekę.

## Krok 1: Konfiguracja projektu i dodanie Aspose.Words

1. Otwórz terminal lub Visual Studio i utwórz nowy projekt konsolowy:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Dodaj pakiet Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Opcjonalnie) Jeśli masz plik licencji, umieść go w katalogu głównym projektu i dodaj następującą linię na początku `Program.cs`, aby uniknąć znaków wodnych oceny:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Krok 2: Utworzenie dokumentu Word programowo – inicjalizacja dokumentu

Pierwszą operacją jest **create Word document programmatically**. Robisz to, tworząc obiekt `Document` oraz `DocumentBuilder`, który umożliwia edycję zawartości dokumentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` reprezentuje cały plik, natomiast `DocumentBuilder` utrzymuje kursor, który możesz przenieść w dowolne miejsce w dokumencie. To rozdzielenie utrzymuje API w czystości i pozwala później **add activex control** bez ręcznego zarządzania strukturami niskiego poziomu.

## Krok 3: Dodanie przycisku polecenia – wstawianie kontrolki ActiveX

Teraz **add command button** poprzez wstawienie kontrolki ActiveX typu `OleControlType.CommandButton`. Metoda `InsertForms2OleControl` wymaga typu kontrolki, lokalizacji (`Point`) i rozmiaru (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Powyższe wywołanie **insert activex button** do dokumentu w dokładnie określonych współrzędnych. Współrzędne mierzone są w punktach (1 pt ≈ 1/72 in). Jeśli potrzebujesz przycisku w konkretnym akapicie, najpierw przesuń kursor buildera:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Krok 4: Ustawienie podpisu przycisku – dostosowanie tekstu przycisku polecenia

Przycisk bez etykiety jest mylący, więc **set button caption** na coś sensownego. Właściwość `Caption` definiuje tekst wyświetlany na przycisku, natomiast `Name` nadaje kontrolce identyfikator programistyczny.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Jeśli później wyeksportujesz dokument do formatu obsługującego makra (`.docm`), wartość `OnClick` musi odpowiadać nazwie makra VBA. Dla zwykłego `.docx` właściwość jest przechowywana, ale nie jest wykonywana, co jest wystarczające w większości scenariuszy automatyzacji.

## Krok 5: Zapisanie dokumentu zawierającego przycisk ActiveX

Po skonfigurowaniu kontrolki możesz **save the document**. Wybierz katalog, do którego masz prawo zapisu, i użyj rozszerzenia `.docx` dla maksymalnej kompatybilności.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Po otwarciu wygenerowanego pliku w Microsoft Word zobaczysz przycisk oznaczony **Submit** w określonych współrzędnych. Kliknięcie przycisku w aplikacji desktopowej spróbuje uruchomić makro `SubmitForm` (jeśli istnieje).

## Krok 6: Weryfikacja wyniku i rozwiązywanie typowych problemów

1. Otwórz `ActiveXCommandButton.docx` w Microsoft Word.  
2. Przełącz się na **Design Mode** (zakładka Developer → **Design Mode**), aby zobaczyć obramowania przycisku.  
3. Jeśli przycisk się nie pojawi, sprawdź, czy zakładka **Developer** jest włączona i czy Twoja wersja Word obsługuje kontrolki ActiveX.  
4. Dla plików obsługujących makra (`.docm`) upewnij się, że nazwa makra w `OnClick` odpowiada procedurze VBA; w przeciwnym razie Word wyświetli ostrzeżenie bezpieczeństwa.

### Porada

Kontrolki ActiveX działają wyłącznie w systemie Windows. Jeśli potrzebujesz interaktywności wieloplatformowej, rozważ użycie **Content Controls** (`RichTextContentControl`) zamiast przycisku ActiveX.

## Pełny kod źródłowy

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Skopiuj go do `Program.cs` i uruchom `dotnet run`.



## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu wraz z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}