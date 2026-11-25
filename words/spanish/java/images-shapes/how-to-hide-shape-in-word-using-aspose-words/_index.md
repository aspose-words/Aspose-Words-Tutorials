---
category: general
date: 2026-11-25
description: Oculta una forma en Word con Aspise.Words y aprende a crear documentos
  Word con Aspose mientras insertas una forma rectangular en Word con solo unas pocas
  líneas de código.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: es
lastmod: 2026-11-25
og_description: Ocultar forma en Word usando Aspose.Words. Este tutorial le muestra
  cómo crear un documento Word con Aspose, insertar una forma rectangular en Word
  y ocultarla programáticamente.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Ocultar forma en Word con Aspose.Words – guía rápida paso a paso
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Cómo ocultar una forma en Word usando Aspose.Words
url: /es/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo ocultar una forma en Word usando Aspose.Words

Si necesita **ocultar una forma en Word** mientras genera documentos programáticamente, Aspose.Words lo hace sin esfuerzo. En esta guía verá exactamente cómo crear un documento Word con Aspose, insertar una forma rectangular en Word y luego ocultar esa forma para que no aparezca en el diseño. Se proporciona el ejemplo completo y ejecutable para que pueda copiar‑pegarlo en su IDE y ver el resultado de inmediato.

Terminará este tutorial con un archivo Word que contiene un rectángulo oculto—útil para marcadores de posición, contenido condicional o metadatos que deben permanecer invisibles para el lector. No se requieren herramientas externas más allá de la biblioteca Aspose.Words para Java (o .NET).

## Lo que aprenderá

* Cómo **crear un documento Word con Aspose** desde cero.  
* Cómo **insertar una forma rectangular en Word** usando `DocumentBuilder`.  
* Cómo establecer la propiedad `hidden` de la forma para que no se renderice en el diseño final.  
* Cómo verificar que la forma está oculta y cómo volver a mostrarla si es necesario.  

### Requisitos previos

