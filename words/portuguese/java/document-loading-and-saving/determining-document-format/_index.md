---
title: Determinando o formato do documento no Aspose.Words para Java
linktitle: Determinando o formato do documento
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda a detectar formatos de documentos em Java com Aspose.Words. Identifique DOC, DOCX e mais. Organize arquivos de forma eficiente.
weight: 25
url: /pt/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Determinando o formato do documento no Aspose.Words para Java


## Introdução à determinação do formato do documento no Aspose.Words para Java

Ao trabalhar com processamento de documentos em Java, é crucial determinar o formato dos arquivos com os quais você está lidando. O Aspose.Words para Java fornece recursos poderosos para identificar formatos de documentos, e nós o guiaremos pelo processo.

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes pré-requisitos:

- [Aspose.Words para Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) instalado no seu sistema
- Conhecimento básico de programação Java

## Etapa 1: Configuração do diretório

Primeiro, precisamos configurar os diretórios necessários para organizar nossos arquivos de forma eficaz. Criaremos diretórios para diferentes tipos de documentos.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Crie os diretórios caso eles ainda não existam.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Criamos diretórios para tipos de documentos suportados, desconhecidos, criptografados e anteriores a 97.

## Etapa 2: Detectando o formato do documento

Agora, vamos detectar o formato dos documentos em nossos diretórios. Usaremos Aspose.Words para Java para fazer isso.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Exibir o tipo de documento
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Adicione casos para outros formatos de documentos conforme necessário
    }

    // Lidar com documentos criptografados
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Lidar com outros tipos de documentos
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

Neste trecho de código, iteramos pelos arquivos, detectamos seus formatos e os organizamos nos respectivos diretórios.

## Código fonte completo para determinar o formato do documento em Aspose.Words para Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Crie os diretórios caso eles ainda não existam.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Exibir o tipo de documento
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Conclusão

Determinar formatos de documentos no Aspose.Words para Java é essencial para o processamento eficiente de documentos. Com as etapas descritas neste guia, você pode identificar tipos de documentos e lidar com eles adequadamente em seus aplicativos Java.

## Perguntas frequentes

### Como instalo o Aspose.Words para Java?

 Você pode baixar o Aspose.Words para Java em[aqui](https://releases.aspose.com/words/java/) siga as instruções de instalação fornecidas.

### Quais são os formatos de documentos suportados?

O Aspose.Words para Java suporta vários formatos de documentos, incluindo DOC, DOCX, RTF, HTML e mais. Você pode consultar a documentação para uma lista completa.

### Como posso detectar documentos criptografados usando o Aspose.Words para Java?

 Você pode usar o`FileFormatUtil.detectFileFormat()` método para detectar documentos criptografados, conforme demonstrado neste guia.

### Há alguma limitação ao trabalhar com formatos de documentos mais antigos?

Formatos de documentos mais antigos, como MS Word 6 ou Word 95, podem ter limitações em termos de recursos e compatibilidade com aplicativos modernos. Considere atualizar ou converter esses documentos quando necessário.

### Posso automatizar a detecção de formato de documento no meu aplicativo Java?

Sim, você pode automatizar a detecção de formato de documento integrando o código fornecido em seu aplicativo Java. Isso permite que você processe documentos com base em seus formatos detectados.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
