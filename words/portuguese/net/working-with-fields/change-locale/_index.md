---
title: Alterar localidade
linktitle: Alterar localidade
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como alterar o local em documentos do Word usando o Aspose.Words para .NET com este guia. Perfeito para lidar com clientes e projetos internacionais.
weight: 10
url: /pt/net/working-with-fields/change-locale/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alterar localidade

## Introdução

Trabalhar com documentos do Word geralmente requer um pouco de sutileza, especialmente ao lidar com diferentes localidades e culturas. Neste tutorial, exploraremos como alterar a localidade de um documento do Word usando o Aspose.Words para .NET. Não importa se você está criando documentos para um público global ou apenas precisa mudar os formatos de data, este guia tem tudo o que você precisa.

## Pré-requisitos

Antes de começarmos, vamos garantir que temos tudo o que precisamos:

-  Aspose.Words para .NET: Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/).
- Visual Studio: qualquer versão que suporte o .NET Framework.
- Conhecimento básico de C#: entender os conceitos básicos de C# e .NET ajudará você a acompanhar.

 Certifique-se de ter instalado o Aspose.Words para .NET. Se não tiver, você pode obter uma avaliação gratuita[aqui](https://releases.aspose.com/) ou compre-o[aqui](https://purchase.aspose.com/buy).

## Importar namespaces

Antes de começarmos a codificar, precisamos importar os namespaces necessários. Eles são como os ingredientes de uma receita, garantindo que tudo funcione perfeitamente.

```csharp
using System.Globalization;
using System.Threading;
using Aspose.Words;
using Aspose.Words.Fields;
```

Alterar o local em um documento do Word é um processo direto. Vamos decompô-lo passo a passo.

## Etapa 1: configure seu documento

Primeiro, vamos configurar nosso documento e o construtor de documentos. É como configurar seu espaço de trabalho antes de começar a cozinhar.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Insira um campo de mesclagem

Agora, vamos inserir um campo de mesclagem para a data. É aqui que o locale entrará em jogo.

```csharp
builder.InsertField("MERGEFIELD Date");
```

## Etapa 3: Salvar a cultura atual

Antes de mudarmos o local, precisamos salvar a cultura atual. Pense nisso como marcar seu lugar antes de passar para outro capítulo.

```csharp
CultureInfo currentCulture = Thread.CurrentThread.CurrentCulture;
```

## Etapa 4: Alterar localidade

Em seguida, mudaremos a cultura atual do tópico para alemão ("de-DE"). Isso é como mudar as configurações de idioma no seu telefone.

```csharp
Thread.CurrentThread.CurrentCulture = new CultureInfo("de-DE");
```

## Etapa 5: Executar mala direta

Agora, executamos a mala direta com a data atual. Isso aplicará o novo locale ao formato de data.

```csharp
doc.MailMerge.Execute(new[] { "Date" }, new object[] { DateTime.Now });
```

## Etapa 6: Restaurar a cultura original

Após executar a mala direta, restauraremos a cultura original. Isso é como voltar para suas configurações de idioma preferidas.

```csharp
Thread.CurrentThread.CurrentCulture = currentCulture;
```

## Etapa 7: Salve o documento

Por fim, salve o documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeLocale.docx");
```

aí está! Você alterou com sucesso o locale no seu documento do Word usando o Aspose.Words for .NET.

## Conclusão

Alterar o local em documentos do Word pode ser incrivelmente útil, especialmente ao lidar com clientes ou projetos internacionais. Com o Aspose.Words para .NET, essa tarefa se torna moleza. Siga estas etapas e você poderá alternar os locais sem esforço.

## Perguntas frequentes

### Posso alterar o idioma para qualquer idioma?
Sim, o Aspose.Words para .NET oferece suporte à alteração do idioma para qualquer idioma suportado pelo .NET.

### Isso afetará outras partes do meu documento?
Alterar o local afetará principalmente os formatos de data e número. Outros textos permanecerão inalterados.

### Preciso de uma licença especial para usar o Aspose.Words para .NET?
 Você pode começar com uma avaliação gratuita, mas para uso contínuo, você precisará comprar uma licença[aqui](https://purchase.aspose.com/buy).

### Posso reverter para o local original se algo der errado?
Sim, salvando a cultura original e restaurando-a mais tarde, você pode reverter para o local original.

### Onde posso obter suporte se tiver problemas?
 Você pode obter suporte da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
