---
title: Não salvar marcador de imagem
linktitle: Não salvar marcador de imagem
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a lidar com marcadores de imagem no Aspose.Words para .NET com nosso guia passo a passo. Simplifique o gerenciamento de documentos e crie documentos profissionais do Word sem esforço.
weight: 10
url: /pt/net/programming-with-docsaveoptions/do-not-save-picture-bullet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Não salvar marcador de imagem

## Introdução

Olá, colegas desenvolvedores! Você já trabalhou com documentos do Word e se viu emaranhado nas complexidades de salvar marcadores de imagem? É um daqueles pequenos detalhes que podem fazer uma grande diferença na aparência final do seu documento. Bem, hoje, estou aqui para guiá-lo pelo processo de manipulação de marcadores de imagem no Aspose.Words para .NET, focando particularmente no recurso "Não salvar marcador de imagem". Pronto para mergulhar? Vamos lá!

## Pré-requisitos

Antes de começarmos a mexer no código, há algumas coisas que você precisa ter em mente:

1.  Aspose.Words para .NET: Certifique-se de ter essa biblioteca poderosa instalada. Se você ainda não a tem, você pode baixá-la[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Um ambiente de desenvolvimento .NET funcional, como o Visual Studio.
3. Conhecimento básico de C#: Alguma familiaridade com programação em C# será útil.
4. Documento de exemplo: Um documento do Word com marcadores de imagem para fins de teste.

## Importar namespaces

Para começar, você precisa importar os namespaces necessários. Isso é bem direto, mas crucial para acessar as funcionalidades do Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Vamos dividir o processo em etapas gerenciáveis. Dessa forma, você pode acompanhar facilmente e entender cada parte do código.

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa especificar o caminho para o diretório dos seus documentos. É aqui que seus documentos do Word são armazenados e onde você salvará os arquivos modificados.

```csharp
// Caminho para o diretório dos seus documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Substituir`"YOUR DOCUMENTS DIRECTORY"` com o caminho real no seu sistema onde seus documentos estão localizados.

## Etapa 2: Carregue o documento com marcadores de imagem

Em seguida, você carregará o documento do Word que contém marcadores de imagem. Este documento será modificado para remover os marcadores de imagem quando salvo.

```csharp
// Carregue o documento com marcadores de imagem
Document doc = new Document(dataDir + "Image bullet points.docx");
```

 Certifique-se de que o arquivo`"Image bullet points.docx"` existe no diretório especificado.

## Etapa 3: Configurar opções de salvamento

Agora, vamos configurar as opções de salvamento para especificar que marcadores de imagem não devem ser salvos. É aqui que a mágica acontece!

```csharp
// Configure as opções de salvamento com o recurso "Não salvar marcadores de imagem"
DocSaveOptions saveOptions = new DocSaveOptions { SavePictureBullet = false };
```

 Ao definir`SavePictureBullet` para`false`, você instrui o Aspose.Words a não salvar marcadores de imagem no documento de saída.

## Etapa 4: Salve o documento

Por fim, salve o documento com as opções especificadas. Isso gerará um novo arquivo onde os marcadores de imagem não estão incluídos.

```csharp
// Salve o documento com as opções especificadas
doc.Save(dataDir + "WorkingWithDocSaveOptions.DoNotSavePictureBullet.docx", saveOptions);
```

 O novo arquivo,`"WorkingWithDocSaveOptions.DoNotSavePictureBullet.docx"`, será salvo no seu diretório de documentos.

## Conclusão

E aí está! Com apenas algumas linhas de código, você configurou com sucesso o Aspose.Words for .NET para omitir marcadores de imagem ao salvar um documento. Isso pode ser incrivelmente útil quando você precisa de uma aparência limpa e consistente sem a distração de marcadores de imagem.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa para criar, editar e converter documentos do Word em aplicativos .NET.

### Posso usar esse recurso para outros tipos de marcadores?
Não, esse recurso específico é para marcadores de imagem. No entanto, o Aspose.Words oferece opções extensas para lidar com outros tipos de marcadores.

### Onde posso obter suporte para o Aspose.Words?
 Você pode obter suporte do[Fórum Aspose.Words](https://forum.aspose.com/c/words/8).

### Existe uma versão de avaliação gratuita do Aspose.Words para .NET?
 Sim, você pode obter uma avaliação gratuita[aqui](https://releases.aspose.com/).

### Como faço para adquirir uma licença do Aspose.Words para .NET?
 Você pode comprar uma licença do[Loja Aspose](https://purchase.aspose.com/buy).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
