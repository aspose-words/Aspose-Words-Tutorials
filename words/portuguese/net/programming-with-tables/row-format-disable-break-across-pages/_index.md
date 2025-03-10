---
title: Formato de linha Desabilitar quebra entre páginas
linktitle: Formato de linha Desabilitar quebra entre páginas
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como desabilitar quebras de linha entre páginas em documentos do Word usando o Aspose.Words para .NET para manter a legibilidade e a formatação da tabela.
weight: 10
url: /pt/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formato de linha Desabilitar quebra entre páginas

## Introdução

Ao trabalhar com tabelas em documentos do Word, você pode querer garantir que as linhas não quebrem entre as páginas, o que pode ser essencial para manter a legibilidade e a formatação dos seus documentos. O Aspose.Words para .NET fornece uma maneira fácil de desabilitar quebras de linha entre páginas.

Neste tutorial, mostraremos a você o processo de desabilitação de quebras de linha em páginas de um documento do Word usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes pré-requisitos:
- Biblioteca Aspose.Words para .NET instalada.
- Um documento do Word com uma tabela que abrange várias páginas.

## Importar namespaces

Primeiro, importe os namespaces necessários no seu projeto:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Etapa 1: Carregue o documento

Carregue o documento que contém a tabela que abrange várias páginas.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Etapa 2: Acesse a tabela

Acesse a primeira tabela no documento. Isso pressupõe que a tabela que você deseja modificar seja a primeira tabela no documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Etapa 3: Desabilite a quebra entre páginas para todas as linhas

 Faça um loop em cada linha da tabela e defina o`AllowBreakAcrossPages`propriedade para`false`. Isso garante que as linhas não sejam quebradas nas páginas.

```csharp
// Desabilite a quebra entre páginas para todas as linhas da tabela.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Etapa 4: Salve o documento

Salve o documento modificado no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusão

Neste tutorial, demonstramos como desabilitar quebras de linha entre páginas em um documento do Word usando o Aspose.Words para .NET. Seguindo as etapas descritas acima, você pode garantir que as linhas da sua tabela permaneçam intactas e não se dividam entre páginas, mantendo a legibilidade e a formatação do documento.

## Perguntas frequentes

### Posso desabilitar quebras de linha entre páginas para uma linha específica em vez de todas as linhas?  
 Sim, você pode desabilitar quebras de linha para linhas específicas acessando a linha desejada e definindo sua`AllowBreakAcrossPages`propriedade para`false`.

### Esse método funciona para tabelas com células mescladas?  
 Sim, esse método funciona para tabelas com células mescladas. A propriedade`AllowBreakAcrossPages` aplica-se à linha inteira, independentemente da mesclagem de células.

### Este método funcionará se a tabela estiver aninhada dentro de outra tabela?  
Sim, você pode acessar e modificar tabelas aninhadas da mesma forma. Certifique-se de referenciar corretamente a tabela aninhada por seu índice ou outras propriedades.

### Como posso verificar se uma linha permite quebra entre páginas?  
 Você pode verificar se uma linha permite quebra entre páginas acessando o`AllowBreakAcrossPages` propriedade do`RowFormat` e verificar seu valor.

### Existe uma maneira de aplicar essa configuração a todas as tabelas de um documento?  
Sim, você pode percorrer todas as tabelas do documento e aplicar essa configuração a cada uma delas.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
