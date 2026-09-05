---
category: general
date: 2026-09-05
description: Poznaj, jak stworzyć grupowy kształt w pliku docx, wstawić przycisk ActiveX
  oraz wczytać Markdown do dokumentu Word, korzystając z kompletnego przykładu w C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: pl
lastmod: 2026-09-05
og_description: Utwórz grupowy kształt docx, wstaw przycisk polecenia ActiveX i załaduj
  Markdown do dokumentu Word przy użyciu C#. Postępuj zgodnie z tym samouczkiem krok
  po kroku.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Utwórz grupowy kształt docx i osadź kontrolki ActiveX – przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Jak utworzyć grupowy kształt w docx i dodać interaktywne kontrolki w C#
url: /pl/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć grupowy kształt docx i dodać interaktywne kontrolki w C#

Jeśli potrzebujesz **create group shape docx** plików programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz także, jak **insert ActiveX command button** kontrolki i **load Markdown into a Word document** bez utraty formatowania podkreślenia. Po zakończeniu tutorialu będziesz mieć w pełni funkcjonalny `.docx`, który łączy grafikę wektorową, interaktywne elementy UI oraz treść opartą na markdown.

Ten tutorial zakłada, że masz podstawowe środowisko programistyczne C# oraz zainstalowaną bibliotekę Aspose.Words for .NET. Nie są wymagane żadne zewnętrzne narzędzia — wszystko działa w standardowej aplikacji konsolowej lub desktopowej .NET.

## Wymagania wstępne

- .NET 6.0 SDK lub nowszy (kod działa również z .NET Framework 4.7+)
- Aspose.Words for .NET (pakiet NuGet `Aspose.Words`)
- Ważny certyfikat X.509 (`.pfx`), jeśli chcesz przetestować krok podpisywania
- Plik obrazu (np. `logo.png`) oraz plik markdown (`sample.md`) umieszczone w znanym folderze

> **Pro tip:** Przechowuj wszystkie pliki wejściowe w jednym folderze *resources*, aby uprościć ścieżki względne.

## Krok 1: Skonfiguruj projekt i zaimportuj przestrzenie nazw

Utwórz nowy projekt konsolowy i dodaj wymagane dyrektywy `using`. Ten blok pokazuje również, jak odwołać się do klas Aspose.Words, które będą używane później.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Dyrektywy `using` zapewniają bezpośredni dostęp do `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` oraz innych typów używanych w całym tutorialu.

## Krok 2: **Create group shape docx** – dodaj grupowany kształt z elementami podrzędnymi

*Group shape* pozwala traktować wiele obiektów rysunkowych jako jedną jednostkę. Jest to przydatne przy przemieszczaniu lub skalowaniu powiązanych grafik razem.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Dlaczego group shape?**  
Grupowanie utrzymuje prostokąt i elipsę wyrównane, gdy użytkownik przeciąga je w Wordzie. Ułatwia to także późniejsze operacje, takie jak zastosowanie wspólnej obramowania czy programowe przemieszczanie całej grafiki.

## Krok 3: Wstaw kontrolkę zawartości plain‑text (placeholder dla danych użytkownika)

Kontrolki zawartości dają użytkownikom końcowym ustrukturyzowany obszar do wpisywania tekstu. Tekst placeholdera znika, gdy użytkownik zaczyna pisać.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Właściwość `PlaceholderName` to to, co Word wyświetla w jasnoszarej wskazówce. Użytkownicy mogą ją zastąpić własnym tekstem, a podstawowy XML pozostaje poprawny.

## Krok 4: **Insert ActiveX command button** – dodaj interaktywny UI do dokumentu

Kontrolki ActiveX są nadal obsługiwane w nowoczesnych plikach Word i mogą wywoływać makra lub zewnętrzną automatyzację. Poniżej dodajemy *command button* i ustawiamy jego etykietę.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Kiedy używać przycisku ActiveX?**  
Jeśli rozpowszechniasz dokument w środowisku korporacyjnym, które opiera się na makrach VBA, przycisk ActiveX może uruchomić makro lub zewnętrzną aplikację. Dla czysto HTML‑owej interaktywności rozważ użycie *content controls* z *Office.js*.

