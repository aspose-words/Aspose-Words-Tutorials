---
category: general
date: 2026-05-04
description: Узнайте, как создать прямоугольную форму, как добавить форму с тенями,
  изменить цвет тени, задать расстояние тени и сохранить документ в формате PDF с
  помощью Aspose.Words для Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: ru
og_description: Создайте прямоугольную форму с помощью Aspose.Words для Python, узнайте,
  как добавить форму, изменить цвет тени, установить расстояние тени и сохранить документ
  в формате PDF.
og_title: Создать прямоугольную форму – добавить тень, изменить цвет и сохранить в
  PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Создание прямоугольной формы в Python – Полное руководство по добавлению теней
  и сохранению в PDF
url: /ru/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной формы – Полное руководство для разработчиков на Python

Когда‑нибудь нужно **создать прямоугольную форму** в документе Word и возникает вопрос, как добавить ей изящную тень? Возможно, вы разрабатываете генератор отчётов, и визуальная отделка имеет значение — особенно когда конечный результат — PDF. Хорошая новость: с Aspose.Words for Python вы можете не только **как добавить форму**, но и настроить каждое свойство тени, от цвета до расстояния, а затем **сохранить документ как pdf** в одном плавном процессе.

В этом руководстве мы пройдём весь процесс шаг за шагом. Вы увидите точный код, который можно скопировать‑вставить, поймёте *почему* каждая строка важна и получите несколько советов по работе с краевыми случаями (например, прозрачные тени или нестандартное DPI). К концу вы сможете **создать прямоугольную форму**, настроить её тень и экспортировать чёткий PDF без усилий.

## Требования

- Python 3.8+ установлен на вашем компьютере.  
- Aspose.Words for Python через `pip install aspose-words`.  
- Базовое знакомство с объектно‑ориентированным Python (ничего сложного).  

Если у вас уже настроено виртуальное окружение, просто выполните команду установки — и всё готово к работе.

## Шаг 1: Инициализация документа и билдера

Прежде чем **как добавить форму**, нужен пустой документ. Класс `Document` представляет весь файл, а `DocumentBuilder` — ваша кисть.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Почему это важно:* `Document` содержит все секции, страницы и ресурсы. `DocumentBuilder` предоставляет удобный API для вставки контента точно туда, где он нужен — представьте себе курсор в текстовом процессоре.

## Шаг 2: Вставка прямоугольной формы

Теперь мы действительно **как добавить форму**. Метод `insert_shape` требует тип формы и её размеры (в пунктах). Здесь мы выбираем прямоугольник 200 × 100 pt и задаём ему светло‑голубую заливку.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Совет профессионала:* Если нужно выровнять форму с существующим текстом, используйте `builder.move_to` перед вставкой или отрегулируйте свойства `left`/`top` после создания.

## Шаг 3: Включение тени

Форма без тени выглядит плоской. Чтобы **установить расстояние тени** и сделать эффект видимым, получаем объект формата тени и включаем его.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Почему этот шаг важен:* Формат тени — отдельный объект; переключение `visible` — первое, что нужно сделать, иначе все остальные свойства тени игнорируются.

## Шаг 4: Настройка тени – Цвет, размытие, расстояние, направление

Здесь происходит магия. Мы **изменим цвет тени**, настроим радиус размытия, зададим, насколько далеко тень будет от прямоугольника, и повернём её на 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Пояснение к каждому свойству:*

| Свойство | Что делает | Типичные значения |
|----------|------------|-------------------|
| `style` | Определяет, будет ли тень *внутренней* или *внешней*. | `OUTER` (самый распространённый) |
| `blur_radius` | Управляет мягкостью; больше → размытие краёв. | обычно 0–20 px |
| `distance` | Как далеко тень смещена от формы. | 0–10 pt для лёгкой, >10 для драматичной |
| `direction` | Угол источника света, измеряется по часовой стрелке от оси x. | 0‑360° |
| `color` | Цвет тени. | Любой `aw.Color` (например, `gray`, `dark_red`) |

*Краевой случай:* Если задать `distance` равным `0`, тень окажется непосредственно под формой, фактически скрыв её заливку. Держите значение выше `0`, чтобы тень была видна.

## Шаг 5: Сохранение документа как PDF

Наконец, мы **сохраняем документ как pdf**. Aspose.Words автоматически растеризует тень, поэтому PDF выглядит точно так же, как в Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Почему PDF?* PDF сохраняет макет на всех платформах, что делает его идеальным для отчётов, счетов‑фактур или любого печатного артефакта.

---

![Создание прямоугольной формы с тенью](https://example.com/images/rectangle-shadow.png){: .align-center alt="пример создания прямоугольной формы с тенью"}

*На изображении выше показан окончательный вывод PDF — светло‑голубый прямоугольник с мягкой серой внешней тенью, точно как мы её настроили.*

## Часто задаваемые вопросы и варианты

### Что делать, если нужна **прозрачная** тень?

Установите альфа‑канал у цвета тени:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Можно ли применить одну и ту же тень к нескольким формам?

Да. Извлеките `ShadowFormat` из одной формы и присвойте его другой:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Как изменить тень для **другого типа формы**?

Все типы форм используют одинаковые свойства `ShadowFormat`, поэтому вы можете переиспользовать тот же блок конфигурации — просто замените `ShapeType.RECTANGLE` на `ShapeType.OVAL`, `ShapeType.TRIANGLE` и т.д.

### Что насчёт **PDF высокого разрешения** для печати?

Укажите `PdfSaveOptions` с более высоким DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Итоги

Мы рассмотрели всё, что нужно для **создания прямоугольной формы**, **как добавить форму**, настройки её **цвета тени**, **установки расстояния тени** и, наконец, **сохранения документа как pdf**. Полный, готовый к запуску скрипт выглядит так:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Запустите скрипт, откройте полученный `ShadowedShape.pdf`, и вы увидите чёткий прямоугольник с лёгкой серой тенью — именно то, что ожидает профессионально оформленный отчёт.

## Что дальше?

- **Исследуйте другие типы форм** (`ShapeType.OVAL`, `ShapeType.LINE`), чтобы обогатить документы.  
- **Комбинируйте несколько теней**, накладывая формы; можно даже создать эффект «сияния», используя внутреннюю тень яркого цвета.  
- **Автоматизируйте пакетную обработку**: пройдитесь по коллекции строк данных, создайте форму для каждой строки и объедините всё в один PDF.  
- **Интегрируйте с другими библиотеками Aspose** (например, Aspose.Slides), если нужно экспортировать тот же визуал в PowerPoint.

Экспериментируйте — меняйте `blur_radius`, играйте с `direction` или заменяйте `gray` на фирменный цвет. API достаточно гибок, чтобы несколько небольших правок существенно изменили визуальное восприятие.

Есть вопросы или сложный сценарий? Оставьте комментарий ниже или обратитесь на форумы сообщества Aspose. Приятного кодинга и наслаждайтесь красиво затенёнными прямоугольниками!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}