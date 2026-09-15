---
category: general
date: 2026-09-14
description: Utwórz kontrolkę ActiveX w dokumencie Word przy użyciu C#. Dowiedz się,
  jak wstawić ActiveX, dodać interaktywny przycisk i programowo wygenerować plik .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: pl
lastmod: 2026-09-14
og_description: Utwórz kontrolkę ActiveX w dokumencie Word przy użyciu C#. Skorzystaj
  z tego pełnego przykładu, aby wstawić ActiveX, dodać interaktywny przycisk i zapisać
  plik.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Tworzenie kontrolki ActiveX w Wordzie przy użyciu C# – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Jak utworzyć kontrolkę ActiveX w dokumencie Word przy użyciu C#
url: /pl/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć kontrolkę ActiveX w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **utworzyć kontrolkę ActiveX** wewnątrz pliku Microsoft Word, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz dokładnie, jak wstawić ActiveX CommandButton, ustawić jego właściwości i zapisać powstały plik `.docx` używając wyłącznie kodu C#.

Dodanie interaktywnego przycisku do dokumentu Word jest częstym wymaganiem, gdy chcesz, aby użytkownicy końcowi wywoływali makra lub własną logikę bezpośrednio z interfejsu dokumentu. Poniższy przykład demonstruje **jak wstawić ActiveX** bez korzystania z narzędzi firm trzecich oraz obejmuje **jak utworzyć dokument Word** programowo.

Po zakończeniu tego samouczka będziesz w stanie **utworzyć przycisk za pomocą kodu**, dostosować jego etykietę i wygenerować przenośny plik Word, który zachowuje kontrolkę ActiveX.

## Wymagania wstępne

- .NET 6.0 lub nowszy (biblioteka Aspose.Words for .NET działa z .NET Core i .NET Framework)
- Odwołanie do pakietu NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Podstawowa znajomość C# i programowania obiektowego

## Krok 1: Skonfiguruj projekt i zaimportuj przestrzenie nazw

