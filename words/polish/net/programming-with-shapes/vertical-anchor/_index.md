---
title: Kotwica pionowa
linktitle: Kotwica pionowa
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak ustawić pionowe pozycje kotwic dla pól tekstowych w dokumentach Worda za pomocą Aspose.Words dla .NET. Łatwy przewodnik krok po kroku w zestawie.
weight: 10
url: /pl/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kotwica pionowa

## Wstęp

Czy kiedykolwiek zdarzyło Ci się potrzebować kontrolować, gdzie dokładnie tekst pojawia się w polu tekstowym w dokumencie Word? Może chcesz, aby tekst był zakotwiczony u góry, na środku lub u dołu pola tekstowego? Jeśli tak, jesteś we właściwym miejscu! W tym samouczku pokażemy, jak używać Aspose.Words dla .NET do ustawiania pionowego zakotwiczenia pól tekstowych w dokumentach Word. Pomyśl o pionowym zakotwiczeniu jako o magicznej różdżce, która umieszcza tekst dokładnie tam, gdzie chcesz, aby się znajdował w jego kontenerze. Gotowy do zanurzenia się? Zaczynajmy!

## Wymagania wstępne

Zanim zagłębimy się w szczegóły kotwienia pionowego, musisz mieć kilka rzeczy:

1.  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Jeśli jeszcze jej nie masz, możesz[pobierz tutaj](https://releases.aspose.com/words/net/).
2. Visual Studio: W tym samouczku założono, że do kodowania używasz programu Visual Studio lub innego środowiska IDE .NET.
3. Podstawowa znajomość języka C#: Znajomość języka C# i .NET pomoże Ci płynnie uczyć się.

## Importuj przestrzenie nazw

Aby zacząć, musisz zaimportować niezbędne przestrzenie nazw do swojego kodu C#. Tutaj informujesz swoją aplikację, gdzie znaleźć klasy i metody, których będziesz używać. Oto, jak to zrobić:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Te przestrzenie nazw zawierają klasy potrzebne do pracy z dokumentami i kształtami.

## Krok 1: Zainicjuj dokument

Po pierwsze, musisz utworzyć nowy dokument Word. Pomyśl o tym jak o ustawieniu płótna przed rozpoczęciem malowania.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Tutaj,`Document` jest twoim pustym płótnem i`DocumentBuilder` jest Twoim pędzlem, dzięki któremu możesz dodawać kształty i tekst.

## Krok 2: Wstaw kształt pola tekstowego

Teraz dodajmy pole tekstowe do naszego dokumentu. To tutaj będzie się znajdował Twój tekst. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 W tym przykładzie,`ShapeType.TextBox` określa pożądany kształt i`200, 200` to szerokość i wysokość pola tekstowego w punktach.

## Krok 3: Ustaw kotwicę pionową

Tutaj dzieje się magia! Możesz ustawić pionowe wyrównanie tekstu w polu tekstowym. Określa to, czy tekst jest zakotwiczony u góry, na środku czy u dołu pola tekstowego.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 W tym przypadku,`TextBoxAnchor.Bottom`zapewnia, że tekst będzie zakotwiczony na dole pola tekstowego. Jeśli chcesz, aby był wyśrodkowany lub wyrównany do góry, użyjesz`TextBoxAnchor.Center` Lub`TextBoxAnchor.Top`, odpowiednio.

## Krok 4: Dodaj tekst do pola tekstowego

Teraz czas dodać trochę treści do pola tekstowego. Pomyśl o tym jak o wypełnieniu płótna ostatnimi szlifami.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Tutaj,`MoveTo` zapewnia, że tekst zostanie wstawiony do pola tekstowego i`Write` dodaje właściwy tekst.

## Krok 5: Zapisz dokument

Ostatnim krokiem jest zapisanie dokumentu. To tak, jakbyś włożył swój ukończony obraz do ramki.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Wniosek

I masz to! Właśnie nauczyłeś się kontrolować pionowe wyrównanie tekstu w polu tekstowym w dokumencie Word za pomocą Aspose.Words dla .NET. Niezależnie od tego, czy zakotwiczasz tekst u góry, na środku czy u dołu, ta funkcja daje Ci precyzyjną kontrolę nad układem dokumentu. Więc następnym razem, gdy będziesz musiał zmienić rozmieszczenie tekstu w dokumencie, będziesz dokładnie wiedział, co zrobić!

## Najczęściej zadawane pytania

### Czym jest kotwiczenie pionowe w dokumencie Word?
Pionowe zakotwiczenie kontroluje położenie tekstu w polu tekstowym, np. wyrównanie do góry, do środka lub do dołu.

### Czy mogę używać innych kształtów oprócz pól tekstowych?
Tak, można stosować kotwiczenie pionowe w przypadku innych kształtów, choć najpopularniejszym przypadkiem użycia są pola tekstowe.

### Jak zmienić punkt kotwiczenia po utworzeniu pola tekstowego?
 Możesz zmienić punkt kotwiczenia, ustawiając`VerticalAnchor` właściwość obiektu kształtu pola tekstowego.

### Czy można zakotwiczyć tekst w środku pola tekstowego?
 Absolutnie! Po prostu użyj`TextBoxAnchor.Center` aby wyśrodkować tekst w pionie w polu tekstowym.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Words dla .NET?
 Sprawdź[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/) aby uzyskać więcej szczegółów i wskazówek.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