* Java 17+ (o .NET 6+ si prefiere C#—las llamadas a la API son análogas).  
* Aspose.Words for Java 24.x (la última versión al momento de escribir).  
* Un IDE como IntelliJ IDEA, Eclipse o VS Code.  

> **Consejo profesional:** Utilice la licencia temporal gratuita de Aspose si aún no tiene una licencia comercial. La biblioteca funciona sin licencia para evaluación, pero una licencia elimina las marcas de agua de evaluación.

## Ocultar una forma en Word con Aspose.Words

Los pasos principales son:

1. **Crear un nuevo `Document`.**  
2. **Insertar una forma rectangular** usando `DocumentBuilder`.  
3. **Marcar la forma como oculta** para que no aparezca cuando se abra el archivo.  

Cada paso se explica a continuación con código y razonamiento.

### Paso 1: Crear un documento Word con Aspose

Primero, instancie un `Document` en blanco y un `DocumentBuilder`. El builder proporciona una API fluida para agregar contenido, incluidas las formas.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:**  
Crear un `Document` nuevo le brinda un lienzo limpio. `DocumentBuilder` es la forma recomendada de modificar el documento porque rastrea automáticamente el punto de inserción actual y maneja la gestión de secciones/páginas por usted.

### Paso 2: Insertar una forma rectangular en Word

Ahora añadimos una forma rectangular. El método `insertShape` requiere el tipo de forma y sus dimensiones en puntos (1 punto = 1/72 de pulgada).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Por qué es importante:**  
`insertShape` crea un objeto de dibujo que vive en la parte *drawing* del documento. Al especificar el tamaño, controla cuánto espacio ocuparía la forma si fuera visible. El estilo opcional le ayuda a verificar la forma antes de ocultarla.

### Paso 3: Ocultar la forma para que no aparezca en el diseño

Aspose.Words refleja el atributo *Hidden* de Microsoft Word. Establecerlo en `true` indica a Word que omita la forma al renderizar, manteniendo el objeto en la estructura del documento.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Por qué es importante:**  
Una forma oculta aún puede ser accedida programáticamente (p. ej., para procesamiento condicional) y puede volver a mostrarse más tarde cambiando la propiedad. Esto es ideal para escenarios como **marcadores de posición condicionales** que solo deben aparecer para ciertas audiencias.

### Paso 4: Guardar y verificar el resultado

Finalmente, escriba el documento en disco. Abra el archivo en Microsoft Word para confirmar que el rectángulo no es visible. También puede inspeccionar el XML subyacente para ver la bandera oculta.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Salida esperada:**  
Ejecutar el programa imprime:

```
Document saved to HideShapeResult.docx
```

Al abrir *HideShapeResult.docx* en Word, la página aparece vacía (o contiene cualquier otro contenido que haya añadido antes de la forma). El rectángulo está presente en el XML del archivo (`<w:hidden>` atributo) pero no se renderiza.

### Paso 5: (Opcional) Mostrar la forma más tarde

Si necesita volver a hacer visible la forma, cargue el documento, localice la forma y establezca `hidden` en `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Por qué es importante:**  
Poder alternar la bandera oculta le brinda control total sobre la generación dinámica de documentos—p. ej., puede generar un documento maestro con todos los elementos opcionales ocultos y luego mostrarlos selectivamente según las preferencias del usuario.

## Ejemplo completo y ejecutable (crear documento Word con Aspose, insertar forma rectangular en Word, ocultar forma)

A continuación se muestra el programa completo que puede compilar y ejecutar directamente.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Ejecutando el código**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Reemplace `aspose-words-24.10.jar` con la versión real que descargó.

### Qué contienen los archivos de salida

* **HideShapeResult.docx** – el rectángulo está oculto; la página parece vacía.  
* **UnhiddenShape.docx** – el mismo rectángulo es visible, mostrando un cuadro rojo con contorno negro.

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Afectará la forma oculta la paginación?* | No. Los objetos ocultos son ignorados por el motor de diseño, por lo que no empujan texto a una nueva página. |
| *¿Puedo ocultar otros objetos de Word (p. ej., imágenes, tablas)?* | Sí. La mayoría de las subclases de `Node` (incluyendo `Shape`, `Paragraph`, `Run`) exponen un método `setHidden(boolean)`. |
| *¿Qué pasa si el documento ya contiene formas?* | Use `doc.getChildNodes(NodeType.SHAPE, true)` para iterar y ocultar solo las formas que desea. |
| *¿Ocultar una forma aumenta el tamaño del archivo?* | Un poco, porque el XML de la forma permanece. El impacto es insignificante para documentos típicos. |
| *¿Sobrevivirá la bandera oculta al guardar el documento como PDF?* | Al convertir a PDF, las formas ocultas se omiten por defecto. Puede controlar esto con `PdfSaveOptions` si es necesario. |

## Mejores prácticas al trabajar con objetos ocultos

* **Nombre sus formas** usando `setName("MyPlaceholder")`. Esto facilita localizarlas más tarde.  
* **Agrupe objetos ocultos relacionados** dentro de un `GroupShape` si necesita alternar la visibilidad de varios elementos a la vez.  
* **Documente el propósito** de los elementos ocultos en comentarios o en un archivo de especificación separado—los futuros mantenedores apreciarán el contexto.  
* **Evite el uso excesivo de objetos ocultos**; aumentan la complejidad del documento y pueden confundir a los usuarios que inspeccionen el XML manualmente.

## Conclusión

Ahora sabe cómo **ocultar una forma en Word** usando Aspose.Words, cómo **crear un documento Word con Aspose** y cómo **insertar una forma rectangular en Word** antes de ocultarla. El ejemplo muestra el ciclo completo: creación, inserción, ocultación, guardado y, opcionalmente, volver a mostrar. Aplique estas técnicas para crear informes dinámicos, plantillas condicionales o cualquier flujo de trabajo automatizado de Word donde se necesiten marcadores de posición invisibles.

### Próximos pasos

* Explore **contenido condicional** combinando formas ocultas con campos de combinación de correspondencia.  
* Aprenda a **ocultar ejecuciones de texto** (`Run.setHidden(true)`) para un control más granular.  
* Consulte la documentación de Aspose.Words sobre **protección de documentos** para evitar que los usuarios desoculten accidentalmente las formas.

¡Feliz codificación, y que sus archivos Word generados permanezcan limpios mientras transportan los datos ocultos que necesita!

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}