Utwórz nowy projekt konsolowy (lub zintegrować kod z istniejącą aplikacją C#). Zaimportuj wymagane przestrzenie nazw, aby kompilator mógł odnaleźć klasy przetwarzania Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Dlaczego ten krok ma znaczenie** – API `Aspose.Words` udostępnia klasy `Document`, `DocumentBuilder` i `Forms2OleControl`, które pozwalają manipulować plikami Word na poziomie obiektowym. Bez tych odwołań reszta kodu nie skompilowałaby się.

## Krok 2: Utwórz nowy dokument Word i obiekt DocumentBuilder

Obiekt `Document` reprezentuje cały pakiet `.docx`, natomiast `DocumentBuilder` oferuje płynne API do wstawiania treści.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Wyjaśnienie** – Utworzenie nowego `Document` zapewnia czyste płótno. Kursor buildera zaczyna się na początku pierwszej sekcji, gotowy do kolejnego wstawienia.

## Krok 3: Wstaw ActiveX CommandButton

Użyj `InsertForms2OleControl`, aby umieścić kontrolkę ActiveX w określonym miejscu. Metoda wymaga typu kontrolki oraz obiektu `RectangleF`, który definiuje współrzędne X/Y i rozmiar (w punktach).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Dlaczego to działa** – `OleControlType.CommandButton` instruuje API, aby utworzyć standardowy przycisk Windows CommandButton. Prostokąt pozycjonuje przycisk względem lewego górnego rogu strony, umożliwiając **dodanie interaktywnego przycisku** dokładnie tam, gdzie jest potrzebny.

## Krok 4: Skonfiguruj właściwości przycisku

Teraz ustaw widoczny tekst przycisku (`Caption`) oraz jego wewnętrzną nazwę (`Name`). Te właściwości są tym, co widzą użytkownicy i do czego może odwoływać się kod VBA później.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Praktyczna wskazówka** – `Name` musi być unikalna w obrębie dokumentu; w przeciwnym razie makra VBA mogą odwoływać się do niewłaściwej kontrolki.

## Krok 5: Zapisz dokument

Na koniec zapisz plik na dysku. Kontrolka ActiveX jest przechowywana wewnątrz pakietu Word, więc zapisany plik zachowa pełną funkcjonalność po otwarciu w Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Wynik** – Otwierając `CommandButton.docx` w Wordzie zobaczysz klikalny CommandButton oznaczony „Click Me”. Kontrolkę można połączyć z makrem poprzez interfejs Word (`Developer → Design Mode → Properties`).

## Pełny listing źródła

Połączenie wszystkich kroków daje pojedynczy, samodzielny program, który możesz skopiować, wkleić i uruchomić.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Oczekiwany wynik

Uruchomienie programu wypisuje linię potwierdzającą:

```
Document saved to C:\Temp\CommandButton.docx
```

Po otwarciu wygenerowanego pliku w Microsoft Word zobaczysz **CommandButton** umieszczony w określonych współrzędnych. Kliknięcie przycisku w trybie projektowania podświetla go; w trybie uruchomionym zachowuje się jak standardowy przycisk ActiveX.

## Typowe warianty i przypadki brzegowe

| Scenariusz | Dostosowanie |
|------------|--------------|
| **Inny typ kontrolki** | Zastąp `OleControlType.CommandButton` przez `OleControlType.CheckBox`, `OleControlType.OptionButton` itp. |
| **Wiele przycisków** | Wywołuj `InsertForms2OleControl` wielokrotnie, aktualizując współrzędne `RectangleF` dla każdego nowego przycisku. |
| **Dynamiczne rozmiary** | Oblicz wymiary prostokąta na podstawie rozmiaru strony (`builder.PageSetup.PageWidth`). |
| **Zapisywanie do strumienia** | Użyj `document.Save(stream, SaveFormat.Docx)`, gdy potrzebujesz zwrócić plik z interfejsu API webowego. |
| **Format Word 97‑2003** | Zmień format zapisu na `SaveFormat.Doc`, aby utworzyć plik `.doc`, który nadal zawiera kontrolkę ActiveX. |

> **Wskazówka:** Zawsze testuj wygenerowany dokument w docelowej wersji Worda, ponieważ starsze wersje mogą wymuszać ustawienia zabezpieczeń, które domyślnie wyłączają kontrolki ActiveX.

## Najczęściej zadawane pytania

**Czy to działa z .NET Core?**  
Tak. Biblioteka Aspose.Words jest wieloplatformowa i w pełni kompatybilna z .NET Core oraz .NET 5/6+.

**Czy mogę przypisać makro do przycisku programowo?**  
API nie osadza kodu VBA bezpośrednio. Po wygenerowaniu dokumentu otwórz go w Wordzie, włącz kartę Developer i nagraj lub napisz makro, które odwołuje się do `btnClick`.

**Co zrobić, gdy przycisk się nie wyświetla?**  
Sprawdź, czy karta `Developer` jest włączona w Wordzie i czy dokument nie jest otwarty w **Protected View**. Upewnij się także, że współrzędne prostokąta mieszczą się w marginesach strony.

## Podsumowanie

Teraz wiesz, jak **utworzyć kontrolkę ActiveX** wewnątrz pliku Word przy użyciu C#. Samouczek omówił **jak wstawić ActiveX**, pokazał **dodanie interaktywnego przycisku**, przedstawił **tworzenie dokumentu Word** od podstaw oraz zilustrował **tworzenie przycisku za pomocą kodu**, który zachowuje się po zapisaniu.  

Od tego momentu możesz badać dodatkowe typy ActiveX, połączyć przycisk z makrami VBA lub osadzić logikę w większej usłudze generowania dokumentów. Eksperymentuj z różnymi rozmiarami, pozycjami i właściwościami kontrolek, aby dopasować dokładne doświadczenie użytkownika, którego potrzebujesz.

---

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i zbadać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz nowy dokument Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Utwórz projekt VBA w dokumencie Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Utwórz i sformatuj dokument Word w Aspose.Words dla .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}