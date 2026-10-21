---
category: general
date: 2026-09-21
description: Utwórz dokument Word programowo i dowiedz się, jak dodać przycisk zapisywania
  dokumentu Word, wstawić przycisk polecenia Word oraz ustawić podpis przycisku polecenia
  przy użyciu DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: pl
lastmod: 2026-09-21
og_description: Twórz dokumenty Word programowo przy użyciu Aspose.Words. Dowiedz
  się, jak dodać przycisk zapisywania dokumentu Word, wstawić przycisk polecenia w
  Wordzie, ustawić etykietę przycisku polecenia oraz używać DocumentBuilder do interaktywnych
  formularzy.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Utwórz dokument Word programowo i dodaj przycisk
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Utwórz dokument Word programowo i wstaw przycisk
url: /pl/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word programowo i wstaw przycisk

Jeśli potrzebujesz **create word document programmatically**, Aspose.Words udostępnia płynne API, które pozwala dodawać interaktywne kontrolki, takie jak CommandButton. Ten tutorial wyjaśnia również **how to use DocumentBuilder**, jak **save word document button**, oraz jak **set command button caption**, aby przycisk wyświetlał się dokładnie tak, jak oczekujesz w pliku .docx.

Nauczysz się jak:

* Zainicjalizować pusty dokument przy użyciu `Document`.
* Pracować z `DocumentBuilder`, aby edytować dokument.
* Wstawić **CommandButton** (`insert command button word`).
* Ustawić nazwę przycisku i widoczny podpis (`set command button caption`).
* Zachować wynik na dysku (`save word document button`).

Kroki są napisane dla programistów .NET używających C# oraz najnowszej wersji Aspose.Words for .NET (v24.10). Nie są wymagane dodatkowe pakiety NuGet poza Aspose.Words.

---

## Co potrzebujesz przed rozpoczęciem

| Wymaganie | Powód |
|--------------|--------|
| Visual Studio 2022 (lub dowolne IDE C#) | Aby skompilować i uruchomić przykładowy kod. |
| .NET 6.0 SDK lub nowszy | Zapewnia środowisko uruchomieniowe dla przykładu. |
| Aspose.Words for .NET (v24.10 lub nowszy) | Biblioteka, która pozwala **create word document programmatically** i manipulować kontrolkami formularzy. |
| Podstawowa znajomość C# i koncepcji OOP | Wymagana do zrozumienia przepływu kodu. |

Możesz zainstalować Aspose.Words za pomocą NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Utwórz dokument Word programowo

Pierwszym krokiem jest utworzenie pustego obiektu `Document`. Ten obiekt reprezentuje cały plik Word w pamięci.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Tworzenie dokumentu programowo daje czyste płótno, na którym możesz dodawać akapity, tabele lub interaktywne kontrolki.  

---

## Jak używać DocumentBuilder

`DocumentBuilder` jest podstawową klasą do edycji `Document`. Udostępnia metody wstawiania tekstu, obrazów i pól formularza. W tym tutorialu używamy go do umieszczenia CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder utrzymuje wewnętrzny kursor wskazujący bieżącą lokalizację wstawiania. Domyślnie zaczyna się na początku pierwszej sekcji, co jest idealne dla naszego przykładu.

---

## Wstaw przycisk CommandButton w Word

Aspose.Words traktuje CommandButton jako kontrolkę ActiveX. Metoda `InsertForms2OleControl` tworzy ogólną kontrolkę OLE, którą następnie konfiguruje się jako przycisk.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

W tym momencie kontrolka istnieje w dokumencie, ale nie ma wizualnej reprezentacji, dopóki nie określimy jej typu.

---

## Ustaw podpis przycisku CommandButton

Teraz informujemy kontrolkę OLE, że powinna zachowywać się jak CommandButton i nadajemy jej przyjazną etykietę.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Ustawienie **command button caption** jest kluczowe, ponieważ Word wyświetla ten tekst na powierzchni przycisku. Jeśli pominiesz `SetCaption`, przycisk pojawi się z ogólną etykietą.

---

## Zapisz dokument Word z przyciskiem

Na koniec zapisz dokument na dysku. Metoda `Save` zapisuje cały pakiet Word, w tym nowo wstawiony przycisk, do pliku .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Plik `CommandButton.docx` zawiera teraz w pełni funkcjonalny przycisk oznaczony **Submit**. Gdy użytkownik otworzy plik w Microsoft Word i kliknie przycisk, zostanie wywołana domyślna akcja ( którą możesz później powiązać za pomocą VBA).

---

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić. Demonstruje cały przepływ pracy od tworzenia dokumentu po zapisanie przycisku.

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

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Oczekiwany wynik**

* Plik o nazwie `CommandButton.docx` znajdujący się w podanej ścieżce.
* Otwarcie pliku w Microsoft Word wyświetla pojedynczy przycisk **Submit** na pierwszej stronie.
* Przycisk można zaznaczyć, zmienić jego rozmiar lub połączyć z makrem z zakładki **Developer** w Wordzie.

---

## Częste pytania i obsługa przypadków brzegowych

| Pytanie | Odpowiedź |
|----------|--------|
| *Co zrobić, jeśli potrzebuję więcej niż jednego przycisku?* | Powtórz kroki 3–6 z różnymi nazwami i podpisami. Każdy przycisk musi mieć unikalną wartość `SetName`. |
| *Czy mogę ustawić rozmiar przycisku?* | Tak. Po wstawieniu kontrolki możesz zmodyfikować jej właściwości `Width` i `Height` za pomocą obiektu `OleFormat`. |
| *Czy przycisk będzie działał we wszystkich wersjach Worda?* | Kontrolki ActiveX są obsługiwane w wersji desktopowej Worda (Windows). Nie są renderowane w Word Online ani na macOS. |
| *Jak dodać obsługę kliknięcia?* | Musisz napisać kod VBA, który odwołuje się do nazwy przycisku (`btnSubmit`). Makro VBA można osadzić używając `doc.VbaProject`. |
| *Co zrobić, jeśli trzeba wstawić przycisk wewnątrz komórki tabeli?* | Przesuń kursor buildera do żądanej komórki (`builder.MoveTo(cell.FirstParagraph)`) przed wywołaniem `InsertForms2OleControl`. |

---

## Porady profesjonalne

* **Pro tip:** Zawsze ustaw znaczącą nazwę przy użyciu `SetName`. Ułatwia to automatyzację VBA i upraszcza debugowanie.
* **Watch out for:** Zapomnienie wywołania `SetControlType`. Bez tego wywołania obiekt OLE pojawia się jako ogólny placeholder zamiast klikalnego przycisku.
* **Performance tip:** Jeśli generujesz wiele dokumentów w pętli, ponownie używaj jednej instancji `DocumentBuilder` i wywołuj `builder.MoveToDocumentEnd()` przed każdym wstawieniem, aby uniknąć niepotrzebnych resetów kursora.

---

## Kolejne kroki

Teraz, gdy wiesz jak **create word document programmatically**, **insert command button word**, **set command button caption** i **save word document button**, możesz eksplorować bardziej zaawansowane scenariusze:

* Dodaj kontrolki **TextFormField** dla wprowadzania danych przez użytkownika.
* Połącz przyciski z polami **MacroButton**, aby bezpośrednio wykonywać VBA.
* Użyj **DocumentBuilder.InsertImage**, aby umieścić ikony na przyciskach.
* Zintegruj z ASP.NET, aby generować formularze Word w

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz nowy dokument Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Utwórz dokument Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Wstaw obraz inline w dokumencie Word przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}