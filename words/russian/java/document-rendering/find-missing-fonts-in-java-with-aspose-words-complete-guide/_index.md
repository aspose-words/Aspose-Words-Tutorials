---
category: general
date: 2026-06-08
description: Быстро находите недостающие шрифты с помощью Aspose.Words для Java. Узнайте,
  как диагностировать предупреждения о замене шрифтов и исправлять проблемы с отсутствующими
  шрифтами за несколько простых шагов.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: ru
og_description: Найдите отсутствующие шрифты в ваших DOCX‑файлах с помощью Aspose.Words
  для Java. В этом руководстве показано, как включить диагностику, считывать события
  FontSubstitutionWarning и выводить оригинальные и заменённые названия шрифтов.
og_title: Поиск недостающих шрифтов в Java – пошаговое руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: Поиск недостающих шрифтов в Java с Aspose.Words – Полное руководство
url: /ru/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Поиск недостающих шрифтов в Java с Aspose.Words – Полное руководство

Когда‑то задумывались, как **найти недостающие шрифты** в документе Word до того, как они испортят макет? Вы не одиноки — разработчики постоянно сталкиваются с тихими заменами шрифтов, которые портят PDF‑файлы или печатные отчёты. Хорошая новость в том, что Aspose.Words for Java предоставляет встроенный API диагностики, который делает поиск таких шрифтов простым.

В этом руководстве мы пройдём реальный пример: загрузим DOCX, включим сбор предупреждений и выведем каждое *FontSubstitutionWarning*, которое нужно знать. К концу вы сможете записать оригинальное имя шрифта, замену, выбранную Aspose, и решить, стоит ли встраивать недостающий шрифт вручную.

## Что понадобится

Прежде чем начать, убедитесь, что у вас есть:

* **Aspose.Words for Java** (последняя версия 23.x) в вашем classpath.  
* Среда разработки Java 8+ (любая IDE, Maven/Gradle подойдёт).  
* Пример DOCX, в котором намеренно указана шрифт, не установленный на вашей машине — назовём его `MissingFonts.docx`.

Это всё. Никаких дополнительных библиотек, сложных настроек, только чистый Java и Aspose.

![Схема поиска недостающих шрифтов](https://example.com/find-missing-fonts.png "Схема поиска недостающих шрифтов")

*На изображении выше показан поток: загрузка → диагностика → предупреждения → вывод.*

## Шаг 1: Подготовьте LoadOptions и укажите формат документа

Первое, что мы делаем, — создаём объект **LoadOptions**. Он сообщает Aspose.Words, как интерпретировать входной файл, и, что важно, включает сбор *document warnings*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*Зачем использовать LoadOptions?*  
Без него Aspose всё равно загрузит файл, но может пропустить часть диагностических данных. Явно задав формат, вы гарантируете стабильную генерацию предупреждений, особенно при работе со старыми или повреждёнными файлами.

## Шаг 2: Загрузите документ с включённой диагностикой

Теперь действительно читаем файл. Конструктор `Document` автоматически начинает собирать предупреждения, которые позже будут включать любые **FontSubstitutionWarning**.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **Совет профессионала:** Если вы используете Maven, добавьте зависимость Aspose.Words в ваш `pom.xml`. Так JAR будет подтянут автоматически, и вам не придётся вручную управлять classpath.

## Шаг 3: Просмотрите предупреждения документа на предмет замен шрифтов

Aspose сохраняет каждое предупреждение в коллекции, по которой можно итерировать. Мы фильтруем объекты `FontSubstitutionWarning`, потому что они именно указывают на недостающий шрифт, который был заменён.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*Что происходит здесь?*  
`doc.getWarnings()` возвращает `List<WarningInfo>`. Проверяя `instanceof FontSubstitutionWarning`, мы изолируем только записи, связанные со шрифтами, игнорируя другие предупреждения, такие как «unsupported feature» или «image conversion».

## Шаг 4: Выведите оригинальные и заменённые имена шрифтов

Наконец, выводим как недостающие (оригинальные) имена шрифтов, так и шрифт, выбранный Aspose в качестве замены. Такой вывод идеален для логирования или передачи в проверку конвейера сборки.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### Ожидаемый вывод в консоль

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

Если ничего не напечатано, значит **не обнаружено недостающих шрифтов** — ваш документ уже содержит шрифты, присутствующие на машине, где выполняется код.

## Шаг 5: Обработка граничных случаев и типичных подводных камней

### Недостающий шрифт, но без предупреждения

Иногда шрифт встроен в DOCX, но встраивание повреждено. Aspose всё равно выдаст `FontSubstitutionWarning`, потому что не может отобразить текст. Чтобы различить ситуации, проверьте `fsWarning.isFontEmbedded()` (доступно в более новых версиях).

### Несколько замен одного и того же шрифта

Один недостающий шрифт может быть заменён несколько раз при разных запусках, если меняется иерархия fallback (например, сначала пытается Arial, затем переходит к Helvetica). Храните `Set<String>` из `getOriginalFontName()` для удаления дубликатов, если нужен только список уникальных недостающих шрифтов.

### Соображения производительности

Загрузка очень больших DOCX (сотни МБ) с включённым сбором предупреждений может добавить накладные расходы. Если нужны только диагностики шрифтов, установите `loadOptions.setValidateStructure(false)`, чтобы пропустить глубокую валидацию. Это ускорит процесс без влияния на генерацию предупреждений.

## Бонус: Автоматическое встраивание шрифтов

Как только вы узнаете, какие шрифты отсутствуют, их можно программно встроить:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

Встраивание гарантирует, что итоговый PDF или сохранённый DOCX будет отображаться одинаково на любой машине — больше никаких неожиданностей с заменами.

## Итоги: Как найти недостающие шрифты с помощью Aspose.Words

- **Создайте LoadOptions** и задайте формат загрузки.  
- **Загрузите документ**, пока Aspose собирает предупреждения.  
- **Итерируйте `doc.getWarnings()`**, фильтруя `FontSubstitutionWarning`.  
- **Выведите** `getOriginalFontName()` и `getSubstitutedFontName()`, чтобы увидеть, какие шрифты отсутствуют.  
- **Опционально:** удаляйте дубликаты, проверяйте статус встраивания или автоматически встраивайте недостающие шрифты.

Это полное решение для **поиска недостающих шрифтов** в Java‑приложении с использованием Aspose.Words. Теперь у вас есть надёжный способ раннего обнаружения проблем со шрифтами, поддержания консистентного вида PDF и избежания неприятных сюрпризов в продакшене.

## Что изучать дальше?

* **Автоматическое встраивание шрифтов** (см. бонусный фрагмент).  
* **Генерация PDF** после исправления шрифтов для проверки визуального результата.  
* **Использование FontSettings** Aspose.Words для определения пользовательской цепочки fallback.  
* **Запуск той же диагностики** для файлов DOC, RTF или HTML — просто измените `LoadFormat` соответственно.

Экспериментируйте с разными типами документов и семействами шрифтов. Если возникнут сложности, оставьте комментарий ниже или обратитесь к официальной Java‑документации API Aspose для более глубокой кастомизации.

Счастливого кодинга, и пусть ваши документы всегда отображаются теми шрифтами, которые вы задумали!

## Что изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Использование шрифтов в Aspose.Words для Java](/words/english/java/using-document-elements/using-fonts/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}