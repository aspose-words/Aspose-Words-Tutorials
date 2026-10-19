---
category: general
date: 2026-04-28
description: Перебрать предупреждения документа в файле Word, чтобы обнаружить отсутствующие
  шрифты, получить их имена и вывести детали отсутствующих шрифтов с использованием
  Aspose.Words для Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: ru
og_description: Итерировать предупреждения документа, чтобы найти отсутствующие шрифты,
  получить их имена и вывести детали отсутствующих шрифтов с полным примером на Java.
og_title: 'Итерация предупреждений документа: обнаружение отсутствующих шрифтов в
  Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Перебор предупреждений документа: обнаружение отсутствующих шрифтов в Java'
url: /ru/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Итерация предупреждений документа – обнаружение недостающих шрифтов в Java

Когда‑то вам нужно было **итерировать предупреждения документа** при открытии файла Word и вы задавались вопросом, какие шрифты отсутствуют? Вы не одиноки. Отсутствующие шрифты могут испортить внешний вид отчёта, и без возможности их обнаружить вы можете отправить документ, который совсем не похож на оригинал.  

В этом руководстве мы покажем, как **обнаружить недостающие шрифты**, загрузив документ Word, пройдя по его предупреждениям, получив имена недостающих шрифтов и, наконец, выведя информацию о недостающих шрифтах — все это с помощью Aspose.Words for Java.  

Мы пройдём от первой строки кода до ожидаемого вывода в консоль, чтобы вы могли скопировать‑вставить готовое решение в свой проект прямо сейчас. Дополнительные документы не требуются.

## Требования

- Установлен Java 8 или новее.  
- Библиотека Aspose.Words for Java (последняя версия на 2026‑04‑28).  
- Файл Word, который потенциально содержит шрифты, не установленные на вашем компьютере (например, `doc-with-missing-font.docx`).

Если всё это уже есть, отлично — вы готовы **load word document** и начать итерацию.

## Шаг 1 – Загрузка документа Word с параметрами по умолчанию

Прежде чем мы сможем **итерировать предупреждения документа**, файл необходимо загрузить в память. Aspose.Words позволяет сделать это одним вызовом конструктора. Использование `LoadOptions` по умолчанию обычно достаточно, но мы покажем явное создание для наглядности.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Почему это важно:**  
> При загрузке документа Aspose.Words сканирует файл в поисках ресурсов, которые нельзя разрешить, например, шрифтов, не установленных локально. Эти проблемы сохраняются как **warnings**, которые мы **итерируем** в следующем шаге.

## Шаг 2 – Итерация предупреждений документа для поиска проблем со шрифтами

Теперь приходит основная часть решения: мы проходим по каждому предупреждению, собранному библиотекой во время загрузки. Объекты `WarningInfo` сообщают, что пошло не так, и мы можем отфильтровать `FontSubstitutionWarning`, чтобы **detect missing fonts**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Совет:** Проверка `instanceof` гарантирует, что мы обрабатываем только предупреждения, связанные со шрифтами, игнорируя остальные, например, проблемы загрузки изображений. Это делает цикл эффективным и фокусирует вывод на шрифтах, для которых вам действительно нужно **retrieve missing font**.

### Ожидаемый вывод в консоль

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Если в документе нет недостающих шрифтов, цикл просто завершится без вывода — ничего не будет **print missing font**.

## Шаг 3 – Почему нельзя просто поймать исключение?

Вы можете задаться вопросом: «Почему бы не обернуть вызов `new Document(...)` в try‑catch и не искать исключение?» Ответ двоякий:

1. **Подробная информация:** Исключения лишь сообщают, что что‑то пошло не так. Предупреждения дают точное имя шрифта и замену, выбранную Aspose.Words.  
2. **Нефатальные проблемы:** Отсутствующие шрифты обычно не являются фатальными; документ всё равно загружается, но визуальная точность страдает. **Итерируя предупреждения документа**, вы сохраняете возможность обработать остальную часть файла.

## Шаг 4 – Расширение примера: сбор недостающих шрифтов в список

Иногда нужны недостающие шрифты для дальнейшей обработки — например, для их встраивания или оповещения пользователя через UI. Ниже небольшое изменение, которое собирает имена в `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Теперь у вас есть чистый способ **retrieve missing font** программно, который можно передать в модуль отчётности или мастер установки шрифтов.

## Шаг 5 – Практические соображения

- **Несколько замен:** Один недостающий шрифт может быть заменён разными шрифтами в разных частях документа. Список предупреждений будет содержать каждое вхождение, поэтому вы можете увидеть дублирующие записи о недостающих шрифтах.  
- **Производительность:** Загрузка очень больших документов может генерировать тысячи предупреждений. Если вас интересуют только шрифты, фильтруйте их сразу, как показано выше, чтобы цикл оставался быстрым.  
- **Кроссплатформенные шрифты:** На Linux шрифтом‑заменой по умолчанию часто является *Liberation Sans*. На Windows — *Arial*. Понимание fallback‑шрифта помогает решить, нужно ли включать пользовательские шрифты в приложение.

## Шаг 6 – Визуальная подсказка

Ниже скриншот вывода консоли (alt‑текст содержит основной ключевой запрос для SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt text:* *пример итерации предупреждений документа, показывающий имена недостающих шрифтов и детали их замен*.

## Заключение

Вы только что узнали, как **итерировать предупреждения документа** в Aspose.Words for Java, **обнаруживать недостающие шрифты**, **load word document** безопасно, **retrieve missing font** информацию и **print missing font** детали в консоль. Полный фрагмент кода работает «как есть», и вы можете адаптировать его для записи в файл, отображения диалогового окна UI или даже автоматического встраивания недостающих шрифтов.

Далее вы можете изучить, как **load word document** с пользовательскими источниками шрифтов (например, добавив папку с корпоративными шрифтами) или как встраивать недостающие шрифты непосредственно в файл, чтобы сохранить макет на разных машинах. Оба направления естественно продолжают то, что мы рассмотрели здесь.

Счастливого кодинга, и пусть ваши PDF всегда выглядят точно так, как вы задумали!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}