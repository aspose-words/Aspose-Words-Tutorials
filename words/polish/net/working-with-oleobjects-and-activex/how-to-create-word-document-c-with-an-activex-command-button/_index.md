---
category: general
date: 2026-10-26
description: Dowiedz się, jak w C# tworzyć dokumenty Word i programowo dodawać przycisk
  ActiveX. Ten przewodnik krok po kroku opisuje wstawianie przycisku polecenia, ukrywanie
  go w czasie projektowania oraz zapisywanie pliku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: pl
lastmod: 2026-10-26
og_description: Utwórz dokument Word w C# i programowo dodaj przycisk ActiveX. Skorzystaj
  z tego pełnego poradnika, aby osadzić przycisk polecenia, który pojawia się tylko
  w czasie wykonywania.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Utwórz dokument Word w C# z przyciskiem polecenia ActiveX – pełny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Jak utworzyć dokument Word w C# z przyciskiem ActiveX?
url: /pl/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word w C# z przyciskiem polecenia ActiveX

Jeśli potrzebujesz **utworzyć dokument Word w C#**, który zawiera interaktywny przycisk, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Po przeczytaniu pierwszych dwóch zdań będziesz znać ogólne podejście, a kolejne kroki przeprowadzą Cię przez każdą linię kodu, którą musisz napisać.

Nauczysz się, jak dodać przycisk ActiveX, ukryć go podczas projektowania i sprawić, by był widoczny dopiero po otwarciu pliku przez użytkownika. Poradnik obejmuje także typowe pułapki, takie jak ostrzeżenia bezpieczeństwa i kompatybilność wersji, abyś mógł dostarczać niezawodne dokumenty.

## Wymagania wstępne

* Zainstalowany .NET 6.0 lub nowszy  
* Licencjonowana kopia **Aspose.Words for .NET** (bezpłatna wersja próbna nadaje się do eksperymentów)  
* Podstawowa znajomość C# i Visual Studio (dowolne IDE obsługujące .NET będzie odpowiednie)

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Krok 1: Utwórz dokument Word w C# i zainicjalizuj DocumentBuilder

Pierwszym krokiem jest utworzenie obiektu `Document` oraz `DocumentBuilder`. `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` udostępnia płynne metody dodawania treści.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Dlaczego to ważne:** Bez `DocumentBuilder` musiałbyś ręcznie manipulować DOM OpenXML, co jest podatne na błędy i trudniejsze do odczytania. Builder abstrahuje te szczegóły i zapewnia prawidłowo sformatowany plik Word.

## Krok 2: Jak dodać przycisk ActiveX – wstaw kontrolkę CommandButton

Teraz wstawiamy **kontrolkę CommandButton ActiveX** w określone miejsce. Prostokąt definiuje pozycję przycisku (X, Y) oraz rozmiar (szerokość, wysokość) w punktach.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Dlaczego to ważne:** `InsertForms2OleControl` jest jedyną metodą Aspose.Words, która tworzy prawdziwy obiekt ActiveX OLE. Wartość wyliczenia `Forms2OleControlType.CommandButton` informuje Word, aby osadził klikalny przycisk zamiast ogólnego kontenera OLE.

## Krok 3: Programowe dodanie przycisku polecenia – ukrycie go do czasu uruchomienia

Word traktuje każde wstawione kształty jako widoczne domyślnie. Aby przycisk był niewidoczny podczas projektowania szablonu, ustaw właściwość `Hidden` na kształcie, który właśnie został utworzony przez builder.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Dlaczego to ważne:** Ustawienie `Hidden = true` zapobiega zagraceniu widoku projektowego przyciskiem. Gdy dokument zostanie otwarty w Wordzie, środowisko uruchomieniowe automatycznie ujawnia kontrolkę, zachowując zamierzone doświadczenie użytkownika.

## Krok 4: Zapisz plik – utwórz dokument Word z przyciskiem polecenia

Na koniec zapisz dokument na dysku. Wybierz ścieżkę, do której aplikacja ma uprawnienia zapisu, i użyj rozszerzenia `.docx`, aby zapewnić nowoczesną kompatybilność.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Dlaczego to ważne:** Zapisanie jako `.docx` gwarantuje, że osadzona kontrolka ActiveX jest zgodna ze standardem Office Open XML, obsługiwanym od Word 2007. Jeśli potrzebujesz starszego formatu `.doc`, zamień rozszerzenie i użyj `SaveFormat.Doc`.

## Pełny działający przykład

