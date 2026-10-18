---
category: general
date: 2026-03-19
description: Utwórz dokument Word w C# przy użyciu Aspose.Words, dowiedz się, jak
  dodać kształt, dodać prostokątny kształt, zastosować cień i zapisać dokument jako
  docx w kilka minut.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: pl
og_description: Utwórz dokument Word przy użyciu Aspose.Words, dodaj kształt prostokąta,
  zastosuj zewnętrzny cień i zapisz dokument jako docx. Przewodnik krok po kroku.
og_title: Utwórz dokument Word – Dodaj kształt prostokąta i cień
tags:
- Aspose.Words
- C#
- Document Automation
title: Tworzenie dokumentu Word – jak dodać kształt prostokąta i cień
url: /pl/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word – Jak dodać kształt prostokąta i cień

Czy kiedykolwiek potrzebowałeś **create word document** programowo i zastanawiałeś się, od czego zacząć? Nie jesteś sam. Wielu programistów napotyka ten sam problem, gdy po raz pierwszy próbują wygenerować plik .docx zawierający własne grafiki. W tym samouczku przeprowadzimy Cię przez cały proces — jak dodać kształt, konkretnie **add rectangle shape**, nadać mu stylowy **add shadow to shape**, i w końcu **save document as docx**.  

Po zakończeniu przewodnika będziesz mieć gotowy do użycia fragment C# , który możesz wkleić do dowolnego projektu .NET. Bez niejasnych odniesień, tylko kompletny, działający przykład.  

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework).  
- Aspose.Words for .NET zainstalowany (pakiet NuGet `Aspose.Words`).  
- Podstawowa znajomość składni C# — nic skomplikowanego nie jest wymagane.  

Jeśli brakuje Ci biblioteki, uruchom:

```bash
dotnet add package Aspose.Words
```

To wszystko — bez dodatkowych SDK, bez interfejsu COM, tylko pojedyncze odwołanie NuGet.

---

## Krok 1: Utwórz dokument Word (główny cel)

Pierwszą rzeczą, której potrzebujemy, jest czyste płótno. Traktuj klasę `Document` jak świeżą stronę w Microsoft Word; przechowuje sekcje, akapity i wszystko, co później dodasz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Dlaczego zaczynać od pustego `Document`? Ponieważ zapewnia, że żadne ukryte formatowanie nie wkrada się z szablonu. Z mojego doświadczenia wynika, że zaczynanie od zera zapobiega tajemniczym przesunięciom układu, gdy później wstawiasz kształty.

---

## Krok 2: Wstaw kształt prostokąta — dodawanie elementu wizualnego

Teraz, gdy mamy dokument, dodajmy **add rectangle shape** do pierwszego akapitu. Obiekt `Shape` jest wszechstronny; możesz wybrać `ShapeType.Rectangle`, `Ellipse` lub nawet własne rysunki. Oto minimalny kod:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Co się dzieje pod maską?**  
- `ShapeType.Rectangle` informuje Aspose, że chcemy prosty prostokąt.  
- `WrapType.Inline` zapewnia, że prostokąt porusza się wraz z przepływem tekstu, co zazwyczaj jest oczekiwane w scenariuszu edytora tekstu.  
- Dodając do `FirstParagraph`, unikamy konieczności ręcznego wstawiania nowego akapitu; Aspose utworzy go dla nas, jeśli dokument jest naprawdę pusty.

> **Pro tip:** Jeśli potrzebujesz, aby kształt znajdował się *za* tekstem, zmień `WrapType` na `WrapType.Transparent`. Ta mała zmiana może przynieść ogromną różnicę wizualną.

---

## Krok 3: Zastosuj zewnętrzny cień — poprawa wyglądu

Płaski prostokąt jest… po prostu płaski. Dodanie **add shadow to shape** nadaje mu głębię bez dodatkowych obrazów. `ShadowFormat` w Aspose umożliwia to w jednej linii.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Dlaczego używać właśnie tych wartości?  
- **Blur** o wartości `5.0` daje subtelną, piórkowaną krawędź, która wygląda profesjonalnie na większości monitorów.  
- **Distance** o wartości `3.0` i **Angle** `45` tworzą naturalne źródło światła z góry‑lewej, co jest powszechną konwencją projektową.  
- **Color.Gray** działa zarówno w jasnych, jak i ciemnych motywach; możesz zamienić go na `Color.Black`, jeśli potrzebny jest większy kontrast.

