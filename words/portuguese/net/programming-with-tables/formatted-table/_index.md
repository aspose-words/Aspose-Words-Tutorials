---
title: Tabela formatada
linktitle: Tabela formatada
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a criar e formatar tabelas em documentos do Word usando o Aspose.Words para .NET com este guia passo a passo detalhado.
weight: 10
url: /pt/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabela formatada

## Introdução

Criar e formatar tabelas em documentos do Word programaticamente pode parecer uma tarefa assustadora, mas com o Aspose.Words para .NET, isso se torna simples e gerenciável. Neste tutorial, mostraremos como criar uma tabela formatada em um documento do Word usando o Aspose.Words para .NET. Abordaremos tudo, desde a configuração do seu ambiente até salvar seu documento com uma tabela lindamente formatada.

## Pré-requisitos

Antes de mergulhar no código, vamos ter certeza de que você tem tudo o que precisa:

1. Biblioteca Aspose.Words para .NET: Baixe em[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Um IDE como o Visual Studio.
3. .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.

## Importar namespaces

Antes de escrever o código real, você precisa importar os namespaces necessários:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa definir o caminho onde seu documento será salvo.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real onde você deseja salvar o documento.

## Etapa 2: inicializar o documento e o DocumentBuilder

Agora, inicialize um novo documento e um objeto DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 O`DocumentBuilder` é uma classe auxiliar que simplifica o processo de construção de documentos.

## Etapa 3: Inicie a tabela

 Em seguida, comece a criar a tabela usando o`StartTable` método.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

É necessário inserir uma célula para iniciar a tabela.

## Etapa 4: aplicar formatação em toda a tabela

Você pode aplicar formatação que afeta a tabela inteira. Por exemplo, definindo o recuo esquerdo:

```csharp
table.LeftIndent = 20.0;
```

## Etapa 5: formatar a linha de cabeçalho

Defina a altura, o alinhamento e outras propriedades para a linha de cabeçalho.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Nesta etapa, fazemos com que a linha de cabeçalho se destaque definindo uma cor de fundo, tamanho de fonte e alinhamento.

## Etapa 6: Insira células de cabeçalho adicionais

Insira mais células para a linha de cabeçalho:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Etapa 7: formatar as linhas do corpo

Depois de configurar o cabeçalho, formate o corpo da tabela:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Etapa 8: Insira as linhas do corpo

Insira as linhas do corpo com o conteúdo:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Repita para as carreiras adicionais:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Etapa 9: Salve o documento

Por fim, salve o documento no diretório especificado:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Isso criará e salvará um documento do Word com a tabela formatada.

## Conclusão

E aí está! Seguindo esses passos, você pode criar uma tabela bem formatada em um documento do Word usando o Aspose.Words para .NET. Essa biblioteca poderosa facilita a manipulação programática de documentos do Word, economizando tempo e esforço.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa para criar, editar e converter documentos do Word programaticamente.

### Posso usar cores diferentes para linhas diferentes?
Sim, você pode aplicar formatações diferentes, incluindo cores, a diferentes linhas ou células.

### O Aspose.Words para .NET é gratuito?
 Aspose.Words para .NET é uma biblioteca paga, mas você pode obter uma[teste gratuito](https://releases.aspose.com/).

### Como obtenho suporte para o Aspose.Words para .NET?
 Você pode obter suporte do[Fóruns da comunidade Aspose](https://forum.aspose.com/c/words/8).

### Posso criar outros tipos de documentos com o Aspose.Words para .NET?
Sim, o Aspose.Words para .NET suporta vários formatos de documento, incluindo PDF, HTML e TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
