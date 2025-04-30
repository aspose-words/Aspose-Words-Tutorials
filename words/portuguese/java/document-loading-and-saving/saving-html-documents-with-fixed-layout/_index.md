---
"description": "Aprenda a salvar documentos HTML com layout fixo no Aspose.Words para Java. Siga nosso guia passo a passo para uma formatação de documentos perfeita."
"linktitle": "Salvando documentos HTML com layout fixo"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Salvando documentos HTML com layout fixo no Aspose.Words para Java"
"url": "/pt/java/document-loading-and-saving/saving-html-documents-with-fixed-layout/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Salvando documentos HTML com layout fixo no Aspose.Words para Java


## Introdução ao salvamento de documentos HTML com layout fixo no Aspose.Words para Java

Neste guia completo, mostraremos o processo de salvar documentos HTML com um layout fixo usando o Aspose.Words para Java. Com instruções passo a passo e exemplos de código, você aprenderá como fazer isso perfeitamente. Então, vamos começar!

## Pré-requisitos

Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:

- Ambiente de desenvolvimento Java configurado.
- Biblioteca Aspose.Words para Java instalada e configurada.

## Etapa 1: Carregando o documento

Primeiro, precisamos carregar o documento que queremos salvar em formato HTML. Veja como fazer isso:

```java
Document doc = new Document("Your Directory Path" + "YourDocument.docx");
```

Substituir `"YourDocument.docx"` com o caminho para seu documento do Word.

## Etapa 2: Configurar opções de salvamento fixo em HTML

Para salvar o documento com um layout fixo, precisamos configurar o `HtmlFixedSaveOptions` classe. Vamos definir o `useTargetMachineFonts` propriedade para `true` para garantir que as fontes da máquina de destino sejam usadas na saída HTML:

```java
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
saveOptions.setUseTargetMachineFonts(true);
```

## Etapa 3: Salve o documento como HTML

Agora, vamos salvar o documento como HTML com o layout fixo usando as opções configuradas anteriormente:

```java
doc.save("Your Directory Path" + "FixedLayoutDocument.html", saveOptions);
```

Substituir `"FixedLayoutDocument.html"` com o nome desejado para seu arquivo HTML.

## Código-fonte completo para salvar documentos HTML com layout fixo no Aspose.Words para Java

```java
        Document doc = new Document("Your Directory Path" + "Bullet points with alternative font.docx");
        HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
        {
            saveOptions.setUseTargetMachineFonts(true);
        }
        doc.save("Your Directory Path" + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
    }
```

## Conclusão

Neste tutorial, aprendemos como salvar documentos HTML com um layout fixo usando o Aspose.Words para Java. Seguindo estes passos simples, você pode garantir que seus documentos mantenham uma estrutura visual consistente em diferentes plataformas.

## Perguntas frequentes

### Como posso configurar o Aspose.Words para Java no meu projeto?

Configurar o Aspose.Words para Java é simples. Você pode baixar a biblioteca em [aqui](https://releases.aspose.com/words/java/) e siga as instruções de instalação fornecidas na documentação [aqui](https://reference.aspose.com/words/java/).

### Há algum requisito de licenciamento para usar o Aspose.Words para Java?

Sim, o Aspose.Words para Java requer uma licença válida para uso em ambiente de produção. Você pode obter uma licença no site do Aspose. Mais detalhes podem ser encontrados na documentação.

### Posso personalizar ainda mais a saída HTML?

Com certeza! O Aspose.Words para Java oferece uma ampla gama de opções para personalizar a saída HTML de acordo com suas necessidades específicas. Você pode consultar a documentação para obter informações detalhadas sobre as opções de personalização.

### O Aspose.Words para Java é compatível com diferentes versões do Java?

Sim, o Aspose.Words para Java é compatível com diversas versões do Java. Certifique-se de usar uma versão compatível do Aspose.Words para Java que corresponda ao seu ambiente de desenvolvimento Java.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}