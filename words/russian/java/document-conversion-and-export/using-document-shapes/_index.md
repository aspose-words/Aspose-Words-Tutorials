---
title: Использование форм документов в Aspose.Words для Java
linktitle: Использование форм документа
second_title: API обработки документов Java Aspose.Words
description: Откройте для себя мощь форм документов в Aspose.Words для Java. Научитесь создавать визуально привлекательные документы с помощью пошаговых примеров.
weight: 14
url: /ru/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование форм документов в Aspose.Words для Java


## Введение в использование фигур документов в Aspose.Words для Java

В этом подробном руководстве мы погрузимся в мир форм документов в Aspose.Words для Java. Формы являются важнейшими элементами, когда дело доходит до создания визуально привлекательных и интерактивных документов. Если вам нужно добавить выноски, кнопки, изображения или водяные знаки, Aspose.Words для Java предоставляет инструменты для эффективного выполнения этой задачи. Давайте рассмотрим, как использовать эти формы шаг за шагом с примерами исходного кода.

## Начало работы с формами документов

 Прежде чем перейти к коду, давайте настроим нашу среду. Убедитесь, что Aspose.Words for Java интегрирован в ваш проект. Если вы еще этого не сделали, вы можете загрузить его с веб-сайта Aspose[Загрузить Aspose.Words для Java](https://releases.aspose.com/words/java/)

## Добавление фигур в документы

### Вставка GroupShape

 А`GroupShape` позволяет группировать несколько фигур вместе. Вот как можно создать и вставить`GroupShape`:

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

### Вставка формы текстового поля

 Чтобы вставить форму текстового поля, вы можете использовать`insertShape` метод, как показано в примере ниже:

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

## Манипулирование свойствами формы

### Управление соотношением сторон

Вы можете контролировать, заблокировано ли соотношение сторон фигуры или нет. Вот как разблокировать соотношение сторон фигуры:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Размещение фигуры в ячейке таблицы

Если вам необходимо поместить фигуру внутрь ячейки таблицы, вы можете сделать это с помощью следующего кода:

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
watermark.isLayoutInCell(true); // Отобразить фигуру за пределами ячейки таблицы, если она будет помещена в ячейку.
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

Вы можете обнаружить фигуры SmartArt в документе, используя следующий код:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Обновление рисунков SmartArt

Чтобы обновить рисунки SmartArt в документе, используйте следующий код:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Заключение

В этом руководстве мы изучили мир форм документов в Aspose.Words для Java. Вы узнали, как добавлять различные формы в документы, управлять их свойствами и работать с формами SmartArt. С этими знаниями вы сможете с легкостью создавать визуально привлекательные и интерактивные документы.

## Часто задаваемые вопросы

### Что такое Aspose.Words для Java?

Aspose.Words for Java — это библиотека Java, которая позволяет разработчикам программно создавать, изменять и конвертировать документы Word. Она предоставляет широкий спектр функций и инструментов для работы с документами в различных форматах.

### Как загрузить Aspose.Words для Java?

 Вы можете загрузить Aspose.Words для Java с веб-сайта Aspose, перейдя по этой ссылке:[Загрузить Aspose.Words для Java](https://releases.aspose.com/words/java/)

### Каковы преимущества использования форм документов?

Формы документов добавляют визуальные элементы и интерактивность в ваши документы, делая их более интересными и информативными. С помощью форм вы можете создавать выноски, кнопки, изображения, водяные знаки и многое другое, улучшая общее взаимодействие с пользователем.

### Могу ли я настроить внешний вид фигур?

Да, вы можете настроить внешний вид фигур, изменив их свойства, такие как размер, положение, поворот и цвет заливки. Aspose.Words для Java предоставляет обширные возможности для настройки фигур.

### Совместим ли Aspose.Words для Java со SmartArt?

Да, Aspose.Words для Java поддерживает фигуры SmartArt, что позволяет работать со сложными диаграммами и графикой в документах.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
