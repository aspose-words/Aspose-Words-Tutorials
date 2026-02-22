---
date: 2026-02-22
description: Aprenda como detectar o formato de documentos Java com Aspose.Words e
  mover arquivos automaticamente por formato. Identifique DOC, DOCX e muito mais.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: detectar o formato de documento Java usando Aspose.Words para Java
url: /pt/java/document-loading-and-saving/determining-document-format/
weight: 25
---

.

Let's produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detectar formato de documento java usando Aspose.Words para Java

Quando você precisa **detect document format java** em um lote de arquivos, a capacidade de classificá‑los automaticamente nas pastas corretas pode economizar horas de trabalho manual. Neste tutorial vamos mostrar como o Aspose.Words para Java facilita a identificação de Word, RTF, HTML, ODT e muitos outros formatos, e então **move arquivos por formato** para diretórios organizados.

## Respostas Rápidas
- **O que significa “detect document format java”?** É o processo de identificar programaticamente o formato de processamento de texto de um arquivo (DOC, DOCX, RTF, etc.) usando código Java.  
- **Qual biblioteca fornece essa capacidade?** O Aspose.Words para Java oferece a API `FileFormatUtil.detectFileFormat`.  
- **A utilidade também lida com arquivos criptografados?** Sim – a flag `FileFormatInfo.isEncrypted()` indica se um documento está protegido por senha.  
- **Preciso de licença para uso em produção?** Uma licença comercial do Aspose.Words é necessária para implantações que não sejam de avaliação.  
- **É possível mover arquivos automaticamente após a detecção?** Absolutamente – combine o resultado da detecção com `FileUtils.copyFile` para classificar arquivos em pastas personalizadas.

## O que é detect document format java?
`detect document format java` refere‑se ao uso de código Java para inspecionar o cabeçalho binário de um arquivo e determinar a qual formato de processamento de texto ele pertence (por exemplo, DOC, DOCX, ODT). O Aspose.Words lê o arquivo sem carregá‑lo completamente, tornando a operação rápida e eficiente em memória.

## Por que mover arquivos por formato?
Organizar documentos pelo seu formato nativo simplifica o processamento subsequente:

- **Conversões em lote** tornam‑se simples quando todos os arquivos DOCX estão em uma única pasta.  
- **Suporte legado**: você pode isolar arquivos Word pré‑97 para tratamento especial.  
- **Segurança**: documentos criptografados podem ser colocados em quarentena automaticamente.  

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

- [Aspose.Words para Java](https://releases.aspose.com/words/java/) (baixe a versão mais recente)  
- Java Development Kit (JDK) 8 ou superior instalado  
- Familiaridade básica com Java I/O e streams  

## Etapa 1: Configurar diretórios para cada formato

Primeiro criamos uma estrutura de pastas limpa onde os arquivos detectados serão movidos. Isso mantém o fluxo de trabalho organizado e facilita a adição de novas categorias de formato no futuro.

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

> **Dica:** Use caminhos absolutos ou configure o diretório base via um arquivo de propriedades para evitar codificação fixa de caminhos no código de produção.

## Etapa 2: Detectar o formato do documento e mover arquivos

O núcleo do **detect document format java** está no loop abaixo. Ele varre cada arquivo, determina seu tipo e o copia para a pasta apropriada.

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

O bloco `switch` pode ser expandido para cobrir todos os formatos que você precisar. Cada caso imprime uma mensagem amigável e então move o arquivo para a pasta correspondente.

## Código‑fonte completo para detectar formato de documento java

A seguir está o exemplo completo, pronto para execução, que combina a configuração de diretórios e a lógica de detecção. Copie‑o para uma classe Java, ajuste o caminho base e execute‑o contra uma pasta com documentos mistos.

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

## Problemas comuns e solução de problemas

| Problema | Por que acontece | Como corrigir |
|----------|------------------|---------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | O arquivo está corrompido ou usa um formato que não é Word. | Verifique a extensão do arquivo, ou adicione um fallback para movê‑lo para a pasta *Unknown* (já incluído no exemplo). |
| **Encrypted files throw an exception** | A API tenta ler o conteúdo antes de verificar a criptografia. | Sempre chame `info.isEncrypted()` antes de qualquer outra operação no documento. |
| **Directory creation fails on Linux** | Permissões insuficientes ou pasta pai ausente. | Garanta que o processo Java tenha permissão de escrita e que o caminho base exista. |

## Perguntas Frequentes

**Q: Como instalo o Aspose.Words para Java?**  
A: Você pode baixar o Aspose.Words para Java a partir do [here](https://releases.aspose.com/words/java/) e seguir as instruções de instalação fornecidas.

**Q: Quais formatos de documento são suportados para detecção?**  
A: O Aspose.Words pode detectar DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML e formatos mais antigos pré‑97, entre outros.

**Q: Este código pode lidar com documentos protegidos por senha?**  
A: Sim. A flag `FileFormatInfo.isEncrypted()` identifica arquivos criptografados, permitindo que você os mova para uma pasta segura sem abri‑los.

**Q: Há impacto de desempenho ao escanear pastas grandes?**  
A: A detecção lê apenas o cabeçalho do arquivo, então mesmo milhares de arquivos são processados rapidamente. Para lotes muito grandes, considere streams paralelos.

**Q: Como posso estender o script para converter formatos não suportados?**  
A: Após a detecção, você pode chamar `Document.save` com o formato de saída desejado para qualquer tipo de origem suportado.

## Conclusão

Usando **detect document format java** com Aspose.Words, você obtém um método confiável para classificar, colocar em quarentena ou converter arquivos relacionados ao Word automaticamente. O código de exemplo demonstra como criar uma hierarquia de pastas limpa, identificar o formato de cada arquivo e movê‑lo de acordo — economizando tempo e reduzindo erros manuais.

---

**Última atualização:** 2026-02-22  
**Testado com:** Aspose.Words para Java 24.12 (mais recente)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}