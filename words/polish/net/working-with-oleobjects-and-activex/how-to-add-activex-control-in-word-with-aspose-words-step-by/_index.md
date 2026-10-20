---
category: general
date: 2026-08-07
description: Dowiedz się, jak dodać kontrolkę ActiveX w dokumencie Word przy użyciu
  C#. Zawiera instrukcje, jak powiązać makro z przyciskiem oraz dodać przykłady przycisków
  klikanych w Wordzie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: pl
lastmod: 2026-08-07
og_description: jak dodać kontrolkę ActiveX w dokumencie Word przy użyciu Aspose.Words.
  Postępuj zgodnie z tym przewodnikiem, aby wstawić przycisk, powiązać makro z przyciskiem
  i dodać klikalny przycisk w dokumencie Word.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: jak dodać kontrolkę ActiveX w Word – kompletny samouczek C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak dodać kontrolkę ActiveX w Wordzie przy użyciu Aspose.Words – przewodnik
  krok po kroku
url: /pl/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak dodać kontrolkę ActiveX w Wordzie przy użyciu Aspose.Words

Jeśli potrzebujesz **jak dodać kontrolkę ActiveX** w pliku Microsoft Word programowo, ten tutorial pokaże Ci dokładne kroki przy użyciu Aspose.Words for .NET. Zobaczysz, jak wstawić przycisk polecenia, ustawić jego podpis oraz **powiązać makro z przyciskiem**, aby kontrolka reagowała po kliknięciu przez użytkownika. Na końcu otrzymasz plik `.docm` z włączonym makrem, zawierający w pełni funkcjonalny przycisk.

Dodanie przycisku ActiveX jest częstym wymogiem przy tworzeniu interaktywnych szablonów, takich jak wnioski kredytowe, formularze wprowadzania pracowników czy raporty automatyczne. Ten przewodnik przechodzi przez każdy wiersz kodu, wyjaśnia **dlaczego** każdy krok ma znaczenie i opisuje typowe pułapki, które możesz napotkać.

