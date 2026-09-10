---
category: general
date: 2026-02-10
description: Создайте прямоугольную форму в документе Word с помощью Aspose.Words
  for Java. Узнайте, как задать цвет тени, как добавить тень и как программно создать
  документ Word.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: ru
og_description: Создайте прямоугольную форму в документе Word с помощью Aspose.Words
  для Java. Следуйте этому пошаговому руководству, чтобы задать цвет тени, добавить
  тень и создать документ Word.
og_title: Создание прямоугольной фигуры в Word с помощью Java – Полное руководство
tags:
- Aspose.Words
- Java
- Document Automation
title: Создание прямоугольной формы в Word с помощью Java – Полное руководство
url: /ru/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Word с помощью Java – Полное руководство

Когда‑то вам нужно было **создать прямоугольную фигуру** в документе Word, но вы не знали, с чего начать? Вы не одиноки — многие разработчики сталкиваются с этой проблемой, пытаясь программно рисовать графику в Word. Хорошая новость: с Aspose.Words for Java вы можете добавить прямоугольник на страницу, придать ему красивую тень и сохранить файл за считанные секунды. В этом руководстве мы подробно разберём, **как добавить тень**, **установить цвет тени** и **создать документ Word** с нуля.  

Мы охватим всё необходимое: требуемые библиотеки, каждую строку кода, почему важны определённые настройки и несколько приёмов, которые не всегда указаны в официальной документации. К концу вы получите готовый к запуску пример, создающий прямоугольную фигуру с мягкой серой тенью, сохранённый как *Shadow.docx*.

## Предварительные требования – Что нужно перед началом

Прежде чем погрузиться в код, убедитесь, что у вас есть следующее:

| Требование | Причина |
|------------|---------|
| Java Development Kit (JDK) 8 или новее | Aspose.Words работает на любой современной JDK. |
| Maven или Gradle (опционально) | Упрощает добавление зависимости Aspose.Words. |
| Лицензия Aspose.Words for Java (или бесплатная пробная версия) | Библиотека коммерческая; пробная версия подходит для тестов. |
| IDE (IntelliJ IDEA, Eclipse, VS Code и т.д.) | Позволяет быстро запустить и отладить пример. |

Если у вас уже есть Java‑проект, просто добавьте Maven‑координату:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Никакой сложной настройки больше не требуется — достаточно обычного метода `public static void main`.

