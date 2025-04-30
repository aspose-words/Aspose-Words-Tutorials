---
"description": "Aprenda a inserir campos aninhados em documentos do Word usando o Aspose.Words para .NET com nosso guia passo a passo. Perfeito para desenvolvedores que buscam automatizar a criação de documentos."
"linktitle": "Inserir campos aninhados"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Inserir campos aninhados"
"url": "/pt/net/working-with-fields/insert-nested-fields/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir campos aninhados

## Introdução

Você já precisou inserir campos aninhados em seus documentos do Word programaticamente? Talvez queira exibir textos diferentes condicionalmente com base no número da página? Bem, você está com sorte! Este tutorial guiará você pelo processo de inserção de campos aninhados usando o Aspose.Words para .NET. Vamos lá!

## Pré-requisitos

Antes de começar, você precisa de algumas coisas:

1. Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words para .NET. Você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: um IDE como o Visual Studio.
3. Conhecimento básico de C#: Compreensão da linguagem de programação C#.

## Importar namespaces

Primeiro, certifique-se de importar os namespaces necessários para o seu projeto. Esses namespaces contêm classes que você precisará para interagir com o Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.HeaderFooter;
```

## Etapa 1: Inicializar o documento

O primeiro passo é criar um novo documento e um objeto DocumentBuilder. A classe DocumentBuilder auxilia na criação e modificação de documentos do Word.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Crie o documento e o DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: inserir quebras de página

Em seguida, inseriremos algumas quebras de página no documento. Isso nos permitirá demonstrar os campos aninhados de forma eficaz.

```csharp
// Inserir quebras de página.
for (int i = 0; i < 5; i++)
{
    builder.InsertBreak(BreakType.PageBreak);
}
```

## Etapa 3: Mover para o rodapé

Após inserir as quebras de página, precisamos ir para o rodapé do documento. É aqui que inseriremos nosso campo aninhado.

```csharp
// Mover para o rodapé.
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);
```

## Etapa 4: Inserir campo aninhado

Agora, vamos inserir o campo aninhado. Usaremos o campo SE para exibir o texto condicionalmente com base no número da página atual.

```csharp
// Inserir campo aninhado.
Field field = builder.InsertField(@"IF ");
builder.MoveTo(field.Separator);
builder.InsertField("PAGE");
builder.Write(" <> ");
builder.InsertField("NUMPAGES");
builder.Write(" \"See next page\" \"Last page\" ");
```

Nesta etapa, primeiro inserimos o campo SE, movemos para o seu separador e, em seguida, inserimos os campos PÁGINA e NUMPÁGIOS. O campo SE verifica se o número da página atual (PÁGINA) não é igual ao número total de páginas (NUMPÁGIOS). Se verdadeiro, exibe "Ver próxima página", caso contrário, exibe "Última página".

## Etapa 5: Atualizar o campo

Por fim, atualizamos o campo para garantir que ele exiba o texto correto.

```csharp
// Atualize o campo.
field.Update();
```

## Etapa 6: Salve o documento

O último passo é salvar o documento no diretório especificado.

```csharp
doc.Save(dataDir + "InsertNestedFields.docx");
```

## Conclusão

pronto! Você inseriu com sucesso campos aninhados em um documento do Word usando o Aspose.Words para .NET. Esta poderosa biblioteca facilita incrivelmente a manipulação programática de documentos do Word. Seja para gerar relatórios, criar modelos ou automatizar fluxos de trabalho de documentos, o Aspose.Words tem tudo o que você precisa.

## Perguntas frequentes

### O que é um campo aninhado em documentos do Word?
Um campo aninhado é um campo que contém outros campos dentro dele. Ele permite conteúdo mais complexo e condicional em documentos.

### Posso usar outros campos dentro do campo SE?
Sim, você pode aninhar vários campos como DATA, HORA e AUTOR dentro do campo SE para criar conteúdo dinâmico.

### Aspose.Words para .NET é gratuito?
Aspose.Words para .NET é uma biblioteca comercial, mas você pode obter uma [teste gratuito](https://releases.aspose.com/) para experimentar.

### Posso usar o Aspose.Words com outras linguagens .NET?
Sim, o Aspose.Words suporta todas as linguagens .NET, incluindo VB.NET e F#.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
Você pode encontrar documentação detalhada [aqui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}