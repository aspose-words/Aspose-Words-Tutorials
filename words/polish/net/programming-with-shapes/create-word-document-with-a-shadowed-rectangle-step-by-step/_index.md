---
category: general
date: 2026-01-13
description: Utwórz dokument Word przy użyciu Aspose.Words i dowiedz się, jak wstawić
  kształt prostokąta, jak dodać cień oraz jak dodać cień do kształtu w C#. Dołączony
  pełny przykład.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: pl
og_description: Utwórz dokument Word przy użyciu Aspose.Words, zobacz, jak wstawić
  kształt prostokąta i jak dodać cień. Śledź kompletny przykład w C#.
og_title: Utwórz dokument Word z prostokątem w cieniu – pełny poradnik
tags:
- Aspose.Words
- C#
- Document Automation
title: Utwórz dokument Word z prostokątem w cieniu – przewodnik krok po kroku
url: /pl/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word z prostokątem z cieniem – przewodnik krok po kroku

Czy kiedykolwiek potrzebowałeś **create word document**, który zawiera ładnie cieniowany prostokąt, ale nie wiedziałeś od czego zacząć? Nie jesteś jedyny — wielu programistów napotyka ten sam problem, gdy po raz pierwszy pracują z Aspose.Words.  

W tym samouczku przeprowadzimy Cię przez wszystko, co potrzebne, aby **create word document** programowo, **insert rectangle shape**, oraz pokazać **how to add shadow**, aby kształt naprawdę się wyróżniał. Po zakończeniu będziesz mieć gotowy do uruchomienia fragment C# , który możesz wkleić do dowolnego projektu .NET.

## Co się nauczysz

- Dokładny kod do **how to insert shape** (prostokąt) w pliku Word.  
- Właściwości, które musisz dostosować, aby **add shape shadow** i kontrolować jego wygląd.  
- Jak zapisać wynik i zweryfikować, że cień jest widoczny.  
- Kilka praktycznych wskazówek i uwag dotyczących przypadków brzegowych, które zaoszczędzą Ci później bólu głowy.

Nie potrzebna jest zewnętrzna dokumentacja — wszystko jest tutaj.

## Wymagania wstępne

1. **.NET 6.0** (lub dowolna nowsza wersja .NET) zainstalowana.  
2. **license** dla Aspose.Words for .NET, lub możesz użyć darmowego trybu ewaluacji do testów.  
3. Środowisko programistyczne — Visual Studio 2022 działa świetnie, ale każdy edytor, który potrafi kompilować C#, wystarczy.

To wszystko. Nie są potrzebne dodatkowe pakiety NuGet poza `Aspose.Words` are needed.

## Krok 1 – Skonfiguruj projekt i odwołanie do Aspose.Words

Najpierw utwórz nową aplikację konsolową i dodaj pakiet Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Jeśli używasz wersji próbnej, pamiętaj, aby wywołać `License.SetLicense` z plikiem licencji; w przeciwnym razie biblioteka doda znak wodny.

## Krok 2 – Zainicjuj Document Builder

Teraz rozpoczniemy rzeczywisty proces **create word document**. Klasa `Document` daje nam pustą płaszczyznę, a `DocumentBuilder` pozwala na rysowanie na niej.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Dlaczego potrzebujemy buildera? Abstrahuje on szczegóły niskopoziomowego OpenXML, więc możesz skupić się na *tym, co* chcesz, a nie na *tym, jak* plik jest zbudowany. To jest sedno **how to insert shape** szybko.

## Krok 3 – Wstaw prostokąt jako kształt

Tutaj faktycznie **insert rectangle shape**. Prostokąt będzie miał 150 × 100 punktów (około 2 cala × 1,3 cala).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Metoda `InsertShape` zwraca obiekt `Shape`, który możemy dalej dostosować. Na tym etapie prostokąt jest po prostu białym, jednolitym pudełkiem — bez cienia.

## Krok 4 – Jak dodać cień (Add Shape Shadow)