## Krok 5: Wstaw ukryty obraz (np. logo) w celu brandingu lub późniejszego dostępu skryptowego

Ukryte kształty nie są wyświetlane w wydrukowanym dokumencie, ale pozostają w XML, co pozwala na ich programowe pobranie później.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Krok 6: **Load markdown into a Word document** przy zachowaniu formatowania podkreślenia

Aspose.Words może importować Markdown bezpośrednio. Włączenie `ImportUnderlineFormatting` zapewnia, że podkreślenia w markdown (`<u>` lub `__text__`) zamieniane są na style podkreślenia w Wordzie zamiast zwykłego tekstu.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Przypadek brzegowy:** Jeśli plik markdown zawiera tabele, są one automatycznie konwertowane na tabele Word. Jeśli potrzebujesz niestandardowego stylu tabeli, zastosuj `DocumentBuilder` po wstawieniu.

## Krok 7: Podpisz dokument przy użyciu XAdES‑EPES (opcjonalny krok bezpieczeństwa)

Podpisy cyfrowe gwarantują integralność dokumentu. Poniższy kod podpisuje plik **create group shape docx** przy użyciu profilu XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** Przechowuj hasło do certyfikatu poza systemem kontroli wersji. Używaj zmiennych środowiskowych lub bezpiecznego magazynu w produkcji.

## Pełny, uruchamialny przykład

Połączenie wszystkich kroków daje pojedynczy, samodzielny program. Zapisz plik jako `Program.cs` i uruchom go z wiersza poleceń.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Uruchomienie programu generuje `CompleteGroupShape.docx` zawierający:

- Grupowany prostokąt + elipsę (rdzeń **create group shape docx**)
- Kontrolkę zawartości plain‑text z tekstem placeholder
- **insert ActiveX command button** oznaczony „Click Me”
- Ukryty obraz logo
- Zawartość markdown z zachowanymi podkreśleniami
- Cyfrowy podpis XAdES‑EPES (jeśli podano certyfikat)

## Częste pytania i rozwiązywanie problemów

| Question | Answer |
|---|---|
| **Czy przycisk ActiveX będzie działał w Wordzie na macOS?** | Word na macOS nie obsługuje kontrolek ActiveX. Przycisk będzie wyświetlany jako statyczny obraz. Użyj content controls z Office.js dla interaktywności wieloplatformowej. |
| **Co jeśli plik markdown zawiera własny CSS?** | Aspose.Words ignoruje CSS; przetwarzana jest tylko standardowa składnia markdown. Przekształć elementy stylizowane CSS na style Word ręcznie po imporcie. |
| **Czy mogę dodać więcej kształtów do tej samej grupy później?** | Tak. Pobierz `GroupShape` po nazwie lub indeksie, a następnie wywołaj `AppendChild(newShape)`. Pamiętaj, aby ponownie zapisać dokument po modyfikacjach. |
| **Jak zmienić algorytm podpisu?** | Ustaw `signature.SignatureAlgorithm` przed wywołaniem `Sign`. Domyślnie jest to SHA‑256, co spełnia większość wymagań zgodności. |
| **Czy ukryty obraz jest widoczny w interfejsie Word?** | Nie, ale może być wyświetlony po włączeniu opcji *Show hidden text* w ustawieniach Worda. Jest to przydatne do przechowywania metadanych bez zagracania układu. |

## Kolejne kroki

Teraz, gdy możesz **create group shape docx**, **insert ActiveX command button** i **load markdown into a Word document**, możesz rozważyć:

- **Embedding VBA macros** które reagują na kliknięcie przycisku ActiveX.
- **Applying custom styles** do akapitów wygenerowanych z markdown.
- **Generating PDFs** z tego samego dokumentu przy użyciu `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** wielu plików markdown w jeden skompilowany raport.

Te rozszerzenia pozwalają zbudować w pełni zautomatyzowane pipeline'y dokumentów, które łączą bogatą grafikę, interaktywne kontrolki i autorstwo oparte na markdown — wszystko w C#.

---

*Szczęśliwego kodowania! Jeśli ten tutorial był dla Ciebie przydatny*

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz Group Shape w dokumencie Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Utwórz prostokątny kształt w Word przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Utwórz markdown z Word – kompletny przewodnik C#](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}