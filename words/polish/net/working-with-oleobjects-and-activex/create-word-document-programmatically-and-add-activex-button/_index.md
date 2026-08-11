---
category: general
date: 2026-08-10
description: Utwórz dokument Word programowo przy użyciu Aspose.Words, a następnie
  dodaj przycisk kontrolki ActiveX. Wstaw przycisk polecenia ActiveX w kilka minut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: pl
lastmod: 2026-08-10
og_description: Utwórz dokument Word programowo przy użyciu Aspose.Words, a następnie
  dodaj przycisk kontrolki ActiveX. Dowiedz się, jak szybko wstawić przycisk polecenia
  ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Tworzenie dokumentu Word programowo – dodaj przycisk ActiveX w C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Utwórz dokument Word programowo i dodaj przycisk ActiveX
url: /pl/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word programowo i dodaj przycisk ActiveX

Jeśli potrzebujesz **utworzyć dokument Word programowo**, ten przewodnik przeprowadzi Cię przez cały proces z Aspose.Words for .NET. Dowiesz się także, jak **dodać elementy kontrolki ActiveX w Word** oraz **wstawić obiekty przycisku polecenia ActiveX** w jednym, samodzielnym przykładzie.

Generowanie plików Word z kodu eliminuje ręczny krok otwierania Microsoft Word, pozwalając automatycznie tworzyć raporty, faktury lub kontrakty oparte na danych. Po zakończeniu tego samouczka będziesz mieć gotową do uruchomienia aplikację konsolową C#, która generuje plik `.docx` zawierający interaktywny przycisk ActiveX CommandButton.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy (kod działa również z .NET Framework 4.6+)
* Visual Studio 2022 lub dowolne IDE obsługujące rozwój .NET
* Ważna licencja Aspose.Words for .NET (możesz użyć darmowego klucza ewaluacyjnego do testów)
* Podstawowa znajomość składni C# oraz koncepcji kontrolerów COM/ActiveX

> **Wskazówka:** Jeśli planujesz dystrybuować wygenerowany dokument do użytkowników, którzy nie mają zainstalowanego Worda, osadź pliki uruchomieniowe kontrolki ActiveX obok pliku `.docx` lub udostępnij szablon z włączonymi makrami.

## Utwórz dokument Word programowo – wstępna konfiguracja

Najpierw dodaj pakiet NuGet Aspose.Words do swojego projektu:

```bash
dotnet add package Aspose.Words
```

Następnie utwórz nowy projekt konsolowy (jeśli jeszcze go nie masz):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Otwórz wygenerowany plik `Program.cs` – zamienimy jego zawartość na pełne rozwiązanie poniżej.

## Krok 1: Importuj przestrzenie nazw i skonfiguruj licencję

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Dlaczego to ważne*: Importowanie `Aspose.Words.Drawing` daje dostęp do `Forms2OleControl`, klasy reprezentującej kontrolkę ActiveX w dokumencie Word. Ustawienie licencji na wczesnym etapie zapobiega ostrzeżeniom w czasie wykonywania w środowisku produkcyjnym.

## Krok 2: Utwórz pusty dokument i DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Obiekt `Document` jest reprezentacją w pamięci pliku `.docx`. `DocumentBuilder` działa jak kursor, którym poruszasz się po dokumencie, aby wstawiać elementy.

## Krok 3: Wstaw kontrolkę ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` tworzy obiekt OLE, który Word traktuje jako kontrolkę ActiveX. System współrzędnych używa punktów (1 punkt = 1/72 cala), co odpowiada silnikowi układu Worda.

## Krok 4: Ustaw podpis przycisku i opcjonalne właściwości

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Ustawienie właściwości `Caption` jest najczęstszym sposobem nadania etykiety przyciskowi. Jeśli potrzebujesz, aby przycisk uruchamiał makro VBA, przypisz nazwę makra do `OnAction`. Ten samouczek koncentruje się na części wizualnej; integracja makr jest omówiona w sekcji „Kolejne kroki”.

## Krok 5: Zapisz dokument

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Po uruchomieniu programu zobaczysz komunikat w konsoli potwierdzający, że `ActiveX_CommandButton.docx` został zapisany na dysku.

### Pełny kod źródłowy (gotowy do kopiowania i wklejenia)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Uruchomienie fragmentu kodu generuje plik Word zawierający klikalny **przycisk polecenia ActiveX**. Otwórz plik w Microsoft Word, przełącz się na **Tryb Projektowania** (zakładka Developer → Tryb Projektowania) i zobaczysz przycisk wyświetlony dokładnie w miejscu, w którym go umieściłeś.

## Krok 6: Zweryfikuj wynik

1. Otwórz `ActiveX_CommandButton.docx` w Microsoft Word.
2. Włącz zakładkę **Developer**, jeśli nie jest widoczna (`Plik → Opcje → Dostosuj wstążkę → zaznacz Developer`).
3. Kliknij **Tryb Projektowania**. Przycisk powinien pojawić się z etykietą „Submit”.
4. Jeśli dodałeś makro `OnAction`, kliknij przycisk przy wyłączonym Trybie Projektowania, aby uruchomić makro.

Jeśli przycisk się nie wyświetla, upewnij się, że ustawienia zabezpieczeń Worda zezwalają na kontrolki ActiveX (`Plik → Opcje → Centrum zaufania → Ustawienia Centrum zaufania → Ustawienia ActiveX`).

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|-----------|
| **Czy mogę wstawić inne typy ActiveX?** | Tak. Enum `Forms2OleControlType` zawiera `CheckBox`, `OptionButton`, `ComboBox` itd. Zastąp `CommandButton` żądaną wartością enumu |

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz kształt grupowy w dokumencie Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Utwórz dokument Word z nagłówkiem i stopką przy użyciu Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Wstaw obraz w linii w dokumencie Word przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}