Jeśli kiedykolwiek potrzebujesz *wewnętrznego* cienia (np. przycisk wklęsły), po prostu zmień `ShadowType.OuterShadow` na `ShadowType.InnerShadow`. Te same właściwości nadal obowiązują.

---

## Krok 4: Zapisz dokument jako DOCX — zachowanie pracy

Cała zabawa jest świetna, ale w końcu będziesz chciał mieć plik na dysku. Krok **save document as docx** jest prosty:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Kilka uwag:  
- Enum `SaveFormat.Docx` zapewnia nowoczesny format Office Open XML, kompatybilny z Word 2007+.  
- Jeśli potrzebujesz przesłać plik bezpośrednio w odpowiedzi webowej, zamień ścieżkę pliku na `MemoryStream` i zapisz go w odpowiedzi HTTP.

Po uruchomieniu kodu otwórz `ShadowedRectangle.docx` w Microsoft Word. Powinieneś zobaczyć szary prostokąt z delikatnym cieniem, umieszczony w linii z pierwszym akapitem — dokładnie to, co chcieliśmy osiągnąć.

---

## Jak dodać kształt — alternatywne podejścia

Powyższy przykład używa podejścia *inline*, ale czasami potrzebny jest kształt, który unosi się nad tekstem. Wtedy przydaje się **how to add shape** z różnym opakowaniem.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Tutaj zmieniliśmy `WrapType` na `Square` i wyśrodkowaliśmy kształt na stronie. Ten wzorzec jest przydatny przy stronach tytułowych lub dekoracyjnych banerach. Pamiętaj: unoszące się kształty nieco zwiększają rozmiar pliku, ponieważ Word przechowuje dodatkowe dane pozycjonowania.

---

## Oczekiwany wynik i weryfikacja

Po otwarciu wygenerowanego pliku powinieneś zobaczyć:

- Jeden akapit zawierający szary prostokąt.  
- Prostokąt o przybliżonych wymiarach 2,8 × 1,4 cala.  
- Subtelny zewnętrzny cień przesunięty w dół‑w prawo.  

Jeśli kształt pojawia się *poza* akapitem, sprawdź ponownie `WrapType`. Jeśli cień wydaje się zbyt ostry, zmniejsz wartość `Blur` lub zmień `Color` na jaśniejszy odcień.

---

## Częste pułapki i jak ich unikać

| Problem | Dlaczego się dzieje | Rozwiązanie |
|-------|----------------|-----|
| Shape disappears after saving | `WrapType` set to `Inline` but paragraph was removed | Ensure the paragraph exists; use `doc.FirstSection.Body.FirstParagraph` to guarantee it. |
| Shadow looks pixelated | Using a very low `Blur` value | Increase `Blur` to at least `3.0` for smooth edges. |
| File size balloons | Adding many high‑resolution images alongside shapes | Use `doc.RemoveUnusedResources()` before saving if you added images. |
| Color not showing on dark mode | Using a dark `Color` for the shape itself | Choose a contrasting color (e.g., `Color.White`) for better visibility. |

---

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do kopiowania i wklejenia kod, który zawiera wszystko, o czym rozmawialiśmy. Śmiało uruchom go jako aplikację konsolową.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Wyjaśnienie każdego bloku** znajduje się w kodzie jako komentarze, zadowalając zarówno czytelników SEO, jak i asystentów AI, którzy lubią samodzielne odpowiedzi.

---

## Zakończenie

Właśnie **create word document** od podstaw, nauczyliśmy się **how to add shape**, konkretnie **add rectangle shape**, nadaliśmy mu **add shadow to shape**, i w końcu **save document as docx**. Kroki są proste, kod zwięzły, a rezultat wygląda dopracowanie.  

Jeśli jesteś gotowy, aby pójść dalej, spróbuj zamienić prostokąt na własny obraz, eksperymentuj z różnymi kolorami cieni, lub wygeneruj cały raport z wieloma sekcjami kształtów. API Aspose.Words jest na tyle elastyczne, że poradzi sobie ze wszystkim, od faktur po broszury marketingowe.  

Masz pytania dotyczące innych typów kształtów lub potrzebujesz pomocy przy integracji tego w usłudze ASP.NET Core? zostaw komentarz poniżej i powodzenia w kodowaniu! 

![utwórz dokument word z kształtem prostokąta i cieniem](placeholder-image.png "utwórz dokument word z kształtem prostokąta i cieniem

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}