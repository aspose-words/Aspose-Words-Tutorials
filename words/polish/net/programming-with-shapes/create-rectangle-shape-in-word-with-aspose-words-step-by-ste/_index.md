---
category: general
date: 2025-12-29
description: Utwórz prostokątny kształt w dokumencie Word przy użyciu Aspose.Words
  C#. Dowiedz się, jak ustawić przezroczystość kształtu, kolor cienia i zapisać dokument
  Word bez wysiłku.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: pl
og_description: Utwórz prostokątny kształt w dokumencie Word przy użyciu Aspose.Words
  C#. Ten przewodnik pokazuje, jak ustawić przezroczystość kształtu, ustawić kolor
  cienia i zapisać dokument Word.
og_title: Utwórz kształt prostokąta w Word – Kompletny samouczek Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Tworzenie prostokątnego kształtu w Wordzie przy użyciu Aspose.Words – Przewodnik
  krok po kroku
url: /pl/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie prostokątnego kształtu w Word – Kompletny poradnik Aspose.Words

Kiedykolwiek potrzebowałeś **utworzyć prostokątny kształt** w dokumencie Word, ale nie wiedziałeś od czego zacząć? Nie jesteś sam; wielu programistów napotyka ten problem przy automatyzacji raportów lub faktur. W tym przewodniku przejdziemy krok po kroku przez proces tworzenia prostokątnego kształtu, ustawiania przezroczystości kształtu, ustawiania koloru cienia oraz w końcu **zapisania dokumentu Word** przy użyciu Aspose.Words for .NET.

Omówimy wszystko – od początkowego obiektu dokumentu po końcowy plik `.docx` na dysku, więc na końcu będziesz w stanie **tworzyć dokumenty Word** programowo bez zgadywania. Bez zewnętrznych odwołań, tylko samodzielne rozwiązanie, które możesz skopiować‑wkleić do swojego projektu.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa także z .NET Framework 4.7+)
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Podstawowa znajomość składni C#
- Ulubione IDE (Visual Studio, Rider, VS Code itp.)

> **Pro tip:** Jeśli używasz darmowej wersji próbnej Aspose.Words, biblioteka doda znak wodny do pliku wyjściowego. W wersji produkcyjnej potrzebna będzie ważna licencja.

## Krok 1: Inicjalizacja dokumentu i buildera

Pierwszą rzeczą, którą robimy, jest stworzenie nowego, pustego dokumentu Word oraz `DocumentBuilder`, który pozwala wstawiać zawartość. Pomyśl o builderze jako o wirtualnym piórze rysującym na stronie.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Dlaczego to ważne:** Bez `DocumentBuilder` musiałbyś manipulować drzewem węzłów niskiego poziomu bezpośrednio, co jest podatne na błędy i trudniejsze do odczytania.

## Krok 2: Utworzenie prostokątnego kształtu

Teraz faktycznie **tworzymy prostokątny kształt**. Metoda `InsertShape` przyjmuje wyliczenie `ShapeType`, szerokość i wysokość (w punktach). Zwrócony obiekt `Shape` pozwala później dostosować właściwości wizualne.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

W tym momencie prostokąt jest czarnym, pełnym pudełkiem zakotwiczonym w bieżącym akapicie. Możesz go później przesuwać, zmieniać rozmiar lub nawet obracać, jeśli zajdzie taka potrzeba.

![utwórz prostokątny kształt z cieniem](/images/rectangle-shadow.png "Dokument Word pokazujący prostokątny kształt z szarym cieniem")

*Tekst alternatywny obrazu: utwórz prostokątny kształt z cieniem w dokumencie Word*

## Krok 3: Ustawienie przezroczystości kształtu

Przezroczystość to poziom „przezroczystości” wypełnienia kształtu. Aspose.Words używa właściwości `Transparency` w zakresie od `0.0` (nieprzezroczysty) do `1.0` (całkowicie przezroczysty). Tutaj **ustawiamy przezroczystość kształtu** na 40 %, aby podtekst pozostał czytelny.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Przypadek brzegowy:** Jeśli potrzebujesz całkowicie niewidzialnego kształtu, ale chcesz, aby cień się pojawił, ustaw `Transparency` na `1.0` i nadaj kształtowi niezerową szerokość konturu.

