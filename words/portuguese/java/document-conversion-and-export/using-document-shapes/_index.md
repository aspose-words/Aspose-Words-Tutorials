---
"description": "Descubra o poder dos formatos de documentos no Aspose.Words para Java. Aprenda a criar documentos visualmente envolventes com exemplos passo a passo."
"linktitle": "Usando formas de documento"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Usando formas de documentos no Aspose.Words para Java"
"url": "/pt/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando formas de documentos no Aspose.Words para Java


## Introdução ao uso de formas de documentos no Aspose.Words para Java

Neste guia completo, vamos nos aprofundar no mundo das formas de documentos no Aspose.Words para Java. As formas são elementos essenciais para criar documentos visualmente atraentes e interativos. Seja para adicionar chamadas, botões, imagens ou marcas d'água, o Aspose.Words para Java oferece as ferramentas necessárias para isso com eficiência. Vamos explorar como usar essas formas passo a passo com exemplos de código-fonte.

## Introdução aos formatos de documentos

Antes de começarmos a programar, vamos configurar nosso ambiente. Certifique-se de ter o Aspose.Words para Java integrado ao seu projeto. Se ainda não o fez, você pode baixá-lo do site do Aspose. [Baixe Aspose.Words para Java](https://releases.aspose.com/words/java/)

## Adicionando formas aos documentos

### Inserindo um GroupShape

UM `GroupShape` permite agrupar várias formas. Veja como você pode criar e inserir uma `GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### Inserindo uma forma de caixa de texto

Para inserir uma forma de caixa de texto, você pode usar o `insertShape` método conforme mostrado no exemplo abaixo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Manipulando Propriedades de Forma

### Gerenciando a proporção da tela

Você pode controlar se a proporção de uma forma está bloqueada ou não. Veja como desbloquear a proporção de uma forma:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Colocando uma forma em uma célula de tabela

Se você precisar colocar uma forma dentro de uma célula de tabela, poderá fazer isso com o seguinte código:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Exiba a forma fora da célula da tabela se ela for colocada em uma célula.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Trabalhando com formas SmartArt

### Detectando Formas SmartArt

Você pode detectar formas SmartArt em um documento usando o seguinte código:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Atualizando desenhos SmartArt

Para atualizar desenhos SmartArt em um documento, use o seguinte código:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusão

Neste guia, exploramos o mundo das formas de documentos no Aspose.Words para Java. Você aprendeu a adicionar diversas formas aos seus documentos, manipular suas propriedades e trabalhar com formas SmartArt. Com esse conhecimento, você poderá criar documentos visualmente atraentes e interativos com facilidade.

## Perguntas frequentes

### O que é Aspose.Words para Java?

Aspose.Words para Java é uma biblioteca Java que permite aos desenvolvedores criar, modificar e converter documentos do Word programaticamente. Ela oferece uma ampla gama de recursos e ferramentas para trabalhar com documentos em diversos formatos.

### Como posso baixar o Aspose.Words para Java?

Você pode baixar o Aspose.Words para Java no site da Aspose seguindo este link: [Baixe Aspose.Words para Java](https://releases.aspose.com/words/java/)

### Quais são os benefícios de usar formas de documentos?

As formas de documento adicionam elementos visuais e interatividade aos seus documentos, tornando-os mais envolventes e informativos. Com as formas, você pode criar chamadas, botões, imagens, marcas d'água e muito mais, aprimorando a experiência geral do usuário.

### Posso personalizar a aparência das formas?

Sim, você pode personalizar a aparência das formas ajustando suas propriedades, como tamanho, posição, rotação e cor de preenchimento. O Aspose.Words para Java oferece diversas opções para personalização de formas.

### Aspose.Words para Java é compatível com o SmartArt?

Sim, o Aspose.Words para Java suporta formas SmartArt, permitindo que você trabalhe com diagramas e gráficos complexos em seus documentos.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}