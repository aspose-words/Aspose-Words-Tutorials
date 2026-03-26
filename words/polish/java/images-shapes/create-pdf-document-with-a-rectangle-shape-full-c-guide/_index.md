---
category: general
date: 2026-03-25
description: Utwórz dokument PDF w C# i dowiedz się, jak dodać kształt prostokąta,
  ustawić kolor wypełnienia, dostosować rozmiar kształtu oraz ustawić przezroczystość
  kształtu w kilku prostych krokach.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: pl
og_description: Utwórz dokument PDF w C# i zobacz, jak dodać prostokąt, ustawić jego
  kolor wypełnienia, rozmiar oraz przezroczystość, aby uzyskać dopracowany efekt PDF.
og_title: Utwórz dokument PDF z prostokątnym kształtem – samouczek C#
tags:
- C#
- PDF
- Aspose.Words
title: Utwórz dokument PDF z prostokątnym kształtem – Kompletny przewodnik C#
url: /pl/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie dokumentu PDF z kształtem prostokąta – Pełny przewodnik C#

Czy kiedykolwiek potrzebowałeś **utworzyć dokument PDF**, który zawiera niestandardowy kształt, ale nie wiedziałeś od czego zacząć? Nie jesteś sam. Niezależnie od tego, czy tworzysz generator raportów, czy ulotkę marketingową, możliwość programowego rysowania prostokąta, ustawiania jego koloru wypełnienia, modyfikowania rozmiaru i nawet regulacji przezroczystości może sprawić, że Twoje PDF‑y będą wyglądały znacznie bardziej profesjonalnie.

W tym tutorialu przejdziemy krok po kroku przez kompletny, gotowy do uruchomienia przykład w C#, który **tworzy dokument PDF**, **dodaje kształt prostokąta**, **ustawia kolor wypełnienia**, **definiuje rozmiar kształtu** oraz **ustawia przezroczystość kształtu** dla subtelnego cienia zewnętrznego. Po zakończeniu będziesz mieć pojedynczy plik PDF (`shadow.pdf`), który możesz otworzyć, aby zobaczyć rezultat.

> **Pro tip:** To samo podejście działa z innymi typami kształtów (ellipse, line, itp.) — po prostu zamień `ShapeType.RECTANGLE` na potrzebny typ.

---

## Co będzie potrzebne

| Wymaganie | Dlaczego jest ważny |
|--------------|----------------|
| **.NET 6+** (lub .NET Framework 4.6+) | Biblioteka Aspose.Words jest skierowana do nowoczesnych środowisk uruchomieniowych. |
| **Aspose.Words for .NET** pakiet NuGet | Dostarcza klasy `Document`, `Shape`, `ShadowEffect` i powiązane. |
| **IDE C#** (Visual Studio, Rider, VS Code) | Ułatwia debugowanie i uruchamianie przykładu. |
| **Podstawowa znajomość C#** | Zrozumiesz składnię bez konieczności głębokiego zanurzenia się. |

Pakiet możesz zainstalować z poziomu wiersza poleceń:

```bash
dotnet add package Aspose.Words
```

To wszystko — bez dodatkowych DLL‑ów, bez natywnych zależności. Gdy pakiet będzie już zainstalowany, poniższy kod skompiluje się i uruchomi.

---

## Implementacja krok po kroku

Poniżej dzielimy proces na pięć logicznych kroków. Każdy krok ma wyraźny nagłówek (aby modele AI mogły go zindeksować) oraz krótki blok kodu, który możesz skopiować i wkleić.

### ## 1. Utwórz dokument PDF i przygotuj płótno

Pierwszą rzeczą, którą robimy, jest utworzenie obiektu `Document`. Traktuj go jak czyste płótno, które ostatecznie stanie się Twoim plikiem PDF.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Dlaczego?** `Document` przechowuje wszystkie sekcje, akapity i kształty. Rozpoczęcie od czystego obiektu zapewnia brak ukrytych artefaktów z poprzednich uruchomień.

### ## 2. Dodaj kształt prostokąta – ustaw kolor wypełnienia i rozmiar kształtu