Łącząc wszystkie elementy, oto kompletny program, który możesz skopiować, wkleić i uruchomić:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Oczekiwany wynik:** Po uruchomieniu programu otwórz `C:\Temp\ActiveX.docx` w Microsoft Word. Zobaczysz pusty dokument; przycisk nie jest widoczny w trybie projektowania. Naciśnij **Alt + F9**, aby przełączyć kody pól, a następnie kliknij obszar przycisku — Word wyświetli kontrolkę ActiveX i będziesz mógł z nią interagować (np. dwukrotnie kliknąć, aby zobaczyć jej właściwości).

## Przypadki brzegowe i wskazówki najlepszych praktyk

| Sytuacja | Na co zwrócić uwagę | Zalecane rozwiązanie |
|-----------|-------------------|-----------------|
| **Użytkownik wyłącza ActiveX** | Word może wyświetlić ostrzeżenie bezpieczeństwa lub zablokować kontrolkę. | Poproś użytkowników końcowych o włączenie „kontrolek ActiveX” w Centrum zaufania, lub zapewnij alternatywę podpisaną makrem. |
| **Dokument otwarty w Word Online** | Word Online nie obsługuje ActiveX; przycisk zostanie pominięty. | Użyj alternatywnego hiperłącza lub kontrolki zawartości, jeśli potrzebna jest kompatybilność w chmurze. |
| **Różne ustawienia DPI** | Rozmiar prostokąta może wyglądać większy lub mniejszy na wyświetlaczach o wysokim DPI. | Użyj `GraphicsUnit.Point` (domyślnego) i testuj na typowych ustawieniach DPI (96 dpi, 120 dpi). |
| **Wiele przycisków** | Wywołanie `GetChildNodes(NodeType.Shape, true)[0]` pobiera tylko pierwszy kształt. | Przejdź pętlą przez `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` i ustaw `Hidden` dla każdego dodanego kształtu. |
| **Starszy format .doc** | Niektóre właściwości ActiveX są tracone przy zapisie jako `.doc`. | Preferuj `.docx`, chyba że masz ścisły wymóg starszego formatu. |

**Porada:** Po wstawieniu przycisku możesz przypisać makro do jego właściwości `OnAction` za pomocą interfejsu Worda. Pozwala to zdefiniować własne zachowanie po kliknięciu bez konieczności pisania dodatkowego kodu C#.

## Najczęściej zadawane pytania

* **Czy to działa z .NET Core?**  
  Tak. Aspose.Words for .NET jest w pełni kompatybilny z .NET 5, .NET 6 i nowszymi. Wystarczy odwołać się do tego samego pakietu NuGet.

* **Czy mogę zmienić podpis przycisku po wygenerowaniu dokumentu?**  
  Podpis ustawiony w `InsertForms2OleControl` staje się domyślnym tekstem w czasie projektowania. Użytkownicy mogą go edytować w Wordzie, ale możesz także zaktualizować podpis programowo, uzyskując dostęp do właściwości obiektu OLE poprzez API `Shape.OleFormat`.

* **Co zrobić, jeśli potrzebuję innego rozmiaru przycisku?**  
  Dostosuj wartości `RectangleF`. Dwa pierwsze parametry to współrzędne X i Y; dwa ostatnie to szerokość i wysokość w punktach (1 pt = 1/72 cala).

## Zakończenie

Teraz wiesz, jak **utworzyć dokument Word w C#** i **programowo dodać przycisk polecenia** przy użyciu Aspose.Words. Poradnik obejmował inicjalizację dokumentu, wstawianie przycisku ActiveX, ukrywanie go do czasu uruchomienia oraz zapisywanie finalnego pliku. Dzięki tym elementom możesz osadzać interaktywne kontrolki w dowolnym szablonie Word, który generujesz.

Następnie odkryj powiązane tematy, takie jak **jak dodać obsługę zdarzeń przycisku ActiveX**, **stylizacja przycisku polecenia w Wordzie** przy użyciu VBA oraz **programowe dodawanie przycisku polecenia** do istniejących dokumentów. Rozszerzenie tego wzorca na pola wyboru, listy rozwijane czy własne obiekty OLE odbywa się tak samo — wystarczy zmienić wartość wyliczenia `Forms2OleControlType`.

Zacznij eksperymentować: zamień podpis, dostosuj pozycję lub połącz wiele kontrolek. Im więcej będziesz ćwiczyć, tym płynniej będziesz tworzyć bogate, interaktywne dokumenty Word z C#. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i poznać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak programowo dodać przycisk polecenia w dokumencie Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Jak dodać przycisk ActiveX w dokumencie Word przy użyciu Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Utwórz dokument Word z przyciskiem ActiveX – przewodnik C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}