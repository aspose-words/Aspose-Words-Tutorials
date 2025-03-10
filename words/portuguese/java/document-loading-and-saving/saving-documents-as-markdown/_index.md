---
title: Salvando documentos como Markdown no Aspose.Words para Java
linktitle: Salvando documentos como Markdown
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda como converter documentos do Word para Markdown com Aspose.Words para Java. Este guia passo a passo abrange alinhamento de tabelas, manipulação de imagens e muito mais.
weight: 18
url: /pt/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvando documentos como Markdown no Aspose.Words para Java


## Introdução ao salvamento de documentos como Markdown no Aspose.Words para Java

Neste guia passo a passo, demonstraremos como salvar documentos como Markdown usando o Aspose.Words para Java. Markdown é uma linguagem de marcação leve que é comumente usada para formatar documentos de texto. Com o Aspose.Words para Java, você pode facilmente converter seus documentos do Word para o formato Markdown. Abordaremos diferentes aspectos de salvar arquivos Markdown, incluindo alinhamento de conteúdo de tabela e manipulação de imagens.

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes pré-requisitos:

- Java Development Kit (JDK) instalado no seu sistema.
-  Biblioteca Aspose.Words para Java. Você pode baixá-la em[aqui](https://releases.aspose.com/words/java/).

## Etapa 1: Criando um documento do Word

Vamos começar criando um documento Word que depois converteremos para o formato Markdown. Você pode personalizar este documento conforme suas necessidades.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir uma tabela com duas células
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Salvar o documento como Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 Neste exemplo, criamos uma tabela simples com duas células e definimos o alinhamento dos parágrafos dentro dessas células. Em seguida, salvamos o documento como Markdown usando o`MarkdownSaveOptions`.

## Etapa 2: personalizar o alinhamento do conteúdo da tabela

O Aspose.Words para Java permite que você personalize o alinhamento do conteúdo da tabela ao salvar como Markdown. Você pode alinhar o conteúdo da tabela à esquerda, à direita, ao centro ou deixá-lo ser determinado automaticamente com base no primeiro parágrafo em cada coluna da tabela.

Veja como personalizar o alinhamento do conteúdo da tabela:

```java
// Defina o alinhamento do conteúdo da tabela para a esquerda
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Defina o alinhamento do conteúdo da tabela para a direita
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Defina o alinhamento do conteúdo da tabela para o centro
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Defina o alinhamento do conteúdo da tabela como automático (determinado pelo primeiro parágrafo)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Ao alterar o`TableContentAlignment` propriedade, você pode controlar como o conteúdo dentro das tabelas é alinhado ao converter para Markdown.

## Etapa 3: Manipulando imagens

 Para incluir imagens no seu documento Markdown, você precisa especificar a pasta onde as imagens estão localizadas. O Aspose.Words para Java permite que você defina a pasta de imagens no`MarkdownSaveOptions`.

Veja como definir a pasta de imagens e salvar o documento com imagens:

```java
// Carregar um documento contendo imagens
Document doc = new Document("document_with_images.docx");

// Defina o caminho da pasta de imagens
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Salvar o documento com imagens
doc.save("document_with_images.md", saveOptions);
```

 Certifique-se de substituir`"document_with_images.docx"` com o caminho para o seu documento do Word contendo imagens e`"images_folder/"` com o caminho real para a pasta onde suas imagens estão armazenadas.

## Código fonte completo para salvar documentos como Markdown no Aspose.Words para Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Faz com que todos os parágrafos dentro da tabela sejam alinhados.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// O alinhamento neste caso será obtido a partir do primeiro parágrafo na coluna correspondente da tabela.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Conclusão

Neste guia, exploramos como salvar documentos como Markdown usando Aspose.Words para Java. Cobrimos a criação de um documento Word, a personalização do alinhamento de conteúdo de tabela e o manuseio de imagens em arquivos Markdown. Agora você pode converter seus documentos Word para o formato Markdown de forma eficiente, tornando-os adequados para várias plataformas de publicação e necessidades de documentação.

## Perguntas frequentes

### Como instalo o Aspose.Words para Java?

 O Aspose.Words para Java pode ser instalado incluindo a biblioteca no seu projeto Java. Você pode baixar a biblioteca em[aqui](https://releases.aspose.com/words/java/) e siga as instruções de instalação fornecidas na documentação.

### Posso converter documentos complexos do Word com tabelas e imagens para Markdown?

Sim, o Aspose.Words para Java suporta a conversão de documentos Word complexos com tabelas, imagens e vários elementos de formatação para Markdown. Você pode personalizar a saída Markdown de acordo com a complexidade do seu documento.

### Como posso manipular imagens em arquivos Markdown?

 Para incluir imagens em arquivos Markdown, defina o caminho da pasta de imagens usando o`setImagesFolder`método em`MarkdownSaveOptions`. Certifique-se de que os arquivos de imagem estejam armazenados na pasta especificada e o Aspose.Words para Java manipulará as referências de imagem adequadamente.

### Existe uma versão de teste do Aspose.Words para Java disponível?

Sim, você pode obter uma versão de teste do Aspose.Words para Java no site da Aspose. A versão de teste permite que você avalie os recursos da biblioteca antes de comprar uma licença.

### Onde posso encontrar mais exemplos e documentação?

 Para mais exemplos, documentação e informações detalhadas sobre Aspose.Words para Java, visite o[documentação](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
