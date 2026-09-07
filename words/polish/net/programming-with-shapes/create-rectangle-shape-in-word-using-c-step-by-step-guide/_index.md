---
category: general
date: 2026-01-03
description: Utwórz prostokątny kształt w Wordzie przy użyciu C# i dodaj cień do kształtu.
  Dowiedz się, jak wstawić kształt w Wordzie, dodać cień do kształtu oraz generować
  dokumenty Worda programowo.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: pl
og_description: Utwórz prostokątny kształt w Wordzie przy użyciu C# i dodaj cień do
  kształtu. Skorzystaj z tego przewodnika, aby wstawić kształt w Wordzie, skonfigurować
  cienie i generować dokumenty programowo.
og_title: Tworzenie prostokątnego kształtu w Wordzie przy użyciu C# – Kompletny poradnik
tags:
- C#
- Word Automation
- Aspose.Words
title: Tworzenie prostokątnego kształtu w Wordzie przy użyciu C# – Przewodnik krok
  po kroku
url: /pl/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz prostokątny kształt w Wordzie przy użyciu C# – Kompletny poradnik

Czy kiedykolwiek potrzebowałeś **create rectangle shape** w dokumencie Word, ale nie wiedziałeś od czego zacząć? Nie jesteś sam — wielu programistów napotyka ten sam problem, gdy chcą **add shadow to shape**, aby uzyskać wykończenie. W tym poradniku przeprowadzimy Cię przez dokładne kroki, aby **insert shape in Word**, zastosować subtelną cieniowanie i w końcu **c# generate word document** pliki, które możesz udostępnić użytkownikom.

Omówimy wszystko, od konfiguracji projektu po dopasowanie właściwości cienia, a zakończymy gotowym przykładem kodu. Bez zbędnych wstępów, tylko praktyczne elementy, które pozwolą wykonać zadanie.

## Czego się nauczysz

- Jak **create rectangle shape** przy użyciu Aspose.Words (lub Open XML) w C#
- Dokładne właściwości potrzebne do **add shadow to shape** dla głębi
- Gdzie umieścić kształt przy użyciu `DocumentBuilder`
- Jak zapisać plik, aby otwierał się poprawnie w Microsoft Word
- Wskazówki, pułapki i warianty dla rzeczywistych scenariuszy

### Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa na .NET Core i .NET Framework)
- Pakiet NuGet, który może manipulować plikami Word — użyjemy **Aspose.Words for .NET**, ponieważ jego API jest zwięzłe. Jeśli wolisz Open XML SDK, koncepcje są takie same, różnią się jedynie klasy.
- Visual Studio, VS Code lub dowolne IDE C#, które lubisz

> **Pro tip:** Jeśli masz ograniczony budżet, Aspose oferuje darmową wersję próbną, idealną do nauki. Po prostu zamień linię licencji na komentarz podczas testów.

## Krok 1: Zainstaluj bibliotekę do przetwarzania Word

Najpierw dodaj bibliotekę do swojego projektu. Otwórz terminal w folderze rozwiązania i uruchom:

```bash
dotnet add package Aspose.Words
```

Jeśli używasz Open XML SDK, polecenie będzie wyglądało tak: `dotnet add package DocumentFormat.OpenXml`. Reszta tego przewodnika zakłada użycie Aspose.Words, ale zamiana wywołań API jest prosta.

## Krok 2: Utwórz nowy pusty dokument

