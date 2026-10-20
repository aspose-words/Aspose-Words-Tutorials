---
category: general
date: 2026-06-21
description: Создайте прямоугольную форму в Python с помощью Aspose.Words. Узнайте,
  как добавить тень к форме, установить цвет её заливки и сохранить документ в PDF
  за несколько минут.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: ru
og_description: Создайте прямоугольную форму в Python с помощью Aspose.Words. Это
  руководство показывает, как добавить тень к форме, установить цвет заливки формы
  и сохранить документ в PDF.
og_title: Создайте прямоугольную форму в Python – учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Создать прямоугольную форму в Python – учебник Aspose.Words
url: /ru/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Python – руководство Aspose.Words

Когда‑то задавались вопросом **как создать прямоугольную фигуру** в документе Word, пока пишете код на Python? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда нужен быстрый визуальный элемент — например, цветной блок с лёгкой тенью — а затем требуется экспортировать всё в PDF.  

В этом руководстве мы пройдём полный, готовый к запуску пример, который **создаёт прямоугольную фигуру**, **задаёт цвет заливки**, **добавляет тень к фигуре** и, наконец, **сохраняет документ как PDF**. Никаких расплывчатых ссылок, только конкретный код, который можно скопировать‑вставить и запустить уже сегодня.

## Что понадобится

Прежде чем погрузиться в детали, убедитесь, что на вашей машине установлено следующее:

- Python 3.8 или новее (используемый синтаксис работает в любой современной версии).
- Действующая лицензия Aspose.Words for Python или бесплатный пробный период (библиотека чисто Python, без необходимости COM‑interop).
- Текстовый редактор или IDE, с которым вам удобно работать — VS Code отлично подходит, но подойдёт любой.

Это всё. Никаких тяжёлых фреймворков, никаких дополнительных зависимостей уровня ОС. Приступим.

## Шаг 1: Установить Aspose.Words for Python

Сначала. Если вы ещё не сделали этого, скачайте пакет с PyPI:

```bash
pip install aspose-words
```

Почему это важно: Aspose.Words предоставляет классы `Document` и `DocumentBuilder`, на которые мы будем опираться. Без библиотеки вызовы вроде `insert_shape` не существуют, и скрипт упадёт ещё до того, как нарисует линию.

> **Pro tip:** Держите виртуальное окружение в порядке. Выполните `python -m venv .venv && source .venv/bin/activate` перед установкой, чтобы библиотека была изолирована от системных пакетов.

## Шаг 2: Создать новый документ и DocumentBuilder

Теперь мы действительно **создаём прямоугольную фигуру** — но сначала нужен чистый холст.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Объект `Document` представляет весь файл, а `DocumentBuilder` — удобный помощник, который знает, где находится курсор, и может вставлять элементы в эту точку. Думайте о builder как о перье, пишущем на странице.

## Шаг 3: Вставить прямоугольную фигуру

Здесь происходит основное действие. Мы **создадим прямоугольную фигуру** с фиксированной шириной и высотой, а затем разместим её на странице.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Почему прямоугольник? Это самая простая фигура, позволяющая продемонстрировать заливку и тени. Если позже понадобится круг или звезда, просто замените `ShapeType.RECTANGLE` на другое значение перечисления.

## Шаг 4: Задать цвет заливки фигуры

Простой белый квадрат не слишком интересен, поэтому **зададим цвет заливки** чему‑то приятному — светло‑голубому, который хорошо смотрится в отчётах.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Можно использовать любой из предопределённых членов `aw.Color` (`red`, `green`, `dark_gray` и т.д.) или передать RGB‑кортеж (`aw.Color.from_argb(255, 30, 144, 255)`). Цвет заливки — то, что пользователь видит до применения тени или границы.

## Шаг 5: Добавить тень к фигуре

Теперь визуальная отделка: **добавить тень к фигуре**. Тени придают глубину и делают прямоугольник более выразительным.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Как добавить тень**? Приведённый выше код делает именно это, но разберём, почему важны каждое свойство:

- `visible` — включает/выключает эффект.
- `color` — задаёт оттенок; тёмно‑серый имитирует естественное освещение.
- `blur` — большие значения делают края мягче.
- `offset_x` / `offset_y` — смещают тень от фигуры; меняя их, можно имитировать разные углы света.
- `transparency` — 0 — непрозрачная, 1 — полностью прозрачная; 0.2 даёт лёгкое ощущение.
- `type` — `OUTER` отбрасывает тень за пределы фигуры, `INNER` — внутренняя тень.

