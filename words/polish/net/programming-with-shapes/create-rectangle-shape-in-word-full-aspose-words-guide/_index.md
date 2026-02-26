---
category: general
date: 2026-02-26
description: Utwórz prostokątny kształt w Wordzie przy użyciu Aspose.Words i dowiedz
  się, jak dodać kształt do Worda, zastosować cień do kształtu oraz ustawić przezroczystość
  kształtu w kilka minut.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: pl
og_description: Utwórz prostokątny kształt w Wordzie przy użyciu Aspose.Words. Dowiedz
  się, jak dodać kształt do Worda, zastosować cień do kształtu i szybko ustawić przezroczystość
  kształtu.
og_title: Tworzenie prostokątnego kształtu w Word – Pełny przewodnik Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Utwórz prostokątny kształt w Word – Pełny przewodnik Aspose.Words
url: /pl/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz prostokątny kształt w Word – Pełny przewodnik Aspose.Words

Kiedykolwiek potrzebowałeś **utworzyć prostokątny kształt** w dokumencie Word, ale nie wiedziałeś, od czego zacząć? Nie jesteś sam — wielu programistów napotyka ten problem przy automatyzacji raportów lub faktur. W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który pokaże, jak **dodać kształt do Word**, zastosować subtelną cieniowanie i kontrolować przezroczystość kształtu, wszystko przy użyciu Aspose.Words dla .NET.

Po zakończeniu przewodnika będziesz mieć plik `.docx` zawierający czysty prostokąt z eleganckim cieniem — idealny do brandingu, wyróżnień lub po prostu, aby Twój dokument wyglądał nieco bardziej profesjonalnie. Nie potrzebujesz żadnych zewnętrznych narzędzi, wystarczy kilka linii C#.

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (najnowsza wersja na początek 2026). Pobierz ją z NuGet (`Install-Package Aspose.Words`).
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code z rozszerzeniem C#).
- Podstawowa znajomość składni C# — nic skomplikowanego, tylko typowe instrukcje `using` i tworzenie obiektów.

Jeśli już to masz, świetnie — przejdźmy do działania.

## Utwórz prostokątny kształt – kluczowe kroki

