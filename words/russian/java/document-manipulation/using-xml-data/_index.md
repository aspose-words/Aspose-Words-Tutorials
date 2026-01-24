---
date: 2026-01-24
description: Узнайте, как объединять XML‑данные с Aspose.Words для Java, автоматизировать
  генерацию документов на Java и использовать синтаксис Mustache для динамических
  документов.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Как объединить XML в Aspose.Words для Java
url: /ru/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как объединять XML в Aspose.Words для Java

В этом полном руководстве вы узнаете **как объединять XML**‑данные с помощью Aspose.Words для Java. Мы пройдём базовые и вложенные сценарии слияния почтовой рассылки, покажем, как **использовать синтаксис Mustache**, и объясним, как **автоматизировать генерацию документов** в проектах на Java. К концу вы сможете создавать персонализированные документы Word напрямую из XML‑источников, написав всего несколько строк кода.

## Быстрые ответы
- **Какой основной класс для слияния почтовой рассылки?** `Document` и его свойство `MailMerge`.  
- **Можно ли объединять вложенные XML‑таблицы?** Да – используйте `executeWithRegions` для иерархических данных.  
- **Поддерживается ли синтаксис Mustache?** Включите его с помощью `setUseNonMergeFields(true)`.  
- **Нужна ли лицензия для продакшн?** Требуется коммерческая лицензия Aspose.Words.  
- **Какая версия Java совместима?** Полностью поддерживаются Java 8+ и более новые версии.

## Что такое XML‑слияние в Aspose.Words?
XML‑слияние позволяет привязывать наборы данных на основе XML к заполнителям в шаблоне Word. Движок заменяет каждый заполнитель соответствующим значением узла XML, создавая готовый документ без ручного редактирования.

## Почему стоит использовать Aspose.Words для генерации документов на основе XML?
- **Автоматизировать генерацию документов Java**‑проекта без зависимостей от Microsoft Office.  
- **Поддержка сложных иерархий** – вложенные таблицы, повторяющиеся секции и условный контент.  
- **Синтаксис Mustache** предоставляет гибкие заполнители без полей слияния для продвинутого шаблонирования.  
- **Кроссплатформенность** – работает в Windows, Linux и macOS.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть следующее:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) установлен (последняя версия).  
- Примерные XML‑файлы для клиентов, заказов и поставщиков (в руководстве используются `Mail merge data - Customers.xml`, `Orders.xml` и `Vendors.xml`).  
- Шаблоны Word, содержащие поля слияния (например, `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Как объединять XML – базовое слияние почтовой рассылки

Базовое слияние извлекает одну XML‑таблицу в шаблон Word. Выполните следующие шаги:

1. Загрузите XML‑файл в `DataSet`.  
2. Откройте целевой документ Word.  
3. Выполните слияние, указав имя таблицы.  
4. Сохраните объединённый документ.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Совет:** Делайте структуру XML плоской для простых слияний – каждая таблица должна напрямую соответствовать набору полей слияния.

## Как объединять XML – вложенное слияние почтовой рассылки

Если ваш XML содержит отношения «родитель‑дочерний» (например, заказы с позициями), понадобится вложенное слияние. Метод `executeWithRegions` обрабатывает каждый регион рекурсивно.

1. Загрузите иерархический XML в `DataSet`.  
2. Отключите обрезку пробелов, если требуется точное форматирование.  
3. Вызовите `executeWithRegions` для обработки всех вложенных таблиц.  
4. Сохраните результат.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Распространённая ошибка:** Не установить `setTrimWhitespaces(false)` может привести к появлению лишних пробелов в финальном документе, особенно в полях валюты или чисел.

## Как использовать синтаксис Mustache с DataSet

Синтаксис Mustache позволяет вставлять заполнители без полей слияния (например, `{{CustomerName}}`) в ваш шаблон. Включите его и выполните слияние по регионам.

1. Загрузите XML поставщика.  
2. Включите поддержку Mustache с помощью `setUseNonMergeFields(true)`.  
3. Выполните слияние с регионами.  
4. Сохраните результат.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Зачем нужен Mustache?** Он предоставляет чистый, независимый от языка способ ссылки на данные, делая шаблоны более читаемыми и поддерживаемыми, особенно при **генерации документов на основе XML**‑рабочих процессов.

## Распространённые проблемы и решения

| Проблема | Решение |
|----------|---------|
| Узлы XML не совпадают с полями слияния | Убедитесь, что имена элементов XML точно соответствуют именам полей слияния (чувствительно к регистру). |
| Пробелы появляются вокруг объединённых значений | Используйте `doc.getMailMerge().setTrimWhitespaces(false)`, чтобы сохранить оригинальные пробелы. |
| Вложенные таблицы игнорируются | Убедитесь, что регион родительской таблицы определён в шаблоне (например, `{{#Orders}} … {{/Orders}}`). |
| Заполнители Mustache не заменяются | Вызовите `setUseNonMergeFields(true)` перед выполнением слияния. |

## Часто задаваемые вопросы

### Как подготовить XML‑данные для слияния почтовой рассылки?

Убедитесь, что ваш XML имеет табличную структуру, где каждый элемент `<TableName>` содержит строки (`<Row>`) и столбцы, соответствующие полям слияния в шаблоне Word.

### Можно ли настроить поведение обрезки пробелов для значений слияния?

Да. Используйте `doc.getMailMerge().setTrimWhitespaces(false)`, чтобы сохранять ведущие/замыкающие пробелы точно так, как они указаны в XML.

### Что такое синтаксис Mustache и когда его следует использовать?

Синтаксис Mustache (`{{FieldName}}`) позволяет использовать гибкие заполнители, не ограниченные традиционными полями слияния. Включайте его с помощью `setUseNonMergeFields(true)`, когда нужен более чистый шаблон или требуется отделить логику данных от кодов полей Word.

### Как автоматизировать генерацию документов Java‑проектов с помощью этого подхода?

Интегрируйте приведённые выше фрагменты кода в слой сервисов, считывайте XML из баз данных или API и вызывайте процедуру слияния каждый раз, когда требуется новый документ (например, генерация счёта‑фактуры, создание контракта).

### Требуется ли коммерческая лицензия для использования в продакшн?

Да, Aspose.Words нуждается в действующей лицензии для развертывания в продакшн. Для оценки доступна бесплатная временная лицензия.

---

**Последнее обновление:** 2026-01-24  
**Тестировано с:** Aspose.Words for Java (последний релиз)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}