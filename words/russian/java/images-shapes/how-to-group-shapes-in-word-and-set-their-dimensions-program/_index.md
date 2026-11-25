---
category: general
date: 2026-11-25
description: Как группировать фигуры в Word с помощью Java и как задавать размеры
  фигур в файле DOCX с использованием Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: ru
lastmod: 2026-11-25
og_description: Как сгруппировать фигуры в Word с помощью Aspose.Words Java API и
  быстро задать размер фигуры. Следуйте полному пошаговому решению.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Как группировать фигуры в Word и задавать их размеры – руководство по Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Как группировать фигуры в Word и задавать их размеры программно
url: /ru/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word и программно задавать их размеры

Если вам нужно **как группировать фигуры в Word** и контролировать их точный размер, это руководство покажет полное, готовое к запуску решение. С помощью Aspose.Words for Java вы можете создать прямоугольник, эллипс, добавить их в `GroupShape`, а затем **как задать размеры фигуры** такие как ширина и высота в одном файле DOCX.

Вы узнаете, как:

* Создать новый документ Word с нуля.  
* Вставить `GroupShape` (новый API в версии 24.9).  
* Добавить прямоугольник и эллипс в группу.  
* **Установить размер фигуры в Word** точно с помощью `setWidth` и `setHeight`.  
* Сохранить документ на диск.

Никакие внешние инструменты не требуются — только Java 17+, Maven и библиотека Aspose.Words for Java.

## Требования

* Java Development Kit 17 или новее.  
* Maven (или Gradle) для управления зависимостями.  
* Aspose.Words for Java 24.9 или новее (API `GroupShape` был добавлен в 24.9).  
* Базовое знакомство с синтаксисом Java и объектно‑ориентированными концепциями.

Если вы ещё не добавили Aspose.Words в свой проект, включите следующую зависимость Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Шаг 1: Создать новый документ и DocumentBuilder

Класс `Document` представляет весь файл Word, а `DocumentBuilder` предоставляет удобный способ добавлять содержимое.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Зачем нужен этот шаг?*  
Создание чистого `Document` даёт вам пустой холст. `DocumentBuilder` — это высокоуровневый помощник, позволяющий вставлять абзацы, таблицы и, в данном случае, фигуры.

## Шаг 2: Вставить GroupShape (новый API в версии 24.9)

`GroupShape` работает как контейнер; любая добавленная фигура становится частью одной визуальной группы.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Зачем использовать `GroupShape`?*  
Группировка фигур упрощает перемещение, вращение или применение форматирования к нескольким объектам одновременно. API был добавлен в 24.9, поэтому в более старых версиях эта строка не скомпилируется.

## Шаг 3: Создать прямоугольник, задать его размер и добавить в группу

Здесь мы демонстрируем **как задать размеры фигуры** для прямоугольника.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Зачем явно задавать ширину и высоту?*  
Word хранит размер фигуры в пунктах. Вызывая `setWidth` и `setHeight`, вы контролируете точный визуальный след, что важно при необходимости точного макета или экспорта в PDF.

## Шаг 4: Создать эллипс, задать его размер и добавить в ту же группу

Та же техника **установки размера фигуры в Word** работает для любого типа фигур.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Зачем добавлять эллипс в тот же `GroupShape`?*  
Обе фигуры будут перемещаться вместе как единое целое. Это полезно при создании иконок, логотипов или сложных диаграмм, которые должны оставаться выровненными.

## Шаг 5: Сохранить документ с группированными фигурами

Наконец, сохраняем файл DOCX на диск.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Запуск этой программы создаёт файл **GroupShape.docx**, содержащий прямоугольник и эллипс, сгруппированные вместе. При открытии файла в Microsoft Word вы увидите, что две фигуры ведут себя как один объект — их можно перетаскивать, изменять размер или вращать совместно.

### Ожидаемый результат

* Документ Word (`GroupShape.docx`) из одной страницы.  
* `GroupShape`, содержащий прямоугольник 100 × 50 pt и эллипс 80 × 80 pt.  
* Выбор любой фигуры выделяет всю группу.

## Часто задаваемые вопросы и особые случаи

### Как изменить позицию группированных фигур?

После создания `GroupShape` можно задать свойства `left` и `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Эти координаты также измеряются в пунктах.

### Что делать, если нужно добавить более двух фигур?

`GroupShape` работает как любой другой контейнерный узел. Вызывайте `groupShape.appendChild(yourShape)` для каждой дополнительной фигуры. API не ограничивает количество дочерних элементов.

### Можно ли применить стиль (цвет заливки, толщину линии) к отдельным фигурам?

Да. Каждый объект `Shape` раскрывает свойства форматирования:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Работает ли код со старыми версиями Aspose.Words?

Метод `insertGroupShape` был введён в версии 24.9. Если вы используете более раннюю версию, придётся создавать `GroupShape` вручную через дерево узлов, что более сложно. Рекомендуется обновить библиотеку.

## Профессиональные советы

* **Используйте пункты для согласованности** — внутренней единицей Word является пункт (1/72 дюйма). Преобразование из пикселей или сантиметров может привести к неожиданным размерам.  
* **Группируйте перед позиционированием** — задавайте позицию `GroupShape` после добавления всех его дочерних элементов; иначе может потребоваться пересчёт смещений.  
* **Повторно используйте DocumentBuilder** — можно вставлять несколько групп в один документ, перемещая курсор билдера (`builder.moveTo`) перед каждым вызовом `insertGroupShape`.

## Заключение

Теперь у вас есть полное, сквозное пример **как группировать фигуры в Word** и **как задавать размеры фигур** с помощью Aspose.Words for Java. В руководстве рассмотрены создание документа, вставка `GroupShape`, добавление прямоугольника и эллипса, точная установка их размеров и сохранение результата.  

Далее вы можете исследовать:

* Добавление текстовых полей или изображений в ту же группу.  
* Анимацию группированных фигур с помощью функций SmartArt в Word (через API).  
* Экспорт группированных фигур в PDF или SVG для веб‑использования.

Не стесняйтесь экспериментировать с различными типами фигур, размерами и позициями — группировка даёт мощный контроль над сложными макетами в документах Word.


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}