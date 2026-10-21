---
category: general
date: 2026-08-04
description: Twórz dokumenty Word programowo przy użyciu C#. Dowiedz się, jak programowo
  dodać przycisk polecenia za pomocą Aspose.Words w kilku prostych krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: pl
lastmod: 2026-08-04
og_description: Utwórz dokument Word programowo przy użyciu Aspose.Words. Ten przewodnik
  pokazuje, jak programowo dodać przycisk polecenia, skonfigurować go i zapisać plik.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Tworzenie dokumentu Word programowo – pełny poradnik C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tworzenie dokumentu Word programowo – przewodnik krok po kroku
url: /pl/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word programowo – kompletny samouczek C#

Jeśli potrzebujesz **create word document programmatically**, ten przewodnik pokazuje dokładnie, jak to zrobić przy użyciu Aspose.Words for .NET. W zaledwie kilku linijkach C# możesz wygenerować pusty plik `.docx`, **programmatically add command button** kontrolki, ustawić ich właściwości i zapisać wynik.  

Kroki poniżej obejmują wszystko, od konfiguracji projektu po obsługę przypadków brzegowych, dzięki czemu możesz skopiować kod do własnej aplikacji i uruchomić go bez modyfikacji.

## Co osiągniesz

* Zainicjuj nowy dokument Word w całości w pamięci.  
* **Programmatically add command button** kontrolki OLE w dowolnym miejscu i rozmiarze.  
* Skonfiguruj podpis przycisku, wewnętrzną nazwę oraz inne właściwości OLE.  
* Zapisz wygenerowany dokument na dysku lub do strumienia w celu dalszego przetwarzania.

### Wymagania wstępne

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).  
* Ważna licencja Aspose.Words for .NET (lub darmowa wersja ewaluacyjna).  
* Podstawowa znajomość C# i Visual Studio (lub dowolnego wybranego IDE).  

> **Pro tip:** Jeśli uruchomisz przykład bez licencji, Aspose.Words doda małą wodną znak wodny ewaluacji na pierwszej stronie.

## Krok 1: Skonfiguruj projekt i zaimportuj wymagane przestrzenie nazw

Utwórz nową aplikację konsolową (lub zintegrować z istniejącą usługą) i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Następnie dołącz niezbędne przestrzenie nazw na początku pliku `.cs`:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Te importy dają dostęp do `Document`, `DocumentBuilder`, `Forms2OleControl` oraz struktury `RectangleF` używanej do pozycjonowania.

## Krok 2: Zainicjuj nowy dokument Word

Pierwsza operacja w każdym przepływie **create word document programmatically** polega na utworzeniu obiektu `Document`. Obiekt ten istnieje wyłącznie w pamięci, dopóki nie zostanie jawnie zapisany.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` działa jak kursor, który śledzi, gdzie zostanie umieszczony kolejny element. Używanie go utrzymuje kod zwięzły i odzwierciedla sposób, w jaki wpisywałbyś tekst bezpośrednio w Wordzie.

## Krok 3: Wstaw kontrolkę OLE przycisku poleceń

Aspose.Words udostępnia metodę `InsertForms2OleControl`, aby osadzić obiekty OLE, takie jak przyciski poleceń, pola wyboru czy pola kombi. Metoda wymaga trzech argumentów:

1. Wartość wyliczenia `ControlType` (tutaj `CommandButton`).  
2. `RectangleF`, który definiuje pozycję X‑Y oraz szerokość‑wysokość kontrolki (mierzone w punktach, gdzie 72 pt = 1 inch).  
3. Opcjonalnie dodatkowe właściwości OLE (nie są potrzebne dla podstawowego przycisku).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Why this works:** `InsertForms2OleControl` tworzy kontener OLE w dokumencie i zwraca obiekt `Forms2OleControl`. Obiekt ten pozwala manipulować podstawowym obiektem OLE (rzeczywistym przyciskiem) bez konieczności pracy z niskopoziomowym COM interop.

## Krok 4: Skonfiguruj podpis i wewnętrzną nazwę przycisku

Po wstawieniu zazwyczaj chcesz nadać przyciskowi widoczny dla użytkownika etykietę oraz wewnętrzny identyfikator, do którego może odwoływać się makro lub dodatek.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` to tekst wyświetlany na przycisku w interfejsie Worda.  
* `Name` to programowy identyfikator używany przez VBA lub zewnętrzne skrypty automatyzacji.

