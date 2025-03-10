---
title: Adicionar propriedades personalizadas do documento
linktitle: Adicionar propriedades personalizadas do documento
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como adicionar propriedades de documento personalizadas em arquivos do Word usando o Aspose.Words para .NET. Siga nosso guia passo a passo para aprimorar seus documentos com metadados adicionais.
weight: 10
url: /pt/net/programming-with-document-properties/add-custom-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar propriedades personalizadas do documento

## Introdução

Olá! Você está mergulhando no mundo do Aspose.Words para .NET e se perguntando como adicionar propriedades de documento personalizadas aos seus arquivos do Word? Bem, você veio ao lugar certo! Propriedades personalizadas podem ser incrivelmente úteis para armazenar metadados adicionais que não são cobertos por propriedades internas. Seja autorizando um documento, adicionando um número de revisão ou até mesmo inserindo datas específicas, as propriedades personalizadas têm tudo o que você precisa. Neste tutorial, vamos orientá-lo nas etapas para adicionar essas propriedades perfeitamente usando o Aspose.Words para .NET. Pronto para começar? Vamos mergulhar!

## Pré-requisitos

Antes de começarmos o código, vamos garantir que você tenha tudo o que precisa:

1.  Biblioteca Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words para .NET. Você pode baixá-la[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Um IDE como o Visual Studio.
3. Conhecimento básico de C#: Este tutorial pressupõe que você tenha um conhecimento básico de C# e .NET.
4.  Documento de exemplo: Tenha um documento de exemplo do Word pronto, chamado`Properties.docx`, que você irá modificar.

## Importar namespaces

Antes de começarmos a codificar, precisamos importar os namespaces necessários. Este é um passo crucial para garantir que seu código tenha acesso a todas as funcionalidades fornecidas pelo Aspose.Words.

```csharp
using System;
using Aspose.Words;
```

## Etapa 1: Configurando o caminho do documento

 Primeiro, precisamos configurar o caminho para o nosso documento. É aqui que especificaremos a localização do nosso`Properties.docx` arquivo.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Neste trecho, substitua`"YOUR DOCUMENT DIRECTORY"` com o caminho real para seu documento. Este passo é crucial, pois permite que o programa localize e abra seu arquivo Word.

## Etapa 2: Acessando propriedades personalizadas do documento

Em seguida, vamos acessar as propriedades personalizadas do documento do Word. É aqui que todos os seus metadados personalizados serão armazenados.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Ao fazer isso, obtemos um controle sobre a coleção de propriedades personalizadas, com a qual trabalharemos nas etapas seguintes.

## Etapa 3: Verificação de propriedades existentes

Antes de adicionar novas propriedades, é uma boa ideia verificar se uma propriedade específica já existe. Isso evita qualquer duplicação desnecessária.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Esta linha verifica se a propriedade "Authorized" já existe. Se existir, o programa sairá do método mais cedo para evitar adicionar propriedades duplicadas.

## Etapa 4: Adicionando uma propriedade booleana

Agora, vamos adicionar nossa primeira propriedade personalizada: um valor booleano para indicar se o documento está autorizado.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Esta linha adiciona uma propriedade personalizada chamada "Autorizado" com um valor de`true`. Simples e direto!

## Etapa 5: Adicionando uma propriedade String

Em seguida, adicionaremos outra propriedade personalizada para especificar quem autorizou o documento.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Aqui, estamos adicionando uma propriedade chamada "Authorized By" com o valor "John Smith". Sinta-se à vontade para substituir "John Smith" por qualquer outro nome que preferir.

## Etapa 6: Adicionando uma propriedade de data

Vamos adicionar uma propriedade para armazenar a data de autorização. Isso ajuda a manter o controle de quando o documento foi autorizado.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Este snippet adiciona uma propriedade chamada "Data Autorizada" com a data atual como seu valor. O`DateTime.Today`propriedade busca automaticamente a data de hoje.

## Etapa 7: Adicionar um número de revisão

Também podemos adicionar uma propriedade para manter o controle do número de revisão do documento. Isso é particularmente útil para controle de versão.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Aqui, estamos adicionando uma propriedade chamada "Revisão Autorizada" e atribuindo a ela o número de revisão atual do documento.

## Etapa 8: Adicionando uma propriedade numérica

Por fim, vamos adicionar uma propriedade numérica para armazenar um valor autorizado. Isso pode ser qualquer coisa, desde um valor de orçamento até um valor de transação.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Esta linha adiciona uma propriedade chamada "Valor Autorizado" com um valor de`123.45`. Novamente, sinta-se à vontade para substituir isso por qualquer número que atenda às suas necessidades.

## Conclusão

aí está! Você adicionou com sucesso propriedades de documento personalizadas a um documento do Word usando o Aspose.Words para .NET. Essas propriedades podem ser incrivelmente úteis para armazenar metadados adicionais específicos para suas necessidades. Não importa se você está rastreando detalhes de autorização, números de revisão ou quantidades específicas, as propriedades personalizadas fornecem uma solução flexível.

Lembre-se, a chave para dominar o Aspose.Words para .NET é a prática. Então, continue experimentando diferentes propriedades e veja como elas podem aprimorar seus documentos. Boa codificação!

## Perguntas frequentes

### O que são propriedades de documentos personalizadas?
Propriedades de documento personalizadas são metadados que você pode adicionar a um documento do Word para armazenar informações adicionais que não são cobertas pelas propriedades integradas.

### Posso adicionar outras propriedades além de strings e números?
Sim, você pode adicionar vários tipos de propriedades, incluindo booleanas, de data e até objetos personalizados.

### Como posso acessar essas propriedades em um documento do Word?
Propriedades personalizadas podem ser acessadas programaticamente usando o Aspose.Words ou visualizadas diretamente no Word por meio das propriedades do documento.

### É possível editar ou excluir propriedades personalizadas?
Sim, você pode editar ou excluir facilmente propriedades personalizadas usando métodos semelhantes fornecidos pelo Aspose.Words.

### Propriedades personalizadas podem ser usadas para filtrar documentos?
Absolutamente! Propriedades personalizadas são excelentes para categorizar e filtrar documentos com base em metadados específicos.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
