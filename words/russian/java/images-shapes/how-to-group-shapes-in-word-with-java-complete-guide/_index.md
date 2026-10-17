---
category: general
date: 2026-10-16
description: Узнайте, как группировать фигуры в Word с помощью Java. В этом руководстве
  показано, как добавить прямоугольную форму, задать её размер и параметры, а также
  сохранить документ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: ru
lastmod: 2026-10-16
og_description: Группировать фигуры в Word с помощью Java. Добавлять прямоугольную
  фигуру, задавать её размер и параметры, а также программно создавать профессиональные
  документы.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Группировка фигур в Word с помощью Java — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Как группировать фигуры в Word с помощью Java – полное руководство
url: /ru/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word с помощью Java – полное руководство

Если вам нужно **группировать фигуры в Word** программно, этот учебник предоставляет готовое решение. Вы увидите, как **добавить прямоугольную фигуру**, отрегулировать её размер, задать размеры фигуры и, наконец, сохранить файл DOCX, содержащий сгруппированный прямоугольник и эллипс.

Группировка фигур в Word полезна для создания сложных диаграмм, создания переиспользуемых графических компонентов или просто для удержания связанных объектов вместе, когда документ редактируется позже. Код использует библиотеку Aspose.Words for Java, которая работает с любой современной JDK и не требует установки Microsoft Word.

## Prerequisites

Before you start, make sure you have:

| Requirement | Reason |
|-------------|--------|
| Java 17 (or later) | Библиотека ориентирована на современные среды выполнения Java. |
| Aspose.Words for Java (latest version) | Предоставляет классы `Document`, `DocumentBuilder`, `GroupShape` и `Shape`, используемые в примере. |
| An IDE or build tool (Maven/Gradle) | Для компиляции и запуска примера. |
| Basic knowledge of Java syntax | Необходимо для понимания потока кода. |

Add the Aspose.Words dependency to your project. For Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Or for Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Overview of the solution

The tutorial follows a clear **problem → solution → explanation** pattern:

1. **Create a new Word document** and obtain a `DocumentBuilder`.  
2. **Insert a `GroupShape` container** that will hold multiple shapes.  
3. **Add a rectangle**, set its width/height (the **set shape size** step), and attach it to the group.  
4. **Add an ellipse**, position it inside the same group, and also set its dimensions.  
5. **Save** the document to disk.

Each step includes the **why** behind the code, so you understand what the API does and how you can adapt it to other scenarios.

## Step 1: Create the document and a DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` представляет весь файл DOCX, тогда как `DocumentBuilder` — это вспомогательный объект, позволяющий вставлять содержимое без работы с низкоуровневым управлением узлами. Создание их вначале даёт чистый холст для всех последующих операций с фигурами.

## Step 2: Insert a GroupShape container

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

A `GroupShape` works like a **folder** for drawing objects. When you move, rotate, or delete the group, all child shapes follow automatically. This is the core of **group shapes in word**.

## Step 3: Add a rectangle shape – the rectangle shape code

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Конструктор `Shape` получает `ShapeType.RECTANGLE`, что указывает Aspose.Words отрисовать прямоугольный контур.  
- **set shape size** – `setWidth` и `setHeight` задают **shape dimensions** в пунктах (1 pt = 1/72 in). Это самый распространённый способ управления визуальным размером.  
- **Why we use `appendChild`** – Он присоединяет прямоугольник к `GroupShape`, чтобы он перемещался вместе с группой.

## Step 4: Add an ellipse and position it inside the group

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

The ellipse demonstrates **set shape dimensions** beyond a simple rectangle. By calling `setLeft`, we control the horizontal offset inside the group, which is useful when arranging multiple objects.

## Step 5: Save the document

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

When you open *GroupShapeDemo.docx* in Microsoft Word, you’ll see a rectangle and an ellipse locked together inside a single group. Selecting either shape will select the entire group—exactly what you expect when **group shapes in word**.

## Full, runnable example

Putting all pieces together, here is the complete source file you can copy into your IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Expected output

- A file named **GroupShapeDemo.docx** appears in the project folder.  
- Opening the file in Word shows two shapes (a rectangle and an ellipse) that are grouped together.  
- Dragging either shape moves the whole group, confirming that **group shapes in word** works as intended.

## Common variations and edge cases

| Scenario | What to change | Why |
|----------|----------------|-----|
| **Different shape types** (e.g., triangle) | Use `ShapeType.TRIANGLE` or any other enum value when constructing `Shape`. | Allows you to build more complex diagrams. |
| **Setting fill color** | Call `shape.getFillColor().setColor(Color.BLUE);` after creating the shape. | Improves visual appearance without affecting grouping. |
| **Rotating the group** | `groupShape.setRotationAngle(45);` | Rotates all child shapes together, useful for icons. |
| **Adding text inside a shape** | `shape.appendChild(new Paragraph(document));` then add a `Run` with text. | Makes the shape act like a label or callout. |
| **Saving to a stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Useful for web services that return the document directly. |

### Pro tip

When you need to **set shape dimensions** based on dynamic data (e.g., a barcode length), calculate the width/height in points first:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

This avoids hard‑coding values and keeps your code adaptable.

## Conclusion

You now know how to **group shapes in Word** using Java, how to **add rectangle shape**, and how to **set shape size** and **set shape dimensions** with concise, production‑ready code. By following the steps above, you can create reusable graphic groups, embed them in automated reports, or build custom diagramming tools without ever opening Word manually.

### What’s next?

- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE` with `setCornerRadius`).  
- Combine **group shapes in word** with tables or charts for richer documents.  
- Look into the Aspose.Words API for **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) to control how surrounding text interacts with your grouped graphics.

Feel free to experiment, adapt the **rectangle shape code**, and share your results


## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Создать документ Word на Java – добавить прямоугольную фигуру с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Создать прямоугольную фигуру в Word с помощью Java – полное руководство](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Создать групповую фигуру в документе Word, используя Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}