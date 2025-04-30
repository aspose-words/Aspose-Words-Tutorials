---
"description": "Guia passo a passo para converter metarquivos para os formatos EMF ou WMF ao converter um documento para HTML com o Aspose.Words para .NET."
"linktitle": "Converter metarquivos para EMF ou WMF"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Converter metarquivos para EMF ou WMF"
"url": "/pt/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Converter metarquivos para EMF ou WMF

## Introdução

Bem-vindo a mais um mergulho profundo no mundo do Aspose.Words para .NET. Hoje, vamos abordar um truque bacana: converter imagens SVG para os formatos EMF ou WMF em seus documentos do Word. Isso pode parecer um pouco técnico, mas não se preocupe. Ao final deste tutorial, você será um profissional nisso. Seja você um desenvolvedor experiente ou esteja apenas começando a usar o Aspose.Words para .NET, este guia o guiará por tudo o que você precisa saber, passo a passo.

## Pré-requisitos

Antes de mergulharmos no código, vamos garantir que tudo esteja configurado. Aqui está o que você precisa:

1. Biblioteca Aspose.Words para .NET: Certifique-se de ter a versão mais recente. Caso não a tenha, você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
2. .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
3. Ambiente de desenvolvimento: Um IDE como o Visual Studio tornará sua vida mais fácil.
4. Conhecimento básico de C#: Você não precisa ser um especialista, mas um conhecimento básico ajudará.

Entendeu tudo? Ótimo! Vamos começar.

## Importar namespaces

Antes de mais nada, precisamos importar os namespaces necessários. Isso é crucial, pois indica ao nosso programa onde encontrar as classes e métodos que usaremos.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Esses namespaces abrangem tudo, desde funções básicas do sistema até a funcionalidade específica do Aspose.Words que precisamos para este tutorial.

## Etapa 1: configure seu diretório de documentos

Vamos começar definindo o caminho para o diretório dos seus documentos. É lá que seu documento do Word será salvo após a conversão dos metarquivos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real onde você deseja salvar seu documento.

## Etapa 2: Crie a string HTML com SVG

Em seguida, precisamos de uma string HTML que contenha a imagem SVG que queremos converter. Aqui está um exemplo simples:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' largura='500' altura='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Este trecho de HTML inclui um SVG básico que diz "Olá, mundo!".

## Etapa 3: Carregar HTML com a opção ConvertSvgToEmf

Agora, usamos o `HtmlLoadOptions` para especificar como queremos lidar com as imagens SVG no HTML. Configuração `ConvertSvgToEmf` para `true` garante que as imagens SVG sejam convertidas para o formato EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Este trecho de código cria um novo `Document` objeto carregando a string HTML nele com as opções de carregamento especificadas.

## Etapa 4: definir HtmlSaveOptions para formato de metarquivo

Para salvar o documento com o formato de metarquivo correto, usamos `HtmlSaveOptions`. Aqui, definimos `MetafileFormat` para `HtmlMetafileFormat.Png`, mas você pode mudar isso para `Emf` ou `Wmf` dependendo de suas necessidades.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Etapa 5: Salve o documento

Por fim, salvamos o documento usando as opções de salvamento especificadas.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Isso salva o documento no diretório especificado com o formato de metarquivo convertido conforme definido.

## Conclusão

Pronto! Seguindo esses passos, você converteu com sucesso imagens SVG para os formatos EMF ou WMF em seus documentos do Word usando o Aspose.Words para .NET. Este método é útil para garantir a compatibilidade e manter a integridade visual dos seus documentos em diferentes plataformas. Boa programação!

## Perguntas frequentes

### Posso converter outros formatos de imagem usando este método?
Sim, você pode converter vários formatos de imagem ajustando as opções de carregamento e salvamento adequadamente.

### É necessário usar uma versão específica do .NET Framework?
O Aspose.Words para .NET oferece suporte a várias versões do .NET Framework, mas é sempre uma boa ideia usar a versão mais recente para melhor compatibilidade e recursos.

### Qual é a vantagem de converter SVG para EMF ou WMF?
A conversão de SVG para EMF ou WMF garante que os gráficos vetoriais sejam preservados e renderizados corretamente em ambientes que podem não oferecer suporte total a SVG.

### Posso automatizar esse processo para vários documentos?
Com certeza! Você pode percorrer vários arquivos HTML, aplicando o mesmo processo para automatizar a conversão para processamento em lote.

### Onde posso encontrar mais recursos e suporte para o Aspose.Words para .NET?
Você pode encontrar documentação abrangente [aqui](https://reference.aspose.com/words/net/) e obtenha suporte da comunidade Aspose [aqui](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}