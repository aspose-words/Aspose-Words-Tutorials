---
category: general
date: 2026-08-20
description: Dowiedz się, jak stworzyć kontrolkę ActiveX, ustawić rozmiar przycisku
  i dodać przycisk do Worda przy użyciu pełnego przykładu w C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: pl
lastmod: 2026-08-20
og_description: Utwórz kontrolkę ActiveX w pliku Word przy użyciu C#. Ten poradnik
  pokazuje, jak ustawić rozmiar przycisku, dodać przycisk do Worda i uczynić go klikalnym.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Utwórz kontrolkę ActiveX w Word – krok po kroku przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Jak utworzyć kontrolkę ActiveX w dokumencie Word przy użyciu C#
url: /pl/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć kontrolkę ActiveX w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **create ActiveX control** wewnątrz pliku Microsoft Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak **add button to Word**, ustawić wymiary przycisku i sprawić, że kontrolka będzie klikalna — wszystko przy użyciu krótkiego, samodzielnego programu w C#.

W tym samouczku:

* Zrozumiesz, dlaczego kontrolka ActiveX jest przydatna w interaktywnych dokumentach Word.  
* Poznasz dokładny kod potrzebny do **set button size** i nadania podpisu.  
* Zobaczysz, jak **create clickable button**, który później można podłączyć do makra lub zewnętrznej logiki.  

Kroki działają z Aspose.Words .NET 23.12 lub nowszym i wymagają jedynie środowiska programistycznego .NET.

> **Prerequisite** – Masz ważną licencję Aspose.Words (lub używasz wersji ewaluacyjnej) oraz Visual Studio 2022 lub dowolne IDE C#.

---

## Jak utworzyć kontrolkę ActiveX w dokumencie Word

Pierwszym krokiem jest utworzenie pustego `Document` oraz `DocumentBuilder`. Builder zapewnia wysokopoziomowe API do wstawiania obiektów, takich jak kontrolki ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Metoda `InsertActiveXButton` (zdefiniowana poniżej) zawiera logikę **how to insert button** i jej konfigurację.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Uruchomienie programu tworzy **ActiveXButton.docx**. Otwarcie pliku w Wordzie wyświetla przycisk oznaczony **Submit**. Kontrolka jest w pełni funkcjonalna — kliknięcie wywoła standardowe zdarzenie `CommandButton_Click`, które możesz później powiązać z makrem VBA.

### Dlaczego to działa

* `InsertForms2OleControl` instruuje Word, aby osadził obiekt OLE typu **CommandButton**, czyli klasyczną kontrolkę ActiveX.  
* Argumenty szerokości i wysokości bezpośrednio **set button size**; Word przelicza wartości z punktów (1 pt ≈ 1/72 in).  
* Nadanie kontrolce nazwy (`Name = "btnSubmit"`) ułatwia jej odnalezienie z VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Ustaw rozmiar przycisku i etykietę

Jeśli potrzebujesz innego wyglądu, dostosuj numeryczne argumenty w wywołaniu `InsertForms2OleControl`. Sygnatura metody wygląda tak:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Identyfikator programowy klasy ActiveX (`"CommandButton"` dla standardowego przycisku).  
* **width / height** – Rozmiar w punktach. Dla przycisku o szerokości 2 cm użyj `width = 56.7` (2 cm ≈ 56.7 pt).  

Możesz także zmodyfikować etykietę po wstawieniu:

```csharp
commandButton.Caption = "Send Request";
```

Zmiana etykiety nie wpływa na rozmiar, ale zmienia wizualny przekaz dla użytkownika.

### Porada

Jeśli chcesz przycisk kwadratowy, ustaw oba wymiary na tę samą wartość:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Dodaj przycisk do Word i spraw, aby był klikalny

Powyższy kod już **add button to Word**. Aby przycisk wykonywał akcję, musisz napisać makro VBA obsługujące zdarzenie `Click`. Oto minimalne makro, które możesz wkleić do edytora VBA w Wordzie (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Ponieważ kontrolka nosi nazwę `btnSubmit`, Word automatycznie mapuje zdarzenie `Click` na `btnSubmit_Click`. To standardowy sposób na **create clickable button** bez użycia zewnętrznych bibliotek.

> **Note:** Ustawienia bezpieczeństwa makr w Wordzie mogą blokować kontrolki ActiveX. Upewnij się, że wybrano „Enable all macros” lub „Enable VBA macros” dla dokumentu, albo cyfrowo podpisz makro do użytku produkcyjnego.

---

## Częste pytania: jak wstawić przycisk i rozwiązywanie problemów

### 1. Co zrobić, gdy przycisk nie pojawia się po zapisaniu?

* Zweryfikuj, czy wersja Aspose.Words obsługuje `InsertForms2OleControl`. Wersje wcześniejsze niż 22.5 nie posiadają tej funkcji.  
* Upewnij się, że docelowy format pliku to `.docx` lub `.doc`. Starsze formaty, takie jak `.rtf`, nie mogą przechowywać obiektów ActiveX.

### 2. Czy mogę wstawić przycisk w określonym zakładce?

Tak. Przenieś builder do zakładki przed wywołaniem `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Jak **set button size** dynamicznie w zależności od długości tekstu?

Oblicz wymaganą szerokość przy użyciu metody `Graphics.MeasureString` (z `System.Drawing`) i przelicz piksele na punkty (`points = pixels * 72 / DPI`). Następnie przekaż obliczoną szerokość do `InsertForms2OleControl`.

### 4. Czy istnieje sposób na dodanie wielu przycisków w pętli?

Oczywiście. Umieść logikę wstawiania w pętli `for` i dostosuj właściwości `Left` oraz `Top` dla każdej iteracji:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Oczekiwany wynik

Po uruchomieniu programu i otwarciu **ActiveXButton.docx**:

* Pojawia się pojedynczy przycisk **Submit** w pobliżu lewego górnego rogu pierwszej strony.  
* Rozmiar przycisku odpowiada podanym wymiarom (`100 pt × 30 pt`).  
* Jeśli dodałeś makro VBA, kliknięcie przycisku wyświetla okno komunikatu: „You clicked the Submit button!”.

Udało Ci się teraz pomyślnie **create ActiveX control**, **set button size** i **add button to Word**, jednocześnie ucząc się **how to insert button** oraz **create clickable button** do przyszłych zadań automatyzacji.

---

## Zakończenie

W tym samouczku nauczyłeś się, jak **create ActiveX control** wewnątrz dokumentu Word przy użyciu C#. Postępując zgodnie z krokami, możesz **set button size**, nadać kontrolce znaczącą nazwę i **add button to Word**, aby stała się **clickable button** powiązana z makrem VBA.  

Od tego momentu możesz rozważyć:

* Powiązanie przycisku z dodatkiem .NET COM zamiast VBA.  
* Użycie innych klas ActiveX, takich jak `CheckBox` lub `ComboBox`.  
* Automatyzację tworzenia pełnych formularzy z wieloma kontrolkami.

Śmiało eksperymentuj z różnymi rozmiarami


## Co powinieneś nauczyć się dalej?

Poniższe samouczki dotyczą ściśle powiązanych tematów, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word z obrazem pływającym w .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Utwórz dokument Word z nagłówkiem i stopką przy użyciu Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Utwórz dostępny PDF z Worda – kompletny przewodnik](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}