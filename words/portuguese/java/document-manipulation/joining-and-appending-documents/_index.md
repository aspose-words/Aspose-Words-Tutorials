---
"description": "Aprenda a unir e anexar documentos sem esforço usando o Aspose.Words para Java. Preserve a formatação, gerencie cabeçalhos, rodapés e muito mais."
"linktitle": "Juntando e anexando documentos"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Unindo e anexando documentos no Aspose.Words para Java"
"url": "/pt/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Unindo e anexando documentos no Aspose.Words para Java


## Introdução à junção e anexação de documentos no Aspose.Words para Java

Neste tutorial, exploraremos como unir e anexar documentos usando a biblioteca Aspose.Words para Java. Você aprenderá a mesclar vários documentos perfeitamente, preservando a formatação e a estrutura.

## Pré-requisitos

Antes de começar, certifique-se de ter o Aspose.Words para API Java configurado no seu projeto Java.

## Opções de junção de documentos

### Acréscimo Simples

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Adicionar com opções de formato de importação

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Anexar ao documento em branco

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Adicionar com conversão de número de página

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Converter campos NUMPAGES
dstDoc.updatePageLayout(); // Atualizar o layout da página para numeração correta
```

## Lidando com diferentes configurações de página

Ao anexar documentos com configurações de página diferentes:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Certifique-se de que as configurações de configuração da página correspondam ao documento de destino
```

## Unindo documentos com estilos diferentes

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Comportamento de estilo inteligente

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Inserindo documentos com o DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Mantendo a numeração da fonte

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Manipulando caixas de texto

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Gerenciando Cabeçalhos e Rodapés

### Vinculando cabeçalhos e rodapés

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Desvinculando cabeçalhos e rodapés

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Conclusão

O Aspose.Words para Java oferece ferramentas flexíveis e poderosas para unir e anexar documentos, seja para manter a formatação, lidar com diferentes configurações de página ou gerenciar cabeçalhos e rodapés. Experimente essas técnicas para atender às suas necessidades específicas de processamento de documentos.

## Perguntas frequentes

### Como posso unir documentos com estilos diferentes sem problemas?

Para unir documentos com estilos diferentes, use `ImportFormatMode.USE_DESTINATION_STYLES` ao anexar.

### Posso preservar a numeração de páginas ao anexar documentos?

Sim, você pode preservar a numeração de páginas usando o `convertNumPageFieldsToPageRef` método e atualização do layout da página.

### O que é comportamento de estilo inteligente?

O Comportamento de Estilo Inteligente ajuda a manter estilos consistentes ao anexar documentos. Use-o com `ImportFormatOptions` para melhores resultados.

### Como posso lidar com caixas de texto ao anexar documentos?

Definir `importFormatOptions.setIgnoreTextBoxes(false)` para incluir caixas de texto durante a anexação.

### se eu quiser vincular/desvincular cabeçalhos e rodapés entre documentos?

Você pode vincular cabeçalhos e rodapés com `linkToPrevious(true)` ou desvinculá-los com `linkToPrevious(false)` conforme necessário.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}