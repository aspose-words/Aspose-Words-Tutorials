---
title: Inserir objeto Ole em documento do Word como ícone
linktitle: Inserir objeto Ole em documento do Word como ícone
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como inserir um objeto OLE como um ícone em documentos do Word usando o Aspose.Words para .NET. Siga nosso guia passo a passo para aprimorar seus documentos.
weight: 10
url: /pt/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir objeto Ole em documento do Word como ícone

## Introdução

Você já precisou incorporar um objeto OLE, como uma apresentação do PowerPoint ou uma planilha do Excel, em um documento do Word, mas queria que ele aparecesse como um pequeno ícone bacana em vez de um objeto completo? Bem, você está no lugar certo! Neste tutorial, mostraremos como inserir um objeto OLE como um ícone em um documento do Word usando o Aspose.Words para .NET. Ao final deste guia, você será capaz de integrar perfeitamente objetos OLE em seus documentos, tornando-os mais interativos e visualmente atraentes.

## Pré-requisitos

Antes de nos aprofundarmos nos detalhes essenciais, vamos abordar o que você precisa:

1.  Aspose.Words para .NET: Certifique-se de ter o Aspose.Words para .NET instalado. Se você ainda não o instalou, você pode baixá-lo do[Página de lançamentos da Aspose](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: você precisa de um ambiente de desenvolvimento integrado (IDE) como o Visual Studio.
3. Conhecimento básico de C#: Um conhecimento básico de programação em C# será útil.

## Importar namespaces

Primeiro, você precisa importar os namespaces necessários. Isso é essencial para acessar as funções da biblioteca Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Etapa 1: Crie um novo documento

Para começar, você precisa criar uma nova instância de documento do Word.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Este trecho de código inicializa um novo documento do Word e um objeto DocumentBuilder que é usado para criar o conteúdo do documento.

## Etapa 2: Insira o objeto OLE como ícone

 Agora, vamos inserir o objeto OLE como um ícone. O`InsertOleObjectAsIcon` O método da classe DocumentBuilder é usado para essa finalidade.

```csharp
builder.InsertOleObjectAsIcon("path_to_your_presentation.pptx", false, "path_to_your_icon.ico", "My embedded file");
```

Vamos analisar esse método:
- `"path_to_your_presentation.pptx"`: Este é o caminho para o objeto OLE que você deseja incorporar.
- `false` : Este parâmetro booleano especifica se o objeto OLE deve ser exibido como um ícone. Como queremos um ícone, o definimos como`false`.
- `"path_to_your_icon.ico"`: Este é o caminho para o arquivo de ícone que você deseja usar para o objeto OLE.
- `"My embedded file"`: Este é o rótulo que aparecerá abaixo do ícone.

## Etapa 3: Salve o documento

Por fim, você precisa salvar o documento. Escolha o diretório onde você quer salvar seu arquivo.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
```

Esta linha de código salva o documento no caminho especificado.

## Conclusão

Parabéns! Você aprendeu com sucesso como inserir um objeto OLE como um ícone em um documento do Word usando o Aspose.Words para .NET. Essa técnica não só ajuda a incorporar objetos complexos, mas também mantém seu documento organizado e profissional.

## Perguntas frequentes

### Posso usar diferentes tipos de objetos OLE com este método?

Sim, você pode incorporar vários tipos de objetos OLE, como planilhas do Excel, apresentações do PowerPoint e até PDFs.

### Como faço para obter uma avaliação gratuita do Aspose.Words para .NET?

 Você pode obter uma avaliação gratuita no[Página de lançamentos da Aspose](https://releases.aspose.com/).

### O que é um objeto OLE?

OLE (Object Linking and Embedding) é uma tecnologia desenvolvida pela Microsoft que permite incorporar e vincular documentos e outros objetos.

### Preciso de uma licença para usar o Aspose.Words para .NET?

 Sim, Aspose.Words para .NET requer uma licença. Você pode comprá-lo no[Aspose página de compra](https://purchase.aspose.com/buy) ou pegue um[licença temporária](https://purchase.aspose.com/temporary-license/) para avaliação.

### Onde posso encontrar mais tutoriais sobre Aspose.Words para .NET?

 Você pode encontrar mais tutoriais e documentação em[Página de documentação do Aspose](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
