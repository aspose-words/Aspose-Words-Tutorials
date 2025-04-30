---
"description": "Получите доступ и проверьте цифровые подписи в документах Word с помощью Aspose.Words для .NET с этим всеобъемлющим пошаговым руководством. Обеспечьте подлинность документа без усилий."
"linktitle": "Доступ и проверка подписи в документе Word"
"second_title": "API обработки документов Aspose.Words"
"title": "Доступ и проверка подписи в документе Word"
"url": "/ru/net/programming-with-digital-signatures/access-and-verify-signature/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Доступ и проверка подписи в документе Word

## Введение

Привет, друзья-энтузиасты технологий! Вы когда-нибудь оказывались в ситуации, когда вам нужно было получить доступ и проверить цифровые подписи в документе Word, но вы не знали, с чего начать? Что ж, вам повезло! Сегодня мы окунемся в чудесный мир Aspose.Words для .NET, мощной библиотеки, которая делает обработку документов Word легкой. Мы проведем вас через весь процесс шаг за шагом, так что к концу этого руководства вы станете профессионалом в проверке цифровых подписей в документах Word. Давайте начнем!

## Предпосылки

Прежде чем мы углубимся в подробности, вам необходимо иметь под рукой несколько вещей:

1. Visual Studio: Убедитесь, что на вашем компьютере установлена Visual Studio. Здесь вы будете писать и запускать свой код.
2. Aspose.Words for .NET: Вам понадобится установленный Aspose.Words for .NET. Вы можете скачать его [здесь](https://releases.aspose.com/words/net/). Не забудьте получить бесплатную пробную версию [здесь](https://releases.aspose.com/) если вы еще этого не сделали!
3. Документ Word с цифровой подписью: Имейте документ Word, который уже имеет цифровую подпись. Это файл, с которым вы будете работать для проверки подписей.

## Импорт пространств имен

Для начала давайте импортируем необходимые пространства имен. Эти пространства имен позволят вам использовать функции Aspose.Words в вашем проекте.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

Хорошо, давайте разобьем это на управляемые шаги. Каждый шаг проведет вас через определенную часть процесса. Готовы? Поехали!

## Шаг 1: Настройте свой проект

Прежде чем вы сможете проверить цифровую подпись, вам нужно настроить свой проект в Visual Studio. Вот как:

### Создать новый проект

1. Откройте Visual Studio.
2. Нажмите «Создать новый проект».
3. Выберите Консольное приложение (.NET Core) или Консольное приложение (.NET Framework) в зависимости от ваших предпочтений.
4. Нажмите «Далее», дайте проекту имя и нажмите «Создать».

### Установить Aspose.Words для .NET

1. В обозревателе решений щелкните правой кнопкой мыши имя вашего проекта и выберите «Управление пакетами NuGet».
2. В диспетчере пакетов NuGet найдите Aspose.Words.
3. Нажмите «Установить», чтобы добавить его в свой проект.

## Шаг 2: Загрузите документ Word с цифровой подписью

Теперь, когда ваш проект настроен, давайте загрузим документ Word с цифровой подписью.

```csharp
// Путь к каталогу документов.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Digitally signed.docx");
```

Заменять `"YOUR DOCUMENT DIRECTORY"` с фактическим путем к вашему каталогу документов. Этот фрагмент кода инициализирует новый `Document` объект и загружает ваш подписанный документ Word.

## Шаг 3: Получите доступ к цифровым подписям

После загрузки документа настало время получить доступ к цифровым подписям.

```csharp
foreach (DigitalSignature signature in doc.DigitalSignatures)
{
    Console.WriteLine("* Signature Found *");
    Console.WriteLine("Is valid: " + signature.IsValid);
    Console.WriteLine("Reason for signing: " + signature.Comments); 
    Console.WriteLine("Time of signing: " + signature.SignTime);
    Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
    Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
    Console.WriteLine();
}
```

Этот код проходит по каждой цифровой подписи в документе и выводит различные сведения о подписи. Давайте разберем, что делает каждая часть:

1. Подпись найдена: указывает на то, что подпись найдена.
2. Действительна: проверяет, действительна ли подпись.
3. Причина подписания: Отображает причину подписания, если таковая имеется.
4. Время подписания: показывает временную метку подписания документа.
5. Имя субъекта: извлекает имя субъекта из сертификата.
6. Имя эмитента: извлекает имя эмитента из сертификата.

## Шаг 4: Запустите свой код

Когда все настроено, пришло время запустить код и посмотреть результаты.


1. Нажмите клавишу F5 или кнопку «Пуск» в Visual Studio, чтобы запустить программу.
2. Если ваш документ имеет цифровую подпись, вы увидите данные подписи, напечатанные в консоли.

## Шаг 5: Обработайте потенциальные ошибки

Всегда полезно обрабатывать любые потенциальные ошибки, которые могут возникнуть. Давайте добавим в наш код базовую обработку ошибок.

```csharp
try
{
    // Путь к каталогу документов.
    string dataDir = "YOUR DOCUMENT DIRECTORY";
    Document doc = new Document(dataDir + "Digitally signed.docx");

    foreach (DigitalSignature signature in doc.DigitalSignatures)
    {
        Console.WriteLine("* Signature Found *");
        Console.WriteLine("Is valid: " + signature.IsValid);
        Console.WriteLine("Reason for signing: " + signature.Comments); 
        Console.WriteLine("Time of signing: " + signature.SignTime);
        Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
        Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
        Console.WriteLine();
    }
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

Это позволит перехватить все возможные исключения и вывести сообщение об ошибке.

## Заключение

И вот оно! Вы успешно получили доступ и проверили цифровые подписи в документе Word с помощью Aspose.Words for .NET. Это не так страшно, как кажется, не так ли? С этими шагами вы сможете уверенно работать с цифровыми подписями в ваших документах Word, гарантируя их подлинность и целостность. Удачного кодирования!

## Часто задаваемые вопросы

### Можно ли использовать Aspose.Words for .NET для добавления цифровых подписей в документ Word?

Да, вы можете использовать Aspose.Words for .NET для добавления цифровых подписей в документы Word. Библиотека предоставляет комплексные функции как для добавления, так и для проверки цифровых подписей.

### Какие типы цифровых подписей может проверять Aspose.Words for .NET?

Aspose.Words for .NET может проверять цифровые подписи в файлах DOCX, использующих сертификаты X.509.

### Совместим ли Aspose.Words для .NET со всеми версиями Microsoft Word?

Aspose.Words для .NET поддерживает все версии документов Microsoft Word, включая DOC, DOCX, RTF и другие.

### Как получить временную лицензию на Aspose.Words для .NET?

Вы можете получить временную лицензию для Aspose.Words for .NET по адресу [здесь](https://purchase.aspose.com/temporary-license/). Это позволяет вам опробовать все возможности библиотеки без каких-либо ограничений.

### Где я могу найти дополнительную документацию по Aspose.Words для .NET?

Подробную документацию по Aspose.Words для .NET вы можете найти [здесь](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}