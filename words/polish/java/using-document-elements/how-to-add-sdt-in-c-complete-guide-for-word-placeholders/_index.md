---
category: general
date: 2026-08-14
description: Jak szybko dodać SDT przy użyciu Aspose.Words. Dowiedz się, jak utworzyć
  placeholder w Wordzie i wstawić kontrolkę zwykłego tekstu w pliku .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: pl
lastmod: 2026-08-14
og_description: Jak dodać SDT w C# przy użyciu Aspose.Words. Skorzystaj z tego samouczka,
  aby utworzyć placeholder w Wordzie i wstawić kontrolkę zwykłego tekstu dla dokumentów
  dynamicznych.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Jak dodać SDT w C# – przewodnik krok po kroku po placeholderach w Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Jak dodać SDT w C# – kompletny przewodnik po placeholderach Word
url: /pl/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać SDT w C# – kompletny przewodnik po znacznikach zastępczych Word

Jeśli potrzebujesz **how to add sdt** w pliku Word, ten tutorial pokazuje dokładne kroki przy użyciu Aspose.Words for .NET. Po zakończeniu przewodnika będziesz w stanie **create word placeholder** tagi, które pozwalają użytkownikom końcowym wpisywać bezpośrednio w dokumencie, oraz zrozumiesz, jak **insert plain text control** w sposób niezawodny.

Praca ze Structured Document Tags (SDT) eliminuje potrzebę ręcznych pól formularza i zapewnia czysty, programistyczny sposób tworzenia dynamicznych kontraktów, raportów lub listów. Poniższy przykład obejmuje wszystko od konfiguracji projektu po zapisanie końcowego pliku .docx, dzięki czemu możesz skopiować‑wkleić kod do własnego rozwiązania bez pomijania żadnych zależności.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
- Visual Studio 2022 lub dowolne IDE C#, które preferujesz
- Licencja Aspose.Words for .NET (bezpłatna licencja tymczasowa działa w testach)
- Podstawowa znajomość składni C# oraz koncepcji SDT

> **Pro tip:** Jeśli planujesz dystrybuować generowane dokumenty, osadź plik licencji, aby uniknąć znaku wodnego oceny.

## Krok 1: Skonfiguruj projekt i zaimportuj Aspose.Words

Utwórz nową aplikację konsolową i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Te dyrektywy `using` dają dostęp do klas `Document`, `DocumentBuilder` i `StructuredDocumentTag`, które są wymagane do operacji **insert plain text control**.

## Krok 2: Zainicjalizuj dokument i builder

Pierwszy blok kodu tworzy pusty dokument Word oraz `DocumentBuilder`, który pozwala na zapisywanie treści w nim.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` działa jak kursor; każde kolejne wywołanie dodaje treść w bieżącej pozycji. Inicjalizacja dokumentu jest podstawą dla każdego scenariusza **how to add sdt**, ponieważ SDT musi należeć do istniejącej instancji `Document`.

## Krok 3: Wstaw Structured Document Tag (SDT) typu plain‑text

Teraz **insert plain text control**, które działa jako znacznik zastępczy, w którym użytkownik może wpisać imię, datę lub dowolną wartość.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` informuje Aspose.Words, aby utworzyć proste pole tekstowe.
- `SdtAppearanceTags.Default` nadaje znacznikowi standardowy wygląd Word (cieniowane pole po otwarciu dokumentu w Wordzie).

## Krok 4: Skonfiguruj SDT z tytułem i tekstem zastępczym

