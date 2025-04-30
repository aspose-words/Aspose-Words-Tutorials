---
"description": "Aprenda a inserir um campo ASK sem usar o Construtor de Documentos no Aspose.Words para .NET. Siga este guia para aprimorar seus documentos do Word dinamicamente."
"linktitle": "Inserir ASKField sem o Document Builder"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Inserir ASKField sem o Document Builder"
"url": "/pt/net/working-with-fields/insert-askfield-with-out-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir ASKField sem o Document Builder

## Introdução

Quer dominar a automação de documentos com o Aspose.Words para .NET? Você veio ao lugar certo! Hoje, vamos mostrar como inserir um campo ASK sem usar um Construtor de Documentos. Este é um recurso bacana quando você quer que seu documento solicite aos usuários uma entrada específica, tornando seus documentos do Word mais interativos e dinâmicos. Então, vamos lá e deixe seus documentos mais inteligentes!

## Pré-requisitos

Antes de colocarmos a mão na massa com algum código, vamos garantir que temos tudo configurado:

1. Aspose.Words para .NET: Certifique-se de ter esta biblioteca instalada. Caso contrário, você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: um IDE adequado, como o Visual Studio.
3. .NET Framework: certifique-se de ter o .NET Framework instalado.

Ótimo! Agora que estamos prontos, vamos começar importando os namespaces necessários.

## Importar namespaces

Antes de mais nada, precisamos importar o namespace Aspose.Words para acessar todos os recursos do Aspose.Words para .NET. Veja como fazer isso:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Etapa 1: Criar um novo documento

Antes de inserir um campo ASK, precisamos de um documento para trabalhar. Veja como criar um novo documento:

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Criação de documentos.
Document doc = new Document();
```

Este trecho de código configura um novo documento do Word onde adicionaremos nosso campo ASK.

## Etapa 2: Acesse o nó Parágrafo

Em um documento do Word, o conteúdo é organizado em nós. Precisamos acessar o primeiro nó do parágrafo, onde inseriremos nosso campo ASK:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Esta linha de código recupera o primeiro parágrafo do documento, pronto para nossa inserção no campo ASK.

## Etapa 3: Insira o campo ASK

Agora, vamos ao evento principal: inserir o campo ASK. Este campo solicitará uma entrada do usuário quando o documento for aberto.

```csharp
// Insira o campo ASK.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Aqui, acrescentamos um campo ASK ao parágrafo. Simples, certo?

## Etapa 4: Configurar o campo ASK

Precisamos definir algumas propriedades para definir o comportamento do campo ASK. Vamos configurar o nome do marcador, o texto do prompt, a resposta padrão e o comportamento da mala direta:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: Um identificador exclusivo para o campo ASK.
- PromptText: O texto que solicita a entrada do usuário.
- DefaultResponse: A resposta pré-preenchida que o usuário pode alterar.
- PromptOnceOnMailMerge: determina se o prompt aparece apenas uma vez durante uma mala direta.

## Etapa 5: Atualizar o campo

Depois de configurar o campo ASK, precisamos atualizá-lo para garantir que todas as configurações sejam aplicadas corretamente:

```csharp
field.Update();
```

Este comando garante que nosso campo ASK esteja pronto e configurado corretamente no documento.

## Etapa 6: Salve o documento

Por fim, vamos salvar o documento no diretório especificado:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Esta linha salva o documento com o campo ASK inserido. E pronto – seu documento agora está equipado com um campo ASK dinâmico!

## Conclusão

Parabéns! Você acabou de adicionar um campo ASK a um documento do Word usando o Aspose.Words para .NET sem o Construtor de Documentos. Este recurso pode aprimorar significativamente a interação do usuário com seus documentos, tornando-os mais flexíveis e fáceis de usar. Continue experimentando diferentes campos e propriedades para explorar todo o potencial do Aspose.Words. Boa programação!

## Perguntas frequentes

### O que é um campo ASK no Aspose.Words?
Um campo ASK no Aspose.Words é um campo que solicita ao usuário uma entrada específica quando o documento é aberto, permitindo a entrada dinâmica de dados.

### Posso usar vários campos ASK em um único documento?
Sim, você pode inserir vários campos ASK em um documento, cada um com prompts e respostas exclusivos.

### Qual é o propósito do `PromptOnceOnMailMerge` propriedade?
O `PromptOnceOnMailMerge` propriedade determina se o prompt ASK aparece apenas uma vez durante uma operação de mala direta ou todas as vezes.

### Preciso atualizar o campo ASK depois de definir suas propriedades?
Sim, atualizar o campo ASK garante que todas as propriedades sejam aplicadas corretamente e que o campo funcione conforme o esperado.

### Posso personalizar o texto do prompt e a resposta padrão?
Com certeza! Você pode definir textos de prompt personalizados e respostas padrão para adaptar o campo PERGUNTAR às suas necessidades específicas.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}