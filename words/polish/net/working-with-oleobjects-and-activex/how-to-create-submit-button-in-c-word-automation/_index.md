---
category: general
date: 2026-08-23
description: Utwórz przycisk zatwierdzania w automatyzacji Worda w C#. Dowiedz się,
  jak dodać przycisk ActiveX, ustawić nazwę przycisku, podpis oraz tekst programowo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: pl
lastmod: 2026-08-23
og_description: Utwórz przycisk zatwierdzania w automatyzacji Worda w C#. Ten przewodnik
  pokazuje, jak dodać przycisk ActiveX, ustawić jego nazwę, podpis oraz tekst przy
  użyciu Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Utwórz przycisk wyślij w automatyzacji Worda w C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Jak stworzyć przycisk wyślij w automatyzacji Worda w C#
url: /pl/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć przycisk Submit w automatyzacji Word przy użyciu C#

Jeśli potrzebujesz **create submit button** wewnątrz dokumentu Word przy użyciu C#, ten przewodnik przeprowadzi Cię przez cały proces. Zobaczysz, jak dodać przycisk ActiveX, przypisać programową nazwę oraz ustawić podpis przycisku, aby wyglądał jak zwykły *Submit* kontrolka.

Automatyzacja kontrolek formularzy w Wordzie może zastąpić ręczną pracę układu i zapewnić spójność w setkach dokumentów. W poniższych krokach dowiesz się również, jak **set button text**, **set button name** i **set button caption** — wszystko to jest niezbędne, gdy przycisk uczestniczy w przepływie pracy sterowanym makrami.

## Wymagania wstępne

* .NET 6.0 (lub nowszy) zainstalowany.
* Odwołanie do **Aspose.Words for .NET** (biblioteka udostępniająca `DocumentBuilder.InsertForms2OleControl`).
* Podstawowa znajomość C# oraz kontrolek formularzy ActiveX w Wordzie.

Możesz zainstalować Aspose.Words za pomocą NuGet:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Użyj najnowszej stabilnej wersji Aspose.Words, aby skorzystać z poprawek błędów i nowych funkcji związanych z kontrolkami ActiveX.

## Przegląd rozwiązania

Samouczek jest podzielony na trzy wyraźne kroki:

1. **Add ActiveX button** – użyj metody `InsertForms2OleControl`, aby umieścić przycisk polecenia w dokumencie.  
2. **Set button name** – przypisz unikalny identyfikator programowy za pomocą właściwości `Name`.  
3. **Set button caption** – określ widoczny tekst na przycisku za pomocą właściwości `Caption` (która również steruje **set button text**, które widzisz w interfejsie).

Po zakończeniu przewodnika będziesz mieć w pełni funkcjonalną rutynę **create submit button**, którą możesz ponownie wykorzystać w dowolnym projekcie automatyzacji Word.

## Krok 1: Dodaj przycisk ActiveX do dokumentu

Pierwszym zadaniem jest **add activex button** do pliku Word. Aspose.Words udostępnia enum `Forms2OleControlType.CommandButton` w tym celu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Dlaczego ten krok ma znaczenie:**  
Kontrolki ActiveX są jedynymi elementami formularzy Word, które mogą wykonywać makra VBA lub współdziałać z kodem zewnętrznym. Dodanie kontrolki tworzy miejsce, które późniejsze kroki mogą skonfigurować.

> **Przypadek brzegowy:** Jeśli dokument już zawiera kontrolkę o tej samej nazwie, Word automatycznie zmieni nazwę nowej (np. `CommandButton1`). Jawne ustawienie nazwy w następnym kroku zapobiega takim kolizjom.

## Krok 2: Ustaw nazwę przycisku

Solidne **set button name** jest kluczowe, gdy musisz odwołać się do kontrolki z VBA lub z innych części kodu C#. Właściwość `Name` nadaje przyciskowi identyfikator programowy.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Dlaczego warto ustawić nazwę:**  
Gdy dokument zostanie otwarty, VBA może pobrać przycisk za pomocą `ActiveDocument.InlineShapes("btnSubmit")`. Znacząca nazwa, taka jak `btnSubmit`, również wyjaśnia zamiar przy przeglądaniu XML dokumentu.

