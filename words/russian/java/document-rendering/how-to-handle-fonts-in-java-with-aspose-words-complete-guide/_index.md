---
category: general
date: 2026-02-10
description: Как работать со шрифтами в Java с помощью Aspose.Words. Узнайте о предупреждениях
  замены шрифтов, обратных вызовах LoadOptions и обработке отсутствующих шрифтов за
  несколько шагов.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: ru
og_description: Как работать со шрифтами в Java с помощью Aspose.Words. Это руководство
  демонстрирует пошаговое управление заменой шрифтов, обработку предупреждающих обратных
  вызовов и управление отсутствующими шрифтами.
og_title: Как работать со шрифтами в Java – Полный учебник по Aspose.Words
tags:
- Java
- Aspose.Words
- Document Processing
title: Как работать со шрифтами в Java с Aspose.Words – Полное руководство
url: /ru/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

Common Questions & Edge Cases", etc.

Also translate the subheadings.

Also translate the bullet points under Pro Tips.

Also translate conclusion.

Make sure to keep markdown formatting.

Now produce final output.

Let's start.

We need to keep the shortcodes exactly as they appear.

Let's produce translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как работать со шрифтами в Java – Полное руководство

Когда в документе Word указана гарнитура, которой нет на вашем сервере, вы когда‑нибудь задумывались **как работать со шрифтами**? Это ситуация, в которой запутывается множество разработчиков, особенно при автоматизации генерации или конвертации документов с помощью Aspose.Words. Хорошая новость: вы можете отлавливать каждое событие подстановки шрифта и реагировать на него — без догадок.

В этом руководстве мы пройдем реальный пример, показывающий **как работать со шрифтами** с использованием Aspose.Words for Java. Мы подключим обратный вызов предупреждений, отфильтруем только предупреждения о подстановке шрифтов и выведем дружелюбное сообщение для каждого отсутствующего шрифта. К концу вы поймёте, почему это важно, как реализовать это чисто и чего ожидать при выполнении кода.

> **Что вы получите:** готовый к запуску Java‑класс, объяснение каждой строки, советы для продакшн‑использования и быстрый способ проверить вывод.

---

## Требования

Прежде чем начать, убедитесь, что у вас есть:

- **Java 8** (или новее), установленная на вашем компьютере.  
- **Aspose.Words for Java** JAR (последняя версия на февраль 2026, например `aspose-words-23.11.jar`).  
- Пример документа (`MissingFont.docx`), в котором используется шрифт, которого у вас нет.  
- Среда разработки (IntelliJ IDEA, Eclipse или даже простой текстовый редактор + командная строка).

Никаких дополнительных фреймворков не требуется — только чистый Java и JAR Aspose.Words.

---

