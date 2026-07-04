---
category: general
date: 2026-04-10
description: jak ustawić cień na kształcie w C# – dowiedz się, jak zastosować cień
  rzucany, zmienić przezroczystość, dostosować rozmycie i dodać cień kształtu przy
  użyciu Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: pl
og_description: jak ustawić cień na kształcie w C# – ten tutorial pokazuje, jak zastosować
  cień rzucany, zmienić przezroczystość, dostosować rozmycie i dodać cień kształtu,
  z przejrzystymi przykładami kodu.
og_title: Jak ustawić cień na kształcie w C# – kompletny przewodnik
tags:
- Aspose.Words
- C#
- Document Automation
title: Jak ustawić cień na kształcie w C# – przewodnik krok po kroku
url: /pl/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić cień na kształcie w C# – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak ustawić cień** na kształcie podczas programowego tworzenia dokumentu Word? Nie jesteś sam. Wielu programistów napotyka trudności, gdy potrzebny jest subtelny cień padający dla pola tekstowego, logo lub ramki wyjaśniającej, a dokumentacja API wydaje się nieco uboga.  

W tym samouczku przeprowadzimy Cię przez cały proces: od wczytania pliku `.docx`, pobrania pierwszego `Shape`, po zastosowanie cienia, dostosowanie jego przezroczystości, regulację promienia rozmycia i ostateczne prawidłowe pozycjonowanie. Po zakończeniu będziesz mieć wielokrotnego użytku fragment kodu, który działa z Aspose.Words .NET 2023 lub nowszym, oraz zrozumiesz *dlaczego* każda właściwość ma znaczenie.

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (pakiet NuGet `Aspose.Words`) – biblioteka, która dostarcza klasy `Document`, `Shape` i `ShadowFormat`.  
- **.NET 6+** (lub .NET Framework 4.7.2) – dowolny nowoczesny runtime wystarczy.  
- Prosty plik Word (`input.docx`), który już zawiera co najmniej jeden kształt, np. pole tekstowe.  
- Visual Studio, VS Code lub Twoje ulubione IDE.

To wszystko. Żadnych dodatkowych narzędzi firm trzecich, żadnego COM interop, po prostu czysty C#.

![przykład ustawiania cienia](image-placeholder.png){:alt="jak ustawić cień na kształcie w dokumencie Word"}

## Jak ustawić cień – przegląd

Podstawowa idea **jak ustawić cień** polega na manipulacji obiektem `ShadowFormat`, który znajduje się w `Shape`. Traktuj `ShadowFormat` jako miniaturowy „arkusz stylów” dla samego cienia: informuje renderer, czy cień ma być widoczny, jaki ma mieć kolor, jaką ma mieć przezroczystość, jak bardzo jest rozmyty oraz gdzie znajduje się względem kształtu.  

Poniżej znajduje się *kompletny* program do uruchomienia. Śmiało skopiuj‑wklej go do aplikacji konsolowej, naciśnij **F5** i obserwuj, jak cień pojawia się w zapisanym pliku `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Dlaczego te ustawienia mają znaczenie

- **Visible** – Bez włączenia tej flagi wszystkie pozostałe właściwości są ignorowane.  
- **Color** – Ciemny szary imituje typowy cień UI; możesz podmienić na dowolny `Color`.  
- **Transparency** – 0.3 daje *łagodny* wygląd, jednocześnie zachowując czytelność kształtu.  
- **Size** – Kontroluje rozmycie; wartość 6 zazwyczaj wystarcza dla profesjonalnego efektu.  
- **Distance & Angle** – Razem definiują *przesunięcie*; 2 pt przy 45° daje subtelny cień ukośny.

To jest istota **jak ustawić cień**. Następnie rozłożymy każdy element, abyś mógł **zastosować cień padający**, **zmienić przezroczystość**, **regulować rozmycie** i **dodać cień do kształtu** oddzielnie.

---

## Zastosuj cień padający do kształtu

Kiedy ludzie pytają „jak **zastosować cień padający** w C#?”, często potrzebują tylko przełącznika widoczności i koloru. Poniższy fragment izoluje te dwie linie:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Jeśli celujesz w starsze wersje Worda (2003‑2007), trzymaj się standardowych kolorów. Niektóre egzotyczne wartości ARGB mogą być ignorowane przez starszy renderer.

---

## Jak zmienić przezroczystość cienia

Przezroczystość jest wyrażana jako **float między 0 a 1**. Wartość **0** oznacza całkowicie nieprzezroczysty cień; **1** sprawia, że jest niewidoczny. Większość projektantów ustawia wartość w okolicach **0.2‑0.4** dla naturalnego wyglądu.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Przypadki brzegowe

- **Negative values** – Aspose.Words ograniczy je do 0, ale lepiej jest zwalidować wejście.  
- **Values > 1** – Ograniczone do 1, skutecznie ukrywając cień.  

Jeśli musisz pozwolić użytkownikom wybrać procent, najpierw przelicz go:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Jak regulować rozmycie (Size) cienia

Właściwość **Size** kontroluje promień rozmycia. Większe liczby dają bardziej miękki, rozproszony cień. Jest mierzona w punktach (pt), a nie w pikselach.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Kiedy używać małego vs. dużego rozmycia

- **Small blur (2‑4 pt)** – Dobre dla wywołań w stylu UI, gdzie chcesz wyraźną krawędź.  
- **Large blur (8‑12 pt)** – Dobrze sprawdza się w raportach drukowanych lub gdy kształt jest daleko od tła.

---

## Dodaj cień do kształtu – pozycjonowanie i kierunek

Ostatnim elementem **add shape shadow** jest offset. Dwie właściwości współpracują ze sobą:

| Property | Meaning |
|----------|---------|
| **Distance** | Jak daleko cień znajduje się od kształtu (w punktach). |
| **Angle**    | Kierunek offsetu (0° = w prawo, 90° = w dół, 180° = w lewo, 270° = w górę). |

Przykład, który tworzy subtelny cień w prawym dolnym rogu:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Możesz eksperymentować z kątami, aby symulować światło pochodzące z różnych źródeł. Popularnym trikiem jest pozwolenie użytkownikowi wybrać „źródło światła” z listy rozwijanej i przypisać mu wartość kąta.

---

## Pełny działający przykład (wszystkie kroki połączone)

Poniżej znajduje się ten sam program co wcześniej, ale z **dodatkowymi komentarzami**, które czynią logikę krystalicznie jasną. Skopiuj go do `Program.cs` i uruchom; plik wyjściowy będzie zawierał pole tekstowe z idealnie dopasowanym cieniem.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Oczekiwany rezultat:** Otwórz `output.docx`. Pierwsze pole tekstowe wyświetli ciemnoszary, 30 % przezroczysty cień, lekko rozmyty (size = 6) i przesunięty o 2 pt pod kątem 45°. Efekt jest subtelny, ale zauważalny — dokładnie to, do czego dąży większość projektantów UI.

---

## Częste pytania i pułapki

- **„Czy to działa również z obrazami?”**  
  Tak. Każdy `Shape` — niezależnie czy to pole tekstowe, obraz czy auto‑kształt — udostępnia `ShadowFormat`. Wystarczy zamienić logikę pobierania kształtu na odpowiedni indeks lub nazwę.

- **„Co jeśli dokument zawiera wiele kształtów?”**  
  Przejdź pętlą przez `doc.GetChildNodes(NodeType.Shape, true)` i zastosuj te same ustawienia do każdego. Możesz także filtrować po `shape.Name` lub `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}