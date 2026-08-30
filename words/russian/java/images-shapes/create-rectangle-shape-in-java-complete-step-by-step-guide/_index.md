---
category: general
date: 2026-07-03
description: Создайте прямоугольник в Java и узнайте, как добавить к нему тень, применить
  эффект тени, установить прозрачность фигуры и быстро создать пустой документ.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: ru
og_description: Создайте прямоугольную форму в Java с тенью, прозрачностью и пустым
  документом. Следуйте этому руководству, чтобы освоить обработку фигур.
og_title: Создайте прямоугольник в Java – Полный учебник по программированию
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Создание прямоугольной формы в Java — Полное пошаговое руководство
url: /ru/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Java – Полное пошаговое руководство

Когда‑нибудь задумывались, как **создать прямоугольную фигуру** в документе Word с помощью Java? Вы не одиноки — разработчикам часто нужен быстрый способ добавить геометрическую графику, а затем придать ей лёгкую тень, чтобы макет выглядел более изысканным. В этом руководстве мы пройдём весь процесс: от создания **пустого документа** до **добавления тени к фигуре**, **применения эффекта тени** и даже **установки прозрачности фигуры** для профессионального вида.

Ниже приведён полностью рабочий пример кода, который вы можете скопировать и вставить в свой проект. Никакой внешней документации не требуется — просто следуйте шагам, поймите «почему», и вы будете генерировать прямоугольники с тенью за считанные секунды.

## Что вы узнаете

- Как **программно создать прямоугольную фигуру** с помощью Aspose.Words for Java.  
- Точные вызовы, необходимые для **добавления тени к фигуре** и настройки её визуальных свойств.  
- Способы **применения эффекта тени** и настройки параметров, таких как смещение, радиус размытия и цвет.  
- Техники **установки прозрачности фигуры** для более мягкого внешнего вида.  
- Как **создать пустой документ**, вставить фигуру и сохранить результат.

> **Pro tip:** Все эти действия выполняются над одним экземпляром `Document`, что позволяет цепочкой вызывать их без необходимости промежуточного ввода‑вывода файлов.

## Предварительные требования

Прежде чем мы начнём, убедитесь, что у вас есть:

- Установлен Java 17 (или любой современный JDK).  
- Библиотека Aspose.Words for Java добавлена в проект (Maven‑координаты: `com.aspose:aspose-words:23.12`).  
- Java‑IDE или простой текстовый редактор — ничего сложного, лишь место для компиляции и запуска.

Если чего‑то не хватает, скачайте JDK с сайта Oracle и подключите зависимость Aspose через Maven или Gradle. После этого вы готовы к работе.

## Шаг 1: **Create blank document** – холст для всего

Первое, что вам нужно, — пустой объект `Document`. Представьте его как чистый лист бумаги; без него некуда помещать ваш прямоугольник.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Почему начинаем с пустого документа? Потому что каждая фигура живёт внутри `Section`, а только что созданный `Document` уже содержит секцию по умолчанию с телом, готовым принимать узлы. Пропуск этого шага заставил бы вас вручную создавать секции позже, что добавляет лишнюю сложность.

## Шаг 2: **Create rectangle shape** и определите её размеры

Теперь, когда у нас есть холст, давайте **создадим прямоугольную фигуру**. Класс `Shape` принимает ссылку на документ и `ShapeType`. Здесь мы выбираем `RECTANGLE` и задаём ширину/высоту в пунктах (1 pt ≈ 1/72 дюйма).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Зачем устанавливать `WrapType.INLINE`? Обтекание INLINE заставляет фигуру вести себя как символ в абзаце, гарантируя её перемещение вместе с окружающим текстом. Если нужен плавающий режим, переключитесь на `WrapType.SQUARE` или `WrapType.TOP_BOTTOM`.

## Шаг 3: **Apply shadow effect** – придаём прямоугольнику глубину

Плоский прямоугольник выглядит… ну, плоско. Добавление тени делает его выразительнее. Мы **применим эффект тени**, создав экземпляр `ShadowEffect`, а затем настроив его визуальные свойства.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Разберём подробнее:

