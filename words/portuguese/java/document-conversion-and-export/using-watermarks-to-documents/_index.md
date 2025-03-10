---
title: Usando marcas d'água em documentos no Aspose.Words para Java
linktitle: Usando marcas d'água em documentos
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda como adicionar marcas d'água a documentos no Aspose.Words para Java. Personalize marcas d'água de texto e imagem para documentos com aparência profissional.
weight: 15
url: /pt/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usando marcas d'água em documentos no Aspose.Words para Java


## Introdução à adição de marcas d'água em documentos no Aspose.Words para Java

Neste tutorial, exploraremos como adicionar marcas d'água a documentos usando o Aspose.Words para API Java. Marcas d'água são uma maneira útil de rotular documentos com texto ou gráficos para indicar seu status, confidencialidade ou outras informações relevantes. Abordaremos marcas d'água de texto e imagem neste guia.

## Configurando Aspose.Words para Java

Antes de começarmos a adicionar marcas d'água a documentos, precisamos configurar o Aspose.Words para Java. Siga estas etapas para começar:

1.  Baixe Aspose.Words para Java em[aqui](https://releases.aspose.com/words/java/).
2. Adicione a biblioteca Aspose.Words for Java ao seu projeto Java.
3. Importe as classes necessárias no seu código Java.

Agora que configuramos a biblioteca, vamos prosseguir para adicionar marcas d'água.

## Adicionar marcas d'água de texto

Marcas d'água de texto são uma escolha comum quando você quer adicionar informações textuais aos seus documentos. Veja como você pode adicionar uma marca d'água de texto usando Aspose.Words para Java:

```java
// Criar uma instância de documento
Document doc = new Document("Document.docx");

// Definir TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Defina o texto e as opções da marca d'água
doc.getWatermark().setText("Test", options);

// Salve o documento com a marca d'água
doc.save("DocumentWithWatermark.docx");
```

## Adicionar marcas d'água de imagem

Além de marcas d'água de texto, você também pode adicionar marcas d'água de imagem aos seus documentos. Veja como adicionar uma marca d'água de imagem:

```java
// Criar uma instância de documento
Document doc = new Document("Document.docx");

// Carregue a imagem para a marca d'água
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Defina o tamanho e a posição da marca d'água
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Adicione a marca d'água ao documento
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Salve o documento com a marca d'água
doc.save("DocumentWithImageWatermark.docx");
```

## Personalizando marcas d'água

Você pode personalizar marcas d'água ajustando sua aparência e posição. Para marcas d'água de texto, você pode alterar a fonte, o tamanho, a cor e o layout. Para marcas d'água de imagem, você pode modificar seu tamanho e posição, conforme demonstrado nos exemplos anteriores.

## Removendo marcas d'água

Para remover marcas d'água de um documento, você pode usar o seguinte código:

```java
// Criar uma instância de documento
Document doc = new Document("DocumentWithWatermark.docx");

// Remover a marca d'água
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Salve o documento sem a marca d'água
doc.save("DocumentWithoutWatermark.docx");
```


## Conclusão

Neste tutorial, aprendemos como adicionar marcas d'água a documentos usando o Aspose.Words para Java. Se você precisa adicionar marcas d'água de texto ou imagem, o Aspose.Words fornece as ferramentas para personalizá-las e gerenciá-las de forma eficiente. Você também pode remover marcas d'água quando elas não forem mais necessárias, garantindo que seus documentos estejam limpos e profissionais.

## Perguntas frequentes

### Como posso alterar a fonte de uma marca d'água de texto?

 Para alterar a fonte de uma marca d'água de texto, modifique o`setFontFamily` propriedade no`TextWatermarkOptions`. Por exemplo:

```java
options.setFontFamily("Times New Roman");
```

### Posso adicionar várias marcas d'água a um único documento?

 Sim, você pode adicionar várias marcas d'água a um documento criando várias`Shape` objetos com configurações diferentes e adicioná-los ao documento.

### É possível girar uma marca d'água?

 Sim, você pode girar uma marca d'água definindo o`setRotation` propriedade no`Shape` objeto. Valores positivos giram a marca d'água no sentido horário, e valores negativos giram no sentido anti-horário.

### Como posso tornar uma marca d'água semitransparente?

 Para tornar uma marca d'água semitransparente, defina o`setSemitransparent`propriedade para`true` no`TextWatermarkOptions`.

### Posso adicionar marcas d'água a seções específicas de um documento?

Sim, você pode adicionar marcas d'água a seções específicas de um documento iterando pelas seções e adicionando a marca d'água às seções desejadas.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