> **Wskazówka:** Trzymaj nazwy krótkie, alfanumeryczne i zaczynające się od litery, aby były zgodne z zasadami nazewnictwa VBA.

## Krok 3: Ustaw podpis przycisku (widoczny tekst)

Tekst, który użytkownicy widzą na przycisku, jest kontrolowany przez właściwość **set button caption**. W interfejsie Word pojawia się jako etykieta przycisku, co jest również **set button text**, które chcesz wyświetlić.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Dlaczego podpis ma znaczenie:**  
Podpis jest etykietą widoczną dla użytkownika. Zmiana go później nie wpływa na nazwę przycisku, więc możesz lokalizować interfejs bez łamania kodu zależnego od `btnSubmit`.

> **Częste pytanie:** *Czy mogę ustawić zarówno Caption, jak i Value?*  
> Dla `CommandButton`, `Caption` steruje etykietą, natomiast `Value` nie jest używane. Jeśli potrzebujesz ukrytej wartości, przechowaj ją w niestandardowej własności dokumentu.

## Pełny działający przykład

Połączenie trzech kroków daje pełną rutynę, którą możesz wkleić do dowolnej aplikacji konsolowej lub Windows:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Oczekiwany wynik

Uruchomienie programu tworzy `SubmitButton.docx`. Po otwarciu pliku w Microsoft Word:

* Pojawia się przycisk **Submit** w określonym miejscu.
* Nazwa przycisku to `btnSubmit` (sprawdź w *Developer → Design Mode → Properties*).
* Kliknięcie przycisku w trybie projektowania wyświetla etykietę *Submit*.

Masz teraz wielokrotnego użytku blok budujący dla dowolnego rozwiązania Word opartego na formularzach.

## Dodatkowe uwagi

### Obsługa kolizji nazw

Jeśli uruchomisz rutynę wielokrotnie na tym samym dokumencie, Word może automatycznie zmienić nazwy duplikatów kontrolek. Aby zapewnić unikalność, możesz dodać przedrostek GUID:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Lokalizacja podpisu przycisku

W dokumentach wielojęzycznych przechowuj podpisy w pliku zasobów i przypisuj je w czasie wykonywania:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Reagowanie na kliknięcie przycisku

Sam przycisk nie zawiera logiki kliknięcia w C#. Zazwyczaj dołączasz makro VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Ponieważ masz **set button name** ustawione na `btnSubmit`, nazwa makra automatycznie podąża za konwencją `<Name>_Click`.

## FAQ – Rozwiązywanie problemów

| Question | Answer |
|----------|--------|
| **Dlaczego przycisk jest pusty?** | Upewnij się, że ustawiłeś właściwość `Caption`; bez niej przycisk nie wyświetla tekstu. |
| **Czy mogę użyć innej kontrolki ActiveX?** | Tak. Zamień `Forms2OleControlType.CommandButton` na `CheckBox`, `OptionButton` itp., ale właściwości się różnią. |
| **Czy jest to kompatybilne z .NET Core?** | Aspose.Words for .NET obsługuje .NET 6+, więc ten sam kod działa na .NET Core i .NET Framework. |
| **Co jeśli dokument już ma przycisk?** | Użyj unikalnej `Name` (np. dodaj GUID), aby uniknąć konfliktów. |

## Zakończenie

Teraz wiesz, jak programowo **create submit button** w dokumencie Word przy użyciu C#. Postępując zgodnie z trzema krokami — **add activex button**, **set button name** i **set button caption** — możesz niezawodnie **set button text**, **set button name** oraz **set button caption** dla dowolnego zautomatyzowanego rozwiązania formularza.

Od tego momentu możesz rozważyć:

* Dodanie makr VBA reagujących na kliknięcie **submit button**.
* Stylizowanie przycisku za pomocą własnych czcionek lub kolorów poprzez podstawowy XML.
* Generowanie wielu przycisków w pętli dla dynamicznych formularzy.

Śmiało eksperymentuj z różnymi podpisami, nazwami i pozycjami, aby dopasować je do swojego konkretnego przepływu pracy. Miłej automatyzacji!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz kształt grupowy w dokumencie Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Utwórz wykres liniowy w Wordzie przy użyciu Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Utwórz dokument Word z nagłówkiem i stopką przy użyciu Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}