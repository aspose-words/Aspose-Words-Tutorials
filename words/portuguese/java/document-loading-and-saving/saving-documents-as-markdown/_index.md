---
date: 2025-12-22
description: Aprenda a exportar markdown convertendo documentos Word para Markdown
  com Aspose.Words for Java. Este guia passo a passo aborda o alinhamento de tabelas,
  o tratamento de imagens e muito mais.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Como Exportar Markdown com Aspose.Words para Java
url: /pt/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Exportar Markdown com Aspose.Words para Java

## Introdução à Exportação de Markdown no Aspose.Words para Java

Neste tutorial passo a passo, **você aprenderá como exportar markdown** de documentos Word usando Aspose.Words para Java. Markdown é uma linguagem de marcação leve que é perfeita para documentação, geradores de sites estáticos e muitas plataformas de publicação. Ao final deste guia, você será capaz de **converter Word para markdown**, personalizar o alinhamento de tabelas e **manipular imagens em markdown** sem esforço.

## Respostas Rápidas
- **Qual é a classe principal para salvar como Markdown?** `MarkdownSaveOptions`
- **As imagens podem ser incorporadas automaticamente?** Sim – defina a pasta de imagens via `setImagesFolder`.
- **Como controlo o alinhamento da tabela?** Use `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Quais são os requisitos mínimos?** JDK 8+ e a biblioteca Aspose.Words para Java.
- **Uma versão de avaliação está disponível?** Sim, faça o download no site da Aspose.

## O que é “exportar markdown”?
Exportar markdown significa pegar um documento Word de texto rico (`.docx`) e gerar um arquivo de texto simples `.md` que preserva títulos, tabelas e imagens na sintaxe Markdown.

## Por que usar Aspose.Words para Java para converter docx com imagens?
Aspose.Words lida com layouts complexos, imagens incorporadas e estruturas de tabelas sem perder fidelidade. Ele também oferece controle detalhado sobre a saída Markdown, como alinhamento de tabelas e gerenciamento da pasta de imagens.

## Pré‑requisitos

- Java Development Kit (JDK) instalado no seu sistema.
- Biblioteca Aspose.Words para Java. Você pode baixá‑la [aqui](https://releases.aspose.com/words/java/).

## Etapa 1: Criar um documento Word simples

Primeiro, criaremos um pequeno documento que contém uma tabela. Isso nos permitirá demonstrar **personalizar o alinhamento da tabela** mais tarde.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

No trecho acima, nós:

1. Criamos um novo `Document`.
2. Usamos `DocumentBuilder` para inserir uma tabela de duas células.
3. Aplicamos alinhamento de parágrafo **direito** e **centralizado** dentro de cada célula.
4. Salvamos o arquivo como Markdown usando `MarkdownSaveOptions`.

## Etapa 2: Personalizar o alinhamento do conteúdo da tabela

Aspose.Words permite que você defina como as células da tabela são renderizadas no Markdown final. Você pode forçar o alinhamento à esquerda, direita, centralizado, ou deixar a biblioteca decidir automaticamente com base no primeiro parágrafo de cada coluna.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Ao alterar a propriedade `TableContentAlignment`, você controla **personalizar o alinhamento da tabela** para a saída Markdown.

## Etapa 3: Manipular imagens ao exportar para markdown

Quando um documento contém imagens, você desejará que essas imagens apareçam corretamente no arquivo `.md` gerado. Defina a pasta onde o Aspose.Words deve armazenar as imagens extraídas.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Substitua `"document_with_images.docx"` pelo caminho do seu arquivo fonte e `"images_folder/"` pela localização onde você deseja armazenar as imagens. O Markdown resultante conterá links de imagem que apontam para essa pasta, permitindo que você **manipule imagens em markdown** sem problemas.

## Código‑Fonte Completo para Salvar Documentos como Markdown no Aspose.Words para Java

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## Problemas Comuns e Soluções

| Problema | Solução |
|----------|---------|
| Imagens não aparecem no arquivo `.md` | Verifique se `setImagesFolder` aponta para um diretório gravável e se a pasta está referenciada corretamente no Markdown gerado. |
| Alinhamento da tabela parece incorreto | Use `TableContentAlignment.AUTO` para permitir que o Aspose.Words infera o melhor alinhamento com base no primeiro parágrafo de cada coluna. |
| Arquivo de saída está vazio | Certifique‑se de que o objeto `Document` realmente contém conteúdo antes de chamar `save`. |

## Perguntas Frequentes

**Q: Como instalo o Aspose.Words para Java?**  
A: O Aspose.Words para Java pode ser instalado incluindo a biblioteca no seu projeto Java. Você pode baixar a biblioteca [aqui](https://releases.aspose.com/words/java/) e seguir as instruções de instalação fornecidas na documentação.

**Q: Posso converter documentos Word complexos com tabelas e imagens para Markdown?**  
A: Sim, o Aspose.Words para Java suporta a conversão de documentos Word complexos com tabelas, imagens e vários elementos de formatação para Markdown. Você pode personalizar a saída Markdown de acordo com a complexidade do seu documento.

**Q: Como posso manipular imagens em arquivos Markdown?**  
A: Defina o caminho da pasta de imagens usando o método `setImagesFolder` em `MarkdownSaveOptions`. Certifique‑se de que os arquivos de imagem sejam armazenados na pasta especificada; o Aspose.Words gerará os links de imagem Markdown apropriados.

**Q: Existe uma versão de avaliação do Aspose.Words para Java disponível?**  
A: Sim, você pode obter uma versão de avaliação do Aspose.Words para Java no site da Aspose. A versão de avaliação permite avaliar as capacidades da biblioteca antes de adquirir uma licença.

**Q: Onde posso encontrar mais exemplos e documentação?**  
A: Para mais exemplos, documentação e informações detalhadas sobre o Aspose.Words para Java, visite a [documentação](https://reference.aspose.com/words/java/).

---

**Última Atualização:** 2025-12-22  
**Testado Com:** Aspose.Words para Java 24.12 (mais recente no momento da escrita)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}