---
category: general
date: 2026-07-16
description: как вставить групповую форму в Java с использованием Aspose.Words – добавить
  прямоугольную форму, задать размеры формы и создать цветной прямоугольник и круг.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: ru
lastmod: 2026-07-16
og_description: 'как вставить групповую форму в Java: практическое руководство по
  добавлению прямоугольной формы, установке размеров формы и созданию цветного прямоугольника
  и круга с помощью Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Вставка групповой фигуры в Java – Полный учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Как вставить групповую форму в Java — Полное руководство
url: /ru/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить групповую форму в Java – Полное руководство

Когда‑нибудь задумывались **как вставить групповую форму** в документ Word с помощью Java? Вы не одиноки. Будь то генератор отчётов или динамический создатель листовок, группировка форм упрощает макет и делает код более управляемым.

В этом руководстве мы пройдём точные шаги по **добавлению прямоугольной формы**, **установке размеров формы**, а также **созданию цветного прямоугольника** и **созданию цветного круга** с использованием библиотеки Aspose.Words. К концу у вас будет готовая программа, генерирующая .docx‑файл с синим прямоугольником и красным кругом, аккуратно упакованными в группу.

## Prerequisites

Прежде чем начать, убедитесь, что у вас есть:

- Java 17 (или любой современный JDK), установленный и настроенный.
- Maven или Gradle для управления зависимостями.
- Aspose.Words for Java 23.9 или новее — можно получить из Maven Central.
- Базовое понимание синтаксиса Java — ничего сложного не требуется.

Если чего‑то не хватает, скачайте JDK с сайта Oracle и добавьте зависимость Aspose.Words в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Теперь, когда подготовка завершена, давайте приступим к делу.

## как вставить групповую форму – Обзор

Основная идея проста: создать `Document`, открыть `DocumentBuilder`, вставить **групповую форму**, затем добавить отдельные формы (прямоугольник и круг) в эту группу. Группа выступает как контейнер, поэтому её перемещение позже сдвинет всё, что внутри — идеально для сложных макетов.

Ниже приведён полный готовый к запуску код. Смело скопируйте и вставьте его в новый Java‑класс с именем `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Совет профессионала:** значения `setLeft` и `setTop` относятся к началу группы, а не к странице. Это упрощает последующее перемещение всей группы.

### Что только что произошло?

1. **Document & Builder** — Мы создаём пустой Word‑файл и `DocumentBuilder`, позволяющий вставлять содержимое.
2. **Group Shape** — `builder.insertGroupShape()` создаёт контейнер. Представьте его как папку для графических объектов.
3. **Blue Rectangle** — Мы создаём объект `Shape` типа `RECTANGLE`, задаём его размер, позицию и заполняем синим цветом — это шаг **create colored rectangle**.
4. **Red Circle** — Аналогично, но используем `ELLIPSE` для идеального круга и заполняем его красным — это шаг **create colored circle**.
5. **Saving** — Наконец сохраняем всё в `GroupShapeDemo.docx`.

Запустите программу (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) и откройте полученный файл. Вы увидите синий прямоугольник слева и красный круг справа, оба зафиксированы внутри единой групповой рамки.

## Добавление прямоугольной формы

Если нужен только прямоугольник без группировки, можно пропустить вызов `insertGroupShape()` и добавить прямоугольник напрямую в тело документа. Тем не менее, группировка даёт гибкость перемещать, вращать или удалять несколько форм одновременно.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Обратите внимание, как мы использовали логику **add rectangle shape** здесь. Прямоугольник появляется на странице как отдельный объект. В большинстве реальных сценариев вам всё же понадобится группа, потому что она сохраняет относительное позиционирование.

## Установка размеров формы

Когда вы видите методы вроде `setWidth` и `setHeight`, помните, что они принимают **points** (1/72 дюйма). Если предпочтительнее миллиметры, сначала выполните преобразование:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Этот фрагмент демонстрирует **set shape dimensions** с преобразованием единиц — удобно, когда спецификации дизайна получены из UI‑макета, использующего метрические единицы.

## Создание цветного прямоугольника

Окрашивание формы так же просто, как вызов `getFill().setForeColor()`. Вы можете передать любой `java.awt.Color`. Хотите градиент? Используйте `setForeColor` для начального цвета и `setBackColor` для конечного.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Это быстрый способ **create colored rectangle** с градиентной заливкой вместо сплошного цвета.

## Создание цветного круга

Круги — это просто эллипсы с одинаковой шириной и высотой. Та же логика окрашивания применяется:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Если нужен прозрачный заливка, задайте альфа‑канал:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Теперь вы освоили технику **create colored circle**.

## Сохранение документа

Aspose.Words позволяет сохранять в множество форматов: DOCX, PDF, HTML, PNG и т.д. Для этой демонстрации мы используем DOCX, поскольку он сохраняет векторные формы без потерь.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Изменив `SaveFormat`, вы можете создать PDF‑версию того же группового рисунка.

## Распространённые ошибки и как их избежать

- **Забыли добавить форму в группу?** Форма появится на странице, но не будет перемещаться вместе с группой. Всегда вызывайте `group.appendChild(yourShape)`.

## Что изучать дальше?

Следующие руководства охватывают близко связанные темы, опирающиеся на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать документ Word на Java – добавить прямоугольную форму с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Как создавать поля формы и добавлять содержимое с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Создать прямоугольную форму в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}