---
category: general
date: 2026-09-24
description: Узнайте, как создать пустой документ Word на Java и сгруппировать фигуры,
  такие как прямоугольники и линии, с помощью Aspose.Words. Включает пошаговый код.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: ru
lastmod: 2026-09-24
og_description: Создайте пустой документ Word на Java и узнайте, как группировать
  фигуры, добавить прямоугольник и задать размер фигуры с помощью Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Создайте пустой документ Word и сгруппируйте фигуры в Java — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Как создать пустой документ Word и сгруппировать фигуры в Java
url: /ru/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и группировать фигуры в Java

Если вам нужно **создать пустой документ Word** и затем организовать несколько графических объектов, это руководство покажет вам, как это сделать. С помощью Aspose.Words for Java вы можете вставить групповую фигуру, добавить прямоугольную фигуру, нарисовать линию и управлять размером и положением каждой фигуры — всё в одной исполняемой программе.

Вы пройдёте каждый шаг, от инициализации документа до сохранения конечного `.docx`. К концу вы поймёте **как группировать фигуры**, **добавлять прямоугольную фигуру** и **устанавливать размер фигуры**, чтобы ваши файлы Word выглядели точно так, как задумано.

## Требования

- Java 17 или новее (код компилируется на любой современной JDK)
- Библиотека Aspose.Words for Java (скачайте с [Aspose website](https://products.aspose.com/words/java))
- IDE или система сборки (Maven/Gradle), позволяющая добавить Aspose.Words JAR в classpath
- Базовые знания синтаксиса Java

> **Совет:** Используйте Maven для управления зависимостями; добавьте `com.aspose:aspose-words:23.12` (или последнюю версию) в ваш `pom.xml`.

## Шаг 1: Создать пустой документ Word

Первая задача — **создать пустой документ Word**. Это даст вам чистый холст, на который вы позже сможете вставлять фигуры.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Почему это важно:* Объект `Document` представляет весь файл `.docx`. Начало с пустого документа гарантирует, что скрытое форматирование не будет влиять на добавляемые фигуры.

## Шаг 2: Вставить групповую фигуру — контейнер для нескольких объектов

**Групповая фигура** работает как контейнер, позволяющий перемещать, изменять размер или вращать несколько фигур одновременно. Это основа **как группировать фигуры** в Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Объяснение:* Метод `insertGroupShape` создаёт объект `GroupShape` и размещает его в текущем положении курсора. Все последующие фигуры, которые вы `appendChild` к этой группе, будут рассматриваться как единое целое.

## Шаг 3: Добавить прямоугольную фигуру и задать её размер

Теперь мы **добавляем прямоугольную фигуру** в группу и **точно задаём размер фигуры**.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Почему необходимо задавать размер фигуры:* Ширина и высота определяют, как прямоугольник будет выглядеть на странице. Методы `setLeft` и `setTop` позиционируют прямоугольник относительно начала группы, обеспечивая точный контроль расположения.

## Шаг 4: Добавить линию и настроить её размеры

Линия — ещё один распространённый графический объект. Мы применим логику, похожую на **добавление прямоугольной фигуры**, к линии, показывая, что те же принципы размеров применимы.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Ключевой момент:* Хотя у линии нет высоты, вы всё равно используете `setWidth` для определения её длины. Позиционирование (`setLeft`, `setTop`) следует той же системе координат, что и у других фигур.

## Шаг 5: Сохранить документ с групповыми фигурами

Наконец, зафиксируйте изменения, сохранив документ. Это создаст файл `.docx`, который можно открыть в Microsoft Word для проверки результата.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Ожидаемый результат:** При открытии `GroupShapeDemo.docx` вы увидите пустую страницу с группированным прямоугольником и линией. Выбор любой фигуры выделяет всю группу, позволяя перемещать их вместе.

## Часто задаваемые вопросы и обработка граничных случаев

| Вопрос | Ответ |
|----------|--------|
| *Могу ли я добавить более двух фигур в группу?* | Да. Вызовите `group.appendChild(yourShape)` для каждой дополнительной фигуры. |
| *Что если мне нужен другой единица измерения (например, сантиметры) для размера?* | Aspose.Words использует пункты (1 пункт = 1/72 дюйма). Преобразуйте с помощью `Points = centimeters * 28.3465`. |
| *Сохранит ли группа своё расположение, когда документ откроют на другом компьютере?* | Абсолютно. Все данные о размере и положении сохраняются в файле `.docx`, делая макет переносимым. |
| *Как позже разгруппировать фигуры?* | Получите объект `GroupShape`, затем пройдитесь по `group.getChildNodes(NodeType.SHAPE, true)` и переместите каждый дочерний элемент из группы. |
| *Что если мне нужно повернуть всю группу?* | Вызовите `group.setRotationAngle(double angleInDegrees)` перед сохранением. |

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в свою IDE. Она включает все необходимые импорты и комментарии.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Запустите программу, откройте `GroupShapeDemo.docx` в Microsoft Word, и вы увидите сгруппированные фигуры точно так, как описано.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **группировать фигуры в Word**, **добавлять прямоугольную фигуру** и **задавать размер фигуры** с помощью Aspose.Words for Java. Размещая фигуры внутри `GroupShape`, вы получаете полный контроль над совместным позиционированием, масштабированием и вращением — идеально для диаграмм, блок‑схем или пользовательской графики, встроенной в автоматизированные отчёты.

**Следующие шаги:**  
- Исследуйте **как группировать фигуры** с более сложными объектами, такими как изображения или текстовые поля.  
- Поэкспериментируйте с `setRotationAngle`, чтобы вращать всю группу.  
- Скомбинируйте эту технику с слиянием почты (mail‑merge), чтобы генерировать персонализированные документы, включающие фирменную графику.

Не стесняйтесь адаптировать код под свои проекты и делиться результатами в комментариях!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать прямоугольную фигуру в Word с Java — Полное руководство](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Создать документ Word Java — Добавить прямоугольную фигуру с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Создать групповую фигуру в документе Word с использованием Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}