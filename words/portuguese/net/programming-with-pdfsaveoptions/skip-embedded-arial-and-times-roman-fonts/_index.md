---
title: Otimize o tamanho do PDF com fontes Arial e Times Roman incorporadas
linktitle: Otimize o tamanho do PDF com fontes Arial e Times Roman incorporadas
second_title: API de processamento de documentos Aspose.Words
description: Otimize o tamanho do PDF ignorando fontes Arial e Times Roman incorporadas usando o Aspose.Words para .NET. Siga este guia passo a passo para otimizar seus arquivos PDF.
weight: 10
url: /pt/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Otimize o tamanho do PDF com fontes Arial e Times Roman incorporadas

## Introdução

Já se viu em uma situação em que o tamanho do seu arquivo PDF é muito grande? É como fazer as malas para as férias e perceber que sua mala está estourando pelas costuras. Você sabe que precisa perder peso, mas do que você se livra? Ao trabalhar com arquivos PDF, especialmente aqueles convertidos de documentos do Word, fontes incorporadas podem aumentar o tamanho do arquivo. Felizmente, o Aspose.Words para .NET fornece uma solução elegante para manter seus PDFs enxutos e eficientes. Neste tutorial, vamos nos aprofundar em como otimizar o tamanho do seu PDF pulando as fontes Arial e Times Roman incorporadas. Vamos começar!

## Pré-requisitos

Antes de começarmos, há algumas coisas que você vai precisar:
-  Aspose.Words para .NET: Certifique-se de ter essa biblioteca poderosa instalada. Se não, você pode baixá-la de[aqui](https://releases.aspose.com/words/net/).
- Um conhecimento básico de C#: isso ajudará você a acompanhar os trechos de código.
- Um documento do Word: usaremos um documento de exemplo para demonstrar o processo. 

## Importar namespaces

Primeiro, certifique-se de ter os namespaces necessários importados. Isso prepara o cenário para acessar as funcionalidades do Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tudo bem, vamos detalhar o processo passo a passo.

## Etapa 1: configure seu ambiente

Para começar, você precisa configurar seu ambiente de desenvolvimento. Abra seu IDE C# favorito (como o Visual Studio) e crie um novo projeto.

## Etapa 2: Carregue o documento do Word

O próximo passo é carregar o documento do Word que você quer converter para PDF. Certifique-se de que seu documento esteja no diretório correto.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Neste trecho, substitua`"YOUR DOCUMENT DIRECTORY"` com o caminho para o diretório do seu documento.

## Etapa 3: Configurar opções de salvamento de PDF

Agora, precisamos configurar as opções de salvamento de PDF para controlar como as fontes são incorporadas. Por padrão, todas as fontes são incorporadas, o que pode aumentar o tamanho do arquivo. Vamos alterar essa configuração.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## Etapa 4: Salve o documento como PDF

Por fim, salve o documento como PDF com as opções de salvamento especificadas. É aqui que a mágica acontece.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

Este comando salva seu documento como um PDF chamado "OptimizedPDF.pdf" no diretório especificado.

## Conclusão

aí está! Você acabou de aprender como otimizar o tamanho do seu arquivo PDF pulando a incorporação de fontes Arial e Times Roman usando o Aspose.Words para .NET. Esse simples ajuste pode reduzir significativamente o tamanho dos seus arquivos, tornando-os mais fáceis de compartilhar e armazenar. É como ir à academia para seus PDFs, eliminando peso desnecessário enquanto mantém todos os itens essenciais intactos.

## Perguntas frequentes

### Por que devo pular a incorporação de fontes Arial e Times Roman?
Ignorar essas fontes comuns pode reduzir o tamanho do arquivo PDF, pois a maioria dos sistemas já tem essas fontes instaladas.

### Isso afetará a aparência do meu PDF?
Não, não vai. Como Arial e Times Roman são fontes padrão, a aparência permanece consistente em diferentes sistemas.

### Posso pular a incorporação de outras fontes também?
Sim, você pode configurar as opções de salvamento para pular a incorporação de outras fontes, se necessário.

### O Aspose.Words para .NET é gratuito?
 Aspose.Words para .NET oferece um teste gratuito que você pode baixar[aqui](https://releases.aspose.com/) , mas para acesso total, você precisa comprar uma licença[aqui](https://purchase.aspose.com/buy).

### Onde posso encontrar mais tutoriais sobre Aspose.Words para .NET?
Você pode encontrar documentação e tutoriais abrangentes[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
