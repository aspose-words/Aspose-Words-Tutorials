---
title: Proporção de Aspecto Bloqueada
linktitle: Proporção de Aspecto Bloqueada
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como bloquear a proporção de formas em documentos do Word usando o Aspose.Words para .NET. Siga este guia passo a passo para manter suas imagens e formas proporcionais.
weight: 10
url: /pt/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Proporção de Aspecto Bloqueada

## Introdução

Você já se perguntou como manter as proporções perfeitas de imagens e formas em seus documentos do Word? Às vezes, você precisa garantir que suas imagens e formas não fiquem distorcidas quando redimensionadas. É aqui que o bloqueio da proporção de aspecto é útil. Neste tutorial, exploraremos como definir a proporção de aspecto para formas em documentos do Word usando o Aspose.Words para .NET. Dividiremos em etapas fáceis de seguir, garantindo que você possa aplicar essas habilidades aos seus projetos com confiança.

## Pré-requisitos

Antes de mergulharmos no código, vamos ver o que você precisa para começar:

- Biblioteca Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Se você ainda não o fez, você pode[baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Certifique-se de ter um ambiente de desenvolvimento .NET configurado. O Visual Studio é uma escolha popular.
- Conhecimento básico de C#: Alguma familiaridade com programação em C# será útil.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Esses namespaces nos darão acesso às classes e métodos que precisamos para trabalhar com documentos e formas do Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Etapa 1: configure seu diretório de documentos

 Antes de começarmos a manipular formas, precisamos configurar um diretório onde nossos documentos serão armazenados. Para simplificar, usaremos um placeholder`YOUR DOCUMENT DIRECTORY`. Substitua isso pelo caminho real para o diretório do seu documento.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Crie um novo documento

Em seguida, criaremos um novo documento do Word usando Aspose.Words. Este documento servirá como nossa tela para adicionar formas e imagens.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aqui, criamos uma instância do`Document` classe e usar um`DocumentBuilder` para nos ajudar a construir o conteúdo do documento.

## Etapa 3: Insira uma imagem

 Agora, vamos inserir uma imagem em nosso documento. Usaremos o`InsertImage` método do`DocumentBuilder`classe. Certifique-se de ter uma imagem no diretório especificado.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Substituir`dataDir + "Transparent background logo.png"` com o caminho para o seu arquivo de imagem.

## Etapa 4: Bloqueie a proporção da tela

Uma vez que a imagem é inserida, podemos bloquear sua proporção de aspecto. Bloquear a proporção de aspecto garante que as proporções da imagem permaneçam constantes ao redimensionar.

```csharp
shape.AspectRatioLocked = true;
```

 Contexto`AspectRatioLocked` para`true` garante que a imagem mantenha sua proporção original.

## Etapa 5: Salve o documento

Por fim, salvaremos o documento no diretório especificado. Esta etapa grava todas as alterações que fizemos no arquivo do documento.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusão

Parabéns! Você aprendeu com sucesso como definir a proporção de aspecto para formas em documentos do Word usando o Aspose.Words para .NET. Seguindo essas etapas, você pode garantir que suas imagens e formas mantenham suas proporções, fazendo com que seus documentos pareçam profissionais e polidos. Sinta-se à vontade para experimentar diferentes imagens e formas para ver como o recurso de bloqueio de proporção de aspecto funciona em vários cenários.

## Perguntas frequentes

### Posso desbloquear a proporção da tela depois de bloqueá-la?
Sim, você pode desbloquear a proporção da tela definindo`shape.AspectRatioLocked = false`.

### O que acontece se eu redimensionar uma imagem com uma proporção bloqueada?
A imagem será redimensionada proporcionalmente, mantendo sua proporção original entre largura e altura.

### Posso aplicar isso a outras formas além de imagens?
Absolutamente! O recurso de bloqueio de proporção de aspecto pode ser aplicado a qualquer forma, incluindo retângulos, círculos e muito mais.

### Aspose.Words para .NET é compatível com o .NET Core?
Sim, o Aspose.Words para .NET oferece suporte ao .NET Framework e ao .NET Core.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
 Você pode encontrar documentação abrangente[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
