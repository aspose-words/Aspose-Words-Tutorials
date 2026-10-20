---
category: general
date: 2026-07-29
description: Dodaj przycisk polecenia do dokumentu Word przy użyciu Aspose.Words.
  Dowiedz się, jak ustawić właściwości kontrolki ActiveX i ustawić podpis przycisku
  polecenia w kilku prostych krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: pl
lastmod: 2026-07-29
og_description: Dodaj przycisk polecenia do dokumentu Word przy użyciu Aspose.Words.
  Ten samouczek pokazuje, jak szybko ustawić właściwości kontrolki ActiveX i ustawić
  podpis przycisku polecenia.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Dodaj przycisk polecenia do dokumentu Word – Aspose.Words krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Dodaj przycisk polecenia do dokumentu Word przy użyciu Aspose.Words – Kompletny
  przewodnik
url: /pl/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj przycisk polecenia do dokumentu Word – Kompletny przewodnik programistyczny

Kiedykolwiek potrzebowałeś **add command button to word document**, ale nie byłeś pewien, które wywołania API użyć? Nie jesteś sam; wielu programistów napotyka tę przeszkodę, gdy po raz pierwszy próbują osadzić interaktywne kontrolki w pliku DOCX. Dobrą wiadomością jest to, że Aspose.Words sprawia to niezwykle łatwym. W tym przewodniku przejdziemy przez tworzenie kontrolki CommandButton ActiveX, **set activex control properties** oraz **set command button caption** — wszystko przy użyciu czystego kodu C#, który możesz od razu skopiować‑wkleić.

Po zakończeniu tego tutorialu będziesz mieć w pełni funkcjonalny plik Word zawierający klikalny przycisk „Submit”, gotowy do otwarcia w Microsoft Word. Bez zewnętrznych skryptów VBA, bez ręcznego manipulowania interfejsem — tylko czysta kontrola programistyczna.

## Czego się nauczysz

* Jak utworzyć pusty dokument Word i `DocumentBuilder`.
* Dokładne wywołanie metody do **add command button to word document** przy użyciu Aspose.Words.
* Sposoby **set activex control properties**, takie jak rozmiar, pozycja i nazwa.
* Prawidłową technikę **set command button caption**, aby przycisk wyświetlał dokładnie to, co chcesz.
* Wskazówki dotyczące obsługi przypadków brzegowych, takich jak różne typy przycisków, skalowanie DPI i kompatybilność wersji Worda.

