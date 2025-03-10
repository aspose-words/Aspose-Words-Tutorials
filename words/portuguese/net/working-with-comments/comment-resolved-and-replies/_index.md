---
title: Comentário resolvido e respostas
linktitle: Comentário resolvido e respostas
second_title: API de processamento de documentos Aspose.Words
description: Automatize a resolução e a resposta a comentários em documentos do Word com o Aspose.Words para .NET. Guia passo a passo incluído.
weight: 10
url: /pt/net/working-with-comments/comment-resolved-and-replies/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comentário resolvido e respostas

## Introdução

Se você estiver trabalhando com documentos do Word, provavelmente já lidou com comentários. Eles são ótimos para colaboração, mas gerenciá-los pode ser um incômodo. Com o Aspose.Words para .NET, você pode automatizar o processo de resolução e resposta a comentários. Este guia o guiará pelas etapas para fazer exatamente isso.

## Pré-requisitos

Antes de mergulhar, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET: Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: configurado com .NET Framework.
3. Conhecimento básico de C#: Familiaridade com a sintaxe e os conceitos.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Isso garante que todas as classes e métodos que precisamos estejam prontamente disponíveis.

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

Vamos dividir o processo em etapas simples e fáceis de seguir. Cada etapa ajudará você a entender o código e sua funcionalidade.

## Etapa 1: Carregue o documento

 Para começar, carregue o documento do Word que contém os comentários. Use o`Document` classe para isso.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

 Esta linha de código inicializa um novo`Document` objeto com o caminho para seu documento do Word.

## Etapa 2: recuperar comentários

 Em seguida, precisamos obter todos os comentários no documento. Usaremos o`GetChildNodes` método para recuperar uma coleção de`Comment` nós.

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

Este código recupera todos os comentários no documento e os armazena em um`NodeCollection`.

## Etapa 3: Acesse o comentário dos pais

Para nosso exemplo, vamos focar no primeiro comentário na coleção. Este será nosso comentário pai.

```csharp
Comment parentComment = (Comment)comments[0];
```

 Aqui, estamos lançando o primeiro nó na coleção para um`Comment` objeto.

## Etapa 4: Loop através das respostas

 Agora, vamos percorrer as respostas ao comentário pai. Usaremos um`foreach` loop para iterar sobre cada resposta.

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

Neste loop, imprimimos o ID do comentário ancestral e seu status (se está feito ou não). Então, marcamos cada resposta como feita.

## Etapa 5: Salve o documento

Por fim, salve o documento modificado no seu diretório.

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

Este código salva as alterações em um novo documento, garantindo que seu arquivo original permaneça intacto.

## Conclusão

Lidar com comentários em documentos do Word não precisa ser uma tarefa manual. Com o Aspose.Words para .NET, você pode automatizar o processo, economizando tempo e reduzindo erros. Siga este guia para resolver e responder eficientemente a comentários em seus documentos.

## Perguntas frequentes

### Posso automatizar outras tarefas relacionadas a comentários com o Aspose.Words para .NET?  
Sim, você pode automatizar várias tarefas, como adicionar, excluir e modificar comentários.

### Aspose.Words para .NET é compatível com o .NET Core?  
Sim, o Aspose.Words para .NET oferece suporte ao .NET Framework e ao .NET Core.

### Como posso obter uma avaliação gratuita do Aspose.Words para .NET?  
 Você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.aspose.com/).

### Posso usar o Aspose.Words for .NET para trabalhar com outros tipos de documentos?  
Sim, o Aspose.Words suporta vários formatos, incluindo DOCX, PDF, HTML e muito mais.

### Onde posso encontrar documentação detalhada do Aspose.Words para .NET?  
 Você pode acessar a documentação[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
