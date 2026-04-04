---
category: general
date: 2026-04-04
description: Utwórz kształt prostokąta w C# przy użyciu Aspose.Words i dowiedz się,
  jak dodać cień, zastosować rozmycie cienia oraz uczynić cień przezroczystym – przewodnik
  krok po kroku.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: pl
og_description: Utwórz kształt prostokąta w C# przy użyciu Aspose.Words. Dowiedz się,
  jak dodać cień, zastosować rozmycie cienia i uczynić cień przezroczystym w zwięzłym
  samouczku.
og_title: Utwórz kształt prostokąta i jak dodać cień w C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Tworzenie kształtu prostokąta i jak dodać cień w C#
url: /pl/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz prostokątny kształt i jak dodać cień w C#

Czy kiedykolwiek potrzebowałeś **utworzyć kształt prostokąta** w dokumencie Word, ale nie byłeś pewien, jak dodać mu subtelny cień typu drop‑shadow? Nie jesteś sam. W wielu scenariuszach raportowania lub brandingu prosty prostokąt z miękkim, półprzezroczystym cieniem może sprawić, że układ będzie wyglądał elegancko bez dużego wysiłku.

W tym samouczku przeprowadzimy Cię przez **jak utworzyć dokument** przy użyciu Aspose.Words, a następnie pokażemy **jak dodać cień**, **zastosować rozmycie cienia** i nawet **uczynić cień przezroczystym**. Po zakończeniu będziesz mieć gotowy do uruchomienia fragment C# generujący plik *.docx* z ładnie zacienionym prostokątem — wszystko w kilka minut.

## Czego będziesz potrzebować

- .NET 6 lub nowszy (API działa również z .NET Framework 4.6+)
- Aspose.Words for .NET (bezpłatna wersja próbna działa w tym przykładzie)
- Edytor kodu – Visual Studio, VS Code, Rider, cokolwiek wolisz
- Podstawowa znajomość C# – nic skomplikowanego, po prostu możliwość uruchomienia aplikacji konsolowej

Jeśli masz to wszystko, możemy od razu przejść do rozwiązania.

## Krok 1 – Jak utworzyć dokument i zainicjować płótno

Na początek: potrzebujesz pustego obiektu `Document`. Traktuj go jak pustą kartkę papieru, którą Aspose.Words później przekształci w plik Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Dlaczego tworzymy instancję `Document` zamiast wczytywać szablon? Rozpoczęcie od zera zapewnia, że żadne ukryte style ani sekcje nie będą kolidować z naszym prostokątem. Dodatkowo utrzymuje rozmiar pliku niewielkim – dobra praktyka przy generowaniu wielu dokumentów w pętli.

## Krok 2 – Utwórz kształt prostokąta (rdzeń naszego głównego słowa kluczowego)

Teraz faktycznie **tworzymy kształt prostokąta**. Klasa `Shape` jest elastyczna; określasz jej typ (Rectangle), rozmiar oraz sposób otaczania tekstem.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Zauważ użycie składni inicjalizatora obiektów – jest zwięzła i zmniejsza ryzyko zapomnienia o ustawieniu właściwości później. Prostokąt zostanie umieszczony w pierwszym akapicie, który dodamy w następnym kroku.

## Krok 3 – Jak dodać cień i dostosować jego wygląd

Dodanie cienia to nie tylko jedna linia kodu; masz kilka właściwości do dostosowania. To właśnie tutaj wchodzą w grę drugorzędne słowa kluczowe **apply blur to shadow** i **make shadow transparent**.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Krótka uwaga dotycząca liczb: `BlurRadius` równy 5 daje delikatne rozmycie; zwiększ go do 10, aby uzyskać miększy efekt, lub zmniejsz do 2, aby uzyskać wyraźną krawędź. Wartość `Transparency` waha się od 0 (nieprzezroczysty) do 1 (niewidzialny). Dostosuj ją w zależności od wymagań kontrastu Twojej marki.

