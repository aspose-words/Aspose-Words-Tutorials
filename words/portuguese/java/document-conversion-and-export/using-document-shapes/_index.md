---
date: 2025-12-14
description: Aprenda como **inserir forma de imagem** com Aspose.Words para Java.
  Este guia mostra como adicionar formas, criar formas de caixa de texto, colocar
  formas em tabelas, definir a proporção da forma e adicionar formas de balão de chamada.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Usando Formas de Documento no Aspose.Words para Java
url: /pt/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como **insert image shape** com Aspose.Words for Java

Neste tutorial abrangente, você descobrirá como **insert image shape** objetos em documentos Word usando Aspose.Words for Java. Seja criando relatórios, materiais de marketing ou formulários interativos, as formas permitem adicionar balões de texto, botões, caixas de texto, marcas d'água e até SmartArt. Vamos percorrer cada passo, explicar por que usar uma forma específica e fornecer trechos de código prontos para execução.

## Respostas rápidas
- **Qual é a maneira principal de adicionar uma forma?** Use `DocumentBuilder.insertShape` ou crie uma instância `Shape` e adicione-a à árvore do documento.  
- **Posso inserir uma imagem como forma?** Sim – chame `builder.insertImage` e trate o `Shape` retornado como qualquer outro.  
- **Como mantenho a proporção de uma forma?** Defina `shape.setAspectRatioLocked(true)` ou `false` conforme sua necessidade.  
- **É possível agrupar formas?** Absolutamente – envolva-as em um `GroupShape` e insira o grupo como um único nó.  
- **Diagramas SmartArt funcionam com Aspose.Words?** Sim, você pode detectar e atualizar formas SmartArt programaticamente.

## O que é **insert image shape**?
Um *image shape* é um elemento visual que contém gráficos raster ou vetoriais dentro de um documento Word. No Aspose.Words, uma imagem é representada por um objeto `Shape`, oferecendo controle total sobre tamanho, posição, rotação e quebra de texto.

## Por que usar formas em seus documentos?
- **Impacto visual:** As formas chamam a atenção para informações importantes.  
- **Interatividade:** Botões e balões de texto podem ser vinculados a URLs ou marcadores.  
- **Flexibilidade de layout:** Posicione gráficos com precisão usando coordenadas absolutas ou relativas.  
- **Automação:** Gere layouts complexos sem edição manual.

## Pré-requisitos
- Java Development Kit (JDK 8 ou superior)  
- Biblioteca Aspose.Words for Java (download no site oficial)  
- Conhecimento básico de Java e programação orientada a objetos  

Você pode baixar a biblioteca aqui: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Como **add shape** – Inserindo um GroupShape
Um `GroupShape` permite tratar várias formas como uma única unidade. Isso é útil para mover ou formatar vários elementos juntos.

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

## Criar **text box shape**
Uma caixa de texto é um contêiner que pode conter texto formatado. Você também pode girá‑la para um visual dinâmico.

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

## Definir **shape aspect ratio**
Às vezes você precisa que uma forma se estique livremente; em outras situações, deseja manter suas proporções originais. Controlar a proporção é simples.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Colocar **shape in table**
Inserir uma forma dentro de uma célula de tabela pode ser útil em layouts de relatórios. O exemplo abaixo cria uma tabela e, em seguida, insere uma forma estilo marca d'água que ocupa a página inteira.

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

## Adicionar **callout shape**
Uma forma de balão de texto é perfeita para destacar notas ou avisos. Embora o código acima já demonstre um `ACCENT_BORDER_CALLOUT_1`, você pode trocar o `ShapeType` por qualquer variante de balão para adequar ao seu design.

## Trabalhando com Formas SmartArt

### Detectar Formas SmartArt
Diagramas SmartArt podem ser identificados programaticamente, permitindo processá‑los ou substituí‑los conforme necessário.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Atualizar Desenhos SmartArt
Uma vez detectados, você pode atualizar os gráficos SmartArt para refletir quaisquer alterações nos dados.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Problemas comuns & Dicas
- **Forma não aparece:** Certifique‑se de que a forma seja inserida após o nó alvo usando `builder.insertNode`.  
- **Rotação inesperada:** Lembre‑se de que a rotação é aplicada ao redor do centro da forma; ajuste `setLeft`/`setTop` se necessário.  
- **Proporção travada:** Por padrão, muitas formas bloqueiam sua proporção; chame `setAspectRatioLocked(false)` para esticar livremente.  
- **Falha na detecção de SmartArt:** Verifique se está usando a versão do Aspose.Words que suporta SmartArt (v24+).

## Perguntas Frequentes

**Q: O que é Aspose.Words for Java?**  
A: Aspose.Words for Java é uma biblioteca Java que permite a desenvolvedores criar, modificar e converter documentos Word programaticamente. Ela oferece uma ampla gama de recursos e ferramentas para trabalhar com documentos em vários formatos.

**Q: Como posso baixar Aspose.Words for Java?**  
A: Você pode baixar Aspose.Words for Java no site da Aspose seguindo este link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Quais são os benefícios de usar formas em documentos?**  
A: Formas adicionam elementos visuais e interatividade aos documentos, tornando‑os mais atraentes e informativos. Com formas, você pode criar balões de texto, botões, imagens, marcas d'água e muito mais, aprimorando a experiência do usuário.

**Q: Posso personalizar a aparência das formas?**  
A: Sim, você pode personalizar a aparência das formas ajustando propriedades como tamanho, posição, rotação e cor de preenchimento. Aspose.Words for Java fornece opções extensas para personalização de formas.

**Q: Aspose.Words for Java é compatível com SmartArt?**  
A: Sim, Aspose.Words for Java suporta formas SmartArt, permitindo trabalhar com diagramas e gráficos complexos em seus documentos.

---

**Última atualização:** 2025-12-14  
**Testado com:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}