---
category: general
date: 2026-06-30
description: Добавьте тень к фигуре с помощью Aspose.Words для Python. Узнайте, как
  задать расстояние тени, настроить размытие и быстро сохранить PDF с тенью фигуры.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: ru
og_description: Добавьте тень к фигуре в документе Word с помощью Aspose.Words для
  Python. Этот учебник показывает, как установить расстояние тени, размытие и цвет,
  а затем сохранить в PDF.
og_title: Добавление тени к фигуре в Python — Полное руководство по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Добавление тени к фигуре в Python с Aspose.Words – Полное руководство
url: /ru/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавить тень к фигуре в Python с Aspose.Words – Полное руководство

Добавить тень к фигуре в документе Word с помощью Aspose.Words for Python проще, чем вы думаете. Если вы когда‑либо задавались вопросом **как установить расстояние тени** или **как добавить тень к фигуре** для профессионального вида, это руководство вам поможет.

В течение нескольких минут мы пройдем всё, что вам нужно: от создания нового документа, вставки прямоугольника, настройки свойств тени, до окончательного сохранения PDF, демонстрирующего эффект. К концу вы сможете добавить тень к любой фигуре — прямоугольнику, эллипсу или пользовательскому рисунку — не копаясь в документации API.

> **Prerequisites** – У вас должен быть установлен Python 3.7+, лицензия Aspose.Words for Python (или бесплатная оценочная версия) и базовое знакомство с написанием скриптов на Python. Другие внешние библиотеки не требуются.

---

## Обзор шагов по добавлению тени к фигуре

Ниже представлена быстрая дорожная карта того, что мы сделаем:

1. **Создать новый документ** и `DocumentBuilder` для его редактирования.  
2. **Вставить форму‑прямоугольник** нужного размера.  
3. **Включить и настроить тень** — здесь проявляется основной ключевой запрос.  
4. **Сохранить документ** в формате PDF, сохраняющем тень фигуры.

Каждый шаг вынесен в отдельный раздел, чтобы вы могли скопировать‑вставить фрагменты кода прямо в свою IDE.

---

## Шаг 1: Инициализация документа и билдера

Сначала — без `Document` у вас нет над чем работать. `DocumentBuilder` — это ваша кисть.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Почему это важно*: Объект `Document` представляет весь файл, а `DocumentBuilder` упрощает вставку текста, таблиц и фигур. Считайте билдер курсором, которым можно перемещаться по странице.

---

## Шаг 2: Вставка формы‑прямоугольника

Теперь добавим прямоугольник — полотно для эффекта тени. При необходимости замените `RECTANGLE` на `ELLIPSE`, `STAR` или любой другой `ShapeType`.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Pro tip*: Размеры указаны в пунктах (1 pt ≈ 1/72 дюйма). Подгоните их под ваш макет; тень будет масштабироваться автоматически.

---

## Как установить расстояние тени

**Расстояние** тени определяет, насколько далеко она будет от фигуры. Большое расстояние имитирует более удалённый источник света, а небольшое — делает подъём более тонким.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Note**: Расстояние работает совместно с `angle`. Изменяя угол, вы вращаете тень вокруг фигуры, а `distance` отодвигает её наружу.

---

## Как добавить тень к фигуре – настройка размытия, цвета и угла

Добавление тени — это не просто включение её; часто требуется подправить размытие, цвет и направление для реалистичного эффекта.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Почему эти настройки?*  
- **Blur radius** смягчает края, предотвращая резкую силуэтную линию.  
- **Angle** имитирует источник света; 45° — обычный дефолт, выглядящий сбалансированно.  
- **Color** может быть любым объектом `Color`; попробуйте `Color.gray` для более мягкого эффекта.

---

## Шаг 4: Сохранение документа в PDF

Когда фигура и её тень готовы, сохранить результат проще простого. Aspose.Words автоматически конвертирует в PDF, сохраняя визуальную точность.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Ожидаемый результат*: Откройте сгенерированный `ShadowShape.pdf`. Вы увидите одну страницу с прямоугольником 200 × 100 pt, тень которого отодвинута на 4 pt под углом 45°, размытие — 5 pt. Тень должна выглядеть как лёгкое серо‑чёрное ореол, облегающий фигуру.

---

## Часто задаваемые вопросы и особые случаи

### Что делать, если нужна другая фигура?

Замените `aw.drawing.ShapeType.RECTANGLE` на любое другое значение перечисления, например `aw.drawing.ShapeType.ELLIPSE`. Те же свойства тени применятся — дополнительный код не нужен.

### Можно ли применить тень к нескольким фигурам одновременно?

Да. Пройдитесь в цикле по созданным фигурам и настройте каждый `shadow_format` отдельно. Быстрый пример:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Как изменить непрозрачность тени?

Используйте свойство `shadow.transparency` (0 = непрозрачная, 1 = полностью прозрачная):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Полный рабочий пример

Ниже представлен полностью готовый скрипт — скопируйте, укажите папку вывода и запустите. Ничего не пропущено.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Запустите скрипт, затем откройте полученный PDF. Вы должны увидеть прямоугольник с чёткой, смещённой тенью — именно то, что обещает **add shadow to shape**.

---

## Заключение

Мы продемонстрировали, как **add shadow to shape** в документе Word с помощью Aspose.Words for Python, охватив ключевые шаги по **set shadow distance**, настройке размытия, угла и цвета, а также экспортированию PDF с сохранением эффекта. Эта техника работает с любым типом фигуры, и её можно расширять с помощью циклов, изменения прозрачности или даже градиентных теней.

Готовы к следующему вызову? Попробуйте комбинировать несколько теней, накладывать фигуры друг на друга или генерировать отчёт, где каждый график получает собственную стилизованную тень. Эксперименты закрепят концепции и откроют новые возможности автоматизации документов.

Если это руководство оказалось полезным, поделитесь им, поставьте звёздочку репозиторию Aspose.Words или оставьте комментарий со своими советами по настройке теней. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}