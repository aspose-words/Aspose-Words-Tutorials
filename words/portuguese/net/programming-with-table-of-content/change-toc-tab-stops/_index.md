---
title: Alterar tabulações de índice em documento do Word
linktitle: Alterar tabulações de índice em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como alterar as paradas de tabulação do TOC em documentos do Word usando o Aspose.Words para .NET. Este guia passo a passo ajudará você a criar um Índice de aparência profissional.
weight: 10
url: /pt/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alterar tabulações de índice em documento do Word

## Introdução

Já se perguntou como dar um toque especial ao Índice (TOC) em seus documentos do Word? Talvez você queira que essas paradas de tabulação se alinhem perfeitamente para aquele toque profissional. Você está no lugar certo! Hoje, estamos nos aprofundando em como você pode alterar as paradas de tabulação do TOC usando o Aspose.Words para .NET. Continue por aqui, e eu prometo que você sairá com todo o conhecimento para fazer seu TOC parecer elegante e organizado.

## Pré-requisitos

Antes de começar, vamos garantir que você tenha tudo o que precisa:

1.  Aspose.Words para .NET: Você pode[baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer IDE compatível com C#.
3. Um documento do Word: especificamente, um que contém um índice.

Entendeu tudo isso? Incrível! Vamos lá.

## Importar namespaces

Primeiro, você precisará importar os namespaces necessários. Isso é como empacotar suas ferramentas antes de começar um projeto.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Vamos dividir esse processo em etapas simples e digeríveis. Passaremos pelo carregamento do documento, modificando as paradas de tabulação do TOC e salvando o documento atualizado.

## Etapa 1: Carregue o documento

Por quê? Precisamos acessar o documento do Word que contém o TOC que queremos modificar.

Como? Aqui está um trecho de código simples para você começar:

```csharp
// Caminho para o diretório dos seus documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Carregue o documento contendo o índice
Document doc = new Document(dataDir + "Table of contents.docx");
```

Imagine que seu documento é como um bolo, e estamos prestes a adicionar um pouco de cobertura. O primeiro passo é tirar esse bolo da caixa.

## Etapa 2: Identifique os parágrafos do TOC

Por quê? Precisamos identificar os parágrafos que compõem o TOC. 

Como? Faça um loop pelos parágrafos e verifique seus estilos:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Parágrafo TOC encontrado
    }
}
```

Pense nisso como escanear uma multidão para encontrar seus amigos. Aqui, estamos procurando por parágrafos estilizados como entradas de TOC.

## Etapa 3: Modifique as paradas de tabulação

Por quê? É aqui que a mágica acontece. Alterar paradas de tabulação dá ao seu TOC uma aparência mais limpa.

Como? Remova a parada de tabulação existente e adicione uma nova em uma posição modificada:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

É como ajustar os móveis da sua sala de estar até que pareçam perfeitos. Estamos ajustando essas paradas de tabulação para a perfeição.

## Etapa 4: Salve o documento modificado

Por quê? Para garantir que todo o seu trabalho duro seja salvo e possa ser visualizado ou compartilhado.

Como? Salve o documento com um novo nome para manter o original intacto:

```csharp
// Salvar o documento modificado
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

E voilà! Seu TOC agora tem as paradas de tabulação exatamente onde você quer.

## Conclusão

Alterar as paradas de tabulação do TOC em um documento do Word usando o Aspose.Words para .NET é simples quando você o divide. Ao carregar seu documento, identificar os parágrafos do TOC, modificar as paradas de tabulação e salvar o documento, você pode obter uma aparência polida e profissional. Lembre-se, a prática leva à perfeição, então continue experimentando diferentes posições de paradas de tabulação para obter o layout exato que você deseja.

## Perguntas frequentes

### Posso modificar paradas de tabulação para diferentes níveis de índice separadamente?
Sim, você pode! Basta verificar cada nível específico de TOC (Toc1, Toc2, etc.) e ajustar de acordo.

### E se meu documento tiver vários TOCs?
O código verifica todos os parágrafos no estilo TOC, então ele modificará todos os TOCs presentes no documento.

### É possível adicionar várias paradas de tabulação em uma entrada do sumário?
 Claro! Você pode adicionar quantas paradas de tabulação forem necessárias ajustando o`para.ParagraphFormat.TabStops` coleção.

### Posso alterar o alinhamento da parada de tabulação e o estilo do líder?
Sim, você pode especificar diferentes alinhamentos e estilos de guia ao adicionar uma nova parada de tabulação.

### Preciso de uma licença para usar o Aspose.Words para .NET?
 Sim, você precisa de uma licença válida para usar o Aspose.Words for .NET além do período de teste. Você pode obter uma[licença temporária](https://purchase.aspose.com/temporary-license/) ou[compre um](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
