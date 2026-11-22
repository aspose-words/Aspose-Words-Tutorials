---
category: general
date: 2026-11-22
description: Добавьте прямоугольную форму в документ Word с помощью Java, задайте
  её размер, сгруппируйте несколько форм и эффективно добавляйте форму в группу.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: ru
lastmod: 2026-11-22
og_description: Добавьте прямоугольную форму в документ Word с помощью Java, затем
  задайте размер формы, сгруппируйте несколько форм и добавьте форму в группу в едином
  рабочем процессе.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Добавление прямоугольной формы и группировка форм в Java — полное руководство
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Добавить прямоугольную фигуру и группировать фигуры в Java
url: /ru/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавление прямоугольной фигуры и группировка фигур в Java

Если вам нужно **добавить прямоугольную фигуру** в документ Word с помощью Java, это руководство проведёт вас через все необходимые шаги. Вы также узнаете, как **задать размер фигуры**, **группировать несколько фигур** и **добавлять фигуру в группу**, не покидая IDE.

Работа с векторной графикой внутри файла DOCX часто напоминает жонглирование разными API. К концу этого урока у вас будет единая, автономная программа, которая создаёт прямоугольник, эллипс и любые дополнительные фигуры, а затем группирует их, чтобы они перемещались как один объект. Ни какие внешние инструменты не требуются, кроме Aspose.Words for Java.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* Java 17 или новее.
* Maven 3.8+ (или Gradle) для управления зависимостями.
* Действующая лицензия Aspose.Words for Java (оценочная версия подходит для тестирования).
* IDE, например IntelliJ IDEA или VS Code, хотя любой текстовый редактор тоже подойдёт.

Эти требования позволяют коду компилироваться и работать в любой современной среде разработки.

## Шаг 1: Настройка Maven‑проекта

Создайте новый Maven‑проект или добавьте зависимость Aspose.Words в существующий `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Зависимость подтягивает все классы, необходимые для работы с документами, включая `Document`, `DocumentBuilder`, `Shape` и `GroupShape`. Maven автоматически скачает JAR‑файлы при запуске `mvn compile`.

## Шаг 2: Загрузка документа и создание DocumentBuilder

`DocumentBuilder` предоставляет удобный API для вставки содержимого. Загрузите существующий DOCX или начните с пустого документа:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Создание билдера заранее даёт вам курсор, расположенный в начале документа, готовый к вставке фигур.

## Добавление прямоугольной фигуры в документ Word

### Шаг 3: Вставка прямоугольной фигуры

Прямоугольник — первый визуальный элемент, который мы хотим разместить в документе. Используя конструктор `Shape` с `ShapeType.RECTANGLE`, вы получаете полностью редактируемый объект.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Добавление прямоугольника на этом этапе не влияет на макет, пока не будет задан его размер и он не будет добавлен в контейнер.

### Задание размера и габаритов фигуры

#### Шаг 4: Определение ширины и высоты

Установка габаритов фигуры определяет, как она будет выглядеть на странице. Значения ширины и высоты измеряются в пунктах (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Вы можете изменить эти числа в соответствии с требованиями вашего дизайна. Те же методы применимы к любой экземпляру `Shape`, поэтому их можно использовать для кругов, стрелок или пользовательских рисунков.

#### Шаг 5: Вставка прямоугольника в документ

Теперь, когда у прямоугольника есть размер, разместите его на странице. Метод `insertShape` класса `DocumentBuilder` добавляет фигуру в текущую позицию курсора.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

На этом этапе прямоугольник отображается один на странице. Следующие шаги покажут, как объединить его с другими фигурами.

## Группировка нескольких фигур вместе

Группировка фигур позволяет перемещать, вращать или изменять их размер как единого объекта. Это особенно полезно при создании сложных схем.

### Шаг 6: Создание контейнера группы фигур

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Вызов `insertGroupShape` добавляет пустой контейнер в документ. Любые фигуры, добавленные в этот контейнер, становятся частью группы.

### Добавление фигуры в группу

#### Шаг 7: Добавление прямоугольника в группу

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Добавление перемещает прямоугольник из тела документа во внутреннюю коллекцию группы. Теперь прямоугольник подчиняется трансформациям группы.

#### Шаг 8: Добавление эллипса для демонстрации

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Эллипс использует ту же систему координат, что и прямоугольник, поэтому при необходимости вы можете визуально выровнять их, изменяя свойства `setLeft` и `setTop`.

### Шаг 9: Сохранение документа

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Запуск программы создаёт `output.docx`. Откройте файл в Microsoft Word или LibreOffice — вы увидите прямоугольник и эллипс, сгруппированные вместе. Выбор любой из фигур выделит всю группу, подтверждая, что **добавление фигуры в группу** прошло успешно.

![Add rectangle shape example in Java](image.png){alt="Пример добавления прямоугольной фигуры в Java"}

*На скриншоте показаны прямоугольник и эллипс внутри одной группы, готовые к совместному манипулированию.*

## Почему этот подход важен

* **Единый источник правды** — Все свойства фигур задаются до создания группы, что предотвращает сбои в макете.
* **Повторное использование** — Одни и те же методы `setWidth`/`setHeight` работают для любой фигуры, поэтому пример можно расширить стрелками, звёздами или пользовательскими SVG.
* **Производительность** — Группировка уменьшает количество объектов рисования, которые должен обрабатывать рендерер Word, ускоряя открытие больших документов.
* **Поддерживаемость** — Хранение логики создания фигур и их группировки вместе упрощает будущим разработчикам изменение размеров или добавление новых фигур без поиска по разрозненному коду.

## Общие варианты и граничные случаи

| Сценарий | Корректировка |
|----------|---------------|
| **Разные единицы измерения** | Используйте конвертацию `PointsToPixels` или задайте `Shape.setWrapType(WrapType.INLINE)` для встроенного размещения. |
| **Вращение группы** | Вызовите `groupShape.setRotation(45);`, чтобы повернуть все дочерние фигуры на 45°. |
| **Добавление текста в фигуру** | Вызовите `Shape.setText("Label");` после задания размеров. |
| **Динамический размер** | Получите размеры страницы через `doc.getFirstSection().getPageSetup().getPageWidth()` и рассчитывайте размеры фигур пропорционально. |

Эти варианты показывают, как основной шаблон — **добавить прямоугольную фигуру**, **задать размер фигуры**, **группировать несколько фигур**, **добавить фигуру в группу** — адаптируется к множеству реальных требований.

## Заключение

Теперь вы знаете, как **добавить прямоугольную фигуру** в документ Word с помощью Java, **задать размер фигуры**, **группировать несколько фигур** и **добавлять фигуру в группу** чистым и поддерживаемым способом. Полный пример компилируется в один исполняемый класс, а полученный DOCX‑файл демонстрирует ожидаемый результат.

Дальнейшие шаги:

* Добавление текстовых меток или гиперссылок к каждой фигуре.
* Вложение групп для построения иерархических схем.
* Экспорт документа в PDF с сохранением групп фигур.

Экспериментируйте с различными размерами, цветами и дополнительными типами фигур. Овладение манипуляцией фигур позволяет автоматизировать генерацию отчётов, создавать динамические схемы и обогащать документы — всё напрямую из кода Java.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающие вам освоить дополнительные возможности API и исследовать альтернативные подходы в своих проектах.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}