---
category: general
date: 2026-09-08
description: Dowiedz się, jak wstawić kontrolkę treści w dokumencie Word przy użyciu
  C# i Aspose.Words. Zawiera kroki tworzenia kontrolki treści, ustawiania symbolu
  zastępczego i zapisywania pliku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: pl
lastmod: 2026-09-08
og_description: Wstaw kontrolkę zawartości w pliku Word przy użyciu C# i Aspose.Words.
  Postępuj zgodnie z tym przewodnikiem, aby utworzyć kontrolkę zawartości, ustawić
  tekst zastępczy i zapisać dokument.
og_image_alt: Insert content control example in a Word document
og_title: Wstaw kontrolkę zawartości w Wordzie przy użyciu C# – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Jak wstawić kontrolę zawartości w dokumencie Word przy użyciu C#
url: /pl/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić kontrolkę zawartości w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **wstawić kontrolkę zawartości** w dokumencie Word, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Dowiesz się także, jak **tworzyć kontrolkę zawartości** programowo, ustawiać tekst zastępczy i zapisywać plik na dysku.

Kontrolki zawartości pozwalają definiować obszary, które użytkownicy mogą wypełniać, powtarzać lub blokować. Są szeroko stosowane w szablonach, formularzach i dynamicznych raportach. Poniższe kroki wykorzystują bibliotekę Aspose.Words for .NET, która działa z .NET 6+, .NET Framework 4.6+ oraz .NET Core.

## Jak wstawić kontrolkę zawartości w dokumencie Word

1. **Dodaj Aspose.Words do swojego projektu**  
   Otwórz terminal w folderze projektu i uruchom:

   ```bash
   dotnet add package Aspose.Words
   ```

   Pakiet zawiera klasy `Document`, `DocumentBuilder` i `StructuredDocumentTag` potrzebne do pracy z kontrolkami zawartości.

2. **Utwórz nowy pusty dokument**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   Obiekt `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` zapewnia wygodny kursor do wstawiania węzłów.

## Tworzenie kontrolki zawartości przy użyciu Aspose.Words

Kontrolki zawartości są reprezentowane przez klasę `StructuredDocumentTag` (SDT). Poniższy kod tworzy kontrolkę zawartości typu **plain‑text** i nadaje jej tytuł, który można później odczytać.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Dlaczego to jest ważne:*  
- `SdtType.PlainText` zapewnia, że kontrolka akceptuje wyłącznie zwykłe znaki.  
- `MarkupLevel.Block` sprawia, że kontrolka zachowuje się jak pełny akapit, co jest idealne dla pól formularza.  
- Właściwość `Title` jest stabilnym identyfikatorem, którego można używać przy wyszukiwaniu lub wiązaniu danych.

## Ustawianie tekstu zastępczego i domyślnego

Tekst zastępczy prowadzi użytkownika zanim coś wpisze. Możesz także wstępnie wypełnić kontrolkę domyślną treścią.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

Fragment XML musi odpowiadać typowi danych kontrolki. Dla kontrolek typu plain‑text wymagany jest element `<text>`. Jeśli pominiesz ten krok, zamiast tego zostanie wyświetlony wcześniej zdefiniowany tekst zastępczy.

## Wstawianie kontrolki zawartości w wybranym miejscu

Kursor `DocumentBuilder` określa, gdzie pojawi się kontrolka. Domyślnie kursor znajduje się na początku dokumentu.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Jeśli potrzebujesz kontrolkę wewnątrz tabeli, nagłówka lub po istniejących akapitach, najpierw przesuń buildera:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Zapisywanie dokumentu z wstawioną kontrolką zawartości

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Plik `SDT.docx` zawiera teraz kontrolkę zawartości typu plain‑text o tytule **CustomerName** z tekstem zastępczym „Enter name here” oraz domyślnym tekstem „John Doe”.

![Przykład wstawienia kontrolki zawartości w dokumencie Word](insert-content-control.png)

*Tekst alternatywny obrazu:* Przykład wstawienia kontrolki zawartości w dokumencie Word

### Oczekiwany rezultat

Po otwarciu `SDT.docx` w programie Microsoft Word:
- Szary tekst zastępczy „Enter name here” pojawia się, jeśli usuniesz domyślny tekst.  
- Kontrolka jest podświetlona po kliknięciu wewnątrz, co wskazuje, że można ją edytować.  
- Zakładka **Developer** (jeśli włączona) wyświetla tytuł kontrolki **CustomerName** w panelu Właściwości.

## Pełny działający przykład

Poniżej znajduje się pojedynczy, samodzielny program, który możesz skopiować, skompilować i uruchomić. Demonstruje każdy krok od konfiguracji projektu po zapisanie pliku.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchom program poleceniem `dotnet run`. Po wykonaniu otwórz wygenerowany plik, aby zweryfikować, że kontrolka zawartości pojawiła się zgodnie z opisem.

## Praktyczne wskazówki i typowe pułapki

| Sytuacja | Zalecane podejście |
|-----------|----------------------|
| **Wiele kontrolek tego samego typu** | Nadaj każdej kontrolce unikalny `Title`. Możesz później pobrać kontrolkę przy użyciu `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Kontrolka niewidoczna w Wordzie** | Upewnij się, że zapisałeś dokument z rozszerzeniem `.docx` oraz że wersja `Aspose.Words` jest kompatybilna z Twoją wersją Office. |
| **Potrzebna kontrolka rich‑text** | Użyj `SdtType.RichText` zamiast `PlainText`. Fragment XML będzie wtedy zawierał elementy `<w:richText>`. |
| **Umieszczanie kontrolki w komórce tabeli** | Najpierw przesuń buildera do komórki: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Wydajność przy dużych dokumentach** | Utwórz `StructuredDocumentTag` raz i używaj go ponownie, jeśli potrzebujesz wielu identycznych kontrolek; sklonuj go za pomocą `sdt.Clone(true)`. |

## Kolejne kroki

- **Utwórz powtarzające się kontrolki zawartości** (`SdtType.RepeatingSection`) dla tabel, które rosną dynamicznie.  
- **Powiąż kontrolki zawartości z danymi XML** używając `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Zablokuj kontrolkę** (`sdt.LockContentControl = true`), aby uniemożliwić edycję przez użytkownika, jednocześnie pozwalając na aktualizacje programowe.  

Zgłębianie tych tematów zwiększy Twoją zdolność do tworzenia solidnych szablonów Word przy użyciu Aspose.Words.

---

**Podsumowanie**  
Teraz wiesz, jak **wstawić kontrolkę zawartości** w dokumencie Word przy użyciu C#. Samouczek obejmował tworzenie kontrolki, ustawianie tekstu zastępczego i domyślnego, wstawianie jej w wybranym miejscu oraz zapisywanie końcowego pliku. Dzięki tej podstawie możesz tworzyć zaawansowane formularze, szablony korespondencji seryjnej oraz automatyczne raporty wykorzystujące natywne funkcje kontrolek zawartości w Wordzie.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Ustaw styl kontrolki zawartości](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Ustaw kolor kontrolki zawartości](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Jak tworzyć pola formularza i dodawać zawartość przy użyciu DocumentBuilder w Aspose.Words dla Javy](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}