Poniżej znajduje się pełny kod źródłowy. Skopiuj‑wklej go do nowego projektu konsolowego, naciśnij **F5**, a w określonym folderze pojawi się plik `ShadowDemo.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Dlaczego to działa

- **`Document`** jest punktem wejścia; reprezentuje cały plik Word.
- **`Shape`** z `ShapeType.Rectangle` mówi Aspose, że chcemy prostokątny obiekt rysunkowy.
- Ustawienie **`Width`** i **`Height`** nadaje kształtowi określony rozmiar; w przeciwnym razie domyślnie jest to mały placeholder.
- Obiekt **`Shadow`** pozwala precyzyjnie dostroić każdy aspekt wizualny: rozmycie, odległość, kierunek, kolor, przezroczystość i rozprzestrzenianie. To serce *apply shadow to shape*.
- Na koniec **`AppendChild`** wstawia kształt do pierwszego akapitu dokumentu, co jest najprostszym sposobem *add shape to Word* bez konieczności operowania tabelami czy nagłówkami.

Gdy otworzysz `ShadowDemo.docx`, zobaczysz szary prostokąt wygodnie umieszczony w dokumencie, a jego cień będzie nachylony w dół‑w prawo pod kątem 45°. Cień nie jest jednolity; promień rozmycia wygładza krawędzie, a przezroczystość sprawia, że wygląda jak naturalny cień, a nie ostre nakładanie.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(Powyższy obrazek przedstawia końcowy rezultat fragmentu kodu.)*

## Dodaj kształt do dokumentu Word – opcje umiejscowienia

Przykład używa **pierwszego akapitu**, ponieważ jest to najszybszy sposób, aby zobaczyć coś na ekranie. W rzeczywistych scenariuszach możesz chcieć:

- Wstawić kształt do konkretnej **sekcji** lub **nagłówka/stopki**.
- Umieścić go wewnątrz **komórki tabeli**, aby wyrównać go z danymi tabelarycznymi.
- Zastosować **opcji zawijania tekstu** (np. `WrapType.Square`), aby otaczający tekst płynął wokół prostokąta.

Oto szybka wariacja, która umieszcza kształt w nowym akapicie z niestandardowym stylem:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Wskazówka:* Zawsze dodawaj kształt **po** skonfigurowaniu jego właściwości; w przeciwnym razie może być konieczne wywołanie `UpdateLayout`, aby odświeżyć wygląd.

## Zastosuj cień do kształtu – precyzyjne dopasowanie wyglądu

Cienie mogą dramatycznie zmienić estetykę dokumentu. Klasa `Shadow` udostępnia kilka właściwości:

| Property      | Co kontroluje                                      | Typowe wartości |
|---------------|----------------------------------------------------|-----------------|
| `BlurRadius`  | Miękkość krawędzi cienia                           | 2.0 – 10.0      |
| `Distance`    | Odległość cienia od kształtu                       | 1.0 – 8.0       |
| `Direction`   | Kąt w stopniach (0 = lewo, 90 = góra)              | 0 – 360         |
| `Color`       | Kolor cienia (dowolny `System.Drawing.Color`)      | Gray, Black, Custom |
| `Transparency`| Przezroczystość (0 = w pełni nieprzezroczysty, 1 = niewidoczny) | 0.0 – 0.5       |
| `Spread`      | Rozszerzenie cienia przed zastosowaniem rozmycia   | 0.0 – 1.0       |

Jeśli chcesz **subtelny, profesjonalny wygląd**, utrzymaj `BlurRadius` w granicach 4‑6 i `Transparency` blisko 0.2, tak jak w powyższym kodzie. Dla **dramatycznego efektu** zwiększ `Distance` do 6, ustaw `Direction` na 135°, a `Transparency` obniż do 0.05.

## Ustaw przezroczystość kształtu i rozprzestrzenianie cienia

Przezroczystość dotyczy nie tylko cienia; możesz także sprawić, że sam prostokąt będzie częściowo przezroczysty:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Połączenie półprzezroczystego wypełnienia z miękkim cieniem często daje nowoczesny wygląd UI — świetny do pulpitów nawigacyjnych lub makiet projektowych osadzonych w raportach.

### Przypadki brzegowe, na które warto zwrócić uwagę

1. **Starsze wersje Worda** (przed 2007) nie obsługują niektórych właściwości cienia. Jeśli tworzysz pliki `.doc`, rozważ uproszczenie cienia (np. ustaw `BlurRadius` na 0).
2. **Wyświetlacze o wysokiej rozdzielczości DPI** mogą renderować cień nieco inaczej. Przetestuj w docelowym środowisku, jeśli dokładność wizualna jest krytyczna.
3. **Nakładające się kształty** — Aspose renderuje cienie w kolejności, w jakiej zostały dodane. Wstawiaj kształty od tyłu do przodu, aby uniknąć niepożądanego zakrywania.

## Zapisz i zweryfikuj wynik

Metoda `Document.Save` automatycznie wykrywa format wyjściowy na podstawie rozszerzenia pliku. Dla pliku **`.docx`** otrzymujesz format Open XML, który rozumie większość nowoczesnych edytorów Word. Jeśli potrzebujesz wersji **PDF** z taką samą stylizacją, po prostu zmień rozszerzenie:

```csharp
document.Save("ShadowDemo.pdf");
```

Otwierając wygenerowany `ShadowDemo.docx` (lub `ShadowDemo.pdf`) powinieneś zobaczyć czysty **prostokąt z cieniem**, co potwierdza, że pomyślnie *create rectangle shape* i *apply shadow to shape* przy użyciu Aspose.Words.

## Najczęściej zadawane pytania

**P: Czy mogę użyć innego kształtu, np. elipsy?**  
O: Oczywiście. Zamień `ShapeType.Rectangle` na `ShapeType.Ellipse` (lub dowolny inny enum `ShapeType`). Właściwości cienia pozostaną takie same.

**P: Co jeśli potrzebuję, aby prostokąt był klikalny?**  
O: Możesz przypisać hiperłącze do kształtu:

```csharp
rectangleShape.Href = "https://example.com";
```

**P: Czy to działa na .NET 6+?**  
O: Tak. Aspose.Words 23.11 i nowsze w pełni wspierają .NET 6, .NET 7 oraz .NET 8. Wystarczy odwołać się do odpowiedniego pakietu NuGet.

**P: Jak zmienić kolor cienia, aby pasował do mojej marki?**  
O: Użyj dowolnego `System.Drawing.Color`, który Ci odpowiada:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Podsumowanie

Omówiliśmy wszystko, co potrzebne, aby **utworzyć prostokątny kształt** w dokumencie Word, **dodać kształt do Word**, **zastosować cień do kształtu** oraz **ustawić przezroczystość kształtu**. Pełny, uruchamialny kod znajduje się na początku tej strony, a wyjaśnienia powinny dać Ci wystarczającą pewność, aby modyfikować rozmiary, kolory i parametry cienia w dowolnym projekcie.

Gotowy na kolejny krok? Wypróbuj:

- Wielokrotne nakładanie kształtów, aby uzyskać efekt odznaki.
- Dynamiczne ustalanie rozmiaru w zależności od zawartości dokumentu (np. obliczanie szerokości na podstawie kolumny tabeli).
- Eksport dokumentu do PDF lub HTML przy zachowaniu cienia.

Śmiało zostaw komentarz, jeśli napotkasz problemy, lub podziel się własnymi wariacjami tematu „prostokąt z cieniem”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}