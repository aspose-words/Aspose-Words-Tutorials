---
category: general
date: 2026-08-14
description: Agrupa formas en Word con Java usando Aspose.Words. Aprende cómo crear
  una forma rectangular, establecer sus dimensiones y agrupar varias formas en un
  documento Word en blanco.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: es
lastmod: 2026-08-14
og_description: Agrupa formas en Word usando Aspose.Words para Java. Crea un documento
  Word en blanco, crea una forma rectangular, establece las dimensiones de la forma
  y agrupa múltiples formas en minutos.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Agrupar formas en Word – ejemplo en Java para desarrolladores
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Agrupar formas en Word – guía completa de programación
url: /es/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas en Word – guía completa de programación

Si necesitas **agrupar formas en Word**, este tutorial te guía a través de todo el proceso con Java y Aspose.Words. Aprenderás cómo **crear un documento Word en blanco**, **crear una forma rectangular**, **establecer las dimensiones de la forma**, y finalmente **agrupar varias formas** para que se comporten como un solo objeto.

Trabajar con formas en un archivo Word a menudo se siente como dibujar en un lienzo sin pincel. Al final de esta guía tendrás un fragmento de código reutilizable que podrás insertar en cualquier proyecto Java, ya sea que estés generando informes, facturas o plantillas personalizadas.

## Lo que necesitarás

- Java 8 o superior
- Aspose.Words para Java (la última versión, por ejemplo, 24.9)
- Un IDE como IntelliJ IDEA o Eclipse
- Familiaridad básica con la programación orientada a objetos

Todos estos requisitos son gratuitos de instalar, y el código a continuación compila con una única dependencia Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Paso 1: Crear un documento Word en blanco e inicializar el builder

Lo primero que debes hacer es **crear un documento Word en blanco**. Esto te brinda un lienzo limpio en el que podrás insertar formas más adelante.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo el archivo *.docx*, mientras que `DocumentBuilder` es el asistente que inserta párrafos, tablas y formas. Inicializar ambos objetos es la base para cualquier tarea de automatización de Word.

## Paso 2: Insertar un contenedor de forma grupal

Una **forma grupal** actúa como una carpeta que puede contener otras formas. Primero creamos el contenedor con un tamaño fijo de 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

El método `insertGroupShape` devuelve un objeto `GroupShape`. Todas las formas posteriores que quieras tratar como una sola unidad deben añadirse a este objeto.

## Paso 3: Crear formas rectangulares y establecer sus dimensiones

Ahora **creamos objetos de forma rectangular**, configuramos su tamaño y los posicionamos dentro del grupo. Este paso también muestra cómo **establecer las dimensiones de la forma** con precisión.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Ambos rectángulos comparten las mismas dimensiones, pero sus propiedades `left` difieren, por lo que aparecen uno al lado del otro. Puedes cambiar `setTop` y `setLeft` para organizar cualquier diseño que necesites.

## Paso 4: Guardar el documento que contiene los rectángulos agrupados

Una vez que las formas están dentro del grupo, simplemente guardas el `Document`. El archivo resultante mostrará dos rectángulos que se mueven juntos al seleccionarlos.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Ejecutar el programa crea `GroupShape.docx` en el directorio de trabajo. Ábrelo en Microsoft Word, selecciona un rectángulo y notarás que todo el grupo se desplaza como una unidad—exactamente lo que **agrupar formas en Word** pretende lograr.

![Group shapes in Word example](group-shapes.png){alt="Ejemplo de formas agrupadas en Word"}

*Figura: Dos formas rectangulares agrupadas en un documento Word.*

## Consejo profesional: Reutilizar el mismo grupo de formas

Si necesitas añadir más formas más adelante (por ejemplo, círculos, cuadros de texto), conserva una referencia a `groupShape` y sigue llamando a `appendChild`. Esto evita recrear el contenedor y garantiza que todos los miembros permanezcan sincronizados.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Casos límite y preguntas frecuentes

- **¿Qué pasa si las formas se superponen?** La superposición está permitida; Word las renderiza en el orden en que fueron añadidas. Usa `setZOrder` si necesitas una pila explícita.
- **¿Puedo agrupar formas en diferentes páginas?** No. Un `GroupShape` está confinado a una sola página porque su sistema de coordenadas es relativo a la página.
- **¿Las formas agrupadas heredan formato?** Cada hijo mantiene su propio formato (color de relleno, estilo de línea). Para aplicar un estilo uniforme, itera sobre `groupShape.getChildNodes()` y establece las propiedades programáticamente.

## Código fuente completo para referencia

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Ejecutar el programa produce un archivo DOCX donde los dos rectángulos están **agrupados**. Seleccionar cualquiera de los rectángulos mueve ambos, confirmando que has **agrupado múltiples formas** con éxito.

## Conclusión

Ahora sabes cómo **agrupar formas en Word** usando Java, desde **crear un documento Word en blanco** hasta **crear una forma rectangular**, **establecer las dimensiones de la forma**, y finalmente **agrupar múltiples formas** en un solo objeto móvil. Este patrón escala a cualquier número de formas y puede combinarse con texto, imágenes o gráficos para crear documentos ricos y programáticos.

### ¿Qué sigue?

- Explora **agrupar múltiples formas** con diferentes tipos (elipses, flechas, cuadros de texto).
- Aplica colores de relleno o bordes llamando a `shape.getFillColor()` y `shape.getLine().setColor()`.
- Inserta la forma agrupada en una celda de tabla para informes estructurados.
- Combina este enfoque con combinación de correspondencia para generar contratos personalizados que incluyan gráficos con marca.

Siéntete libre de experimentar, adaptar las dimensiones o incrustar contenido adicional. Cuando domines el agrupamiento, tus scripts de automatización de Word serán mucho más flexibles y mantenibles. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}