---
category: general
date: 2026-08-20
description: Узнайте, как группировать фигуры, задавать размер фигуры, вставлять изображение
  в документ, добавлять картинку в группу и создавать прямоугольную фигуру с помощью
  Aspose.Words в Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: ru
lastmod: 2026-08-20
og_description: Как группировать фигуры в документе Word с помощью Aspose.Words. Следуйте
  этому пошаговому руководству на Java, чтобы задать размер фигуры, вставить изображение
  в документ, добавить картинку в группу и создать прямоугольную фигуру.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Как сгруппировать фигуры в документе Word с помощью Aspose.Words – руководство
  по Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Как сгруппировать фигуры в документе Word с помощью Aspose.Words
url: /ru/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сгруппировать фигуры в документе Word с помощью Aspose.Words

Если вам нужно **как сгруппировать фигуры** в файле Word, этот учебник покажет полное решение на Java. Вы увидите, как **установить размер фигуры**, **вставить изображение в документ**, **добавить картинку в группу** и **создать прямоугольную фигуру** — всё с понятными объяснениями и готовым примером кода.

Группировка фигур упрощает управление макетом, позволяет перемещать или вращать несколько объектов как единое целое и поддерживает порядок в документе. В следующих шагах вы создадите группу, содержащую прямоугольник и изображение, а затем разместите эту группу на странице.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* Java 17 или новее.
* Aspose.Words for Java (версия 23.9 или новее), добавленная в classpath вашего проекта.
* Пример JPEG‑изображения по пути `YOUR_DIRECTORY/sample.jpg` (замените `YOUR_DIRECTORY` на реальный путь).

Aspose.Words можно добавить через Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Как сгруппировать фигуры с помощью Aspose.Words

В следующих разделах подробно рассматриваются все операции, необходимые для **как сгруппировать фигуры**. Основной заголовок H2 содержит основной ключевой запрос, что удовлетворяет правилам SEO.

### Шаг 1: Создать новый документ и `DocumentBuilder`

`Document` представляет файл Word, а `DocumentBuilder` предоставляет удобные методы для вставки контента.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно*: Создание нового `Document` гарантирует, что создаваемая группа не будет конфликтовать с уже существующими элементами.

### Шаг 2: Вставить групповую фигуру, которая будет содержать несколько дочерних фигур

Групповая фигура работает как контейнер. Ее размеры определяют ограничивающий прямоугольник для всех дочерних фигур.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Подсказка*: Ширина (`300`) и высота (`200`) указаны в пунктах (1 pt = 1/72 дюйма). Подгоните их под размер фигур, которые планируете добавить.

### Шаг 3: Создать прямоугольную фигуру, задать её размер и добавить в группу

Точное задание размеров фигуры необходимо, когда требуется точный контроль над макетом.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Почему мы задаём размер фигуры*: Методы `setWidth` и `setHeight` соответствуют вторичному ключевому запросу **set shape size**, предоставляя пиксельно‑точный контроль над внешним видом прямоугольника.

### Шаг 4: Вставить изображение, затем добавить фигуру‑картинку в ту же группу

Вставка изображения — основной элемент требования **insert image into document**. Возвращаемый `Shape` является фигурой‑картинкой, которую можно группировать как любую другую фигуру.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Профессиональный совет*: Если нужно сохранить исходное соотношение сторон, задайте только одну измерение (`setWidth` или `setHeight`). Aspose.Words автоматически масштабирует другое измерение.

### Шаг 5: Позиционировать всю группу на странице

После добавления всех дочерних фигур вы можете перемещать, вращать или скрывать всю группу. Позиционирование использует концепцию **add picture to group** косвенно, поскольку группа теперь содержит картинку.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Объяснение*: `setLeft` и `setTop` размещают группу относительно полей страницы. Вращение группы демонстрирует, что все дочерние фигуры наследуют трансформацию.

### Шаг 6: Сохранить документ

Наконец, запишите файл на диск. Откройте полученный `.docx` в Word, чтобы убедиться в правильности группировки.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Запуск программы создаёт **GroupShapesDemo.docx**, содержащий прямоугольник и изображение, объединённые вместе. Выбор любой из фигур в Word также выделит другую, подтверждая, что вы успешно освоили **how to group shapes**.

---

## Ожидаемый результат

При открытии *GroupShapesDemo.docx* в Microsoft Word:

* Слева от группы появляется прямоугольник (золотая заливка).
* Справа от прямоугольника отображается предоставленная вами картинка.
* Оба объекта перемещаются вместе при перетаскивании группы.
* Группа расположена на расстоянии 50 pt от левого поля и 100 pt от верхнего поля, повернута на 15°.

Если изображение не отображается, проверьте путь к файлу в `insertImage`. Aspose.Words бросает `IOException`, когда файл не найден.

---

## Часто задаваемые вопросы и обработка граничных случаев

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes?** | Yes. Call `groupShape.appendChild(otherShape)` for each additional shape. |
| **What if I need a transparent background for the rectangle?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Is grouping supported in older Word formats (e.g., `.doc`)?** | Grouping works for `.docx` and `.doc` but some older viewers may ignore the group metadata. Save as `.docx` for full fidelity. |
| **How do I ungroup later?** | Retrieve the child nodes via `groupShape.getChildNodes(NodeType.ANY, true)` and move them to the document body, then remove the group. |
| **Can I group shapes across different sections?** | No. A `GroupShape` must reside within a single `Story` (usually the main document body). |

---

## Профессиональные советы для надёжной работы с фигурами

* **Используйте абсолютное позиционирование умеренно** — относительное позиционирование (`builder.moveToDocumentEnd()`) часто даёт более адаптивные макеты.
* **Кешируйте `DocumentBuilder`** — создание нового builder‑а для каждой операции может ухудшить производительность при работе с большими документами.
* **Устанавливайте `PictureFillMode`**, когда нужно растянуть или замостить изображение внутри фигуры: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Проверяйте размеры изображения** перед вставкой, чтобы избежать неожиданного масштабирования, которое может изменить ограничивающий прямоугольник группы.

---

## Следующие шаги

Теперь, когда вы знаете **how to group shapes**, вы можете изучить:

* **Insert image into document** с расширенными опциями, такими как обрезка (`pictureShape.setCropTop(...)`).
* **Set shape size** динамически в зависимости от размеров страницы (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** вместе с текстовыми полями для подписанных графиков.
* **Create rectangle shape** с закруглёнными углами (`rectangleShape.setCornerRadius(5);`).

Эти темы опираются на тот же набор API и помогут создавать сложные программные отчёты Word.

---

## Заключение

В этом учебнике вы узнали **how to group shapes** в документе Word с помощью Aspose.Words for Java. Следуя шести шагам — созданию документа, вставке группы, **creating rectangle shape**, **set shape size**, **insert image into document**, **add picture to group** и позиционированию группы — вы получили переиспользуемый шаблон для сложных сценариев макета. Экспериментируйте с дополнительными дочерними фигурами, различными углами вращения или условной логикой группировки, чтобы адаптировать решение под нужды вашего приложения.

Happy coding!


## Что вам стоит изучить дальше?


Ниже представлены учебники, охватывающие тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}