---
title: Trabalhando com o modelo Open AI
linktitle: Trabalhando com o modelo Open AI
second_title: API de processamento de documentos Aspose.Words
description: Desbloqueie sumarização eficiente de documentos usando Aspose.Words para .NET com os modelos poderosos do OpenAI. Mergulhe neste guia abrangente agora.
weight: 10
url: /pt/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Trabalhando com o modelo Open AI

## Introdução

No mundo digital de hoje, o conteúdo é rei. Seja você um estudante, um profissional de negócios ou um escritor ávido, a capacidade de manipular, resumir e gerar documentos de forma eficiente é inestimável. É aqui que a biblioteca Aspose.Words para .NET entra em cena, permitindo que você gerencie documentos como um profissional. Neste tutorial abrangente, vamos nos aprofundar em como aproveitar o Aspose.Words em conjunto com os modelos OpenAI para resumir documentos de forma eficaz. Pronto para desbloquear seu potencial de gerenciamento de documentos? Vamos começar!

## Pré-requisitos

Antes de arregaçarmos as mangas e mergulharmos no código, há alguns princípios essenciais que você precisa ter em mãos:

### Estrutura .NET
Certifique-se de que você esteja executando uma versão do .NET framework que seja compatível com Aspose.Words. Geralmente, .NET 5.0 e acima devem funcionar perfeitamente.

### Biblioteca Aspose.Words para .NET
 Você precisará baixar e instalar a biblioteca Aspose.Words. Você pode obtê-la em[este link](https://releases.aspose.com/words/net/).

### Chave API OpenAI
Para integrar os modelos de linguagem do OpenAI para sumarização de documentos, você precisará de uma Chave de API. Você pode obtê-la inscrevendo-se na plataforma OpenAI e recuperando sua chave nas configurações da sua conta.

### IDE para Desenvolvimento
Ter um Ambiente de Desenvolvimento Integrado (IDE) como o Visual Studio configurado é ideal para desenvolver aplicativos .NET.

### Conhecimento básico de programação
Uma compreensão básica de C# e programação orientada a objetos ajudará você a entender os conceitos com mais facilidade.

## Pacotes de importação

Agora que temos tudo alinhado, vamos importar nossos pacotes. Abra seu projeto do Visual Studio e adicione as bibliotecas necessárias. Veja como você pode fazer isso:

### Adicionar pacote Aspose.Words

Você pode adicionar o pacote Aspose.Words via NuGet Package Manager. Veja como fazer isso:
- Vá para Ferramentas -> Gerenciador de Pacotes NuGet -> Gerenciar Pacotes NuGet para Solução.
- Procure por "Aspose.Words" e clique em Instalar.

### Adicionar ambiente do sistema

 Certifique-se de incluir o`System`namespace para manipular variáveis de ambiente:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Adicionar Aspose.Words

Em seguida, inclua o namespace Aspose.Words no seu arquivo C#:
```csharp
using Aspose.Words;
```

### Adicionar biblioteca OpenAI

Se você estiver usando uma biblioteca para interagir com o OpenAI (como um cliente REST), certifique-se de incluí-la também. Você pode precisar adicioná-la via NuGet da mesma forma que adicionamos Aspose.Words.

Agora que preparamos nosso ambiente e importamos os pacotes necessários, vamos detalhar o processo de resumo de documentos passo a passo.

## Etapa 1: Defina seus diretórios de documentos

Antes de começar a brincar com seus documentos, você precisa configurar diretórios onde seus documentos e artefatos residirão:

```csharp
// Seu diretório de documentos
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Seu Diretório de Artefatos
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Isso torna seu código mais gerenciável, pois você pode facilmente alterar os caminhos, se necessário. O`MyDir` é onde seus documentos de entrada são armazenados, enquanto`ArtifactsDir` é onde você salvará os resumos gerados.

## Etapa 2: Carregue seus documentos

Em seguida, você carregará os documentos que deseja resumir. Isso é direto com Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Certifique-se de que os nomes dos seus documentos correspondem aos que você pretende usar, caso contrário, você encontrará erros!

## Etapa 3: Obtenha sua chave de API

Agora que seus documentos estão carregados, é hora de puxar sua chave OpenAI API. Você vai buscá-la de variáveis de ambiente para mantê-la segura:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
É essencial gerenciar sua chave de API com segurança para manter usuários não autorizados afastados.

## Etapa 4: Crie uma instância do modelo OpenAI

Com sua chave de API pronta, agora você pode criar uma instância do modelo OpenAI. Para sumarização de documentos, usaremos o modelo Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Esta etapa essencialmente configura a capacidade intelectual necessária para resumir seus documentos, dando a você acesso ao resumo orientado por IA.

## Etapa 5: Resumir um único documento

Vamos resumir o primeiro documento primeiro. É aqui que a mágica acontece:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Aqui, estamos usando o`Summarize` método do modelo. O`SummaryLength.Short`parâmetro especifica que queremos um breve resumo — perfeito para uma visão geral rápida!

## Etapa 6: Resumir vários documentos

Sente-se ambicioso? Você pode resumir vários documentos de uma vez. Veja como é fácil:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Este recurso é particularmente útil para comparar vários arquivos. Talvez você esteja se preparando para uma reunião e precise de notas concisas de vários relatórios longos. Este é seu novo melhor amigo!

## Conclusão

Resumir documentos com o Aspose.Words para .NET e OpenAI não é apenas uma habilidade benéfica; é bastante fortalecedor. Ao seguir este guia, você transformou textos longos e complicados em resumos concisos, economizando tempo e esforço. Quer esteja garantindo clareza para clientes ou se preparando para aquela apresentação importante, agora você tem as ferramentas para fazer isso de forma eficiente.

Então, o que você está esperando? Mergulhe em seus documentos com confiança e deixe a tecnologia fazer o trabalho pesado!

## Perguntas frequentes

### O que é Aspose.Words para .NET?  
Aspose.Words para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, manipular e converter documentos programaticamente.

### Preciso de uma chave de API para o OpenAI?  
Sim, você deve ter uma chave de API OpenAI válida para acessar os recursos de sumarização usando seus modelos.

### Posso resumir vários documentos de uma só vez?  
Absolutamente! Você pode resumir vários documentos em uma única chamada, o que é ideal para relatórios extensos.

### Como instalo o Aspose.Words?  
Você pode instalá-lo por meio do Gerenciador de Pacotes NuGet no Visual Studio pesquisando por "Aspose.Words".

### Existe um teste gratuito do Aspose.Words?  
 Sim, você pode acessar uma avaliação gratuita do Aspose.Words por meio de seu[site](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
