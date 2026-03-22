---
category: general
date: 2026-03-22
description: Utwórz kształt prostokąta w C# i dodaj cień do kształtu za pomocą Aspose.Words.
  Dowiedz się, jak dodać cień, jak utworzyć prostokąt i jak ustawić właściwości cienia.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: pl
og_description: Utwórz kształt prostokąta w C# i dodaj cień do kształtu przy użyciu
  Aspose.Words. Przewodnik krok po kroku opisujący, jak dodać cień, jak utworzyć prostokąt
  i jak ustawić cień.
og_title: Utwórz prostokątny kształt z cieniem w C# – kompletny przewodnik
tags:
- Aspose.Words
- C#
- Document Automation
title: Utwórz prostokątny kształt z cieniem w C# przy użyciu Aspose.Words
url: /pl/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz prostokątny kształt z cieniem w C# przy użyciu Aspose.Words

Czy kiedykolwiek potrzebowałeś **create rectangle shape** w dokumencie Word, ale nie byłeś pewien, jak dodać mu subtelny cień? Nie jesteś sam — wielu programistów napotyka ten problem, gdy po raz pierwszy zaczyna pracę z automatyzacją dokumentów. W tym przewodniku pokażemy dokładnie, jak **add shadow to shape** przy użyciu Aspose.Words, a także odpowiemy na pytania „**how to add shadow**”, „**how to create rectangle**” i „**how to set shadow**”.

Zaczniemy od czystego `Document`, narysujemy prostokąt, włączymy jego cień, dostosujemy rozmycie, odległość, kąt i kolor, a na końcu zapisujemy plik. Po zakończeniu będziesz mieć gotowy do użycia `.docx`, który pokazuje szary prostokąt unoszący się tuż nad stroną. Bez tajemnic, po prostu prosty kod, który możesz skopiować i wkleić do dowolnego projektu .NET.

## Wymagania wstępne

* **Aspose.Words for .NET** (najnowsza wersja na marzec 2026). Możesz ją pobrać z NuGet przy użyciu `Install-Package Aspose.Words`.
* Środowisko programistyczne .NET – Visual Studio, Rider lub nawet VS Code z rozszerzeniem C# działa bez problemu.
* Podstawowa znajomość C# – nic skomplikowanego, wystarczy umiejętność stworzenia aplikacji konsolowej lub WinForms.

To wszystko. Bez dodatkowych bibliotek, bez ukrytych kroków. Gotowy? Zaczynajmy.

## Krok 1: Zainicjalizuj nowy pusty dokument

Aby **create rectangle shape**, najpierw potrzebujemy kontenera – obiektu `Document` – który reprezentuje plik Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

Klasa `Document` jest punktem wejścia dla wszystkiego, co robi Aspose.Words. Traktuj ją jak czyste płótno; bez niej nie możesz dodać żadnych kształtów, tabel ani tekstu.

## Krok 2: Utwórz prostokąt, który będzie nosił cień

Teraz pokażemy **how to create rectangle** poprzez utworzenie `Shape` typu `Rectangle`. Ustawiamy także jego rozmiar w punktach (1 punkt ≈ 1/72 cala).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Dlaczego wybrać 200 × 100 punktów? To przyzwoity rozmiar na demonstrację – wystarczająco duży, aby wyraźnie zobaczyć cień, ale nie tak ogromny, by przytłoczyć stronę. Śmiało dostosuj te liczby do swojego układu.

## Krok 3: Włącz efekt cienia i skonfiguruj jego wygląd

Oto sedno tutorialu: właściwości **how to add shadow** i **how to set shadow**. Aspose.Words udostępnia obiekt `Shadow` dla każdego kształtu, umożliwiając włączanie efektu i dostosowywanie parametrów wizualnych.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** rozmywa krawędzie – wyższa wartość sprawia, że cień wygląda bardziej rozproszony.
* **Distance** oddala cień dalej od prostokąta.
* **Angle** określa, skąd wydaje się pochodzić światło; 45° daje diagonalny, naturalny wygląd.
* **Color** pozwala wybrać dowolny `System.Drawing.Color`. Szary jest bezpiecznym domyślnym, ale możesz użyć odważnego `Color.Black` lub subtelnego `Color.LightGray`.

Wskazówka: Jeśli ustawisz `Enabled = false`, wszystkie pozostałe ustawienia cienia są ignorowane, więc zawsze sprawdzaj tę flagę.

## Krok 4: Wstaw kształt do treści dokumentu