> **Wymagania wstępne:** Visual Studio (lub dowolne IDE C#) z zainstalowanym Aspose.Words for .NET (pakiet NuGet `Aspose.Words`). Nie wymagana wcześniejsza znajomość ActiveX.

---

## Krok 1: Konfiguracja projektu i import przestrzeni nazw

Zanim będziemy mogli **add command button to word document**, potrzebujemy projektu C#, który odwołuje się do Aspose.Words. Utwórz nową aplikację konsolową .NET, a następnie dodaj pakiet NuGet:

```bash
dotnet add package Aspose.Words
```

Teraz wprowadź wymagane przestrzenie nazw do swojego pliku źródłowego:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Te trzy dyrektywy `using` dają dostęp do klas `Document`, `DocumentBuilder` oraz `Forms2OleControl`, które napędzają wstawianie ActiveX.

*Pro tip:* Jeśli używasz Visual Studio, IDE zasugeruje automatyczne dodanie tych dyrektyw, gdy wpiszesz nazwy klas.

---

## Krok 2: Utwórz pusty dokument i builder

Świeży obiekt `Document` reprezentuje pusty plik Word. `DocumentBuilder` to nasz wygodny „długopis”, który pozwala rysować, wstawiać tekst i — co najważniejsze — umieszczać kontrolki ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

W tym momencie dokument jest po prostu czystym płótnem — wyobraź sobie kartkę papieru czekającą na Twój przycisk polecenia.

---

## Krok 3: Wstaw kontrolkę CommandButton ActiveX

Teraz w końcu **add command button to word document**. Aspose.Words udostępnia metodę `InsertForms2OleControl`, która przyjmuje typ kontrolki oraz wymiary. Użyjemy `Forms2OleControlType.CommandButton` i nadamy jej wygodną szerokość 150 punktów oraz wysokość 30 punktów.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Metoda zwraca instancję `Forms2OleControl`, którą wykorzystamy do **set activex control properties** w następnym kroku.

---

## Krok 4: Konfiguracja kontrolki – nazwa, podpis i pozycja

### Ustawianie podpisu

Podpis to tekst wyświetlany na samym przycisku. Aby **set command button caption**, po prostu przypisz ciąg znaków do właściwości `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Możesz zmienić `"Submit"` na dowolny tekst — „Save”, „Export”, „Launch” itd. — a Word wyświetli dokładnie tę treść.

### Nadawanie nazwy kontrolce

Nadanie kontrolce znaczącej nazwy ułatwia późniejsze odwołania (np. przy automatyzacji makr Worda). Ustawimy właściwość `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Pozycjonowanie na stronie

Word używa punktów (1/72 cala) do układu. Dostosuj właściwości `Left` i `Top`, aby umieścić przycisk w żądanym miejscu:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Jeśli potrzebujesz wyrównać przycisk względem akapitu, najpierw przesuń kursor buildera, a potem wstaw kontrolkę; współrzędne będą względne względem tej pozycji.

*Edge case:* Na monitorach o wysokim DPI wizualny rozmiar może nieco różnić się w Wordzie. Aby zachować fizyczny rozmiar przycisku spójny na różnych urządzeniach, możesz obliczyć punkty na podstawie docelowego DPI (zwykle 96 DPI dla Worda).

---

## Krok 5: Zapisz dokument

Po pełnej konfiguracji przycisku zapisanie pliku to jednowierszowy kod:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Wynikowy plik `CommandButton.docx` zawiera w pełni funkcjonalny przycisk ActiveX. Otwórz go w Microsoft Word, a zobaczysz przycisk „Submit” umieszczony dokładnie tam, gdzie go ustawiłeś.

### Oczekiwany rezultat

1. Dokument Word otwiera się jako pojedyncza strona.  
2. Prostokątny przycisk oznaczony **Submit** pojawia się w podanych współrzędnych.  
3. Jeśli klikniesz prawym przyciskiem myszy przycisk i wybierzesz **Properties**, zobaczysz nazwę `btnSubmit` oraz inne ustawione właściwości.

---

## Krok 6: Zaawansowane warianty i typowe pułapki

### Wstawianie innych typów ActiveX

Metoda `InsertForms2OleControl` nie ogranicza się tylko do przycisków. Możesz osadzić pola wyboru, przyciski opcji lub nawet własne obiekty ActiveX:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Ten sam wzorzec **set activex control properties** obowiązuje — po prostu zamień typ wyliczeniowy.

### Obsługa wersji Worda

Starsze wersje Worda (przed 2007) używają binarnego formatu `.doc`, który przechowuje kontrolki ActiveX inaczej. Aspose.Words automatycznie konwertuje kontrolkę przy zapisie jako `.doc`, ale niektóre właściwości (np. precyzyjne pozycjonowanie) mogą się przesunąć. Jeśli celujesz w starsze formaty, przetestuj wynik w konkretnej wersji Worda, której potrzebujesz.

### Ustawienia bezpieczeństwa

Word może wyłączać kontrolki ActiveX na maszynach z surowymi ustawieniami zabezpieczeń makr. Aby uniknąć okna dialogowego „Security Warning”, rozważ:

* Podpisanie dokumentu zaufanym certyfikatem.  
* Instrukcję dla użytkowników, aby włączyli zawartość ActiveX dla tej lokalizacji pliku.  
* Użycie alternatywy bez makr (np. zwykłych kontrolek zawartości), jeśli bezpieczeństwo jest priorytetem.

---

## Krok 7: Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który zawiera wszystkie omówione kroki. Skopiuj go do swojego `Program.cs`, w razie potrzeby dostosuj ścieżkę wyjściową i naciśnij **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Co robi ten kod:**

* Rozpoczyna od nowego dokumentu.  
* Wstawia przycisk polecenia, **sets activex control properties** i **sets command button caption**.  
* Dodaje krótki akapit wyjaśniający.  
* Zapisuje plik jako `CommandButton.docx`.

Uruchom program, otwórz wygenerowany plik i zobacz przycisk umieszczony pod tekstem wyjaśniającym.

---

## Zakończenie

Właśnie pokazaliśmy, jak **add command button to word document** przy użyciu Aspose.Words, jak **set activex control properties** oraz jak **set command button caption** — wszystko w zwięzłym, gotowym do produkcji fragmencie C#. Podejście skaluje się: zamień typ kontrolki, dostosuj wymiary lub iteruj po źródle danych, aby automatycznie osadzić dziesiątki przycisków.

Chcesz iść dalej? Spróbuj:

* Powiązania przycisku z makrem, które wywołuje eksport danych.  
* Dodania obrazów lub własnych ikon wewnątrz przycisku przy użyciu właściwości `Picture`.  
* Zbudowania pełnego formularza z wieloma kontrolkami ActiveX (pola tekstowe, listy rozwijane itp.).

Eksperymentowanie to najlepszy sposób na opanowanie automatyzacji Worda. Jeśli napotkasz problem, sprawdź obliczenia DPI oraz ustawienia zabezpieczeń Worda. Powodzenia w kodowaniu i niech Twoje dokumenty będą coraz bardziej interaktywne!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz krok‑po‑kroku wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Dodaj zawartość przy użyciu Document Builder w Aspose.Words dla .NET](/words/english/net/add-content-using-document-builder/)
- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Utwórz dokument Word z nagłówkiem i stopką przy użyciu Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}