---
title: Formatar tabela e célula com bordas diferentes
linktitle: Formatar tabela e célula com bordas diferentes
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a formatar tabelas e células com bordas diferentes usando o Aspose.Words para .NET. Aprimore seus documentos do Word com estilos de tabela e sombreamento de células personalizados.
weight: 10
url: /pt/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatar tabela e célula com bordas diferentes

## Introdução

Você já tentou fazer seus documentos do Word parecerem mais profissionais personalizando as bordas de tabelas e células? Se não, você está em uma surpresa! Este tutorial irá guiá-lo pelo processo de formatação de tabelas e células com bordas diferentes usando o Aspose.Words para .NET. Imagine ter o poder de mudar a aparência de suas tabelas com apenas algumas linhas de código. Intrigado? Vamos mergulhar e explorar como você pode conseguir isso com facilidade.

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes pré-requisitos em vigor:
- Uma compreensão básica da programação em C#.
- Visual Studio instalado no seu computador.
-  Biblioteca Aspose.Words para .NET. Se você ainda não instalou, você pode baixá-la[aqui](https://releases.aspose.com/words/net/).
-  Uma licença Aspose válida. Você pode obter uma avaliação gratuita ou uma licença temporária em[aqui](https://purchase.aspose.com/temporary-license/).

## Importar namespaces

Para trabalhar com Aspose.Words para .NET, você precisa importar os namespaces necessários para o seu projeto. Adicione as seguintes diretivas using no topo do seu arquivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Etapa 1: inicializar o documento e o DocumentBuilder

Primeiro, você precisa criar um novo documento e inicializar o DocumentBuilder, que ajuda a construir o conteúdo do documento. 

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Comece a criar uma tabela

Em seguida, use o DocumentBuilder para começar a criar uma tabela e inserir a primeira célula.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Etapa 3: Definir bordas da tabela

Defina as bordas para a tabela inteira. Esta etapa garante que todas as células dentro da tabela tenham um estilo de borda consistente, a menos que especificado de outra forma.

```csharp
// Defina as bordas para a tabela inteira.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Etapa 4: aplicar sombreamento de célula

Aplique sombreamento às células para torná-las visualmente distintas. Neste exemplo, definiremos a cor de fundo da primeira célula como vermelho.


```csharp
// Defina o sombreamento desta célula.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Etapa 5: Insira outra célula com sombreamento diferente

Insira a segunda célula e aplique uma cor de sombreamento diferente. Isso torna a tabela mais colorida e fácil de ler.

```csharp
builder.InsertCell();
// Especifique um sombreamento de célula diferente para a segunda célula.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Etapa 6: Limpar formatação de célula

Limpe a formatação de células de operações anteriores para garantir que as próximas células não herdem os mesmos estilos.


```csharp
// Limpe a formatação de células de operações anteriores.
builder.CellFormat.ClearFormatting();
```

## Etapa 7: personalizar bordas para células específicas

Personalize as bordas para células específicas para destacá-las. Aqui, definiremos bordas maiores para a primeira célula da nova linha.

```csharp
builder.InsertCell();
// Crie bordas maiores para a primeira célula desta linha. Isso será diferente
// comparado com as bordas definidas para a tabela.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Etapa 8: Insira a célula final

Insira a célula final e certifique-se de que sua formatação esteja limpa, para que ela use os estilos padrão da tabela.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Etapa 9: Salve o documento

Por fim, salve o documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Conclusão

E aí está! Você acabou de aprender como formatar tabelas e células com bordas diferentes usando o Aspose.Words para .NET. Ao personalizar bordas de tabela e sombreamento de células, você pode melhorar significativamente o apelo visual dos seus documentos. Então vá em frente, experimente estilos diferentes e faça seus documentos se destacarem!

## Perguntas frequentes

### Posso usar estilos de borda diferentes para cada célula?
 Sim, você pode definir diferentes estilos de borda para cada célula usando o`CellFormat.Borders` propriedade.

### Como posso remover todas as bordas de uma tabela?
 Você pode remover todas as bordas definindo o estilo da borda como`LineStyle.None`.

### É possível definir cores de borda diferentes para cada célula?
 Absolutamente! Você pode personalizar a cor da borda para cada célula usando o`CellFormat.Borders.Color` propriedade.

### Posso usar imagens como planos de fundo de células?
Embora o Aspose.Words não suporte diretamente imagens como planos de fundo de células, você pode inserir uma imagem em uma célula e ajustar seu tamanho para cobrir a área da célula.

### Como faço para mesclar células em uma tabela?
 Você pode mesclar células usando o`CellFormat.HorizontalMerge` e`CellFormat.VerticalMerge` propriedades.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
