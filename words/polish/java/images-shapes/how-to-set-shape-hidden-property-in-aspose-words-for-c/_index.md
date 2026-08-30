---
category: general
date: 2026-08-20
description: Dowiedz się, jak ustawić właściwość ukrycia kształtu w Aspose.Words dla
  C#. Ten przewodnik pokazuje, jak wstawić obraz i ukryć kształt, aby nigdy nie pojawił
  się w interfejsie użytkownika ani w wydruku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: pl
lastmod: 2026-08-20
og_description: Ustaw właściwość ukrycia kształtu w Aspose.Words przy użyciu C#. Wstaw
  obraz, ukryj kształt i upewnij się, że nigdy nie pojawia się w interfejsie użytkownika
  ani w wydruku.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Ustaw ukrytą właściwość kształtu w Aspose.Words – kompletny przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Jak ustawić właściwość ukrycia kształtu w Aspose.Words dla C#
url: /pl/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić właściwość ukrycia kształtu w Aspose.Words dla C#

Jeśli potrzebujesz **ustawić właściwość ukrycia kształtu** w dokumencie Word, ten samouczek pokaże Ci dokładne kroki przy użyciu Aspose.Words dla .NET. Niezależnie od tego, czy tworzysz silnik szablonów, generujesz raporty, czy osadzasz logo, które musi pozostać niewidoczne, nauczysz się wstawiać obraz i ukrywać kształt, aby nigdy nie pojawił się w interfejsie użytkownika ani w wydruku.

W tym przewodniku omówimy również **wstawianie obrazu do dokumentu**, wyjaśnimy, dlaczego ukrywanie kształtu ma znaczenie przy drukowaniu, oraz przeprowadzimy Cię przez kompletny, gotowy do uruchomienia kod. Nie są wymagane żadne zewnętrzne odwołania — wystarczy skopiować, wkleić i uruchomić.

## Wymagania wstępne

* .NET 6.0 lub nowszy (najnowsza wersja Aspose.Words celuje w .NET 6+)
* Ważna licencja Aspose.Words dla .NET (lub użyj trybu darmowej ewaluacji)
* Visual Studio 2022 lub dowolne IDE C#, które preferujesz
* Plik obrazu (np. `logo.png`) umieszczony w folderze, do którego możesz odwołać się w kodzie

## Krok 1: Utwórz nowy Document i DocumentBuilder

Klasa `DocumentBuilder` jest punktem wejścia do programowego budowania zawartości Word. Umożliwia wstawianie akapitów, tabel i kształtów, takich jak obrazy.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Dlaczego ten krok?*  
Utworzenie `Document` zapewnia reprezentację pliku .docx w pamięci, natomiast `DocumentBuilder` dostarcza płynne API, które wstawia obiekty. Bez tych obiektów nie możesz umieścić kształtu w dokumencie.

## Krok 2: Wstaw obraz jako kształt

Aspose.Words traktuje każdy obraz jako `Shape`. Metoda `InsertImage` zwraca tę instancję `Shape`, którą możesz później manipulować.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Dlaczego ten krok?*  
Użycie `InsertImage` nie tylko dodaje obraz do przepływu tekstu, ale także daje Ci referencję (`picture`), którą możesz skonfigurować. Jest to niezbędne dla **właściwości ukrycia kształtu w C#**, którą ustawimy w następnym kroku.

## Krok 3: Ustaw właściwość ukrycia kształtu

Właściwość `Hidden` kontroluje, czy kształt uczestniczy w interfejsie użytkownika i drukowaniu. Ustawienie jej na `true` sprawia, że kształt jest niewidoczny w UI Worda i gwarantuje, że nie zostanie wydrukowany.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Dlaczego ten krok?*  
Gdy kształt jest oznaczony jako ukryty, Word traktuje go jak komentarz — obecny w strukturze dokumentu, ale nigdy nie renderowany. To jest sedno **ustawiania właściwości ukrycia kształtu**.

## Krok 4: Zapisz dokument