![Диаграмма, показывающая как работать со шрифтами в Java с Aspose.Words](https://example.com/handle-fonts-diagram.png "диаграмма как работать со шрифтами")

*Текст alt: диаграмма как работать со шрифтами*

---

## Шаг 1 – Настройка обратного вызова предупреждений (ядро **как работать со шрифтами**)

Когда Aspose.Words загружает документ, он генерирует серию объектов `WarningInfo` для всего, что не идеально. Подключив `IWarningCallback`, вы можете перехватывать эти предупреждения в реальном времени.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**Почему это важно:**  
Если пропустить обратный вызов, Aspose.Words молча заменит отсутствующие шрифты на шрифт по умолчанию, и вы никогда не узнаете, какие шрифты отсутствовали. Обрабатывая предупреждение, вы получаете видимость и можете решить, встраивать ли запасной шрифт, записать проблему в лог или даже прервать операцию.

---

## Шаг 2 – Загрузка документа с использованием настроенных `LoadOptions`

Теперь, когда обратный вызов готов, просто загружаем документ. Экземпляр `LoadOptions`, созданный выше, передаётся напрямую конструктору `Document`.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**Чего ожидать:**  
Когда `MissingFont.docx` ссылается, скажем, на *Comic Sans MS*, а на сервере установлен только *Arial*, обратный вызов выводит что‑то вроде:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

Если документ загружается без отсутствующих шрифтов, ничего не выводится — именно то, что нужно при **как работать со шрифтами** без лишних сообщений.

---

## Шаг 3 – (Опционально) Проверка таблицы шрифтов документа

Иногда необходимо проверить, какие шрифты документ действительно использует после загрузки. Aspose.Words делает это легко.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Когда использовать:**  
Если вы создаёте пакетный процессор, который должен сообщать об отсутствующих шрифтах перед публикацией PDF, вывод таблицы шрифтов даст вам окончательную проверку.

---

## Полный, готовый к запуску пример

Объединив всё вместе, получаем полный класс, который можно скопировать в `FontSubstitutionDemo.java` и запустить:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Запуск кода:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

Вы должны увидеть сообщения о подстановке, а затем окончательный список шрифтов.

---

## Часто задаваемые вопросы и особые случаи

### Что делать, если я хочу подменить шрифт сам?

Обратный вызов предупреждений лишь сообщает, *что* было заменено. Если нужно принудительно задать конкретный запасной шрифт, используйте `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

Теперь любое вхождение “MissingFont” будет заменено на “Arial” до загрузки документа.

### Работает ли это при сохранении в PDF?

Абсолютно. Тот же обратный вызов срабатывает во время `document.save("out.pdf")`, если рендерер PDF также нуждается в подстановке шрифтов. Просто оставьте те же `LoadOptions` или подключите новый обратный вызов к `PdfSaveOptions`.

### Как это ведёт себя в многопоточном окружении?

`LoadOptions` **не** является потокобезопасным, поэтому создавайте новый экземпляр для каждого потока. Сам обратный вызов может быть без состояния (как показано) или вы можете внедрить логгер, умеющий работать с потоками.

### Что если отсутствующий шрифт — это фирменный корпоративный шрифт?

Обычно его размещают в папке шрифтов сервера и указывают Aspose.Words через `FontSettings.setFontsFolder("path/to/fonts", true)`. После этого обратный вызов перестанет срабатывать для этого шрифта, потому что он больше не считается отсутствующим.

---

## Профессиональные советы для продакшн‑готовой обработки шрифтов

- **Логировать, а не просто `System.out.println`** – используйте полноценный фреймворк логирования (SLF4J, Log4j), чтобы захватывать предупреждения в системе мониторинга.  
- **Кешировать поиск шрифтов** – если обрабатываете тысячи документов, избегайте повторного сканирования системной папки шрифтов. Загрузите шрифты один раз в экземпляр `FontSettings` и переиспользуйте его.  
- **Останавливать процесс при критически важных шрифтах** – можно бросить исключение внутри обратного вызова, если определённый шрифт обязателен для соответствия бренду.  
- **Тестировать на разнообразных документах** – включайте PDF, DOCX и DOC; каждый формат может генерировать разные типы предупреждений.  

---

## Заключение

Мы рассмотрели **как работать со шрифтами** в Java с помощью Aspose.Words от начала до конца:

1. Подключить `IWarningCallback` для перехвата предупреждений о подстановке шрифтов.  
2. Загрузить документ с `LoadOptions`, чтобы обратный вызов сработал автоматически.  
3. (Опционально) Проверить окончательную таблицу шрифтов, чтобы подтвердить результат.  

Следуя этим шагам, вы получаете полную видимость отсутствующих шрифтов, можете применять корпоративные политики шрифтов и избегать тихих подстановок, которые могут испортить внешний вид ваших генерируемых PDF или Word‑файлов.

Готовы к следующему вызову? Попробуйте изменить обратный вызов, чтобы логировать *все* предупреждения, поэкспериментировать с `FontSettings` для пользовательских правил подстановки или интегрировать эту логику в микросервис Spring‑Boot, обрабатывающий документы «на лету».

Счастливого кодинга, и пусть ваши документы всегда отображаются нужным шрифтом!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}