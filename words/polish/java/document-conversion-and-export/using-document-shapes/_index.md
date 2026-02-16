---
date: 2026-02-16
description: Dowiedz się, jak utworzyć pole tekstowe, dodać znak wodny w postaci słowa,
  grupować wiele kształtów, ustawić proporcje kształtu oraz umieścić kształt w komórce
  tabeli przy użyciu Aspose.Words dla Javy.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Jak utworzyć pole tekstowe i używać kształtów dokumentu w Aspose.Words dla
  Javy
url: /pl/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Używanie kształtów dokumentu w Aspose.Words dla Javy

## Wprowadzenie do używania kształtów dokumentu w Aspose.Words dla Javy

W tym obszernym przewodniku, **dowiesz się, jak tworzyć obiekty text box** i inne potężne kształty przy użyciu Aspose.Words dla Javy. Kształty pozwalają wzbogacić dokumenty Word o dymki, przyciski, znaki wodne, SmartArt i wiele innych — czyniąc je wizualnie atrakcyjnymi i interaktywnymi. Przejdziemy przez praktyczne przykłady, od wstawiania prostego text box po grupowanie wielu kształtów, ustawianie proporcji i umieszczanie kształtów w komórkach tabel.

## Szybkie odpowiedzi
- **Jaki jest podstawowy sposób dodania text box?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Czy mogę grupować kształty razem?** Yes – create a `GroupShape` and append child shapes.
- **Jak zablokować lub odblokować proporcje kształtu?** Call `shape.setAspectRatioLocked(true/false)`.
- **Czy można dodać znak wodny przy użyciu kształtu?** Absolutely – insert a `Shape` with `TEXT_PLAIN_TEXT` and set its fill/stroke.
- **Czy diagramy SmartArt działają w Aspose.Words?** Yes – detect with `shape.hasSmartArt()` and update via `shape.updateSmartArtDrawing()`.

## Czym jest text box i dlaczego tworzyć kształty text box?

Text box jest kontenerem, który może przechowywać sformatowany tekst, obrazy lub inne kształty. Używanie **create text box** w automatyzacji pozwala umieścić pływającą treść w dowolnym miejscu na stronie, idealne do adnotacji, dymków lub elementów dekoracyjnych bez zmiany głównego przepływu dokumentu.

## Jak dodać kształt

Before we dive into code, ensure Aspose.Words for Java is referenced in your project. If you haven’t added it yet, download the library from the official site:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Dodawanie kształtów do dokumentów

## Jak grupować wiele kształtów

A `GroupShape` lets you treat several individual shapes as a single unit—useful for moving or rotating them together.

### Wstawianie GroupShape

Below is a complete example that creates a group, adds two different shapes, and inserts the group into the document.

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

## Jak utworzyć text box (create text box)

### Wstawianie kształtu Text Box

The `insertShape` method makes it straightforward to add a text box. The example below shows two ways to position and rotate a text box.

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

## Jak ustawić proporcje kształtu

### Zarządzanie proporcjami

Sometimes you need a shape to stretch without preserving its original proportions. The following snippet demonstrates unlocking the aspect ratio of an image shape.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Jak umieścić kształt w komórce tabeli

### Umieszczanie kształtu wewnątrz komórki tabeli

Below is a step‑by‑step example that builds a table, then inserts a watermark shape that is positioned relative to the page but can also be placed inside a cell.

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

## Praca z kształtami SmartArt

### Wykrywanie kształtów SmartArt

You can programmatically find SmartArt objects in a document using the `hasSmartArt()` method.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizowanie rysunków SmartArt

Once you’ve located SmartArt shapes, you can refresh their internal drawing data with `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Podsumowanie

In this guide, we’ve covered how to **create text box** objects, group multiple shapes, adjust aspect ratios, embed shapes inside table cells, add watermarks, and work with SmartArt diagrams using Aspose.Words for Java. These techniques empower you to build richly formatted, interactive Word documents programmatically.

## FAQ

### Czym jest Aspose.Words dla Javy?

Aspose.Words for Java is a Java library that allows developers to create, modify, and convert Word documents programmatically. It provides a wide range of features and tools for working with documents in various formats.

### Jak mogę pobrać Aspose.Words dla Javy?

You can download Aspose.Words for Java from the Aspose website by following this link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Jakie są korzyści z używania kształtów dokumentu?

Document shapes add visual elements and interactivity to your documents, making them more engaging and informative. With shapes, you can create callouts, buttons, images, watermarks, and more, enhancing the overall user experience.

### Czy mogę dostosować wygląd kształtów?

Yes, you can customize the appearance of shapes by adjusting their properties such as size, position, rotation, and fill color. Aspose.Words for Java provides extensive options for shape customization.

### Czy Aspose.Words dla Javy jest kompatybilny ze SmartArt?

Yes, Aspose.Words for Java supports SmartArt shapes, allowing you to work with complex diagrams and graphics in your documents.

## Najczęściej zadawane pytania

**Q: Czy mogę połączyć text box z obrazem w tym samym kształcie?**  
A: Yes. Insert an image into the text box shape using `builder.insertImage()` after creating the shape, then adjust its layout as needed.

**Q: Jak zapewnić, że znak wodny pojawia się za całą treścią dokumentu?**  
A: Set the shape’s `WrapType` to `NONE` and adjust its `RelativeHorizontalPosition` and `RelativeVerticalPosition` to `PAGE`. This positions the watermark behind the main flow.

**Q: Czy można animować grupowany kształt w Wordzie?**  
A: While Aspose.Words can create and group shapes, animation features are not supported because they rely on Word’s UI capabilities.

**Q: Jakiej wersji Aspose.Words potrzebuję do obsługi SmartArt?**  
A: SmartArt detection and updating are available starting from Aspose.Words 20.9 for Java and later.

**Q: Czy biblioteka radzi sobie efektywnie z dużymi dokumentami zawierającymi wiele kształtów?**  
A: Yes. Use `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` or higher to improve performance on documents with many shapes.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}