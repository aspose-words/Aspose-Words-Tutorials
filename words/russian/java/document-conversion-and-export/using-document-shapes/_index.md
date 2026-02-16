---
date: 2026-02-16
description: Узнайте, как создать текстовое поле, добавить водяной знак со словом,
  сгруппировать несколько фигур, установить соотношение сторон фигуры и разместить
  фигуру в ячейке таблицы с помощью Aspose.Words for Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Как создать текстовое поле и использовать формы документа в Aspose.Words для
  Java
url: /ru/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Использование фигур документа в Aspose.Words для Java

## Введение в использование фигур документа в Aspose.Words для Java

В этом полном руководстве **вы узнаете, как создать text box** объекты и другие мощные фигуры с помощью Aspose.Words для Java. Фигуры позволяют обогащать документы Word выносками, кнопками, водяными знаками, SmartArt и многим другим — делая их визуально привлекательными и интерактивными. Мы пройдём через практические примеры, от вставки простого text box до группировки нескольких фигур, установки соотношения сторон и размещения фигур внутри ячеек таблицы.

## Быстрые ответы
- **Какой основной способ добавить text box?** Используйте `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Можно ли сгруппировать фигуры вместе?** Да — создайте `GroupShape` и добавьте дочерние фигуры.
- **Как заблокировать или разблокировать соотношение сторон фигуры?** Вызовите `shape.setAspectRatioLocked(true/false)`.
- **Можно ли добавить водяной знак с помощью фигуры?** Абсолютно — вставьте `Shape` с `TEXT_PLAIN_TEXT` и задайте её заливку/контур.
- **Работают ли диаграммы SmartArt с Aspose.Words?** Да — определяйте их с помощью `shape.hasSmartArt()` и обновляйте через `shape.updateSmartArtDrawing()`.

## Что такое text box и почему создавать фигуры text box?

Text box — это контейнер, способный содержать отформатированный текст, изображения или другие фигуры. Использование **create text box** в вашей автоматизации позволяет размещать плавающий контент в любой точке страницы, что идеально подходит для аннотаций, выносков или декоративных элементов без изменения основного потока документа.

## Как добавить фигуру

Прежде чем приступать к коду, убедитесь, что Aspose.Words для Java подключён к вашему проекту. Если вы ещё не добавили его, скачайте библиотеку с официального сайта:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Adding Shapes to Documents

## Как сгруппировать несколько фигур

`GroupShape` позволяет рассматривать несколько отдельных фигур как единый объект — удобно для совместного перемещения или вращения.

### Вставка GroupShape

Ниже приведён полный пример, который создаёт группу, добавляет две разные фигуры и вставляет группу в документ.

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

## Как создать text box (create text box)

### Вставка фигуры Text Box

Метод `insertShape` упрощает добавление text box. Пример ниже демонстрирует два способа позиционирования и вращения text box.

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

## Как установить соотношение сторон фигуры

### Управление соотношением сторон

Иногда требуется растянуть фигуру, не сохраняя её исходные пропорции. Ниже показан фрагмент кода, разблокирующий соотношение сторон фигуры‑изображения.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Как разместить фигуру в ячейке таблицы

### Размещение фигуры внутри ячейки таблицы

Ниже пошаговый пример, который создаёт таблицу, а затем вставляет фигуру‑водяной знак, позиционированную относительно страницы, но также может быть размещена внутри ячейки.

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

## Работа с фигурами SmartArt

### Обнаружение фигур SmartArt

Вы можете программно находить объекты SmartArt в документе, используя метод `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Обновление рисунков SmartArt

После того как вы нашли фигуры SmartArt, можно обновить их внутренние данные рисунка с помощью `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Заключение

В этом руководстве мы рассмотрели, как **create text box** объекты, группировать несколько фигур, регулировать соотношения сторон, встраивать фигуры в ячейки таблиц, добавлять водяные знаки и работать с диаграммами SmartArt с помощью Aspose.Words для Java. Эти приёмы позволяют программно создавать богато оформленные, интерактивные документы Word.

## FAQ's

### Что такое Aspose.Words для Java?

Aspose.Words для Java — это библиотека Java, позволяющая разработчикам программно создавать, изменять и конвертировать документы Word. Она предоставляет широкий набор функций и инструментов для работы с документами в различных форматах.

### Как я могу скачать Aspose.Words для Java?

Вы можете скачать Aspose.Words для Java с сайта Aspose, перейдя по этой ссылке: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Каковы преимущества использования фигур в документе?

Фигуры добавляют визуальные элементы и интерактивность вашим документам, делая их более привлекательными и информативными. С их помощью можно создавать выноски, кнопки, изображения, водяные знаки и многое другое, улучшая общий пользовательский опыт.

### Можно ли настроить внешний вид фигур?

Да, внешний вид фигур можно настраивать, изменяя такие свойства, как размер, позиция, вращение и цвет заливки. Aspose.Words для Java предоставляет обширные возможности кастомизации фигур.

### Совместим ли Aspose.Words для Java с SmartArt?

Да, Aspose.Words для Java поддерживает фигуры SmartArt, позволяя работать со сложными диаграммами и графикой в ваших документах.

## Frequently Asked Questions

**Q: Можно ли объединить text box с изображением внутри одной фигуры?**  
A: Да. Вставьте изображение в фигуру text box с помощью `builder.insertImage()` после создания фигуры, затем при необходимости отрегулируйте её расположение.

**Q: Как обеспечить, чтобы водяной знак отображался позади всего содержимого документа?**  
A: Установите `WrapType` фигуры в `NONE` и задайте `RelativeHorizontalPosition` и `RelativeVerticalPosition` в `PAGE`. Это разместит водяной знак за основным потоком.

**Q: Можно ли анимировать сгруппированную фигуру в Word?**  
A: Хотя Aspose.Words может создавать и группировать фигуры, функции анимации не поддерживаются, так как они зависят от возможностей пользовательского интерфейса Word.

**Q: Какая версия Aspose.Words требуется для поддержки SmartArt?**  
A: Обнаружение и обновление SmartArt доступны, начиная с Aspose.Words 20.9 для Java и более новых версий.

**Q: Эффективно ли библиотека работает с большими документами, содержащими множество фигур?**  
A: Да. Используйте `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` или более новую версию, чтобы повысить производительность при работе с документами, содержащими большое количество фигур.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}