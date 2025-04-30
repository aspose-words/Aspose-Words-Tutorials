---
"description": "Aprenda a converter um documento do Word em uma imagem indexada de 1Bpp usando o Aspose.Words para .NET. Siga nosso guia passo a passo para uma conversão fácil."
"linktitle": "Formato 1Bpp Indexado"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Formato 1Bpp Indexado"
"url": "/pt/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formato 1Bpp Indexado

## Introdução

Já se perguntou como salvar um documento do Word como uma imagem em preto e branco com apenas algumas linhas de código? Bem, você está com sorte! Hoje, vamos explorar um truque bacana usando o Aspose.Words para .NET que permite converter seus documentos em imagens indexadas de 1Bpp. Este formato é perfeito para certos tipos de arquivamento digital, impressão ou quando você precisa economizar espaço. Vamos detalhar cada etapa para facilitar ao máximo. Pronto para começar? Vamos lá!

## Pré-requisitos

Antes de colocarmos a mão na massa, há algumas coisas que você precisa ter em mãos:

- Aspose.Words para .NET: Certifique-se de ter a biblioteca instalada. Você pode [baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento .NET: o Visual Studio é uma boa opção, mas você pode usar qualquer ambiente com o qual se sinta confortável.
- Conhecimento básico de C#: Não se preocupe, vamos simplificar, mas um pouco de familiaridade com C# ajudará.
- Um documento do Word: tenha um documento de exemplo do Word pronto para ser convertido.

## Importar namespaces

Antes de mais nada, precisamos importar os namespaces necessários. Isso é crucial, pois nos permite acessar as classes e métodos que precisamos do Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: configure seu diretório de documentos

Você precisará especificar o caminho para o diretório do seu documento. É lá que o documento do Word será armazenado e onde a imagem convertida será salva.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Carregue o documento do Word

Agora, vamos carregar o documento do Word em um Aspose.Words `Document` objeto. Este objeto representa seu arquivo do Word e permite que você o manipule.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 3: Configurar opções de salvamento de imagem

Em seguida, precisamos configurar o `ImageSaveOptions`É aqui que a mágica acontece. Vamos configurá-lo para salvar a imagem no formato PNG com modo de cor indexada de 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Isso especifica que queremos salvar o documento como uma imagem PNG.
- PageSet(1): Isso indica que estamos convertendo apenas a primeira página.
- ImageColorMode.BlackAndWhite: define a imagem em preto e branco.
- ImagePixelFormat.Format1bppIndexed: define o formato da imagem como indexado em 1Bpp.

## Etapa 4: Salve o documento como uma imagem

Por fim, salvamos o documento como uma imagem usando o `Save` método do `Document` objeto.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Conclusão

E pronto! Com apenas algumas linhas de código, você transformou seu documento do Word em uma imagem indexada de 1Bpp usando o Aspose.Words para .NET. Este método é incrivelmente útil para criar imagens de alto contraste e com economia de espaço a partir dos seus documentos. Agora você pode integrá-lo facilmente aos seus projetos e fluxos de trabalho. Boa programação!

## Perguntas frequentes

### O que é uma imagem indexada de 1Bpp?
Uma imagem indexada de 1Bpp (1 Bit Per Pixel) é um formato de imagem em preto e branco onde cada pixel é representado por um único bit, 0 ou 1. Esse formato é altamente eficiente em termos de espaço.

### Posso converter várias páginas de um documento do Word de uma só vez?
Sim, você pode. Modifique o `PageSet` propriedade no `ImageSaveOptions` para incluir várias páginas ou o documento inteiro.

### Preciso de uma licença para usar o Aspose.Words para .NET?
Sim, o Aspose.Words para .NET requer uma licença para funcionalidade completa. Você pode obter uma [licença temporária aqui](https://purchase.aspose.com/temporary-license/).

### Para quais outros formatos de imagem posso converter meu documento do Word?
O Aspose.Words suporta vários formatos de imagem, incluindo JPEG, BMP e TIFF. Basta alterar o `SaveFormat` no `ImageSaveOptions`.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?
Você pode encontrar documentação detalhada sobre o [Página de documentação do Aspose.Words para .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}