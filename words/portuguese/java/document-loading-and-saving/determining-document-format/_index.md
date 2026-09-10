---
date: 2025-12-20
description: Aprenda a organizar arquivos por tipo e detectar formatos de documentos
  em Java com Aspose.Words. Suporta DOC, DOCX, RTF e mais.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organize arquivos por tipo usando Aspose.Words para Java
url: /pt/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organizar Arquivos por Tipo Usando Aspose.Words para Java

Quando você precisa **organizar arquivos por tipo** em uma aplicação Java, o primeiro passo é determinar de forma confiável o formato de cada documento. Aspose.Words para Java torna isso simples, permitindo detectar DOC, DOCX, RTF, HTML, ODT e muitos outros formatos – inclusive arquivos criptografados ou desconhecidos. Neste guia, vamos percorrer a configuração de pastas, a detecção de formatos de arquivo e a classificação automática dos seus arquivos.

## Respostas Rápidas
- **O que significa “organizar arquivos por tipo”?** Significa mover automaticamente os documentos para pastas com base no formato detectado (ex.: DOCX, PDF, RTF).  
- **Qual biblioteca ajuda a detectar o formato de arquivo em Java?** Aspose.Words para Java fornece `FileFormatUtil.detectFileFormat()`.  
- **A API pode identificar tipos de arquivo desconhecidos?** Sim – ela retorna `LoadFormat.UNKNOWN` para arquivos não suportados ou não reconhecíveis.  
- **A detecção de documentos criptografados é suportada?** Absolutamente; a flag `FileFormatInfo.isEncrypted()` indica se um arquivo está protegido por senha.  
- **Preciso de licença para uso em produção?** Uma licença válida do Aspose.Words é necessária para implantações comerciais.

## Introdução: Organizar Arquivos por Tipo com Aspose.Words para Java

Ao trabalhar com processamento de documentos em Java, é crucial determinar o formato dos arquivos que você está manipulando. Aspose.Words para Java oferece recursos poderosos para **detect file format java**, e vamos guiá‑lo pelo processo de organizar seus arquivos de forma eficiente.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem os seguintes pré‑requisitos:

- [Aspose.Words para Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) instalado no seu sistema
- Conhecimento básico de programação Java

## Etapa 1: Configuração de Diretórios

Primeiro, precisamos criar os diretórios necessários para organizar nossos arquivos de forma eficaz. Criaremos pastas para diferentes tipos de documentos.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Criamos pastas para tipos suportados, desconhecidos, criptografados e documentos pré‑97.

## Etapa 2: Detectando o Formato do Documento

Agora, vamos detectar o formato dos documentos em nossas pastas. Usaremos Aspose.Words para Java para isso.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
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

Neste trecho iteramos pelos arquivos, **detect file format java**, e os organizamos nas pastas apropriadas.

## Código‑Fonte Completo para Determinar o Formato do Documento em Aspose.Words para Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
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
            // Display the document type
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

## Como Detectar Formato de Arquivo Java

O método `FileFormatUtil.detectFileFormat()` inspeciona o cabeçalho do arquivo e retorna um objeto `FileFormatInfo`. Esse objeto informa o **load format**, se o arquivo está criptografado e outras metadatas úteis. Usando essas informações, você pode programaticamente **identify unknown file types** e decidir como processar cada um.

## Identificar Tipos de Arquivo Desconhecidos

Quando a API retorna `LoadFormat.UNKNOWN`, o arquivo está corrompido ou usa um formato que o Aspose.Words não suporta. No nosso código de exemplo, movemos esses arquivos para a pasta **Unknown** para que você possa revisá‑los posteriormente.

## Problemas Comuns e Soluções

| Problema | Motivo | Solução |
|----------|--------|---------|
| Arquivos são sempre colocados na pasta *Supported* | `FileFormatUtil` não conseguiu ler o cabeçalho (ex.: arquivo vazio) | Certifique‑se de que está passando o caminho correto do arquivo e que ele não tem tamanho zero. |
| Arquivos criptografados lançam exceção | Tentativa de leitura sem tratar a criptografia | Use a verificação `info.isEncrypted()` antes de qualquer processamento adicional, como mostrado no código. |
| Documentos Word pré‑97 não são detectados | Formatos antigos precisam do caso `DOC_PRE_WORD_60` | Mantenha o bloco `case LoadFormat.DOC_PRE_WORD_60` para direcioná‑los à pasta *Pre97*. |

## Perguntas Frequentes

### Como instalo o Aspose.Words para Java?

Você pode baixar o Aspose.Words para Java [aqui](https://releases.aspose.com/words/java/) e seguir as instruções de instalação fornecidas.

### Quais são os formatos de documento suportados?

Aspose.Words para Java suporta vários formatos de documento, incluindo DOC, DOCX, RTF, HTML, ODT e mais. Consulte a documentação oficial para a lista completa.

### Como posso detectar documentos criptografados usando Aspose.Words para Java?

Use o método `FileFormatUtil.detectFileFormat()`; a flag `FileFormatInfo.isEncrypted()` retornada indica criptografia, como demonstrado neste guia.

### Existem limitações ao trabalhar com formatos de documento mais antigos?

Formatos antigos como MS Word 6 ou Word 95 podem carecer de recursos modernos e apresentar problemas de compatibilidade. Considere convertê‑los para formatos mais recentes quando possível.

### Posso automatizar a detecção de formato de documento na minha aplicação Java?

Sim, incorpore o código fornecido ao pipeline de processamento da sua aplicação. Isso permite a classificação e o tratamento automáticos com base nos formatos detectados.

---

**Última atualização:** 2025-12-20  
**Testado com:** Aspose.Words para Java 24.12 (mais recente)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}