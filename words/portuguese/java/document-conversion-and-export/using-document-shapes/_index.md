---
date: 2026-02-16
description: Aprenda como criar caixa de texto, adicionar marca d'água de palavra,
  agrupar várias formas, definir a proporção da forma e colocar a forma em uma célula
  de tabela usando Aspose.Words para Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Como criar caixa de texto e usar Formas de Documento no Aspose.Words para Java
url: /pt/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando Formas de Documento no Aspose.Words para Java

## Introdução ao Uso de Formas de Documento no Aspose.Words para Java

Neste guia abrangente, **você aprenderá a criar text box** objetos e outras formas poderosas com Aspose.Words para Java. As formas permitem enriquecer documentos Word com chamadas, botões, marcas d'água, SmartArt e muito mais—tornando-os visualmente atraentes e interativos. Percorreremos exemplos do mundo real, desde a inserção de um simples text box até agrupar várias formas, definir proporções de aspecto e posicionar formas dentro de células de tabela.

## Respostas Rápidas
- **Qual é a maneira principal de adicionar um text box?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Posso agrupar formas juntas?** Sim – crie um `GroupShape` e anexe formas filhas.
- **Como bloqueio ou desbloqueio a proporção de aspecto de uma forma?** Chame `shape.setAspectRatioLocked(true/false)`.
- **É possível adicionar uma marca d'água com uma forma?** Absolutamente – insira um `Shape` com `TEXT_PLAIN_TEXT` e defina seu preenchimento/contorno.
- **Diagramas SmartArt funcionam com Aspose.Words?** Sim – detecte com `shape.hasSmartArt()` e atualize via `shape.updateSmartArtDrawing()`.

## O que é um text box e por que criar formas de text box?

Um text box é um contêiner que pode conter texto formatado, imagens ou outras formas. Usar **criar text box** na sua automação permite posicionar conteúdo flutuante em qualquer parte da página, perfeito para anotações, chamadas ou elementos decorativos sem alterar o fluxo principal do documento.

## Como adicionar forma

Antes de mergulharmos no código, certifique‑se de que o Aspose.Words para Java está referenciado no seu projeto. Se ainda não o adicionou, baixe a biblioteca do site oficial:

[Baixar Aspose.Words para Java](https://releases.aspose.com/words/java/)

### Adicionando Formas a Documentos

## Como agrupar várias formas

Um `GroupShape` permite tratar várias formas individuais como uma única unidade—útil para mover ou girar todas juntas.

### Inserindo um GroupShape

A seguir, um exemplo completo que cria um grupo, adiciona duas formas diferentes e insere o grupo no documento.

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

## Como criar um text box (criar text box)

### Inserindo uma Forma de Text Box

O método `insertShape` facilita a adição de um text box. O exemplo abaixo mostra duas maneiras de posicionar e girar um text box.

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

## Como definir a proporção de aspecto da forma

### Gerenciando a Proporção de Aspecto

Às vezes, você precisa que uma forma se estique sem preservar suas proporções originais. O trecho a seguir demonstra como desbloquear a proporção de aspecto de uma forma de imagem.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Como posicionar forma em uma célula de tabela

### Posicionando uma Forma Dentro de uma Célula de Tabela

A seguir, um exemplo passo a passo que cria uma tabela e, em seguida, insere uma forma de marca d'água posicionada em relação à página, mas que também pode ser colocada dentro de uma célula.

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

## Trabalhando com Formas SmartArt

### Detectando Formas SmartArt

Você pode encontrar programaticamente objetos SmartArt em um documento usando o método `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Atualizando Desenhos SmartArt

Depois de localizar as formas SmartArt, você pode atualizar seus dados internos de desenho com `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusão

Neste guia, cobrimos como **criar text box** objetos, agrupar várias formas, ajustar proporções de aspecto, incorporar formas dentro de células de tabela, adicionar marcas d'água e trabalhar com diagramas SmartArt usando Aspose.Words para Java. Essas técnicas permitem que você construa documentos Word ricos em formatação e interatividade de forma programática.

## Perguntas Frequentes

### O que é Aspose.Words para Java?

Aspose.Words para Java é uma biblioteca Java que permite aos desenvolvedores criar, modificar e converter documentos Word programaticamente. Ela oferece uma ampla gama de recursos e ferramentas para trabalhar com documentos em vários formatos.

### Como posso baixar Aspose.Words para Java?

Você pode baixar Aspose.Words para Java no site da Aspose seguindo este link: [Baixar Aspose.Words para Java](https://releases.aspose.com/words/java/)

### Quais são os benefícios de usar formas de documento?

Formas de documento adicionam elementos visuais e interatividade aos seus documentos, tornando‑os mais envolventes e informativos. Com formas, você pode criar chamadas, botões, imagens, marcas d'água e muito mais, aprimorando a experiência geral do usuário.

### Posso personalizar a aparência das formas?

Sim, você pode personalizar a aparência das formas ajustando propriedades como tamanho, posição, rotação e cor de preenchimento. Aspose.Words para Java fornece opções extensas para personalização de formas.

### Aspose.Words para Java é compatível com SmartArt?

Sim, Aspose.Words para Java suporta formas SmartArt, permitindo que você trabalhe com diagramas e gráficos complexos em seus documentos.

## Perguntas Frequentes

**Q: Posso combinar um text box com uma imagem dentro da mesma forma?**  
A: Sim. Insira uma imagem na forma de text box usando `builder.insertImage()` após criar a forma, então ajuste seu layout conforme necessário.

**Q: Como garanto que uma marca d'água apareça atrás de todo o conteúdo do documento?**  
A: Defina o `WrapType` da forma para `NONE` e ajuste `RelativeHorizontalPosition` e `RelativeVerticalPosition` para `PAGE`. Isso posiciona a marca d'água atrás do fluxo principal.

**Q: É possível animar uma forma agrupada no Word?**  
A: Embora o Aspose.Words possa criar e agrupar formas, os recursos de animação não são suportados porque dependem das capacidades da interface do Word.

**Q: Qual versão do Aspose.Words é necessária para suporte a SmartArt?**  
A: A detecção e atualização de SmartArt estão disponíveis a partir do Aspose.Words 20.9 para Java e versões posteriores.

**Q: A biblioteca lida eficientemente com documentos grandes contendo muitas formas?**  
A: Sim. Use `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` ou superior para melhorar o desempenho em documentos com muitas formas.

---

**Última atualização:** 2026-02-16  
**Testado com:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}