---
category: general
date: 2026-10-10
description: Создайте параметры подписи и подпишите документ Word с использованием
  XAdES EPES в Java. Узнайте, как подписать офисный документ сертификатом в нескольких
  понятных шагах.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: ru
lastmod: 2026-10-10
og_description: Создайте параметры подписи и подпишите документ Word с использованием
  XAdES EPES в Java. Это руководство покажет, как безопасно подписать офисный документ
  с помощью сертификата.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Создайте параметры подписи и подпишите документ Word с помощью XAdES EPES
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Создайте параметры подписи и подпишите документ Word с помощью XAdES EPES
url: /ru/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание параметров подписи и подпись Word‑документа с XAdES EPES

Если вам нужно **создать параметры подписи** для файла DOCX, это руководство покажет, как подписать Word‑документ, используя уровень XAdES‑EPES в Java. Вы получите полностью готовый пример, который подписывает офисный документ сертификатом PFX всего в нескольких строках кода.

Подписание офисных документов — распространённая задача для юридических процессов, автоматизированной обработки контрактов и безопасного обмена документами. В этом уроке вы узнаете:

* Как настроить `SignatureOptions` для XAdES‑EPES.  
* Как вызвать `DigitalSignatureUtil.sign` для **подписи Word‑документов**.  
* Как справляться с типичными проблемами, такими как загрузка сертификата и ошибки пароля.

> **Требования** – Java 17 или новее, библиотека GroupDocs.Signature for Java (или совместимая XAdES‑библиотека) и действительный файл сертификата `.pfx`.

---

## Что понадобится

| Элемент | Причина |
|------|--------|
| Java 17+ | Современные возможности языка и улучшенные API безопасности |
| GroupDocs.Signature for Java (или эквивалент) | Предоставляет `SignatureOptions`, `XmlDsigLevel` и `DigitalSignatureUtil` |
| Сертификат PFX (`.pfx`) | Содержит закрытый ключ для цифровой подписи |
| Пароль к сертификату | Необходим для разблокировки закрытого ключа |
| Не подписанный DOCX‑файл (`Unsigned.docx`) | Исходный документ, который вы хотите **подписать офисный документ** |

Убедитесь, что JAR‑файл библиотеки находится в вашем classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Шаг 1: Импортировать необходимые классы

Начните с импорта классов, которые работают с подписями и вводом‑выводом файлов.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Эти импорты дают вам доступ к API, используемому для **создания параметров подписи** и выполнения самой операции подписи.

---

## Шаг 2: Создать параметры подписи

Объект `SignatureOptions` хранит всю конфигурацию, необходимую для процесса подписи, включая уровень подписи, визуальное оформление и настройки метки времени.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Создание нового экземпляра `SignatureOptions` — первый шаг в **как подписать docx**‑файлы, поскольку он изолирует каждый запрос подписи, предотвращая побочные эффекты между документами.

---

## Шаг 3: Указать уровень подписи XAdES EPES

XAdES‑EPES (Explicit Policy‑based Electronic Signature) — широко принятая политика для подписей офисных документов. Установка уровня сообщает библиотеке, какой криптографический профиль использовать.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Почему XAdES‑EPES? Он встраивает политику подписи непосредственно в подпись, делая подписанный документ самодостаточным и соответствующим многим нормативам электронных подписей.

---

## Шаг 4: Подписать DOCX‑файл

Теперь вызовите `DigitalSignatureUtil.sign`. Этот метод читает исходный файл, применяет подпись и записывает подписанный результат.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**Что происходит «под капотом»?**  
1. Библиотека загружает файл `.pfx` и извлекает закрытый ключ, используя указанный пароль.  
2. Создаётся структура XML‑DSig, соответствующая профилю XAdES‑EPES.  
3. Подпись встраивается в пакет DOCX, сохраняя оригинальное оформление документа.  

Если пароль к сертификату неверен или файл не может быть прочитан, будет выброшено `IOException`, которое следует обработать, как показано.

---

## Шаг 5: Проверить подписанный документ (необязательно)

После подписи вы можете убедиться, что подпись присутствует и действительна. GroupDocs предоставляет API проверки, но быструю ручную проверку можно выполнить в Microsoft Word:

1. Откройте `SignedXades.docx` в Word.  
2. Выберите **Файл → Свойства → Просмотр подписей**.  
3. Word должен отобразить зелёную галочку, указывающую на действительную цифровую подпись.

Автоматическая проверка с помощью библиотеки выглядит так:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Выполнение шага проверки даёт программную уверенность в том, что **подпись офисного документа** прошла успешно.

---

## Полный, готовый к запуску пример

Объединив все части, получаем самостоятельный Java‑класс, который можно скопировать, вставить и запустить.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Ожидаемый вывод**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Если что‑то пойдёт не так, в консоли появится понятное сообщение об ошибке, помогающее отладить проблемы с сертификатом или путём к файлу.

---

## Часто задаваемые вопросы и обработка граничных случаев

| Вопрос | Ответ |
|----------|--------|
| **Можно ли использовать другой уровень подписи?** | Да. Замените `XmlDsigLevel.XAdES_EPES` на `XAdES_BES`, `XAdES_T` и т.д., в зависимости от требований к соответствию. |
| **Что если мой сертификат хранится в keystore, а не в файле .pfx?** | Загрузите `KeyStore` вручную, извлеките `PrivateKey` и `Certificate`, затем передайте их в перегруженную версию `sign`, принимающую объект `KeyStore`. |
| **Как добавить видимую подпись‑изображение?** | Вызовите `signatureOptions.setSignatureImage("path/to/image.png")` перед вызовом `sign`. |
| **Потокобезопасен ли процесс подписи?** | Метод `DigitalSignatureUtil.sign` не хранит состояние; его можно безопасно вызывать из нескольких потоков, при условии, что каждый поток использует собственный экземпляр `SignatureOptions`. |
| **Что если DOCX уже содержит подписи?** | Библиотека добавит новую запись подписи, сохранив существующие подписи. Убедитесь, что политика подписи допускает множественные подписи, если это необходимо. |

---

## Советы и лучшие практики (E‑E‑A‑T)

* **Pro tip:** Храните пароль к сертификату в защищённом хранилище (например, Azure Key Vault), а не в коде.  
* **Обратите внимание:** Разделители путей в Windows (`\`) и Unix (`/`). Используйте `Paths.get(...)` для построения кроссплатформенных путей.  
* **Производительность:** Подписание больших DOCX‑файлов может быть ограничено вводом‑выводом; рассмотрите потоковую передачу входного файла при пакетной обработке.  
* **Соответствие:** XAdES‑EPES соответствует регламенту EU eIDAS; проверьте локальные юридические требования перед выбором уровня подписи.

---

## Заключение

В этом руководстве вы узнали, как **создать параметры подписи** и **подписать Word‑документ** уровнем XAdES‑EPES с помощью Java. Полный пример охватывает загрузку сертификата, конфигурацию параметров, вызов подписи и опциональную проверку, предоставляя готовое решение для **как подписать docx**‑файлы в продакшене.

## Что изучать дальше?

Следующие учебные материалы охватывают смежные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в своих проектах.

- [Create Load Options in Java – Detect Missing Fonts & How to Load DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Create Editable Ranges in Read-Only Documents Using Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}