---
category: general
date: 2026-05-30
description: Зарегистрировать обработчик предупреждений в Java для отслеживания отсутствующих
  шрифтов и настройки загрузки документа с помощью Aspose.Words. Узнайте полное пошаговое
  решение.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: ru
og_description: Зарегистрировать обратный вызов предупреждения в Java для отслеживания
  отсутствующих шрифтов и настройки загрузки документа. Полное руководство с кодом
  и объяснениями.
og_title: Регистрация обработчика предупреждений в Java – Отслеживание недостающих
  шрифтов
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Регистрация обработчика предупреждений в Java – отслеживание отсутствующих
  шрифтов
url: /ru/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Регистрация обратного вызова предупреждений в Java – Отслеживание отсутствующих шрифтов

Когда‑нибудь задумывались, как **отслеживать отсутствующие шрифты** при загрузке Word‑документа с помощью Aspose.Words for Java? Возможно, вы видели тихие подстановки шрифтов и думали: «Что случилось с моим макетом?» Хорошая новость — угадывать не придётся. **Зарегистрировав обратный вызов предупреждений**, вы сможете фиксировать каждое событие подстановки шрифта в момент чтения документа, а также **настроить загрузку документа** под ваш конвейер.

В этом руководстве мы пройдём реальный пример, показывающий, как именно настроить обратный вызов, почему это важно и как сохранить остальную часть вашего конвейера обработки чистой. К концу вы получите готовый к запуску Java‑класс, который выводит каждое предупреждение об отсутствующем шрифте и сохраняет обработанную копию документа. Никаких внешних ссылок — только чистый, исполняемый код.

> **Что вы получите:**  
> • Полную Java‑программу с использованием Aspose.Words  
> • Пошаговые объяснения каждой строки  
> • Советы по обработке крайних случаев, таких как зашифрованные файлы или большие партии  
> • Быструю проверку, которую можно запустить на любом файле `.docx`

## Требования

Прежде чем мы начнём, убедитесь, что у вас есть:

- **Java 17** (или любой современный JDK) установлен и переменная `JAVA_HOME` настроена.  
- **Aspose.Words for Java** JAR в вашем classpath. Последнюю версию можно взять из репозитория Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Пример Word‑документа (`input.docx`), в котором, как вы подозреваете, используются шрифты, не установленные на вашей машине.  
- IDE или инструмент сборки командной строки (Maven/Gradle), с которым вам удобно работать.

Это всё. Никаких дополнительных шрифтов, никаких внешних сервисов — только чистый Java и Aspose.Words.

## Почему стоит регистрировать обратный вызов предупреждений?

Подумайте о **обратном вызове предупреждений** как о системе видеонаблюдения для процесса загрузки вашего документа. Когда Aspose.Words встречает отсутствующий глиф, он не бросает исключение; он тихо заменяет его запасным шрифтом. Такая скрытая подстановка может нарушить ваш макет, особенно в PDF‑документах или счетах, где важна точная фирменная стилистика. Зарегистрировав обратный вызов, вы:

1. **Получаете информацию в реальном времени** — каждое предупреждение `FONT_SUBSTITUTION` доставляется мгновенно.  
2. **Логируете или реагируете** — можно записать в файл, поднять тревогу или даже программно заменить шрифт.  
3. **Поддерживаете чистый вывод** — знание, какие шрифты отсутствуют, позволяет исправить исходный документ до публикации.

Короче говоря, обратный вызов превращает скрытую проблему в видимую, делая ваш конвейер обработки документов гораздо надёжнее.

## Шаг 1 — Создание `LoadOptions` для настройки загрузки документа

Первое, что мы делаем, — создаём экземпляр `LoadOptions`. Этот объект является шлюзом для всех настроек, которые могут понадобиться во время загрузки, от обработки пароля до нашей функции **регистрации обратного вызова предупреждений**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Почему бы просто не вызвать `new Document("file.docx")`? Потому что без `LoadOptions` вы теряете возможность подключиться к событиям загрузки. `LoadOptions` — единственное место, где Aspose.Words позволяет **настраивать загрузку документа**.

## Шаг 2 — Регистрация обратного вызова предупреждений для отслеживания отсутствующих шрифтов

Теперь наступает звёздный момент: мы **регистрируем обратный вызов предупреждений**, реализующий `IWarningCallback`. Внутри метода `warning` мы фильтруем `WarningType.FONT_SUBSTITUTION` и выводим полезное сообщение.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Несколько замечаний:

