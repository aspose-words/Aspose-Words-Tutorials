---
date: 2025-12-14
description: Узнайте, как **вставлять изображение в виде фигуры** с помощью Aspose.Words
  для Java. В этом руководстве показано, как добавлять фигуры, создавать текстовые
  блоки, размещать фигуры в таблицах, задавать соотношение сторон фигуры и добавлять
  фигурные выноски.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Использование фигур документа в Aspose.Words для Java
url: /ru/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как **insert image shape** с Aspose.Words for Java

В этом полном руководстве вы узнаете, как **insert image shape** объекты вставлять в документы Word с помощью Aspose.Words for Java. Независимо от того, создаёте ли вы отчёты, маркетинговые материалы или интерактивные формы, фигуры позволяют добавлять выноски, кнопки, текстовые поля, водяные знаки и даже SmartArt. Мы пройдём каждый шаг, объясним, зачем использовать конкретную форму, и предоставим готовый к запуску код.

## Быстрые ответы
- **Как основной способ добавить форму?** Используйте `DocumentBuilder.insertShape` или создайте экземпляр `Shape` и добавьте его в дерево документа.  
- **Можно ли вставить изображение как форму?** Да — вызовите `builder.insertImage`, а затем обращайтесь с возвращённым `Shape` как с любой другой формой.  
- **Как сохранить соотношение сторон формы?** Установите `shape.setAspectRatioLocked(true)` или `false` в зависимости от потребностей.  
- **Можно ли группировать формы?** Конечно — оберните их в `GroupShape` и вставьте группу как один узел.  
- **Работают ли диаграммы SmartArt с Aspose.Words?** Да, их можно обнаруживать и обновлять программно.

## Что такое **insert image shape**?
*Image shape* — визуальный элемент, содержащий растровую или векторную графику внутри документа Word. В Aspose.Words изображение представлено объектом `Shape`, дающим полный контроль над размером, положением, вращением и обтеканием.

## Почему стоит использовать формы в документах?
- **Визуальное воздействие:** Формы привлекают внимание к ключевой информации.  
- **Интерактивность:** Кнопки и выноски могут быть связаны с URL‑адресами или закладками.  
- **Гибкость макета:** Точно позиционируйте графику с помощью абсолютных или относительных координат.  
- **Автоматизация:** Генерируйте сложные макеты без ручного редактирования.

## Предварительные требования
- Java Development Kit (JDK 8 или выше)  
- Библиотека Aspose.Words for Java (скачать с официального сайта)  
- Базовые знания Java и объектно‑ориентированного программирования  

Скачать библиотеку можно здесь: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Как **add shape** – вставка GroupShape
`GroupShape` позволяет рассматривать несколько форм как единый объект. Это удобно для перемещения или форматирования нескольких элементов одновременно.

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

## Создание **text box shape**
Текстовое поле — контейнер, способный содержать отформатированный текст. Его также можно вращать для динамичного вида.

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

## Установка **shape aspect ratio**
Иногда требуется, чтобы форма свободно растягивалась, а иногда — сохраняла исходные пропорции. Управлять соотношением сторон просто.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Размещение **shape in table**
Вставка формы в ячейку таблицы может быть полезна для макетов отчётов. Пример ниже создаёт таблицу и затем вставляет форму‑водяной знак, охватывающую всю страницу.

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

## Добавление **callout shape**
Форма‑выноска идеально подходит для выделения заметок или предупреждений. В приведённом выше коде уже используется `ACCENT_BORDER_CALLOUT_1`; вы можете заменить `ShapeType` на любой другой вариант выноски, соответствующий вашему дизайну.

## Работа с формами SmartArt

### Обнаружение SmartArt Shapes
Диаграммы SmartArt можно программно идентифицировать, что позволяет обрабатывать или заменять их по необходимости.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Обновление SmartArt Drawings
После обнаружения вы можете обновлять графику SmartArt, отражая любые изменения данных.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Распространённые проблемы и советы
- **Форма не отображается:** Убедитесь, что форма вставлена после целевого узла с помощью `builder.insertNode`.  
- **Неожиданное вращение:** Помните, что вращение происходит вокруг центра формы; при необходимости скорректируйте `setLeft`/`setTop`.  
- **Соотношение сторон заблокировано:** По умолчанию многие формы блокируют соотношение сторон; вызовите `setAspectRatioLocked(false)`, чтобы растянуть её свободно.  
- **Не удаётся обнаружить SmartArt:** Проверьте, что используете версию Aspose.Words, поддерживающую SmartArt (v24+).

## Часто задаваемые вопросы

**В: Что такое Aspose.Words for Java?**  
О: Aspose.Words for Java — библиотека Java, позволяющая разработчикам программно создавать, изменять и конвертировать документы Word. Она предоставляет широкий набор функций и инструментов для работы с документами в различных форматах.

**В: Как скачать Aspose.Words for Java?**  
О: Скачать Aspose.Words for Java можно с сайта Aspose по следующей ссылке: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**В: Каковы преимущества использования форм в документе?**  
О: Формы добавляют визуальные элементы и интерактивность, делая документы более привлекательными и информативными. С их помощью можно создавать выноски, кнопки, изображения, водяные знаки и многое другое, улучшая общий пользовательский опыт.

**В: Можно ли настроить внешний вид форм?**  
О: Да, внешний вид форм можно настраивать, изменяя такие свойства, как размер, положение, вращение и цвет заливки. Aspose.Words for Java предоставляет обширные возможности для кастомизации форм.

**В: Совместим ли Aspose.Words for Java с SmartArt?**  
О: Да, Aspose.Words for Java поддерживает формы SmartArt, позволяя работать со сложными диаграммами и графикой в ваших документах.

---

**Последнее обновление:** 2025-12-14  
**Тестировано с:** Aspose.Words for Java 24.12 (latest)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}