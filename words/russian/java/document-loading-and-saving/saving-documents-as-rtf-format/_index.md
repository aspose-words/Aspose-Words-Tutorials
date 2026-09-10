---
date: 2025-12-24
description: Узнайте, как конвертировать Word в RTF с помощью Aspose.Words для Java.
  Этот пошаговый учебник показывает загрузку DOCX, настройку параметров сохранения
  RTF и сохранение в формате Rich Text.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: Преобразовать Word в RTF с помощью Aspose.Words для Java. Учебник
url: /ru/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Преобразование Word в RTF с помощью Aspose.Words for Java

В этом руководстве вы узнаете **как преобразовать Word в RTF** быстро и надёжно с помощью Aspose.Words for Java. Преобразование DOCX в формат RTF — распространённая задача, когда требуется широкая совместимость со старыми текстовыми процессорами, почтовыми клиентами или системами архивирования документов. Мы пройдём процесс загрузки документа Word в Java, настройки параметров сохранения RTF (включая сохранение изображений в формате WMF) и, наконец, записи выходного файла.

## Быстрые ответы
- **Что означает «convert word to rtf»?** Он преобразует файл DOCX/Word в формат Rich Text Format, сохраняя текст, стили и, при желании, изображения.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для разработки; для продакшн‑использования требуется коммерческая лицензия.  
- **Какая версия Java поддерживается?** Aspose.Words for Java поддерживает Java 8 и выше.  
- **Можно ли сохранить изображения при преобразовании?** Да — используйте параметр `saveImagesAsWmf`, чтобы внедрить изображения в формате WMF в RTF.  
- **Сколько времени занимает преобразование?** Обычно менее секунды для стандартных документов; более крупные файлы могут потребовать несколько секунд.

## Что такое «convert word to rtf»?
Преобразование документа Word в RTF создаёт платформенно‑независимый файл, который хранит текст, форматирование и, при желании, изображения в разметке на основе обычного текста. Это позволяет просматривать документ почти в любом текстовом процессоре без потери макета.

## Почему стоит использовать Aspose.Words for Java для сохранения в формат rich text?
- **Полная точность** – Все возможности Word (стили, таблицы, колонтитулы) сохраняются.  
- **Не требуется Microsoft Office** – Работает на любом сервере или в облачной среде.  
- **Тонкая настройка** – Параметры сохранения позволяют выбрать способ хранения изображений, кодировку и многое другое.

## Предварительные требования
1. **Библиотека Aspose.Words for Java** – Скачайте и добавьте JAR в ваш проект из [здесь](https://releases.aspose.com/words/java/).  
2. **Исходный файл Word** – Например, `Document.docx`, который вы хотите сохранить как RTF.  
3. **Среда разработки Java** – JDK 8+ и ваша любимая IDE.

## Шаг 1: Загрузка документа Word (load word document java)
Сначала загрузите существующий DOCX в объект `Document`. Это основа для любого преобразования.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **Совет:** Используйте абсолютные пути или ресурсы из class‑path, чтобы избежать `FileNotFoundException`.

## Шаг 2: Настройка параметров сохранения RTF (save images as wmf)
Aspose.Words предоставляет класс `RtfSaveOptions` для тонкой настройки вывода. В этом примере мы включаем **save images as WMF**, который является предпочтительным форматом для файлов RTF.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

Вы также можете изменить другие параметры, например `saveOptions.setEncoding(Charset.forName("UTF-8"))`, если требуется определённая кодировка символов.

## Шаг 3: Сохранение документа как RTF (save docx as rtf)
Теперь запишите документ, используя настроенные параметры. Этот шаг **сохраняет DOCX как RTF**, создавая файл rich‑text, готовый к распространению.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## Полный исходный код для преобразования Word в RTF
Ниже представлена компактная версия, которую можно скопировать и вставить в класс Java. Она демонстрирует **save as rich text** с опцией изображений WMF в одном блоке.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## Распространённые ошибки и их устранение
| Проблема | Причина | Решение |
|----------|---------|---------|
| RTF‑файл пустой | Исходный файл не найден или не загружен | Проверьте путь в `new Document(...)` |
| Изображения отсутствуют | `saveImagesAsWmf` установлен в `false` | Включите `saveOptions.setSaveImagesAsWmf(true)` |
| Искажение символов | Неправильная кодировка | Установите `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## Часто задаваемые вопросы

**В: Как изменить другие параметры сохранения RTF?**  
О: Используйте класс `RtfSaveOptions` — он предоставляет свойства для сжатия, шрифтов и прочего. Обратитесь к документации Aspose.Words Java API для полного списка.

**В: Можно ли сохранить документ RTF в другой кодировке?**  
О: Да. Вызовите `saveOptions.setEncoding(Charset.forName("UTF-8"))` (или любую поддерживаемую кодировку) перед сохранением.

**В: Можно ли сохранить документ RTF без изображений?**  
О: Конечно. Установите `saveOptions.setSaveImagesAsWmf(false)`, чтобы исключить изображения из вывода.

**В: Как обрабатывать исключения во время преобразования?**  
О: Оберните вызовы загрузки и сохранения в блок try‑catch, перехватывая `Exception`. Запишите ошибку в лог и при необходимости пере‑выбросьте пользовательское исключение для вашего приложения.

**В: Работает ли это с защищёнными паролем файлами Word?**  
О: Загрузите документ с помощью объекта `LoadOptions`, содержащего пароль, а затем выполните те же шаги сохранения.

## Заключение
Теперь у вас есть полный, готовый к продакшн метод **преобразования Word в RTF** с помощью Aspose.Words for Java. Загрузив DOCX, настроив `RtfSaveOptions` (включая **save images as WMF**) и вызвав `doc.save(...)`, вы можете генерировать высококачественные файлы rich‑text, работающие везде. Не стесняйтесь изучать дополнительные параметры сохранения, чтобы адаптировать вывод под ваши точные требования.

---

**Последнее обновление:** 2025-12-24  
**Тестировано с:** Aspose.Words for Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}