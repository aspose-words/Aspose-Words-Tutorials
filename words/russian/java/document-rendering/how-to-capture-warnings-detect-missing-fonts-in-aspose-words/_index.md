---
category: general
date: 2026-03-19
description: Узнайте, как перехватывать предупреждения в Aspose.Words for Java и обнаруживать
  отсутствующие шрифты. Это пошаговое руководство также показывает, как корректно
  обрабатывать недостающие шрифты.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: ru
og_description: Как перехватывать предупреждения в Aspose.Words для Java, обнаруживать
  отсутствующие шрифты и обрабатывать их с полным примером кода.
og_title: Как перехватывать предупреждения – обнаружение отсутствующих шрифтов в Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Как перехватывать предупреждения – обнаружение отсутствующих шрифтов в Aspose.Words
url: /ru/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как захватывать предупреждения — обнаружение отсутствующих шрифтов в Aspose.Words

Когда‑нибудь задумывались **как захватывать предупреждения**, когда Word‑документ загружается и некоторые шрифты недоступны на машине? Вы не одиноки. Во многих реальных проектах отсутствующие шрифты вызывают тихие сдвиги макета, и единственный способ узнать, что произошло, — прослушать поток предупреждений, который генерирует Aspose.Words.  

В этом руководстве мы пройдем через полностью готовый к запуску пример, который **обнаруживает отсутствующие шрифты**, показывает **как программно обнаруживать отсутствующие шрифты** и даже дает быстрый совет по **обработке отсутствующих шрифтов**, чтобы ваш вывод оставался предсказуемым.

> **Быстрая заметка:** Код работает с Aspose.Words 23.9 (или новее) и требует Java 8+.

---

## Что вам понадобится

- **Aspose.Words for Java** (зависимость Maven/Gradle или JAR в classpath)  
- Word‑файл (`input.docx`), который ссылается на шрифт, не установленный в вашей системе (например, “Comic Sans MS”)  
- Java‑IDE или простая настройка командной строки `javac`/`java`  

Никаких дополнительных библиотек не требуется — всё остальное находится внутри пакета Aspose.Words.

---

## Шаг 1 – Настройте LoadOptions для захвата предупреждений  

Чтобы начать прослушивание предупреждений, необходимо создать экземпляр `LoadOptions`. Этот объект сообщает загрузчику отслеживать любые проблемы, с которыми он сталкивается, такие как отсутствующие шрифты.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Почему это важно:** Без `LoadOptions` загрузчик тихо заменяет отсутствующие шрифты шрифтом системы по умолчанию, и вы никогда не узнаете о замене. Включение предупреждений дает полную видимость.

---

## Шаг 2 – Загрузите документ, используя LoadOptions  

Теперь мы действительно загружаем документ. `LoadOptions`, который мы только что создали, передаётся в конструктор, поэтому любые предупреждения, возникшие во время разбора, фиксируются.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Совет:** Если вы обрабатываете множество файлов пакетно, переиспользуйте один и тот же экземпляр `LoadOptions`, чтобы избежать лишнего создания объектов.

---

## Шаг 3 – Переберите захваченные предупреждения  

Aspose.Words хранит каждое предупреждение как объект `WarningInfo`. Нас интересуют только предупреждения, связанные со шрифтами, поэтому мы фильтруем их по `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Объяснение:**  
- `document.getWarnings()` возвращает список всех предупреждений, возникших во время загрузки.  
- `FontSubstitutionWarningInfo` содержит две важные части данных: **запрошенный шрифт** (тот, который указан в DOCX) и **фактический шрифт**, на который Aspose.Words переключился.  
- Выводя оба значения, вы мгновенно видите, какие шрифты отсутствуют и какая замена произошла.

---

## Шаг 4 – (Опционально) Обработайте отсутствующие шрифты программно  

Захват предупреждений — лишь половина истории. Узнав, что шрифт отсутствует, вы можете **обработать отсутствующие шрифты**, предоставив собственную замену или записав проблему для последующего анализа.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Зачем это делать?**  
- Гарантирует согласованное отображение на разных машинах.  
- Предотвращает неожиданные изменения макета в PDF‑файлах или изображениях, генерируемых позже.  

Вы также можете сохранить детали предупреждения в базе данных, отправить письмо команде контента или даже прервать процесс, если критически важный шрифт отсутствует.

---

## Полный рабочий пример  

Ниже представлен полностью готовый к запуску код. Просто замените `YOUR_DIRECTORY/input.docx` на путь к вашему тестовому файлу, добавьте JAR‑файл Aspose.Words в classpath и запустите.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Ожидаемый вывод** (когда “Comic Sans MS” отсутствует):

```
Requested: Comic Sans MS → Substituted: Arial
```

После выполнения опционального кода замены сохранённый `output.docx` будет отображать **Arial** там, где изначально указывался “Comic Sans MS”.

---

## Часто задаваемые вопросы и особые случаи  

| Вопрос | Ответ |
|----------|--------|
| *Что если в документе несколько отсутствующих шрифтов?* | Цикл выдаст предупреждение для каждого из них. Вы можете собрать их в `Map<String, String>` для пакетной обработки. |
| *Работает ли это для PDF, сгенерированных из документа?* | Абсолютно. Замена шрифтов происходит на этапе загрузки, поэтому любой последующий экспорт (PDF, HTML, изображение) использует уже разрешённые шрифты. |
| *Можно ли подавить предупреждения вместо их захвата?* | Да — установите `loadOptions.setWarningCallback(null);`, но вы потеряете видимость отсутствующих шрифтов. |
| *Очищается ли список предупреждений после сохранения?* | Коллекция предупреждений принадлежит экземпляру `Document`. После вызова `document.save()` список остаётся неизменным, если только вы не создадите новый `Document`. |
| *Что насчёт пользовательских шрифтов, встроенных в DOCX?* | Встроенные шрифты считаются доступными; Aspose.Words будет использовать их, даже если они не установлены в системе. |

---

## Профессиональные советы для продакшн‑использования  

- **Кешируйте FontSettings:** При обработке сотен файлов создайте один `FontSettings` с вашими предпочтительными заменами и переиспользуйте его, чтобы избежать лишних накладных расходов.  
- **Записывайте структурированные данные:** Вместо простого `System.out` выводите предупреждения в JSON‑лог — это упростит последующий анализ (например, “какие шрифты отсутствуют чаще всего”).  
- **Валидация на раннем этапе:** Выполните быструю “сухую загрузку” с `LoadOptions` перед тяжёлой обработкой; при отсутствии критических шрифтов прерывайте процесс сразу.  
- **Потокобезопасность:** Объекты `Document` не являются потокобезопасными. Обрабатывайте каждый файл в отдельном потоке или используйте `LoadOptions`, хранящийся в Thread‑Local.  

---

## Заключение  

Теперь вы знаете **как захватывать предупреждения** в Aspose.Words для Java, **обнаруживать отсутствующие шрифты** и **обрабатывать отсутствующие шрифты** с помощью чистой стратегии замены. Используя `LoadOptions` и перебирая `document.getWarnings()`, вы получаете полную информацию о событиях замены шрифтов, гарантируя, что генерируемые документы выглядят точно так, как задумано, во всех средах.

Готовы к следующему шагу? Попробуйте расширить этот шаблон для **обнаружения отсутствующих изображений**, **отслеживания неподдерживаемых функций** или даже **автоматического встраивания отсутствующих шрифтов** в итоговый файл. Тот же подход захвата предупреждений работает во множестве других сценариев обработки документов, делая ваш код надёжным и готовым к будущему.

Счастливого кодинга, и пусть ваши документы всегда отображаются красиво!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}