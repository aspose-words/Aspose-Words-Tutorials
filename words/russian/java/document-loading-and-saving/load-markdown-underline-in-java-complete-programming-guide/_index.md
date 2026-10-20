---
category: general
date: 2026-08-04
description: Загрузите подчеркивание markdown в Java и сохраните форматирование markdown
  при загрузке markdown в документ. Следуйте этому пошаговому руководству.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: ru
lastmod: 2026-08-04
og_description: Загружайте подчеркивание markdown в Java и сохраняйте форматирование
  markdown. Узнайте, как загрузить markdown в документ с полной поддержкой подчеркивания.
og_image_alt: Diagram showing load markdown underline process
og_title: Загрузка подчеркивания Markdown в Java – пошаговое руководство
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Загрузка подчеркивания Markdown в Java — полное руководство по программированию
url: /ru/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Загрузка подчеркивания markdown в Java – полное руководство по программированию

Если вам нужно **load markdown underline** при преобразовании файла Markdown в объект `Document`, это руководство покажет, как это сделать. Вы также узнаете, как **load markdown into document** без потери подчеркивания, гарантируя полное сохранение исходного форматирования Markdown.

В руководстве рассматривается всё, что вам необходимо знать: требуемые библиотеки, каждый шаг настройки и как проверить, что форматирование подчеркивания сохранилось после импорта. К концу вы получите переиспользуемый фрагмент кода, который можно вставить в любой проект Java.

## Предварительные требования

- Java 17 или новее, установленный (пример использует современную модульную систему)
- Последняя версия **GroupDocs.Viewer** (или совместимая библиотека, предоставляющая `LoadOptions` и `Document`)
- Файл Markdown (`sample.md`), содержащий подчеркиваемый текст, например `<u>underlined</u>` или синтаксис GitHub‑flavored `__underlined__`
- IDE, например IntelliJ IDEA или VS Code, хотя любой текстовый редактор подойдет

Эти требования гарантируют, что код будет работать без дополнительной настройки.

## Загрузка подчеркивания markdown – пошаговое руководство

Процесс состоит из трёх основных действий: создать экземпляр `LoadOptions`, включить обнаружение подчеркивания и, наконец, загрузить файл Markdown с этими параметрами. Каждый шаг объяснён ниже.

### Шаг 1: Создание `LoadOptions` для документа

`LoadOptions` позволяет настроить, как библиотека разбирает исходный файл. Создание нового экземпляра даёт чистый лист для дальнейших настроек.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

Объект `LoadOptions` является точкой входа для всех настроек, связанных с импортом. Вы будете использовать его в следующем шаге, чтобы включить обнаружение подчеркивания.

### Шаг 2: Включение обнаружения форматирования подчеркивания при загрузке

По умолчанию просмотрщик может игнорировать теги подчеркивания, поскольку они реже встречаются в Markdown. Включение этого флага сообщает парсеру сохранять диапазоны подчеркивания.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Установка `setImportUnderlineFormatting(true)` гарантирует, что любой HTML‑тег `<u>` или синтаксис подчеркивания GitHub‑flavored будет преобразован в модель `Document` как стиль подчеркивания. Это ключевое действие, позволяющее **load markdown underline** работать как ожидается.

### Шаг 3: Загрузка файла Markdown с использованием настроенных параметров

Теперь можно загрузить файл. Передайте объект `loadOptions` в конструктор `Document`, чтобы парсер учитывал флаг подчеркивания.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

После завершения конструктора `markdownDoc` содержит полное представление Markdown‑источника в памяти, включая диапазоны подчеркивания.

### Шаг 4: Проверка сохранения форматирования подчеркивания

Быстрая проверка помогает убедиться, что **preserve markdown formatting** сработало. Следующий фрагмент выводит текст каждого абзаца и отмечает подчеркиваемые фрагменты тильдой (`~`) для наглядности.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Ожидаемый вывод** (при условии, что `sample.md` содержит `This is __underlined__ text`):

```
This is ~underlined~ text
```

Тильды указывают, что стиль подчеркивания выжил после импорта, подтверждая, что операция **load markdown into document** сохранила оригинальное форматирование.

## Распространённые ошибки и как их избежать

| Симптом | Причина | Решение |
|---|---|---|
| Подчеркивание исчезает после загрузки | `setImportUnderlineFormatting` оставлен со значением по умолчанию `false` | Убедитесь, что вызываете `loadOptions.setImportUnderlineFormatting(true)` перед созданием `Document`. |
| Подчеркивание применяется только к части текста | Смешанный синтаксис Markdown (например, HTML `<u>` вместе с `__underline__`) | Библиотека поддерживает оба варианта; проверьте, что исходный файл использует единый маркер подчеркивания. |
| Не удаётся загрузить документ | Неправильный путь к файлу или отсутствующие зависимости библиотеки | Используйте абсолютный путь или разместите `sample.md` относительно рабочей директории; включите JAR‑файлы viewer в classpath. |

**Подсказка:** Если вам также нужно сохранять жирный или курсивный стиль, включите их с помощью `setImportBoldFormatting(true)` и `setImportItalicFormatting(true)` соответственно. Комбинация этих флагов обеспечивает полностью точный импорт большинства распространённых стилей Markdown.

## Полный исполняемый пример

Ниже представлена автономная Java‑программа, объединяющая всё вместе. Скопируйте код в файл с именем `LoadMarkdownUnderlineDemo.java`, скорректируйте путь к файлу и запустите его командой `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Запуск программы выводит содержимое документа с маркерами подчеркивания, подтверждая, что функция **load markdown underline** работает и что вы можете **preserve markdown formatting** на протяжении всего процесса импорта.

## Заключение

Теперь вы знаете, как **load markdown underline** в Java, как **load markdown into document** с сохранением оригинального стиля, и как проверить, что форматирование подчеркивания осталось неизменным. Этот подход работает с последними версиями GroupDocs.Viewer и может быть расширен для поддержки дополнительных возможностей Markdown, таких как жирный, курсив и таблицы.

Далее изучайте связанные темы, такие как **preserve markdown formatting for tables**, **render Markdown to PDF**, или **custom styling of imported Markdown elements**. Настройте флаги `LoadOptions` в соответствии с точными требованиями форматирования вашего приложения, и вы получите тонкий контроль над каждым шагом импорта. Приятного кодинга!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, основанные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в своих проектах.

- [Master Markdown Load Options with Aspose.Words for Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Master Markdown Load Options Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}