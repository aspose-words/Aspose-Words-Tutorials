---
title: Vincular SDT à parte XML personalizada
linktitle: Vincular SDT à parte XML personalizada
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como vincular Marcadores de Documento Estruturados (SDTs) a Partes XML Personalizadas em documentos do Word usando o Aspose.Words para .NET com este tutorial passo a passo.
weight: 10
url: /pt/net/programming-with-sdt/bind-sdt-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vincular SDT à parte XML personalizada

## Introdução

Criar documentos dinâmicos do Word que interagem com dados XML personalizados pode aumentar significativamente a flexibilidade e a funcionalidade dos seus aplicativos. O Aspose.Words para .NET fornece recursos robustos para vincular Structured Document Tags (SDTs) a Custom XML Parts, permitindo que você crie documentos que exibam dados dinamicamente. Neste tutorial, vamos orientá-lo no processo de vinculação de um SDT a um Custom XML Part passo a passo. Vamos mergulhar!

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes pré-requisitos em vigor:

-  Aspose.Words para .NET: Você pode baixar a versão mais recente em[Lançamentos do Aspose.Words para .NET](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE .NET compatível.
- Noções básicas de C#: Familiaridade com a linguagem de programação C# e o framework .NET.

## Importar namespaces

Para usar o Aspose.Words para .NET efetivamente, você precisa importar os namespaces necessários para o seu projeto. Adicione as seguintes diretivas using no topo do seu arquivo de código:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Saving;
```

Vamos dividir o processo em etapas gerenciáveis para torná-lo mais fácil de seguir. Cada etapa cobrirá uma parte específica da tarefa.

## Etapa 1: Inicializar o documento

Primeiro, você precisa criar um novo documento e configurar o ambiente.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializar um novo documento
Document doc = new Document();
```

Nesta etapa, estamos inicializando um novo documento que conterá nossos dados XML personalizados e o SDT.

## Etapa 2: Adicionar uma parte XML personalizada

Em seguida, adicionamos uma Custom XML Part ao documento. Esta parte conterá os dados XML que queremos vincular ao SDT.

```csharp
// Adicionar uma parte XML personalizada ao documento
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(Guid.NewGuid().ToString("B"), "<root><text>Hello, World!</text></root>");
```

Aqui, criamos uma nova parte XML personalizada com um identificador exclusivo e adicionamos alguns dados XML de amostra.

## Etapa 3: Crie uma tag de documento estruturado (SDT)

Depois de adicionar a parte XML personalizada, criamos um SDT para exibir os dados XML.

```csharp
//Crie uma tag de documento estruturado (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Block);
doc.FirstSection.Body.AppendChild(sdt);
```

Criamos um SDT do tipo PlainText e o anexamos à primeira seção do corpo do documento.

## Etapa 4: vincular o SDT à parte XML personalizada

Agora, vinculamos o SDT à parte XML personalizada usando uma expressão XPath.

```csharp
// Vincular o SDT à parte XML personalizada
sdt.XmlMapping.SetMapping(xmlPart, "/root[1]/text[1]", "");
```

 Esta etapa mapeia o SDT para o`<text>` elemento dentro do`<root>` nó da nossa parte XML personalizada.

## Etapa 5: Salve o documento

Por fim, salvamos o documento no diretório especificado.

```csharp
// Salvar o documento
doc.Save(dataDir + "WorkingWithSdt.BindSDTtoCustomXmlPart.doc");
```

Este comando salva o documento com o SDT vinculado no diretório designado.

## Conclusão

Parabéns! Você vinculou com sucesso um SDT a uma Custom XML Part usando o Aspose.Words para .NET. Esse recurso poderoso permite que você crie documentos dinâmicos que podem ser facilmente atualizados com novos dados simplesmente modificando o conteúdo XML. Não importa se você está gerando relatórios, criando modelos ou automatizando fluxos de trabalho de documentos, o Aspose.Words para .NET oferece as ferramentas necessárias para tornar suas tarefas mais fáceis e eficientes.

## Perguntas frequentes

### O que é uma etiqueta de documento estruturado (SDT)?
Uma Structured Document Tag (SDT) é um elemento de controle de conteúdo em documentos do Word que pode ser usado para vincular dados dinâmicos, tornando os documentos interativos e orientados por dados.

### Posso vincular vários SDTs a diferentes partes XML em um único documento?
Sim, você pode vincular vários SDTs a diferentes partes XML no mesmo documento, permitindo modelos complexos baseados em dados.

### Como atualizo os dados XML na parte XML personalizada?
 Você pode atualizar os dados XML acessando o`CustomXmlPart` objeto e modificando seu conteúdo XML diretamente.

### É possível vincular SDTs a atributos XML em vez de elementos?
Sim, você pode vincular SDTs a atributos XML especificando a expressão XPath apropriada que tenha como alvo o atributo desejado.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
 Você pode encontrar documentação abrangente sobre Aspose.Words para .NET em[Documentação Aspose.Words](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
