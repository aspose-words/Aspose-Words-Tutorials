---
category: general
date: 2026-09-30
description: Dodaj kontrolkę ActiveX do dokumentu Word przy użyciu C#. Dowiedz się,
  jak wstawić przycisk ActiveX, dodać przycisk polecenia i sprawić, aby był klikalny.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: pl
lastmod: 2026-09-30
og_description: Dodaj kontrolkę ActiveX do dokumentu Word przy użyciu C#. Postępuj
  zgodnie z tym kompletnym przewodnikiem, aby wstawić przycisk ActiveX, dodać przycisk
  polecenia i uczynić go klikalnym.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Dodaj kontrolkę ActiveX do dokumentów Word – przewodnik krok po kroku w
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Jak dodać kontrolkę ActiveX w Wordzie przy użyciu C#
url: /pl/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać słowo kontrolki ActiveX w Wordzie przy użyciu C#

Jeśli potrzebujesz osadzić **ActiveX control word** w pliku Microsoft Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz kompletny, działający przykład, który wstawia przycisk, zapisuje dokument i działa z najnowszą wersją Aspose.Words for .NET.

Dodanie słowa kontrolki ActiveX pozwala tworzyć interaktywne formularze, własne okna dialogowe lub proste elementy UI, które zachowują się jak natywne kontrolki Worda. Niezależnie od tego, czy tworzysz szablon umowy wymagający interakcji użytkownika, czy raport potrzebujący przycisku „Run”, poniższe kroki obejmują wszystko, czego potrzebujesz.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy (kod działa również z .NET Framework 4.8)
* Visual Studio 2022 (lub dowolne IDE obsługujące C#)
* Aspose.Words for .NET zainstalowany (`dotnet add package Aspose.Words`)
* Podstawowa znajomość C# i struktury dokumentu Word

> **Wskazówka:** Metoda `InsertForms2OleControl` działa tylko z legacy kontrolkami „Forms 2.0”, które są kontrolkami ActiveX używanymi przez Word do pól formularzy. Jeśli celujesz w nowsze wersje Office, kontrolka nadal jest poprawnie renderowana w kliencie desktopowym.

## Krok 1: Skonfiguruj projekt i zaimportuj przestrzenie nazw

Utwórz nowy projekt konsolowy i dodaj wymagane instrukcje `using`. Zapewnia to, że kompilator znajdzie klasy `Document`, `DocumentBuilder` oraz `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Przestrzeń nazw `Aspose.Words` udostępnia wysokopoziomowe API do przetwarzania Word, natomiast `Aspose.Words.Drawing` zawiera wyliczenie `OleControlType` potrzebne do określenia typu kontrolki ActiveX.

## Krok 2: Załaduj źródłowy dokument Word

Musisz rozpocząć od pliku Word, który chcesz zmodyfikować. Poniższy kod ładuje `input.docx` z określonego folderu.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Jeśli plik nie istnieje, Aspose.Words zgłasza `FileNotFoundException`. Owiń wywołanie w blok `try/catch`, jeśli potrzebujesz eleganckiego obsługi błędów.

## Krok 3: Utwórz DocumentBuilder do edycji dokumentu

`DocumentBuilder` jest głównym narzędziem do wstawiania tekstu, obrazów i kontrolek. Utrzymuje kursor wskazujący miejsce, w którym zostanie umieszczony kolejny element.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Domyślnie kursor buildera jest ustawiony na początku pierwszej sekcji. Możesz go przenieść metodami takimi jak `MoveToDocumentEnd()` lub `MoveToParagraph(index)`, jeśli chcesz umieścić przycisk w innym miejscu.

## Krok 4: Wstaw kontrolkę ActiveX CommandButton

Teraz przechodzi do sedna tutorialu: wstawianie **ActiveX control word**, które pojawia się jako przycisk do kliknięcia. Metoda `InsertForms2OleControl` przyjmuje dwa argumenty — typ kontrolki oraz podpis (lub nazwę) kontrolki.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Dlaczego używać `OleControlType.CommandButton`?**  
  Informuje Word, aby utworzył klasyczny przycisk Forms 2.0, który wyświetla podpis i może być później podłączony do makra lub skryptu VBA.

* **Co robi podpis?**  
  Ciąg znaków `"ClickMe"` staje się widocznym tekstem przycisku. Możesz go zmienić na dowolny, pasujący do Twojego interfejsu.

### Wstawianie przycisku w określonym miejscu

Jeśli potrzebujesz przycisk po określonym paragrafie, najpierw przesuń buildera:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Krok 5: Zapisz zmodyfikowany dokument

Po wstawieniu kontrolki, zapisz zmiany do nowego pliku (lub nadpisz oryginał).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Gdy otworzysz `output.docx` w wersji desktopowej Worda, zobaczysz przycisk oznaczony **ClickMe** (lub **Submit**, w zależności od użytego podpisu). Kliknięcie przycisku w trybie projektowania nie robi nic domyślnie; możesz później przypisać makro za pomocą zakładki „Developer” w Wordzie.

## Pełny, działający przykład

Poniżej znajduje się samodzielny program, który demonstruje cały przepływ pracy. Skopiuj go do `Program.cs` nowej aplikacji konsolowej i uruchom.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Oczekiwany wynik

* Konsola wyświetla komunikat o sukcesie wraz ze ścieżką wyjściową.
* Otwierając `output.docx` widzisz przycisk **ClickMe** w miejscu, w którym builder go wstawił.
* Przycisk można zaznaczyć, zmienić jego rozmiar lub przypisać makro za pomocą **Developer → Design Mode** w Wordzie.

## Często zadawane pytania i obsługa przypadków brzegowych

| Question | Answer |
|----------|--------|
| **Jak wstawić przycisk ActiveX w nagłówku/stopce?** | Przenieś buildera do nagłówka/stopki za pomocą `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` przed wywołaniem `InsertForms2OleControl`. |
| **Co zrobić, jeśli potrzebuję pola wyboru zamiast przycisku?** | Użyj `OleControlType.CheckBox` i podaj podpis, np. `"Agree"`. |
| **Czy przycisk będzie działał w Word Online?** | Nie. Word Online nie obsługuje starszych kontrolek Forms 2.0 ActiveX. Przycisk renderuje się tylko w kliencie desktopowym. |
| **Czy mogę ustawić rozmiar przycisku programowo?** | Po wstawieniu pobierz obiekt `Shape` za pomocą `builder.CurrentParagraph.Runs[0].GetShape()` i dostosuj `Width`/`Height`. |
| **Czy istnieje sposób, aby przypisać makro z kodu?** | Aspose.Words nie udostępnia edycji makr. Musisz otworzyć dokument w Wordzie i ręcznie dołączyć makro lub użyć API Office Interop. |

## Wskazówki do użycia w produkcji

* **Unikaj ścieżek zakodowanych na stałe** – używaj `Path.Combine` i plików konfiguracyjnych.
* **Zwalniaj `Document`** – owiń go w instrukcję `using`, jeśli pracujesz z dużymi plikami, aby szybko zwolnić pamięć.
* **Waliduj wynik** – programowo sprawdź, czy dokument zawiera kształt typu `OleControl`, iterując `doc.GetChildNodes(NodeType.Shape, true)`.
* **Uwaga dotycząca bezpieczeństwa** – kontrolki ActiveX mogą uruchamiać kod na maszynie klienta. Rozprowadzaj dokumenty tylko do zaufanych użytkowników i rozważ podpisy cyfrowe.

## Zakończenie

Teraz wiesz, jak dodać **ActiveX control word** do dokumentu Word przy użyciu C#. Ładując dokument, tworząc `DocumentBuilder`, wstawiając przycisk polecenia za pomocą `InsertForms2OleControl` i zapisując plik, możesz zautomatyzować tworzenie interaktywnych formularzy Word. Eksperymentuj z innymi wartościami `OleControlType`, umieszczaj kontrolki w nagłówkach lub tabelach i łącz je z makrami, aby uzyskać bogatsze doświadczenia użytkownika.

---

*Kolejne kroki*: poznaj **jak wstawiać inne typy kontrolek ActiveX**, dowiedz się **jak dodać obsługę zdarzeń przycisku** za pomocą VBA oraz przeczytaj o **najlepszych praktykach wstawiania przycisku ActiveX** pod kątem kompatybilności międzyplatformowej.

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Osadzanie obiektów OLE i kontrolek ActiveX w dokumentach Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Dodaj pole formularza Combo Box do dokumentu Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Dodaj pole formularza Check Box do dokumentu Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}