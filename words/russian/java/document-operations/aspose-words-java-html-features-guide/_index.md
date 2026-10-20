---
date: '2026-02-06'
description: Узнайте, как загружать HTML‑VML с помощью Aspose.Words для Java, шифровать
  HTML‑файлы Java, задавать базовый URI HTML и настраивать параметры управления HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Загрузка HTML VML с помощью Aspose.Words для Java – Полное руководство
url: /ru/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Полный набор возможностей HTML в Aspose.Words for Java: Руководство разработчика

## Введение

Ориентироваться в сложном мире обработки документов может быть непросто, особенно когда речь идет о различных функциях HTML. Будь то поддержка Vector Markup Language (VML), зашифрованные документы или специфическое поведение импорта HTML, **Aspose.Words for Java** предлагает надёжное решение. В этом руководстве вы узнаете, **как загрузить html vml** эффективно и безопасно, а также рассмотрите сопутствующие задачи, такие как **encrypt html java**, **set html base uri** и **configure html control**.

**Что вы узнаете:**
- Как загружать HTML‑документы с поддержкой VML.
- Приёмы работы с фиксированными HTML‑страницами и предупреждениями.
- Методы шифрования и загрузки HTML‑документов, защищённых паролем.
- Использование базовых URI в параметрах загрузки HTML.
- Импорт HTML‑элементов ввода как структурированных тегов документа или полей формы.
- Игнорирование элементов `<noscript>` при загрузке HTML.
- Настройка режимов импорта блоков для контроля сохранения структуры HTML.
- Поддержка правил `@font-face` для пользовательских шрифтов.

## Быстрые ответы
- **Какой основной способ включить VML при загрузке HTML?** Установите `loadOptions.setSupportVml(true)`.
- **Можно ли загрузить HTML‑файлы, защищённые паролем?** Да, передайте пароль в `HtmlLoadOptions`.
- **Как разрешить относительные пути к изображениям?** Используйте `loadOptions.setBaseUri("your/base/uri")`.
- **Можно ли импортировать `<select>` как поле формы?** Установите `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Какой класс захватывает предупреждения во время загрузки?** Реализуйте `IWarningCallback` и назначьте его через `loadOptions.setWarningCallback(...)`.

## Предварительные требования

Прежде чем приступить к реализации различных функций HTML в Aspose.Words for Java, убедитесь, что ваша среда правильно настроена:

- **Необходимые библиотеки:** Требуется библиотека Aspose.Words версии 25.3 или новее.
- **Среда разработки:** В данном руководстве предполагается использование Maven или Gradle для управления зависимостями.
- **База знаний:** Базовое понимание Java и знакомство с HTML‑документами будет полезным.

## Настройка Aspose.Words

Чтобы начать работу с Aspose.Words, сначала добавьте её в ваш проект. Ниже приведены шаги по настройке библиотеки с помощью Maven и Gradle:

### Maven

Добавьте следующую зависимость в файл `pom.xml`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Включите это в файл `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Приобретение лицензии

Aspose.Words требует лицензию для полной функциональности. Вы можете получить бесплатную пробную версию, запросить временную лицензию или приобрести постоянную. Подробнее см. на [странице покупки](https://purchase.aspose.com/buy).

Чтобы инициализировать Aspose.Words в вашем Java‑проекте, убедитесь, что лицензия настроена корректно:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Руководство по реализации

Мы разобьём реализацию на разделы в зависимости от функций, которые хотим внедрить.

### Как загрузить html vml с помощью Aspose.Words

**Обзор:**  
Загрузка HTML‑документа с поддержкой VML позволяет гибко отображать векторную графику, такую как диаграммы и фигуры. Это основной шаг для ключевого запроса **load html vml**.

#### Пошагово

1. **Настройка параметров загрузки**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Загрузка документа**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Проверка типа изображения**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Загрузка фиксированного HTML и обработка предупреждений

**Обзор:**  
Загрузка фиксированных HTML‑страниц может генерировать предупреждения, которые необходимо обрабатывать для точного результата.

#### Пошагово

1. **Определение обратного вызова предупреждений**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Настройка параметров загрузки**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Загрузка документа и проверка предупреждений**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Шифрование HTML‑документов

**Обзор:**  
Шифрование HTML‑документа паролем обеспечивает безопасный доступ, что важно для конфиденциальной информации — это покрывает сценарий **encrypt html java**.

#### Пошагово

1. **Подготовка параметров цифровой подписи**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Подписание и шифрование документа**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Загрузка зашифрованного документа**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Базовый URI для параметров загрузки HTML

**Обзор:**  
Указание **set html base uri** помогает разрешать относительные URI, особенно при работе с изображениями или другими связанными ресурсами.

#### Пошагово

1. **Настройка параметров загрузки с базовым URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Загрузка документа и проверка изображения**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Импорт HTML‑элемента `<select>` как Structured Document Tag

**Обзор:**  
Чтобы **configure html control** поведение, можно импортировать элементы `<select>` как Structured Document Tags, получая более тонкий контроль над полями формы в Word‑документах.

#### Пошагово

1. **Установка предпочтительного типа управления**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Загрузка документа и проверка структуры**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Распространённые проблемы и решения

| Проблема | Причина | Решение |
|----------|---------|----------|
| Графика VML не отображается | Флаг `supportVml` оставлен по умолчанию (`false`) | Убедитесь, что `loadOptions.setSupportVml(true)` вызывается до загрузки. |
| После загрузки изображения отсутствуют | Относительные пути не могут быть разрешены | Используйте **set html base uri** (`loadOptions.setBaseUri(...)`) для указания правильной папки. |
| HTML, защищённый паролем, вызывает исключение | Пароль не передан | Передайте пароль в `new HtmlLoadOptions("yourPassword")`. |
| Элементы формы отображаются как обычный текст | Неправильный `HtmlControlType` | Установите `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` или `FormField` при необходимости. |
| Неожиданные предупреждения | Необработанные HTML‑элементы | Реализуйте `IWarningCallback` для захвата и анализа предупреждений. |

## Часто задаваемые вопросы

**В: Можно ли загружать HTML‑файлы, содержащие как VML, так и современные SVG‑графики?**  
О: Да. Включите VML через `setSupportVml(true)`; SVG обрабатывается автоматически Aspose.Words.

**В: Как зашифровать HTML‑документ без использования цифрового сертификата?**  
О: Используйте конструктор `HtmlLoadOptions`, принимающий пароль, и сохраните документ с `Document.save(..., SaveFormat.HTML)`, предварительно задав пароль.

**В: Что произойдёт, если базовый URI указывает на несуществующую папку?**  
О: Aspose.Words выбросит `FileNotFoundException` для недостающих ресурсов. Проверьте путь перед загрузкой.

**В: Можно ли изменить тип управления по умолчанию для всех HTML‑элементов формы?**  
О: Да. Вызов `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` применит его глобально.

**В: Являются ли обратные вызовы предупреждений потокобезопасными?**  
О: Реализация обратного вызова должна быть потокобезопасной, если планируется параллельная загрузка документов. Используйте синхронизированные коллекции или хранилище thread‑local.

---

**Последнее обновление:** 2026-02-06  
**Тестировано с:** Aspose.Words for Java 25.3  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}