- **Color** – `Color.getGray(0.5)` даёт 50 % серый, нейтральный и подходящий для большинства фонов.  
- **OffsetX/Y** – Положительные значения смещают тень вправо и вниз; отрицательные — влево и вверх.  
- **BlurRadius** – Большие значения создают более мягкую, рассеянную тень.  
- **Transparency** – Диапазон от `0` (непрозрачная) до `1` (полностью прозрачная). Здесь выбрано `0.3` для лёгкого эффекта.

## Шаг 4: **Add shadow to shape** – привязываем эффект

Создать эффект недостаточно; нужно **добавить тень к фигуре**, присвоив объект `ShadowEffect` нашему прямоугольнику.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

За кулисами этот вызов обновляет базовую разметку OpenXML (`<w:shdw>`), которую Word использует для отрисовки теней. Если открыть сохранённый `.docx`, вы увидите элемент `<w:effect>` с нашими параметрами.

## Шаг 5: **Set shape transparency** – опционально, но часто полезно

Иногда хочется, чтобы сам прямоугольник был полупрозрачным, позволяя видеть текст фона. Класс `Shape` предоставляет `setFillColor` и `setFillTransparency`. Ниже быстрый пример, делающий фигуру на 40 % прозрачной:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Зачем это может понадобиться? Представьте водяной знак или выделенный блок, где основной контент должен оставаться читаемым. Регулируйте значение прозрачности под ваш дизайн.

## Шаг 6: Вставка фигуры в документ

Мы создали прямоугольник, добавили тень и (по желанию) задали прозрачность. Последний шаг — **добавить фигуру в первую секцию документа**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Добавление фигуры в тело помещает её в конец первого абзаца. Если нужен конкретный пункт вставки, получите целевой `Paragraph` и используйте `insertBefore` или `insertAfter`.

## Шаг 7: Сохранить документ – увидеть результат

Вся эта работа завершается единственным вызовом `save`. Укажите путь, подходящий для вашей среды.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Откройте полученный `ShadowShape.docx` в Microsoft Word или LibreOffice, и вы увидите чёткий прямоугольник с лёгкой серой тенью, слегка прозрачный, если вы выполнили опциональный шаг. Визуал соответствует параметрам, заданным программно.

---

![создание прямоугольной фигуры с тенью в документе Word](https://example.com/images/rectangle-shadow.png "создание прямоугольной фигуры с тенью")

*Текст alt:* **создание прямоугольной фигуры с тенью** – визуальное представление конечного результата.

## Часто задаваемые вопросы и особые случаи

### Что делать, если я хочу другую цветовую тень?

Просто измените вызов `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Помните, что слишком яркие тени могут выглядеть непрофессионально; обычно лучше использовать мягкие оттенки.

### Можно ли применить одну и ту же тень к нескольким фигурам?

Да. Создайте один экземпляр `ShadowEffect`, настройте его и переиспользуйте:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Только не меняйте `ShadowEffect` после того, как привязали его к другим фигурам, если только вы не хотите обновить их все сразу.

### Как динамически менять размытие тени?

Создайте UI‑ползунок, который будет менять значение `setBlurRadius`. Обычно используют диапазон от `2` до `12`; большие числа дают «сияние», а не чёткую тень.

### Что если мне нужна плавающая фигура, а не inline?

Смените тип обтекания:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Плавающие фигуры дают большую свободу вёрстки, но требуют дополнительной логики позиционирования.

## Полный рабочий пример

Ниже полностью готовая к копированию программа, включающая все обсуждённые шаги. Запустите её как обычное Java‑приложение.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Ожидаемый результат:** При открытии `ShadowShape.docx` вы увидите белый прямоугольник размером 200 × 100 pt, центрированный в первом абзаце, со средней серой тенью, смещённой на 5 pt, размытой радиусом 8 и 30 % прозрачностью. Сам прямоугольник будет 40 % прозрачен, позволяя просвечивать любой подложный текст.

## Подведение итогов

Мы только что **создали прямоугольную фигуру** с нуля, **добавили тень к фигуре**, **применили эффект тени** и даже **установили прозрачность фигуры** — всё это на основе **создания пустого документа**. Подход прост, использует плавный API Aspose.Words и может быть расширен до кругов, звёзд или пользовательских полигонов.

Что дальше в вашем плане? Попробуйте заменить `ShapeType.RECTANGLE` на `ShapeType.OVAL`, чтобы генерировать тени для кругов, или поэкспериментируйте с градиентными заливками для

## Что вам стоит изучить дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом гайде. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}