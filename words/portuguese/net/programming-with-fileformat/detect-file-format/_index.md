---
title: Detectar formato de arquivo de documento
linktitle: Detectar formato de arquivo de documento
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a detectar formatos de arquivo de documento usando o Aspose.Words para .NET com este guia abrangente passo a passo.
weight: 10
url: /pt/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detectar formato de arquivo de documento

## Introdução

No mundo digital de hoje, gerenciar diferentes formatos de documentos de forma eficiente é crucial. Não importa se você está lidando com Word, PDF, HTML ou outros formatos, ser capaz de detectar e processar esses arquivos corretamente pode economizar muito tempo e esforço. Neste tutorial, exploraremos como detectar formatos de arquivo de documento usando o Aspose.Words para .NET. Este guia o guiará por tudo o que você precisa saber, desde os pré-requisitos até um guia detalhado passo a passo.

## Pré-requisitos

Antes de mergulharmos no código, vamos garantir que você tenha tudo o que precisa:

-  Aspose.Words para .NET: Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/) . Certifique-se de ter uma licença válida. Se não, você pode obter uma[licença temporária](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Qualquer versão recente funcionará bem.
- .NET Framework: certifique-se de ter a versão correta instalada.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários no seu projeto:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Vamos dividir o exemplo em várias etapas para torná-lo mais fácil de seguir.

## Etapa 1: Configurar diretórios

Primeiro, precisamos configurar diretórios onde os arquivos serão classificados com base em seu formato.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Crie os diretórios caso eles ainda não existam.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Etapa 2: Obtenha a lista de arquivos

Em seguida, obteremos uma lista de arquivos do diretório, excluindo quaisquer documentos corrompidos.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Etapa 3: Detectar formatos de arquivo

Agora, iteramos por cada arquivo e detectamos seu formato usando Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Exibir o tipo de documento
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Conclusão

Detectar formatos de arquivo de documento usando o Aspose.Words para .NET é um processo direto. Ao configurar seus diretórios, obter sua lista de arquivos e utilizar o Aspose.Words para detectar formatos de arquivo, você pode organizar e gerenciar seus documentos de forma eficiente. Essa abordagem não só economiza tempo, mas também garante que você manipule vários formatos de documento corretamente.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words for .NET é uma biblioteca poderosa para trabalhar com documentos do Word programaticamente. Ela permite que desenvolvedores criem, modifiquem e convertam documentos em vários formatos.

### O Aspose.Words pode detectar documentos criptografados?
Sim, o Aspose.Words pode detectar se um documento está criptografado e você pode lidar com esses documentos adequadamente.

### Quais formatos o Aspose.Words pode detectar?
O Aspose.Words pode detectar uma ampla variedade de formatos, incluindo DOC, DOCX, RTF, HTML, MHTML, ODT e muitos outros.

### Como posso obter uma licença temporária para o Aspose.Words?
 Você pode obter uma licença temporária no[Aspose Compra](https://purchase.aspose.com/temporary-license/) página.

### Onde posso encontrar a documentação do Aspose.Words?
 A documentação para Aspose.Words pode ser encontrada[aqui](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