Если нужен драматичный «дроп‑шадоу», увеличьте `blur` до 10‑15 и поднимите `offset_x`/`offset_y` до 6‑8.

## Шаг 6: Сохранить документ как PDF

Вся эта работа бессмысленна, если нельзя **сохранить документ как PDF** и поделиться им. Aspose.Words делает это в одну строку:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Почему PDF? PDF сохраняет макет на всех платформах, что делает его идеальным для отчётов, счетов‑фактур или любого печатного материала. Метод `save` автоматически определяет расширение файла и выбирает нужный формат — просто убедитесь, что путь заканчивается на `.pdf`.

### Ожидаемый результат

Откройте полученный `ShapeWithShadow.pdf`, и вы увидите светло‑голубой прямоугольник, центрированный ближе к верхней части первой страницы, с мягкой тёмно‑серой тенью, слегка смещённой вправо и вниз. Края фигуры чёткие, тень ненавязчивая, а размер файла обычно менее 100 KB.

## Бонус: Настройка теней – ответы на «как добавить тень»

Возможно, вы задаётесь вопросом: *«Можно ли изменить направление тени, не перемещая саму фигуру?»* Конечно. Позиция тени независима от координат фигуры; просто отрегулируйте `offset_x` и `offset_y`. Положительные значения смещают тень вправо/вниз, отрицательные — влево/вверх. Для источника света сверху‑слева используйте `offset_x = -3` и `offset_y = -3`.

Ещё один часто задаваемый вопрос: *«Что если мне нужны несколько теней на одной фигуре?»* Aspose.Words поддерживает только одну тень на фигуру. Если нужны слоистые эффекты, создайте дубликат фигуры, слегка сместите его и примените к каждому свою тень. Это небольшой хак, но работает.

## Полный скрипт – готов к запуску

Ниже полностью автономный скрипт. Скопируйте его в файл `create_rectangle_with_shadow.py` и запустите командой `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Note:** Замените `YOUR_DIRECTORY` на абсолютный или относительный путь, существующий на вашем компьютере. Если папка не существует, Python выбросит `FileNotFoundError`.

## Распространённые ошибки и как их избежать

| Проблема | Почему происходит | Как исправить |
|----------|-------------------|---------------|
| Тень не появляется | `shadow.visible` оставлен по умолчанию `False` | Установите `shadow.visible = True` |
| Фигура невидима | Цвет заливки установлен в `aw.Color.transparent` или `None` | Используйте сплошной цвет, например `aw.Color.light_blue` |
| PDF пустой | Не вызван `doc.save` или сохранён с неправильным расширением | Вызовите `doc.save("output.pdf")` и проверьте путь |
| Ошибка `ImportError` | Aspose.Words не установлен или активировано неправильное окружение | Выполните `pip install aspose-words` внутри активного venv |

## Следующие шаги – исследуем другие фигуры и форматирование

Теперь, когда вы освоили **создание прямоугольной фигуры**, вы можете:

- Заменить `ShapeType.RECTANGLE` на `ShapeType.ELLIPSE` или `ShapeType.PENTAGON`, чтобы поэкспериментировать с другими геометриями.
- Добавить текст внутрь фигуры, используя `builder.move_to(rectangle.absolute_position)` и затем `builder.writeln("Hello World")`.
- Объединить несколько фигур в группу с помощью `group = aw.drawing.GroupShape(doc)` для сложных диаграмм.
- Экспортировать в другие форматы, такие как DOCX (`doc.save("output.docx")`) или HTML (`doc.save("output.html")`), чтобы увидеть, как тень переносится.

Все эти расширения базируются на тех же основных концепциях: **добавить тень к фигуре**, **задать цвет заливки**, и **сохранить документ как PDF** (или в другом формате).

---

### Предпросмотр изображения *(опционально)*

![Создание прямоугольной фигуры с тенью в Python](https://example.com/rectangle-shadow.png "Создание прямоугольной фигуры с тенью в Python")

*Скриншот показывает окончательный вывод PDF с светло‑голубым прямоугольником и лёгкой внешней тенью.*

---

## Заключение

Мы прошли каждый шаг, необходимый для **создания прямоугольной фигуры** в Python, задали пользовательскую заливку, **добавили тень к фигуре** и, наконец, **сохранили документ как PDF**. Код полностью исполняем, объяснения охватывают *почему* каждого свойства, а также мы рассмотрели типичные подводные камни и дальнейшие возможности.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы вы могли освоить дополнительные возможности API и исследовать альтернативные подходы в своих проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}