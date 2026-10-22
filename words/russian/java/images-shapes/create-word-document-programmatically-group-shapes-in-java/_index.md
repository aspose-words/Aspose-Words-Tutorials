---
category: general
date: 2026-09-21
description: Создавайте документ Word программно с помощью Java. Узнайте, как группировать
  фигуры в Word, вставлять прямоугольник, задавать размер фигуры и добавлять фигуры
  в документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: ru
lastmod: 2026-09-21
og_description: 'Создайте документ Word программно с помощью Java: в этом руководстве
  показано, как группировать фигуры в Word, вставлять прямоугольные фигуры, задавать
  их размер и добавлять их в документ Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Создать документ Word программно, группировать фигуры в Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Создать документ Word программно, группировать фигуры в Java
url: /ru/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Программное создание Word‑документа, группировка фигур в Java

Если вам нужно **программно создавать Word‑документ**, это руководство проведёт вас через полное решение. Вы увидите, как **группировать фигуры в Word**, вставить прямоугольник, задать его размер и добавить другие фигуры — всё с использованием Java и библиотеки Aspose.Words for Java.

В руководстве рассматривается каждый шаг от настройки проекта до сохранения окончательного файла .docx. По завершении вы сможете генерировать Word‑документ, содержащий прямоугольник и изображение, объединённые в одну группу, что упрощает их совместное перемещение и изменение размеров. Предыдущий опыт работы с API Aspose.Words не требуется, однако у вас должна быть базовая среда разработки Java.

## Prerequisites

* Java Development Kit (JDK) 8 или новее  
* Maven или Gradle для управления зависимостями  
* Aspose.Words for Java 23.9 (или последняя версия) — библиотека бесплатна для оценки  
* Файл изображения (например, `sample.jpg`) в известном каталоге  

Наличие этих элементов гарантирует, что код будет работать без дополнительной настройки.

## Step 1: Set up the project and import Aspose.Words

Создайте Maven‑проект (или добавьте зависимость в ваш существующий `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Если вы предпочитаете Gradle, добавьте следующее в `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

После того как зависимость будет разрешена, импортируйте необходимые классы в ваш Java‑файл:

```java
import com.aspose.words.*;
import java.io.File;
```

## Step 2: Create the Word document programmatically

Первая операция в любой автоматизации — создание объекта `Document` и `DocumentBuilder`. Builder упрощает вставку текста, изображений и фигур.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

На данном этапе документ существует только в памяти. Теперь можно начинать добавлять фигуры.

## Step 3: Insert a rectangle shape – how to insert rectangle shape

Прямоугольник — это базовый `Shape` с типом `ShapeType.RECTANGLE`. Его размеры задаются через `setWidth`, `setHeight`, а позиция — через `setTop` и `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Почему это важно:** Явное указание размера и позиции (`set shape size word`) гарантирует, что прямоугольник появится точно там, где вы ожидаете, независимо от стандартного расположения элементов в документе.

## Step 4: Insert an image – add shapes to word document

`DocumentBuilder` может вставлять изображение напрямую из пути к файлу. После вставки вы можете переместить картинку так же, как любую другую фигуру.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Теперь прямоугольник и изображение являются независимыми фигурами внутри документа.

## Step 5: Group the shapes – how to group shapes in word

Группировка фигур полезна, когда нужно перемещать или изменять их размер как единого объекта. Aspose.Words предоставляет контейнер `GroupShape` для этой цели.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

При сохранении группы Word рассматривает оба дочерних объекта как один логический элемент. Позже вы сможете выбрать группу и перетащить её, и оба — прямоугольник и изображение — будут перемещаться вместе.

## Step 6: Save the document

Наконец, запишите документ на диск. Путь должен быть доступен для записи процессом Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Запуск метода `main` создаст файл с именем **GroupShapeExample.docx**. Откройте его в Microsoft Word, чтобы увидеть прямоугольник и изображение, объединённые в одну группу. Выбор группы позволяет перемещать оба объекта одновременно, подтверждая успешность группировки.

## Expected output

* Word‑файл (`GroupShapeExample.docx`) в указанном вами каталоге.  
* Внутри файла прямоугольник (заполненный светло‑серым) находится в левом верхнем углу, а изображение расположено непосредственно под ним.  
* Оба объекта входят в одну группу, поэтому при перетаскивании одного перемещается и другой.

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| **Different image formats** | Aspose.Words поддерживает PNG, BMP, GIF и TIFF. Используйте соответствующее расширение файла в `insertImage`. |
| **Negative dimensions** | API бросает `ArgumentException`. Всегда проверяйте ширину и высоту перед вызовом `setWidth` / `setHeight`. |
| **Large documents** | Группировка большого количества фигур может увеличить размер файла. При необходимости высокой производительности рассмотрите объединение фигур в одно изображение. |
| **Word version compatibility** | GroupShape работает с Word 2007 (`.docx`) и новее. Для более старых файлов `.doc` группа будет «развёрнута». |
| **Dynamic positioning** | Используйте вычисления, основанные на размере страницы (`doc.getFirstSection().getPageSetup().getPageWidth()`), если требуется адаптивное размещение. |

**Pro tip:** После создания группы вы можете изменить

## What Should You Learn Next?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}