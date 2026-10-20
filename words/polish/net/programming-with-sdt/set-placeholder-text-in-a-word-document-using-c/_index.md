---
category: general
date: 2026-10-20
description: Ustaw tekst zastępczy w dokumencie Word przy użyciu C#. Dowiedz się,
  jak szybko dodać kontrolkę i ustawić tekst zastępczy za pomocą Aspose.Words dla
  .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: pl
lastmod: 2026-10-20
og_description: Ustaw tekst zastępczy w dokumencie Word przy użyciu C#. Ten tutorial
  pokazuje, jak dodać kontrolkę, ustawić tekst zastępczy i generować pliki Word programowo.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Ustaw tekst zastępczy w dokumencie Word przy użyciu C# – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Ustaw tekst zastępczy w dokumencie Word przy użyciu C#
url: /pl/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw tekst zastępczy w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **ustawić tekst zastępczy** w pliku Microsoft Word podczas generowania go w C#, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz zwięzłe, kompleksowe rozwiązanie, które dodaje kontrolkę zawartości, definiuje jej tekst zastępczy i zapisuje dokument — wszystko przy użyciu Aspose.Words for .NET.

Wielu programistów zastanawia się, **jak dodać kontrolkę** do dokumentu Word lub **jak ustawić tekst zastępczy** bez ręcznego otwierania Worda. Ten tutorial odpowiada na te pytania i dodatkowo pokazuje czysty sposób **generowania plików Word w C#**, które są gotowe do wprowadzania danych przez użytkownika.

## Co osiągniesz

* Utwórz pusty dokument Word programowo.
* Wstaw plain‑text Structured Document Tag (SDT), który jest techniczną nazwą kontrolki zawartości.
* Przypisz znaczący tytuł i tekst zastępczy do SDT.
* Zapisz powstały plik `.docx` na dysku.

Nie są wymagane żadne dodatkowe narzędzia poza biblioteką Aspose.Words oraz środowiskiem programistycznym .NET 6 (lub nowszym).

## Wymagania wstępne

* Zainstalowany .NET 6 SDK lub nowszy.  
* Visual Studio 2022 (lub dowolne IDE obsługujące .NET).  
* Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  

> **Wskazówka:** Użyj darmowej wersji ewaluacyjnej Aspose.Words, jeśli tylko testujesz; dodaje ona znak wodny, ale w pozostałych aspektach działa tak samo jak wersja licencjonowana.

## Krok 1: Skonfiguruj projekt i zaimportuj przestrzenie nazw

Utwórz nowy projekt konsolowy i dodaj wymagane dyrektywy `using`. Dzięki nim dostępne będą podstawowe klasy Aspose.Words oraz przestrzeń nazw markup.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Dlaczego ten krok jest ważny:* Importowanie `Aspose.Words.Markup` zapewnia dostęp do `StructuredDocumentTag`, `SdtType` i `MarkupLevel` — obiektów potrzebnych do **dodania kontrolki** i **ustawienia tekstu zastępczego**.

## Krok 2: Utwórz pusty dokument i DocumentBuilder

`Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` zapewnia wygodny kursor do wstawiania elementów.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Dlaczego ten krok jest ważny:* Rozpoczęcie od czystego dokumentu zapewnia, że ustawiony tekst zastępczy pojawi się dokładnie tam, gdzie zamierzasz, bez zakłóceń ze strony istniejącej zawartości.

## Krok 3: Utwórz kontrolkę zawartości (Structured Document Tag)

Tutaj tworzymy plain‑text SDT, nadajemy mu tytuł i ustawiamy tekst zastępczy, który użytkownik zobaczy, gdy kontrolka będzie pusta.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Dlaczego ten krok jest ważny:* Właściwość `Title` pozwala później odwołać się do kontrolki (np. przy wiązaniu danych). `PlaceholderName` to dokładnie **ustawiony tekst zastępczy**, który ma się pojawić, prowadząc użytkownika końcowego.

## Krok 4: Wstaw kontrolkę w bieżącej pozycji kursora

