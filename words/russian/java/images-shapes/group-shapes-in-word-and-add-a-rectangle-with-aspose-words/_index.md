---
category: general
date: 2026-09-11
description: Группируйте фигуры в Word и добавьте прямоугольную форму с помощью Aspose.Words
  for Java. Узнайте, как задать размер формы, сгруппировать объекты и сохранить документ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: ru
lastmod: 2026-09-11
og_description: Группируйте фигуры в Word и добавьте прямоугольную фигуру с помощью
  Aspose.Words для Java. Этот учебник показывает, как задать размер фигуры, группировать
  фигуры и экспортировать документ.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Группировка фигур в Word – добавление прямоугольника с помощью Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Группировать фигуры в Word и добавить прямоугольник с помощью Aspose.Words
url: /ru/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Группировка фигур в Word и добавление прямоугольника с Aspose.Words

Если вам нужно **группировать фигуры в Word** при программном добавлении прямоугольника, это руководство предоставляет готовое решение, готовое к запуску. Вы увидите, как вставить группу фигур, добавить прямоугольник, задать размер фигуры и, наконец, сохранить документ, чтобы сразу увидеть результат.

Работа с документами Word часто подразумевает расположение нескольких объектов — изображений, диаграмм или простых геометрических фигур — в одну логическую единицу. Группировка этих объектов упрощает их перемещение, вращение или стилизацию совместно. В этом уроке мы также рассмотрим **как добавить прямоугольник** и **задать размер фигуры** для точного контроля макета.

## Что вы узнаете

* Как создать новый документ Word с помощью Aspose.Words for Java.  
* **Как группировать фигуры**, чтобы они вели себя как один объект.  
* **Добавить прямоугольник** в группу и вставить изображение в ту же группу.  
* **Задать размер фигуры** для прямоугольника и изображения.  
* Сохранить документ и открыть его в Microsoft Word для проверки результата.

### Предварительные требования

* Установлен Java 17 или новее.  
* Maven или Gradle для управления зависимостями.  
* Действующая лицензия Aspose.Words for Java (или бесплатный оценочный ключ).  
* Файл изображения (`sample.png`), размещённый в известном каталоге (замените `YOUR_DIRECTORY` на ваш реальный путь).

---

## Как группировать фигуры в Word с помощью Aspose.Words

Первый шаг — создать `Document` и `DocumentBuilder`. Builder предоставляет удобный API для вставки фигур, текста и других элементов.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Почему это важно:** `DocumentBuilder` работает напрямую с объектом `Document`, позволяя вставлять фигуры без ручного управления низкоуровневыми коллекциями узлов.

### Добавление группы фигур

Группа фигур — это контейнер, который может содержать другие фигуры. По сути, это папка для графических объектов.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Метод `insertGroupShape()` создаёт узел `GroupShape` и возвращает его, чтобы вы могли позже добавить дочерние фигуры.  

---

## Добавление прямоугольника в группу

Теперь мы **добавим прямоугольник** в ранее созданную группу. Прямоугольник будет служить фоном или рамкой для изображения.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Совет:** Установка `FillColor` и `StrokeColor` делает прямоугольник видимым в итоговом документе. Если эти свойства опустить, фигура может оказаться прозрачной.

### Как добавить прямоугольник

Приведённый выше код демонстрирует **как добавить прямоугольник**, создавая экземпляр `Shape` с `ShapeType.RECTANGLE` и затем добавляя его в `GroupShape`. Такая же схема работает для любых других типов фигур (например, `ELLIPSE`, `POLYLINE`).

---

## Задание размера фигуры для прямоугольника и изображения

Корректный размер гарантирует правильное выравнивание прямоугольника и изображения. Здесь мы также **задём размер фигуры** для изображения, которое будет вставлено далее.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Теперь и прямоугольник, и изображение имеют одинаковые размеры (100 × 50 points). Поскольку они находятся в одной группе, перемещение или вращение группы будет влиять на обе фигуры одновременно.

> **Зачем совпадающие размеры?** Выравнивание размеров гарантирует, что изображение аккуратно помещается внутри прямоугольника, создавая чистый эффект «рамки».

---

## Сохранение документа и просмотр результата

Наконец, сохраняем документ на диск. Открытие файла в Microsoft Word покажет сгруппированные фигуры как один выбираемый объект.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

При открытии `output.docx` вы увидите прямоугольник с изображением внутри. При щелчке по фигуре выделяются одновременно прямоугольник и изображение, потому что они **сгруппированы**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Текст альтернативы изображения:* *пример группировки фигур в Word* — документ Word, показывающий сгруппированный прямоугольник и изображение.

---

## Часто задаваемые вопросы и обработка граничных случаев

| Вопрос | Ответ |
|----------|--------|
| **Что делать, если нужен другой размер изображения?** | Отрегулируйте `picture.setWidth()` и `picture.setHeight()` после вставки. Прямоугольник может сохранить свой исходный размер, либо вы также можете изменить его, чтобы они совпадали. |
| **Можно ли добавить больше фигур в ту же группу?** | Да. Вызовите `group.appendChild(newShape)` для любых дополнительных объектов `Shape`. |
| **Как повернуть всю группу?** | Используйте `group.setRotationAngle(double angleInRadians)`. Поворот применяется ко всем дочерним фигурам. |
| **Что если файл изображения отсутствует?** | `insertImage` бросает `FileNotFoundException`. Оберните вызов в блок try‑catch и предоставьте запасную фигуру‑заполнитель. |
| **Можно ли позже разгруппировать?** | Вызовите `group.removeAllChildren()`, чтобы отсоединить дочерние элементы, а затем вставьте их обратно в документ по отдельности. |

---

## Заключение

Теперь у вас есть полностью готовый пример, показывающий **как группировать фигуры в Word**, **добавлять прямоугольник**, **задать размер фигуры** и **сохранять** документ с помощью Aspose.Words for Java. Группируя прямоугольник и изображение, вы можете перемещать, менять размер или вращать их как единый объект — что требуется во многих сценариях автоматизации документов.

Дальнейшие шаги:

* Добавление текстовых полей в ту же группу (стиль «как добавить прямоугольник»).  
* Применение различных шаблонов заливки или градиентов (`set shape size` в сочетании со стилизацией).  
* Использование той же техники для группировки диаграмм, таблиц или SmartArt (`how to group shapes` для других типов объектов).  

Экспериментируйте с другими типами фигур, цветами и параметрами макета. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}