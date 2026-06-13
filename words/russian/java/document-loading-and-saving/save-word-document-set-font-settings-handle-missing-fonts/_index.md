---
category: general
date: 2026-04-24
description: Узнайте, как сохранять документ Word с помощью Aspose.Words, задавая
  параметры шрифтов и обрабатывая отсутствующие шрифты, используя простой и понятный
  код на Java.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: ru
og_description: Сохраните документ Word с помощью Aspose.Words, задавая параметры
  шрифтов и обрабатывая отсутствующие шрифты. Полное руководство по Java для разработчиков.
og_title: Сохранить документ Word – установить параметры шрифта, обработать отсутствующие
  шрифты
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Сохранить документ Word – задать настройки шрифта, обработать отсутствующие
  шрифты
url: /ru/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить документ Word – установить параметры шрифтов, обработать отсутствующие шрифты

Когда‑нибудь вам нужно было **save Word document**, но исходный файл использует шрифты, которых нет на вашем сервере? Это распространённая проблема, которая может превратить гладкую автоматизированную цепочку в головную боль.  

Хорошие новости? С помощью Aspose.Words вы можете **set font settings** «на лету», отлавливать предупреждения об отсутствующих шрифтах и всё равно получить идеально сохранённый документ Word. В этом руководстве мы пройдём полный пример на Java, показывающий **how to set font settings**, обработку страшных предупреждений *font substitution* и, наконец, **save Word document** без сюрпризов.

## Чему вы научитесь

- Как настроить `LoadOptions` с пользовательским объектом `FontSettings`.  
- Как зарегистрировать callback предупреждений, который сообщает о событиях **aspose words font substitution**.  
- Как загрузить DOCX, позволить Aspose заменить отсутствующие шрифты и **save Word document** в новое место.  
- Советы по обработке граничных случаев, таких как зашифрованные файлы или документы со встроенными шрифтами.  

Никакие дополнительные библиотеки, помимо Aspose.Words, не требуются, и код работает с последним выпуском 24.x (по состоянию на апрель 2026).  

---

![Diagram illustrating the save word document workflow with font settings and warning callback](font-workflow.png "Diagram showing save word document workflow")

## Сохранить документ Word с пользовательскими параметрами шрифтов

Первый шаг — сообщить Aspose.Words, что делать, когда он не может найти шрифт, указанный в исходном документе. Здесь и вступает в действие **set font settings**.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Почему это работает:**  
- `LoadOptions` сообщает Aspose.Words использовать предоставленные `FontSettings` при разборе файла.  
- `IWarningCallback` перехватывает любые сообщения **aspose words font substitution**, предоставляя вам живой журнал отсутствующих шрифтов.  
- Когда вы вызываете `document.save(...)`, Aspose автоматически заменяет отсутствующие шрифты на наиболее подходящие из системы или папок, добавленных в `FontSettings`.

### Ожидаемый результат

Запуск программы выводит строки вроде:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

И вы получаете `output.docx`, который выглядит точно так же, как оригинал — за исключением того, что отсутствующие шрифты заменены, и файл успешно **saved word document** на диске.

## Как установить параметры шрифтов в Aspose.Words

Если вам нужен больший контроль — например, указать Aspose пользовательскую папку со шрифтами или встроить запасной шрифт — просто измените объект `FontSettings` перед тем, как присвоить его `LoadOptions`.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**Когда использовать:**  
- Ваше приложение работает в контейнере, который поставляется только с минимальным набором системных шрифтов.  
- У вас есть фирменные шрифты, находящиеся в защищённом сетевом ресурсе.  
- Вы хотите гарантировать, что конкретный запасной шрифт (например, “Arial”) всегда используется, избегая непредсказуемых замен.

## Обработка отсутствующих шрифтов – обратный вызов замены шрифтов

Callback предупреждений, который мы зарегистрировали ранее, является ядром логики **handle missing fonts**. Вы можете расширить его, чтобы:

1. **Собирать предупреждения** в список для последующего отчёта.  
2. **Выбрасывать исключение** если критический шрифт отсутствует (например, шрифт логотипа).  
3. **Записывать в систему мониторинга** (Splunk, ELK и т.д.) для аудита.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**Pro tip:** Если вам нужно прервать операцию, когда отсутствует определённый шрифт, сравните `info.getDescription()` со списком разрешённых и выбросьте `RuntimeException`, когда совпадения нет.

## Полный пример на Java – от начала до конца

Объединив всё вместе, представляем автономную программу, которую можно скопировать и вставить в свою IDE. Убедитесь, что JAR‑файл Aspose.Words for Java находится в вашем classpath.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Запустите программу, следите за консолью на наличие любых **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}