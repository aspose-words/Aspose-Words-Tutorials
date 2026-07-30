---
date: 2025-12-14
description: Naucz się, jak **wstawiać kształt obrazu** za pomocą Aspose.Words for
  Java. Ten przewodnik pokazuje, jak dodawać kształty, tworzyć kształty pól tekstowych,
  umieszczać kształty w tabelach, ustawiać proporcje kształtu oraz dodawać kształty
  dymków.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Używanie kształtów dokumentu w Aspose.Words dla Javy
url: /pl/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak **wstawić kształt obrazu** przy użyciu Aspose.Words for Java

W tym kompleksowym samouczku odkryjesz, jak **wstawiać kształty obrazu** do dokumentów Word przy użyciu Aspose.Words for Java. Niezależnie od tego, czy tworzysz raporty, materiały marketingowe, czy interaktywne formularze, kształty pozwalają dodawać dymki, przyciski, pola tekstowe, znaki wodne i nawet SmartArt. Przeprowadzimy Cię przez każdy krok, wyjaśnimy, dlaczego warto użyć konkretnego kształtu, i udostępnimy gotowe do uruchomienia fragmenty kodu.

## Szybkie odpowiedzi
- **Jaki jest podstawowy sposób dodania kształtu?** Użyj `DocumentBuilder.insertShape` lub utwórz instancję `Shape` i dodaj ją do drzewa dokumentu.  
- **Czy mogę wstawić obraz jako kształt?** Tak – wywołaj `builder.insertImage`, a następnie traktuj zwrócony `Shape` jak każdy inny.  
- **Jak zachować proporcje kształtu?** Ustaw `shape.setAspectRatioLocked(true)` lub `false` w zależności od potrzeb.  
- **Czy można grupować kształty?** Oczywiście – otocz je w `GroupShape` i wstaw grupę jako pojedynczy węzeł.  
- **Czy diagramy SmartArt działają z Aspose.Words?** Tak, możesz wykrywać i aktualizować kształty SmartArt programowo.

## Co to jest **wstawianie kształtu obrazu**?
*Kształt obrazu* to element wizualny, który przechowuje grafikę rastrową lub wektorową w dokumencie Word. W Aspose.Words obraz jest reprezentowany przez obiekt `Shape`, dając pełną kontrolę nad rozmiarem, pozycją, obrotem i opakowaniem.

## Dlaczego używać kształtów w dokumentach?
- **Efekt wizualny:** Kształty przyciągają uwagę do kluczowych informacji.  
- **Interaktywność:** Przyciskom i dymkom można przypisać linki do URL‑ów lub zakładek.  
- **Elastyczność układu:** Pozycjonuj grafikę precyzyjnie przy użyciu współrzędnych bezwzględnych lub względnych.  
- **Automatyzacja:** Generuj złożone układy bez ręcznej edycji.

## Prerequisites
- Java Development Kit (JDK 8 lub nowszy)  
- Biblioteka Aspose.Words for Java (pobierz z oficjalnej strony)  
- Podstawowa znajomość Javy i programowania obiektowego  

Możesz pobrać bibliotekę tutaj: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Jak **dodać kształt** – Wstawianie GroupShape
`GroupShape` pozwala traktować kilka kształtów jako jedną jednostkę. Jest to przydatne przy przenoszeniu lub formatowaniu wielu elementów jednocześnie.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## Utwórz **kształt pola tekstowego**
Pole tekstowe to kontener, który może zawierać sformatowany tekst. Możesz je także obrócić, aby uzyskać dynamiczny wygląd.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Ustaw **proporcje kształtu**
Czasami potrzebujesz, aby kształt rozciągał się dowolnie, innym razem chcesz zachować jego oryginalne proporcje. Kontrolowanie proporcji jest proste.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Umieść **kształt w tabeli**
Osadzenie kształtu w komórce tabeli może być przydatne przy układach raportów. Poniższy przykład tworzy tabelę, a następnie wstawia kształt w stylu znaku wodnego, który rozciąga się na całą stronę.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Dodaj **kształt dymku**
Kształt dymku jest idealny do wyróżniania notatek lub ostrzeżeń. Chociaż powyższy kod już demonstruje `ACCENT_BORDER_CALLOUT_1`, możesz zamienić `ShapeType` na dowolny wariant dymku, aby dopasować go do swojego projektu.

## Working with SmartArt Shapes

### Wykrywanie kształtów SmartArt
Diagramy SmartArt można identyfikować programowo, co pozwala na ich przetwarzanie lub zamianę w razie potrzeby.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizacja rysunków SmartArt
Po wykryciu możesz odświeżyć grafiki SmartArt, aby odzwierciedlić zmiany danych.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Typowe problemy i wskazówki
- **Kształt nie pojawia się:** Upewnij się, że kształt jest wstawiany po węźle docelowym przy użyciu `builder.insertNode`.  
- **Nieoczekiwany obrót:** Pamiętaj, że obrót jest stosowany wokół środka kształtu; w razie potrzeby dostosuj `setLeft`/`setTop`.  
- **Zablokowane proporcje:** Domyślnie wiele kształtów blokuje proporcje; wywołaj `setAspectRatioLocked(false)`, aby swobodnie rozciągać.  
- **Wykrywanie SmartArt nie powodzi się:** Sprawdź, czy używasz wersji Aspose.Words obsługującej SmartArt (v24+).

## Frequently Asked Questions

**Q: Czym jest Aspose.Words for Java?**  
A: Aspose.Words for Java to biblioteka Java, która umożliwia programistom tworzenie, modyfikowanie i konwertowanie dokumentów Word programowo. Dostarcza szeroki zakres funkcji i narzędzi do pracy z dokumentami w różnych formatach.

**Q: Jak mogę pobrać Aspose.Words for Java?**  
A: Możesz pobrać Aspose.Words for Java ze strony Aspose, korzystając z tego linku: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Jakie są korzyści z używania kształtów w dokumencie?**  
A: Kształty w dokumencie dodają elementy wizualne i interaktywność, czyniąc je bardziej angażującymi i informacyjnymi. Dzięki kształtom możesz tworzyć dymki, przyciski, obrazy, znaki wodne i wiele innych, co podnosi ogólne wrażenia użytkownika.

**Q: Czy mogę dostosować wygląd kształtów?**  
A: Tak, możesz dostosować wygląd kształtów, zmieniając ich właściwości, takie jak rozmiar, pozycja, obrót i kolor wypełnienia. Aspose.Words for Java oferuje szerokie możliwości personalizacji kształtów.

**Q: Czy Aspose.Words for Java jest kompatybilny ze SmartArt?**  
A: Tak, Aspose.Words for Java obsługuje kształty SmartArt, umożliwiając pracę z złożonymi diagramami i grafiką w dokumentach.

---

**Ostatnia aktualizacja:** 2025-12-14  
**Testowano z:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}