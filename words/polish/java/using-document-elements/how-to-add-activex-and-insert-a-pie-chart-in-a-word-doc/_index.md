---
category: general
date: 2026-08-17
description: Jak dodać kontrolki ActiveX i wstawić wykres kołowy w dokumencie Word
  przy użyciu Aspose.Words. Oddziel kawałek i zapisz jako DOCX w kilku krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: pl
lastmod: 2026-08-17
og_description: Jak dodać kontrolki ActiveX, wstawić wykres kołowy, rozdzielić kawałek
  i zapisać jako DOCX przy użyciu Aspose.Words – kompletny przewodnik krok po kroku.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Jak dodać ActiveX i wstawić wykres kołowy w dokumencie Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Jak dodać ActiveX i wstawić wykres kołowy w dokumencie Word
url: /pl/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać kontrolki ActiveX i wstawić wykres kołowy w dokumencie Word

Jeśli potrzebujesz **jak dodać kontrolki ActiveX** i osadzić wykres w dokumencie Word, ten tutorial pokazuje kompletną, gotową do uruchomienia rozwiązanie. Korzystając z Aspose.Words możesz umieścić przycisk CommandButton typu ActiveX, utworzyć wykres kołowy, „wybuchnąć” (explode) wycinek dla podkreślenia, a na koniec **zapisz jako DOCX** w zaledwie kilku linijkach C#.

W poniższych sekcjach zobaczysz wszystkie niezbędne importy, pełny listing kodu oraz wyjaśnienia, dlaczego każdy krok ma znaczenie. Po zakończeniu będziesz w stanie zintegrować interaktywne kontrolki i wizualne dane w dowolnym pliku .docx generowanym programowo.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 lub nowszy (kod działa także z .NET Framework 4.7+)
* Pakiet Aspose.Words for .NET (dostępny przez NuGet)
* Środowisko programistyczne, takie jak Visual Studio 2022 lub VS Code
* Podstawową znajomość C# oraz modelu obiektowego Worda

Nie są wymagane dodatkowe zewnętrzne biblioteki wykresów — Aspose.Words zapewnia wbudowane tworzenie wykresów.

## Jak dodać kontrolki ActiveX przy użyciu Aspose.Words

Kontrolki ActiveX pozwalają osadzać interaktywne elementy UI bezpośrednio w pliku Word. W tym przewodniku dodajemy **CommandButton**, który później można podłączyć do kodu VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Dlaczego to działa:**  
`InsertForms2OleControl` tworzy kontener OLE, który interfejs Worda rozpoznaje jako kontrolkę ActiveX. Ustawienie typu kontrolki na `CommandButton` i nadanie jej podpisu sprawia, że zachowuje się jak standardowy przycisk, gdy użytkownik otworzy plik w Wordzie.

## Wstaw wykres kołowy i „wybuchnij” wycinek

Wykresy są przydatne do wizualizacji danych bez opuszczania dokumentu. Poniższe kroki demonstrują **jak wstawić wykres** i konkretnie **wykres kołowy**, którego pierwszy wycinek jest „wybuchnięty”.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Dlaczego wybuchamy wycinek:**  
Wywołanie `SetExplode(0, true)` instruuje Aspose.Words, aby odsunięto pierwszy punkt danych, przyciągając wzrok odbiorcy do tego segmentu. To powszechna technika w prezentacjach, aby podkreślić kluczową wartość.

## Zapisz jako DOCX

Po dodaniu przycisku ActiveX i wykresu, zapisz dokument na dysku. Ten krok demonstruje **zapis jako DOCX** przy użyciu standardowej metody.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Plik `Output.docx` zawiera teraz interaktywny przycisk, wykres kołowy z odsuniętym wycinkiem i może być otwarty w Microsoft Word bez dodatkowych wtyczek.

## Pełny, uruchamialny przykład

Łącząc wszystko razem, oto samodzielny program, który możesz skopiować do aplikacji konsolowej i od razu uruchomić.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Oczekiwany rezultat:**  
Otwarcie `Output.docx` w Wordzie wyświetla przycisk oznaczony *Click Me* oraz wykres kołowy, w którym pierwszy wycinek (January) jest odsunięty od reszty. Przycisk jest gotowy do obsługi zdarzeń VBA, a wykres można edytować przy użyciu wbudowanych narzędzi Worda.

## Częste pytania i przypadki brzegowe

* **Czy mogę dodać inne typy ActiveX?**  
  Tak. Zamień `Forms2OleControlType.CommandButton` na dowolną wartość z wyliczenia `Forms2OleControlType` (np. `CheckBox`, `OptionButton`). Ten sam wzorzec wstawiania ma zastosowanie.

* **Co jeśli potrzebuję innego typu wykresu?**  
  Użyj `ChartType.Bar`, `ChartType.Line` itd. w wywołaniu `InsertChart`. Krok **jak wstawić wykres** pozostaje identyczny; zmienia się jedynie wartość wyliczenia.

* **Jak kontrolować rozmiar odsuniętego wycinka?**  
  Aspose.Words obecnie obsługuje binarną flagę explode (true/false). Aby uzyskać dokładniejszą kontrolę (np. odległość odsunięcia), trzeba edytować wygenerowany OOXML po zapisaniu.

* **Czy dokument jest kompatybilny ze starszymi wersjami Worda?**  
  Zapis jako DOCX zapewnia kompatybilność z Word 2007 i nowszymi. Dla Word 2003 można użyć `SaveFormat.Doc`, ale wsparcie dla ActiveX w tym formacie jest ograniczone.

* **Czy muszę odwoływać się do `System.Drawing`?**  
  Nie. Wszystkie obiekty rysunkowe są dostarczane przez Aspose.Words, więc jedynym wymaganym pakietem NuGet jest `Aspose.Words`.

## Podsumowanie

Teraz wiesz **jak dodać ActiveX**, **wstawić wykres kołowy**, **wybuchnąć wycinek koła** oraz **zapisz jako DOCX** przy użyciu Aspose.Words for .NET. Kompletny przykład obejmuje każdy krok od tworzenia dokumentu po ostateczne zapisanie i wyjaśnia uzasadnienie każdego wywołania API.

Następnie możesz rozważyć:

* Dodanie makr VBA reagujących na kliknięcie CommandButton (**jak wstawić wykres** i automatyzować aktualizacje danych)
* Dostosowanie wyglądu wykresu (kolory, etykiety danych) do identyfikacji wizualnej firmy
* Osadzenie dodatkowych kontrolek ActiveX, takich jak **ComboBox** lub **ListBox**, aby wzbogacić formularze

Śmiało eksperymentuj z kodem, zamień przykładowe dane i zintegrować rozwiązanie ze swoimi pipeline’ami generowania dokumentów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i poznać alternatywne podejścia implementacyjne w własnych projektach.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}