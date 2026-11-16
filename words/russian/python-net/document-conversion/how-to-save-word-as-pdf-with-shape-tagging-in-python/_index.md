---
category: general
date: 2026-11-15
description: Сохраните документ Word в PDF в Python с помощью Aspose.Words, узнайте,
  как экспортировать фигуры и помечать плавающие фигуры как встроенные для точного
  преобразования docx в PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- how to convert docx
- how to tag shapes
language: ru
lastmod: 2026-11-15
og_description: Сохраните Word в PDF с помощью Python и Aspose.Words. В этом руководстве
  показано, как экспортировать фигуры, помечать плавающие фигуры как встроенные и
  надёжно конвертировать docx в PDF.
og_image_alt: Screenshot of Python code that saves a Word document as PDF with shape
  tagging
og_title: Сохранить Word в PDF с тегированием фигур в Python — полное руководство
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Save Word as PDF in Python using Aspose.Words, learn how to export
    shapes and tag floating shapes as inline for accurate docx to PDF conversion.
  headline: How to save Word as PDF with shape tagging in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
title: Как сохранить Word в PDF с тегированием фигур в Python
url: /ru/python/document-conversion/how-to-save-word-as-pdf-with-shape-tagging-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сохранить Word как PDF с тегированием фигур в Python

Если вам нужно **сохранить Word как PDF** и сохранить каждую рисунок ровно на своём месте, это руководство покажет надёжный способ сделать это с помощью Aspose.Words for Python. Вы также узнаете **как экспортировать фигуры** и **как тегировать фигуры**, чтобы плавающие объекты стали встроенными элементами во время конвертации.

В этом учебнике мы рассмотрим:

* Конвертацию файла DOCX в PDF (`convert docx to pdf`)  
* Экспорт плавающих фигур как встроенных тегов (`how to export shapes`)  
* Тегирование фигур во время операции сохранения PDF (`how to tag shapes`)  

Никакие внешние инструменты не требуются — только несколько строк кода на Python.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* Python 3.8+ установлен  
* Действующая лицензия Aspose.Words for Python (или бесплатная пробная версия)  
* Пакет `aspose-words`, установленный (`pip install aspose-words`)  
* Файл DOCX (`input.docx`), содержащий плавающие фигуры (изображения, текстовые блоки и т.д.)

## Шаг 1: Установить и импортировать Aspose.Words

Сначала добавьте библиотеку в своё окружение и импортируйте её в скрипте.

```python
# Install the package (run once):
# pip install aspose-words

import aspose.words as aw
```

*Почему?* Модуль `aspose.words` предоставляет класс `Document` и `PdfSaveOptions`, необходимые для управления обработкой фигур.

## Шаг 2: Загрузить документ Word

Используйте конструктор `Document`, чтобы прочитать исходный файл.

```python
# Load the Word document you want to convert
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

Если файл не существует, Aspose.Words выбрасывает `FileNotFoundError`. Оберните вызов в блок `try/except` для production‑кода.

## Шаг 3: Настроить параметры сохранения PDF — экспорт и тегирование фигур

Ключ к чистой конвертации — объект `PdfSaveOptions`. Установка `export_floating_shapes_as_inline_tag` в `True` сообщает движку рассматривать плавающие рисунки как встроенные элементы, что устраняет смещения макета в получаемом PDF.

```python
# Create PDF save options and enable inline tagging for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes
```

*Почему?* Когда `export_floating_shapes_as_inline_tag` равно `False` (значение по умолчанию), плавающие фигуры сохраняют свои исходные метаданные позиции, что может привести к их неправильному размещению в PDF. Включение встроенного тега заставляет Aspose.Words вставлять небольшой XML‑тег, который рендерер PDF интерпретирует как встроенный объект, сохраняя визуальную точность.

## Шаг 4: Сохранить документ как PDF

Теперь запишите PDF‑файл, используя настроенные параметры.

```python
# Save the document as a PDF, applying the shape‑tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)

print(f"PDF saved to {output_path}")
```

После выполнения `output.pdf` будет содержать оригинальное расположение Word с правильно отрендеренными плавающими фигурами как встроенными элементами.

## Шаг 5: Проверить конвертацию (по желанию)

Можно программно проверить, что PDF был создан и содержит хотя бы одну страницу:

```python
import os
from aspose.pdf import Document as PdfDocument

