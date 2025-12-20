---
date: 2025-12-20
description: Узнайте, как загружать HTML и преобразовывать HTML в DOCX с помощью Aspose.Words
  для Java. Пошаговое руководство показывает, как сохранять файлы DOCX и использовать
  структурированные теги документа.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Как загрузить HTML и сохранить как DOCX с помощью Aspose.Words для Java
url: /ru/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как загрузить HTML и сохранить как DOCX с помощью Aspose.Words for Java

## Введение в загрузку и сохранение HTML‑документов с помощью Aspose.Words for Java

В этой статье мы рассмотрим **как загрузить html** и сохранить его в файл DOCX с помощью библиотеки Aspose.Words for Java. Aspose.Words — мощный API, позволяющий программно работать с документами Word, и он предоставляет надёжную поддержку импорта/экспорта HTML. Мы пройдём весь процесс, от настройки параметров загрузки до сохранения результата в документ Word.

## Быстрые ответы
- **Какой основной класс для загрузки HTML?** `Document` вместе с `HtmlLoadOptions`.
- **Какая опция включает Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Можно ли конвертировать HTML в DOCX за один шаг?** Да — загрузите HTML и вызовите `doc.save(...".docx")`.
- **Нужна ли лицензия для разработки?** Бесплатная пробная версия подходит для тестирования; для продакшн‑использования требуется коммерческая лицензия.
- **Какая версия Java требуется?** Поддерживается Java 8 и выше.

## Что означает «как загрузить html» в контексте Aspose.Words?
Загрузка HTML означает чтение строки HTML или файла и преобразование его в объект `Document` библиотеки Aspose.Words. Этот объект затем можно редактировать, форматировать или сохранять в любой поддерживаемый API формат, такой как DOCX, PDF или RTF.

## Почему стоит использовать Aspose.Words для конвертации HTML‑в‑DOCX?
- **Сохраняет макет** — таблицы, списки и изображения остаются неизменными.
- **Поддерживает Structured Document Tags** — идеально для создания элементов управления содержимым в Word.
- **Не требует Microsoft Office** — работает на любом сервере или в облачной среде.
- **Высокая производительность** — быстро обрабатывает большие HTML‑файлы.

## Требования

1. **Библиотека Aspose.Words for Java** — скачайте её по ссылке [here](https://releases.aspose.com/words/java/).
2. **Среда разработки Java** — установлен и настроен JDK 8+.
3. **Базовые знания Java I/O** — мы будем использовать `ByteArrayInputStream` для передачи строки HTML.

## Как загрузить HTML‑документы

Ниже приведён краткий пример, демонстрирующий загрузку фрагмента HTML с включённой функцией **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Объяснение**

- Мы создаём строку `HTML`, содержащую простой элемент `<select>`.
- `HtmlLoadOptions` позволяет задать, как следует интерпретировать HTML. Установка предпочтительного типа управления в `STRUCTURED_DOCUMENT_TAG` указывает Aspose.Words преобразовать элементы управления формы HTML в элементы управления содержимым Word.
- Конструктор `Document` читает HTML из `ByteArrayInputStream` с использованием кодировки UTF‑8.

## Как сохранить как DOCX (конвертация HTML в DOCX)

После загрузки HTML в объект `Document` сохранение его в файл DOCX происходит просто:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Замените `"Your Directory Path"` на фактический путь к папке, где вы хотите разместить выходной файл.

## Полный исходный код для загрузки и сохранения HTML‑документов

Ниже представлен полный готовый к запуску пример, объединяющий шаги загрузки и сохранения. Смело копируйте‑вставляйте его в свою IDE.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Распространённые ошибки и советы

| Проблема | Почему происходит | Как исправить |
|----------|-------------------|---------------|
| **Отсутствие шрифтов** | HTML ссылается на шрифты, не установленные на сервере. | Встроить шрифты в DOCX с помощью `FontSettings` или убедиться, что требуемые шрифты доступны. |
| **Изображения не отображаются** | Относительные пути к изображениям не могут быть разрешены. | Использовать абсолютные URL или загрузить изображения в `MemoryStream` и установить `HtmlLoadOptions.setImageSavingCallback`. |
| **Тип управления не преобразован** | `setPreferredControlType` не установлен или установлен неверный enum. | Проверьте, что вы используете `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Проблемы с кодировкой** | Строка HTML закодирована в другой кодировке. | Всегда используйте `StandardCharsets.UTF_8` при преобразовании строки в байты. |

## Часто задаваемые вопросы

### Как установить Aspose.Words for Java?
Aspose.Words for Java можно скачать по ссылке [here](https://releases.aspose.com/words/java/). Следуйте руководству по установке на странице загрузки, чтобы добавить JAR‑файлы в classpath вашего проекта.

### Можно ли загрузить сложные HTML‑документы с помощью Aspose.Words?
Да, Aspose.Words for Java способен обрабатывать сложный HTML, включая вложенные таблицы, CSS‑стили и интерактивные элементы без JavaScript. Настраивайте `HtmlLoadOptions` (например, `setLoadImages` или `setCssStyleSheetFileName`), чтобы точно управлять импортом.

### Какие другие форматы документов поддерживает Aspose.Words?
Aspose.Words поддерживает DOC, DOCX, RTF, HTML, PDF, EPUB, XPS и многие другие. API предоставляет однострочное сохранение в любой из этих форматов.

### Подходит ли Aspose.Words для корпоративной автоматизации документов?
Безусловно. Он используется крупными компаниями для автоматической генерации отчётов, массовой конвертации документов и серверной обработки без зависимости от Microsoft Office.

### Где можно найти дополнительную документацию и примеры для Aspose.Words for Java?
Вы можете изучить полную справку API и дополнительные руководства на сайте документации Aspose.Words for Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Последнее обновление:** 2025-12-20  
**Тестировано с:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}