Na koniec zapisz dokument na dysku. Możesz wybrać dowolny format obsługiwany przez Aspose.Words (`.docx`, `.pdf`, `.html` itp.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Dlaczego ten krok?*  
Zapisanie finalizuje zmiany w pamięci. Otwarcie powstałego `.docx` w Microsoft Word nie pokazuje widocznego obrazu, a eksport do PDF potwierdza, że kształt nigdy nie pojawia się w wydruku.

## Pełny, gotowy do uruchomienia przykład

Łącząc wszystko razem, oto kompletny program, który możesz skompilować i uruchomić:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Oczekiwany wynik**

* Otwieranie `HiddenImageDocument.docx` w Microsoft Word nie pokazuje widocznego obrazu.
* Eksportowanie lub drukowanie dokumentu (lub otwieranie PDF) również nie pokazuje obrazu.
* Ukryty kształt nadal istnieje w XML dokumentu, co możesz zweryfikować, otwierając `.docx` jako archiwum zip i przeglądając `word/document.xml` — zobaczysz element `<w:pict>` z atrybutem `w:hidden="true"`.

## Typowe warianty i przypadki brzegowe

| Situation | What to do | Why it matters |
|-----------|------------|----------------|
| **Brak pliku obrazu** | Umieść `InsertImage` w bloku `try/catch` i obsłuż `FileNotFoundException`. | Zapobiega awarii aplikacji i umożliwia zapisanie czytelnego błędu w logu. |
| **Wiele ukrytych kształtów** | Wywołaj `picture.Hidden = true` dla każdego wstawianego `Shape`, lub iteruj po `doc.GetChildNodes(NodeType.Shape, true)`. | Gwarantuje, że każdy niepożądany element wizualny pozostaje niewidoczny. |
| **Potrzeba widoczności kształtu tylko w trybie edycji** | Ustaw `picture.Hidden = false` po edycji, a następnie przywróć na `true` przed zapisem. | Umożliwia pracę z kształtem w UI, jednocześnie zachowując czysty wynik końcowy. |
| **Drukowanie w starszych wersjach Worda** | Sprawdź dokument w Word 2010 lub nowszym; flaga ukrycia jest obsługiwana we wszystkich nowoczesnych wersjach. | Zapewnia kompatybilność wśród użytkowników. |
| **Użycie innego formatu pliku (np. PDF bezpośrednio)** | Flaga `Hidden` działa tak samo; Aspose.Words respektuje ją podczas konwersji do PDF. | Potwierdza, że **zapobieganie drukowaniu kształtu** działa dla wszystkich docelowych formatów eksportu. |

## Porada: Sprawdź flagę ukrycia programowo

Jeśli musisz potwierdzić, że kształt jest ukryty przed zapisem, możesz sprawdzić właściwość:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

To proste sprawdzenie jest przydatne w zautomatyzowanych pipeline'ach, gdzie musisz zapewnić zgodność z politykami generowania dokumentów.

## Podsumowanie

Teraz wiesz, jak **ustawić właściwość ukrycia kształtu** w Aspose.Words dla C#. Wstawiając obraz, ustawiając `picture.Hidden = true` i zapisując dokument, kształt pozostaje poza UI i nigdy nie pojawia się w wydruku. Technika ta jest niezbędna, gdy potrzebujesz placeholderów, znaków wodnych lub elementów brandingowych, które mają pozostać niewidoczne dla użytkowników.

### Co dalej?

* Poznaj inne właściwości kształtu, takie jak `picture.WrapType`, `picture.Rotation` i `picture.RelativeHorizontalPosition`.
* Dowiedz się, jak **ukrywać kształt w Aspose.Words** warunkowo, w zależności od danych wejściowych użytkownika lub konfiguracji.
* Połącz ukryte kształty z pętlami **wstawiania obrazu do dokumentu**, aby generować dynamiczne, niewidoczne znaczniki do późniejszego przetwarzania (np. pola scalania korespondencji).

Śmiało eksperymentuj z różnymi formatami obrazów, układami dokumentów i docelowymi formatami eksportu. Ukrywanie kształtów daje Ci precyzyjną kontrolę nad tym, co Twoi czytelnicy naprawdę widzą — a co pozostaje w tle. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz prostokątny kształt w Word przy użyciu Aspose.Words – Przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Wstaw obraz inline w dokumencie Word przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}