Teraz tworzymy prostokąt, nadajemy mu jasny żółty kolor wypełnienia i definiujemy wymiary. To obejmuje zarówno **add rectangle shape**, **set fill color**, jak i **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Uwaga:** Szerokość/wysokość podawane są w punktach (1 punkt = 1/72 cala). Dostosuj te liczby do własnego układu.

### ## 3. Dodaj zewnętrzny cień i ustaw przezroczystość kształtu

Cienie dodają głębi, a kontrolowanie ich nieprzezroczystości jest istotą **set shape transparency**. Poniżej konfigurujemy szary cień zewnętrzny z 30 % przezroczystością.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Dlaczego ustawiać przezroczystość?** Cień o 30 % przezroczystości wygląda subtelnie, zapobiegając „płaskiemu” wyglądowi prostokąta na stronie.

### ## 4. Wstaw kształt do ciała dokumentu

Teraz umieszczamy prostokąt w pierwszym akapicie pierwszej sekcji dokumentu. Ten krok łączy wszystkie elementy.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Przypadek brzegowy:** Jeśli potrzebujesz kształtu na nowej stronie, przed dołączeniem kształtu wstaw `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;`.

### ## 5. Zapisz dokument jako plik PDF

Na koniec zapisujemy strukturę w pamięci do fizycznego pliku PDF. Plik zostanie zapisany w podanym folderze.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Po uruchomieniu programu pojawi się plik o nazwie `shadow.pdf`. Po otwarciu zobaczysz żółty prostokąt z delikatnym szarym cieniem odsuniętym o 4 punkty — dokładnie tak, jak opisuje nasz kod.

> **Oczekiwany wynik:** Jednostronicowy PDF, w którym prostokąt znajduje się w pobliżu lewego górnego rogu strony, jest wypełniony żółtym kolorem, ma rozmiar 200 × 100 punktów i rzuca półprzezroczysty cień zewnętrzny.

---

## Pełny działający przykład (gotowy do kopiowania)

Poniżej znajduje się cały plik źródłowy, gotowy do wklejenia do nowego projektu konsolowego.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Wskazówka:** Zamień `YOUR_DIRECTORY` na ścieżkę absolutną, np. `C:\Temp`, lub względną, taką jak `.\output`. Program utworzy folder, jeśli jeszcze nie istnieje.

---

## Najczęściej zadawane pytania (FAQ)

**Q: Czy mogę zmienić położenie prostokąta na stronie?**  
A: Oczywiście. Ustaw `rectangle.Left` i `rectangle.Top` (oba mierzone w punktach) przed dołączeniem go do akapitu.

**Q: Co jeśli potrzebuję przezroczystego wypełnienia zamiast przezroczystego cienia?**  
A: Użyj `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — pierwszy argument to kanał alfa (0‑255), gdzie 128 daje ~50 % przezroczystości.

**Q: Czy to działa z .NET Core?**  
A: Tak. Aspose.Words obsługuje .NET Standard 2.0+, więc możesz uruchomić ten sam kod na .NET 6, .NET 7 lub .NET Framework 4.6+.

**Q: Jak dodać wiele kształtów?**  
A: Po prostu powtórz kroki 2‑4 dla każdego kształtu, ewentualnie wstawiając je do różnych akapitów lub sekcji.

---

## Zakończenie

Właśnie **utworzyliśmy dokument PDF** od podstaw, **dodaliśmy kształt prostokąta**, **ustawiliśmy jego kolor wypełnienia**, **zdefiniowaliśmy rozmiar** i **dostosowaliśmy przezroczystość kształtu**, aby uzyskać elegancki efekt cienia. Przykładowy kod jest samodzielny, działa w mniej niż minutę i demonstruje podstawowe koncepcje potrzebne do bardziej rozbudowanych układów PDF.

Gotowy na kolejny wyzwanie? Spróbuj zamienić prostokąt na kształt z zaokrąglonymi rogami, osadź obraz wewnątrz kształtu lub automatycznie wygeneruj spis treści. To samo API pozwala warstwować tekst, obrazy i wektory — więc niebo jest granicą.

Jeśli ten przewodnik okazał się przydatny, daj mu gwiazdkę na GitHubie, podziel się nim z kolegą lub zostaw komentarz z własnymi wariacjami. Szczęśliwego kodowania! 

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}