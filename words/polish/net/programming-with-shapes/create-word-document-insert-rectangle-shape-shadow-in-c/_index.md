---
category: general
date: 2026-05-26
description: Utwórz dokument Word w C# przy użyciu Aspose.Words, wstaw kształt prostokąta,
  ustaw kolor wypełnienia i dodaj efekt cienia – przewodnik krok po kroku.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: pl
og_description: Utwórz dokument Word w C# przy użyciu Aspose.Words. Dowiedz się, jak
  wstawić kształt prostokąta, ustawić jego kolor wypełnienia i dodać efekt cienia.
og_title: Utwórz dokument Word – wstaw prostokąt i cień w C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Utwórz dokument Word – wstaw kształt prostokąta i cień w C#
url: /pl/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word – wstaw prostokątny kształt i cień w C#

Zastanawiałeś się kiedyś, jak **utworzyć dokument Word** programowo, bez otwierania Microsoft Word? Nie jesteś jedyny. W wielu scenariuszach automatyzacji — myśl o fakturach, umowach lub masowej generacji raportów — potrzebujesz niezawodnego sposobu na stworzenie pliku .docx, wstawienie do niego kształtu, nadanie mu koloru, a może nawet cienia dla uzyskania wykończonego wyglądu.

W tym samouczku przeprowadzimy Cię krok po kroku przez to: używając Aspose.Words for .NET **utworzyć dokument Word**, **wstawić prostokątny kształt**, zastosować wypełnienie i **dodać cień**. Po zakończeniu będziesz mieć gotowy do zapisania plik, który możesz wprowadzić do dowolnego dalszego procesu.

Poruszymy także **sposób wstawiania kształtu** w elastyczny sposób oraz dlaczego **sposób ustawiania wypełnienia** ma znaczenie dla spójności wizualnej. Bez zbędnych wstępów, tylko kod, który możesz skopiować‑wkleić i uruchomić.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz:

- .NET 6+ (lub .NET Framework 4.7+) zainstalowany.
- Ważną licencję Aspose.Words for .NET (lub tymczasowy klucz ewaluacyjny).
- Visual Studio, Rider lub dowolne IDE dla C#, które lubisz.
- Podstawową znajomość składni C# — nic skomplikowanego nie jest potrzebne.

Masz to wszystko? Świetnie, zaczynajmy.

## Krok 1 – Utwórz dokument Word