## Krok 4: Konfiguracja cienia

Subtelny cień dodaje głębi. **Ustawimy kolor cienia** na średnią szarość, dostosujemy promień rozmycia i przesuniemy go o kilka punktów w poziomie i pionie.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Dlaczego to ważne:** Cień, który jest zbyt ostry lub zbyt ciemny, może wyglądać jak artefakt drukarski. Dostosuj `Blur` i `Transparency`, aż będzie wyglądał naturalnie.

## Krok 5: Zapisanie dokumentu Word

Na koniec **zapisujemy dokument Word** na dysku. Metoda `` automatycznie określa format pliku na podstawie rozszerzenia; `.docx` to nowoczesny format OpenXML.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Jeśli folder nie istnieje, Aspose.Words zgłosi `ArgumentException`. Upewnij się, że ścieżka jest prawidłowa lub utwórz katalog wcześniej.

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który łączy wszystkie kroki. Skopiuj go do nowego projektu konsolowego i naciśnij **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Oczekiwany rezultat

Otwórz `ShadowRectangle.docx` w Microsoft Word. Powinieneś zobaczyć jasno‑szary prostokąt z miękkim, lekko przesuniętym cieniem, oba renderowane z 40 % przezroczystością. Kształt znajduje się na pustej stronie, gotowy na dodatkową treść.

## Częste pytania i warianty

**Co zrobić, jeśli potrzebuję innego kształtu?**  
Zamień `ShapeType.Rectangle` na dowolną inną wartość wyliczenia (`Ellipse`, `Triangle`, `Star` itp.). Reszta kodu pozostaje bez zmian.

**Czy mogę zmienić kolor konturu?**  
Tak — użyj `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` i opcjonalnie ustaw `rectangleShape.StrokeWeight = 1.5;`.

**Jak umieścić kształt w określonym miejscu na stronie?**  
Ustaw `rectangleShape.WrapType = WrapType.None;`, a następnie dostosuj właściwości `rectangleShape.Left` i `rectangleShape.Top` (wartości w punktach).

**Czy można dodać tekst wewnątrz prostokąta?**  
Oczywiście. Po utworzeniu kształtu możesz wywołać `rectangleShape.AppendChild(new Paragraph(document))`, a następnie dodać `Run` z własnym tekstem. Pamiętaj, aby ustawić właściwości `rectangleShape.TextBox`, jeśli chcesz bardziej zaawansowane formatowanie.

## Pro tipy i pułapki

- **Licencja od razu:** Jeśli zapomnisz zastosować licencję, Aspose.Words wstawi znak wodny na pierwszej stronie, co może wprowadzać w błąd podczas testów.
- **Wskazówka wydajnościowa:** Generując wiele dokumentów w pętli, ponownie używaj jednej instancji `Document` i wywołuj `document.RemoveAllChildren();` po każdym zapisie, aby uniknąć nadmiernego obciążenia GC.
- **Widoczność cienia:** Na ekranach o niskiej rozdzielczości subtelny cień może wydawać się niewidoczny. Zwiększ `Blur` lub `OffsetX/Y` w celu debugowania, a potem przytn dla wersji produkcyjnej.

## Kolejne kroki

Teraz, gdy wiesz jak **utworzyć prostokątny kształt**, **ustawić przezroczystość kształtu**, **ustawić kolor cienia** i **zapisać dokument Word**, rozważ rozszerzenie poradnika:

- Dodaj wiele kształtów i pogrupuj je.
- Wstaw prostokąt do komórki tabeli, aby uzyskać układ raportu.
- Połącz kształt z `DocumentBuilder.InsertHtml`, aby nałożyć treść stylizowaną HTML‑owo.
- Zbadaj inne efekty wizualne, takie jak `Glow` czy `Reflection`, aby uzyskać bardziej UI‑like dokumenty.

Eksperymentuj, łam rzeczy, a potem udoskonalaj — generowanie dokumentów programowo to plac zabaw, gdzie projektowanie wizualne spotyka się z kodem.

---

*Miłego kodowania! Jeśli napotkasz jakiekolwiek problemy, zostaw komentarz poniżej, a pomożemy rozwiązać je razem.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}