Gdy prostokąt jest gotowy i jego cień skonfigurowany, musimy umieścić go w dokumencie. Najprostszy sposób to dołączenie go do pierwszego akapitu pierwszej sekcji.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Jeśli Twój dokument już zawiera tekst, możesz znaleźć konkretny `Paragraph` lub nawet komórkę `Table` i wstawić tam kształt. Metoda `AppendChild` jest wszechstronna – działa z każdym typem `Node`.

## Krok 5: Zapisz dokument i zweryfikuj wynik

Na koniec zapisujemy plik na dysku. Zmień ścieżkę na dowolną; folder musi istnieć, w przeciwnym razie otrzymasz wyjątek.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Otwórz powstały `ShadowedRectangle.docx` w Microsoft Word (lub LibreOffice) i powinieneś zobaczyć szary prostokąt z wyraźnym, diagonalnym cieniem przesuwającym się w dół‑w prawo. Jeśli cień wydaje się zbyt słaby, zwiększ `BlurRadius` lub `Distance` i ponownie uruchom kod – eksperymentowanie jest częścią zabawy.

![Przykład tworzenia prostokątnego kształtu z cieniem](rectangle-shadow.png){alt="Przykład tworzenia prostokątnego kształtu z cieniem"}

### Oczekiwany wynik

* Dokument Word jednosktranicowy.
* Szary prostokąt 200 × 100 punktów umieszczony w lewym górnym rogu strony.
* Subtelny szary cień przesunięty o 8 pikseli pod kątem 45°, rozmyty o 5 pikseli.

## Jak dodać cień do kształtu – głębsze zanurzenie

Możesz się zastanawiać, *„Czy mogę animować cień lub zmieniać go w zależności od danych wejściowych użytkownika?”* Choć Aspose.Words nie obsługuje animacji, możesz programowo dostosować właściwości cienia przed zapisem, tworząc w praktyce wiele wersji tego samego dokumentu o różnych wyglądach. Na przykład, iterując po kolekcji kolorów:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Ten mały fragment pokazuje **how to set shadow** dynamicznie — świetne do generowania raportów tematycznych.

## Jak utworzyć prostokąt – alternatywne kształty

Jeśli potrzebujesz prostokąta z zaokrąglonymi rogami, po prostu zmień `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Lub, aby uzyskać idealny kwadrat, ustaw `Width` równy `Height`. Te same właściwości cienia mają zastosowanie, więc masz już pokryte **how to add shadow** dla dowolnego wybranego kształtu.

## Typowe pułapki i rozwiązywanie problemów

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Cień nie pojawia się | `Shadow.Enabled` pozostawiony jako `false` | Ustaw `rectangleShape.Shadow.Enabled = true;` |
| Cień wygląda zbyt ostry | `BlurRadius` ustawiony na 0 | Zwiększ `BlurRadius` przynajmniej do 3 |
| Dokument wyrzuca `FileNotFoundException` przy zapisie | Folder docelowy nie istnieje | Utwórz folder najpierw lub użyj prawidłowej ścieżki |
| Kształt jest niewidoczny | Width/Height ustawione na 0 | Upewnij się, że oba wymiary są > 0 |

Śledzenie tych problemów chroni Cię przed klasycznym momentem „dlaczego mój kształt się nie wyświetla?”.

## Podsumowanie – co osiągnęliśmy

* **Create rectangle shape** w nowym dokumencie Word przy użyciu Aspose.Words.  
* **Add shadow to shape** poprzez przełączanie flagi `Shadow.Enabled` i dostosowywanie rozmycia, odległości, kąta i koloru.  
* Zademonstrowano **how to add shadow**, **how to create rectangle** oraz **how to set shadow** w czystym, wielokrotnego użytku fragmencie kodu.  
* Dostarczono kompletny, gotowy do uruchomienia przykład, który możesz wkleić do dowolnego projektu C#.

## Co dalej?

* **How to add shadow to images** – to samo API `Shadow` działa dla `ShapeType.Image`.
* **Combining multiple shapes** – twórz diagramy przepływu lub infografiki bezpośrednio w Wordzie.
* **Exporting to PDF** – wywołaj `document.Save("output.pdf")` po dodaniu cieni, aby uzyskać wersję do druku.

Śmiało eksperymentuj z różnymi kolorami, kątami lub nawet wypełnieniami gradientowymi. API jest na tyle elastyczne, że pozwala tworzyć profesjonalnie wyglądające dokumenty bez ręcznego otwierania Worda.

---

Miłego kodowania! Jeśli napotkasz jakiekolwiek problemy, zostaw komentarz poniżej lub sprawdź fora Aspose.Words – społeczność szybko pomaga.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}