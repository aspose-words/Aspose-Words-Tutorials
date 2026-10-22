---
category: general
date: 2026-08-17
description: Wstaw przykład OleControlType.CommandButton w programie Word przy użyciu
  Aspose.Words. Dowiedz się, jak programowo dodawać kontrolki formularza do dokumentu
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: pl
lastmod: 2026-08-17
og_description: Wstaw przykład OleControlType.CommandButton w Wordzie przy użyciu
  Aspose.Words. Postępuj zgodnie z tym przewodnikiem, aby dodać kontrolki formularza
  do dokumentu Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Wstaw przykład OleControlType.CommandButton w Wordzie
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Wstaw przykład OleControlType.CommandButton w Wordzie
url: /pl/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw przykład OleControlType.CommandButton w Wordzie

Jeśli potrzebujesz **wstawić przykład OleControlType.CommandButton** do pliku Word, ten przewodnik pokaże Ci, jak to zrobić. Nauczysz się **jak dodać kontrolki formularza do dokumentu Word** przy użyciu Aspose.Words, z kompletnym, uruchamialnym programem C#.

Kontrolki formularza, takie jak przyciski ActiveX, pozwalają tworzyć interaktywne szablony Word — przydatne w umowach, ankietach czy narzędziach wewnętrznych. Poniższe kroki obejmują wszystko, od konfiguracji projektu po weryfikację, że przycisk pojawia się poprawnie w zapisanym pliku `.docx`.

## Wymagania wstępne

- .NET 6.0 SDK lub nowszy zainstalowany  
- Visual Studio 2022 (lub dowolne IDE C#)  
- Licencja Aspose.Words for .NET lub darmowa licencja tymczasowa  
- Podstawowa znajomość C# i koncepcji plików Word  

> **Wskazówka:** Jeśli korzystasz z wersji próbnej, umieść plik licencji w tym samym folderze co plik wykonywalny i wczytaj go na początku `Main`.

## Krok 1: Utwórz nowy projekt konsolowy i dodaj Aspose.Words

Otwórz terminal i uruchom:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Tworzy to czysty projekt i pobiera najnowszy pakiet Aspose.Words, który udostępnia API `Document`, `DocumentBuilder` oraz `InsertForms2OleControl` potrzebne do **przykładu wstawienia OleControlType.CommandButton**.

## Krok 2: Napisz pełny program

Utwórz lub zamień plik `Program.cs` następującym kodem. Zawiera on wszystkie wymagane dyrektywy `using`, wczytywanie licencji oraz czterostopniowy przepływ pracy przedstawiony w oryginalnym fragmencie.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Dlaczego każda linia ma znaczenie

* **Ładowanie licencji** – zapewnia, że nie jesteś ograniczony przez ograniczenia wersji ewaluacyjnej.  
* **`Document doc = new Document();`** – tworzy kontener dla całej zawartości Word; jest to podstawa **przykładu wstawienia OleControlType.CommandButton**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – udostępnia płynne API do dodawania tekstu, obrazów i kontrolek.  
* **`InsertForms2OleControl`** – podstawowa metoda implementująca **jak dodać kontrolki formularza do dokumentu Word**. Wartość wyliczenia `OleControlType.CommandButton` informuje Aspose.Words, aby utworzyć przycisk ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – pozycjonuje przycisk 100 pt od lewego i górnego marginesu, o szerokości 80 pt i wysokości 30 pt. Dostosuj te wartości do swojego układu.  
* **`doc.Save`** – zapisuje plik .docx na dysku; plik teraz zawiera osadzony przycisk.

## Krok 3: Zbuduj i uruchom program

Z folderu projektu wykonaj:

```bash
dotnet run
```

Powinieneś zobaczyć komunikat w konsoli:

```
Document saved to ActiveXButton.docx
```

Otwórz `ActiveXButton.docx` w programie Microsoft Word. Zobaczysz przycisk oznaczony **ClickMe**, umieszczony mniej więcej w środku strony. Kliknięcie przycisku wywołuje domyślne zachowanie ActiveX (zwykle nic nie robi, chyba że podłączysz makro).

![przykład insert olecontroltype.commandbutton](/images/activex-button.png "ActiveX CommandButton wstawiony do dokumentu Word")

*Tekst alternatywny obrazu:* insert olecontroltype.commandbutton example – ActiveX CommandButton wyświetlony w dokumencie Word.

## Krok 4: Dostosowywanie przycisku (opcjonalnie)

Podstawowy **przykład insert OleControlType.CommandButton** tworzy domyślny przycisk. Możesz zmienić jego etykietę, czcionkę lub nawet dołączyć makro, edytując podstawowy obiekt OLE. Poniżej znajduje się zwięzły sposób na zmianę etykiety przycisku po wstawieniu:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Uwaga:** Bezpośrednia manipulacja właściwościami OLE wymaga zrozumienia podstawowego interfejsu COM. W większości przypadków domyślna etykieta jest wystarczająca.

## Krok 5: Częste problemy i jak ich uniknąć

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Przycisk nie pojawia się w Wordzie | Dokument został zapisany jako `.docx`, ale otworzono go w przeglądarce, która usuwa kontrolki OLE (np. Google Docs). | Otwórz plik w Microsoft Word lub Word Online z uprawnieniami do edycji. |
| Błąd wykonania `ArgumentOutOfRangeException` | Współrzędne `Rectangle` znajdują się poza marginesami strony. | Użyj wartości mieszczących się w rozmiarze strony (np. 0‑500 dla A4). |
| Wyjątek licencyjny | Licencja próbna wygasa po 30 dniach. | Wczytaj ważny plik licencji lub poproś o przedłużony okres próbny w Aspose. |

## Krok 6: Jak ten przykład pasuje do większych projektów automatyzacji

Gdy potrzebujesz **jak dodać kontrolki formularza do dokumentu Word** na dużą skalę — np. generując setki szablonów umów — opakuj logikę wstawiania w metodę wielokrotnego użytku:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Możesz wtedy wywołać `AddCommandButton` wewnątrz pętli przetwarzających wiersze danych, zapewniając, że każdy wygenerowany dokument zawiera przycisk o unikalnej nazwie (np. `Approve_001`, `Approve_002`).

## Zakończenie

Masz teraz kompletny **przykład insert OleControlType.CommandButton**, który demonstruje **jak dodać kontrolki formularza do dokumentu Word** przy użyciu Aspose.Words dla .NET. Samouczek obejmował konfigurację projektu, pełny kod źródłowy, wskazówki dotyczące dostosowywania oraz typowe kroki rozwiązywania problemów.

Od tego miejsca możesz zbadać:

- Dodawanie innych typów kontrolek, takich jak **CheckBox** lub **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Powiązanie przycisku z makrem VBA w celu uzyskania większej interaktywności.  
- Generowanie plików PDF z tego samego dokumentu przy zachowaniu pól formularza.

Eksperymentuj z różnymi rozmiarami, pozycjami i nazwami kontrolek, aby dopasować je do swojego konkretnego przypadku użycia. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i zbadać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstaw pole formularza Combo Box w dokumencie Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Wstaw pole formularza Check Box w dokumencie Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Wstaw pole formularza Text Input w dokumencie Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}