---
"description": "Aprenda a ler propriedades de controles ActiveX em arquivos do Word usando o Aspose.Words para .NET em um guia passo a passo. Aprimore suas habilidades de automação de documentos."
"linktitle": "Ler propriedades do Active XControl de um arquivo do Word"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Ler propriedades do Active XControl de um arquivo do Word"
"url": "/pt/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ler propriedades do Active XControl de um arquivo do Word

## Introdução

Na era digital atual, a automação é fundamental para aumentar a produtividade. Se você estiver trabalhando com documentos do Word que contêm controles ActiveX, pode ser necessário ler suas propriedades para diversos fins. Controles ActiveX, como caixas de seleção e botões, podem conter dados importantes. Usando o Aspose.Words para .NET, você pode extrair e manipular esses dados programaticamente de forma eficiente.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. Biblioteca Aspose.Words para .NET: Você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
2. Visual Studio ou qualquer IDE C#: para escrever e executar seu código.
3. Um documento do Word com controles ActiveX: Por exemplo, "Controles ActiveX.docx".
4. Conhecimento básico de C#: É necessário ter familiaridade com programação em C# para acompanhar.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários para trabalhar com o Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Etapa 1: Carregue o documento do Word

Para começar, você precisará carregar o documento do Word que contém os controles ActiveX.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Etapa 2: Inicializar uma string para conter propriedades

Em seguida, inicialize uma string vazia para armazenar as propriedades dos controles ActiveX.

```csharp
string properties = "";
```

## Etapa 3: iterar pelas formas no documento

Precisamos iterar por todas as formas no documento para encontrar os controles ActiveX.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Processar o controle ActiveX
    }
}
```

## Etapa 4: Extrair propriedades dos controles ActiveX

Dentro do loop, verifique se o controle é um Forms2OleControl. Em caso afirmativo, faça uma conversão e extraia as propriedades.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Etapa 5: Contagem total de controles ActiveX

Depois de iterar por todas as formas, conte o número total de controles ActiveX encontrados.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Etapa 6: Exibir as propriedades

Por fim, imprima as propriedades extraídas no console.

```csharp
Console.WriteLine("\n" + properties);
```

## Conclusão

pronto! Você aprendeu com sucesso a ler propriedades de controles ActiveX de um documento do Word usando o Aspose.Words para .NET. Este tutorial abordou o carregamento de um documento, a iteração por formas e a extração de propriedades de controles ActiveX. Seguindo esses passos, você pode automatizar a extração de dados importantes dos seus documentos do Word, aumentando a eficiência do seu fluxo de trabalho.

## Perguntas frequentes

### O que são controles ActiveX em documentos do Word?
Os controles ActiveX são objetos interativos incorporados em documentos do Word, como caixas de seleção, botões e campos de texto, usados para criar formulários e automatizar tarefas.

### Posso modificar as propriedades dos controles ActiveX usando o Aspose.Words para .NET?
Sim, o Aspose.Words para .NET permite que você modifique as propriedades dos controles ActiveX programaticamente.

### O Aspose.Words para .NET é gratuito?
O Aspose.Words para .NET oferece um teste gratuito, mas você precisará adquirir uma licença para uso contínuo. Você pode obter um teste gratuito [aqui](https://releases.aspose.com/).

### Posso usar o Aspose.Words para .NET com outras linguagens .NET além de C#?
Sim, o Aspose.Words para .NET pode ser usado com qualquer linguagem .NET, incluindo VB.NET e F#.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
Você pode encontrar documentação detalhada [aqui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}