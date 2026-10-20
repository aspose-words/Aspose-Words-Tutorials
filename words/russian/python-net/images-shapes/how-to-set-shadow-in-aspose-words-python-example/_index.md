---
category: general
date: 2026-08-01
description: Как установить тень для формы Word с помощью Aspose.Words для Python.
  Узнайте, как быстро изменить непрозрачность, настроить размытие и изменить расстояние
  тени.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: ru
lastmod: 2026-08-01
og_description: Как установить тень для фигуры с помощью Aspose.Words для Python.
  Следуйте этому пошаговому руководству, чтобы изменить непрозрачность, настроить
  размытие и изменить расстояние тени.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Как задать тень в Aspose.Words – Быстрое руководство по Python
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Как задать тень в Aspose.Words – пример на Python
url: /ru/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить тень в Aspose.Words – пример на Python

Когда‑нибудь задумывались **как установить тень** на объект Word, не открывая документ вручную? Вы не одиноки — многие разработчики сталкиваются с этой проблемой при автоматизации отчетов или создании шаблонов, соответствующих фирменному стилю. Хорошая новость? С Aspose.Words для Python вы можете настроить тень объекта, её непрозрачность, размытие и расстояние всего в несколько строк кода.

В этом руководстве мы пройдем полный, исполняемый пример, который демонстрирует **как установить тень**, **как изменить непрозрачность**, **как настроить размытие**, а также **как изменить расстояние тени**. К концу вы получите уверенное понимание **как использовать Aspose.Words** для программного стилизования объектов.

---

![How to set shadow on a shape using Aspose.Words](image-placeholder.png){alt="Как установить тень на объект с помощью Aspose.Words"}

## Необходимые условия

Перед тем как начать, убедитесь, что у вас есть:

| Требование | Причина |
|-------------|--------|
| Python 3.8+ | Современный синтаксис, подсказки типов |
| `aspose-words` package (pip install aspose-words) | Основная библиотека для работы с Word |
| Пример `input.docx` с как минимум одной фигурой | Фигура, к которой мы добавим тень |
| Разрешение на запись в папку, где будет сохранён `output.docx` | Для сохранения изменений |

Никаких дополнительных DLL или COM‑interop — Aspose.Words полностью на Python, поэтому вы можете запускать его в Windows, macOS или Linux.

---

## Как установить тень на объект с помощью Aspose.Words

Ниже представлен **полный** скрипт. Он загружает документ, находит первую фигуру (рекурсивно), настраивает тень и сохраняет результат. Каждая строка прокомментирована, чтобы вы понимали **почему** она нужна, а не только **что** она делает.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Почему это работает

* **`doc.get_child(..., True)`** – Флаг `True` указывает Aspose.Words выполнять поиск **рекурсивно**, поэтому находятся даже фигуры в заголовках, нижних колонтитулах или сгруппированных объектах. Это важно, когда вы точно не знаете, где находится фигура.
* **`shadow_format`** – Это свойство объединяет все настройки, связанные с тенью. Устанавливая `distance`, `blur` и `opacity`, вы контролируете визуальную глубину фигуры. Изменение любого из этих значений демонстрирует **как изменить непрозрачность**, **как настроить размытие** и **изменить расстояние тени** в одном согласованном вызове.
* **Saving** – `doc.save` записывает новый файл `.docx`. Оригинал остаётся нетронутым, что является безопасным подходом для пакетной обработки.

---

## Как изменить непрозрачность тени фигуры

Непрозрачность определяет, насколько прозрачной выглядит тень. Диапазон от 0.0 (полностью невидимая) до 1.0 (полностью сплошная). В приведённом выше коде вы можете просто изменить аргумент `opacity`:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Совет:** При последующей генерации PDF более высокая непрозрачность часто приводит к более глубокой, лучше печатаемой тени. Экспериментируйте со значениями от 0.4 до 0.9, чтобы найти оптимальный вариант для ваших бренд‑руководств.

---

## Как настроить размытие для более мягкого вида

Размытие — это радиус гауссового размытия, применяемого к краям тени. Большее значение даёт более «перышковый» эффект:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Если нужен чёткий, «падающий» вид тени (в стиле Microsoft PowerPoint), установите `blur` в небольшое значение, например `1.0`.

---

## Измените расстояние тени для создания глубины

Расстояние измеряется в пунктах (1 pt = 1/72 дюйма). Чем дальше отодвинуть тень, тем выше будет выглядеть фигура:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Сочетайте большее `distance` с умеренным `blur` для драматического «поднятого» эффекта.

---

## Объединяем всё вместе — мини‑проект

Представьте, что вы создаёте автоматический генератор отчетов, который вставляет логотип компании в текстовое поле. Вы хотите, чтобы каждый логотип имел лёгкую тень, соответствующую корпоративному стилю. С помощью функции `apply_shadow` вы можете:

1. **Создать документ** (или загрузить шаблон).
2. **Вставить форму логотипа** (через `DocumentBuilder.insert_image` или `Shape`).
3. **Вызвать `apply_shadow`** с параметрами тени вашего бренда.
4. **Экспортировать** в DOCX, PDF или HTML одной строкой кода.

Поскольку функция принимает параметры, вы можете хранить настройки тени в JSON‑файле и применять их к десяткам документов — без ручной настройки.

---

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Что делать, если в документе несколько фигур?** | Пример ориентируется на *первую* фигуру. Чтобы затронуть все фигуры, выполните цикл с `doc.get_child_nodes(aw.NodeType.SHAPE, True)` и примените те же настройки `shadow_format` к каждому узлу. |
| **Можно ли задать другой цвет тени?** | Конечно. Используйте `shape.shadow_format.color = aw.Color(255, 0, 0)` для красной тени или любой другой `aw.Color` по вашему выбору. |
| **Сохраняются ли эти настройки при конвертации в PDF?** | Да. Aspose.Words сохраняет свойства тени при рендеринге в PDF, хотя очень большие значения размытия могут быть приближёнными. |
| **Есть ли влияние на производительность при работе с большими документами?** | API тени работает только с объектами фигур, поэтому даже 500‑страничный отчёт обрабатывается за миллисекунды. Узким местом обычно является ввод‑вывод, а не настройка тени. |
| **Можно ли позже удалить тень?** | Установите `shape.shadow_format.is_visible = False` или просто сбросьте свойства к значениям по умолчанию. |

---

## Полный рабочий пример — резюме

Вот весь скрипт ещё раз, без комментариев для быстрого копирования:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Запустите скрипт, откройте `output.docx`, и вы увидите, что у фигуры появилась аккуратная тень, соответствующая заданным параметрам.

---

## Заключение

Мы рассмотрели **

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Учебник по тени фигур Aspose.Words — Добавление тени к фигуре Word на C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Как реализовать комментарии и ответы в документах Word с помощью Aspose.Words для Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Как управлять переменными документа с помощью Aspose.Words в Python: Полное руководство](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}