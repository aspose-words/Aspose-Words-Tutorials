---
category: general
date: 2026-10-07
description: Dowiedz się, jak wstawić przycisk polecenia OLE w dokumencie Word przy
  użyciu Aspose.Words C#. Przewodnik krok po kroku obejmujący DocumentBuilder, właściwości
  i zapisywanie pliku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: pl
lastmod: 2026-10-07
og_description: Wstaw przycisk OLE CommandButton w dokumencie Word przy użyciu C#.
  Postępuj zgodnie z tym zwięzłym samouczkiem, aby dodać, skonfigurować i zapisać
  działający przycisk CommandButton przy użyciu Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Wstaw przycisk polecenia OLE w Wordzie przy użyciu C# – kompletny przewodnik
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Jak wstawić przycisk polecenia OLE w dokumencie Word przy użyciu C#
url: /pl/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić przycisk OLE command button w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **wstawić przycisk OLE command button** do pliku Word programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words for .NET. Niezależnie od tego, czy tworzysz raport wypełniony formularzem, czy automatyzujesz szablon wymagający interakcji użytkownika, poniższe kroki dostarczą Ci kompletną, gotową do uruchomienia rozwiązanie.

Nauczysz się, jak utworzyć pusty dokument, użyć `DocumentBuilder` do umieszczenia `Forms2OleControl`, ustawić podpis i nazwę przycisku oraz ostatecznie zapisać plik `.docx`. Nie są wymagane żadne zewnętrzne narzędzia poza biblioteką Aspose.Words.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7+)
* Ważna licencja Aspose.Words for .NET lub darmowy klucz ewaluacyjny
* Visual Studio 2022 (lub dowolne IDE C#, które preferujesz)
* Podstawowa znajomość składni C# i koncepcji Word OLE

> **Wskazówka:** Jeśli używasz darmowej wersji ewaluacyjnej, wygenerowany dokument będzie zawierał małą znak wodny. Wersja licencjonowana usuwa go automatycznie.

## Krok 1: Zainstaluj Aspose.Words

Dodaj pakiet Aspose.Words do swojego projektu za pomocą NuGet:

```bash
dotnet add package Aspose.Words
```

Pakiet zawiera przestrzenie nazw `Aspose.Words.Drawing` i `Aspose.Words.Drawing.Ole` niezbędne do obsługi kontrolek OLE.

## Krok 2: Wstaw przycisk OLE command button przy użyciu DocumentBuilder

Główną częścią tutorialu jest metoda `InsertForms2OleControl`. Tworzy ona **Forms2 OLE CommandButton** w określonym miejscu i rozmiarze.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Dlaczego to działa

* `DocumentBuilder` jest podstawowym API do programowego tworzenia dokumentów Word.  
* `InsertForms2OleControl` instruuje Aspose.Words, aby osadził **Forms2 OLE control**, czyli starszą technologię formularzy Word, która obsługuje przyciski command, pola wyboru itp.  
* Wartość wyliczenia `OleControlType.CommandButton` określa, że wstawiona kontrola jest **przyciskiem command** — dokładny typ, którego potrzebujesz, gdy chcesz **wstawić przycisk OLE command button**.  
* `Rectangle` określa położenie wizualne. Dostosuj współrzędne X/Y lub szerokość/wysokość, aby pasowały do Twojego układu.

## Krok 3: Zapisz dokument

Po skonfigurowaniu przycisku zapisz dokument na dysku. Możesz wybrać dowolny format obsługiwany przez Aspose.Words (`.docx`, `.pdf`, `.odt`, …). W tym tutorialu zapiszemy go jako dokument Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Gdy otworzysz `CommandButton.docx` w Microsoft Word, zobaczysz klikalny przycisk oznaczony **Click Me**. Naciśnięcie go w Wordzie wywołuje domyślne okno dialogowe „Run Macro”, ponieważ przycisk jest kontrolką formularza OLE; później możesz dołączyć makro lub kod VBA, jeśli zajdzie taka potrzeba.

## Krok 4: Zweryfikuj wynik (oczekiwany rezultat)

Otwórz wygenerowany plik:

1. Przycisk pojawia się w podanych przez Ciebie współrzędnych (około 1,4  cala od lewej i górnej krawędzi strony).  
2. Etykieta brzmi **Click Me**.  
3. Właściwość nazwy (`cmdSubmit`) jest widoczna w panelu **Developer → Properties** w Wordzie, co jest przydatne, gdy musisz odwołać się do kontrolki z VBA.

![Wstaw przykład przycisku OLE command button w dokumencie Word](insert-ole-button.png)

*Tekst alternatywny obrazu*: **Wstaw przykład przycisku OLE command button w dokumencie Word** (zawiera główne słowo kluczowe dla dostępności i SEO).

## Przypadki brzegowe i często zadawane pytania

### 1. Co zrobić, gdy przycisk nie pojawia się w oczekiwanym miejscu?

* Word używa punktów, nie pikseli. Przelicz piksele ekranu na punkty (`points = pixels * 72 / DPI`).  
* Upewnij się, że prostokąt nie przecina marginesów strony; w przeciwnym razie Word może przesunąć kontrolkę.

### 2. Czy mogę wstawić przycisk do istniejącego dokumentu?

Tak. Załaduj dokument przy użyciu `new Document("Existing.docx")` i użyj tego samego przepływu pracy `DocumentBuilder`. Pamiętaj tylko, aby przenieść kursor buildera (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` itp.) przed wywołaniem `InsertForms2OleControl`.

### 3. Jak dołączyć makro do przycisku?

Aspose.Words nie tworzy kodu VBA, ale możesz osadzić makro po wygenerowaniu dokumentu:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Czy to działa z .NET Core na Linuksie?

Kontrolka OLE jest funkcją specyficzną dla systemu Windows, ponieważ opiera się na COM. Na Linuksie przycisk zostanie wstawiony, ale będzie wyświetlany jako statyczny obraz bez interaktywnego zachowania. Dla wieloplatformowych formularzy interaktywnych rozważ użycie kontrolek treści (`StructuredDocumentTag`) zamiast tego.

### 5. Co zrobić, gdy potrzebuję innego rozmiaru lub wielu przycisków?

Utwórz dodatkowe obiekty `Rectangle` z unikalnymi współrzędnymi i powtórz wywołanie `InsertForms2OleControl`. Każdy przycisk może mieć własny `Caption` i `Name`.

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystkie niezbędne dyrektywy `using`, obsługę błędów i komentarze.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Uruchom program, otwórz wygenerowany `CommandButton.docx`, a zobaczysz przycisk **Click Me** gotowy do dalszej personalizacji.

## Zakończenie

Teraz wiesz, jak **wstawić przycisk OLE command button** do dokumentu Word przy użyciu C# i Aspose.Words. Tutorial obejmował:

* Instalację pakietu Aspose.Words  
* Użycie `DocumentBuilder.InsertForms2OleControl` z `OleControlType.CommandButton`  
* Ustawianie właściwości przycisku (`Caption`, `Name`)  
* Zapisywanie i weryfikację wyniku  

Od tego momentu możesz zgłębiać powiązane tematy, takie jak **Aspose.Words OLE control** dla pól wyboru, pól kombi lub osadzania całych arkuszy Excel. Możesz także eksperymentować z automatyzacją **Word OLE command button** w większych szablonach lub zastąpić kontrolki OLE nowoczesnymi **content controls** dla lepszej obsługi wieloplatformowej.

Śmiało dostosowuj wartości prostokąta, dodawaj wiele przycisków lub dołączaj makra VBA, aby spełnić potrzeby Twojej aplikacji. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstaw obiekt Ole w dokumencie Word](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Wstaw obiekt Ole w dokumencie Word jako ikonę](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Wstaw obiekt Ole w Wordzie przy użyciu pakietu Ole](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}