Dobrze nazwany SDT sprawia, że dokument jest samowyjaśniający się dla użytkowników końcowych. Tutaj **create word placeholder** metadane i ustawiamy podpowiedź wyświetlaną wewnątrz pola.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` jest wewnętrznym identyfikatorem, którego możesz używać później przy wyodrębnianiu lub aktualizacji wartości programowo.
- `PlaceholderName` to przyciemniona podpowiedź wyświetlana w Wordzie, informująca użytkownika, co wpisać.

## Krok 5: Dodaj otaczającą treść

Dokument rzadko składa się z jednego SDT. Zazwyczaj potrzebne są zwykłe akapity przed i po znaczniku zastępczym. Użyj metody `WriteLine` buildera, aby dodać statyczny tekst.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Wywołanie `InsertNode` umieszcza wcześniej utworzony SDT dokładnie tam, gdzie jest potrzebny, zachowując otaczający przepływ tekstu.

## Krok 6: Zapisz dokument do pliku .docx

Na koniec zapisz dokument na dysku. Ścieżka może być bezwzględna lub względna względem folderu projektu.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Otwierając `SDT.docx` w Microsoft Word pojawia się szary znacznik zastępczy z tekstem **Enter name here**. Użytkownicy mogą kliknąć pole, wpisać wartość, a dokument zachowa tę wartość po ponownym zapisaniu.

## Pełny, uruchamialny przykład

Połączenie wszystkich elementów daje samodzielny program, który możesz uruchomić od razu:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Oczekiwany wynik** po uruchomieniu programu:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Otwierając wygenerowany `SDT.docx` widać:

```
Dear [Enter name here],
After the SDT
```

Tekst w nawiasach to znacznik zastępczy **insert plain text control**, który użytkownicy mogą zamienić.

## Częste warianty i przypadki brzegowe

| Sytuacja | Jak dostosować kod |
|-----------|-----------------------|
| **Multiple placeholders** | Call `InsertStructuredDocumentTag` repeatedly and give each tag a unique `Title`. |
| **Rich‑text SDT** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Lock the placeholder** | Set `plainTextTag.LockContentControl = true;` to prevent users from deleting the field. |
| **Pre‑populate with a value** | Assign `plainTextTag.Text = "John Doe";` before saving. |
| **Conditional appearance** | Use `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` for a tick‑box control. |

Te warianty pozwalają Ci **create word placeholder** struktury, które pasują do prawie każdego scenariusza podobnego do formularza.

## Porady dotyczące rozwiązywania problemów

- **Placeholder not visible** – Upewnij się, że otwierasz plik w Microsoft Word (lub kompatybilnym podglądzie). Niektóre lekkie edytory ukrywają SDT.
- **License warning** – Jeśli widzisz znak wodny oceny, sprawdź, czy plik licencji został poprawnie załadowany (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Po wstawieniu SDT kursor buildera pozostaje *po* znaczniku. Jeśli potrzebujesz dodać tekst *wewnątrz* znacznika, użyj `builder.MoveTo(plainTextTag);` przed zapisem.

## Zakończenie

Teraz wiesz, jak **how to add sdt** do dokumentu Word przy użyciu Aspose.Words for .NET, jak **create word placeholder** tagi oraz jak **insert plain text control**, które użytkownicy mogą edytować bezpośrednio w Wordzie. Pełny przykład demonstruje inicjalizację, wstawianie tagów, konfigurację, otaczającą treść i zapisywanie — wszystko w jednym, uruchamialnym programie.

Następnie, zapoznaj się z powiązanymi tematami, takimi jak **insert rich text control**, **populate SDTs from a database**, lub **convert the final document to PDF**. Wszystkie te zagadnienia opierają się na tych samych podstawach przedstawionych tutaj, więc możesz z pewnością rozbudowywać swoją automatyzację dokumentów.

Miłego kodowania i zachęcamy do eksperymentowania z różnymi typami SDT, aby dopasować je do potrzeb automatyzacji dokumentów!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularza i dodawać zawartość przy użyciu DocumentBuilder w Aspose.Words dla Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak tworzyć edytowalne zakresy w dokumentach tylko do odczytu przy użyciu Aspose.Words dla Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Dodawanie zakładek w Wordzie przy użyciu Aspose.Words dla Java – wstawianie, aktualizacja, usuwanie](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}