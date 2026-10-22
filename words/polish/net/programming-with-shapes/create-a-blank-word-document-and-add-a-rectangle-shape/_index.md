---
category: general
date: 2026-09-05
description: Dowiedz się, jak utworzyć pusty dokument Word i dodać kształt prostokąta,
  który można ukryć przy użyciu Aspose.Words w C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: pl
lastmod: 2026-09-05
og_description: Tworzenie pustego dokumentu Word i wstawianie ukrytego prostokątnego
  kształtu przy użyciu Aspose.Words – przewodnik krok po kroku dla programistów C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Utwórz pusty dokument Word z ukrytym prostokątnym kształtem
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Utwórz pusty dokument Word i dodaj kształt prostokąta
url: /pl/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word i dodaj kształt prostokąta

Jeśli potrzebujesz tworzenia **pustego dokumentu Word**, który dodatkowo zawiera kształt, którego nie chcesz, aby pojawił się w układzie, ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words dla .NET. Zobaczysz kompletny, działający przykład, który tworzy nowy dokument, dodaje kształt prostokąta, ukrywa ten kształt i zapisuje plik — bez dodatkowych narzędzi.

Samouczek obejmuje wszystko, od konfiguracji projektu po rozwiązywanie typowych problemów. Po jego zakończeniu będziesz w stanie wygenerować plik Word, który wygląda na pusty dla czytelnika, ale nadal zawiera ukryte metadane, co jest przydatne w takich przypadkach jak znaki wodne, niestandardowe przechowywanie XML lub kotwice układu.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy (kod działa również z .NET Framework 4.7+)
* Visual Studio 2022 (lub dowolne IDE obsługujące C#)
* Aktywna licencja **Aspose.Words** NuGet (bezpłatna wersja próbna działa do testów)
* Podstawowa znajomość C# oraz koncepcji węzłów dokumentu

Możesz zainstalować bibliotekę przy użyciu następującego polecenia CLI:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Utrzymuj swoją wersję Aspose.Words aktualną; API użyte w tym samouczku jest stabilne od wersji 23.10.

## Jak utworzyć pusty dokument Word przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie obiektu `Document`. Nowy `Document` reprezentuje pusty **dokument Word** — brak akapitów, brak sekcji, tylko kontener pliku.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Dlaczego to ważne:** Rozpoczęcie od czystego dokumentu zapewnia, że ukryty kształt, który dodasz później, nie będzie kolidował z istniejącą treścią ani stylami.

## Dodaj kształt prostokąta do dokumentu

Następnie tworzymy kształt prostokątny. W Aspose.Words kształt jest węzłem, który może być umieszczony w dowolnym miejscu drzewa dokumentu i może być konfigurowany pod względem rozmiaru, wypełnienia, stylu linii i widoczności.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Powyższy kod tworzy widoczny prostokąt. W tym momencie mógłbyś wstawić go do dokumentu za pomocą `builder.InsertNode(rectangle)`. Jednakże, ponieważ chcemy, aby kształt pozostał ukryty, przed wstawieniem zmodyfikujemy jego właściwość `Hidden`.

## Jak ukryć kształt w dokumencie Word

Word udostępnia atrybut `Hidden` dla węzłów kształtów. Gdy jest ustawiony na `true`, kształt nie pojawia się w układzie strony, ale pozostaje częścią XML dokumentu. To jest sedno wymogu **jak ukryć kształt**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Wyjaśnienie:** Ustawienie `Hidden = true` dodaje atrybut `<w:hide>` do XML kształtu. Procesory Word ignorują kształt podczas renderowania, jednak kształt nadal może być dostępny programowo lub poprzez widok XML Worda.

## Wstaw ukryty kształt do pustego dokumentu

Teraz umieszczamy ukryty prostokąt w drzewie dokumentu. Ponieważ dokument jest nadal pusty, kształt staje się pierwszym węzłem w głównej historii.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Jeśli otworzysz powstały plik w Microsoft Word, zobaczysz pozornie pustą stronę. Kształt jest obecny, ale jest niewidzialny.

## Zapisz dokument

Na koniec zapisz dokument na dysku. Możesz wybrać dowolny obsługiwany format (`.docx`, `.pdf`, `.odt` itp.). W tym samouczku użyjemy nowoczesnego formatu DOCX.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Oczekiwany rezultat

Otwórz `HiddenRectangle.docx` w Wordzie:

* Dokument wydaje się pusty (brak widocznych kształtów lub tekstu).
* Jeśli przeanalizujesz plik przy pomocy narzędzia takiego jak **Open XML SDK** lub **Word XML Viewer**, zobaczysz element `<w:pict>` zawierający prostokąt z atrybutem `hidden`.

![pusty dokument Word z ukrytym kształtem prostokąta](image.png){: .align-center alt="pusty dokument Word z ukrytym kształtem prostokąta"}

## Pełny, działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystkie niezbędne dyrektywy `using`, obsługę błędów oraz komentarze.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Uruchom program (`dotnet run`) i zweryfikuj plik wyjściowy. Konsola potwierdzi miejsce zapisu.

## Częste pytania i przypadki brzegowe

### Czy mogę ukryć wiele kształtów jednocześnie?

Tak. Utwórz każdy kształt, ustaw `Hidden = true` i wstaw je kolejno. Flaga ukrycia działa na poziomie węzła, więc mieszanie ukrytych i widocznych kształtów w tym samym dokumencie jest obsługiwane.

### Co zrobić, jeśli kształt ma być ukryty tylko w widoku wydruku?

Word rozróżnia widoczność **wyświetlania** i **wydruku** za pomocą właściwości `DisplayWhen`. Aspose.Words nie udostępnia bezpośredniego API dla tej flagi, ale możesz zmodyfikować leżący u podstaw XML:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Używaj tego tylko wtedy, gdy potrzebujesz widoczności wyłącznie w wydruku.

### Czy ukryty kształt wpływa na rozmiar pliku?

Ukryty kształt dodaje taki sam ładunek XML jak widoczny, więc zwiększenie rozmiaru pliku jest identyczne. Jednakże, ponieważ kształt

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz pusty dokument Word z kształtem prostokąta z cieniowaniem – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Utwórz kształt prostokąta w Wordzie przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Samouczek cieniowania kształtu Aspose.Words – Dodaj cień do kształtu Word w C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}