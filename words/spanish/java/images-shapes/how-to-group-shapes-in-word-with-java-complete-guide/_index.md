---
category: general
date: 2026-10-16
description: Aprende cómo agrupar formas en Word usando Java. Este tutorial muestra
  cómo agregar una forma de rectángulo, establecer el tamaño y las dimensiones de
  la forma, y guardar el documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: es
lastmod: 2026-10-16
og_description: Agrupa formas en Word usando Java. Añade una forma rectangular, establece
  el tamaño y las dimensiones de la forma, y crea documentos profesionales de forma
  programática.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Agrupa formas en Word con Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 'Cómo agrupar formas en Word con Java: guía completa'
url: /es/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word con Java – guía completa

Si necesitas **agrupar formas en Word** de forma programática, este tutorial te brinda una solución lista para ejecutar. Verás cómo **añadir una forma rectangular**, ajustar su tamaño, establecer dimensiones de la forma y, finalmente, guardar un archivo DOCX que contiene un rectángulo agrupado y una elipse.

Agrupar formas en Word es útil para crear diagramas complejos, generar componentes gráficos reutilizables o simplemente mantener objetos relacionados juntos cuando el documento se edita más adelante. El código utiliza la biblioteca Aspose.Words for Java, que funciona con cualquier JDK reciente y no requiere que Microsoft Word esté instalado.

## Requisitos previos

| Requisito | Razón |
|-------------|--------|
| Java 17 (o posterior) | La biblioteca está dirigida a entornos de ejecución modernos de Java. |
| Aspose.Words for Java (latest version) | Proporciona las clases `Document`, `DocumentBuilder`, `GroupShape` y `Shape` usadas en el ejemplo. |
| Un IDE o herramienta de construcción (Maven/Gradle) | Para compilar y ejecutar el ejemplo. |
| Conocimientos básicos de sintaxis Java | Necesario para entender el flujo del código. |

Agrega la dependencia de Aspose.Words a tu proyecto. Para Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

O para Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Visión general de la solución

El tutorial sigue un patrón claro de **problema → solución → explicación**:

1. **Crear un nuevo documento Word** y obtener un `DocumentBuilder`.  
2. **Insertar un contenedor `GroupShape`** que contendrá múltiples formas.  
3. **Añadir un rectángulo**, establecer su ancho/alto (el paso **set shape size**), y adjuntarlo al grupo.  
4. **Añadir una elipse**, posicionarla dentro del mismo grupo, y también establecer sus dimensiones.  
5. **Guardar** el documento en disco.

Cada paso incluye el **por qué** detrás del código, para que comprendas qué hace la API y cómo puedes adaptarla a otros escenarios.

## Paso 1: Crear el documento y un DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por qué es importante:** `Document` representa todo el archivo DOCX, mientras que `DocumentBuilder` es un asistente que te permite insertar contenido sin lidiar con la gestión de nodos de bajo nivel. Crearlos primero te brinda un lienzo limpio para todas las operaciones de forma posteriores.

## Paso 2: Insertar un contenedor GroupShape

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Un `GroupShape` funciona como una **carpeta** para objetos de dibujo. Cuando mueves, rotas o eliminas el grupo, todas las formas hijas siguen automáticamente. Esto es el núcleo de **group shapes in word**.

## Paso 3: Añadir una forma rectangular – el código de la forma rectangular

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – El constructor `Shape` recibe `ShapeType.RECTANGLE`, lo que indica a Aspose.Words que renderice un contorno rectangular.  
- **set shape size** – `setWidth` y `setHeight` definen las **shape dimensions** en puntos (1 pt = 1/72 in). Esta es la forma más común de controlar el tamaño visual.  
- **Why we use `appendChild`** – Adjunta el rectángulo al `GroupShape` para que se mueva junto con el grupo.

## Paso 4: Añadir una elipse y posicionarla dentro del grupo

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

La elipse demuestra **set shape dimensions** más allá de un simple rectángulo. Al llamar a `setLeft`, controlamos el desplazamiento horizontal dentro del grupo, lo cual es útil al organizar múltiples objetos.

## Paso 5: Guardar el documento

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Cuando abras *GroupShapeDemo.docx* en Microsoft Word, verás un rectángulo y una elipse bloqueados juntos dentro de un solo grupo. Seleccionar cualquiera de las formas seleccionará todo el grupo—exactamente lo que esperas al **group shapes in word**.

## Ejemplo completo y ejecutable

Poniendo todas las piezas juntas, aquí está el archivo fuente completo que puedes copiar en tu IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Resultado esperado

- Un archivo llamado **GroupShapeDemo.docx** aparece en la carpeta del proyecto.  
- Al abrir el archivo en Word se muestran dos formas (un rectángulo y una elipse) que están agrupadas.  
- Arrastrar cualquiera de las formas mueve todo el grupo, confirmando que **group shapes in word** funciona como se espera.

## Variaciones comunes y casos límite

| Escenario | Qué cambiar | Por qué |
|----------|----------------|-----|
| **Tipos de forma diferentes** (p.ej., triángulo) | Use `ShapeType.TRIANGLE` u otro valor del enum al construir `Shape`. | Permite crear diagramas más complejos. |
| **Establecer color de relleno** | Llame a `shape.getFillColor().setColor(Color.BLUE);` después de crear la forma. | Mejora la apariencia visual sin afectar el agrupamiento. |
| **Rotar el grupo** | `groupShape.setRotationAngle(45);` | Rota todas las formas hijas juntas, útil para íconos. |
| **Agregar texto dentro de una forma** | `shape.appendChild(new Paragraph(document));` luego agregue un `Run` con texto. | Hace que la forma actúe como una etiqueta o llamado. |
| **Guardar en un flujo** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Útil para servicios web que devuelven el documento directamente. |

### Consejo profesional

Cuando necesites **set shape dimensions** basadas en datos dinámicos (p.ej., la longitud de un código de barras), calcula primero el ancho/alto en puntos:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## Conclusión

Ahora sabes cómo **group shapes in Word** usando Java, cómo **add rectangle shape**, y cómo **set shape size** y **set shape dimensions** con código conciso y listo para producción. Siguiendo los pasos anteriores, puedes crear grupos gráficos reutilizables, incrustarlos en informes automatizados o construir herramientas de diagramación personalizadas sin necesidad de abrir Word manualmente.

### ¿Qué sigue?

- Explora variaciones de **add rectangle shape** como esquinas redondeadas (`ShapeType.RECTANGLE` con `setCornerRadius`).  
- Combina **group shapes in word** con tablas o gráficos para documentos más ricos.  
- Investiga la API de Aspose.Words para **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) para controlar cómo el texto circundante interactúa con tus gráficos agrupados.

Siéntete libre de experimentar, adaptar el **rectangle shape code**, y compartir tus resultados

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma rectangular en Word con Java – Guía completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}