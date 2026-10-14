---
category: general
date: 2026-10-13
description: Узнайте, как создавать сгруппированные фигуры в Word с помощью Java.
  Это руководство покажет, как вставить группу фигур, добавить линию в группу и сгруппировать
  несколько фигур по всему документу.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: ru
lastmod: 2026-10-13
og_description: Создавайте сгруппированные фигуры в Word с помощью Java. Следуйте
  этому полному руководству, чтобы вставить группу фигур, добавить линию в группу
  и объединить несколько фигур в документах Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Создание сгруппированных фигур в Word с помощью Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Как создать сгруппированные фигуры в документе Word с помощью Java
url: /ru/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать сгруппированные фигуры в документе Word с помощью Java

Если вам нужно **создать сгруппированные фигуры** в файле Microsoft Word из Java, этот учебник проведёт вас через весь процесс. Вы увидите, как **вставить группу фигур**, разместить прямоугольник и линию внутри одного контейнера и, наконец, сохранить документ с группированными графическими элементами.

Группировка фигур упрощает перемещение, изменение размера или стилизацию нескольких графических объектов как единого блока — идеально для диаграмм, блок‑схем или пользовательских украшений страниц. К концу руководства вы сможете **добавить линию в группу**, **группировать несколько фигур в Word** документы и повторно использовать эту технику для любого количества фигур.

## Предварительные требования

- Java 17 или более поздняя версия, установленная на вашей машине разработки.  
- Лицензия Aspose.Words for Java (или бесплатная оценочная версия).  
- Maven или Gradle проект, в который вы можете добавить зависимость Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Дополнительные библиотеки не требуются.

## Шаг 1: Вставить контейнер группы фигур

Первый шаг — **вставить группу фигур** в документ. Этот контейнер будет содержать все последующие фигуры.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` создаёт пустой объект `Shape` типа `GROUPSHAPE`. Считайте его прозрачным холстом, который может содержать другие графические объекты.

## Шаг 2: Добавить прямоугольник в группу

Прямоугольник часто служит визуальным фоном для группы фигур.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Установка `Left` и `Top` в `0` размещает прямоугольник в левом верхнем углу группы. Вы можете изменить эти значения, чтобы сместить фигуру внутри группы.

## Шаг 3: **Добавить линию в группу** – создать линейную фигуру

Теперь мы **добавляем линию в группу**. Линия появится под прямоугольником.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Свойство `Top` перемещает линию на 60 пунктов ниже прямоугольника, создавая простую вертикальную компоновку. При необходимости можно также задать `Left` для горизонтального смещения.

## Шаг 4: Сохранить документ с группированными фигурами

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Когда вы откроете `GroupShapeDemo.docx` в Microsoft Word, вы увидите одну группу, содержащую как прямоугольник, так и линию. Выбор группы позволяет перемещать обе фигуры одновременно, что демонстрирует, что вы успешно **группировали несколько фигур в Word**.

## Полный, исполняемый пример

Ниже приведена полная программа со всеми импортами и обработкой ошибок. Скопируйте её в свою IDE, замените `YOUR_DIRECTORY` на существующий путь к папке и запустите.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Ожидаемый результат

- Файл с именем `GroupShapeDemo.docx` появляется в целевой папке.  
- Открывая файл в Word, вы видите один сгруппированный объект, содержащий прямоугольник сверху и линию снизу.  
- Перетаскивание группы перемещает обе фигуры вместе, подтверждая, что вы успешно **создали сгруппированные фигуры**.

## Советы и распространённые подводные камни

- **Pro tip:** Если вам нужно вращать или стилизовать отдельные фигуры внутри группы, вызовите соответствующие сеттеры (`setRotation`, `getFill().setForeColor` и т.д.) до их добавления в группу. Группа сохранит эти визуальные свойства.  
- **Watch out for:** Если забыть установить свойство `Top` для линии, она может перекрывать прямоугольник, из‑за чего группа будет выглядеть загромождённой.  
- **Edge case:** При добавлении более двух фигур помните, что координаты каждого дочернего элемента относительны к началу группы (0,0). Планируйте расположение соответственно.  
- **Performance note:** Группировка большого количества фигур (сотни) может немного увеличить размер файла, но упрощает последующее редактирование в Word.

## Как программно **группировать несколько фигур в Word** документы

Показанный выше шаблон — создать контейнер группы, настроить каждую дочернюю фигуру и добавить её — работает для любого количества фигур: кругов, изображений, текстовых полей и т.д. Просто повторяйте шаги «создать фигуру → задать свойства → добавить» перед вызовом `doc.save()`.

Если вам нужно **добавить линию в группу** после того, как группа уже содержит другие фигуры, вы можете получить существующую группу с помощью:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Это демонстрирует, что вы можете изменять группу в любой момент жизненного цикла документа.

## Заключение

Теперь вы знаете, как **создать сгруппированные фигуры** в документе Word с помощью Java и Aspose.Words. **Вставляя группу фигур**, **добавляя линию в группу** и **группируя несколько фигур в Word**, вы можете создавать сложные рисунки, которые ведут себя как один объект — идеально для диаграмм, шаблонов и автоматической генерации отчётов.

Далее изучите связанные темы:

- **Applying styles to grouped shapes** – узнайте, как задать цвета заливки, границы и эффекты для всех дочерних элементов одновременно.  
- **Exporting grouped shapes to PDF** – посмотрите, как та же группа сохраняется при конвертации документа в PDF.  
- **Animating shapes with VBA** – комбинируйте группы, созданные в Java, с макросами Word для интерактивных документов.

Не стесняйтесь экспериментировать с различными типами фигур, размерами и позициями. Группировка даёт гибкость рассматривать множество объектов как один, упрощая как код, так и взаимодействие с пользователем. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}