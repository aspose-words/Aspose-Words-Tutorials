---
category: general
date: 2026-01-08
description: Utwórz pusty dokument Word i dowiedz się, jak dodać cień do prostokątnego
  kształtu. Wstaw pliki Word z kształtami i dodaj cień kształtu w C# przy użyciu Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: pl
og_description: Utwórz pusty dokument Word i zobacz, jak dodać cień do prostokątnego
  kształtu przy użyciu C#. Pełny kod, wyjaśnienia i wskazówki.
og_title: Utwórz pusty dokument Word – Dodaj prostokąt z cieniem
tags:
- Aspose.Words
- C#
- Document Automation
title: Utwórz pusty dokument Word z cieniowanym prostokątem – przewodnik krok po kroku
url: /pl/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word z prostokątem z cieniowaniem – Pełny samouczek

Czy kiedykolwiek potrzebowałeś **tworzyć puste pliki Word** programowo i następnie ozdobić je ładnym prostokątem z cieniowaniem? Nie jesteś sam. Wielu programistów napotyka problem, gdy odkrywają, że wstawianie kształtów i stosowanie efektów nie jest tak proste, jak wpisywanie tekstu.  

W tym przewodniku przeprowadzimy Cię przez cały proces — od utworzenia pustego pliku `.docx` po **dodanie cienia** do obiektu **rectangle shape word**, a na końcu **wstawienie zawartości shape word** z dopracowanym efektem **add shape shadow**. Po zakończeniu będziesz mieć gotowy fragment kodu działający z najnowszą wersją Aspose.Words dla .NET.

---

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (v24.10 lub nowszy) – biblioteka napędzająca wszystko poniżej.  
- Środowisko programistyczne .NET (Visual Studio, Rider lub `dotnet` CLI).  
- Podstawowa znajomość C# – jeśli potrafisz napisać „Hello World”, jesteś gotowy.  

Nie są wymagane dodatkowe pakiety NuGet; wszystko znajduje się w `Aspose.Words` i `System.Drawing`.

---

## Krok 1: Utwórz pusty dokument Word

Pierwszym krokiem jest utworzenie pustego obiektu `Document`. Traktuj go jak czyste płótno — tak jakbyś ręcznie otworzył nowy plik Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Dlaczego to ważne:*  
Instancja `Document` reprezentuje cały plik Word. Rozpoczęcie od pustego dokumentu daje pełną kontrolę nad każdym elementem, który później dodasz, od akapitów po kształty.

---

## Krok 2: Zdefiniuj prostokątny kształt (Rectangle Shape Word)

Teraz potrzebujemy kształtu, z którym będziemy pracować. Prostokąt jest najprostszą geometrią i sprawdza się doskonale jako baner, placeholder lub prosty mock‑up UI.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Dlaczego to ważne:*  
Ustawienie `Width` i `Height` pozwala kontrolować wizualny rozmiar kształtu. `ShapeType.Rectangle` instruuje Aspose, aby narysował klasyczną ramkę — idealną do późniejszego demonstrowania **add shape shadow**.

---

## Krok 3: Dodaj cień do kształtu (How to Add Shadow)

Cienie dodają głębi, sprawiając, że płaski prostokąt wygląda jak fizyczny obiekt. Aspose.Words udostępnia właściwość `Shadow`, w której możesz dostosować kolor, odległość, rozmycie i przezroczystość.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Dlaczego to ważne:*  
Każda właściwość wpływa na wizualny sygnał:

- **Enabled** – bez tego pozostałe ustawienia są ignorowane.  
- **Color** – wybierz odcień pasujący do motywu dokumentu.  
- **Distance** – większe wartości oddalają cień.  
- **BlurRadius** – wyższe liczby sprawiają, że cień jest bardziej miękki.  
- **Transparency** – precyzyjnie dopasuj krycie dla subtelności.

Śmiało eksperymentuj; aby uzyskać dramatyczny efekt, zwiększ `Distance` do `10` i ustaw `Transparency` na `0.5`.

---

## Krok 4: Wstaw kształt do dokumentu (Insert Shape Word)

Gdy prostokąt jest gotowy, potrzebujemy miejsca, w którym go umieścimy. Najprostszym miejscem jest pierwszy akapit ciała dokumentu.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Dlaczego to ważne:*  
`FirstSection.Body.FirstParagraph` jest zawsze obecny w nowym `Document`. Dodając tutaj kształt, zapewniasz, że pojawi się on na górze pliku — przydatne w nagłówkach lub banerach tytułowych.

