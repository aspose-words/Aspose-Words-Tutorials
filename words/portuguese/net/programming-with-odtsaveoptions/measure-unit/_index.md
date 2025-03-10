---
title: Unidade de Medida
linktitle: Unidade de Medida
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a configurar o recurso de unidade de medida no Aspose.Words para .NET para preservar a formatação do documento durante a conversão ODT.
weight: 10
url: /pt/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Unidade de Medida

## Introdução

Você já precisou converter seus documentos do Word para formatos diferentes, mas precisava de uma unidade de medida específica para seu layout? Não importa se você está lidando com polegadas, centímetros ou pontos, garantir que seu documento mantenha sua integridade durante o processo de conversão é crucial. Neste tutorial, mostraremos como configurar o recurso de unidade de medida no Aspose.Words para .NET. Esse recurso poderoso garante que a formatação do seu documento seja preservada exatamente como você precisa ao converter para o formato ODT (Open Document Text).

## Pré-requisitos

Antes de mergulhar no código, há algumas coisas que você precisa saber para começar:

1. Aspose.Words para .NET: Certifique-se de ter a versão mais recente do Aspose.Words para .NET instalada. Se você ainda não a tem, você pode baixá-la em[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: um IDE como o Visual Studio para escrever e executar seu código C#.
3. Conhecimento básico de C#: entender os conceitos básicos de C# ajudará você a acompanhar o tutorial.
4. Um documento do Word: tenha um documento de exemplo do Word pronto que você pode usar para conversão.

## Importar namespaces

Antes de começarmos a codificar, vamos nos certificar de que importamos os namespaces necessários. Adicione estas diretivas using no topo do seu arquivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa definir o caminho para o diretório do seu documento. É aqui que seu documento do Word está localizado e onde o arquivo convertido será salvo.

```csharp
// Caminho para o diretório dos seus documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Substituir`"YOUR DOCUMENTS DIRECTORY"` com o caminho real para seu diretório. Isso garante que seu código saiba onde encontrar seu documento do Word.

## Etapa 2: Carregue o documento do Word

 Em seguida, você precisa carregar o documento do Word que deseja converter. Isso é feito usando o`Document` classe do Aspose.Words.

```csharp
// Carregue o documento do Word
Document doc = new Document(dataDir + "Document.docx");
```

Certifique-se de que seu documento do Word, chamado "Documento.docx", esteja presente no diretório especificado.

## Etapa 3: Configurar a unidade de medida

 Agora, vamos configurar a unidade de medida para a conversão ODT. É aqui que a mágica acontece. Vamos configurar o`OdtSaveOptions` usar polegadas como unidade de medida.

```csharp
// Configuração de opções de backup com o recurso "Unidade de medida"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 Neste exemplo, estamos definindo a unidade de medida para polegadas. Você também pode escolher outras unidades, como`OdtSaveMeasureUnit.Centimeters` ou`OdtSaveMeasureUnit.Points` dependendo de suas necessidades.

## Etapa 4: converter o documento para ODT

 Por fim, converteremos o documento do Word para o formato ODT usando o formato configurado`OdtSaveOptions`.

```csharp
// Converter o documento para ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Esta linha de código salva o documento convertido no diretório especificado com a nova unidade de medida aplicada.

## Conclusão

aí está! Seguindo esses passos, você pode configurar facilmente o recurso de unidade de medida no Aspose.Words for .NET para garantir que o layout do seu documento seja preservado durante a conversão. Não importa se você está trabalhando com polegadas, centímetros ou pontos, este tutorial mostrou como assumir o controle da formatação do seu documento com facilidade.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words for .NET é uma biblioteca poderosa para trabalhar com documentos do Word programaticamente. Ela permite que desenvolvedores criem, modifiquem, convertam e processem documentos do Word sem precisar do Microsoft Word.

### Posso usar outras unidades de medida além de polegadas?
 Sim, o Aspose.Words for .NET suporta outras unidades de medida, como centímetros e pontos. Você pode especificar a unidade desejada usando o`OdtSaveMeasureUnit` enumeração.

### Existe uma versão de avaliação gratuita disponível para o Aspose.Words para .NET?
 Sim, você pode baixar uma versão de avaliação gratuita do Aspose.Words para .NET em[aqui](https://releases.aspose.com/).

### Onde posso encontrar documentação do Aspose.Words para .NET?
 Você pode acessar a documentação abrangente do Aspose.Words para .NET em[este link](https://reference.aspose.com/words/net/).

### Como posso obter suporte para o Aspose.Words para .NET?
 Para obter suporte, você pode visitar o fórum Aspose.Words em[este link](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
