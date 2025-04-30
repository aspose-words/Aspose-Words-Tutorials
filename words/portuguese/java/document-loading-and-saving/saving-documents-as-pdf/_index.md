---
"description": "Aprenda a salvar documentos do Word como PDF usando o Aspose.Words para Java. Personalize fontes, propriedades e qualidade de imagem. Um guia completo para conversão de PDF."
"linktitle": "Salvando documentos como PDF"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Salvando documentos como PDF no Aspose.Words para Java"
"url": "/pt/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Salvando documentos como PDF no Aspose.Words para Java


## Introdução ao salvamento de documentos como PDF no Aspose.Words para Java

Neste guia passo a passo, exploraremos como salvar documentos como PDF usando o Aspose.Words para Java. Abordaremos vários aspectos da conversão de PDF e forneceremos exemplos de código para facilitar o processo.

## Pré-requisitos

Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:

- Java Development Kit (JDK) instalado no seu sistema.
- Biblioteca Aspose.Words para Java. Você pode baixá-la em [aqui](https://releases.aspose.com/words/java/).

## Convertendo um documento em PDF

Para converter um documento do Word em PDF, você pode usar o seguinte trecho de código:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Substituir `"input.docx"` com o caminho para o seu documento do Word e `"output.pdf"` com o caminho do arquivo PDF de saída desejado.

## Controlando opções de salvamento de PDF

Você pode controlar várias opções de salvamento de PDF usando o `PdfSaveOptions` classe. Por exemplo, você pode definir o título de exibição do documento PDF da seguinte forma:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Incorporando fontes em PDF

Para incorporar fontes no PDF gerado, use o seguinte código:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Personalizando propriedades do documento

Você pode personalizar as propriedades do documento no PDF gerado. Por exemplo:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Exportando Estrutura de Documento

Para exportar a estrutura do documento, defina o `exportDocumentStructure` opção para `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Compressão de imagem

Você pode controlar a compactação de imagem usando o seguinte código:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Atualizando a última propriedade impressa

Para atualizar a propriedade "Última impressão" no PDF, use:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Renderização de efeitos 3D DML

Para renderização avançada de efeitos 3D DML, defina o modo de renderização:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolando Imagens

Você pode habilitar a interpolação de imagem para melhorar a qualidade da imagem:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Conclusão

O Aspose.Words para Java oferece recursos abrangentes para converter documentos do Word para o formato PDF, com flexibilidade e opções de personalização. Você pode controlar vários aspectos da saída do PDF, incluindo fontes, propriedades do documento, compactação de imagens e muito mais.

## Perguntas frequentes

### Como faço para converter um documento do Word em PDF usando o Aspose.Words para Java?

Para converter um documento do Word em PDF, use o seguinte código:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Substituir `"input.docx"` com o caminho para o seu documento do Word e `"output.pdf"` com o caminho do arquivo PDF de saída desejado.

### Posso incorporar fontes no PDF gerado pelo Aspose.Words para Java?

Sim, você pode incorporar fontes no PDF configurando o `setEmbedFullFonts` opção para `true` em `PdfSaveOptions`. Aqui está um exemplo:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Como posso personalizar as propriedades do documento no PDF gerado?

Você pode personalizar as propriedades do documento no PDF usando o `setCustomPropertiesExport` opção em `PdfSaveOptions`. Por exemplo:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Qual é o propósito da compactação de imagens no Aspose.Words para Java?

A compactação de imagens permite controlar a qualidade e o tamanho das imagens no PDF gerado. Você pode definir o modo de compactação de imagens usando `setImageCompression` em `PdfSaveOptions`.

### Como atualizo a propriedade "Última impressão" no PDF?

Você pode atualizar a propriedade "Última impressão" no PDF configurando `setUpdateLastPrintedProperty` para `true` em `PdfSaveOptions`. Isso refletirá a última data impressa nos metadados do PDF.

### Como posso melhorar a qualidade da imagem ao converter para PDF?

Para melhorar a qualidade da imagem, habilite a interpolação de imagem configurando `setInterpolateImages` para `true` em `PdfSaveOptions`. Isso resultará em imagens mais suaves e de alta qualidade no PDF.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}