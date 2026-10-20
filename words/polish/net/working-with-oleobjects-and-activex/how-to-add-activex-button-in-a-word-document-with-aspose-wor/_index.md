---
category: general
date: 2026-08-14
description: Jak dodać przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words
  – dowiedz się, jak utworzyć pusty dokument Word i wstawić przycisk ActiveX programowo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: pl
lastmod: 2026-08-14
og_description: Jak dodać przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words.
  Ten samouczek pokazuje, jak utworzyć pusty dokument Word, wstawić przycisk ActiveX
  i zapisać wynik.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Jak dodać przycisk ActiveX w Word – przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Jak dodać przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words
url: /pl/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words

Jeśli potrzebujesz **jak dodać ActiveX** kontrolki do generowanego pliku Word, ten przewodnik pokaże Ci dokładne kroki. Nauczysz się **wstawiać przycisk ActiveX** programowo, zaczynając od **utworzenia pustego dokumentu Word** i kończąc na zapisanym pliku, który można otworzyć w Microsoft Word.

Dodanie przycisku, który uruchamia kod VBA lub wywołuje makro, jest częstym wymogiem w generatorach raportów, szablonach formularzy czy interaktywnych kontraktach. Korzystanie z Aspose.Words dla .NET pozwala budować dokument bez uruchamiania Office, co utrzymuje proces szybkim i przyjaznym dla serwera.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* .NET 6.0 (lub nowszy) SDK zainstalowany.  
* Visual Studio 2022 lub dowolne IDE kompatybilne z C#.  
* Pakiet NuGet **Aspose.Words for .NET** (`Aspose.Words` w wersji 24.9 lub nowszej).  
  Zainstaluj go za pomocą:
  ```bash
  dotnet add package Aspose.Words
  ```
* Środowisko Windows, jeśli planujesz testować przycisk ActiveX, ponieważ kontrolki ActiveX wymagają wersji Windows Microsoft Word.

## Krok 1: Utwórz pusty dokument Word

Pierwszym zadaniem jest **utworzenie pustego dokumentu Word** w pamięci. Aspose.Words udostępnia klasę `Document` do tego celu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` reprezentuje cały plik .docx. W tym momencie dokument nie zawiera żadnych stron, ale możesz od razu zaczynać dodawać zawartość.

## Krok 2: Zainicjalizuj DocumentBuilder

`DocumentBuilder` to pomocnik, który pozwala wstawiać tekst, obrazy i inne obiekty do dokumentu. Działa na instancji `Document`, którą właśnie utworzyłeś.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder utrzymuje pozycję kursora; wszystko, co wstawisz po tej linii, pojawi się na początku pierwszej strony.

## Krok 3: Wstaw kontrolkę ActiveX CommandButton

Aspose.Words udostępnia metodę `InsertForms2OleControl` do dodawania starszych kontrolek formularzy, w tym ActiveX. Metoda wymaga typu kontrolki oraz jej rozmiaru w punktach.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Zwrócony obiekt `Forms2OleControl` pozwala skonfigurować właściwości, takie jak nazwa kontrolki i jej podpis.

## Krok 4: Skonfiguruj właściwości przycisku

Ustawienie znaczącej `Name` umożliwia odwoływanie się do kontrolki z kodu VBA później. `Caption` to tekst, który użytkownik widzi na przycisku.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Trzymaj nazwę krótką i alfanumeryczną; Word odrzuci nazwy zawierające spacje lub znaki specjalne.

## Krok 5: Zapisz dokument

Na koniec zapisz dokument na dysku. Użyj rozszerzenia `.docx` dla nowoczesnych plików Word; przycisk ActiveX działa tak samo w plikach `.doc`, ale `.docx` jest preferowanym formatem dla nowych projektów.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Po otwarciu `ActiveXButton.docx` w Microsoft Word zobaczysz klikalny przycisk **Submit**. Jeśli włączysz makra, możesz podpiąć kod VBA do `btnSubmit_Click`, który wykona się po kliknięciu przycisku.

## Pełny, działający przykład

Połączenie wszystkich elementów daje samodzielny program, który możesz skopiować, wkleić i uruchomić.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Oczekiwany wynik** – Po uruchomieniu programu konsola wypisze lokalizację zapisu, a otwarcie wygenerowanego pliku w Wordzie pokaże przycisk oznaczony **Submit** umieszczony u góry pierwszej strony.

## Obsługa typowych pytań i przypadków brzegowych

### Czy przycisk działa we wszystkich wersjach Worda?

Kontrolki ActiveX są obsługiwane w wersji desktopowej Worda na Windows. Nie są renderowane w Word Online, Word dla macOS ani w aplikacjach mobilnych. Jeśli potrzebujesz interaktywności wieloplatformowej, rozważ użycie kontrolek treści lub rozwiązań opartych na HTML.

### Co zrobić, jeśli potrzebuję innego rozmiaru lub pozycji?

`InsertForms2OleControl` umieszcza kontrolkę w bieżącym miejscu kursora buildera. Aby ją przesunąć, najpierw przesuń kursor za pomocą `builder.MoveTo` przed wstawieniem lub zmodyfikuj właściwości `Left` i `Top` kontrolki po jej utworzeniu:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Czy mogę dodać inne typy ActiveX?

Tak. Wyliczenie `Forms2OleControlType` zawiera `CheckBox`, `OptionButton`, `ListBox` i inne. Zamień `CommandButton` na żądaną wartość wyliczenia i dostosuj właściwości odpowiednio.

### Czy makro jest wymagane, aby przycisk coś robił?

Sam przycisk nic nie robi, dopóki nie podłączysz kodu VBA. W Wordzie naciśnij **Alt+F11**, aby otworzyć edytor VBA, znajdź `btnSubmit_Click` i napisz pożądaną logikę. Wygenerowany dokument zachowa projekt VBA, jeśli zapiszesz go w formacie **SaveFormat.Doc** (starszy `.doc`), ale pliki `.docx` nie mogą przechowywać makr VBA. Użyj formatu `.doc`, jeśli potrzebujesz osadzonego VBA.

## Zakończenie

Teraz wiesz, **jak dodać ActiveX** kontrolki do pliku Word przy użyciu Aspose.Words. Postępując zgodnie z krokami: **utwórz pusty dokument Word**, zainicjalizuj `DocumentBuilder`, **wstaw przycisk ActiveX**, skonfiguruj jego właściwości i zapisz plik, możesz generować interaktywne szablony Word bezpośrednio z kodu .NET.

Następnie zgłęb tematy pokrewne, takie jak obsługa zdarzeń **insert ActiveX button**, dodawanie **create word document aspose** dla tabel lub obrazów oraz zabezpieczanie dokumentów z włączonymi makrami dla wdrożeń korporacyjnych. Eksperymentuj z różnymi typami kontrolek i opcjami układu, aby dostosować doświadczenie użytkownika do potrzeb Twojej aplikacji.

Miłego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}