---
category: general
date: 2025-12-08
description: Szybko dodaj cień do kształtu za pomocą Aspose.Words. Dowiedz się, jak
  utworzyć dokument Word przy użyciu Aspose, jak dodać cień do kształtu oraz jak zastosować
  przezroczystość cienia w C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: pl
og_description: Dodaj cień do kształtu w pliku Word przy użyciu Aspose.Words. Ten
  przewodnik krok po kroku pokazuje, jak utworzyć dokument, dodać kształt i zastosować
  przezroczystość cienia.
og_title: Dodaj cień do kształtu – Poradnik Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: Dodaj cień do kształtu w dokumencie Word – Kompletny przewodnik Aspose.Words
url: /polish/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Dodaj cień do kształtu – Kompletny przewodnik Aspose.Words

Kiedykolwiek potrzebowałeś **dodać cień do kształtu** w pliku Word, ale nie byłeś pewien, które wywołania API użyć? Nie jesteś sam. Wielu programistów napotyka trudności, gdy po raz pierwszy próbują dodać prostokątowi lub innemu elementowi rysunkowemu właściwy cień, szczególnie pracując z Aspose.Words dla .NET.

W tym samouczku przeprowadzimy Cię przez wszystko, co musisz wiedzieć: od **tworzenia dokumentu Word przy użyciu Aspose** po konfigurowanie cienia, dostosowywanie jego rozmycia, odległości, kąta oraz nawet **stosowanie przezroczystości cienia**. Na końcu będziesz mieć gotowy do uruchomienia program w C#, który generuje plik `.docx` z ładnie przyciemnionym prostokątem — bez ręcznego manipulowania w Wordzie.

---

## Czego się nauczysz

- Jak skonfigurować projekt Aspose.Words w Visual Studio.  
- Dokładne kroki do **tworzenia dokumentu Word przy użyciu Aspose** i wstawiania kształtu.  
- **Jak dodać cień do kształtu** z pełną kontrolą nad rozmyciem, odległością, kątem i przezroczystością.  
- Wskazówki dotyczące rozwiązywania typowych problemów (np. brak licencji, nieprawidłowe jednostki).  
- Pełny, gotowy do skopiowania i wklejenia przykład kodu, który możesz uruchomić już dziś.

> **Wymagania wstępne:** .NET 6+ (lub .NET Framework 4.7.2+), ważna licencja Aspose.Words (lub wersja próbna), oraz podstawowa znajomość C#.

---

## Krok 1 – Skonfiguruj projekt i dodaj Aspose.Words

Na początek. Otwórz Visual Studio, utwórz nową **Console App (.NET Core)** i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Jeśli masz plik licencji (`Aspose.Words.lic`), skopiuj go do katalogu głównego projektu i załaduj przy uruchamianiu. Zapobiega to pojawianiu się znaku wodnego w trybie darmowej oceny.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Krok 2 – Utwórz nowy pusty dokument

Teraz faktycznie **tworzymy dokument Word przy użyciu Aspose**. Ten obiekt będzie służył jako płótno dla naszego kształtu.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

Klasa `Document` jest punktem wejścia dla wszystkiego — akapity, sekcje i oczywiście obiekty rysunkowe.

---

## Krok 3 – Wstaw prostokąt jako kształt

Gdy dokument jest gotowy, możemy dodać kształt. Tutaj wybieramy prosty prostokąt, ale ta sama logika działa dla kół, linii lub własnych wielokątów.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Dlaczego kształt?** W Aspose.Words obiekt `Shape` może zawierać tekst, obrazy lub po prostu pełnić rolę elementu dekoracyjnego. Dodanie cienia do kształtu jest znacznie prostsze niż próba manipulacji ramką obrazu.

---

## Krok 4 – Skonfiguruj cień (Dodaj cień do kształtu)

To jest sedno samouczka — **jak dodać cień do kształtu** i precyzyjnie dostroić jego wygląd. Właściwość `ShadowFormat` daje pełną kontrolę.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Co robi każda właściwość

