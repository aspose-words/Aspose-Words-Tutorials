---
category: general
date: 2026-06-05
description: Пример создания документа Word на Python демонстрирует, как добавить
  тень к фигуре, применяя эффект тени в Word с помощью Aspose.Words.
draft: false
keywords:
- create word document python
- how to add shadow
- add shadow to shape
- apply shadow effect word
- insert shape with shadow
language: ru
og_description: Учебник по созданию документа Word на Python пошагово покажет, как
  добавить тень к фигуре и применить эффект тени в Word с помощью Aspose.Words.
og_title: Создать документ Word на Python – добавить тень к фигуре
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Create Word document Python example shows how to add shadow to a shape,
    applying shadow effect in Word with Aspose.Words.
  headline: Create Word Document Python – Add Shadow to Shape Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Use `builder.insert_image(...)` to place an image, then access
      `image_shape.shadow_format` just like we did with the rectangle.
    question: Can I add a shadow to a picture instead of a shape?
  - answer: Yes. Aspose.Words preserves shape effects during conversion, so the PDF
      will retain the shadow.
    question: Does the shadow survive when I convert the document to PDF?
  - answer: Call `builder.insert_shape` for each shape, then configure each shape’s
      `shadow_format` independently. No shared state.
    question: What if I need multiple shapes with different shadows?
  - answer: 'Minimal for typical documents. If you’re generating thousands of shapes,
      consider batch processing or limiting blur radius to keep rendering fast. ##
      Conclusion We’ve just demonstrated how to **create Word document python** code
      that inserts a rectangle and **adds shadow to shape** using Aspose.Word'
    question: Is there a performance impact when adding many shadows?
  type: FAQPage
tags:
- python
- aspose-words
- document automation
title: Создание Word‑документа на Python – Руководство по добавлению тени к фигуре
url: /ru/python/images-shapes/create-word-document-python-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word документа Python – Руководство по добавлению тени к фигуре

Когда‑то задавались вопросом, как **создать Word документ python** код, который не только вставляет фигуру, но и придаёт ей стильную тень? Вы не одиноки. Во многих отчетах, счетах‑фактурах или рекламных листовках тонкая тень может заставить прямоугольник выглядеть так, будто он отрывается от страницы, добавляя глубину без дополнительных графических элементов.

В этом руководстве мы пройдемся по полностью готовому, исполняемому примеру, который показывает, **как добавить тень** к фигуре с помощью Aspose.Words for Python. К концу вы получите файл `.docx` с прямоугольником, отбрасывающим мягкую тень под углом 45° — идеально для того, чтобы ваши документы выглядели отполированными и профессиональными.

## Что покрывает это руководство

Мы начнём с настройки окружения, затем создадим новый Word документ, вставим прямоугольник, настроим свойства его тени и, наконец, сохраним файл. По пути мы обсудим, почему важна каждая настройка, типичные подводные камни и несколько дополнительных приёмов, которые вы можете попробовать. Внешних ссылок не требуется; всё, что нужно, находится здесь.

**Prerequisites**

- Python 3.8+ установлен  
- пакет `aspose-words` (`pip install aspose-words`)  
- базовое знакомство с синтаксисом Python (если вы уже писали «Hello, World!», вам достаточно)

Готовы? Поехали.

## Шаг 1: Инициализация документа – Основы **Create Word Document Python**

Первое, что вам нужно — это пустой объект документа и `DocumentBuilder`, позволяющий добавлять содержимое. Думайте о билдере как о ручке, пишущей в файл Word.

```python
import aspose.words as aw

# Create a new, empty Word document
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add elements
builder = aw.DocumentBuilder(doc)
```

*Почему это важно:* `aw.Document()` — точка входа для любой операции Aspose.Words. Без него нельзя добавить фигуры, текст или любой другой элемент. Билдер хранит ссылку на документ, поэтому не требуется передавать документ вручную.

## Шаг 2: Вставка прямоугольника – Логика **Insert Shape With Shadow**

Теперь разместим прямоугольник на странице. Размеры указаны в пунктах (1 pt ≈ 1/72 дюйма), так что 150 × 100 pt дают красиво пропорциональный блок.

```python
# Insert a rectangle shape of 150x100 points
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
```

*Совет:* Если нужен другой тип фигуры, просто замените `ShapeType.RECTANGLE` на `ShapeType.ELLIPSE`, `ShapeType.CLOUD` и т.д. Тот же код настройки тени работает для любой выбранной фигуры.

## Шаг 3: Применение эффекта тени – **How To Add Shadow** Точно

Здесь происходит магия. Объект `shadow_format` управляет видимостью, расстоянием, размытием, углом, цветом и прозрачностью. Настраивая каждое свойство, вы получаете желаемый вид.

