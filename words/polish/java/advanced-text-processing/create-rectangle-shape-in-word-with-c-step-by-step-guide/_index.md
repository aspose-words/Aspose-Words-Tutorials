---
category: general
date: 2026-03-04
description: Dowiedz się, jak utworzyć prostokąt, dodać cień do kształtu i zastosować
  efekt cienia w dokumencie Word, a następnie automatycznie zapisać dokument Word.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: pl
og_description: Utwórz prostokątny kształt, dodaj cień do kształtu i zastosuj efekt
  cienia w dokumencie Word przy użyciu C#. Skorzystaj z tego przewodnika, aby bezproblemowo
  zapisać dokument Word.
og_title: Create rectangle shape in Word – Complete C# Tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /pl/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz kształt prostokąta w Wordzie przy użyciu C# – Kompletny samouczek programistyczny

Czy kiedykolwiek potrzebowałeś **create rectangle shape** w pliku Word, ale nie wiedziałeś od czego zacząć? Nie jesteś sam — wielu programistów napotyka ten problem, gdy po raz pierwszy zagłębia się w programowe generowanie dokumentów. Dobrą wiadomością jest to, że kilkoma wierszami C# możesz wstawić prostokąt, **add shadow to shape**, i **apply shadow effect** bez otwierania Worda. W tym przewodniku przeprowadzimy Cię przez cały proces, od świeżego **create blank document** po zapisanie końcowego **save word document** na dysku.

Omówimy wszystko, czego potrzebujesz: wymaganą paczkę NuGet, dokładne API, dlaczego każda właściwość ma znaczenie oraz kilka wskazówek, aby uniknąć najczęstszych pułapek. Po zakończeniu będziesz mieć w pełni działający przykład, który możesz wkleić do dowolnego projektu .NET.

## Prerequisites

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7+)
- Visual Studio 2022 lub dowolne IDE, które preferujesz
- **Aspose.Words for .NET** zainstalowany przez NuGet (`Install-Package Aspose.Words`)
- Podstawowa znajomość składni C#

Nie są potrzebne dodatkowe biblioteki interop Word — Aspose.Words obsługuje wszystko w pamięci.

## Krok 1 – Utwórz pusty dokument

Pierwszą rzeczą, którą robimy, jest **create blank document**. Traktuj to jak pustą płaszczyznę, na której później **create rectangle shape**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Why this matters:** Rozpoczęcie od czystego obiektu `Document` zapewnia, że żadne ukryte style ani sekcje nie będą zakłócać pozycjonowania kształtu później.

## Krok 2 – Wstaw kształt prostokąta do dokumentu

Teraz faktycznie **create rectangle shape**. Ustawimy jego rozmiar, pozycję i poinstruujemy Word, aby nie zawijał tekstu wokół niego.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** Jeśli potrzebujesz, aby prostokąt znajdował się wewnątrz komórki tabeli, zmień `WrapType` na `WrapType.Inline`. Dla większości raportów, `None` utrzymuje kształt unoszący się nad tekstem.

## Krok 3 – Dodaj cień do kształtu i skonfiguruj jego wygląd

Tutaj dzieje się magia: **add shadow to shape** i **apply shadow effect**. Cień sprawia, że prostokąt wyróżnia się na stronie, szczególnie po wydrukowaniu.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Why these values?**  
> - **BlurRadius** kontroluje, jak rozmyte wyglądają krawędzie; wartość około `5` daje subtelny, profesjonalny wygląd.  
> - **Transparency** pozwala, aby tekst pod nim pozostał czytelny.  
> - **OffsetX/Y** przesuwają cień od kształtu, tworząc głębię.  
> - Użycie odcienia **blue** to tylko przykład — dowolny `System.Drawing.Color` działa.

## Krok 4 – Dodaj skonfigurowany kształt do ciała dokumentu

Po pełnym wystylizowaniu prostokąta, teraz **add rectangle shape** do pierwszej sekcji dokumentu. Ten krok faktycznie umieszcza kształt w pliku.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Edge case:** Jeśli Twój dokument już zawiera sekcje, możesz chcieć skierować się do konkretnej (`doc.Sections[2]` na przykład). Powyższy kod działa dla dokumentu jednosekcyjnego, co jest typowe dla szybkich raportów.

## Krok 5 – Zapisz dokument Word

