---
category: general
date: 2026-03-01
description: Utwórz dokument Word przy użyciu Aspose.Words i dowiedz się, jak dodać
  kształt prostokąta, jak dodać cień, jak ustawić przezroczystość oraz jak utworzyć
  kształt — wszystko w C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: pl
og_description: Utwórz dokument Word przy użyciu Aspose.Words w C#. Dowiedz się, jak
  dodać kształt prostokąta, zastosować zewnętrzny cień i ustawić przezroczystość w
  kilku prostych krokach.
og_title: Utwórz dokument Word z prostokątnym kształtem i cieniem – przewodnik
tags:
- Aspose.Words
- C#
- Document Generation
title: Tworzenie dokumentu Word z prostokątnym kształtem i cieniem – przewodnik krok
  po kroku
url: /pl/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word z prostokątnym kształtem i cieniem – przewodnik krok po kroku

Czy kiedykolwiek potrzebowałeś **utworzyć dokument Word**, który zawiera niestandardowy prostokąt? Może tworzysz szablon raportu i chcesz subtelny cień, aby układ się wyróżniał. Nie jesteś jedyny — programiści ciągle pytają: „Jak dodać prostokątny kształt i cień programowo?” Dobrą wiadomością jest to, że z Aspose.Words możesz to zrobić w kilku linijkach.

W tym samouczku przeprowadzimy Cię przez cały proces: od utworzenia pustego pliku Word, przez dodanie prostokątnego kształtu, po skonfigurowanie zewnętrznego cienia z przezroczystością. Po zakończeniu będziesz mieć gotowy do użycia `Shadow.docx`, który możesz otworzyć w Wordzie i od razu zobaczyć efekt. Bez zewnętrznych narzędzi, bez skomplikowanego XML — tylko czysty kod C# i klarowne wyjaśnienia.

## Czego się nauczysz

- **How to create shape** objects in a Word document using Aspose.Words.
- **How to add rectangle shape** to a paragraph without messing up existing content.
- **How to add shadow** (outer shadow) and control its color, offset, blur, and transparency.
- **How to set transparency** on the shadow so it looks professional.
- Tips, pitfalls, and variations you might need in real‑world projects.

### Wymagania wstępne

- .NET 6.0 lub nowszy (API działa również z .NET Framework 4.6+).
- Aspose.Words for .NET zainstalowany przez NuGet (`Install-Package Aspose.Words`).
- Podstawowa znajomość składni C# — nic skomplikowanego, tylko typowe instrukcje `using` i tworzenie obiektów.

> **Pro tip:** Jeśli używasz Visual Studio, włącz „nullable reference types”, aby wcześnie wykrywać potencjalne błędy związane z null.

## Krok 1 – Utwórz pusty dokument Word

Aby **utworzyć dokument Word** zaczynamy od klasy `Document`. Traktuj ją jak pustą płótno; później możesz dodać sekcje, akapity, tabele lub kształty.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Dlaczego potrzebujemy świeżej instancji `Document`? Ponieważ każdy kształt, akapit czy styl istnieje w modelu obiektowym dokumentu (DOM). Rozpoczęcie od czystego dokumentu gwarantuje, że dodany prostokąt nie zakłóci istniejącej treści.

## Krok 2 – Zdefiniuj prostokątny kształt