if os.path.exists(output_path):
    pdf_doc = PdfDocument(output_path)
    print(f"PDF has {pdf_doc.pages.count} page(s).")
else:
    raise FileNotFoundError("PDF was not created.")
```

*Подсказка:* Используйте PDF‑просмотрщик, чтобы убедиться, что изображения, текстовые блоки и выноски находятся точно там, где они были в файле DOCX.

## Распространённые варианты и граничные случаи

| Ситуация | Что изменить |
|-----------|----------------|
| **Вам нужно оставить плавающие фигуры плавающими** | Установите `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **Конвертировать множество файлов пакетно** | Пройдитесь по списку путей к файлам и переиспользуйте один экземпляр `PdfSaveOptions`. |
| **Вы хотите задать пароль** | Используйте `pdf_opts.encrypt_options.password = "your‑password"` перед вызовом `save`. |
| **Большие документы вызывают нагрузку на память** | Включите `pdf_opts.memory_optimization = True`, чтобы снизить потребление ОЗУ. |

## Профессиональный совет: обработка отсутствующих шрифтов

Если исходный DOCX использует шрифты, не установленные на сервере, рендеринг PDF может переключиться на шрифт по умолчанию. Зарегистрируйте недостающие шрифты с помощью `FontSettings`:

```python
font_settings = aw.FontSettings()
font_settings.set_fonts_folder("YOUR_DIRECTORY/fonts", recursive=True)
doc.font_settings = font_settings
```

Это гарантирует, что PDF будет выглядеть идентично оригинальному файлу Word.

## Полный рабочий пример

```python
import aspose.words as aw
import os

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Saves a Word document as PDF while tagging floating shapes as inline.
    """
    # Load the DOCX
    doc = aw.Document(input_path)

    # Optional: register custom fonts
    # font_settings = aw.FontSettings()
    # font_settings.set_fonts_folder("fonts", recursive=True)
    # doc.font_settings = font_settings

    # Configure PDF options to export shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes

    # Save as PDF
    doc.save(output_path, pdf_opts)
    print(f"PDF saved to {output_path}")

if __name__ == "__main__":
    INPUT = "YOUR_DIRECTORY/input.docx"
    OUTPUT = "YOUR_DIRECTORY/output.pdf"

    if not os.path.isfile(INPUT):
        raise FileNotFoundError(f"Input file not found: {INPUT}")

    convert_docx_to_pdf(INPUT, OUTPUT)

    # Verify creation
    if os.path.isfile(OUTPUT):
        from aspose.pdf import Document as PdfDocument
        pdf = PdfDocument(OUTPUT)
        print(f"Conversion successful – PDF has {pdf.pages.count} page(s).")
    else:
        raise RuntimeError("PDF conversion failed.")
```

Запуск скрипта создаст `output.pdf` со всеми плавающими фигурами, корректно тегированными, обеспечивая чистый результат **save word as pdf**.

## Заключение

Теперь вы знаете, как **сохранить Word как PDF** в Python, контролируя обработку фигур. Настраивая `PdfSaveOptions.export_floating_shapes_as_inline_tag`, вы надёжно **конвертируете docx в pdf**, **экспортируете фигуры** как встроенные теги и отвечаете на вопрос **how to tag shapes** во время конвертации.  

Дальше вы можете исследовать:

* Добавление водяных знаков (`pdf_opts.add_watermark`) — естественное расширение настройки PDF.  
* Конвертацию других форматов (HTML, EPUB) с тем же шаблоном `save`.  
* Автоматизацию пакетных конвертаций для больших репозиториев документов.

Попробуйте скрипт, поэкспериментируйте с дополнительными настройками и интегрируйте его в ваш конвейер обработки документов уже сегодня. Приятного кодинга!


## Что изучать дальше?


Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Save Word as PDF – Convert Shapes to Inline with Aspose.Words](/words/english/python-net/document-conversion/save-word-as-pdf-convert-shapes-to-inline-with-aspose-words/)
- [How to save Word as PDF with Aspose.Words for Python](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-with-aspose-words-for-python/)
- [How to convert DOCX to PDF in Python using Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}