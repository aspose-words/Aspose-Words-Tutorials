---
title: Incorporar fontes de subconjunto em documento PDF
linktitle: Incorporar fontes de subconjunto em documento PDF
second_title: API de processamento de documentos Aspose.Words
description: Reduza o tamanho do arquivo PDF incorporando apenas subconjuntos de fontes necessários usando o Aspose.Words para .NET. Siga nosso guia passo a passo para otimizar seus PDFs de forma eficiente.
weight: 10
url: /pt/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Incorporar fontes de subconjunto em documento PDF

## Introdução

Você já notou como alguns arquivos PDF são muito maiores do que outros, mesmo quando contêm conteúdo semelhante? O culpado geralmente está nas fontes. Incorporar fontes em um PDF garante que ele tenha a mesma aparência em qualquer dispositivo, mas também pode aumentar o tamanho do arquivo. Felizmente, o Aspose.Words para .NET oferece um recurso útil para incorporar apenas os subconjuntos de fontes necessários, mantendo seus PDFs enxutos e eficientes. Este tutorial o guiará pelo processo, passo a passo.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Você pode baixá-lo[aqui](https://releases.aspose.com/words/net/).
- Ambiente .NET: certifique-se de ter um ambiente de desenvolvimento .NET funcional.
- Conhecimento básico de C#: A familiaridade com a programação em C# ajudará você a acompanhar.

## Importar namespaces

Para usar o Aspose.Words para .NET, você precisa importar os namespaces necessários no seu projeto. Adicione estes no topo do seu arquivo C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Carregue o documento

 Primeiro, precisamos carregar o documento do Word que queremos converter para PDF. Isso é feito usando o`Document` aula fornecida por Aspose.Words.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Este trecho de código carrega o documento localizado em`dataDir` . Certifique-se de substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real para o seu documento.

## Etapa 2: Configurar opções de salvamento de PDF

 Em seguida, configuramos o`PdfSaveOptions` para garantir que apenas os subconjuntos de fontes necessários sejam incorporados. Ao definir`EmbedFullFonts` para`false`, dizemos ao Aspose.Words para incorporar apenas os glifos usados no documento.

```csharp
// O PDF de saída conterá subconjuntos das fontes no documento.
// Somente os glifos usados no documento são incluídos nas fontes do PDF.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Esta pequena, mas crucial etapa ajuda a reduzir significativamente o tamanho do arquivo PDF.

## Etapa 3: Salve o documento como PDF

 Por fim, salvamos o documento como PDF usando o`Save` método, aplicando o configurado`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 Este código irá gerar um arquivo PDF com o nome`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` no diretório especificado, com apenas os subconjuntos de fontes necessários incorporados.

## Conclusão

aí está! Seguindo estes passos simples, você pode reduzir eficientemente o tamanho dos seus arquivos PDF incorporando apenas os subconjuntos de fontes necessários usando o Aspose.Words para .NET. Isso não só economiza espaço de armazenamento, mas também garante tempos de carregamento mais rápidos e melhor desempenho, especialmente para documentos com fontes extensas.

## Perguntas frequentes

### Por que devo incorporar apenas subconjuntos de fontes em um PDF?
Incorporar apenas os subconjuntos de fontes necessários pode reduzir significativamente o tamanho do arquivo PDF sem comprometer a aparência e a legibilidade do documento.

### Posso voltar a incorporar fontes completas se necessário?
 Sim, você pode. Basta definir o`EmbedFullFonts`propriedade para`true` no`PdfSaveOptions`.

### O Aspose.Words para .NET oferece suporte a outros recursos de otimização de PDF?
Com certeza! O Aspose.Words for .NET oferece uma gama de opções para otimizar PDFs, incluindo compactação de imagens e remoção de objetos não utilizados.

### Que tipos de fontes podem ser subconjuntos incorporados usando o Aspose.Words para .NET?
O Aspose.Words para .NET oferece suporte à incorporação de subconjuntos para todas as fontes TrueType usadas no documento.

### Como posso verificar quais fontes estão incorporadas no meu PDF?
Você pode abrir o PDF no Adobe Acrobat Reader e verificar as propriedades na aba Fontes para ver as fontes incorporadas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