- **Почему `IWarningCallback`?** Это интерфейс, который Aspose.Words использует для всех типов предупреждений, предоставляя единый входной пункт для множества возможных проблем.  
- **Фильтрация критична** — без проверки `if` вы будете видеть предупреждения о недостающих изображениях, устаревших функциях и т.д., что засорит ваш журнал.  
- **Потокобезопасность** — обратный вызов исполняется в том же потоке, что и загрузка документа, поэтому вы можете безопасно обновлять общие структуры, если позже захотите агрегировать результаты.

Этот фрагмент **регистрирует обратный вызов предупреждений**, и с этого момента каждое событие отсутствующего шрифта будет выводиться в `stdout`. Это ядро **отслеживания отсутствующих шрифтов**.

## Шаг 3 — Загрузка документа с использованием сконфигурированных `LoadOptions`

С установленным обратным вызовом мы наконец загружаем файл. Если документ ссылается на шрифт, которого у вас нет, обратный вызов срабатывает до полной инициализации объекта `Document`.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Замените `YOUR_DIRECTORY` реальным путём на вашей машине. Конструктор `Document` читает файл, применяет пароль (если вы задали его в `loadOptions`) и вызывает обратный вызов предупреждений для каждого отсутствующего шрифта. Вы увидите вывод вроде:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Эта строка доказывает, что вы успешно **отслеживаете отсутствующие шрифты**.

## Шаг 4 — Дальнейшая обработка документа (по желанию)

На этом этапе вы можете манипулировать документом как угодно — заменять текст, вставлять изображения или даже программно менять подставленные шрифты. Обратный вызов уже дал вам список проблемных шрифтов, так что, например, можно внедрить запасной шрифт:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Можно пропустить этот блок, если вам нужно только **отслеживать отсутствующие шрифты**. Главное, что теперь у вас есть информация, необходимая для принятия обоснованного решения.

## Шаг 5 — Сохранение обработанного документа

Наконец, сохраняем документ. Можно перезаписать оригинал, сохранить в новое место или экспортировать в PDF — всё без потери данных предупреждений, собранных ранее.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Запуск полного класса выведет в консоль сообщения о каждом отсутствующем шрифте и создаст новый файл `processed.docx` в той же папке.

## Полный рабочий пример

Ниже представлен полный Java‑класс, который можно скопировать и вставить в свою IDE. Он включает всё, о чём мы говорили, плюс небольшой `main`‑метод‑обёртку.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Ожидаемый вывод

При запуске программы на документе, использующем шрифт, не установленный в системе, вы увидите примерно следующее:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Если в документе **нет отсутствующих шрифтов**, консоль будет молчать до финальной строки «Document saved successfully.» — именно то, что ожидается от корректно реализованного **регистрации обратного вызова предупреждений**.

## Профессиональные советы и распространённые подводные камни

- **Несколько обратных вызовов?** Aspose.Words допускает только один обработчик предупреждений. Если нужно логировать и в файл, и в консоль, реализуйте составной обратный вызов, который будет перенаправлять предупреждения в несколько мест.  
- **Большие партии** — при обработке сотен файлов имеет смысл переиспользовать один экземпляр `LoadOptions`; создание нового объекта для каждого файла добавляет лишние накладные расходы.  
- **Зашифрованные документы** — задайте пароль в `LoadOptions` до загрузки, иначе вы получите `IncorrectPasswordException` ещё до того, как обратный вызов сработает.  
- **Производительность** — обратный вызов работает синхронно. Если вы логируете в удалённый сервис, буферизуйте сообщения и сбрасывайте их после завершения загрузки, чтобы избежать узких мест ввода‑вывода.  
- **Запасные шрифты** — можно также предоставить собственную коллекцию `FontSource`, если у вас есть проприетарные шрифты, которые Aspose.Words должен учитывать перед тем, как обращаться к системным.

## Заключение

Вы только что узнали, как **зарегистрировать обратный вызов предупреждений** в Java, эффективно **отслеживать отсутствующие шрифты** и **настраивать загрузку документа** с помощью Aspose.Words. Решение автономно, запускается из единственного `main`‑метода и сразу даёт видимость любой подстановки шрифта, которая иначе осталась бы незамеченной.

Что дальше? Попробуйте расширить обратный вызов, чтобы записывать предупреждения в CSV‑файл для аудита, или объедините его с пакетным процессором, который автоматически встраивает недостающие шрифты. Вы также можете изучить другие типы предупреждений, такие как `IMAGE_SUBSTITUTION` или `DEPRECATED_FEATURE` — тот же шаблон применим.

Счастливого кодинга, и пусть ваши документы всегда отображаются точно так, как вы задумали!

![Диаграмма регистрации обратного вызова предупреждений](register-warning-callback.png "Схема регистрации обратного вызова предупреждений")


## Что стоит изучить дальше?

- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}