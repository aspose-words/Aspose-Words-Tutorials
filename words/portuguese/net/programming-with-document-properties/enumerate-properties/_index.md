---
title: Enumerar Propriedades
linktitle: Enumerar Propriedades
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como enumerar propriedades em um documento do Word usando Aspose.Words para .NET com este guia passo a passo. Perfeito para desenvolvedores de todos os níveis de habilidade.
weight: 10
url: /pt/net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enumerar Propriedades

## Introdução

Procurando trabalhar com documentos do Word programaticamente? O Aspose.Words para .NET é uma ferramenta poderosa que pode ajudar você a conseguir exatamente isso. Hoje, vou mostrar como enumerar propriedades de um documento do Word usando o Aspose.Words para .NET. Seja você iniciante ou tenha alguma experiência, este guia vai detalhar passo a passo de uma forma coloquial e fácil de seguir.

## Pré-requisitos

Antes de começarmos o tutorial, há algumas coisas que você precisa saber para começar:

-  Aspose.Words para .NET: Você pode[baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: o Visual Studio é recomendado, mas você pode usar qualquer IDE C#.
- Conhecimento básico de C#: Uma compreensão fundamental de C# ajudará você a acompanhar.

Agora, vamos direto ao assunto!

## Etapa 1: Configurando seu projeto

Primeiramente, você precisa configurar seu projeto no Visual Studio.

1. Criar um novo projeto: Abra o Visual Studio e crie um novo projeto de aplicativo de console.
2. Instalar Aspose.Words para .NET: Use o NuGet Package Manager para instalar o Aspose.Words para .NET. Clique com o botão direito do mouse no seu projeto no Solution Explorer, selecione "Manage NuGet Packages" e pesquise por "Aspose.Words". Instale o pacote.

## Etapa 2: Importar namespaces

Para trabalhar com Aspose.Words, você precisa importar os namespaces necessários. Adicione o seguinte no topo do seu arquivo Program.cs:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## Etapa 3: Carregue seu documento

Em seguida, vamos carregar o documento do Word com o qual você quer trabalhar. Para este exemplo, usaremos um documento chamado "Properties.docx" localizado no diretório do seu projeto.

1. Definir o caminho do documento: especifique o caminho para o seu documento.
2.  Carregue o documento: use o Aspose.Words`Document` classe para carregar o documento.

Aqui está o código:

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## Etapa 4: Exibir nome do documento

Depois que seu documento for carregado, você pode querer exibir seu nome. Aspose.Words fornece uma propriedade para isso:

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## Etapa 5: Enumerar propriedades integradas

Propriedades incorporadas são propriedades de metadados predefinidas pelo Microsoft Word. Elas incluem título, autor e mais.

1.  Acessar propriedades integradas: use o`BuiltInDocumentProperties` coleção.
2. Percorrer propriedades: itere pelas propriedades e exiba seus nomes e valores.

Aqui está o código:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Etapa 6: Enumerar propriedades personalizadas

Propriedades personalizadas são propriedades de metadados definidas pelo usuário. Elas podem ser qualquer coisa que você queira adicionar ao seu documento.

1.  Acessar propriedades personalizadas: use o`CustomDocumentProperties` coleção.
2. Percorrer propriedades: itere pelas propriedades e exiba seus nomes e valores.

Aqui está o código:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Conclusão

aí está! Você enumerou com sucesso propriedades internas e personalizadas de um documento do Word usando o Aspose.Words para .NET. Esta é apenas a ponta do iceberg quando se trata do que você pode fazer com o Aspose.Words. Quer você esteja automatizando a geração de documentos ou manipulando documentos complexos, o Aspose.Words fornece um rico conjunto de recursos para tornar sua vida mais fácil.

## Perguntas frequentes

### Posso adicionar novas propriedades a um documento?
 Sim, você pode adicionar novas propriedades personalizadas usando o`CustomDocumentProperties` coleção.

### O Aspose.Words é gratuito?
 Aspose.Words oferece uma[teste gratuito](https://releases.aspose.com/) e diferente[opções de compra](https://purchase.aspose.com/buy).

### Como obtenho suporte para o Aspose.Words?
 Você pode obter suporte da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8).

### Posso usar o Aspose.Words com outras linguagens .NET?
Sim, o Aspose.Words suporta diversas linguagens .NET, incluindo VB.NET.

### Onde posso encontrar mais exemplos?
 Confira o[Aspose.Words para documentação .NET](https://reference.aspose.com/words/net/) para mais exemplos e informações detalhadas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