```python
# Grab the shadow formatting object
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set how far the shadow sits from the shape (in points)
shadow.distance = 5.0

# Blur radius controls softness; higher = fuzzier edges
shadow.blur = 3.0

# Angle determines the light source direction (degrees clockwise from the x‑axis)
shadow.angle = 45

# Choose a color – black works for most professional documents
shadow.color = aw.drawing.Color.black

# Transparency is a float from 0 (opaque) to 1 (fully transparent)
shadow.transparency = 0.4   # 40 % transparent gives a subtle effect
```

**Почему каждая настройка важна**

| Свойство | Типичное использование | Визуальный эффект |
|----------|------------------------|-------------------|
| `visible` | Включает/выключает эффект | Нет тени, если `False` |
| `distance` | Управляет смещением от фигуры | Большие значения отодвигают тень дальше |
| `blur` | Смягчает края | Чем выше размытость, тем более диффузная тень |
| `angle` | Симулирует направление света | 0° = тень вправо, 90° = вниз |
| `color` | Соответствует бренду или теме | Белая тень обычно не имеет смысла |
| `transparency` | Регулирует непрозрачность | 0.0 = сплошная, 0.8 = почти незаметная |

*Распространённая ошибка:* забыть установить `shadow.visible = True` — в результате будет правильная фигура, но без тени, что легко пропустить, сосредоточившись на цвете или размере.

## Шаг 4: Сохранение документа – Финальный шаг **Create Word Document Python**

После настройки фигуры просто запишите документ на диск. Вы можете выбрать любой поддерживаемый формат (`.docx`, `.pdf`, `.html` и т.д.). В этом руководстве мы останемся с классическим `.docx`.

```python
# Save the document to the desired location
output_path = "shadowed_shape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Когда откроете `shadowed_shape.docx` в Microsoft Word (или любом совместимом просмотрщике), вы увидите прямоугольник с чёткой тенью под углом 45° — именно то, что описывает код выше.

### Ожидаемый результат

- Одностраничный файл Word.  
- Один прямоугольник, центрированный там, где находился билдер.  
- Полупрозрачная чёрная тень, смещённая на 5 pt, размытие 3 pt, под углом 45°.

Если тень не отображается, проверьте, что `shadow.visible` установлен в `True`, и что вы используете просмотрщик, поддерживающий эффекты фигур (большинство современных версий Word поддерживают).

## Бонус: Настройка тени под разные стили

Возможно, вам нужен более мягкий вид для корпоративного отчёта или яркая, цветная тень для рекламного листа. Ниже несколько быстрых вариантов:

```python
# Soft gray shadow for subtle emphasis
shadow.color = aw.drawing.Color.gray
shadow.transparency = 0.6
shadow.blur = 5.0
shadow.distance = 3.0

# Red, dramatic shadow for a creative brochure
shadow.color = aw.drawing.Color.red
shadow.transparency = 0.2
shadow.blur = 2.0
shadow.angle = 120
```

Экспериментировать с этими значениями — лучший способ понять, как **add shadow to shape** работает на практике.

## Визуальный предварительный просмотр (Alt Text включён)

![Shadowed rectangle shape in a Word document – create word document python example](/images/shadowed_rectangle.png)

*Alt text:* *Прямоугольник с тенью в документе Word – пример создания Word документа Python.*

## Часто задаваемые вопросы

**Q: Можно ли добавить тень к изображению вместо фигуры?**  
A: Конечно. Используйте `builder.insert_image(...)` для размещения изображения, затем обращайтесь к `image_shape.shadow_format` так же, как мы делали с прямоугольником.

**Q: Сохраняется ли тень при конвертации документа в PDF?**  
A: Да. Aspose.Words сохраняет эффекты фигур при конвертации, поэтому PDF также будет содержать тень.

**Q: Что делать, если нужно несколько фигур с разными тенями?**  
A: Вызывайте `builder.insert_shape` для каждой фигуры, затем независимо настраивайте `shadow_format` каждой из них. Общего состояния нет.

**Q: Влияет ли добавление множества теней на производительность?**  
A: Минимально для типичных документов. Если генерируете тысячи фигур, рассмотрите пакетную обработку или ограничьте радиус размытия, чтобы ускорить рендеринг.

## Заключение

Мы только что продемонстрировали, как **create Word document python** код вставляет прямоугольник и **adds shadow to shape** с помощью Aspose.Words. Настраивая `shadow_format`, вы можете **apply shadow effect word** документы с точным контролем расстояния, размытия, угла, цвета и прозрачности. Та же схема работает для любой фигуры, изображения или даже текстового блока, предоставляя универсальный набор инструментов для профессионально выглядящих документов.

Что дальше? Попробуйте комбинировать несколько фигур, накладывать текст сверху или экспортировать в PDF, чтобы увидеть, как тень сохраняется при конвертации. Вы также можете исследовать другие визуальные эффекты, такие как glow или reflection — просто замените `shadow_format` на `glow_format` или `reflection_format`.

Счастливого кодинга, и пусть ваши документы всегда обладают дополнительной глубиной!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}