Dodanie cienia jest zaskakująco proste, gdy wiesz, które właściwości należy zmienić. Obiekt `ShadowFormat` kontroluje widoczność, kolor, rozmycie, offset i rozmiar.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Ten blok odpowiada na pytanie **how to add shadow** w prostych słowach: włącz go, wybierz kolor, dostosuj przezroczystość, offset, rozmycie i rozmiar. Możesz eksperymentować z tymi wartościami, aby uzyskać mocny cień opadający lub delikatny jak szept.

### Typowe warianty

- **Różne kolory:** Użyj `Color.Black` dla klasycznego cienia, lub `Color.BlueViolet` dla stylizowanego efektu.  
- **Zero blur:** Ustaw `BlurRadius = 0` dla wyraźnej, ostrej krawędzi.  
- **Większe offsety:** Zwiększ `OffsetX`/`OffsetY`, aby przesunąć cień dalej od kształtu.

## Krok 5 – Zapisz dokument i zweryfikuj

Na koniec zapisz dokument na dysku. Plik będzie standardowym `.docx`, który może otworzyć każdy nowoczesny edytor Word.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Otwórz powstały plik *ShadowRectangle.docx* w Microsoft Word. Powinieneś zobaczyć prostokąt z miękkim szarym cieniem przesuniętym w dół i w prawo — dokładnie to, co określił kod.

> **Expected output:** Jednostronicowy plik Word zawierający prostokąt 150 × 100 punktów z 30 % przezroczystym szarym cieniem, przesuniętym o 5 pt, rozmytym o 4 pt i o rozmiarze 75 % kształtu.

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny, gotowy do uruchomienia program:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchom program (`dotnet run`) i otrzymasz nowy plik Word z ładnie cieniowanym prostokątem — idealny do raportów, certyfikatów lub dowolnego wizualnego elementu, którego potrzebujesz.

## Najczęściej zadawane pytania (FAQ)

**Q: Czy mogę wstawić inne kształty (elipsę, gwiazdę) i nadal używać tego samego kodu cienia?**  
A: Oczywiście. Metoda `InsertShape` przyjmuje dowolną wartość wyliczenia `ShapeType`. Gdy masz już instancję `Shape`, właściwości `ShadowFormat` działają identycznie, więc **how to add shadow** jest niezależny od kształtu.

**Q: Co zrobić, jeśli potrzebuję cienia po obu stronach kształtu?**  
A: Aspose.Words obsługuje tylko pojedynczy cień opadający na kształt. Aby zasymulować podwójny efekt, zduplikuj kształt, przesuwając każdą kopię inaczej, i ustaw `ShadowFormat.Visible` jednego na `false`, pozostawiając cień drugiego widoczny.

**Q: Czy to działa na .NET Framework 4.8?**  
A: Tak. API jest niezależne od wersji; wystarczy odwołać się do odpowiedniego pliku Aspose.Words DLL dla docelowego frameworka.

## Wskazówki i pułapki

- **Don’t forget to set `Visible = true`** — właściwości cienia są ignorowane w przeciwnym razie.  
- **Transparency values range from 0.0 (opaque) to 1.0 (fully transparent).** Powszechnym błędem jest użycie `30` zamiast `0.3`.  
- **Saving to a read‑only folder throws an exception.** Upewnij się, że katalog wyjściowy jest zapisywalny.

## Kolejne kroki

Teraz, gdy znasz **how to insert shape**, **add shape shadow** i **create word document** z Aspose.Words, możesz chcieć zbadać:

- Dodawanie **text inside the rectangle** przy użyciu `builder.InsertParagraph()` przed wstawieniem kształtu.  
- Stosowanie **gradient fills** lub **patterned borders** dla bogatszego stylu wizualnego.  
- Automatyzacja generowania wielu stron, każda z innym cieniowanym kształtem, aby tworzyć dynamiczne raporty.

Śmiało eksperymentuj — zmiana koloru, rozmycia lub rozmiaru cienia może dramatycznie zmienić wygląd dokumentu.

---

*Gotowy, aby wprowadzić to do produkcji? Pobierz kod, dostosuj parametry i zobacz, jak Twoje pliki Word zyskują profesjonalny wygląd w kilka sekund.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}