---
category: general
date: 2026-11-18
description: Utwórz pusty dokument Word i wstaw przycisk ActiveX przy użyciu C#. Dowiedz
  się, jak dodać kontrolkę, ustawić podpis przycisku i zapisać plik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: pl
lastmod: 2026-11-18
og_description: Utwórz pusty dokument Word i wstaw przycisk ActiveX przy użyciu C#.
  Skorzystaj z tego pełnego samouczka, aby dodać kontrolkę, ustawić podpis przycisku
  i zapisać wynik.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Utwórz pusty dokument Word i wstaw przycisk ActiveX – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Utwórz pusty dokument Word i wstaw przycisk ActiveX
url: /pl/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word i wstaw przycisk ActiveX

Jeśli potrzebujesz **utworzyć pusty dokument Word** i umieścić w nim interaktywny przycisk ActiveX, ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words for .NET. Zobaczysz pełny kod, zrozumiesz, dlaczego każda linia ma znaczenie, i nauczysz się **ustawiać podpis przycisku**, aby kontrolka wyglądała na gotową do interakcji z użytkownikiem.

Oprócz głównego celu omówimy **jak wstawić ActiveX**, kroki **jak dodać kontrolkę** do pliku Word oraz niuanse **wstawiania przycisku ActiveX** z niestandardowym podpisem. Po zakończeniu będziesz mieć wielokrotnego użytku wzorzec dla każdego scenariusza automatyzacji dokumentów, który wymaga osadzonych elementów UI.

## Co się nauczysz

* Jak **utworzyć pusty dokument Word** programowo.  
* Dokładne wywołania API potrzebne do **wstawienia przycisku ActiveX** i skonfigurowania jego właściwości.  
* Jak **ustawić podpis przycisku**, aby kontrolka wyświetlała żądany tekst.  
* Wskazówki dotyczące zapisywania pliku w wybranej lokalizacji oraz radzenia sobie z typowymi pułapkami.

### Wymagania wstępne

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).  
* Aspose.Words for .NET zainstalowany (`Install-Package Aspose.Words`).  
* Podstawowa znajomość C# oraz Visual Studio lub dowolnego środowiska IDE zgodnego z .NET.

---

## Utwórz pusty dokument Word przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie pustego obiektu `Document`. Obiekt ten reprezentuje plik Word, który nie zawiera żadnej treści, dopóki nie dodamy czegoś.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Dlaczego to ważne*: Pusty `Document` zapewnia czyste płótno. Możesz później dodawać akapity, tabele lub kontrolki, nie martwiąc się o istniejące formatowanie.

---

## Zainicjalizuj DocumentBuilder do pracy z dokumentem

`DocumentBuilder` to klasa pomocnicza, która pozwala wstawiać treść w bieżącej pozycji kursora. Automatycznie śledzi, gdzie znajdujesz się w dokumencie.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego to ważne*: Bez `DocumentBuilder` musiałbyś ręcznie manipulować niskopoziomowym drzewem węzłów. Builder upraszcza wstawianie tekstu, obrazów i kontrolek ActiveX.

---

## Jak wstawić przycisk ActiveX (insert activex button)

Teraz używamy `InsertForms2OleControl`, aby osadzić kontrolkę ActiveX. Metoda wymaga trzech argumentów:

1. Typ kontrolki (`OleControlType.CommandButton`).  
2. Wewnętrzna nazwa kontrolki (używana przez VBA lub kod makr).  
3. `RectangleF` definiujący pozycję i rozmiar na stronie.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Dlaczego to ważne*: To jest sedno **jak wstawić activex** do dokumentu Word. Współrzędne prostokąta podawane są w punktach (1 punkt = 1/72 cala). Dostosuj je, aby umieścić przycisk w żądanym miejscu.

### Wskazówka

Jeśli potrzebujesz, aby przycisk pojawił się na konkretnej stronie, najpierw przesuń kursor buildera:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Jak ustawić podpis przycisku (set button caption)

