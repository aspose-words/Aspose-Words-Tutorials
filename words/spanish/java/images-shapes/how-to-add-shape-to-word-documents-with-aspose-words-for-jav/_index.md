---
category: general
date: 2026-11-22
description: 'Aprenda cómo agregar una forma a Word usando Aspose.Words para Java:
  inserte un rectángulo y ocultelo programáticamente.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: es
lastmod: 2026-11-22
og_description: Agregar forma a Word usando Aspose.Words para Java. Este tutorial
  muestra cómo insertar un rectángulo, ocultar la forma y guardar el documento.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Agregar forma a Word con Aspose.Words – Guía de Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Cómo agregar una forma a documentos de Word con Aspose.Words para Java
url: /es/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar forma a documentos Word con Aspose.Words para Java

Si necesita **agregar forma a Word** documentos programáticamente, Aspose.Words para Java lo hace sencillo. En esta guía aprenderá **cómo insertar forma**, controlar su visibilidad y **cómo ocultar forma** para que el archivo final se vea exactamente como espera.

Recorrerá un ejemplo completo y ejecutable que carga un `.docx` existente, inserta un rectángulo, lo oculta y guarda el resultado. No se requieren scripts externos ni pasos manuales, y el tutorial cubre variaciones comunes como crear un documento nuevo desde cero u ocultar una forma solo al imprimir.

## Requisitos previos

Antes de comenzar, asegúrese de tener:

* Java 17 (o posterior) instalado – versiones anteriores funcionan, pero la última LTS ofrece mejor rendimiento.  
* Maven 3.8+ para la gestión de dependencias.  
* Una licencia válida de Aspose.Words para Java (la evaluación gratuita sirve para aprendizaje).  
* Un IDE o editor de texto de su elección (p. ej., IntelliJ IDEA, VS Code).

## Paso 1: Agregar Aspose.Words a su proyecto Maven

Agregue la siguiente dependencia a su `pom.xml`. Esto obtiene la última versión estable (a partir de noviembre 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Consejo:** Use una cláusula `<scope>provided</scope>` si planea distribuir el JAR con su propia lógica de licenciamiento.

## Agregar forma a Word – inicializando el documento

El primer paso funcional es obtener un objeto `Document`. Puede cargar un archivo existente o crear uno nuevo.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Por qué es importante*: La clase `Document` es el punto de entrada para todas las manipulaciones de Word. Cargar un archivo existente conserva estilos, encabezados y pies de página, mientras que un documento nuevo le brinda una hoja en blanco.

## Cómo insertar forma en un documento Word

A continuación, cree un `DocumentBuilder` para modificar el contenido del documento. El builder le brinda métodos para insertar texto, tablas y **formas**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

La llamada `insertShape` devuelve un objeto `Shape` que puede configurar adicionalmente (color, borde, texto, etc.). Las dimensiones se expresan en puntos (1 pt = 1/72 in).

*Por qué podría usar un rectángulo*: Los rectángulos son el contenedor más común para anotaciones, marcas de agua o marcadores de posición. Puede reemplazar `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., para satisfacer diferentes necesidades visuales.

## Cómo ocultar forma en Word

A veces necesita que una forma exista para cálculos de diseño pero que no aparezca en la representación final. Aspose.Words proporciona el método `setHidden(true)` para lograrlo.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

La bandera oculta funciona como la opción de formato **Hidden** en Microsoft Word: la forma se omite del diseño visual pero sigue participando en el modelo de objetos del documento. Esto es útil para:

* Almacenar metadatos o marcadores que su aplicación leerá después.  
* Crear marcadores de posición que se eliminan justo antes de publicar.  
* Controlar la visibilidad para diferentes formatos de salida (p. ej., ocultar en HTML pero mantener en PDF).

> **Nota:** Las formas ocultas todavía se exportan a PDF por defecto. Si necesita que también se omitan del PDF, establezca `rectangle.getWrapType( ) = WrapType.NONE` y ajuste la propiedad `Hidden` en consecuencia.

## Paso 4: Guardar el documento modificado

Finalmente, persista los cambios en un archivo nuevo.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Al abrir `output.docx` en Microsoft Word, el rectángulo no será visible, pero seguirá formando parte del árbol del documento. Puede verificar su presencia programáticamente recargando el archivo y comprobando `Shape.isHidden()`.

### Resultado esperado

* El archivo `output.docx` se abre sin formas visibles.  
* Si inspecciona el documento con Aspose.Words (p. ej., `doc.getChildNodes(NodeType.SHAPE, true).size()`), el recuento de formas será **1**, confirmando que la forma existe pero está oculta.

## Variaciones avanzadas y casos límite

### 1. Crear una forma en un documento nuevo

Si comienza desde cero, reemplace la línea de carga por:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Posicionar la forma con precisión

Por defecto, `insertShape` coloca la forma en la ubicación actual del cursor. Para posicionarla de forma absoluta:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Controlar la visibilidad por formato de salida

Si necesita que la forma sea visible en la interfaz de Word pero oculta al exportar a PDF, use `Shape.setWrapType(WrapType.NONE)` junto con `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Agregar texto dentro de la forma

Un rectángulo puede contener un marco de texto:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Luego puede ocultar el cuadro de texto con la misma llamada `setHidden(true)`.

## Problemas comunes y cómo evitarlos

| Síntoma | Causa | Solución |
|---------|-------|----------|
| La forma aparece aun después de `setHidden(true)` | El documento se guardó antes de establecer la bandera oculta. | Asegúrese de llamar `setHidden(true)` **antes** de `doc.save()`. |
| El tamaño de la forma se ve distorsionado | Confusión entre puntos y píxeles en pantallas de alta DPI. | Use puntos (72 pt = 1 in) para un dimensionado consistente en todas las plataformas. |
| La forma oculta aún se imprime | Algunas impresoras ignoran la bandera oculta. | Establezca `Shape.setWrapType(WrapType.NONE)` y también desactive `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Conclusión

Ahora sabe cómo **agregar forma a documentos Word** usando Aspose.Words para Java, **cómo insertar forma** y **cómo ocultar forma** para que permanezca invisible para los usuarios finales mientras sigue formando parte de la estructura del documento. El ejemplo completo anterior carga un archivo, inserta un rectángulo, lo oculta y guarda el resultado, cubriendo tanto casos de uso típicos como varios casos límite.

A partir de aquí puede explorar temas relacionados como **cómo insertar forma** con colores de relleno personalizados, **cómo ocultar forma en Word** para impresión condicional, o automatizar el procesamiento masivo de documentos con Aspose.Words. Experimente con diferentes valores de `ShapeType`, opciones de posicionamiento y banderas de visibilidad para adaptarse a su flujo de trabajo específico.

¡Feliz codificación y disfrute de la flexibilidad que brinda la manipulación programática de Word en sus aplicaciones Java!

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear un documento Word programáticamente, agregar y ocultar una forma en Java usando Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Cómo ocultar forma en un documento Word usando Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Crear un documento .docx en blanco y agregar una forma rectangular oculta con Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}