---
category: general
date: 2026-06-20
description: Как установить обратный вызов в Aspose.Words Java для обнаружения отсутствующих
  шрифтов и настройки загрузки документа. Узнайте пошагово, как обрабатывать предупреждения
  о замене шрифтов.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: ru
og_description: Как установить обратный вызов в Aspose.Words Java для обнаружения
  отсутствующих шрифтов, обработки замен и настройки загрузки документа. Полное руководство
  с кодом.
og_title: как установить обратный вызов – обнаружение отсутствующих шрифтов в Aspose.Words
  Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Как установить обратный вызов в Aspose.Words Java – обнаружение и обработка
  отсутствующих шрифтов
url: /ru/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# как установить callback в Aspose.Words Java – обнаружение и обработка отсутствующих шрифтов

Задумывались ли вы **как установить callback** в Aspose.Words Java, чтобы обнаружить отсутствующие шрифты до того, как они испортят ваш PDF или DOCX? Вы не одиноки. Предупреждения об отсутствующих шрифтах могут тихо испортить макет, а без правильного callback‑а вы можете никогда не заметить проблему, пока конечный документ не будет выглядеть некорректно.  

В этом руководстве мы пройдемся по полностью готовому к запуску примеру, который **обнаруживает отсутствующие шрифты**, **корректно обрабатывает отсутствующие шрифты** и показывает, как **настроить загрузку документа** с помощью callback‑а предупреждений. К концу вы получите автономный Java‑класс, который можно добавить в любой проект — без необходимости искать дополнительную документацию.

## Что вам понадобится

- Java 8 или новее (код также работает с Java 11+)  
- Библиотека Aspose.Words for Java (версия 23.9 или новее)  
- Файл DOCX, который ссылается на шрифт, которого у вас нет (например, фирменный корпоративный шрифт)  

Если вы ещё не добавили Aspose.Words в ваш Maven‑проект, просто включите:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Вот и всё — никаких дополнительных плагинов, никаких нативных зависимостей.

---

## Шаг 1: Понять механизм WarningCallback

**Callback предупреждений** — это способ Aspose.Words сообщать вам о неожиданностях, происходящих при загрузке или сохранении документа. Реализуя `IWarningCallback`, вы получаете полный контроль над тем, что будет записано в лог, проигнорировано или даже превращено в исключение.

> **Почему это важно:**  
> Когда шрифт отсутствует, Aspose подставляет резервный шрифт. Визуальный результат может сильно отличаться, особенно в PDF с сильным брендингом. Перехватывая `WarningType.FONT_SUBSTITUTION`, вы можете записать точное название шрифта, решить, прервать ли процесс, или программно подменить шрифт своим собственным.

---

## Шаг 2: Создать экземпляр LoadOptions

`LoadOptions` — точка входа для настройки загрузки документа. Вы привяжете callback к этому объекту перед тем, как действительно загрузить файл.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

На данном этапе `loadOptions` — просто пустой контейнер, ничего не происходит. Настоящая магия начинается, когда мы подключаем callback.

---

## Шаг 3: Реализовать и присоединить Callback

Ниже представлен компактный анонимный класс, реализующий `IWarningCallback`. Он выводит дружелюбную строку в консоль каждый раз, когда происходит подстановка шрифта.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Совет:** Если вы хотите **обрабатывать отсутствующие шрифты**, предоставляя замену, вы также можете задать `FontSettings` в `LoadOptions` и сопоставить отсутствующие шрифты известным резервным.

---

## Шаг 4: Загрузить документ с вашими пользовательскими настройками

Теперь, когда callback подключён, загрузите документ. Если файл ссылается на шрифт, которого у вас нет, вы увидите вывод предупреждения.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

При запуске программы в консоли может появиться:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Эта строка доказывает, что вы успешно **обнаружили отсутствующие шрифты** и теперь можете **обрабатывать отсутствующие шрифты** как считаете нужным.

---

## Шаг 5: Необязательно – заменить отсутствующие шрифты известным шрифтом

Если вы хотите автоматически заменять любой отсутствующий шрифт, скажем, на `Times New Roman`, добавьте объект `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Теперь документ загружается, и любое упоминание `MyCustomFont` бесшумно заменяется на `Times New Roman`. Консоль всё равно будет сообщать, что было заменено, держась в курсе происходящего.

---

## Полный рабочий пример

Ниже приведён один Java‑класс, включающий все шаги выше. Скопируйте‑вставьте его в вашу IDE, скорректируйте `docPath` и запустите.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый вывод**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Теперь у вас есть воспроизводимый способ **обнаружить отсутствующие шрифты**, **обработать отсутствующие шрифты** и **настроить загрузку документа** — всё благодаря правильному использованию **как установить callback**.

---

## Часто задаваемые вопросы

### Что делать, если я хочу, чтобы программа прекращала загрузку при отсутствии шрифта?

Бросьте исключение внутри метода `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Блок `catch` внизу перехватит его, и вы сможете решить, как логировать или оповещать пользователя.

### Работает ли это для PDF, генерируемых из DOCX?

Абсолютно. Callback срабатывает во время **фазы загрузки**, которая одинаковая для всех форматов вывода (`save` в PDF, DOCX, HTML и т.д.). Пока вы загружаете исходный документ с теми же `LoadOptions`, вы поймаете отсутствующие шрифты до того, как они повлияют на финальный PDF.

### Могу ли я перехватывать другие типы предупреждений (например, конверсия изображений)?

Да — `WarningInfo.getWarningType()` можно сравнивать с другими перечислениями, такими как `WarningType.IMAGE_CONVERSION`. Просто добавьте дополнительные ветки `if` в callback.

### Есть ли влияние на производительность?

Незначительное. Callback выполняется синхронно во время загрузки, а дополнительные проверки лёгкие. Если вы загружаете тысячи документов, можете отключить предупреждения в продакшене, задав `loadOptions.setWarningCallback(null);`.

---

## Визуальный обзор

![пример установки callback в Aspose.Words Java](https://example.com/images/callback-diagram.png "пример установки callback")

*Диаграмма иллюстрирует поток: `LoadOptions` → `IWarningCallback` → загрузка документа → обработка подстановки шрифта.*

---

## Итоги

Мы рассмотрели **как установить callback** в Aspose.Words Java, продемонстрировали **обнаружение отсутствующих шрифтов**, показали практические способы **обработки отсутствующих шрифтов** и объяснили, как **настроить загрузку документа** с помощью `LoadOptions`.  

Обладая этими знаниями, вы теперь можете защитить свои конвейеры документов от тихих замен шрифтов, сохранить фирменный стиль и предоставить пользователям чёткую обратную связь, когда что‑то идёт не так.

### Что дальше?

- Изучите **таблицы подстановки шрифтов** для массового сопоставления многих отсутствующих шрифтов.  
- Скомбинируйте этот callback с **валидацией документа**, чтобы обеспечить соблюдение стайл‑гайдов.  
- Попробуйте **пользовательские callback‑и предупреждений**, которые пишут в файл журнала или систему мониторинга вместо `System.out`.  

Экспериментируйте, делитесь своими решениями и расскажите, как вы адаптировали callback под свои проекты. Приятного кодинга!

---


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом гайде. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}