---
title: Reduza o tamanho do arquivo PDF não incorporando fontes principais
linktitle: Reduza o tamanho do arquivo PDF não incorporando fontes principais
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como reduzir o tamanho do arquivo PDF não incorporando fontes principais usando o Aspose.Words para .NET. Siga nosso guia passo a passo para otimizar seus PDFs.
weight: 10
url: /pt/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reduza o tamanho do arquivo PDF não incorporando fontes principais

## Introdução

Você já se pegou coçando a cabeça, se perguntando por que seus arquivos PDF são tão grandes? Bem, você não está sozinho. Um culpado comum é incorporar fontes principais como Arial e Times New Roman. Felizmente, o Aspose.Words para .NET tem uma maneira bacana de lidar com esse problema. Neste tutorial, mostrarei como reduzir o tamanho do seu arquivo PDF evitando a incorporação dessas fontes principais. Vamos direto ao assunto!

## Pré-requisitos

Antes de embarcarmos nessa jornada emocionante, vamos garantir que você tenha tudo o que precisa. Aqui vai uma lista de verificação rápida:

-  Aspose.Words para .NET: Certifique-se de ter o Aspose.Words para .NET instalado. Se você ainda não o tem, você pode baixá-lo[aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: você precisará de um ambiente de desenvolvimento como o Visual Studio.
- Um documento do Word: usaremos um documento do Word (por exemplo, "Rendering.docx") para este tutorial.
- Conhecimento básico de C#: um conhecimento básico de C# ajudará você a acompanhar.

Tudo bem, agora que estamos prontos, vamos ao que interessa!

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Este passo garante que temos acesso a todas as funcionalidades do Aspose.Words que precisamos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: inicialize seu diretório de documentos

Antes de começarmos a manipular nosso documento, precisamos especificar o diretório onde nossos documentos estão armazenados. Isso é essencial para acessar os arquivos.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real onde seu documento do Word está localizado.

## Etapa 2: Carregue o documento do Word

Em seguida, precisamos carregar o documento do Word que queremos converter para PDF. Neste exemplo, estamos usando um documento chamado "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Esta linha de código carrega o documento na memória, pronto para processamento posterior.

## Etapa 3: Configurar opções de salvamento de PDF

Agora vem a parte mágica! Configuraremos as opções de salvamento do PDF para evitar a incorporação de fontes principais. Esta é a etapa principal que ajuda a reduzir o tamanho do arquivo PDF.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 Contexto`UseCoreFonts` para`true` garante que fontes principais como Arial e Times New Roman não sejam incorporadas no PDF, o que reduz significativamente o tamanho do arquivo.

## Etapa 4: Salve o documento como PDF

Por fim, salvamos o documento do Word como um PDF usando as opções de salvamento configuradas. Esta etapa gera o arquivo PDF sem incorporar as fontes principais.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

E aí está! Seu arquivo PDF agora está salvo no diretório especificado sem aquelas fontes de núcleo volumosas.

## Conclusão

Reduzir o tamanho do arquivo PDF pode ser moleza com o Aspose.Words para .NET. Ao evitar a incorporação de fontes principais, você pode diminuir significativamente o tamanho do arquivo, facilitando o compartilhamento e o armazenamento de seus documentos. Espero que este tutorial tenha sido útil e tenha lhe dado uma compreensão clara do processo. Lembre-se, pequenos ajustes podem fazer uma grande diferença!

## Perguntas frequentes

### Por que devo evitar incorporar fontes principais em PDFs?
Evitar incorporar fontes principais reduz o tamanho do arquivo, facilitando seu compartilhamento e armazenamento.

### Ainda posso visualizar o PDF corretamente sem fontes principais incorporadas?
Sim, fontes básicas como Arial e Times New Roman geralmente estão disponíveis na maioria dos sistemas.

### E se eu precisar incorporar fontes personalizadas?
 Você pode personalizar o`PdfSaveOptions`para incorporar fontes específicas conforme necessário.

### O Aspose.Words para .NET é gratuito?
 Aspose.Words para .NET requer uma licença. Você pode obter uma avaliação gratuita[aqui](https://releases.aspose.com/).

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
 Você pode encontrar documentação detalhada[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
