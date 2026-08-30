---
category: general
date: 2026-08-14
description: Группировка фигур в Word с помощью Java и Aspose.Words. Узнайте, как
  создать прямоугольную фигуру, задать её размеры и сгруппировать несколько фигур
  в пустом документе Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: ru
lastmod: 2026-08-14
og_description: Группировка фигур в Word с помощью Aspose.Words для Java. Создайте
  пустой документ Word, создайте прямоугольную фигуру, задайте её размеры и сгруппируйте
  несколько фигур за считанные минуты.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Группировка фигур в Word – пример на Java для разработчиков
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Группировка фигур в Word — полное руководство по программированию
url: /ru/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Группировка фигур в Word – полное руководство по программированию

Если вам нужно **группировать фигуры в Word**, это руководство проведёт вас через весь процесс с использованием Java и Aspose.Words. Вы узнаете, как **создать пустой документ Word**, **создать прямоугольную фигуру**, **задать размеры фигуры** и, наконец, **группировать несколько фигур**, чтобы они вели себя как один объект.

Работа с фигурами в файле Word часто напоминает рисование на холсте без кисти. К концу этого руководства у вас будет переиспользуемый фрагмент кода, который можно вставить в любой Java‑проект, будь то генерация отчётов, счетов‑фактур или пользовательских шаблонов.

## Что вам понадобится

- Java 8 или новее
- Aspose.Words for Java (последняя версия, например, 24.9)
- IDE, например IntelliJ IDEA или Eclipse
- Базовое знакомство с объектно‑ориентированным программированием

Все эти требования бесплатны, а код ниже компилируется с единственной Maven‑зависимостью:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Шаг 1: Создание пустого документа Word и инициализация builder‑а

Первое, что нужно сделать, — **создать пустой документ Word**. Это даст вам чистый холст, на который позже можно будет вставлять фигуры.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет весь файл *.docx*, а `DocumentBuilder` — вспомогательный объект, который вставляет абзацы, таблицы и фигуры. Инициализация обоих объектов является фундаментом любой задачи автоматизации Word.

## Шаг 2: Вставка контейнера групповой фигуры

**Групповая фигура** работает как папка, в которой могут находиться другие фигуры. Сначала создаём контейнер фиксированного размера 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Метод `insertGroupShape` возвращает объект `GroupShape`. Все последующие фигуры, которые вы хотите рассматривать как единое целое, должны быть добавлены к этому объекту.

## Шаг 3: Создание прямоугольных фигур и задание их размеров

Теперь **создаём объекты прямоугольных фигур**, задаём их размер и позицию внутри группы. Этот шаг также демонстрирует, как **точно задать размеры фигуры**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Оба прямоугольника имеют одинаковые размеры, но их свойства `left` различаются, поэтому они располагаются рядом. Вы можете изменить `setTop` и `setLeft`, чтобы построить любой нужный вам макет.

## Шаг 4: Сохранение документа с группированными прямоугольниками

После того как фигуры помещены в группу, просто сохраняем `Document`. Полученный файл покажет два прямоугольника, которые перемещаются вместе при выборе.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Запуск программы создаёт `GroupShape.docx` в рабочем каталоге. Откройте его в Microsoft Word, выберите один прямоугольник, и вы заметите, что вся группа перемещается как единое целое — именно то, что **группировка фигур в Word** должна делать.

![Group shapes in Word example](group-shapes.png){alt="Пример группировки фигур в Word"}

*Рисунок: Два прямоугольных объекта, сгруппированные вместе в документе Word.*

## Полезный совет: повторное использование одной и той же групповой фигуры

Если позже понадобится добавить больше фигур (например, круги, текстовые поля), сохраните ссылку на `groupShape` и продолжайте вызывать `appendChild`. Это избавит от необходимости заново создавать контейнер и гарантирует синхронность всех членов группы.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Особые случаи и часто задаваемые вопросы

- **Что делать, если фигуры перекрываются?** Перекрытие допускается; Word отобразит их в порядке добавления. При необходимости явного порядка используйте `setZOrder`.
- **Можно ли группировать фигуры на разных страницах?** Нет. `GroupShape` ограничена одной страницей, так как её система координат привязана к странице.
- **Наследуют ли группированные фигуры форматирование?** Каждый дочерний элемент сохраняет собственное форматирование (цвет заливки, стиль линии). Чтобы применить единый стиль, пройдитесь по `groupShape.getChildNodes()` и задайте свойства программно.

## Полный исходный код для справки

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Запуск программы создаёт DOCX‑файл, где два прямоугольника **сгруппированы**. Выбор любого прямоугольника перемещает оба, подтверждая, что вы успешно **сгруппировали несколько фигур**.

## Заключение

Теперь вы знаете, как **группировать фигуры в Word** с помощью Java, начиная с **создания пустого документа Word**, затем **создания прямоугольной фигуры**, **задания размеров фигуры** и, наконец, **группировки нескольких фигур** в один перемещаемый объект. Этот шаблон масштабируется на любое количество фигур и может быть комбинирован с текстом, изображениями или диаграммами для создания богатых программных документов.

### Что дальше?

- Исследуйте **группировку нескольких фигур** разных типов (эллипсы, стрелки, текстовые блоки).
- Применяйте цвета заливки или границы, вызывая `shape.getFillColor()` и `shape.getLine().setColor()`.
- Вставляйте сгруппированную фигуру в ячейку таблицы для структурированных отчётов.
- Сочетайте этот подход с рассылкой писем (mail‑merge) для генерации персонализированных контрактов с фирменной графикой.

Не бойтесь экспериментировать, менять размеры или встраивать дополнительный контент. Когда вы освоите группировку, ваши скрипты автоматизации Word станут гораздо гибче и поддерживаемее. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}