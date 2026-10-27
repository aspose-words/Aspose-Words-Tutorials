---
category: general
date: 2026-10-04
description: Как создать документ на Python и добавить тень к фигуре с помощью Aspose.Words.
  Узнайте, как установить цвет тени, вставить прямоугольную форму и настроить внешнюю
  тень.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: ru
lastmod: 2026-10-04
og_description: Как создать документ в Python и добавить тень к фигуре. В этом руководстве
  показано, как установить цвет тени, вставить прямоугольную форму и применить внешнюю
  тень с помощью Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Как создать документ с прямоугольной фигурой и тенью в Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Как создать документ с прямоугольной фигурой и тенью в Python
url: /ru/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ с прямоугольной фигурой и тенью в Python

Если вам нужно **создать документ**, содержащий стилизованный прямоугольник, это руководство предоставляет полное решение. Вы увидите, как **добавить тень к фигуре**, задать цвет тени и управлять её смещением и размытием — все с помощью Aspose.Words for Python. К концу урока вы сможете сгенерировать файл `.docx`, который выглядит отшлифованным и готовым к распространению.

Ниже перечислены все шаги от установки библиотеки до настройки внешнего вида тени. Внешняя документация не требуется; код готов к копированию, запуску и адаптации под ваши проекты. Вы также узнаете, как **вставить прямоугольную фигуру**, выбрать **внешний стиль тени** и справиться с типичными проблемами, такими как невидимая тень или неправильные настройки обтекания.

## Требования

Перед началом убедитесь, что у вас есть:

* Python 3.8 или новее.
* Действующая лицензия Aspose.Words for Python (или бесплатный оценочный ключ).
* Базовые навыки скриптинга на Python.
* Доступ к файловой системе, где будет сохранён сгенерированный документ.

Установить SDK можно с помощью pip:

```bash
pip install aspose-words
```

## Шаг 1: Импортировать библиотеку и создать новый пустой документ

Создание нового документа — это первое действие в любой автоматизации Word. Конструктор `aw.Document()` предоставляет пустой файл, который вы можете заполнять текстом, изображениями или фигурами.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Объект `DocumentBuilder` упрощает вставку содержимого. Он отслеживает текущую позицию курсора, позволяя добавлять элементы последовательно без ручного управления секциями.

## Шаг 2: Вставить прямоугольную фигуру нужного размера

Прямоугольная фигура служит контейнером для визуальных элементов. Вы можете задать её ширину и высоту в пунктах (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

На данном этапе фигура не имеет визуального оформления и выглядит как простая контурная линия. Следующие шаги придадут ей глубину и цвет.

## Шаг 3: Установить фигуру в поток «inline» с окружающим текстом

Когда фигура **inline**, она ведёт себя как символ в абзаце. Это гарантирует, что прямоугольник останется там, где вы ожидаете, в макете документа.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Если вы предпочитаете, чтобы фигура «плавала» над текстом, можно использовать `WrapType.SQUARE` или `WrapType.TOP_BOTTOM`, но для большинства отчётов inline‑фигура обеспечивает предсказуемый макет.

## Шаг 4: Сделать тень видимой и выбрать её цвет

Тень, которая не видна, не приносит пользы. Флаг `visible` активирует эффект, а свойство `color` определяет её оттенок. Чёрный цвет даёт классическую, ненавязчивую глубину.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Вы можете заменить `aw.drawing.Color.black` на любой другой цвет, например `aw.drawing.Color.gray` или пользовательское значение RGB (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Шаг 5: Задать смещение и размытие тени для придания глубины

Смещение контролирует, насколько тень сдвинута от фигуры, а радиус размытия смягчает её края. Маленькие значения дают чёткую тень; большие — мягкий вид.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Экспериментируйте с этими числами, чтобы соответствовать вашим дизайнерским требованиям. Для сильной падающей тени можно увеличить и смещение, и размытие.

## Шаг 6: Выбрать внешний стиль тени

Aspose.Words предлагает несколько стилей тени, таких как `INNER`, `OUTER` и `PERSPECTIVE`. **Внешний** стиль размещает тень за пределами границы фигуры, что идеально подходит для чистого, профессионального вида.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Если нужен более драматичный эффект, попробуйте `ShadowStyle.PERSPECTIVE` — он добавит трёхмерный наклон.

## Шаг 7: Сохранить документ с фигурой и тенью

Сохранение завершает работу с файлом и записывает всё форматирование на диск. Выберите каталог, в котором у вас есть права записи, и дайте файлу понятное имя.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Запуск скрипта создаст Word‑файл, содержащий прямоугольник с видимой, цветной тенью. Откройте файл в Microsoft Word или LibreOffice, чтобы проверить результат.

## Полный исполняемый пример

Ниже приведён полный скрипт, включающий каждый из описанных шагов. Скопируйте код в файл `create_shadowed_shape.py` и выполните его командой `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Ожидаемый результат**

При открытии `ShapeWithShadow.docx` вы увидите один прямоугольник, центрированный на странице. Прямоугольник сопровождается лёгкой чёрной тенью, смещённой вниз‑вправо и слегка размытой для создания глубины. Тень использует внешний стиль, поэтому она не пересекает внутреннюю часть прямоугольника.

## Часто задаваемые вопросы и особые случаи

### Почему тень иногда не видна?

Тень отрисовывается только если `shadow.visible` установлен в `True` **и** тип обтекания `wrap_type` фигуры позволяет её отображать. Inline‑фигура работает надёжно; плавающие фигуры могут потребовать дополнительных настроек макета.

### Как изменить цвет тени, чтобы он соответствовал фирменной палитре?

Замените `aw.drawing.Color.black` на пользовательское значение RGB:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Что делать, если нужно, чтобы фигура находилась позади текста?

Установите тип обтекания в `WrapType.BEHIND` и при необходимости скорректируйте `z_order_position`. Учтите, что некоторые просмотрщики могут по‑разному отображать фигуры позади текста.

### Можно ли применить одинаковые настройки тени к нескольким фигурам?

Да. Создайте вспомогательную функцию, которая конфигурирует тень, и вызывайте её для каждой вставляемой фигуры. Это повышает переиспользуемость кода и обеспечивает единообразный стиль.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Заключение

Теперь вы знаете, **как создать документ**, содержащий прямоугольную фигуру с настраиваемой тенью, используя Aspose.Words for Python. В руководстве рассмотрены вставка прямоугольника, перевод фигуры в режим inline, включение тени, установка её цвета, смещения, размытия и стиля, а также сохранение файла.

Дальше вы можете изучать связанные темы, такие как **add shadow to shape** для других типов фигур, **set shadow color** динамически на основе данных или **how to add shadow** к изображениям и текстовым блокам. Экспериментируйте с различными размерами, цветами и стилями тени, чтобы соответствовать вашим бренд‑гайдам или системе дизайна.

Готовы автоматизировать больше Word‑документов? Попробуйте добавить таблицы, заголовки или динамический контент — каждый шаг опирается на те же принципы, продемонстрированные здесь. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}