Teraz **how to create shape** prostokąt. Konstruktor `Shape` przyjmuje dokument właściciela oraz typ kształtu. Ustawiamy także jego szerokość i wysokość w punktach (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Możesz się zastanawiać: „Czy mogę używać centymetrów zamiast punktów?” API akceptuje wyłącznie punkty, ale możesz przeliczyć: `points = centimeters * 28.35`. To małe przeliczenie jest przydatne, gdy wyrównujesz kształty do marginesów strony.

## Krok 3 – Dodaj zewnętrzny cień i ustaw przezroczystość

Tutaj dzieje się magia: **how to add shadow** i **how to set transparency** tego cienia. Właściwość `ShadowFormat` daje pełną kontrolę.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Dlaczego te ustawienia?**  
- **Transparency** pozwala, aby tekstura podstrony prześwitywała, zapobiegając zbyt ciężkiemu wyglądowi cienia.  
- **OffsetX/Y** tworzy wrażenie, że kształt jest podniesiony nad stroną.  
- **BlurRadius** wygładza krawędzie — bez tego cień byłby twardym prostokątem, co wygląda nienaturalnie.  

Jeśli potrzebujesz bardziej dramatycznego efektu, zwiększ `OffsetX/Y` do 10 i podnieś `BlurRadius` do 8. Natomiast dla subtelnego akcentu pozostaw je na poziomie 2 i 2.

## Krok 4 – Wstaw kształt do dokumentu

Teraz **add rectangle shape** do pierwszego akapitu dokumentu. Jeśli dokument nie ma treści, `FirstParagraph` zostanie automatycznie utworzony.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Co zrobić, gdy chcesz umieścić kształt w konkretnej komórce tabeli lub w późniejszym akapicie? Po prostu znajdź ten węzeł (`doc.GetChild(NodeType.Paragraph, index, true)`) i wywołaj na nim `AppendChild`. Ten sam obiekt kształtu można sklonować, jeśli potrzebujesz wielu kopii.

## Krok 5 – Zapisz dokument

Na koniec **utworzyć dokument Word** na dysku. Użyj ścieżki odpowiedniej dla Twojego środowiska; w przykładzie użyto symbolicznego placeholdera.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Gdy otworzysz `Shadow.docx` w Microsoft Word, zobaczysz jasnoszary prostokąt z miękkim zewnętrznym cieniem przesuniętym w dół‑w prawo. Przezroczystość cienia wynosząca 30 % zapewnia, że nie przytłacza on strony.

---

![Create word document with a shadowed rectangle shape](image.png "Create word document with a shadowed rectangle")

*Image alt text: utworzyć dokument Word z prostokątnym kształtem i cieniem*

## Pełny, gotowy do uruchomienia kod

Poniżej znajduje się kompletny program, który możesz skopiować‑wkleić do aplikacji konsolowej. Brak brakujących fragmentów, brak „zobacz dokumentację po więcej”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Oczekiwany wynik

- Plik o nazwie **Shadow.docx** pojawia się w docelowym folderze.
- Po otwarciu w Wordzie widoczny jest prostokąt (200 × 100 pt) z ciemnoszarym zewnętrznym cieniem.
- Cień jest przesunięty o 5 pt w poziomie i pionie, rozmyty i ma 30 % przezroczystości.

## Częste pytania i przypadki brzegowe

| Question | Answer |
|----------|--------|
| **Can I change the shadow color to match my brand?** | Absolutely—just replace `System.Drawing.Color.DarkGray` with any `Color` you prefer, e.g., `Color.FromArgb(255, 0, 120, 215)` for a blue accent. |
| **What if I need an inner shadow instead of outer?** | Set `ShadowFormat.Style = ShadowStyle.InnerShadow`. The rest of the properties behave the same. |
| **Is transparency supported in older Word versions?** | Yes. Aspose.Words writes the appropriate XML that Word 2007+ understands. Older versions may ignore the transparency value but will still show the shadow. |
| **Can I add multiple shapes with different shadows?** | Sure—just create new `Shape` instances, configure each shadow independently, and append them to the desired nodes. |
| **What about performance for hundreds of shapes?** | Creating many shapes can increase memory usage. Reuse a single `Document` instance and add shapes in a loop; dispose of temporary objects if you run into pressure. |

## Wskazówki dla projektów w rzeczywistym świecie

- **Batch generation:** When generating reports for many users, instantiate a single `Document` template and clone it for each iteration. Replace placeholders before appending shapes.
- **Dynamic sizing:** Use page dimensions (`document.FirstSection.PageSetup.PageWidth`) to calculate shape size relative to the page, ensuring consistent layout across different paper sizes.
- **Testing:** Always open the generated `.docx` in Word after a change to the shadow parameters. Visual feedback is quicker than guessing numbers.

## Kolejne kroki

Teraz, gdy wiesz **how to add rectangle shape**, **how to add shadow** i **how to set transparency**, rozważ dalsze eksploracje:

- Dodawanie **gradient fills** do kształtów (`Shape.FillFormat`).
- Osadzanie **pictures** wewnątrz kształtów w celu uzyskania efektu znaku wodnego.
- Używanie **tables** do wyrównania wielu cieniowanych kształtów w siatce.
- Eksportowanie tego samego dokumentu do PDF (`document.Save("output.pdf")`) przy zachowaniu cieni.

Każdy z tych elementów opiera się na tych samych podstawowych koncepcjach, więc będziesz czuł się pewnie rozszerzając kod.

---

### Podsumowanie

Zaczęliśmy od **utworzyć dokument Word** z Aspose.Words, potem **how to create shape** prostokąt, zastosowaliśmy **how to add shadow**, dopasowaliśmy **how to set transparency** i zapisaliśmy wynik. Cały proces mieści się w kompaktowym, wielokrotnie używalnym wzorcu, który możesz dostosować do dowolnego scenariusza automatyzacji.

Śmiało eksperymentuj — zmieniaj kolory, baw się przesunięciami lub układaj kilka kształtów razem. Gdy napotkasz problem, wróć do powyższych sekcji; zostały zaprojektowane jako szybka referencja. Szczęśliwego kodowania i niech Twoje dokumenty zawsze wyglądają profesjonalnie!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}