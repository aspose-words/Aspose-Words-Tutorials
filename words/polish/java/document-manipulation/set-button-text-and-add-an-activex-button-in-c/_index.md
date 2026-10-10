---
category: general
date: 2026-10-10
description: Ustaw tekst przycisku i dodaj przycisk ActiveX w C# przy użyciu Aspose.Words.
  Dowiedz się, jak wstawić przycisk, utworzyć kontrolkę przycisku i dostosować podpis
  w dokumencie Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: pl
lastmod: 2026-10-10
og_description: Ustaw tekst przycisku i dodaj przycisk ActiveX w C# przy użyciu Aspose.Words.
  Postępuj zgodnie z tym przewodnikiem krok po kroku, aby wstawić przycisk, utworzyć
  kontrolkę przycisku i dostosować jego etykietę.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Ustaw tekst przycisku i dodaj przycisk ActiveX w C# – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Ustaw tekst przycisku i dodaj przycisk ActiveX w C#
url: /pl/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw tekst przycisku i dodaj przycisk ActiveX w C#

Jeśli potrzebujesz **ustawić tekst przycisku** na przycisku ActiveX w dokumencie Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Po zakończeniu tutorialu będziesz w stanie **wstawić przycisk**, utworzyć **kontrolkę przycisku** i dostosować jego podpis kilkoma liniami kodu C#.

Praca z kontrolkami ActiveX jest powszechna, gdy chcesz interaktywne formularze w Wordzie — niezależnie od tego, czy tworzysz szablon umowy, ankietę, czy wewnętrzne narzędzie. Przykład wykorzystuje Aspose.Words for .NET, bibliotekę umożliwiającą manipulację plikami Word bez zainstalowanego Microsoft Office.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 SDK lub nowszy zainstalowany  
* Visual Studio 2022 (lub dowolne IDE obsługujące C#)  
* Licencję Aspose.Words for .NET (bezpłatna wersja ewaluacyjna wystarczy do nauki)  

Potrzebujesz także odwołania do pakietu NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Jak wstawić przycisk do dokumentu Word

Pierwszym krokiem jest utworzenie nowego `Document` i `DocumentBuilder`. Builder jest punktem wejścia do dodawania treści, w tym kontrolek ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:** `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` udostępnia wysokopoziomowe metody takie jak `InsertParagraph` i `InsertFormField`. Rozpoczęcie od czystego dokumentu zapewnia, że przycisk pojawi się dokładnie tam, gdzie go potrzebujesz.

## Utwórz kontrolkę przycisku za pomocą Forms2OleControl

Teraz tworzymy właściwą kontrolkę przycisku. `Forms2OleControl` to klasa używana przez Aspose.Words dla wszystkich obiektów ActiveX, a typ `COMMANDBUTTON` renderuje się jako klikalny przycisk w Wordzie.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Wyjaśnienie:**  
* `InsertForms2OleControl` umieszcza kontrolkę w dokładnych współrzędnych, które podasz.  
* Rozmiar definiowany jest w punktach (1 punkt = 1/72 cala). Dostosuj te liczby, aby pasowały do Twojego układu.

## Dodaj kontrolkę ActiveX i nadaj jej unikalną nazwę

Każdy obiekt ActiveX powinien mieć odrębną nazwę, aby później móc się do niego odwołać (np. przy obsłudze zdarzeń w VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Wskazówka:** Unikaj spacji i znaków specjalnych w nazwie; Word traktuje nazwę jako identyfikator w swoim wewnętrznym modelu formularzy.

## Ustaw tekst przycisku (caption) na przycisku ActiveX

Tutaj wkracza główne słowo kluczowe **set button text**. Właściwość `Caption` definiuje etykietę, którą użytkownicy widzą na przycisku.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Możesz zmienić podpis w dowolnym momencie przed zapisaniem dokumentu. Jeśli później będziesz musiał zlokalizować interfejs, po prostu wywołaj ponownie `SetCaption` z innym ciągiem znaków.

## Zapisz dokument i zweryfikuj wynik

Na koniec zapisz dokument na dysku. Otworzenie pliku w Microsoft Word pokaże przycisk z własnym podpisem.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Oczekiwany wynik:** Po otwarciu *ActiveXButton.docx* w Wordzie zobaczysz przycisk umieszczony w określonych współrzędnych, oznaczony **Click Me**. Kliknięcie przycisku wywoła domyślne zachowanie przycisku poleceń Word (które możesz później dostosować za pomocą VBA).

![Set button text example](https://example.com/activex-button.png){alt="Przykład ustawiania tekstu przycisku"}

## Dodaj przycisk ActiveX i obsłuż zdarzenia (opcjonalnie)

Jeśli potrzebujesz, aby przycisk wykonywał niestandardową akcję, możesz dodać makro VBA reagujące na zdarzenie `Click`. Makro może być wstrzykiwane programowo, ale to wykracza poza zakres tego tutorialu. Ważne jest, że przycisk jest już obecny, a jego podpis ustawiony — gotowy do obsługi dowolnych zdarzeń, które wybierzesz.

## Typowe pułapki i jak ich unikać

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Przycisk wyświetla się nieprawidłowo wyrównany | Współrzędne podawane są w punktach, nie w pikselach | Przelicz wartości pikseli na punkty (`punkty = piksele * 72 / DPI`) |
| Podpis nie zmienia się po zapisaniu | `SetCaption` wywołane po `Save` | Zawsze ustawiaj podpis **przed** wywołaniem `doc.Save` |
| Kontrolka niewidoczna w starszych wersjach Worda | Niektóre starsze wersje Worda nie obsługują w pełni ActiveX | Testuj na docelowej wersji Worda; rozważ użycie `CheckBox` lub `DropDownList` jako alternatywy |
| Ostrzeżenie o licencji w wyniku | Licencja ewaluacyjna wygasła | Zastosuj ważną licencję Aspose.Words poprzez `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić. Zawiera wszystkie niezbędne dyrektywy `using` i demonstruje cały przepływ od tworzenia dokumentu po zapis.

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
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Uruchom program poleceniem `dotnet run`. Po wykonaniu otwórz *ActiveXButton.docx*, aby potwierdzić, że podpis przycisku brzmi **Click Me**.

## Podsumowanie tego, czego się nauczyłeś

* Nauczyłeś się, jak **set button text** na przycisku ActiveX przy użyciu Aspose.Words.  
* Zobaczyłeś dokładne kroki, jak **how to insert button**, **create button control** oraz **add activex control** do dokumentu Word.  
* Masz teraz wielokrotnego użytku fragment kodu, który możesz dostosować do dowolnego projektu automatyzacji formularzy w Wordzie.

## Kolejne kroki

* Zbadaj inne wartości `Forms2OleControlType`, takie jak `CHECKBOX` czy `LISTBOX`, aby budować bardziej rozbudowane formularze.  
* Połącz przycisk z makrem VBA, aby wykonywać obliczenia lub walidację danych.  
* Skorzystaj z API `FormField` Aspose.Words, aby odczytywać dane wprowadzone przez użytkownika po wypełnieniu dokumentu.

Śmiało eksperymentuj z rozmiarem, pozycją i podpisem, aby dopasować je do wymagań projektu. Jeśli napotkasz problemy, dokumentacja Aspose.Words zawiera szczegółowe odniesienia do każdej klasy użytej w tym tutorialu.

Miłego kodowania!


## Co powinieneś nauczyć się dalej?


Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu wraz z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}