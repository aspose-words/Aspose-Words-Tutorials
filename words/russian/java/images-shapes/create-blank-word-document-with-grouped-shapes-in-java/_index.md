---
category: general
date: 2026-08-07
description: Создайте пустой документ Word с группой фигур в Java, используя Aspose.Words.
  Узнайте, как группировать фигуры, задавать их размер и добавлять их в Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: ru
lastmod: 2026-08-07
og_description: Создайте пустой документ Word с группированными фигурами в Java. Следуйте
  этому руководству, чтобы установить размер фигур, добавить их в Word и освоить,
  как группировать фигуры.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Создайте пустой документ Word с группированными фигурами – учебник по Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Создать пустой документ Word с группой фигур в Java
url: /ru/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание пустого документа Word с группой фигур в Java

Если вам нужно **создать пустой документ Word**, содержащий несколько фигур, объединённых в единый объект, этот учебник покажет, как это сделать. Вы увидите полностью готовый, исполняемый пример, демонстрирующий **как группировать объекты shape**, изменять их размеры и **добавлять фигуры в Word** с помощью Aspose.Words for Java.

Руководство проходит каждый шаг — от настройки проекта до сохранения окончательного файла .docx — чтобы вы могли скопировать код прямо в своё приложение. Внешних ссылок не требуется, решение работает с Aspose.Words 23.9 и новее.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* Java 17 (или любой поддерживаемый JDK)
* Maven или Gradle для управления зависимостями
* Лицензия Aspose.Words for Java (или временный ключ оценки)
* Пример файла изображения (например, `sample.jpg`) в известном каталоге

Если чего‑то не хватает, установите это сначала; остальные части учебника предполагают готовую среду.

## Шаг 1: Добавьте Aspose.Words в проект

Добавьте зависимость Aspose.Words в ваш `pom.xml` (Maven) или `build.gradle` (Gradle). Эта библиотека предоставляет классы `Document`, `DocumentBuilder`, `GroupShape` и `Shape`, которые будут использоваться далее.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Почему это важно:** Без библиотеки ни один из API для обработки Word недоступен, и вы не сможете **создать пустой документ Word** программно.

## Шаг 2: Создайте пустой документ Word

Первое конкретное действие — создать объект `Document`, представляющий **пустой документ Word** в памяти.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* создаёт **пустой документ Word** с настройками по умолчанию (страница A4, стандартные поля). Связанный `DocumentBuilder` позволяет вставлять содержимое в текущую позицию курсора.

## Шаг 3: Вставьте групповую фигуру (как группировать shape)

*Group shape* выступает контейнером для других фигур. На этом этапе вы узнаете **как группировать shape**‑объекты, чтобы они перемещались вместе.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Метод `insertGroupShape` размещает контейнер в позиции курсора билдера. Группировка необходима, когда нужно рассматривать несколько рисунков как один объект — это суть функциональности **group shapes word**.

## Шаг 4: Создайте прямоугольник и задайте его размер

Теперь добавим прямоугольник в группу. Это демонстрирует **set shape size**, что необходимо для точного расположения.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Зачем задавать размеры?* Явный вызов `setWidth` и `setHeight` гарантирует, что прямоугольник будет выглядеть точно так, как задумано, независимо от стилей фигур по умолчанию в документе.

## Шаг 5: Вставьте изображение и добавьте его в группу

Добавление картинки показывает ещё один типичный сценарий для **add shapes to word**. Изображение становится частью той же группы и перемещается вместе с прямоугольником.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Если файл изображения отсутствует, Aspose.Words бросит исключение. Практический совет — проверьте путь заранее:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Шаг 6: Сохраните документ с группой фигур

Наконец, сохраните **пустой документ Word** (теперь уже заполненный группой фигур) на диск.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Когда откроете `GroupShapeDemo.docx` в Microsoft Word, вы увидите один сгруппированный объект, содержащий прямоугольник и изображение. Выбор любой части группы перемещает весь контейнер, подтверждая, что фигуры действительно **группированы**.

### Ожидаемый результат

* Файл `GroupShapeDemo.docx` в указанном каталоге.
* При открытии файла отображается контейнер 300 × 200 пунктов с:
  * Прямоугольником 100 × 50 пунктов, расположенным в (20, 20).
  * Изображением, расположенным в (150, 30) внутри того же контейнера.

## Особые случаи и варианты

| Ситуация | Как решить |
|-----------|-----------------|
| **Другой размер страницы** | Вызовите `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` перед вставкой группы. |
| **Несколько групп** | Повторите шаги 3‑5 с новым экземпляром `GroupShape`; каждую группу можно позиционировать независимо. |
| **Поворот фигур** | Используйте `shape.setRotationAngle(45.0);` для поворота прямоугольника или картинки перед добавлением в группу. |
| **Фигуры, не являющиеся изображениями** | Создавайте объекты `Shape` типа `ShapeType.ELLIPSE`, `ShapeType.LINE` и т.д., и добавляйте их так же, как прямоугольник. |
| **Большие изображения** | Масштабируйте картинку с помощью `picture.setWidth(80.0); picture.setHeight(60.0);`, чтобы группа оставалась в своих исходных границах. |

Эти варианты позволяют адаптировать базовый шаблон под широкий спектр сценариев генерации документов.

## Практические советы из опыта

* **Pro tip:** Установите для группы `RelativeHorizontalPosition` и `RelativeVerticalPosition` значения `RelativeHorizontalPosition.PAGE` и `RelativeVerticalPosition.PAGE`, если хотите, чтобы группа была привязана к странице, а не к курсору.
* **Обратите внимание:** Добавление фигуры, превышающей размеры группы, приведёт к её обрезке в Word. Соответственно скорректируйте размер группы через `group.setWidth()` и `group.setHeight()`.
* **Замечание о производительности:** При массовой генерации документов в цикле переиспользуйте один экземпляр `DocumentBuilder` и вызывайте `doc.clone()`, чтобы снизить накладные расходы на создание объектов.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, содержащий сгруппированную коллекцию фигур, используя Aspose.Words for Java. В учебнике показан полный рабочий процесс: подключение библиотеки, создание документа, вставка группы, **set shape size**, **add shapes to word** и сохранение результата.

Далее вы можете изучать более продвинутые возможности, такие как группировка диаграмм, применение стилей к отдельным фигурам или экспорт документа в PDF. Все эти темы опираются на те же принципы, продемонстрированные в данном руководстве.

---


## Что изучать дальше?


Следующие учебники охватывают смежные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}