Za pomocą `DocumentBuilder` wstaw SDT do dokumentu w miejscu, w którym aktualnie znajduje się kursor buildera.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Dlaczego ten krok jest ważny:* Wstawienie węzła łączy kontrolkę z DOM dokumentu. Jeśli potrzebujesz dodać wiele tekstów zastępczych, możesz przesunąć kursor buildera i powtórzyć ten krok.

## Krok 5: Zapisz dokument

Na koniec zapisz dokument na dysku. Zastąp `YOUR_DIRECTORY` rzeczywistą ścieżką na swoim komputerze.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Gdy otworzysz `SDT.docx` w Microsoft Word, zobaczysz szary, wbudowany pole tekstowe z napisem **Enter name here**. Kliknięcie wewnątrz pola usuwa tekst zastępczy, umożliwiając użytkownikowi wpisanie nazwy klienta.

### Oczekiwany wynik

| Lokalizacja pliku | Podgląd zawartości |
|-------------------|--------------------|
| `C:\Temp\SDT.docx` | Wbudowany tekst zastępczy **Enter name here** wewnątrz plain‑text kontrolki zawartości o tytule *CustomerName*. |

## Przypadki brzegowe i warianty

| Sytuacja | Zalecana korekta |
|----------|------------------|
| **Wiele tekstów zastępczych** | Utwórz dodatkowe obiekty `StructuredDocumentTag` z różnymi wartościami `Title` i `PlaceholderName`, a następnie wstaw każdy tam, gdzie jest potrzebny. |
| **Rich‑text tekst zastępczy** | Użyj `SdtType.RichText` zamiast `PlainText`, aby umożliwić formatowanie wewnątrz tekstu zastępczego. |
| **Kontrolka poziomu blokowego** | Zmień `MarkupLevel.Inline` na `MarkupLevel.Block`, aby kontrolka zachowywała się jak pełny akapit. |
| **Tekst zastępczy niewidoczny** | Upewnij się, że ustawienia widoku dokumentu w Wordzie nie ukrywają kontrolek zawartości (`File → Options → Advanced → Show content controls`). |
| **Zapisywanie do strumienia** | Wywołaj `doc.Save(stream, SaveFormat.Docx)`, jeśli musisz przesłać plik przez HTTP zamiast zapisywać na dysku. |

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić. Zawiera wszystkie powyższe kroki w jednej metodzie `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Uruchom program, otwórz wygenerowany plik i zobaczysz tekst zastępczy gotowy do wprowadzenia przez użytkownika.

## Często zadawane pytania

**P: Czy to działa z .NET Core?**  
O: Tak. Aspose.Words for .NET jest kompatybilny z .NET Core, .NET 5 i .NET 6+. Ten sam kod działa bez zmian.

**P: Czy mogę ustawić wartość domyślną oprócz tekstu zastępczego?**  
O: Użyj `sdt.SetText("Default value")` po utworzeniu SDT. Tekst zastępczy znika po ustawieniu wartości.

**P: Co zrobić, jeśli później trzeba odczytać wprowadzoną wartość?**  
O: Załaduj dokument, znajdź SDT po jego `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) i odczytaj `sdt.GetText()`.

## Podsumowanie

Teraz wiesz, jak **ustawić tekst zastępczy** w dokumencie Word przy użyciu C#. Tworząc plain‑text `StructuredDocumentTag`, przypisując tytuł i tekst zastępczy, wstawiając go przy pomocy `DocumentBuilder` i zapisując plik, możesz **dodać kontrolkę** i **generować pliki Word w C#** programowo.  

Od tego momentu możesz zgłębiać:

* Dodawanie kontrolek rich‑text lub list rozwijanych (`SdtType.RichText`, `SdtType.DropDownList`).  
* Wypełnianie wielu tekstów zastępczych z bazy danych.  
* Konwertowanie wygenerowanego `.docx` na PDF przy użyciu Aspose.Words.

Eksperymentuj z różnymi typami kontrolek i stylami tekstów zastępczych, aby dopasować je do potrzeb Twojej aplikacji. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, które pomogą Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}