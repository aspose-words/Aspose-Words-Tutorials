---
"description": "Узнайте, как читать свойства элементов управления ActiveX из файлов Word с помощью Aspose.Words для .NET в пошаговом руководстве. Улучшите свои навыки автоматизации документов."
"linktitle": "Чтение свойств Active XControl из файла Word"
"second_title": "API обработки документов Aspose.Words"
"title": "Чтение свойств Active XControl из файла Word"
"url": "/ru/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Чтение свойств Active XControl из файла Word

## Введение

В сегодняшнюю цифровую эпоху автоматизация является ключом к повышению производительности. Если вы работаете с документами Word, содержащими элементы управления ActiveX, вам может потребоваться прочитать их свойства для различных целей. Элементы управления ActiveX, такие как флажки и кнопки, могут содержать важные данные. Используя Aspose.Words для .NET, вы можете эффективно извлекать и обрабатывать эти данные программным способом.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующее:

1. Библиотека Aspose.Words for .NET: Вы можете загрузить ее с сайта [здесь](https://releases.aspose.com/words/net/).
2. Visual Studio или любая C# IDE: для написания и выполнения вашего кода.
3. Документ Word с элементами управления ActiveX: например, «ActiveX controls.docx».
4. Базовые знания C#: для изучения курса необходимы знания программирования на C#.

## Импорт пространств имен

Сначала давайте импортируем необходимые пространства имен для работы с Aspose.Words для .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Шаг 1: Загрузите документ Word

Для начала вам необходимо загрузить документ Word, содержащий элементы управления ActiveX.

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Шаг 2: Инициализация строки для хранения свойств

Затем инициализируйте пустую строку для хранения свойств элементов управления ActiveX.

```csharp
string properties = "";
```

## Шаг 3: Перебор фигур в документе

Нам необходимо перебрать все фигуры в документе, чтобы найти элементы управления ActiveX.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Обработка элемента управления ActiveX
    }
}
```

## Шаг 4: Извлечение свойств из элементов управления ActiveX

В цикле проверьте, является ли элемент управления Forms2OleControl. Если это так, приведите его и извлеките свойства.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Шаг 5: Подсчитайте общее количество элементов управления ActiveX

После перебора всех фигур подсчитайте общее количество найденных элементов управления ActiveX.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Шаг 6: Отображение свойств

Наконец, выведите извлеченные свойства на консоль.

```csharp
Console.WriteLine("\n" + properties);
```

## Заключение

И вот оно! Вы успешно научились читать свойства элементов управления ActiveX из документа Word с помощью Aspose.Words for .NET. В этом руководстве рассматривалась загрузка документа, итерация фигур и извлечение свойств из элементов управления ActiveX. Выполнив эти шаги, вы сможете автоматизировать извлечение важных данных из документов Word, повысив эффективность своего рабочего процесса.

## Часто задаваемые вопросы

### Что такое элементы управления ActiveX в документах Word?
Элементы управления ActiveX — это интерактивные объекты, встроенные в документы Word, такие как флажки, кнопки и текстовые поля, используемые для создания форм и автоматизации задач.

### Можно ли изменять свойства элементов управления ActiveX с помощью Aspose.Words для .NET?
Да, Aspose.Words для .NET позволяет программно изменять свойства элементов управления ActiveX.

### Является ли Aspose.Words для .NET бесплатным для использования?
Aspose.Words for .NET предлагает бесплатную пробную версию, но для дальнейшего использования вам необходимо приобрести лицензию. Вы можете получить бесплатную пробную версию [здесь](https://releases.aspose.com/).

### Могу ли я использовать Aspose.Words для .NET с другими языками .NET, помимо C#?
Да, Aspose.Words для .NET можно использовать с любым языком .NET, включая VB.NET и F#.

### Где я могу найти дополнительную документацию по Aspose.Words для .NET?
Подробную документацию вы можете найти [здесь](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}