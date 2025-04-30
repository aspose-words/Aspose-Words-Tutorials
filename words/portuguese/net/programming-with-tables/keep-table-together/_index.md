---
"description": "Aprenda a evitar que tabelas se quebrem entre páginas em documentos do Word usando o Aspose.Words para .NET. Siga nosso guia para manter documentos profissionais e legíveis."
"linktitle": "Mantenha a mesa junta"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Mantenha a mesa junta"
"url": "/pt/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mantenha a mesa junta

## Introdução

Já se sentiu frustrado quando uma tabela no seu documento do Word se divide em duas páginas? É como se suas informações cuidadosamente organizadas de repente tivessem decidido fazer uma pausa no meio do caminho! Manter as tabelas juntas em uma página é crucial para a legibilidade e a apresentação. Seja para um relatório, uma proposta de projeto ou apenas um documento pessoal, ter tabelas divididas pode ser bastante desagradável. Para nossa sorte, o Aspose.Words para .NET tem uma maneira bacana de resolver esse problema. Neste tutorial, mostraremos os passos para manter suas tabelas intactas e com uma aparência impecável. Vamos lá!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. Aspose.Words para .NET - Se você ainda não o instalou, pode baixá-lo em [aqui](https://releases.aspose.com/words/net/).
2. Um documento do Word com uma tabela - Trabalharemos com um documento de exemplo que tem uma tabela abrangendo várias páginas.
3. Conhecimento básico de C# - Este tutorial pressupõe que você tenha um conhecimento básico de programação em C#.

## Importar namespaces

Primeiramente, vamos importar os namespaces necessários. Isso nos dará acesso às classes e métodos necessários do Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Vamos dividir o processo em etapas fáceis e de fácil assimilação. Começaremos carregando nosso documento e terminaremos salvando o documento atualizado, onde a tabela permanece unida.

## Etapa 1: Carregue o documento

Para trabalhar com um documento do Word, primeiro precisamos carregá-lo. Usaremos o `Document` classe para isso.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Etapa 2: Acesse a tabela

Em seguida, precisamos obter a tabela que queremos manter unida. Vamos supor que seja a primeira tabela do documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Etapa 3: defina KeepWithNext para parágrafos

Para evitar que a tabela se quebre entre as páginas, precisamos definir o `KeepWithNext` propriedade para cada parágrafo na tabela, exceto para os últimos parágrafos na última linha.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Etapa 4: Salve o documento

Por fim, salvamos o documento atualizado. Isso aplicará nossas alterações e garantirá que a tabela permaneça unida em uma única página.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusão

E pronto! Com apenas algumas linhas de código, você pode evitar que suas tabelas se dividam entre as páginas dos seus documentos do Word. Esta solução simples, porém eficaz, garante que suas tabelas permaneçam organizadas e profissionais, melhorando a legibilidade dos seus documentos. O Aspose.Words para .NET facilita a resolução desses problemas de formatação, permitindo que você se concentre na criação de conteúdo de qualidade.

## Perguntas frequentes

### Posso manter várias tabelas juntas usando esse método?  
Sim, você pode aplicar a mesma lógica a várias tabelas iterando em cada tabela do seu documento.

### E se minha tabela for grande demais para caber em uma página?  
Se uma tabela for grande demais para caber em uma única página, ela ainda se estenderá por várias páginas. Esse método garante que tabelas menores permaneçam intactas sem se dividirem.

### Existe uma maneira de automatizar isso para todas as tabelas em um documento?  
Sim, você pode percorrer todas as tabelas do seu documento e aplicar o `KeepWithNext` propriedade para cada parágrafo.

### Preciso de uma licença paga para o Aspose.Words para .NET?  
Você pode começar com um teste gratuito em [aqui](https://releases.aspose.com/), mas para funcionalidade completa, uma licença paga é recomendada.

### Posso aplicar outra formatação à tabela e mantê-la unida?  
Com certeza! Você pode formatar sua tabela conforme necessário, garantindo que tudo fique reunido em uma única página.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}