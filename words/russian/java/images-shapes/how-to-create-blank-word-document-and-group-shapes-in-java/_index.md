---
category: general
date: 2026-09-27
description: Создайте пустой документ Word на Java и сгруппируйте фигуры с помощью
  Aspose.Words. Узнайте, как задать размер фигуры, установить цвет её заливки и добавить
  дочерний элемент в группу.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: ru
lastmod: 2026-09-27
og_description: Создайте пустой документ Word на Java с помощью Aspose.Words. Этот
  учебник показывает, как группировать фигуры в Word, задавать размер фигуры, устанавливать
  цвет её заливки и добавлять дочерний элемент в группу.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Создайте пустой документ Word и сгруппируйте фигуры в Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Как создать пустой документ Word и сгруппировать фигуры в Java
url: /ru/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и сгруппировать фигуры в Java

Если вам нужно **создать пустой документ Word** программно, это руководство покажет, как сделать это с помощью Aspose.Words for Java. Вы также узнаете, как **группировать фигуры в Word**, задавать размер каждой фигуры, применять цвет заливки и **добавлять дочерний элемент в группу**, чтобы объекты вели себя как единое целое.

Работа с файлами Word из кода избавляет от ручного форматирования и позволяет автоматически генерировать отчёты, контракты или маркетинговые брошюры. К концу этого руководства у вас будет готовая Java‑программа, которая создаёт файл `.docx` с синим прямоугольником и изображением, оба сгруппированы вместе.

## Prerequisites

- Установлен Java 17 (или любой современный JDK).
- Maven или Gradle для управления зависимостями.
- Лицензия Aspose.Words for Java (бесплатная оценочная версия подходит для тестирования).
- Пример файла изображения (например, `sample.jpg`), размещённый в папке, к которой вы можете обратиться из кода.

> **Совет:** Храните файлы изображений в каталоге `resources` и загружайте их с помощью `ClassLoader.getResourceAsStream`, чтобы избежать жёстко прописанных абсолютных путей.

## Шаг 1: Создать пустой документ Word и добавить GroupShape

The first step is to instantiate a new `Document` object, which represents an empty Word file, and then insert a `GroupShape`. The group will serve as a container for any shapes you add later.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Почему это важно:* `GroupShape` позволяет перемещать, вращать или форматировать несколько фигур одновременно, что необходимо для сложных макетов, таких как диаграммы или водяные знаки.

## Шаг 2: Вставить прямоугольник и **задать размер фигуры**

Next, create a rectangle, define its dimensions, and add it to the group. This demonstrates the **set shape size** operation.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Объяснение:* `setWidth` и `setHeight` задают точный размер фигуры в пунктах (1 пункт = 1/72 дюйма). Корректируйте эти значения в соответствии с требованиями вашего макета.

## Шаг 3: **Задать цвет заливки фигуры** для прямоугольника

The rectangle’s background is set to blue using `setFillColor`. You can use any `java.awt.Color` constant or create a custom RGB color.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Почему это полезно:* Цвета заливки помогают визуально различать объекты, особенно при последующем экспорте документа в PDF или печати.

## Шаг 4: Вставить изображение и **добавить дочерний элемент в группу**

Now add an image to the same `GroupShape`. The image is inserted via `DocumentBuilder.insertImage`, then appended to the group so it moves together with the rectangle.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Особый случай:* Если путь к изображению неверен, Aspose.Words бросает `FileNotFoundException`. Используйте относительный путь или загрузите изображение из ресурсов, чтобы избежать этой проблемы.

## Шаг 5: **Сохранить документ с сгруппированными фигурами**

Finally, write the document to disk. The resulting file will contain the rectangle and the image grouped together.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Ожидаемый результат

- Файл с именем `GroupShape.docx` появляется в указанном каталоге.
- Открытие файла в Microsoft Word показывает пустую страницу с синим прямоугольником и выбранным изображением, оба выделены как один объект (их можно перемещать или изменять размер совместно).

![создать пустой документ Word с группированными фигурами](/images/grouped-shapes.png "создать пустой документ Word с группированными фигурами")

*Скриншот выше демонстрирует окончательные сгруппированные фигуры внутри только что созданного документа Word.*

## Общие варианты и дополнительные советы

| Ситуация | Как решить |
|-----------|-----------------|
| **Несколько изображений** | Вставляйте каждое изображение с помощью `builder.insertImage` и вызывайте `group.appendChild(picture)` для каждого из них. |
| **Разные типы фигур** | Используйте `ShapeType.OVAL`, `ShapeType.LINE` и т.д. при создании объекта `Shape`. |
| **Изменение позиции группы** | После добавления всех дочерних элементов задайте `group.setLeft(x)` и `group.setTop(y)`, чтобы переместить всю группу. |
| **Экспорт в PDF** | Вызовите `doc.save("output.pdf")` после группировки; PDF сохранит группировку. |
| **Применение лицензии** | Если вы используете оценочную версию, появится водяной знак. Установите действующую лицензию, чтобы его убрать. |

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, вставить **GroupShape**, **задать размер фигуры**, **задать цвет заливки фигуры** и **добавлять дочерний элемент в группу** с помощью Aspose.Words for Java. Этот подход позволяет создавать сложные программные макеты, которые позже можно редактировать в Word или экспортировать в другие форматы.

Далее изучайте, как **группировать фигуры в Word** с помощью текстовых полей, добавлять гиперссылки к фигурам или автоматизировать генерацию многостраничных отчётов. Принципы те же — просто создавайте дополнительные фигуры, настраивайте их свойства и добавляйте их в одну группу.

Удачной разработки!

## Что стоит изучить дальше?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Создать прямоугольную фигуру в Word с Java – Полное руководство](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Создать документ Word Java – Добавить прямоугольную фигуру с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Создать групповую фигуру в документе Word с использованием Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}