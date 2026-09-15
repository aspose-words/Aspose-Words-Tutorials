---
date: 2025-12-14
description: Aprenda cómo **insertar forma de imagen** con Aspose.Words para Java.
  Esta guía le muestra cómo agregar formas, crear formas de cuadro de texto, colocar
  formas en tablas, establecer la relación de aspecto de la forma y agregar formas
  de globo de texto.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Uso de formas de documento en Aspose.Words para Java
url: /es/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo **insertar forma de imagen** con Aspose.Words para Java

En este tutorial exhaustivo descubrirás cómo **insertar objetos de forma de imagen** en documentos Word usando Aspose.Words para Java. Ya sea que estés creando informes, material de marketing o formularios interactivos, las formas te permiten añadir llamadas, botones, cuadros de texto, marcas de agua e incluso SmartArt. Revisaremos cada paso, explicaremos por qué usar una forma concreta y proporcionaremos fragmentos de código listos para ejecutar.

## Respuestas rápidas
- **¿Cuál es la forma principal de agregar una forma?** Usa `DocumentBuilder.insertShape` o crea una instancia de `Shape` y añádela al árbol del documento.  
- **¿Puedo insertar una imagen como forma?** Sí – llama a `builder.insertImage` y luego trata el `Shape` devuelto como cualquier otro.  
- **¿Cómo mantengo la proporción de una forma?** Establece `shape.setAspectRatioLocked(true)` o `false` según tus necesidades.  
- **¿Es posible agrupar formas?** Absolutamente – envuélvelas en un `GroupShape` e inserta el grupo como un solo nodo.  
- **¿Los diagramas SmartArt funcionan con Aspose.Words?** Sí, puedes detectar y actualizar formas SmartArt programáticamente.

## ¿Qué es **insertar forma de imagen**?
Una *forma de imagen* es un elemento visual que contiene gráficos raster o vectoriales dentro de un documento Word. En Aspose.Words, una imagen se representa mediante un objeto `Shape`, dándote control total sobre el tamaño, posición, rotación y ajuste de texto.

## ¿Por qué usar formas en tus documentos?
- **Impacto visual:** Las formas atraen la atención a la información clave.  
- **Interactividad:** Botones y llamadas pueden enlazarse a URL o marcadores.  
- **Flexibilidad de diseño:** Posiciona los gráficos con precisión mediante coordenadas absolutas o relativas.  
- **Automatización:** Genera diseños complejos sin edición manual.

## Requisitos previos
- Java Development Kit (JDK 8 o superior)  
- Biblioteca Aspose.Words para Java (descárgala desde el sitio oficial)  
- Conocimientos básicos de Java y programación orientada a objetos  

Puedes descargar la biblioteca aquí: [Descargar Aspose.Words para Java](https://releases.aspose.com/words/java/)

## Cómo **agregar forma** – Insertar un GroupShape
Un `GroupShape` te permite tratar varias formas como una única unidad. Esto es útil para mover o formatear varios elementos juntos.

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

## Crear **forma de cuadro de texto**
Un cuadro de texto es un contenedor que puede albergar texto con formato. También puedes rotarlo para lograr un aspecto dinámico.

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

## Establecer **proporción de la forma**
A veces necesitas que una forma se estire libremente, otras veces deseas mantener sus proporciones originales. Controlar la proporción es sencillo.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Colocar **forma en tabla**
Insertar una forma dentro de una celda de tabla puede ser práctico para diseños de informes. El ejemplo a continuación crea una tabla y luego inserta una forma tipo marca de agua que abarca toda la página.

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

## Añadir **forma de llamada**
Una forma de llamada es perfecta para resaltar notas o advertencias. Mientras que el código anterior ya muestra un `ACCENT_BORDER_CALLOUT_1`, puedes cambiar el `ShapeType` a cualquier variante de llamada que se ajuste a tu diseño.

## Trabajando con formas SmartArt

### Detectar formas SmartArt
Los diagramas SmartArt pueden identificarse programáticamente, lo que permite procesarlos o reemplazarlos según sea necesario.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Actualizar dibujos SmartArt
Una vez detectados, puedes refrescar los gráficos SmartArt para reflejar cualquier cambio de datos.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Problemas comunes y consejos
- **Forma no aparece:** Asegúrate de que la forma se inserte después del nodo objetivo usando `builder.insertNode`.  
- **Rotación inesperada:** Recuerda que la rotación se aplica alrededor del centro de la forma; ajusta `setLeft`/`setTop` si es necesario.  
- **Proporción bloqueada:** Por defecto, muchas formas bloquean su proporción; llama a `setAspectRatioLocked(false)` para estirarlas libremente.  
- **Falla en la detección de SmartArt:** Verifica que estés usando una versión de Aspose.Words que soporte SmartArt (v24+).

## Preguntas frecuentes

**P: ¿Qué es Aspose.Words para Java?**  
R: Aspose.Words para Java es una biblioteca Java que permite a los desarrolladores crear, modificar y convertir documentos Word de forma programática. Proporciona una amplia gama de funciones y herramientas para trabajar con documentos en varios formatos.

**P: ¿Cómo puedo descargar Aspose.Words para Java?**  
R: Puedes descargar Aspose.Words para Java desde el sitio web de Aspose siguiendo este enlace: [Descargar Aspose.Words para Java](https://releases.aspose.com/words/java/)

**P: ¿Cuáles son los beneficios de usar formas en documentos?**  
R: Las formas añaden elementos visuales e interactividad a tus documentos, haciéndolos más atractivos e informativos. Con ellas puedes crear llamadas, botones, imágenes, marcas de agua y más, mejorando la experiencia del usuario.

**P: ¿Puedo personalizar la apariencia de las formas?**  
R: Sí, puedes personalizar la apariencia de las formas ajustando sus propiedades como tamaño, posición, rotación y color de relleno. Aspose.Words para Java ofrece opciones extensas para la personalización de formas.

**P: ¿Aspose.Words para Java es compatible con SmartArt?**  
R: Sí, Aspose.Words para Java soporta formas SmartArt, lo que permite trabajar con diagramas y gráficos complejos en tus documentos.

---

**Última actualización:** 2025-12-14  
**Probado con:** Aspose.Words para Java 24.12 (última)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}