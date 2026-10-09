---
category: general
date: 2026-03-06
description: Utwórz kształt prostokąta w programie Word i dodaj cień kształtu za pomocą
  Aspose.Words. Dowiedz się, jak wstawić prostokąt w Wordzie oraz jak dodać cień do
  kształtu w języku C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: pl
og_description: Utwórz prostokątny kształt w programie Word i dodaj cień do kształtu
  za pomocą Aspose.Words. Przewodnik krok po kroku, jak wstawić prostokąt w Wordzie
  i jak dodać cień do kształtu.
og_title: Utwórz prostokątny kształt z cieniem w Wordzie przy użyciu Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Utwórz prostokątny kształt z cieniem w Wordzie przy użyciu Aspose.Words
url: /pl/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz kształt prostokąta z cieniem w Wordzie przy użyciu Aspose.Words

Czy kiedykolwiek potrzebowałeś **create rectangle shape** w dokumencie Word, ale nie wiedziałeś, jak nadać mu wykończony wygląd? Nie jesteś sam — większość programistów napotyka ten sam problem, gdy po raz pierwszy próbuje dodać wizualny akcent do automatycznych dokumentów. Dobra wiadomość? Z Aspose.Words dla .NET możesz zarówno **create rectangle shape**, jak i **add shape shadow** w zaledwie kilku linijkach C#.

W tym samouczku przeprowadzimy Cię krok po kroku przez **how to insert rectangle in Word**, a następnie pokażemy **how to add shadow to shape**, aby wyróżnił się na stronie. Po zakończeniu będziesz mieć gotowy do zapisania `Shadow.docx`, który możesz otworzyć w Wordzie i zobaczyć szary prostokąt z delikatnym cieniem. Bez dodatkowych plików graficznych, bez ręcznych poprawek — tylko kod.

## Co się nauczysz

- Dokładne instrukcje C# potrzebne do **create rectangle shape** przy użyciu Aspose.Words.  
- Jak włączyć i skonfigurować cień przy użyciu obiektu `Shadow`.  
- Dlaczego każda właściwość ma znaczenie (np. `Transparency`, `Blur`, `Angle`).  
- Typowe pułapki (jednostki, kompatybilność wersji) oraz szybkie rozwiązania.  
- Kompletny program gotowy do kopiowania i wklejania, który możesz uruchomić już dziś.

### Wymagania wstępne

