---
category: general
date: 2026-07-29
description: Rysuj prostokąt w dokumencie Word przy użyciu Aspose.Words. Dowiedz się,
  jak dodać kształt prostokąta, dodać kształt linii oraz zarządzać wieloma kształtami
  w jednym dokumencie Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: pl
lastmod: 2026-07-29
og_description: Rysuj prostokąt w Wordzie przy użyciu Aspose.Words. Postępuj zgodnie
  z tym przewodnikiem krok po kroku, aby dodać kształt prostokąta, dodać kształt linii
  i bez wysiłku pracować z wieloma kształtami w Wordzie.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Rysowanie prostokąta w Word – Mistrz dodawania kształtów w Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Rysowanie prostokąta w Word – Dodawanie kształtów w Word przy użyciu Aspose
url: /pl/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Kompletny przewodnik po dodawaniu kształtów w Wordzie

Zastanawiałeś się kiedyś, jak **draw rectangle word** dokumenty bez otwierania interfejsu za każdym razem? Nie jesteś sam. Wielu programistów musi generować pliki Word w locie, a najprostszym sposobem jest pozwolić bibliotece wykonać ciężką pracę. W tym samouczku pokażemy dokładnie **jak dodawać kształty** — konkretnie prostokąt i linię — używając Aspose.Words for .NET, i skupimy się na frazie *draw rectangle word*, abyś nigdy się nie zgubił.

Pomyśl o tym jak o mini‑studiu artystycznym, które żyje w twoim kodzie. Po zakończeniu będziesz w stanie **add rectangle shape**, **add line shape**, a nawet połączyć je w grupy **multiple shapes word**. Bez interfejsu, bez ręcznego kombinowania, tylko czysty, powtarzalny C#.

## Co się nauczysz

- Utwórz nowy dokument Word przy użyciu Aspose.Words.  
- Utwórz **GroupShape**, który może przechowywać kilka obiektów.  
- **Add rectangle shape** i **add line shape** wewnątrz tej grupy.  
- Wstaw zgrupowane kształty do ciała dokumentu.  
- Zapisz plik i zobacz wynik natychmiast.  

Jeśli czujesz się komfortowo z podstawowym C# i masz kopię Aspose.Words, jesteś gotowy. Nie są wymagane dodatkowe pakiety NuGet poza podstawową biblioteką.

> **Pro tip:** Aspose.Words działa z .NET 6, .NET 7 i .NET Framework 4.6+. Wybierz środowisko uruchomieniowe, które pasuje do twojego projektu.

