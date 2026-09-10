---
date: 2025-12-18
description: Aprenda como adicionar marca d'água a documentos com Aspose.Words for
  Java, incluindo exemplo de marca d'água de imagem, alterar a cor da marca d'água,
  definir a transparência da marca d'água e remover a marca d'água do documento.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Como adicionar marca d'água a documentos usando Aspose.Words para Java
url: /pt/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Adicionar Marca d'Água a Documentos Usando Aspose.Words para Java

## Introdução à Adição de Marcas d'Água a Documentos no Aspose.Words para Java

Neste tutorial você aprenderá **como adicionar marca d'água** a documentos Word com Aspose.Words para Java. Marcas d'água são uma maneira rápida de rotular um arquivo como confidencial, rascunho ou aprovado, e podem ser baseadas em texto ou em imagem. Vamos percorrer a configuração da biblioteca, a criação de marcas d'água de texto e de imagem, a personalização de sua aparência (incluindo alteração da cor da marca d'água e definição da transparência da marca d'água), e até a remoção de uma marca d'água do documento quando não for mais necessária.

## Respostas Rápidas
- **O que é uma marca d'água?** Uma sobreposição semitransparente (texto ou imagem) que aparece atrás do conteúdo principal do documento.  
- **Posso adicionar várias marcas d'água?** Sim – crie vários objetos `Shape` e adicione cada um às seções desejadas.  
- **Como altero a cor da marca d'água?** Ajuste a propriedade `Color` em `TextWatermarkOptions`.  
- **Existe um exemplo de marca d'água de imagem?** Veja a seção “Adicionando Marcas d'Água de Imagem” abaixo.  
- **Preciso de licença para remover uma marca d'água?** É necessária uma licença válida do Aspose.Words para uso em produção.

## Configurando Aspose.Words para Java

Antes de começarmos a adicionar marcas d'água aos documentos, precisamos configurar o Aspose.Words para Java. Siga estas etapas para começar:

1. Baixe o Aspose.Words para Java em [aqui](https://releases.aspose.com/words/java/).  
2. Adicione a biblioteca Aspose.Words para Java ao seu projeto Java.  
3. Importe as classes necessárias no seu código Java.

Agora que temos a biblioteca configurada, vamos mergulhar na criação real da marca d'água.

## Adicionando Marcas d'Água de Texto

Marcas d'água de texto são uma escolha comum quando você deseja adicionar informações textuais aos seus documentos. Veja como você pode adicionar uma marca d'água de texto usando Aspose.Words para Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Por que isso importa:** Ajustando `setFontFamily`, `setFontSize` e `setColor` você pode **alterar a cor da marca d'água** para combinar com a identidade da sua marca, e `setSemitransparent(true)` permite que você **defina a transparência da marca d'água** para um efeito sutil.

## Adicionando Marcas d'Água de Imagem

Além das marcas d'água de texto, você também pode adicionar marcas d'água de imagem aos seus documentos. Abaixo está um **exemplo de marca d'água de imagem** que demonstra como incorporar um logotipo ou selo PNG:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Você pode repetir este bloco com diferentes imagens ou posições para **adicionar várias marcas d'água** a um único arquivo.

## Personalizando Marcas d'Água

Você pode personalizar marcas d'água ajustando sua aparência e posição. Para marcas d'água de texto, você pode alterar a fonte, tamanho, cor e layout. Para marcas d'água de imagem, você pode modificar o tamanho, rotação e alinhamento conforme demonstrado nos exemplos anteriores.

## Removendo Marcas d'Água

Se precisar **remover o conteúdo da marca d'água** do documento, o código a seguir percorre todas as formas e exclui aquelas identificadas como marcas d'água:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Casos de Uso Comuns & Dicas

- **Rascunhos confidenciais:** Aplique uma marca d'água de texto semitransparente como “CONFIDENTIAL”.  
- **Branding:** Use uma marca d'água de imagem que contenha o logotipo da sua empresa.  
- **Marcas d'água específicas por seção:** Percorra `doc.getSections()` e adicione uma marca d'água apenas nas seções que você escolher.  
- **Dica de desempenho:** Reutilize a mesma instância de `TextWatermarkOptions` ao aplicar a mesma marca d'água em vários documentos.

## Perguntas Frequentes

### Como posso mudar a fonte de uma marca d'água de texto?

Para mudar a fonte de uma marca d'água de texto, modifique a propriedade `setFontFamily` em `TextWatermarkOptions`. Por exemplo:

```java
options.setFontFamily("Times New Roman");
```

### Posso adicionar várias marcas d'água a um único documento?

Sim, você pode adicionar várias marcas d'água a um documento criando múltiplos objetos `Shape` com configurações diferentes e adicionando-os ao documento.

### É possível girar uma marca d'água?

Sim, você pode girar uma marca d'água definindo a propriedade `setRotation` no objeto `Shape`. Valores positivos giram a marca d'água no sentido horário, e valores negativos giram no sentido anti‑horário.

### Como posso tornar uma marca d'água semitransparente?

Para tornar uma marca d'água semitransparente, defina a propriedade `setSemitransparent` como `true` em `TextWatermarkOptions`.

### Posso adicionar marcas d'água a seções específicas de um documento?

Sim, você pode adicionar marcas d'água a seções específicas de um documento percorrendo as seções e adicionando a marca d'água às seções desejadas.

---

**Última Atualização:** 2025-12-18  
**Testado com:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}