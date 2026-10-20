---
category: general
date: 2026-06-27
description: Узнайте, как вставить прямоугольную форму в Python с помощью Aspose.Words,
  изменить цвет тени, добавить внешнюю тень и применить эффект тени к форме — всё
  в одном учебнике.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: ru
og_description: Освойте, как вставить прямоугольную форму в Python, изменить её цвет
  тени, добавить внешнюю тень и применить эффект тени к форме с помощью Aspose.Words.
og_title: Как вставить прямоугольную форму в Python – учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Как вставить прямоугольную форму в Python — Полное руководство по Aspose.Words
url: /ru/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить прямоугольную форму в Python – Полное руководство Aspose.Words

Когда‑нибудь задумывались **как вставить прямоугольную форму** в документ Word с помощью Python? Вы не одиноки — многие разработчики сталкиваются с этой задачей при автоматизации отчетов или создании шаблонов. Хорошая новость в том, что Aspose.Words делает это проще простого, и в этом руководстве мы пройдем весь процесс, от рисования прямоугольника до добавления к нему стильной внешней тени.

Мы также расскажем **как изменить цвет тени**, **как добавить внешнюю тень**, и о последнем шаге — **применить эффект тени к форме**. К концу вы получите полностью стилизованный прямоугольник, который можно программно вставлять в любой файл .docx.

## Требования

- Python 3.8+ установленный на вашем компьютере  
- Aspose.Words for Python через `pip install aspose-words`  
- Базовые знания скриптинга на Python (глубокие знания Word‑API не требуются)  

Если всё уже готово — отлично, приступаем. Если нет, сначала установите библиотеку; дальше руководство предполагает, что импорт проходит без проблем.

## Как вставить прямоугольную форму с Aspose.Words for Python

Первый шаг — именно то, что обещает основной запрос: **как вставить прямоугольную форму**. Мы создадим новый документ, инициализируем `DocumentBuilder` и разместим прямоугольник на странице.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Почему это важно:** Вызов `insert_shape` — ядро *как вставить прямоугольную форму*. Он возвращает объект `Shape`, которым позже можно управлять — размер, позиция, заливка, границы и т.д. Обратите внимание, что мы также задаём `fill_color`; без неё тень может слиться с белой страницей и стать незаметной.

### Совет профессионалов
Если требуется разместить прямоугольник в определённом месте, используйте `builder.move_to` перед вставкой или отрегулируйте `rectangle.left` и `rectangle.top` после создания.

## Как изменить цвет тени формы

Теперь, когда прямоугольник находится в документе, ответим на вопрос **как изменить цвет тени**. Aspose.Words предоставляет объект `ShadowEffect`, в котором можно задать свойство `color` любым RGB‑значением.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Зачем это нужно:** Тёмная чёрная тень может выглядеть слишком резкой, особенно в светлых документах. Настройка цвета позволяет подстроить её под фирменный стиль или просто добиться более мягкого визуального эффекта.

### Пограничный случай
Если забыть установить `shadow.opacity`, по умолчанию будет полная непрозрачность, из‑за чего тень выглядит как сплошная форма. Всегда сочетайте изменение цвета с подходящим уровнем прозрачности.

## Как добавить внешнюю тень

Следующий часто задаваемый вопрос — **как добавить внешнюю тень**. Флаг `ShadowStyle.OUTER` указывает Aspose.Words отрисовывать тень за пределами контура формы, а не внутри неё.

В приведённом выше фрагменте кода уже используется `ShadowStyle.OUTER`, но для ясности выделим эту настройку отдельно:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Если переключить на `ShadowStyle.INNER`, тень появится *внутри* прямоугольника, что полезно для эффекта тиснения. Для большинства сценариев оформления документов внешний стиль создаёт естественный эффект падающей тени.

## Как применить эффект тени к форме

Мы уже **применили эффект тени к форме**, присвоив `rectangle.shadow = shadow`. Теперь соберём всё вместе и сохраним документ, убедившись, что эффект сохраняется.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

При открытии `RectangleWithShadow.docx` в Microsoft Word вы увидите светло‑синий прямоугольник с тонкой серой внешней тенью, отбрасываемой под углом 45°. Тень будет слегка размыта и смещена, точно как мы её настроили.

### Распространённые подводные камни
- **Отсутствующая папка:** `doc.save` вызовет ошибку, если каталог не существует. Создайте его заранее или используйте `os.makedirs`.
- **Несоответствие версии:** API тени требует Aspose.Words 22.9+; более старые версии просто игнорируют настройки тени.

## Полный рабочий пример

Ниже представлен полностью готовый к запуску скрипт, объединяющий все шаги. Скопируйте его в файл `rectangle_shadow.py` и выполните командой `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Ожидаемый результат:** Word‑документ (`RectangleWithShadow.docx`) с одним прямоугольником и серой внешней тенью. Откройте его в Word, чтобы убедиться в визуальном эффекте.

## Часто задаваемые вопросы

| Вопрос | Ответ |
|----------|--------|
| *Можно ли использовать другой тип формы?* | Конечно — замените `ShapeType.RECTANGLE` на `ShapeType.OVAL`, `ShapeType.TRIANGLE` и т.д., логика тени останется той же. |
| *Как сделать границу толще?* | Установите `rectangle.line_width = 2.0` (points) перед применением тени. |
| *Можно ли анимировать тень?* | Не напрямую через Aspose.Words; для анимации потребуется экспорт в HTML/CSS. |
| *Работает ли это на macOS?* | Да — Aspose.Words платформенно‑независим, пока установлен Python. |

## Заключение

Мы прошли путь от **как вставить прямоугольную форму**, через демонстрацию **как изменить цвет тени**, объяснили **как добавить внешнюю тень** и, наконец, показали **как применить эффект тени к форме** с помощью Aspose.Words for Python. Полный скрипт готов к интеграции в любой конвейер автоматизации, обеспечивая профессиональный прямоугольник с отточенной тенью за считанные секунды.

Готовы к следующему шагу? Попробуйте изменить цвет заливки, поэкспериментировать с разными углами `direction` или добавить несколько форм на одну страницу. Вы также можете изучить богатый API форматирования текста Aspose.Words, чтобы комбинировать тени со стилизованным текстом — идеальный вариант для привлекающих внимание отчетов.

Если вам понравилось это руководство, поставьте лайк, поделитесь им с коллегами или оставьте комментарий со своими вариантами. Приятного кодинга!

![Диаграмма, показывающая, как вставить прямоугольную форму с внешней тенью в документ Word](/images/rectangle-shadow.png)


## Что вам стоит изучить дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом гайде. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}