Jeśli potrzebujesz wstawić kształt w innym miejscu, możesz znaleźć konkretny `Paragraph` lub `Run` i użyć `InsertAfter` lub `InsertBefore`.

---

## Krok 5: Zapisz plik Word

Ostatnim krokiem jest zapisanie dokumentu w pamięci na dysku. Wybierz folder, do którego masz prawo zapisu, i nadaj plikowi sensowną nazwę.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Dlaczego to ważne:*  
Wywołanie `Save` zapisuje w pełni zgodny plik `.docx`. Otwórz go w Microsoft Word, LibreOffice lub dowolnym przeglądarce i zobaczysz prostokąt z delikatnym szarym cieniem — dokładnie taki, jaki skonfigurowaliśmy.

---

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystkie dyrektywy `using`, tworzenie kształtu, konfigurację cienia, wstawianie oraz zapisywanie.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Oczekiwany wynik:**  
Otwórz `ShadowedRectangle.docx` i zobaczysz jasnoszary prostokąt wyśrodkowany u góry strony z subtelnym cieniem odsuniętym o 5 pt. Brak dodatkowego tekstu, tylko kształt — dokładnie to, co generuje kod.

---

## Częste pytania i przypadki brzegowe

### Co zrobić, jeśli potrzebuję innego kształtu?

Zastąp `ShapeType.Rectangle` dowolną inną wartością wyliczenia `ShapeType` (`Ellipse`, `Triangle`, `Star` itp.). Właściwości cienia działają w ten sam sposób.

### Czy mogę dodać wiele cieni?

Aspose.Words obsługuje tylko jeden cień na kształt. Jeśli potrzebujesz warstwowych efektów, utwórz dwa nakładające się kształty z różnymi ustawieniami cienia.

### Jak to działa na .NET Core?

To samo API działa na .NET 6/7/8. Upewnij się tylko, że odwołujesz się do pakietu **Aspose.Words.NETCore** (lub standardowego pakietu, który jest teraz wieloplatformowy).

### Czy `System.Drawing` jest nadal wspierany na Linuksie?

`System.Drawing.Common` jest dostępny tylko na Windows od .NET 6. W projektach wieloplatformowych użyj `Aspose.Drawing` (oddzielny pakiet NuGet) lub trzymaj się kolorów definiowanych bezpośrednio przez `Aspose.Words`.

### Co z skalowaniem DPI?

Wymiary kształtu podawane są w punktach (1 pt = 1/72 cala). Jeśli potrzebujesz precyzyjnego rozmiaru w pikselach dla określonego DPI, oblicz punkty jako `pixels * 72 / dpi`.

---

## Porady i pułapki

- **Pro tip:** Ustaw `rectangleShape.WrapType = WrapType.Inline;`, jeśli chcesz, aby kształt przepływał z tekstem zamiast unosić się nad nim.  
- **Watch out for:** Zapomnienie o włączeniu cienia (`Enabled = true`). Pozostałe ustawienia będą cicho ignorowane.  
- **Performance note:** Dodawanie wielu kształtów w pętli może być wolne. Grupuj je w jednej `Section` i wywołaj `document.UpdatePageLayout()` raz na końcu.  
- **Version check:** API cienia zostało wprowadzone w Aspose.Words 20.2. Jeśli używasz starszej wersji, zaktualizuj ją, aby uniknąć brakujących właściwości.

---

## Zakończenie

Utworzyliśmy **pusty dokument Word**, zbudowaliśmy **rectangle shape word**, nauczyliśmy się **dodawać cień**, a na końcu **wstawiliśmy zawartość shape word** z dopracowanym efektem **add shape shadow** — wszystko przy użyciu Aspose.Words dla .NET.  

Fragment kodu jest w pełni uruchamialny, działa na Windows i wieloplatformowym .NET, i może być rozszerzony o inne kształty, kolory lub nawet animowane GIF‑y. Następnie możesz spróbować dodać tekst wewnątrz prostokąta, zastosować wypełnienia gradientowe lub wygenerować cały raport z wieloma stylizowanymi kształtami.  

Masz więcej pomysłów? Spróbuj zamienić szary cień na niebieski, zwiększyć rozmycie dla efektu marzycielskiego lub połączyć kilka kształtów w własne logo. Nie ma granic, a teraz masz elementy konstrukcyjne, aby to zrobić.  

Szczęśliwego kodowania i niech Twoje dokumenty zawsze wyglądają ostro (z odpowiednią ilością cienia)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}