| Właściwość | Efekt | Typowe wartości |
|------------|-------|-----------------|
| **Visible** | Włącza/wyłącza cień. | `true` / `false` |
| **Blur** | Zmiękcza krawędzie cienia. | `0` (twardy) do `10` (bardzo miękki) |
| **Distance** | Oddala cień od kształtu. | `1`–`5` punktów jest typowe |
| **Angle** | Kontroluje kierunek przesunięcia. | `0`–`360` stopni |
| **Transparency** | Sprawia, że cień jest częściowo przezroczysty. | `0` (nieprzezroczysty) do `1` (niewidzialny) |

> **Przypadek brzegowy:** Jeśli ustawisz `Transparency` na `1`, cień zniknie całkowicie — przydatne przy przełączaniu go programowo.

---

## Krok 5 – Dodaj kształt do dokumentu

Teraz dołączamy kształt do pierwszego akapitu ciała dokumentu. Aspose automatycznie tworzy akapit, jeśli nie istnieje.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Jeśli Twój dokument już zawiera treść, możesz wstawić kształt w dowolnym węźle używając `InsertAfter` lub `InsertBefore`.

---

## Krok 6 – Zapisz dokument

Na koniec zapisz plik na dysku. Możesz wybrać dowolny obsługiwany format (`.docx`, `.pdf`, `.odt` itp.), ale w tym samouczku pozostaniemy przy natywnym formacie Word.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Otwórz powstały plik `ShadowedShape.docx` w Microsoft Word i zobaczysz prostokąt z miękkim, 45‑stopniowym cieniem, który jest w 30 % przezroczysty — dokładnie tak, jak skonfigurowaliśmy.

---

## Pełny działający przykład

Poniżej znajduje się **kompletny, gotowy do skopiowania i wklejenia** program, który zawiera wszystkie powyższe kroki. Zapisz go jako `Program.cs` i uruchom poleceniem `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Oczekiwany wynik:** Plik o nazwie `ShadowedShape.docx` zawierający pojedynczy prostokąt z subtelnym, półprzezroczystym cieniem skierowanym pod kątem 45°.

---

## Warianty i zaawansowane wskazówki

### Zmiana koloru cienia

Domyślnie cień dziedziczy kolor wypełnienia kształtu, ale możesz ustawić własny kolor:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Wiele kształtów z różnymi cieniami

Jeśli potrzebujesz kilku kształtów, po prostu powtórz kroki tworzenia i konfiguracji. Pamiętaj, aby nadać każdemu kształtowi unikalną nazwę, jeśli zamierzasz odwoływać się do nich później.

### Eksport do PDF z zachowanymi cieniami

Aspose.Words zachowuje efekty cieni przy zapisywaniu do PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Typowe problemy

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|-------|--------------------------|-------------|
| Cień nie jest widoczny | `ShadowFormat.Visible` pozostawiono jako `false` | Ustaw na `true`. |
| Cień wygląda zbyt twardo | `Blur` ustawiono na `0` | Zwiększ `Blur` do 3–6. |
| Cień znika w PDF | Używana jest stara wersja Aspose.Words (< 22.9) | Zaktualizuj do najnowszej biblioteki. |

---

## Podsumowanie

Omówiliśmy **jak dodać cień do kształtu** przy użyciu Aspose.Words, od inicjalizacji dokumentu po precyzyjne dostosowanie rozmycia, odległości, kąta i **stosowanie przezroczystości cienia**. Pełny przykład pokazuje czyste, gotowe do produkcji podejście, które możesz dostosować do dowolnego kształtu lub układu dokumentu.

Masz pytania dotyczące **create word document using aspose** w bardziej złożonych scenariuszach — np. tabel z cieniami lub dynamicznie generowanych kształtów? Dodaj komentarz poniżej lub sprawdź powiązane samouczki o obsłudze obrazów i formatowaniu akapitów w Aspose.Words.

Miłego kodowania i ciesz się nadawaniem swoim dokumentom Word dodatkowego wykończenia wizualnego! 

--- 

![przykład dodawania cienia do kształtu](shadowed_shape.png "przykład dodawania cienia do kształtu")

{{< layout-end >}}

{{< layout-end >}}