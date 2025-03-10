---
title: Layout na célula
linktitle: Layout na célula
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como definir o layout na célula usando Aspose.Words para .NET com este guia abrangente. Perfeito para desenvolvedores que buscam personalizar documentos do Word.
weight: 10
url: /pt/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Layout na célula

## Introdução

Se você sempre quis ajustar o layout das células da sua tabela em documentos do Word programaticamente, você está no lugar certo. Hoje, vamos mergulhar em como definir o layout na célula usando o Aspose.Words para .NET. Vamos percorrer um exemplo prático, dividindo-o passo a passo para que você possa acompanhar com facilidade.

## Pré-requisitos

Antes de começarmos o código, vamos garantir que você tenha tudo o que precisa:

1.  Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words para .NET instalada. Se não tiver, você pode[baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: você precisará de um ambiente de desenvolvimento configurado com .NET. O Visual Studio é uma ótima escolha se você estiver procurando recomendações.
3. Conhecimento básico de C#: embora eu explique cada etapa, um conhecimento básico de C# ajudará você a acompanhar mais facilmente.
4.  Diretório de documentos: prepare um caminho de diretório onde você salvará seus documentos. Vamos nos referir a isso como`YOUR DOCUMENT DIRECTORY`.

## Importar namespaces

Para começar, certifique-se de importar os namespaces necessários no seu projeto:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Vamos dividir o processo em etapas gerenciáveis.

## Etapa 1: Crie um novo documento

 Primeiro, criaremos um novo documento do Word e inicializaremos um`DocumentBuilder` objeto para nos ajudar a construir nosso conteúdo.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: iniciar uma tabela e definir o formato da linha

Começaremos construindo uma tabela e especificaremos a altura e a regra de altura para as linhas.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Etapa 3: Insira células e preencha com conteúdo

Em seguida, fazemos um loop para inserir células na tabela. Para cada 7 células, encerraremos a linha para criar uma nova.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Etapa 4: adicione uma forma de marca d'água

 Agora, vamos adicionar uma marca d'água ao nosso documento. Vamos criar uma`Shape` objeto e definir suas propriedades.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Exiba a forma fora da célula da tabela se ela for colocada em uma célula.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Etapa 5: personalizar a aparência da marca d'água

Personalizaremos ainda mais a aparência da marca d'água definindo suas propriedades de cor e texto.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Etapa 6: Insira a marca d'água no documento

Encontraremos a última execução no documento e inseriremos a marca d'água nessa posição.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Etapa 7: otimizar o documento para o Word 2010

Para garantir a compatibilidade, otimizaremos o documento para o Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Etapa 8: Salve o documento

Por fim, salvaremos nosso documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Conclusão

E aí está! Você criou com sucesso um documento do Word com um layout de tabela personalizado e adicionou uma marca d'água usando o Aspose.Words para .NET. Este tutorial teve como objetivo fornecer um guia claro e passo a passo para ajudar você a entender cada parte do processo. Com essas habilidades, agora você pode criar documentos do Word mais sofisticados e personalizados programaticamente.

## Perguntas frequentes

### Posso usar uma fonte diferente para o texto da marca d'água?
 Sim, você pode alterar a fonte definindo o`watermark.TextPath.FontFamily` propriedade para a fonte desejada.

### Como ajusto a posição da marca d'água?
 Você pode modificar o`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , e`VerticalAlignment` propriedades para ajustar a posição da marca d'água.

### É possível usar uma imagem em vez de texto para a marca d'água?
 Absolutamente! Você pode criar um`Shape` com o tipo`ShapeType.Image` e definir sua imagem usando o`ImageData.SetImage` método.

### Posso criar tabelas com alturas de linha variadas?
Sim, você pode definir alturas diferentes para cada linha alterando o`RowFormat.Height` propriedade antes de inserir células nessa linha.

### Como faço para remover uma marca d'água do documento?
 Você pode remover a marca d'água localizando-a na coleção de formas do documento e chamando o método`Remove` método.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