Na koniec **save word document** na dysk. Plik będzie zawierał prostokąt z cieniem, gotowy do otwarcia w Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Użyj `doc.Save(outputPath, SaveFormat.Docx)`, jeśli musisz wyraźnie określić format. Metoda `Save` automatycznie wykrywa rozszerzenie, ale jawne określenie może uniknąć nieporozumień, gdy ścieżka jest generowana programowo.

## Pełny, uruchamialny przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystkie dyrektywy `using` oraz metodę `Main`, więc możesz go uruchomić od razu.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Oczekiwany wynik

Gdy otworzysz *shadowed_rectangle.docx* w Microsoft Word, zobaczysz niebiesko obramowany prostokąt unoszący się blisko górnej części pierwszej strony, z miękkim niebieskim cieniem przesuniętym o 8 pt w prawo i w dół. Żaden dodatkowy tekst go nie otacza, ponieważ ustawiliśmy `WrapType.None`.

## Najczęściej zadawane pytania i warianty

| Pytanie | Odpowiedź |
|----------|--------|
| **Czy mogę zmienić kształt na elipsę?** | Tak — zamień `ShapeType.Rectangle` na `ShapeType.Ellipse`. Wszystkie właściwości cienia pozostają takie same. |
| **Co zrobić, jeśli potrzebuję wielu kształtów?** | Po prostu powtórz Kroki 2‑4 dla każdej nowej instancji `Shape`, dostosowując `OffsetX/Y` lub `Left/Top`, aby uniknąć nakładania się. |
| **Czy istnieje sposób, aby kolor cienia pasował do wypełnienia kształtu?** | Oczywiście. Najpierw ustaw `rectangle.FillColor`, a potem przypisz `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Jak wstawić kształt do komórki tabeli?** | Użyj `cell.FirstParagraph.AppendChild(rectangle);` po zlokalizowaniu odpowiedniego obiektu `Cell`. |
| **Czy to będzie działać na .NET Core?** | Tak — Aspose.Words jest wieloplatformowy. Upewnij się tylko, że odwołujesz się do odpowiedniej wersji pakietu NuGet dla .NET Core/5/6. |

## Częste pułapki i wskazówki profesjonalne

- **Pitfall:** Zapomnienie o ustawieniu `ShadowFormat.Visible = true`. Właściwości cienia zostaną zignorowane w ciszy.  
  **Fix:** Zawsze włącz widoczność przed modyfikacją innych parametrów cienia.

- **Pitfall:** Użycie bardzo dużego `BlurRadius` (np. 20) może sprawić, że cień będzie rozmyty i nieprofesjonalny.  
  **Fix:** Trzymaj się wartości między `3` a `8` dla większości dokumentów biznesowych.

- **Pro tip:** Jeśli potrzebujesz, aby kształt był później wybieralny (np. do edycji przez użytkownika końcowego), unikaj ustawiania `WrapType.Inline`. Pływające kształty (`WrapType.None`) są łatwiejsze do przemieszczania programowo.

- **Pro tip:** Generując wiele dokumentów w pętli, ponownie używaj jednej instancji `Document` i wywołuj `doc.Clone(true)` dla każdej iteracji, aby poprawić wydajność.

## Powiązane tematy, które możesz zbadać dalej

- **Add text inside a rectangle shape** – dowiedz się, jak używać `Shape.TextPath` do etykiet.  
- **Create complex diagrams** – połącz wiele kształtów, łączniki i grupowanie.  
- **Export to PDF** – konwertuj ten sam dokument do PDF za pomocą jednego `doc.Save("output.pdf")`.  
- **Apply different fill styles** – gradienty, tekstury lub nawet obrazy wewnątrz kształtów.

## Zakończenie

Właśnie **create rectangle shape**, **add shadow to shape** i **apply shadow effect** w pliku Word przy użyciu C#. Postępując zgodnie z pięcioma zwięzłymi krokami, masz teraz wzorzec, który można ponownie wykorzystać w dowolnym scenariuszu automatyzacji dokumentów, i wiesz, jak **save word document** niezawodnie. Śmiało modyfikuj wymiary, kolory lub nawet zamień prostokąt na inną geometrię — Aspose.Words sprawia, że wszystko jest proste.

Jeśli ten samouczek okazał się pomocny, wystaw mu gwiazdkę na GitHubie lub podziel się własnymi wariantami w komentarzach. Szczęśliwego kodowania i niech Twoje dokumenty zawsze wyglądają tak dopracowanie jak ten prostokąt z cieniem!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}