---
title: Układ w komórce
linktitle: Układ w komórce
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak ustawić układ w komórce za pomocą Aspose.Words dla .NET dzięki temu kompleksowemu przewodnikowi. Idealne dla programistów, którzy chcą dostosować dokumenty Word.
weight: 10
url: /pl/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Układ w komórce

## Wstęp

Jeśli kiedykolwiek chciałeś programowo dostroić układ komórek tabeli w dokumentach Word, jesteś we właściwym miejscu. Dzisiaj zagłębimy się w to, jak ustawić układ w komórce za pomocą Aspose.Words dla .NET. Przeprowadzimy Cię przez praktyczny przykład, rozkładając go krok po kroku, abyś mógł łatwo śledzić.

## Wymagania wstępne

Zanim przejdziemy do kodu, upewnijmy się, że masz wszystko, czego potrzebujesz:

1.  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Jeśli nie, możesz[pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Będziesz potrzebować środowiska programistycznego skonfigurowanego z .NET. Visual Studio jest świetnym wyborem, jeśli szukasz rekomendacji.
3. Podstawowa znajomość języka C#: Choć dokładnie wyjaśnię każdy krok, podstawowa znajomość języka C# pomoże Ci łatwiej nadążać.
4.  Katalog dokumentów: Przygotuj ścieżkę katalogu, w którym będziesz zapisywać swoje dokumenty. Będziemy się do tego odnosić jako`YOUR DOCUMENT DIRECTORY`.

## Importuj przestrzenie nazw

Aby rozpocząć, upewnij się, że importujesz niezbędne przestrzenie nazw do swojego projektu:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Podzielmy ten proces na łatwiejsze do opanowania kroki.

## Krok 1: Utwórz nowy dokument

 Najpierw utworzymy nowy dokument Word i zainicjujemy`DocumentBuilder` obiekt, który pomoże nam w tworzeniu treści.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Rozpocznij tworzenie tabeli i ustaw format wiersza

Zaczniemy od utworzenia tabeli i określimy wysokość oraz regułę wysokości dla wierszy.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Krok 3: Wstaw komórki i wypełnij je treścią

Następnie wykonujemy pętlę, aby wstawić komórki do tabeli. Co 7 komórek zakończymy wiersz, aby utworzyć nowy.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Krok 4: Dodaj kształt znaku wodnego

 Teraz dodajmy znak wodny do naszego dokumentu. Stworzymy`Shape` obiekt i ustaw jego właściwości.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Wyświetl kształt poza komórką tabeli, jeśli będzie on umieszczony w komórce.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Krok 5: Dostosuj wygląd znaku wodnego

Następnie dostosujemy wygląd znaku wodnego, ustawiając jego kolor i właściwości tekstu.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Krok 6: Wstaw znak wodny do dokumentu

Znajdziemy ostatni przebieg w dokumencie i wstawimy znak wodny w tym miejscu.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Krok 7: Zoptymalizuj dokument dla programu Word 2010

Aby zapewnić zgodność, zoptymalizujemy dokument pod kątem programu Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Krok 8: Zapisz dokument

Na koniec zapiszemy nasz dokument w podanym katalogu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Wniosek

I masz to! Udało Ci się utworzyć dokument Word z dostosowanym układem tabeli i dodać znak wodny za pomocą Aspose.Words dla .NET. Ten samouczek miał na celu dostarczenie przejrzystego przewodnika krok po kroku, który pomoże Ci zrozumieć każdą część procesu. Dzięki tym umiejętnościom możesz teraz programowo tworzyć bardziej wyrafinowane i dostosowane dokumenty Word.

## Najczęściej zadawane pytania

### Czy mogę użyć innej czcionki dla tekstu znaku wodnego?
 Tak, możesz zmienić czcionkę, ustawiając`watermark.TextPath.FontFamily` właściwość na wybraną czcionkę.

### Jak zmienić położenie znaku wodnego?
 Możesz zmodyfikować`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , I`VerticalAlignment` Właściwości umożliwiające dostosowanie położenia znaku wodnego.

### Czy można użyć obrazu zamiast tekstu w znaku wodnym?
 Oczywiście! Możesz stworzyć`Shape` z typem`ShapeType.Image` i ustaw jego obraz za pomocą`ImageData.SetImage` metoda.

### Czy mogę tworzyć tabele z różną wysokością wierszy?
Tak, możesz ustawić różne wysokości dla każdego rzędu, zmieniając`RowFormat.Height` właściwość przed wstawieniem komórek do tego wiersza.

### Jak usunąć znak wodny z dokumentu?
 Możesz usunąć znak wodny, lokalizując go w kolekcji kształtów dokumentu i wywołując`Remove` metoda.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
