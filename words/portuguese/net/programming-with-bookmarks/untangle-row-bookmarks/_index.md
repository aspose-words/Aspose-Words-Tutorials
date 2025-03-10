---
title: Desembaraçar marcadores de linha em documento do Word
linktitle: Desembaraçar marcadores de linha em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Desembarace marcadores de linhas emaranhados em seus documentos do Word com facilidade usando Aspose.Words for .NET. Este guia orienta você no processo para um gerenciamento de favoritos mais limpo e seguro.
weight: 10
url: /pt/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Desembaraçar marcadores de linha em documento do Word

## Introdução

Você já se deparou com uma situação em que a exclusão de uma linha em um documento do Word por um marcador atrapalha outros marcadores em linhas adjacentes? Isto pode ser extremamente frustrante, especialmente quando se lida com tabelas complexas. Felizmente, Aspose.Words for .NET oferece uma solução poderosa: desemaranhar marcadores de linha. 

Este guia irá orientá-lo no processo de desemaranhar marcadores de linha em seus documentos do Word usando Aspose.Words for .NET. Dividiremos o código em etapas fáceis de entender e explicaremos a finalidade de cada função, capacitando você a resolver esses incômodos problemas de marcadores com confiança.

## Pré-requisitos

Antes de mergulhar, você precisará de algumas coisas:

1.  Aspose.Words for .NET: Esta biblioteca comercial oferece funcionalidades para trabalhar com documentos do Word de forma programática. 2. Você pode baixar uma avaliação gratuita em[link para baixar](https://releases.aspose.com/words/net/) ou compre uma licença de[comprar](https://purchase.aspose.com/buy).
3. Ambiente de desenvolvimento AC#: Visual Studio ou qualquer outro IDE C# funcionará perfeitamente.
4. Um documento do Word com marcadores de linha: usaremos um documento de exemplo denominado "Marcadores de coluna da tabela.docx" para fins de demonstração.

## Importar namespaces

A primeira etapa envolve a importação dos namespaces necessários para o seu projeto C#. Esses namespaces fornecem acesso às classes e funcionalidades que usaremos no Aspose.Words for .NET:

```csharp
using Aspose.Words;
using System;
```

## Etapa 1: carregue o documento do Word

 Começamos carregando o documento do Word que contém os marcadores de linha emaranhados. O`Document` classe lida com a manipulação de documentos em Aspose.Words. Veja como carregar o documento:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Substitua pela localização do seu documento
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Lembre-se de substituir`"YOUR DOCUMENT DIRECTORY"` pelo caminho real para o arquivo "Table column bookmarks.docx".

## Etapa 2: desembaraçar marcadores de linha

 É aqui que a mágica acontece! O`Untangle` A função cuida de desembaraçar os marcadores de linha. Vamos detalhar sua funcionalidade:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Obtenha a linha pai do marcador e do final do marcador
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Verifique se as linhas são válidas e adjacentes
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Mover o final do marcador para o último parágrafo da última célula da linha superior
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Aqui está uma explicação passo a passo do que o código faz:

 Iteramos todos os marcadores do documento usando um`foreach` laço.
Para cada marcador, recuperamos a linha pai do início do marcador (`bookmark.BookmarkStart`) e o final do marcador (`bookmark.BookmarkEnd` ) usando o`GetAncestor` método.
Em seguida, verificamos se ambas as linhas foram encontradas (`row1 != null`e`row2 != null`) e se forem linhas adjacentes (`row1.NextSibling == row2`). Isso garante que modifiquemos apenas os marcadores que abrangem linhas adjacentes.
Se as condições forem atendidas, movemos o nó final do marcador para o final do último parágrafo na última célula da linha superior (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) desembaraçando-os efetivamente.

## Etapa 3: excluir linha por marcador

 Agora que os marcadores estão desembaraçados, podemos excluir linhas com segurança usando seus nomes de marcadores. O`DeleteRowByBookmark` função lida com esta tarefa:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Aqui está um detalhamento desta função:

Pegamos o nome do marcador (`bookmarkName`) como entrada.
 Recuperamos o objeto de marcador correspondente usando`doc.Range.Bookmarks[bookmarkName]`.
Em seguida, obtemos a linha pai do marcador que começa a usar`GetAncestor` (semelhante ao`Untangle` função).
Finalmente, verificamos se o marcador e a linha existem (`bookmark != null` e

## Etapa 4: verifique o desembaraço

 Enquanto o`Untangle` função deve garantir a segurança de outros marcadores, é sempre uma boa prática verificar. Veja como podemos verificar se o processo de desembaraço não excluiu acidentalmente o final de outro marcador:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Este trecho de código verifica se o final do marcador denominado "ROW1" ainda existe após a exclusão da linha com o marcador "ROW2". Se for nulo, uma exceção será lançada, indicando um problema no processo de desembaraço. 

## Etapa 5: salve o documento

 Finalmente, depois de desembaraçar os marcadores e potencialmente excluir linhas, salve o documento modificado usando o`Save` método:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Isso salva o documento com os marcadores desembaraçados e quaisquer linhas excluídas sob um novo nome de arquivo "WorkingWithBookmarks.UntangleRowBookmarks.docx". 

## Conclusão

 Seguindo estas etapas e utilizando o`Untangle`função, você pode desembaraçar efetivamente marcadores de linha em seus documentos do Word com Aspose.Words for .NET. Isso garante que a exclusão de linhas por marcadores não cause consequências indesejadas com outros marcadores em linhas adjacentes. Lembre-se de substituir espaços reservados como`"YOUR DOCUMENT DIRECTORY"` com seus caminhos e nomes de arquivos reais.

## Perguntas frequentes

### O Aspose.Words para .NET é gratuito?

 Aspose.Words for .NET é uma biblioteca comercial com versão de avaliação gratuita disponível. Você pode baixá-lo em[link para baixar](https://releases.aspose.com/words/net/).

### Posso desembaraçar os marcadores de linha manualmente no Word?

Embora seja tecnicamente possível, desembaraçar manualmente os favoritos no Word pode ser tedioso e sujeito a erros. Aspose.Words for .NET automatiza esse processo, economizando tempo e esforço.

###  O que acontece se o`Untangle` function encounters an error?

O código inclui um manipulador de exceções que lança uma exceção se o processo de desemaranhamento excluir acidentalmente o final de outro marcador. Você pode personalizar esse tratamento de erros para atender às suas necessidades específicas.

### Posso usar esse código para desembaraçar marcadores em linhas não adjacentes?

Atualmente, o código se concentra em desemaranhar marcadores que se estendem por linhas adjacentes. Modificar o código para lidar com linhas não adjacentes exigiria lógica adicional para identificar e lidar com esses cenários.

### Há alguma limitação para usar essa abordagem?

Essa abordagem pressupõe que os marcadores estejam bem definidos nas células da tabela. Se os marcadores forem colocados fora das células ou em locais inesperados, o processo de desembaraçar poderá não funcionar conforme o esperado.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
