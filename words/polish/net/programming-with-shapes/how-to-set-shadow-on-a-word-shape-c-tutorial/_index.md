---
category: general
date: 2026-03-30
description: Dowiedz się, jak ustawić cień na kształcie w programie Word przy użyciu
  C#. Ten przewodnik pokazuje także, jak dodać cień do kształtu, dostosować przezroczystość
  kształtu i dodać cień prostokąta.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: pl
og_description: Jak ustawić cień na kształcie w Wordzie w C#? Skorzystaj z tego przewodnika
  krok po kroku, aby dodać cień do kształtu, dostosować przezroczystość kształtu i
  dodać cień prostokąta.
og_title: Jak ustawić cień na kształcie w Wordzie – samouczek C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Jak ustawić cień na kształcie w Wordzie – samouczek C#
url: /pl/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić cień na kształcie w Word – samouczek C#

Zastanawiałeś się kiedyś **jak ustawić cień** na kształcie w dokumencie Word bez ręcznego korzystania z interfejsu? Nie jesteś sam. W wielu raportach czy prezentacjach subtelny cień sprawia, że prostokąt wyróżnia się, a zrobienie tego programowo oszczędza godziny pracy.

W tym przewodniku przejdziemy krok po kroku przez kompletny, gotowy do uruchomienia przykład, który nie tylko pokazuje **jak ustawić cień**, ale także obejmuje **add shape shadow**, **adjust shape transparency** oraz **add rectangle shadow** dla klasycznych ramek wyjaśniających. Po zakończeniu będziesz mieć plik Word (`output.docx`) wyglądający profesjonalnie i zrozumiesz, dlaczego każda właściwość ma znaczenie.

## Wymagania wstępne

- .NET 6+ (lub .NET Framework 4.7.2) z kompilatorem C#  
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Podstawowa znajomość C# i modelu obiektowego Worda  

Nie są potrzebne dodatkowe biblioteki — wszystko znajduje się w Aspose.Words.

---

## Jak ustawić cień na kształcie Word w C#

Poniżej znajduje się pełny plik źródłowy. Zapisz go jako `Program.cs` i uruchom w swoim IDE lub `dotnet run`. Kod ładuje istniejący plik `.docx`, znajduje pierwszy kształt (domyślnie prostokąt), włącza jego cień, dostosowuje kilka parametrów wizualnych i zapisuje wynik.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Co zobaczysz** – Prostokąt otrzyma czarny cień o 30 % przezroczystości, przesunięty o 5 pt w prawo i w dół, z delikatnym rozmyciem. Otwórz `output.docx` w Wordzie, aby to zweryfikować.

## Adjust Shape Transparency – Why It Matters

Transparentność nie jest jedynie estetycznym suwakiem; wpływa na czytelność. Wartość 0.0 sprawia, że cień jest w pełni nieprzezroczysty, a 1.0 ukrywa go całkowicie. W powyższym fragmencie użyliśmy `0.3`, aby uzyskać subtelny efekt działający zarówno na jasnym, jak i ciemnym tle. Śmiało eksperymentuj:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Pamiętaj, że **adjust shape transparency** można również zastosować do koloru wypełnienia kształtu, jeśli potrzebujesz półprzezroczystego prostokąta.

## Add Shape Shadow to Different Objects

Kod, którego użyliśmy, celuje w obiekt `Shape`, ale te same właściwości `ShadowFormat` istnieją w obiektach **Image**, **Chart**, a nawet **TextBox**. Oto szybki wzorzec, który możesz skopiować‑wkleić:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Tak więc, niezależnie od tego, czy **add shape shadow** do logo, czy dekoracyjnej ikony, podejście pozostaje identyczne.

## How to Add Shadow to Any Shape – Edge Cases

1. **Kształt bez ramki** – Niektóre kształty Worda (np. swobodne rysunki) nie obsługują cieni. Próba ustawienia `ShadowFormat.Visible` zakończy się cichym niepowodzeniem. Sprawdź `shape.IsShadowSupported`, jeśli potrzebujesz bezpieczeństwa.  
2. **Starsze wersje Worda** – Właściwości cienia mapują się na funkcje Word 2007+. Jeśli musisz obsługiwać Word 2003, cień zostanie zignorowany przy otwieraniu pliku.  
3. **Wiele cieni** – Aspose.Words obecnie obsługuje jeden cień na kształt. Jeśli potrzebujesz podwójnego efektu, skopiuj kształt, przesuń go i zastosuj różne ustawienia cienia.

## Add Rectangle Shadow – Realny przykład

Wyobraź sobie, że generujesz kwartalny raport, a każdy nagłówek sekcji to kolorowy prostokąt. Dodanie **add rectangle shadow** nadaje stronie wygląd „karty”. Kroki są identyczne jak w podstawowym przykładzie; po prostu upewnij się, że docelowy kształt jest rzeczywiście prostokątem (`shape.ShapeType == ShapeType.Rectangle`). Jeśli musisz utworzyć prostokąt od zera, zobacz poniższy fragment:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Uruchomienie pełnego programu z tym dodatkiem da Ci nowy prostokąt, który już posiada pożądany efekt **add rectangle shadow**.

---

![Word shape with shadow](placeholder-image.png){alt="jak ustawić cień na kształcie w Wordzie"}

*Rysunek: Prostokąt po zastosowaniu ustawień cienia.*

## Szybkie podsumowanie (lista kontrolna)

- **Load** dokument przy pomocy `new Document(path)`.  
- **Locate** kształt za pomocą `doc.GetChild(NodeType.Shape, index, true)`.  
- **Enable** cień: `shape.ShadowFormat.Visible = true;`.  
- **Set color** przy użyciu dowolnego `System.Drawing.Color`.  
- **Adjust transparency** (`0.0–1.0`) aby kontrolować nieprzezroczystość.  
- **OffsetX / OffsetY** przesuwają cień w poziomie/pionie (punkty).  
- **BlurRadius** rozmywa krawędź — wyższe wartości = bardziej rozmyty cień.  
- **Save** plik i otwórz go w Wordzie, aby zobaczyć rezultat.

## Co spróbować dalej?

- **Dynamic colors** – Pobieraj kolor cienia z motywu lub danych wejściowych użytkownika.  
- **Conditional shadows** – Stosuj cień tylko wtedy, gdy szerokość kształtu przekracza określony próg.  
- **Batch processing** – Przejdź przez wszystkie kształty w dokumencie i **add shape shadow** automatycznie.  

Jeśli podążałeś za instrukcjami, teraz wiesz **jak ustawić cień**, jak **adjust shape transparency**, oraz jak **add rectangle shadow** dla profesjonalnego wykończenia. Eksperymentuj, łam rzeczy, a potem naprawiaj — kodowanie to najlepszy nauczyciel.

---

*Miłego kodowania! Jeśli ten samouczek był pomocny, zostaw komentarz lub podziel się własnymi trikami dotyczącymi cieni. Im więcej się uczymy od siebie, tym ładniejsze stają się nasze dokumenty Word.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}