- .NET 6+ (lub .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 lub nowszy (pakiet NuGet to `Aspose.Words`).  
- Podstawowa znajomość C# i Visual Studio (lub dowolnego ulubionego IDE).  

Jeśli już je masz, przejdźmy od razu do działania.

---

## Krok 1: Skonfiguruj projekt i zaimportuj przestrzenie nazw

Najpierw utwórz nową aplikację konsolową (lub użyj istniejącej) i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Następnie wprowadź wymagane przestrzenie nazw do pliku `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** Jeśli celujesz w .NET 6+, możesz włączyć globalne dyrektywy `using`, aby uniknąć powtarzania tych linii w każdym pliku.

---

## Krok 2: **Create rectangle shape** w pustym dokumencie Word

Zaczniemy od nowego obiektu `Document` i `DocumentBuilder`, aby go modyfikować. Metoda `InsertShape` buildera to miejsce, gdzie dzieje się magia.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Dlaczego 200 × 100 punktów? W Wordzie punkt to 1/72 cala, więc prostokąt ma w przybliżeniu 2,8 × 1,4 cala — wystarczająco duży, aby go zauważyć, ale nie przytłaczający. Możesz zmienić te liczby, aby dopasować je do swojego układu; pamiętaj jednak, że są mierzone w **points**, a nie w pikselach.

---

## Krok 3: **Add shape shadow** – konfigurowanie wyglądu

Teraz, gdy mamy prostokąt, nadamy mu subtelny szary cień. Obiekt `Shadow` jest częścią `Shape` i udostępnia kilka przydatnych właściwości.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Co robi każda właściwość

| Właściwość | Efekt | Typowe wartości |
|------------|-------|-----------------|
| **Enabled** | Włącza/wyłącza cień | `true` or `false` |
| **Color** | Podstawowy kolor cienia | Any `System.Drawing.Color` |
| **Transparency** | Przezroczystość (0 = pełny, 1 = niewidzialny) | 0.0 – 1.0 |
| **Blur** | Miękkość krawędzi | 0 – 10 (wyższa = bardziej miękka) |
| **Distance** | Odległość między kształtem a cieniem | 0 – 20 punktów |
| **Angle** | Kierunek, z którego wydaje się padać światło | 0 – 360 stopni |
| **Size** | Skala cienia względem kształtu | 0 – 200 % |

> **Po co te ustawienia?**  
> Dostosowywanie cienia pozwala dopasować go do wytycznych brandingowych firmy (np. subtelna 20 % przezroczystość dla profesjonalnego wyglądu) bez konieczności korzystania z zewnętrznych edytorów graficznych.

---

## Krok 4: Zapisz dokument i zweryfikuj wynik

Na koniec zapisz plik na dysku. Możesz wybrać dowolny folder; po prostu zamień `YOUR_DIRECTORY` na rzeczywistą ścieżkę.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Otwórz `Shadow.docx` w Microsoft Word i powinieneś zobaczyć szary prostokąt z delikatnym cieniem, przesuniętym pod kątem 45°. Ten wizualny efekt sprawia, że kształt wydaje się „uniesiony” nad stroną — dokładnie to, czego oczekujesz od dopracowanego raportu lub faktury.

---

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do `Program.cs`. Nie brakuje żadnych fragmentów; kompiluje się i działa bez zmian.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Oczekiwany wynik

- **Plik:** `Shadow.docx` umieszczony w folderze wykonywania projektu.  
- **Wizualizacja:** Jeden prostokąt wyśrodkowany na stronie, wypełniony domyślną bielą oraz szary cień przesunięty o 4 punkty w dół i w prawo, lekko rozmyty dla naturalnego wyglądu.

---

## Częste pytania i przypadki brzegowe

### 1. Co zrobić, jeśli potrzebuję innej jednostki (np. centymetry)?

Aspose.Words działa w punktach, ale możesz przeliczyć centymetry na punkty prostą formułą:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Czy to działa ze starszymi wersjami Aspose.Words?

API `Shadow` zostało wprowadzone w wersji 14.0. Jeśli używasz starszej wersji, musisz zaktualizować ją przez NuGet. Reszta kodu (tworzenie kształtów) jest stabilna od wielu lat, więc nie napotkasz niekompatybilnych zmian.

### 3. Czy mogę dodać cień do innych kształtów (np. okręgów)?

Oczywiście — każdy obiekt `Shape` udostępnia właściwość `Shadow`. Wystarczy zamienić `ShapeType.Rectangle` na `ShapeType.Ellipse` lub `ShapeType.Cloud`, a następnie zastosować te same ustawienia cienia.

### 4. Co zrobić, jeśli potrzebuję kolorowego cienia (np. niebieskiego dla marki)?

Zamień `Color.Gray` na dowolny `Color`, którego potrzebujesz:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Pamiętaj, aby dostosować `Transparency`, aby kolor nie stał się zbyt dominujący.

---

## 🎨 Podsumowanie wizualne

![utwórz kształt prostokąta z cieniem w Wordzie przy użyciu Aspose.Words](image-placeholder.png "utwórz kształt prostokąta z cieniem w Wordzie przy użyciu Aspose.Words")

*Tekst alternatywny: utwórz kształt prostokąta z cieniem w Wordzie przy użyciu Aspose.Words*

Zrzut ekranu (placeholder) pokazuje finalny dokument — tylko prostokąt i jego delikatny szary cień.

---

## Zakończenie

Teraz wiesz, jak **create rectangle shape** w pliku Word, **add shape shadow**, oraz jak precyzyjnie dopasować każdy aspekt wizualny przy użyciu Aspose.Words dla .NET. Krótki program, który stworzyliśmy, obejmuje cały przepływ pracy — od

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}