![przykład draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – grupowane kształty w pliku Word")

## draw rectangle word – Przygotowanie dokumentu

Zanim będziemy mogli **draw rectangle word**, potrzebujemy czystego płótna. Klasa `Document` jest tym płótnem; `DocumentBuilder` jest naszym pędzlem.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Powyższe dwie linie dają nam świeży, w‑pamięci `.docx`. Nic nie jest jeszcze zapisywane na dysku, co oznacza, że możemy eksperymentować bez zagracania systemu plików.

## Jak dodawać kształty – Tworzenie kontenera GroupShape

Kiedy chcesz, aby **multiple shapes word** zachowywały się jako jedna jednostka — poruszały się razem, obracały się razem — otaczasz je w `GroupShape`. Pomyśl o grupie jako o folderze, który przechowuje inne kształty.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Dlaczego grupa? Ponieważ później możesz chcieć **add rectangle shape** i **add line shape**, a następnie przesunąć je razem. Bez grupy musiałbyś przemieszczać każdy kształt osobno.

## add rectangle shape – Wstawianie prostokąta do grupy

Teraz, gdy kontener istnieje, dodajmy **add rectangle shape**. Prostokąt to `Shape`, którego `ShapeType` to `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Zauważ, że wartości `Left` i `Top` są względne względem początku grupy, a nie strony. To ułatwia precyzyjne ustawienie kształtów. Prostokąt pojawi się w pobliżu lewego górnego rogu grupy.

## add line shape – Dodawanie linii do tej samej grupy

Linia to po prostu kolejny `Shape`, ale jej `ShapeType` to `Line`. Umieścimy ją pod prostokątem.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Ponieważ wysokość linii wynosi zero, właściwość `Top` określa, gdzie linia znajduje się pionowo. `Width` kontroluje, jak długo linia rozciąga się poziomo.

## multiple shapes word – Wstawianie grupy do ciała dokumentu

Mamy grupę, która teraz zawiera **add rectangle shape** i **add line shape**. Ostatnim krokiem jest wstawienie całości do dokumentu.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` umieszcza grupę dokładnie tam, gdzie aktualnie znajduje się `DocumentBuilder`. Jeśli potrzebujesz jej w konkretnym paragrafie, najpierw przesuń builder przy użyciu `builder.MoveToParagraph(index)`.

## Zapisywanie wyniku – Podgląd wyniku draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Otwórz wygenerowany plik w Microsoft Word i zobaczysz jedną grupę zawierającą prostokąt i linię. Możesz kliknąć grupę, przeciągnąć ją, a nawet zmienić rozmiar — wszystkie kształty poruszają się razem. To jest moc **multiple shapes word**.

### Oczekiwany wynik

- Plik `.docx` o nazwie `GroupShape.docx`.  
- Jedna strona z grupowanym prostokątem (120 × 80 pt) w pobliżu lewego górnego rogu.  
- Pozioma linia (150 pt długości) umieszczona tuż pod prostokątem.  
- Oba kształty są wybieralne jako pojedynczy obiekt.

Jeśli dwukrotnie klikniesz grupę, Word pozwoli ci edytować każdy kształt osobno — idealne do precyzyjnego dostrajania.

## Częste pytania i przypadki brzegowe

**Co jeśli potrzebuję więcej niż dwóch kształtów?**  
Po prostu kontynuuj wywoływanie `group.AppendChild(yourShape)` dla każdego dodatkowego obiektu. Grupa może przechowywać dowolną liczbę kształtów, co czyni ją idealną do złożonych diagramów.

**Czy mogę zmienić kolor wypełnienia prostokąta?**  
Oczywiście. Po utworzeniu prostokąta ustaw `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Działa to dla każdego kształtu, który obsługuje wypełnianie.

**Czy muszę ustawiać `Height = 0` dla linii?**  
Tak, dla prostej poziomej linii wysokość powinna być zero. Dla linii pionowej ustaw `Width = 0` i nadaj `Height` dodatnią wartość.

**Czy to będzie działać z plikami .doc (Word 97‑2003)?**  
Aspose.Words może zapisywać w starszym formacie `.doc`, ale niektóre nowoczesne funkcje kształtów mogą być ograniczone. Trzymaj się `.docx` dla pełnej wierności.

**Jak obrócić całą grupę?**  
Możesz ustawić `group.Rotation = 45;` (stopnie) przed jej wstawieniem. Obrót dotyczy każdego kształtu podrzędnego.

## Podsumowanie – Jak dodawać kształty w Wordzie programowo

- **draw rectangle word** zaczyna się od utworzenia `Document` i `DocumentBuilder`.  
- Utwórz **GroupShape**, aby przechowywać **multiple shapes word**.  
- **add rectangle shape** i **add line shape** są dodawane do grupy.  
- Wstaw grupę do ciała dokumentu przy użyciu `builder.InsertNode`.  
- Zapisz plik i otwórz go, aby zweryfikować wynik wizualny.

To cały przepływ pracy, zamknięty w jednym, łatwym do odczytania przykładzie kodu.

## Kolejne kroki i powiązane tematy

Teraz, gdy wiesz **jak dodawać kształty**, rozważ eksplorację:

- **add rectangle shape** z zaokrąglonymi rogami (`ShapeType.Rectangle` + `CornerRadius`).  
- Stylowanie linii z różnymi wzorami kreski (`line.LineFormat.DashStyle`).  
- Osadzanie obrazów obok kształtów dla bogatszych raportów.  
- Używanie **multiple shapes word** do tworzenia diagramów przepływu lub prostych diagramów UML.  

Każdy z tych tematów naturalnie rozwija fundament, który tutaj przedstawiliśmy, i wszystkie podążają za tym samym schematem tworzenia kształtów, ich konfigurowania oraz grupowania w razie potrzeby.

---

Miłego kodowania! Jeśli napotkasz problemy lub masz ciekawy przypadek użycia do podzielenia się, zostaw komentarz poniżej. Twoja opinia pomaga nam wszystkim opanować sztukę **draw rectangle word** i nie tylko.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera pełne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz kształt prostokąta w Wordzie przy użyciu C# – Przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Utwórz kształt prostokąta w Wordzie z Aspose.Words – Przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Wstawianie kształtów w dokumentach Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}