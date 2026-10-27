---
category: general
date: 2026-10-23
description: Utwórz pusty dokument Word w C# i dowiedz się, jak wstawiać kontrolki
  ActiveX, w tym przycisk, przy użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: pl
lastmod: 2026-10-23
og_description: Utwórz pusty dokument Word w C# i dowiedz się, jak wstawiać kontrolki
  ActiveX, w tym przycisk, przy użyciu Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Utwórz pusty dokument Word i dodaj przycisk ActiveX w C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Utwórz pusty dokument Word i dodaj przycisk ActiveX w C#
url: /pl/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word i dodaj przycisk ActiveX w C#

Jeśli potrzebujesz **create blank Word document** programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz kompletny, działający przykład, który tworzy nowy dokument, wstawia przycisk ActiveX CommandButton i zapisuje plik — wszystko przy użyciu Aspose.Words for .NET.

Praca z plikami Word często wymaga czegoś więcej niż zwykły tekst. Dodanie **ActiveX button** pozwala osadzić interaktywną funkcjonalność, którą można wykorzystać w szablonach z włączonymi makrami lub rozwiązaniach wyłącznie dla Windows. Po zakończeniu tego samouczka będziesz w stanie wstawić dowolny kontrolkę ActiveX, ale skupiamy się na najczęstszym scenariuszu: **word document activex button**, który wysyła formularz.

## Wymagania wstępne

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7+)
* Visual Studio 2022 (lub dowolne IDE C#)
* **Aspose.Words for .NET** pakiet NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Podstawowa znajomość składni C#

> **Wskazówka:** Aspose.Words jest komercyjną biblioteką, ale oferuje darmową tymczasową licencję do testów. Zainstaluj licencję wcześnie, aby uniknąć znaku wodnego oceny.

## Krok 1: Utwórz pusty dokument Word przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie obiektu `Document`. Reprezentuje on pusty plik `.docx` w pamięci.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` rozpoczyna się bez sekcji, stron ani zawartości. To czysta karta, której potrzebujesz w scenariuszach **create blank word document**, takich jak generowanie raportów od podstaw.

## Krok 2: Uzyskaj DocumentBuilder do edycji dokumentu

`DocumentBuilder` zapewnia wygodne API do dodawania tekstu, obrazów i kontrolek. Użyjemy go do pozycjonowania kontrolki ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder automatycznie dodaje domyślną sekcję i pierwszą stronę, więc możesz od razu zaczynać wstawiać obiekty.

## Krok 3: Jak wstawiać kontrolki ActiveX do dokumentu

Aspose.Words udostępnia metodę `InsertForms2OleControl` do osadzania obiektów OLE/ActiveX. Metoda wymaga typu kontrolki, szerokości i wysokości (w punktach). Poniżej wstawiamy **CommandButton** — klasyczny przycisk formularza, który widzisz w starszych szablonach Word.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Dlaczego to działa:** `Forms2OleControlType.COMMANDBUTTON` instruuje Word, aby utworzył przycisk, który może reagować na zdarzenia kliknięcia, gdy dokument zostanie otwarty w środowisku Windows obsługującym ActiveX.

## Krok 4: Utwórz kontrolkę ActiveX – ustaw jej właściwości

Teraz nadamy przyciskowi programową nazwę i widoczną etykietę. To część **create activex control**, którą programiści często pomijają.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` to identyfikator, którego będziesz używać w makrach VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` to etykieta wyświetlana na samym przycisku.

## Krok 5: Zapisz dokument Word z przyciskiem ActiveX

Na koniec zapisz dokument na dysku. Rozszerzenie pliku musi być `.docx` (lub `.docm`, jeśli planujesz później dodać makra). Przykład zapisuje do folderu zastępczego — zamień go na własną ścieżkę.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Kiedy otworzysz powstały plik w Microsoft Word (tylko Windows), zobaczysz działający **word document activex button**, który można podłączyć do kodu VBA.

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do nowego projektu konsolowego.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Oczekiwany wynik po uruchomieniu programu**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Otwórz wygenerowany `ActiveXButton.docx` w Wordzie, a zobaczysz przycisk oznaczony **Submit** umieszczony u góry pierwszej strony.

## Przypadki brzegowe i typowe pułapki

| Situation | What to watch for | Recommendation |
|-----------|-------------------|----------------|
| Uruchamianie na macOS lub Linux | ActiveX jest technologią tylko dla Windows, więc przycisk będzie wyświetlany jako placeholder. | Używaj tego samouczka wyłącznie dla szablonów przeznaczonych na Windows. |
| Dokument otwarty w Word Online | Kontrolki ActiveX nie są obsługiwane w widoku przeglądarki. | Zapewnij alternatywny interfejs UI lub poinstruuj użytkowników, aby otworzyli plik w aplikacji desktopowej. |
| Potrzeba pliku z włączonymi makrami | Pliki `.docx` nie mogą przechowywać kodu VBA. | Zapisz jako `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) i dodaj makro osobno. |
| Niezgodność rozmiaru kontrolki | Wartości szerokości/wysokości są w punktach (1 pt ≈ 1/72 in). | Dostosuj wartości liczbowe, aby uzyskać pożądany rozmiar wizualny. |

## Najczęściej zadawane pytania

**Jak wstawiać kontrolki ActiveX inne niż przycisk?**  
Użyj tej samej metody `InsertForms2OleControl`, ale przekaż inną wartość wyliczenia `Forms2OleControlType`, taką jak `COMBOBOX` lub `LISTBOX`.

**Czy mogę zmienić czcionkę lub kolor przycisku?**  
Wygląd przycisku ActiveX jest kontrolowany przez aplikację hosta (Word) oraz podstawowy motyw Windows. Możesz modyfikować właściwości takie jak `ForeColor` i `BackColor` za pomocą VBA po otwarciu dokumentu.

**Czy istnieje sposób, aby dodać obsługę zdarzenia kliknięcia bezpośrednio z C#?**  
Nie. Zdarzenie kliknięcia musi być obsłużone przez VBA lub dodatek Word, ponieważ przycisk działa wewnątrz procesu Word, a nie Twojej aplikacji .NET.

## Zakończenie

Teraz wiesz, jak **create blank Word document** programowo i osadzić **ActiveX button** przy użyciu Aspose.Words for .NET. Omówione kroki:

1. Utwórz instancję `Document`.
2. Użyj `DocumentBuilder` do pracy z plikiem.
3. Wywołaj `InsertForms2OleControl`, aby **how to insert activex** kontrolki.
4. Skonfiguruj właściwości kontrolki (**create activex control**).
5. Zapisz plik, uzyskując **word document activex button** gotowy do integracji z VBA.

Od tego momentu możesz eksperymentować z dodawaniem innych typów kontrolek, podłączaniem makr VBA lub konwertowaniem dokumentu do PDF przy zachowaniu przycisku (jako statyczny obraz). Eksperymentuj z różnymi rozmiarami, etykietami i nazwami.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}