---
"description": "Aprenda a vincular dinamicamente dados XML a tags de documentos estruturados no Word usando o Aspose.Words para .NET. Siga nosso guia passo a passo."
"linktitle": "Mapeamento XML de início de intervalo de tags de documento estruturado"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Mapeamento XML de início de intervalo de tags de documento estruturado"
"url": "/pt/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mapeamento XML de início de intervalo de tags de documento estruturado

## Introdução

Você já quis inserir dados XML dinamicamente em um documento do Word? Bem, você está com sorte! O Aspose.Words para .NET torna essa tarefa muito fácil. Neste tutorial, vamos nos aprofundar no mapeamento XML de início de intervalo de tags de documento estruturado. Este recurso permite vincular partes XML personalizadas a controles de conteúdo, garantindo que o conteúdo do seu documento seja atualizado perfeitamente com seus dados XML. Pronto para transformar seus documentos em obras-primas dinâmicas.

## Pré-requisitos

Antes de começarmos a codificação, vamos garantir que você tenha tudo o que precisa:

1. Biblioteca Aspose.Words para .NET: Certifique-se de ter a versão mais recente. Você pode baixá-la [aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE que suporte C#.
3. Conhecimento básico de C#: familiaridade com programação em C# é essencial.
4. Documento do Word: Um exemplo de documento do Word para trabalhar.

## Importar namespaces

Primeiramente, vamos importar os namespaces necessários. Isso garantirá que tenhamos acesso a todas as classes e métodos necessários no Aspose.Words para .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Etapa 1: configure seu diretório de documentos

Todo projeto precisa de uma base, certo? Aqui, configuramos o caminho para o seu diretório de documentos.

```csharp
// Caminho para o diretório do seu documento 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Carregue o documento do Word

Em seguida, carregamos o documento do Word. É neste documento que inseriremos nossos dados XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Etapa 3: Adicionar parte XML personalizada

Precisamos construir uma parte XML contendo os dados que queremos inserir e adicioná-la à coleção CustomXmlPart do documento. Essa parte XML personalizada servirá como fonte de dados para nossas tags de documento estruturadas.

### Criando uma parte XML

Primeiro, gere um ID exclusivo para a parte XML e defina seu conteúdo.

```csharp
// Crie uma parte XML que contenha dados e adicione-a à coleção CustomXmlPart do documento.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verifique o conteúdo da parte XML

Para garantir que a parte XML seja adicionada corretamente, imprimimos seu conteúdo.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Etapa 4: Criar uma tag de documento estruturado

Uma Tag de Documento Estruturada (SDT) é um controle de conteúdo que pode ser vinculado a uma parte XML. Aqui, criamos uma SDT que exibirá o conteúdo da nossa parte XML personalizada.

Primeiro, localize o início do intervalo SDT no documento.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Etapa 5: definir o mapeamento XML para o SDT

Agora, é hora de vincular nossa parte XML ao SDT. Ao definir um mapeamento XML, especificamos qual parte dos dados XML deve ser exibida no SDT.

O XPath aponta para o elemento específico na parte XML que queremos exibir. Aqui, apontamos para o segundo `<text>` elemento dentro do `<root>` elemento.

```csharp
// Defina um mapeamento para nossa StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Etapa 6: Salve o documento

Por fim, salve o documento para ver as alterações em ação. O SDT no documento do Word agora exibirá o conteúdo XML especificado.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusão

pronto! Você mapeou com sucesso uma parte XML para uma tag de documento estruturada em um documento do Word usando o Aspose.Words para .NET. Este poderoso recurso permite que você crie documentos dinâmicos e baseados em dados sem esforço. Seja para gerar relatórios, faturas ou qualquer outro tipo de documento, o mapeamento XML pode otimizar significativamente seu fluxo de trabalho.

## Perguntas frequentes

### O que é uma tag de documento estruturada no Word?
Marcas de documentos estruturadas, também conhecidas como controles de conteúdo, são contêineres para tipos específicos de conteúdo em documentos do Word. Elas podem ser usadas para vincular dados, restringir a edição ou orientar os usuários na criação de documentos.

### Como posso atualizar o conteúdo da parte XML dinamicamente?
Você pode atualizar o conteúdo da parte XML modificando o `xmlPartContent` string antes de adicioná-la ao documento. Basta atualizar a string com os novos dados e adicioná-la ao `CustomXmlParts` coleção.

### Posso vincular várias partes XML a diferentes SDTs no mesmo documento?
Sim, você pode vincular várias partes XML a diferentes SDTs no mesmo documento. Cada SDT pode ter sua própria parte XML e mapeamento XPath.

### É possível mapear estruturas XML complexas para SDTs?
Com certeza! Você pode mapear estruturas XML complexas para SDTs usando expressões XPath detalhadas que apontam com precisão para os elementos desejados dentro da parte XML.

### Como posso remover uma parte XML de um documento?
Você pode remover uma parte XML chamando o `Remove` método sobre o `CustomXmlParts` coleta, passando o `xmlPartId` da parte XML que você deseja remover.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}