Pierwszą rzeczą, której potrzebujesz, jest pusty obiekt dokumentu. To płótno, na którym będzie się znajdować wszystko inne.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` reprezentuje plik .docx w pamięci, natomiast `DocumentBuilder` udostępnia wygodne API do wstawiania tekstu, tabel i kształtów. **Tworzenie dokumentu Word** w ten sposób jest natychmiastowe — bez UI, bez COM interop, po prostu czysty .NET.

## Krok 2 – Wstaw prostokątny kształt

Teraz, gdy mamy dokument, **wstawmy prostokątny kształt**. Metoda `InsertShape` przyjmuje wyliczenie `ShapeType`, szerokość i wysokość (w punktach). Użyjemy prostokąta o wymiarach 150 × 80 punktów, co w przybliżeniu odpowiada 2 × 1 cali.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Za kulisami Aspose tworzy obiekt `Shape`, dodaje go do bieżącego akapitu i zwraca referencję, którą możesz stylizować. To jest sedno **sposobu wstawiania kształtu** — tylko jedna linijka kodu, a jednocześnie niezwykle potężna.

## Krok 3 – Jak ustawić wypełnienie

Kształt bez wypełnienia jest niewidoczny na białej stronie. Dodajmy mu przyjemne, jasno‑niebieskie tło.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Można również używać gradientów, tekstur lub nawet wypełnienia obrazem, ale jednolity kolor upraszcza przykład. To pokazuje **sposób ustawiania wypełnienia** na dowolnym kształcie, który tworzysz, zapewniając wizualny efekt, którego oczekują czytelnicy.

## Krok 4 – Jak dodać cień

Cienie dodają głębi i sprawiają, że kształt „wyskakuje”. Aspose.Words udostępnia obiekt `ShadowFormat`, w którym możesz włączyć widoczność, wybrać kolor oraz precyzyjnie dostroić rozmycie, odległość i kąt.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Dlaczego właśnie te wartości? Kąt 45° daje naturalne źródło światła z góry‑prawej, umiarkowane rozmycie utrzymuje cień subtelnym, a krótka odległość zapobiega wrażeniu, że kształt jest oderwany. Śmiało eksperymentuj — zmiana kąta na 135° spowoduje, że cień padnie w dół‑lewo, na przykład.

## Krok 5 – Zapisz dokument

Wszystko gotowe; teraz zapisujemy plik na dysku. Wybierz dowolną ścieżkę, ale upewnij się, że folder istnieje.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Gdy otworzysz `ShadowShape.docx` w Microsoft Word, zobaczysz jasno‑niebieski prostokąt z delikatnym szarym cieniem — dokładnie to, co zakodowaliśmy.

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny, gotowy do skopiowania program:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Oczekiwany wynik

- Plik o nazwie **ShadowShape.docx** pojawia się w docelowym folderze.
- Po otwarciu w Wordzie widoczny jest jasno‑niebieski prostokąt wyśrodkowany na pierwszej stronie.
- Prostokąt rzuca szary cień pod kątem 45°, nadając subtelny efekt 3‑D.

## Częste pytania i przypadki brzegowe

**Co zrobić, jeśli potrzebuję innego kształtu?**  
Zastąp `ShapeType.Rectangle` dowolną inną wartością wyliczenia (`Ellipse`, `Star`, `Arrow` itp.). Reszta kodu pozostaje bez zmian.

**Czy mogę dodać tekst wewnątrz kształtu?**  
Tak — po utworzeniu kształtu wywołaj `shape.AppendChild(new Paragraph(doc))`, a następnie wstaw `Run` z tekstem. Pamiętaj, aby ustawić właściwości `shape.TextBox`, jeśli chcesz, aby tekst się zawijał.

**A co z DPI lub jednostkami miary?**  
Aspose pracuje w punktach (1 pt = 1/72 cala). Jeśli wolisz centymetry, pomnóż przez 28,35 (ponieważ 1 cm ≈ 28,35 pt).

**Czy potrzebna jest licencja, aby to działało?**  
Wersja ewaluacyjna dodaje znak wodny na pierwszej stronie. Prawidłowa licencja usuwa go i odblokowuje pełne API.

## Porady i pułapki

- **Pro tip:** Wywołaj `builder.MoveToDocumentEnd()` przed wstawieniem kształtu, jeśli chcesz, aby znajdował się na samym końcu dokumentu.
- **Uwaga:** Zapis do folderu tylko do odczytu spowoduje wyrzucenie `UnauthorizedAccessException`. Upewnij się, że aplikacja ma uprawnienia do zapisu.
- **Uwaga dotycząca wydajności:** Przy masowej generacji (setki dokumentów) używaj jednego egzemplarza `Document` jako szablonu i klonuj go metodą `doc.Clone(true)`, aby uniknąć powtarzalnego kosztu inicjalizacji.

## Zakończenie

Teraz wiesz, jak **utworzyć dokument Word**, **wstawić prostokątny kształt**, **ustawić wypełnienie** i **dodać cień** przy użyciu Aspose.Words for .NET. Powyższy fragment kodu to samodzielne rozwiązanie, które możesz wstawić do dowolnego projektu C#, niezależnie od tego, czy jest to aplikacja konsolowa, API webowe czy usługa w tle.

Od tego momentu możesz rozważyć:

- Dodawanie wielu kształtów o różnych kolorach.
- Użycie gradientów lub wypełnień obrazem (`shape.FillColor = ...` → `shape.FillPattern`).
- Łączenie kształtów z tabelami w celu stworzenia złożonych układów raportów.

Spróbuj, zmodyfikuj parametry i zobacz, jak Twoje automatycznie generowane pliki Word stają się bardziej profesjonalne dzięki kilku linijkom kodu. Szczęśliwego kodowania!

## Powiązane samouczki

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}