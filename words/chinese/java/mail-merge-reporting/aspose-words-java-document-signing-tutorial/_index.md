---
"date": "2025-03-28"
"description": "学习如何使用 Aspose.Words for Java 实现文档签名自动化。本教程涵盖环境设置、测试数据创建、签名行添加以及文档数字签名。"
"title": "使用 Aspose.Words 在 Java 中自动进行文档签名的综合指南"
"url": "/zh/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words 在 Java 中自动进行文档签名：综合指南

## 介绍

在当今快节奏的商业世界中，高效的文档管理至关重要。自动化文档创建和数字签名可以节省时间并最大限度地减少错误。本教程将指导您使用 Aspose.Words for Java 为签名者创建测试数据、添加签名行并对文档进行数字签名。

**您将学到什么：**
- 在 Java 项目中设置 Aspose.Words
- 使用 Java 创建测试签名者数据
- 在 Word 文档中添加签名行
- 使用数字证书对文档进行数字签名

让我们从准备您的开发环境开始！

## 先决条件

在深入学习本教程之前，请确保您的设置满足以下要求：

- **Java 开发工具包 (JDK)：** 版本 8 或更高版本。
- **集成开发环境（IDE）：** 例如 IntelliJ IDEA 或 Eclipse。
- **Java 版 Aspose.Words：** 该库可以通过 Maven 或 Gradle 包含。

### 知识前提

具备 Java 编程基础知识并熟悉文件和流处理将对您有所帮助。如果您是 Aspose 新手，不用担心——我们会讲解基础知识。

## 设置 Aspose.Words

要在您的项目中使用 Aspose.Words for Java，请按照以下步骤操作：

### Maven 依赖

将以下依赖项添加到您的 `pom.xml` 文件：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle 依赖

对于 Gradle 项目，请在您的 `build.gradle` 文件：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 许可证获取

Aspose 提供不同的许可选项：

- **免费试用：** 下载免费试用版来测试其功能。
- **临时执照：** 获取临时许可证以用于评估目的。
- **购买：** 要获得完全访问权限，请从 Aspose 网站购买许可证。

确保您的项目已配置必要的依赖项和所有必要的许可证。此设置将使您能够无缝利用 Aspose 强大的文档处理功能。

## 实施指南

我们将逐步介绍每个功能，从创建测试签名者数据开始。

### 功能 1：为签名者创建测试数据

#### 概述

此功能可生成包含签名者唯一 ID、姓名、职位和图像的列表。这对于在不使用真实数据的情况下测试文档签名场景至关重要。

##### 步骤 1：设置 Java 类

创建一个名为 `SignPersonCreator` 并导入必要的库：

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### 解释

- **UUID：** 为每个签名者生成一个唯一的标识符。
- **获取字节流：** 将图像文件转换为字节数组进行存储。

### 功能 2：在文档中添加签名行

#### 概述

此功能可在您的文档中添加签名行，并将其与签名者的详细信息关联起来。

##### 步骤 1：创建 SignatureLineAdder 类

实施 `SignatureLineAdder` 类如下：

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### 解释

- **签名行选项：** 配置签名者的姓名和职称。
- **插入签名行：** 在文档的当前光标位置插入签名行。

### 功能3：使用数字证书签署文档

#### 概述

此功能使用数字证书对文档进行数字签名，确保真实性和完整性。

##### 步骤 1：创建 DocumentSigner 类

实施 `DocumentSigner` 班级：

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### 解释

- **证书持有人：** 表示用于签名的数字证书。
- **符号：** 使用指定的选项和证书对文档进行签名的方法。

## 结论

在本教程中，您学习了如何使用 Aspose.Words 在 Java 中自动创建和签名文档。按照这些步骤，您可以简化文档管理流程，增强安全性并确保数据完整性。如需进一步探索，请考虑深入了解 Aspose.Words 的更多高级功能。

**后续步骤：**
- 探索其他 Aspose.Words 功能，如邮件合并或报告生成。
- 查看 Aspose 文档以获取详细指南和 API 参考。
- 尝试 Aspose.Words 支持的不同文档格式。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}