### Porada

Jeśli kiedykolwiek potrzebujesz kolorowego cienia (np. korporacyjnego niebieskiego), po prostu zamień `Color.DarkGray` na `Color.FromArgb(80, 0, 120, 215)`. Pierwszy argument to kanał alfa – utrzymaj go niskim dla subtelności.

## Krok 4 – Wstaw kształt do dokumentu

Gdy prostokąt i jego cień są gotowe, umieszczamy go w pierwszym akapicie dokumentu. Ten krok zapewnia, że kształt pojawi się na samym początku pliku.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Dlaczego pierwszy akapit? To bezpieczne domyślne rozwiązanie, które działa nawet, gdy dokument jest całkowicie pusty. Jeśli masz określone miejsce (np. po nagłówku), znajdziesz ten węzeł i wstawisz tam kształt.

## Krok 5 – Zapisz plik i zweryfikuj wynik

Na koniec zapisujemy dokument na dysku. Możesz wybrać dowolną ścieżkę; po prostu upewnij się, że folder istnieje.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Kiedy otworzysz *ShadowRectangle.docx* w Microsoft Word, powinieneś zobaczyć prostokąt o wymiarach 200 × 100 punktów z ciemnoszarym, lekko rozmytym, w 30 % przezroczystym cieniem, przesuniętym o trzy punkty w prawo i w dół. Efekt jest subtelny, ale dodaje głębi do wcześniej płaskich układów.

![utwórz kształt prostokąta z cieniem w Aspose.Words](https://example.com/placeholder-image.png "utwórz kształt prostokąta z cieniem w Aspose.Words")

*Tekst alternatywny obrazu:* **utwórz kształt prostokąta z cieniem w Aspose.Words** – obraz przedstawia końcowy dokument z zacienionym prostokątem.

## Typowe warianty i przypadki brzegowe

### Dynamiczna zmiana koloru cienia

Jeśli Twoja aplikacja obsługuje motywy, możesz pobrać kolor cienia z pliku konfiguracyjnego:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Tworzenie kształtu nie‑inline

Czasami chcesz, aby prostokąt unosił się nad tekstem. Zmień `WrapType` na `WrapType.Square` i ustaw `RelativeHorizontalPosition` na `RelativeHorizontalPosition.Margin`, aby uzyskać większą kontrolę.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Obsługa wielu stron

Jeśli potrzebujesz prostokąta na każdej stronie, przeiteruj `doc.Sections` i dołącz sklonowany kształt do pierwszego akapitu każdej sekcji. Pamiętaj, aby wywołać `rect.Clone(true)`, aby również skopiować ustawienia cienia.

## Podsumowanie – Co osiągnęliśmy

- **Utworzono kształt prostokąta** przy użyciu Aspose.Words
- **Jak dodać cień** z kolorem, przesunięciem, rozmyciem i przezroczystością
- Zademonstrowano **apply blur to shadow** i **make shadow transparent**
- Zapisano plik Word, który można od razu otworzyć

Wszystko to osiągnięto przy użyciu zaledwie kilku linii kodu, co dowodzi, że zaawansowane poprawki wizualne nie zawsze wymagają ciężkich bibliotek graficznych.

## Co dalej?

- Eksperymentuj z innymi `ShapeType` (Ellipse, Cloud itp.) i zobacz, jak zachowują się cienie.
- Połącz prostokąt z polami tekstowymi, aby tworzyć opisane adnotacje.
- Zanurz się w szablony **how to create document**, które już zawierają miejsca na kształty, a następnie wypełnij je programowo.

Śmiało dostosowuj promień rozmycia, kolor lub przezroczystość, aż cień będzie idealnie pasował do Twojego języka projektowego. API jest wyrozumiałe, a zmiany są widoczne od razu po ponownym uruchomieniu aplikacji konsolowej.

Miłego kodowania i niech Twoje dokumenty zawsze mają ten dodatkowy odcień głębi!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}