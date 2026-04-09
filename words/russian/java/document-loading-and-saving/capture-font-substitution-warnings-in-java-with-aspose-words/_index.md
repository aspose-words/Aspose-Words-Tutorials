---
category: general
date: 2026-01-11
description: Узнайте, как перехватывать предупреждения о замене шрифтов с помощью
  Aspose.Words for Java. Этот пошаговый учебник также охватывает LoadOptions и обратные
  вызовы предупреждений.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: ru
og_description: Захватывайте предупреждения о замене шрифтов с помощью Aspose.Words
  для Java. Следуйте этому руководству, чтобы настроить LoadOptions и обратный вызов
  предупреждений для надёжной загрузки документов.
og_title: Захват предупреждений о замене шрифтов в Java – полный учебник
tags:
- Aspose.Words
- Java
- Document Processing
title: Отслеживание предупреждений о замене шрифтов в Java с Aspose.Words – Полное
  руководство
url: /ru/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Захват предупреждений о замене шрифтов – Полный учебник по Java

Когда‑нибудь вам нужно было **захватывать предупреждения о замене шрифтов** при открытии документа Word с отсутствующими шрифтами? Это распространённая головная боль, особенно когда вы генерируете PDF или печатаете на сервере, где не установлены все типографские гарнитуры. Хорошая новость? Aspose.Words for Java делает это простым — просто настройте объект `LoadOptions` и подключите обратный вызов предупреждений. В этом руководстве вы увидите, как именно это сделать, почему это важно и чего ожидать, когда предупреждение срабатывает.

Мы также коснёмся связанных тем, таких как **Aspose.Words font substitution**, использование **Java warning callback** и лучшие практики **LoadOptions usage**. К концу вы получите готовый к запуску фрагмент кода, который будет регистрировать каждое событие отсутствующего шрифта, чтобы последующая обработка никогда не удивляла вас.

## Требования

Перед тем как начать, убедитесь, что у вас есть:

- Java 17 (или любой современный JDK), установленный и настроенный.
- Aspose.Words for Java 23.10 (или новее) в вашем classpath.
- Документ Word, который ссылается на шрифт, отсутствующий у вас локально (например, `DocWithMissingFont.docx`).
- Базовое знакомство с блоками try/catch в Java — ничего сложного.

Если что‑то из перечисленного вам незнакомо, сделайте паузу и установите библиотеку из Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Теперь, когда подготовка завершена, перейдём к коду.

## Шаг 1: Настройте обратный вызов предупреждений для **захвата предупреждений о замене шрифтов**

Первое, что вам нужно — это обратный вызов, который Aspose.Words будет вызывать каждый раз, когда встретит отсутствующий шрифт. Именно здесь мы **захватываем предупреждения о замене шрифтов**. Обратный вызов реализует интерфейс `IWarningCallback` и проверяет `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Почему это важно:** Без обратного вызова Aspose.Words тихо заменяет отсутствующий шрифт на шрифт по умолчанию, и вы никогда не узнаете, что визуальный вывод изменился. Захватывая предупреждение, вы можете вести журнал, отправлять оповещения или даже прерывать загрузку, если отсутствующий шрифт критичен.

## Шаг 2: Настройте **LoadOptions** и зарегистрируйте обратный вызов

Теперь мы создаём экземпляр `LoadOptions` и привязываем наш `FontWarningCallback`. Этот шаг необходим для **LoadOptions usage** и гарантирует, что каждая загрузка документа проходит через один и тот же фильтр предупреждений.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Подсказка:** Вы можете переиспользовать один и тот же объект `LoadOptions` для нескольких документов, что экономит несколько строк шаблонного кода и обеспечивает согласованную обработку **document loading warnings** во всём приложении.

## Шаг 3: Загрузите документ и наблюдайте вывод

С подключённым обратным вызовом просто загрузите ваш файл Word. Если документ ссылается на шрифт, который не установлен, обратный вызов сработает и выведет детали в консоль.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Ожидаемый вывод в консоль

Предположим, `DocWithMissingFont.docx` ссылается на отсутствующий шрифт *«Comic Sans MS»*, вы увидите нечто вроде:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Если документ **не содержит отсутствующих шрифтов**, в консоли будет только последняя строка, подтверждающая, что ваш обратный вызов не создал ложных срабатываний.

## Шаг 4: Обработка граничных случаев и распространённых подводных камней

### Несколько отсутствующих шрифтов

Если документ использует несколько недоступных шрифтов, обратный вызов будет выполнен один раз для каждого шрифта. Вы получите серию сообщений, каждое со своим `source` и `description`. Дополнительный код не требуется — просто убедитесь, что ваша система логирования способна обрабатывать быстрые последовательные вызовы.

### Подавление предупреждений

В редких случаях вы можете захотеть игнорировать определённые замены (например, если знаете, что конкретный запасной шрифт приемлем). Расширьте логику обратного вызова:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Потокобезопасность

`LoadOptions` в Aspose.Words по умолчанию не являются потокобезопасными. Если вы загружаете документы параллельно, создавайте отдельный экземпляр `LoadOptions` для каждого потока или синхронизируйте обратный вызов, чтобы избежать гонок.

## Шаг 5: Проверка заменённого шрифта в полученном документе

После загрузки вы, возможно, захотите убедиться, что замена действительно произошла. API позволяет перебрать все `Run`‑ы и проверить фактическое имя шрифта:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Этот фрагмент кода выводит каждый текстовый `Run` с его окончательным шрифтом. Это удобная проверка, когда вы строите автоматизированные конвейеры конвертации в PDF.

## Полный рабочий пример

Объединив всё вместе, получаем полностью готовую к запуску программу:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Сохраните её как `FontSubstitutionInfo.java`, скомпилируйте с помощью `javac` и запустите `java FontSubstitutionInfo`. Вы должны увидеть сообщения предупреждений (если они есть), а затем список `Run`‑ов и их окончательных шрифтов.

## Визуальная подсказка

![Скриншот вывода консоли, показывающий предупреждения о замене шрифтов](/images/font-substitution-warning.png "пример захвата предупреждений о замене шрифтов")

*Текст альтернативы:* **capture font substitution warnings** – вывод консоли после загрузки документа с отсутствующими шрифтами.

## Заключение

Теперь вы знаете, как **захватывать предупреждения о замене шрифтов** с помощью Aspose.Words for Java. Настроив объект `LoadOptions` и предоставив собственный `IWarningCallback`, вы получаете полную видимость всех событий отсутствующего шрифта, которые иначе могли бы тихо изменить внешний вид вашего документа. Эта техника напрямую интегрируется в обработку **Aspose.Words font substitution**, обеспечивает надёжные **document loading warnings** и даёт гибкость для логирования, оповещения или прерывания процесса в соответствии с вашими бизнес‑правилами.

### Что дальше?

- Изучите шаблоны **Java warning callback** для других типов предупреждений (например, `DEPRECATED_FEATURE`).
- Сочетайте этот подход с **PDF conversion**, чтобы гарантировать, что заменённые шрифты не нарушат макет.
- Углубитесь в **LoadOptions usage** — экспериментируйте с `Password`, `Encoding` и `ResourceLoadingCallback` для более сложных сценариев.

Не стесняйтесь дорабатывать обратный вызов, направлять предупреждения в систему логирования или даже бросать пользовательское исключение, если критически важный шрифт отсутствует. Возможности безграничны, и теперь у вас есть прочная основа для дальнейшего развития.

Счастливого кодинга, и пусть ваши документы всегда отображаются именно так, как вы ожидаете!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}