## Prerequisites

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6 (lub .NET Core 3.1 / .NET Framework 4.8) zainstalowany.
* Ważną licencję Aspose.Words for .NET lub tymczasowy klucz ewaluacyjny.
* Visual Studio 2022 (lub dowolne IDE obsługujące C#).
* Podstawową znajomość makr Worda (VBA), jeśli planujesz napisać makro, które ma wywoływać przycisk.

> **Pro tip:** Gdy uruchamiasz przykład, zapisz wynik w folderze, do którego masz uprawnienia zapisu, w przeciwnym razie `doc.Save` zgłosi wyjątek.

## How to add ActiveX control in a Word document using Aspose.Words

Sednem rozwiązania jest krótki program w C#, który tworzy nowy dokument, wstawia kontrolkę ActiveX **CommandButton** i zapisuje plik jako dokument z włączonym makrem (`.docm`). Kod jest kompletny i gotowy do skopiowania‑wklejenia.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Why each line matters

| Line | Purpose |
|------|---------|
| `Document doc = new Document();` | Tworzy nowy pakiet Word w pamięci. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Udostępnia płynne API do wstawiania treści, w tym kontrolek ActiveX. |
| `InsertForms2OleControl` | Jedyna metoda Aspose.Words tworząca kontrolkę ActiveX; określasz typ kontrolki (`CommandButton`) oraz jej geometrię. |
| `commandButton.Caption = "Click Me";` | Ustawia **add clickable button word**, które widzi użytkownik końcowy. Bez podpisu przycisk jest pusty. |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – informuje Word, które makro VBA uruchomić po kliknięciu kontrolki. |
| `doc.Save("CommandButton.docm");` | Zapisuje dokument jako plik z włączonym makrem; zwykły `.docx` usunąłby kontrolkę i makro. |

> **Note:** Współrzędne (lewy, górny) podawane są w punktach (1 pt ≈ 1/72 in). Dostosuj je, aby umieścić przycisk w żądanym miejscu na stronie.

## How to associate macro with button

Właściwość `OnAction` łączy przycisk z makrem VBA o nazwie `MyMacro`. Musisz nadal utworzyć to makro wewnątrz pliku Word, ręcznie lub wstrzykując kod VBA programowo (Aspose.Words nie zapisuje kodu VBA). Oto minimalne makro, które możesz dodać przy użyciu edytora **Developer → Visual Basic** w Wordzie:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Gdy użytkownik otworzy `CommandButton.docm` i kliknie przycisk, Word wykona `MyMacro` i wyświetli okno komunikatu. Jeśli zabezpieczenia makr są ustawione na **Disable all macros without notification**, przycisk będzie wyłączony. Doradź użytkownikom, aby włączyli makra dla dokumentu lub podpisali makro zaufanym certyfikatem.

### Common pitfalls when associating a macro

* **Macro security settings** – Jeśli dokument zostanie otwarty na komputerze z restrykcyjnymi zasadami bezpieczeństwa, makro może zostać zablokowane. Podaj instrukcje, jak obniżyć poziom zabezpieczeń lub podpisać makro.
* **Naming conflicts** – Nazwa makra musi być unikalna w projekcie VBA dokumentu; w przeciwnym razie Word zgłosi błąd „duplicate procedure name”.
* **64‑bit vs 32‑bit Word** – Kontrolki ActiveX działają tak samo, ale edytor VBA może wyświetlać różne komunikaty ostrzegawcze w zależności od wersji Office.

## How to add clickable button word to a Word form

Właściwość `Caption` to tekst widoczny na przycisku. Możesz go dalej dostosować:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Jeśli potrzebujesz, aby podpis zmieniał się dynamicznie w zależności od danych wprowadzonych przez użytkownika, możesz później odwołać się do kontrolki poprzez model obiektowy Worda:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Edge case: Long captions

Word przycina podpisy, które przekraczają szerokość przycisku. Aby uniknąć obcięcia, zwiększ argument szerokości w `InsertForms2OleControl` lub skróć tekst. Warto przetestować różne języki (np. niemiecki lub japoński), ponieważ szerokość znaków się różni.

## How to add command button word for form automation

Poza wizualnym podpisem, pojęcie **add command button word** obejmuje programową nazwę kontrolki. Aspose.Words nie udostępnia bezpośredniej właściwości `Name` dla kontrolek ActiveX, ale możesz ustawić pole `AltText`, które Word traktuje jako identyfikator kontrolki:

```csharp
commandButton.AltText = "SubmitButton";
```

Później w VBA możesz odwołać się do przycisku po jego wartości `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Technika ta jest przydatna, gdy masz wiele przycisków i musisz je odróżnić programowo.

## Full working example

Poniżej znajduje się kompletny program, który możesz skompilować i uruchomić jako aplikację konsolową. Zawiera opcjonalne formatowanie, powiązanie makra oraz blok komentarzy opisujący każdy krok.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** Otwierając `SubmitForm.docm` w Microsoft Word zobaczysz niebiesko‑obramowany przycisk oznaczony *Submit Form*. Kliknięcie przycisku wywoła makro VBA `SubmitMacro` (o ile dodałeś je do dokumentu). Przycisk można przesuwać, zmieniać jego rozmiar lub stylizować dalej przy użyciu tego samego obiektu `Forms2OleControl`.

## Testing the solution

1. Zbuduj i uruchom aplikację konsolową w C#.
2. Otwórz wygenerowany plik `SubmitForm.docm` w Wordzie.
3. Jeśli pojawi się monit, włącz makra.
4. Kliknij przycisk *Submit Form* – powinno wyświetlić się okno komunikatu zdefiniowane w `SubmitMacro`.

Jeśli przycisk pojawi się, ale nie zadziała, sprawdź dokładnie, czy nazwa makra jest identyczna (`SubmitMacro`) oraz czy zabezpieczenia makr nie blokują jego wykonania.

## Frequently asked questions

| Question | Answer |
|----------|--------|
| *Can I add more than one ActiveX button?* | Yes. Call `InsertForms2OleControl` multiple times with different coordinates. Use distinct `OnAction` and `AltText` values to differentiate them. |
| *Is the ActiveX control visible in Word Online?* | No. |

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add a New Section to Word Document | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}