Teraz, gdy biblioteka jest gotowa, możemy **create rectangle shape** zaczynając od czystego obiektu `Document`. Traktuj to jak świeże płótno.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` daje nam wysokopoziomowy sposób wstawiania treści bez zagłębiania się w niskopoziomowe drzewa węzłów.

## Krok 3: Wstaw prostokątny kształt

Mając `builder` w ręku, możemy **insert shape in Word**. Metoda `InsertShape` przyjmuje typ kształtu oraz jego wymiary (szerokość, wysokość) w punktach.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

W tym momencie prostokąt pojawia się w dokumencie, ale wygląda nieco płasko. Tu wchodzi kolejny krok.

## Krok 4: Dodaj cień do kształtu

Cienie nadają kształtowi poczucie głębi. Obiekt `Shadow` pozwala precyzyjnie dostroić rozmycie, odległość, kąt, kolor i przezroczystość. Poniżej pełna konfiguracja, która sprawdza się w większości raportów.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Dlaczego te wartości?**  
- **BlurRadius** o wartości `5.0` utrzymuje krawędź gładką, nie rozmytą.  
- **Distance** o wartości `4.0` przesuwa cień wystarczająco, aby był zauważalny.  
- **Angle** `45` naśladuje naturalne oświetlenie z góry‑lewej, co jest powszechną konwencją UI.  
- **Transparency** `0.3` zapobiega przytłoczeniu wypełnienia kształtu przez cień.

Jeśli potrzebujesz bardziej dramatycznego efektu, zwiększ `BlurRadius` i zmniejsz `Transparency`. Dla subtelnego, prawie niewidocznego podniesienia, odwróć te liczby.

## Krok 5: Zapisz dokument

Na koniec zapisz plik na dysku. Metoda `Save` wykrywa format na podstawie rozszerzenia pliku, więc `.docx` daje nowoczesny format Worda.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Otwórz `ShadowRectangle.docx` w Microsoft Word, a zobaczysz wyraźny prostokąt z delikatnym cieniem — dokładnie to, czego oczekiwałeś, pytając „**how to add shape**” z profesjonalnym wykończeniem.

![Utwórz prostokątny kształt z cieniem w Wordzie](placeholder-image.png "Utwórz prostokątny kształt z cieniem w Wordzie")

*Tekst alternatywny obrazu: Utwórz prostokątny kształt z cieniem w Wordzie*

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny, gotowy do uruchomienia program. Skopiuj‑wklej do aplikacji konsolowej i naciśnij **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Oczekiwany rezultat

- Wygenerowany `ShadowRectangle.docx` zawiera **one rectangle shape** wyśrodkowany w miejscu, gdzie znajdował się kursor.  
- Prostokąt wyświetla **soft, 30 % transparent black shadow** przesunięty pod kątem 45°.  
- Nie dodano żadnej innej treści, co utrzymuje plik lekki i łatwy do osadzenia w większych raportach.

## Często zadawane pytania i przypadki brzegowe

### Co zrobić, jeśli potrzebuję innego kształtu?

Zamień `ShapeType.Rectangle` na dowolną inną wartość wyliczenia `ShapeType` (np. `Ellipse`, `Triangle`). API cienia działa tak samo, więc możesz ponownie użyć tej konfiguracji.

### Jak zmienić kolor wypełnienia?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Czy mogę dodać kształt do konkretnego akapitu?

Tak. Przenieś `DocumentBuilder` do docelowego akapitu za pomocą `builder.MoveToParagraph(index)` przed wywołaniem `InsertShape`. Dzięki temu kształt pojawi się dokładnie tam, gdzie go potrzebujesz.

### Co z starszymi formatami Worda (.doc)?

Po prostu zmień rozszerzenie:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Funkcja cienia jest obsługiwana w Word 2003 i nowszych, więc efekt będzie widoczny.

### Używanie Open XML SDK zamiast Aspose?

Kroki pozostają takie same: utwórz `WordprocessingDocument`, dodaj element `Drawing`, ustaw właściwości `<a:shadow>`. XML jest bardziej rozbudowany, ale te same koncepcje (rozmiar, rozmycie, odległość, kąt) mają zastosowanie.

## Wskazówki, aby uniknąć pułapek

- **Nie zapomnij o licencji**, jeśli używasz płatnej wersji Aspose; w przeciwnym razie otrzymasz znak wodny.  
- **Jednostki to punkty**, nie piksele. Typowy piksel ekranu ≈ 0.75 pt, więc dostosuj wymiary odpowiednio.  
- **Właściwości cienia są ignorowane**, jeśli `WrapType` kształtu jest ustawiony na `Inline`. Użyj `WrapType = WrapType.Square` dla kształtów pływających, które respektują renderowanie cienia.  
- **Zapisywanie na udostępnionym dysku sieciowym** może wymagać odpowiednich uprawnień; zawsze najpierw przetestuj ścieżkę.

## Zakończenie

Teraz wiesz, jak **create rectangle shape** w dokumencie Word przy użyciu C#, **add shadow to shape**, oraz **c# generate word document** pliki, które wyglądają profesjonalnie od razu po wygenerowaniu. Główne kroki — instalacja biblioteki, utworzenie `Document`, wstawienie kształtu, skonfigurowanie cienia i zapis — są proste do zapamiętania i można je łatwo dostosować do innych kształtów, kolorów czy dynamicznych danych.

Co dalej? Spróbuj warstwować wiele kształtów, osadzać obrazy lub generować pełny raport z tabelami i wykresami. Możesz także eksperymentować z formatowaniem warunkowym — zmieniając intensywność cienia w zależności od wartości danych — aby Twoje dokumenty były nie tylko funkcjonalne, ale i wizualnie atrakcyjne.

Śmiało eksperymentuj, a jeśli napotkasz problemy, zostaw komentarz poniżej. Miłego kodowania i niech Twoje dokumenty Word zawsze mają idealny cień!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}