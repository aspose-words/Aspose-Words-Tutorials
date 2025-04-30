---
"description": "Aprenda a bloquear a proporção de formas em documentos do Word usando o Aspose.Words para .NET. Siga este guia passo a passo para manter suas imagens e formas proporcionais."
"linktitle": "Proporção de aspecto bloqueada"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Proporção de aspecto bloqueada"
"url": "/pt/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Proporção de aspecto bloqueada

## Introdução

Você já se perguntou como manter as proporções perfeitas de imagens e formas em seus documentos do Word? Às vezes, você precisa garantir que suas imagens e formas não fiquem distorcidas ao redimensioná-las. É aqui que o bloqueio da proporção da tela se torna útil. Neste tutorial, exploraremos como definir a proporção da tela para formas em documentos do Word usando o Aspose.Words para .NET. Dividiremos o processo em etapas fáceis de seguir, garantindo que você possa aplicar essas habilidades aos seus projetos com confiança.

## Pré-requisitos

Antes de mergulharmos no código, vamos ver o que você precisa para começar:

- Biblioteca Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Se ainda não o tiver, você pode [baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: certifique-se de ter um ambiente de desenvolvimento .NET configurado. O Visual Studio é uma opção popular.
- Conhecimento básico de C#: alguma familiaridade com programação em C# será útil.

## Importar namespaces

Primeiramente, vamos importar os namespaces necessários. Esses namespaces nos darão acesso às classes e métodos necessários para trabalhar com documentos e formas do Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Etapa 1: configure seu diretório de documentos

Antes de começarmos a manipular as formas, precisamos configurar um diretório onde nossos documentos serão armazenados. Para simplificar, usaremos um espaço reservado `YOUR DOCUMENT DIRECTORY`. Substitua isso pelo caminho real para o seu diretório de documentos.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Criar um novo documento

Em seguida, criaremos um novo documento do Word usando o Aspose.Words. Este documento servirá como tela para adicionar formas e imagens.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Aqui, criamos uma instância do `Document` classe e usar um `DocumentBuilder` para nos ajudar a construir o conteúdo do documento.

## Etapa 3: Insira uma imagem

Agora, vamos inserir uma imagem em nosso documento. Usaremos o `InsertImage` método do `DocumentBuilder` classe. Certifique-se de ter uma imagem no diretório especificado.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Substituir `dataDir + "Transparent background logo.png"` com o caminho para seu arquivo de imagem.

## Etapa 4: Bloqueie a proporção da tela

Após a inserção da imagem, podemos bloquear sua proporção. Bloquear a proporção garante que as proporções da imagem permaneçam constantes durante o redimensionamento.

```csharp
shape.AspectRatioLocked = true;
```

Contexto `AspectRatioLocked` para `true` garante que a imagem mantenha sua proporção original.

## Etapa 5: Salve o documento

Por fim, salvaremos o documento no diretório especificado. Esta etapa grava todas as alterações que fizemos no arquivo do documento.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusão

Parabéns! Você aprendeu com sucesso a definir a proporção de formas em documentos do Word usando o Aspose.Words para .NET. Seguindo esses passos, você garante que suas imagens e formas mantenham suas proporções, dando aos seus documentos uma aparência profissional e elegante. Sinta-se à vontade para experimentar diferentes imagens e formas para ver como o recurso de bloqueio de proporção funciona em diferentes cenários.

## Perguntas frequentes

### Posso desbloquear a proporção da tela depois de bloqueá-la?
Sim, você pode desbloquear a proporção da tela definindo `shape.AspectRatioLocked = false`.

### que acontece se eu redimensionar uma imagem com uma proporção de aspecto bloqueada?
A imagem será redimensionada proporcionalmente, mantendo sua proporção original entre largura e altura.

### Posso aplicar isso a outras formas além de imagens?
Com certeza! O recurso de bloqueio de proporção pode ser aplicado a qualquer formato, incluindo retângulos, círculos e muito mais.

### Aspose.Words para .NET é compatível com o .NET Core?
Sim, o Aspose.Words para .NET oferece suporte ao .NET Framework e ao .NET Core.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
Você pode encontrar documentação abrangente [aqui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}