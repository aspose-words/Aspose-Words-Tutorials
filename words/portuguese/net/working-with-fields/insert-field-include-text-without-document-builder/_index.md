---
"description": "Aprenda como inserir um FieldIncludeText sem usar o DocumentBuilder no Aspose.Words para .NET com nosso guia detalhado passo a passo."
"linktitle": "Inserir FieldIncludeText sem o Document Builder"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Inserir campo Incluir texto sem o Construtor de documentos"
"url": "/pt/net/working-with-fields/insert-field-include-text-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir campo Incluir texto sem o Construtor de documentos

## Introdução

No mundo da automação e manipulação de documentos, o Aspose.Words para .NET se destaca como uma ferramenta poderosa. Hoje, vamos apresentar um guia detalhado sobre como inserir um FieldIncludeText sem usar o DocumentBuilder. Este tutorial guiará você pelo processo passo a passo, garantindo que você entenda cada parte do código e sua finalidade.

## Pré-requisitos

Antes de mergulharmos no código, vamos garantir que você tenha tudo o que precisa:

1. Aspose.Words para .NET: Certifique-se de ter a versão mais recente instalada. Você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento .NET: qualquer IDE compatível com .NET, como o Visual Studio.
3. Conhecimento básico de C#: A familiaridade com a programação em C# ajudará você a acompanhar.

## Importar namespaces

Primeiramente, precisamos importar os namespaces necessários. Esses namespaces fornecem acesso às classes e métodos necessários para manipular documentos do Word.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Agora, vamos dividir o exemplo em várias etapas. Cada etapa será explicada em detalhes para garantir clareza.

## Etapa 1: definir o caminho do diretório

O primeiro passo é definir o caminho para o diretório dos seus documentos. É lá que seus documentos do Word serão armazenados e acessados.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Etapa 2: Crie o documento e o parágrafo

Em seguida, criamos um novo documento e um parágrafo dentro dele. Este parágrafo conterá o campo FieldIncludeText.

```csharp
// Crie o documento e o parágrafo.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Etapa 3: Inserir campo FieldIncludeText

Agora, inserimos o campo FieldIncludeText no parágrafo. Este campo permite incluir o texto de outro documento.

```csharp
// Inserir campo FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Etapa 4: definir propriedades do campo

Precisamos especificar as propriedades do campo FieldIncludeText. Isso inclui definir o nome do marcador e o caminho completo do documento de origem.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Etapa 5: Anexar parágrafo ao documento

Com o campo configurado, acrescentamos o parágrafo ao corpo da primeira seção do documento.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Etapa 6: Atualizar campo

Antes de salvar o documento, precisamos atualizar o FieldIncludeText para garantir que ele extraia o conteúdo correto do documento de origem.

```csharp
fieldIncludeText.Update();
```

## Etapa 7: Salve o documento

Por fim, salvamos o documento no diretório especificado.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Conclusão

E pronto! Seguindo estes passos, você pode inserir facilmente um FieldIncludeText sem usar o DocumentBuilder no Aspose.Words para .NET. Essa abordagem oferece uma maneira simplificada de incluir conteúdo de um documento em outro, simplificando muito suas tarefas de automação de documentos.

## Perguntas frequentes

### O que é Aspose.Words para .NET?  
Aspose.Words para .NET é uma biblioteca poderosa para trabalhar com documentos do Word em aplicativos .NET. Ela permite criar, editar e converter documentos programaticamente.

### Por que usar FieldIncludeText?  
FieldIncludeText é útil para incluir dinamicamente conteúdo de um documento em outro, permitindo documentos mais modulares e fáceis de manter.

### Posso usar esse método para incluir texto de outros formatos de arquivo?  
FieldIncludeText funciona especificamente com documentos do Word. Para outros formatos, você pode precisar de métodos ou classes diferentes fornecidos pelo Aspose.Words.

### Aspose.Words para .NET é compatível com o .NET Core?  
Sim, o Aspose.Words para .NET oferece suporte ao .NET Framework, .NET Core e .NET 5/6.

### Como posso obter uma avaliação gratuita do Aspose.Words para .NET?  
Você pode obter um teste gratuito em [aqui](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}