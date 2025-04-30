---
"description": "Aprenda como evitar que tabelas se quebrem entre páginas usando o Aspose.Words para .NET com este guia passo a passo. Garanta documentos do Word organizados e com aparência profissional."
"linktitle": "Mantenha a mesa junta"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Mantenha a mesa junta"
"url": "/pt/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mantenha a mesa junta

## Introdução

As tabelas são uma parte essencial de muitos documentos do Word, mas, às vezes, você pode se deparar com uma situação em que a tabela se divide em duas páginas. Isso pode atrapalhar o fluxo do documento e afetar sua legibilidade. Não seria ótimo se houvesse uma maneira de manter a tabela inteira unida em uma única página? Bem, com o Aspose.Words para .NET, há uma solução fácil para esse problema! Neste tutorial, mostraremos como evitar que as tabelas se dividam entre as páginas, garantindo que seu documento tenha uma aparência organizada e profissional.

## Pré-requisitos

Antes de começarmos o tutorial, vamos garantir que você tenha tudo o que precisa para seguir adiante sem problemas.

### Biblioteca Aspose.Words para .NET

Primeiro, você precisa ter o Aspose.Words para .NET instalado. Esta é a poderosa biblioteca que permite trabalhar com documentos do Word programaticamente.

- [Baixe Aspose.Words para .NET](https://releases.aspose.com/words/net/)

### Ambiente de Desenvolvimento

Você deve ter um ambiente de desenvolvimento configurado para executar código C#, como:

- Visual Studio (qualquer versão recente)
- .NET Framework 2.0 ou posterior

### Um documento do Word com uma tabela

Você precisará de um documento do Word que contenha uma tabela. Neste tutorial, trabalharemos com um documento de exemplo chamado `"Table spanning two pages.docx"`. Este arquivo contém uma tabela que atualmente se estende por duas páginas.

### Licença Temporária (Opcional)

Embora o Aspose.Words venha com um teste gratuito, você pode querer usar um [licença temporária](https://purchase.aspose.com/temporary-license/) para liberar todo o potencial da biblioteca.

## Pacotes de importação

Antes de escrever qualquer código, precisamos importar os namespaces necessários para trabalhar com o Aspose.Words para .NET. Adicione as seguintes importações no início do seu arquivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Esses namespaces fornecem acesso a classes como `Document`, `Table`, `Cell`, e outros que usaremos neste tutorial.

## Etapa 1: Carregue o documento

A primeira coisa que precisamos fazer é carregar o documento do Word que contém a tabela. Para isso, usaremos o `Document` classe do Aspose.Words. Esta classe permite abrir e manipular arquivos do Word programaticamente.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

Neste trecho de código, especificamos a localização do nosso documento. Substituir `"YOUR DOCUMENTS DIRECTORY"` com o diretório real onde seu documento está armazenado.

## Etapa 2: Acesse a tabela

Após o carregamento do documento, o próximo passo é acessar a tabela que queremos manter unida. Neste exemplo, assumimos que a tabela é a primeira tabela do documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Esta linha de código encontra a primeira tabela no documento. A `GetChild` método recupera um tipo específico de nó, que neste caso é `NodeType.Table`. O `0` indica que queremos a primeira tabela e a `true` O sinalizador garante que pesquisaremos recursivamente em todos os nós filhos.

## Etapa 3: Percorrer as células da tabela

Agora, precisamos percorrer cada célula da tabela. Como uma tabela contém várias linhas e cada linha contém várias células, iteraremos por cada célula e garantiremos que ela não se quebre entre as páginas.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Aqui, `GetChildNodes` recupera todas as células da tabela e percorremos cada uma delas. O `EnsureMinimum()` O método garante que cada célula contenha pelo menos um parágrafo, pois uma célula vazia pode causar problemas mais tarde.

## Etapa 4: definir a propriedade KeepWithNext

Para evitar que a tabela se quebre entre as páginas, precisamos definir o `KeepWithNext` propriedade para cada parágrafo dentro da tabela. Essa propriedade garante que o parágrafo permaneça junto com o próximo, evitando efetivamente quebras de página entre eles.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Este loop verifica cada parágrafo dentro de cada célula. A condição garante que não apliquemos o `KeepWithNext` propriedade para o último parágrafo da última linha. Caso contrário, a propriedade não teria efeito, pois não há próximo parágrafo.

## Etapa 5: Salve o documento

Por fim, após a aplicação do `KeepWithNext` propriedade, precisamos salvar o documento modificado.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Esta linha salva o documento atualizado com um novo nome, preservando o arquivo original. Agora você pode abrir o arquivo resultante e ver que a tabela não está mais dividida em duas páginas!

## Conclusão

Pronto! Seguindo estes passos simples, você pode facilmente evitar que as tabelas se quebrem entre páginas em documentos do Word usando o Aspose.Words para .NET. Seja trabalhando em relatórios, contratos ou outros documentos, manter as tabelas intactas garante uma aparência mais elegante e profissional.

A beleza do Aspose.Words reside na sua flexibilidade e facilidade de uso, permitindo manipular documentos do Word programaticamente sem precisar ter o Microsoft Word instalado no seu computador. Agora que você já sabe como organizar tabelas, explore outros recursos da biblioteca para levar suas habilidades de processamento de documentos a um novo patamar!

## Perguntas frequentes

### Por que minha tabela ainda está quebrando entre páginas depois de usar esse código?

Se a sua mesa ainda estiver quebrando, certifique-se de ter aplicado o `KeepWithNext` propriedade corretamente. Verifique novamente se todos os parágrafos, exceto o último, em cada célula têm esta propriedade definida.

### Posso manter apenas linhas específicas juntas?

Sim, você pode aplicar seletivamente o `KeepWithNext` propriedade para linhas ou parágrafos específicos dentro da tabela para controlar quais partes devem permanecer juntas.

### Esse método funciona com tabelas grandes?

Para tabelas muito grandes, o Word ainda pode dividi-las em páginas se não houver espaço suficiente para acomodar a tabela inteira em uma única página. Considere ajustar a formatação ou as margens da sua tabela para acomodar tabelas maiores.

### Posso usar esse método com outros formatos de documento?

Sim! O Aspose.Words para .NET suporta diversos formatos, como DOC, DOCX, PDF e outros. O mesmo método funciona em todos os formatos que suportam tabelas.

### O Aspose.Words para .NET é uma biblioteca gratuita?

O Aspose.Words para .NET oferece um teste gratuito, mas para acesso total a todos os recursos, você precisará adquirir uma licença. Você pode explorar as opções de licenciamento no site [Página de compra Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}