---
title: Trabalhando com modelo de IA
linktitle: Trabalhando com modelo de IA
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a usar o Aspose.Words for .NET para resumir documentos com IA. Passos fáceis para aprimorar o gerenciamento de documentos.
weight: 10
url: /pt/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Trabalhando com modelo de IA

## Introdução

Bem-vindo ao mundo cativante do Aspose.Words para .NET! Se você já desejou levar o gerenciamento de documentos para o próximo nível, você está no lugar certo. Imagine ter a capacidade de resumir automaticamente documentos grandes com apenas algumas linhas de código. Parece incrível, certo? Neste guia, estamos nos aprofundando no uso do Aspose.Words para gerar resumos de documentos usando poderosos modelos de linguagem de IA como o GPT da OpenAI. Seja você um desenvolvedor que busca aprimorar seus aplicativos ou um entusiasta de tecnologia ansioso para aprender algo novo, este tutorial tem tudo o que você precisa.

## Pré-requisitos

Antes de arregaçarmos as mangas e começarmos a codificar, há alguns itens essenciais que você precisa ter em mãos:

1. Visual Studio instalado: Certifique-se de ter o Visual Studio instalado em sua máquina. Você pode baixá-lo gratuitamente se ainda não o tiver.
  
2. .NET Framework: Certifique-se de que você esteja usando uma versão compatível do .NET Framework para Aspose.Words. Ele suporta tanto o .NET Framework quanto o .NET Core.

3.  Aspose.Words para .NET: Você precisará baixar e instalar o Aspose.Words. Você pode obter a versão mais recente[aqui](https://releases.aspose.com/words/net/).

4. Uma chave de API para modelos de IA: para utilizar sumarização de IA, você precisará de acesso a um modelo de IA. Obtenha sua chave de API de plataformas como OpenAI ou Google.

5. Conhecimento básico de C#: Uma compreensão fundamental da programação em C# é necessária para aproveitar ao máximo este tutorial.

Pegou tudo? Incrível! Vamos pular para a parte divertida - importar nossos pacotes necessários.

## Pacotes de importação

Para aproveitar os poderes do Aspose.Words e trabalhar com modelos de IA, começamos importando os pacotes necessários. Veja como fazer isso:

### Criar um novo projeto

Primeiro, inicie o Visual Studio e crie um novo projeto de aplicativo de console.

1. Abra o Visual Studio.
2. Clique em “Criar um novo projeto”.
3. Selecione “Console App (.NET Framework)” ou “Console App (.NET Core)” com base na sua configuração.
4. Dê um nome ao seu projeto e especifique o local.

### Instalar os pacotes Aspose.Words e AI Model

Para usar o Aspose.Words, você precisa instalar o pacote via NuGet.

1. Clique com o botão direito do mouse no seu projeto no Solution Explorer e escolha “Gerenciar pacotes NuGet”.
2. Pesquise por “Aspose.Words” e clique em “Instalar”.
3. Se você estiver usando algum pacote de modelo de IA específico (como OpenAI), certifique-se de que ele também esteja instalado.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Parabéns! Com os pacotes prontos, vamos nos aprofundar mais em nossa implementação.

## Etapa 1: configure seus diretórios de documentos

Em nosso código, definiremos diretórios para gerenciar onde nossos documentos serão armazenados e para onde nossa saída irá. 

```csharp
// Seu diretório de documentos
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Seu diretório ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  Aqui, substitua`YOUR_DOCUMENT_DIRECTORY` com o local onde seus documentos estão armazenados e`YOUR_ARTIFACTS_DIRECTORY` onde você deseja salvar os arquivos resumidos.

## Etapa 2: Carregue os documentos

Em seguida, carregaremos os documentos que queremos resumir em nosso programa. Isso é muito fácil! Veja como:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Ajuste os nomes dos arquivos para o que você salvou. O exemplo assume que você tem dois documentos chamados “Big document.docx” e “Document.docx.”

## Etapa 3: Inicializar o modelo de IA

Nosso próximo passo é estabelecer uma conexão com o modelo de IA. É aqui que entra em jogo a chave de API que você obteve anteriormente.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Certifique-se de ter sua chave de API armazenada como uma variável de ambiente. É como manter seu molho secreto seguro!

## Etapa 4: Gere um resumo para o primeiro documento

Agora, vamos criar um resumo para nosso primeiro documento. Definiremos parâmetros para definir o comprimento do resumo também.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Este snippet resume o primeiro documento e salva a saída no diretório de artefatos especificado. Sinta-se à vontade para alterar o comprimento do resumo conforme sua preferência!

## Etapa 5: Gerar um resumo para vários documentos

Está se sentindo aventureiro? Você também pode resumir vários documentos de uma vez! Veja como fazer:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Assim, você está resumindo dois documentos simultaneamente! Fala sobre eficiência, certo?

## Conclusão

E aí está! Ao seguir este guia, você dominou a arte de resumir documentos usando o Aspose.Words para .NET e poderosos modelos de IA. É um recurso interessante que pode economizar muito tempo, seja para uso pessoal ou integração em aplicativos profissionais. Agora vá em frente, libere o poder da automação e veja sua produtividade disparar!

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, modificar, converter e renderizar documentos do Word programaticamente.

### Como obtenho uma chave de API para modelos de IA?
Você pode obter uma chave de API de provedores de IA como OpenAI ou Google. Certifique-se de criar uma conta e seguir suas instruções para gerar sua chave.

### Posso usar o Aspose.Words para outros formatos de arquivo?
Sim! O Aspose.Words suporta vários formatos de arquivo, incluindo DOCX, RTF e HTML, fornecendo recursos abrangentes além de apenas documentos de texto.

### Existe uma versão gratuita do Aspose.Words?
O Aspose oferece um teste gratuito, permitindo que você teste seus recursos. Você pode baixá-lo do site deles.

### Onde posso encontrar mais recursos para o Aspose.Words?
 Você pode verificar a documentação[aqui](https://reference.aspose.com/words/net/) para guias e insights abrangentes.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