![пример создания прямоугольной фигуры](https://example.com/rectangle-shadow.png "создание прямоугольной фигуры с тенью в Word")

*Текст альтернативы изображения: пример создания прямоугольной фигуры, показывающий циан‑прямоугольник с серой тенью.*

## Шаг 1 – Создание нового документа Word

Первое, что нам нужно сделать, — создать пустой документ. Представьте, что вы открываете чистый файл Word, на котором позже будете рисовать.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Почему начинаем с пустого `Document`? Потому что Aspose.Words рассматривает класс `Document` как холст для всех последующих операций — добавления абзацев, таблиц или фигур. Если пропустить этот шаг, при попытке вставить что‑либо вы получите `NullPointerException`.

## Шаг 2 – Настройка DocumentBuilder

`DocumentBuilder` — ваш «ручка», которая пишет в `Document`. Это рекомендуемый способ добавления контента, поскольку он автоматически управляет позицией курсора.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Вы можете спросить: «Почему не работать напрямую с документом?» Ответ: builder абстрагирует низкоуровневые детали, такие как работа с секциями, делая код чище и менее подверженным ошибкам.

## Шаг 3 – Вставка прямоугольной фигуры

Теперь самая интересная часть — **как создать фигуру**. Мы вставим прямоугольник размером 100 × 50 пунктов и зададим ему циан‑заполнение, чтобы его было видно.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Несколько замечаний:

* `ShapeType.RECTANGLE` сообщает Aspose, что нам нужен прямоугольник; можно заменить на `OVAL`, `LINE` и т.д.
* Размеры указаны в пунктах (1 pt ≈ 1/72 дюйма). Подгоняйте их под ваш макет.
* Без цвета заливки фигура будет невидима на белой странице — отсюда циан.

## Шаг 4 – Добавление тени и **установка цвета тени**

Здесь мы отвечаем на вопрос **как добавить тень**. Объект `ShadowFormat` управляет каждым визуальным аспектом тени, от цвета до радиуса размытия.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Почему именно такие значения?

* **Visibility** — без `setVisible(true)` остальные настройки игнорируются.
* **Color** — серый нейтрален и подходит как для светлых, так и для тёмных фонов. При желании замените `java.awt.Color.GRAY` на любой другой `java.awt.Color`.
* **Blur radius** — значение `5.0` даёт лёгкое размытие; большие числа делают тень более диффузной.
* **OffsetX/Y** — смещения сдвигают тень вправо и вниз, имитируя источник света сверху‑слева.
* **Transparency** — полупрозрачная тень лучше сочетается со страницей, особенно при печати.

Если нужен более резкий вид, установите радиус размытия `0` и увеличьте смещение. Экспериментируйте — тени сильно зависят от визуального восприятия, а правильные параметры подбираются под дизайн вашего документа.

## Шаг 5 – Сохранение документа

Наконец, сохраняем всё в файл `.docx`. Вы можете указать любой путь, лишь бы директория существовала.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Открыв *Shadow.docx* в Microsoft Word, вы увидите циан‑прямоугольник с лёгкой серой тенью, смещённой на 4 пт вправо и вниз. Это полностью завершённый **create word document** процесс.

### Ожидаемый результат

| Элемент | Внешний вид |
|---------|-------------|
| Прямоугольник | Циан‑заполнение, размер 100 × 50 pt |
| Тень | Серая, 30 % прозрачная, размытие 5 pt, смещение (4, 4) |
| Файл | `Shadow.docx`, сохранённый по указанному пути |

Если фигура не появляется, проверьте, что цвет заливки отличается от цвета фона страницы, и что тень помечена как видимая.

## Полезные советы и распространённые подводные камни

* **Совет:** используйте `rectangle.setStrokeColor(java.awt.Color.BLACK);`, если хотите добавить границу вокруг фигуры. Это делает прямоугольник более заметным на печатной странице.
* **Осторожно:** сохранение в папку только для чтения вызовет `IOException`. Выберите записываемое место или измените права доступа.
* **Особый случай:** если нужна прозрачная заливка (без цвета), вызовите `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Фигура всё равно будет отбрасывать тень, что удобно для водяных знаков.
* **Замечание о производительности:** добавление сотен фигур в цикле может увеличить расход памяти. Вызывайте `document.save` только один раз после добавления всех фигур.

## Полный рабочий пример

Ниже представлен весь код, который можно скопировать в Java‑класс `ShadowDemo`. Он компилируется и запускается «как есть» (при условии, что JAR Aspose.Words находится в classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Запустите программу, откройте полученный *Shadow.docx* — и вы увидите прямоугольник с тенью точно так, как описано.

## Что если понадобится больше фигур?

Вы можете задаться вопросом: «Можно ли **create rectangle shape** несколько раз или использовать другие фигуры?» Конечно. Просто поместите код вставки в цикл и меняйте координаты с помощью `builder.moveTo` или `builder.insertParagraph`. Те же настройки тени можно вынести в вспомогательный метод:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Вызовите `applyStandardShadow(rectangle);` после каждой вставки фигуры, чтобы ваш код оставался DRY (Don’t Repeat Yourself).

## Следующие шаги – Выход за пределы базового уровня

Теперь, когда вы знаете **how to add shadow**, рассмотрите следующие связанные темы:

* **How to set shadow color** для текстовых фрагментов — придаёт заголовкам лёгкое поднятие.
* **Create word document** с таблицами и изображениями — комбинируйте фигуры с другим контентом.
* **How to create shape** анимации с помощью встроенных возможностей Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}