Po umieszczeniu kontrolki możesz modyfikować jej właściwości. Najbardziej widoczną właściwością jest `Caption`, która określa tekst wyświetlany na przycisku.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Dlaczego to ważne*: Użytkownicy widzą podpis, a nie wewnętrzną nazwę. Zmiana go sprawia, że przycisk ma sens w ostatecznym dokumencie.

---

## Zapisz dokument zawierający przycisk

Na koniec zapisz dokument na dysku. Możesz wybrać dowolny obsługiwany format (`.docx`, `.pdf` itp.). Tutaj zapisujemy jako dokument Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Dlaczego to ważne*: Zachowanie pliku umożliwia otwarcie go w Microsoft Word i przetestowanie przycisku. Po otwarciu dokumentu przycisk pojawi się z podpisem „Press”.

### Oczekiwany rezultat

Otwarcie `with_button.docx` w Wordzie pokazuje pustą stronę z prostokątnym przyciskiem oznaczonym **Press**. Kliknięcie przycisku nie robi nic domyślnie, ponieważ nie jest podłączona żadna makro VBA, ale kontrolka jest w pełni funkcjonalna i może być później podłączona do kodu.

---

## Jak dodać kontrolkę do konkretnego akapitu (how to add control)

Czasami chcesz umieścić przycisk w określonym akapicie, na przykład po jakimś tekście instrukcyjnym. Użyj `MoveTo`, aby ustawić pozycję buildera przed wstawieniem kontrolki.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Dlaczego to ważne*: Ten wzorzec demonstruje **jak dodać kontrolkę** w kontekście, zapewniając logiczny układ dokumentu.

---

## Typowe pułapki i jak ich unikać

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Przycisk pojawia się poza stroną | Współrzędne prostokąta znajdują się poza marginesami strony | Użyj `builder.PageSetup`, aby uzyskać wymiary strony i obliczyć bezpieczny `RectangleF`. |
| Podpis się nie wyświetla | `Caption` ustawiono przed pełnym zainicjowaniem kontrolki | Ustaw `Caption` **po** wywołaniu `InsertForms2OleControl`, jak pokazano w Kroku 4. |
| Dokument zapisuje się bez przycisku | Kursor buildera został przeniesiony po wstawieniu bez zatwierdzenia zmian | Pozostaw builder na tej samej stronie lub wywołaj `builder.Document.UpdatePageLayout()` przed zapisem. |

---

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić. Tworzy on pusty plik Word, wstawia przycisk ActiveX, ustawia jego podpis i zapisuje wynik.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Wynik**: Po uruchomieniu programu otwórz `C:\Temp\with_button.docx` w Microsoft Word. Zobaczysz jedną stronę z tekstem „Below is an ActiveX button created programmatically:” oraz przyciskiem oznaczonym **Press**.

---

## Podsumowanie

Teraz wiesz, jak **utworzyć pusty dokument Word**, **wstawić przycisk ActiveX**, **ustawić podpis przycisku** i **zapisać** wynik przy użyciu Aspose.Words for .NET. Ten sam wzorzec można rozszerzyć na inne kontrolki ActiveX (checkboxy, listboxy itp.) poprzez zmianę `OleControlType`.  

Następnie możesz zbadać **jak wstawiać zdarzenia przycisku ActiveX** za pomocą VBA lub **jak dodać kontrolkę** do istniejących dokumentów, które już zawierają treść. Oba tematy opierają się bezpośrednio na koncepcjach przedstawionych tutaj.

Miłego kodowania i zachęcamy do eksperymentowania z różnymi rozmiarami, pozycjami i podpisami, aby dopasować je do wymagań UI Twojej aplikacji!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć dokument Word w C# z przyciskiem polecenia ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Jak dodać przycisk ActiveX do dokumentu Word przy użyciu Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}