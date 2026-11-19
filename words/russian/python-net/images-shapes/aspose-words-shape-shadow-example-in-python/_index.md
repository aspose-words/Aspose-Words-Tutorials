---
category: general
date: 2026-11-18
description: Пример тени формы Aspose.Words демонстрирует, как добавить тень к объекту
  Word с помощью Python. Следуйте этому пошаговому руководству, чтобы изменить и сохранить
  документ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: ru
lastmod: 2026-11-18
og_description: Пример тени формы в Aspose.Words демонстрирует, как добавить тень
  к объекту Word с помощью Python. Узнайте полный код, почему каждый шаг важен и как
  его адаптировать.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Пример тени фигуры Aspose.Words – руководство по Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Пример тени фигуры Aspose.Words в Python
url: /ru/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Пример тени для фигуры Aspose.Words на Python

Пример тени для фигуры Aspose.Words демонстрирует, как добавить эффект тени к фигуре в документе Word с помощью Python. В этом руководстве вы получите полностью готовый к запуску скрипт, который загружает документ, настраивает тень и сохраняет результат.

Применение тени к фигуре — распространённый способ улучшить визуальную иерархию в отчётах, брошюрах или счетах. Приведённый ниже код работает с Aspose.Words for Python via .NET и не требует дополнительных сторонних библиотек.

## Что вы узнаете

* Как загрузить файл `.docx` с помощью **Aspose.Words for Python**.  
* Как найти первую фигуру (включая фигуры внутри таблиц или групп).  
* Как настроить размытие тени, горизонтальное и вертикальное смещение.  
* Как сохранить изменённый документ, сохранив всё остальное содержимое.  

**Требования**

* Python 3.8 или новее.  
* Aspose.Words for Python via .NET установлен (`pip install aspose-words`).  
* Документ Word (`input.docx`), содержащий хотя бы одну фигуру (например, изображение, AutoShape или текстовое поле).  

Если необходимо установить библиотеку, выполните:

```bash
pip install aspose-words
```

## Обзор примера тени для фигуры Aspose.Words

Ниже представлен полный скрипт. Он следует четырём логическим шагам типичного рабочего процесса **манипуляции документами Aspose**: загрузка, поиск, изменение и сохранение.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Ожидаемый результат

Откройте `output.docx` в Microsoft Word. Первая добавленная вами фигура теперь должна отображать мягкую тень, смещённую на 2 pt по горизонтали и вертикали, с радиусом размытия 5 pt. Всё остальное содержимое остаётся без изменений.

## Шаг 1: Загрузка документа Word

Загрузка документа — первая операция в любом рабочем процессе **Aspose.Words for Python**. Класс `Document` разбирает файл и создаёт объектную модель в памяти. Поскольку библиотека работает на платформе .NET, она может эффективно обрабатывать большие файлы.

*Почему это важно:* Загрузка документа один раз и хранение ссылки (`doc`) избавляет от повторных операций ввода‑вывода, что повышает производительность при необходимости выполнить несколько изменений.

## Шаг 2: Доступ к фигуре

Фигуры могут быть прямыми дочерними элементами тела документа, либо находиться внутри таблиц, групп или холстов рисования. Вызов `get_child(NodeType.SHAPE, 0, True)` рекурсивно ищет и возвращает первую подходящую фигуру.

*Почему это важно:* Флаг `True` гарантирует, что вы не пропустите фигуры, скрытые внутри других узлов. Если его опустить, будут учитываться только фигуры верхнего уровня, и во многих реальных документах результатом будет `None`.

### Альтернатива: Поиск фигуры по имени

Если в документе несколько фигур, вы можете захотеть найти конкретную:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Этот фрагмент демонстрирует вариант **python shape shadow**, который фильтрует по свойству `name` фигуры.

## Шаг 3: Настройка тени фигуры

Свойство `shadow` объекта `Shape` предоставляет тонкую настройку визуального эффекта. Три наиболее часто изменяемых атрибута:

| Свойство | Типичный диапазон | Визуальный эффект |
|----------|-------------------|-------------------|
| `blur`   | 0 – 15            | Более высокие значения создают более мягкий край. |
| `offset_x` | –10 – 10        | Положительные значения смещают тень вправо. |
| `offset_y` | –10 – 10        | Положительные значения смещают тень вниз. |

Вы также можете изменить `color`, `transparency`, `visible` и `style`. В примере задаётся умеренное размытие и небольшое смещение, чтобы тень оставалась ненавязчивой.

**Полезный совет:** Если у фигуры уже есть тень, указанные свойства перезапишут существующие настройки. Чтобы сохранить оригинальный стиль, прочитайте текущие значения перед их изменением.

## Шаг 4: Сохранение изменённого документа

Вызов `doc.save()` записывает представление в памяти обратно в файл `.docx`. Aspose.Words автоматически обновляет все внутренние связи, поэтому полученный файл полностью совместим с Microsoft Word.

*Почему это важно:* Сохранение один раз в конце процесса снижает риск повреждения файла и повышает общую скорость, особенно при пакетной обработке большого количества документов.

## Распространённые варианты и граничные случаи

### Работа с несколькими фигурами

Если нужно применить одну и ту же тень ко всем фигурам, пройдитесь по коллекции узлов:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Применение тени к определённому типу фигур

Можно фильтровать по `ShapeType` (например, `aw.ShapeType.IMAGE`). Это полезно, когда требуется затронуть только изображения, а не AutoShape.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Обработка документов без фигур

Скрипт уже генерирует понятную `ValueError`, если фигура не найдена. В производственном коде вы можете записать эту проблему в журнал и продолжить обработку остальных файлов.

### Примечания о совместимости

* Код работает с **Aspose.Words for Python via .NET** версии 23.10 и новее.  
* Эффект тени поддерживается в Word 2007+ (`.docx`). Старые форматы (`.doc`) потеряют эффект после конвертации.

## Заключение

Этот **aspose.words shape shadow example** проводит вас через загрузку файла Word, поиск фигуры, настройку её тени и сохранение результата с помощью **Aspose.Words for Python**. Теперь у вас есть переиспользуемый шаблон для любой задачи **манипуляции документами Aspose**, связанной с визуальными улучшениями.

Далее вы можете изучить:

* Добавление градиентных заливок или стилей линий к фигурам (`modify shape shadow` и другие визуальные свойства).  
* Комбинирование настройки тени с форматированием текста для создания полностью стилизованных шаблонов.  
* Автоматизацию процесса для пакета документов с использованием `os.listdir` и показанного выше шаблона.

Не стесняйтесь экспериментировать с различными уровнями размытия, смещениями и цветами, чтобы соответствовать требованиям вашего бренда. Приятного кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}