### Opcjonalnie: Przypisz makro do przycisku

Jeśli planujesz uruchomić makro VBA po kliknięciu przycisku, możesz dołączyć nazwę makra:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Edge case:** Gdy dokument docelowy zostanie otwarty na maszynie bez tego makra, Word wyświetli ostrzeżenie bezpieczeństwa. Zawsze podpisuj swoje makra lub informuj użytkowników o wymaganych ustawieniach.

## Krok 5: Zapisz dokument

Możesz zapisać plik na dysku, w `MemoryStream` lub bezpośrednio do obiektu odpowiedzi w API webowym. Najprostsze podejście dla demonstracji konsolowej to zapis do lokalnego folderu:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wynikowy `.docx` otwiera się w Microsoft Word z działającym przyciskiem, który wyświetla „Click Me”. Kliknięcie przycisku wywoła przypisane makro (jeśli istnieje) lub po prostu wyświetli domyślną wiadomość.

## Pełny działający przykład

Skopiuj poniższy program do `Program.cs` i uruchom go. Demonstracja obejmuje cały przepływ **create word document programmatically**, w tym obsługę błędów.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Expected result:** Otwierając `CommandButton.docx` w Wordzie pojawia się przycisk oznaczony „Click Me”. Najazd kursorem na przycisk ujawnia nazwę `cmdClickMe` w panelu właściwości.

## Częste pytania i rozwiązywanie problemów

| Pytanie | Odpowiedź |
|----------|--------|
| *Czy mogę dodać przycisk do istniejącego dokumentu?* | Tak. Załaduj plik przy pomocy `new Document("Existing.docx")`, a następnie użyj tego samego wywołania `InsertForms2OleControl`. |
| *Jakich jednostek używa `RectangleF`?* | Punktów (1 inch = 72 pt). Dostosuj wartości, aby precyzyjnie pozycjonować przycisk. |
| *Czy przycisk będzie działał w Wordzie na Macu?* | Kontrolki OLE są obsługiwane tylko w wersji Windows Word. Na Macu przycisk pojawia się jako statyczny obraz. |
| *Czy potrzebuję licencji do użytku produkcyjnego?* | Licencja komercyjna usuwa znaki wodne ewaluacji i odblokowuje pełną funkcjonalność. |
| *Jak zmienić rozmiar przycisku po wstawieniu?* | Zmodyfikuj `commandButton.Width` i `commandButton.Height` lub ponownie wstaw przycisk z nowym `RectangleF`. |

## Rozszerzanie rozwiązania

Teraz, gdy wiesz, jak **programmatically add command button** kontrolki, możesz zgłębić powiązane tematy:

* **Insert other form controls** – użyj `ControlType.CheckBox`, `ControlType.OptionButton` itp. (obejmuje drugorzędne słowo kluczowe *Aspose.Words InsertForms2OleControl*).  
* **Populate the document with dynamic data** – scal dane z bazy danych do tabel lub pól korespondencji seryjnej.  
* **Export to PDF** – po dodaniu przycisku wywołaj `doc.Save("output.pdf", SaveFormat.Pdf)`, aby uzyskać wersję PDF (dotyczy *C# Word automation*).  

## Zakończenie

Masz teraz kompletny, gotowy do produkcji wzorzec dla **create word document programmatically** i **programmatically add command button** przy użyciu Aspose.Words for .NET. Samouczek obejmował konfigurację projektu, inicjalizację dokumentu, wstawianie przycisku OLE, konfigurację właściwości oraz zapis pliku. Śmiało dostosowuj kod, aby wstawiać inne kontrolki formularzy, dołączać makra lub integrować logikę z usługami webowymi czy zadaniami w tle.

Miłego kodowania i przyjemności z automatyzacji dokumentów Word!

## Co powinieneś się nauczyć dalej?

Poniższe samouczki dotyczą ściśle powiązanych tematów, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}