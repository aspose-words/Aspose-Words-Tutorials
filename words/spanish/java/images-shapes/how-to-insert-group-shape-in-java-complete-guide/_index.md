---
category: general
date: 2026-07-16
description: cómo insertar un grupo de formas en Java usando Aspose.Words – agregar
  una forma rectangular, establecer las dimensiones de la forma y crear un rectángulo
  y un círculo coloreados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: es
lastmod: 2026-07-16
og_description: 'cómo insertar un grupo de formas en Java: una guía práctica para
  agregar una forma rectangular, establecer dimensiones de la forma y crear rectángulo
  y círculo coloreados con Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Insertar forma de grupo en Java – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Cómo insertar un grupo de formas en Java – Guía completa
url: /es/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo insertar forma de grupo en Java – Guía completa

¿Alguna vez te has preguntado **cómo insertar forma de grupo** en un documento Word usando Java? No eres el único. Ya sea que estés creando un generador de informes o un creador de folletos dinámicos, agrupar formas mantiene tu diseño ordenado y tu código manejable.

En este tutorial recorreremos los pasos exactos para **add rectangle shape**, **set shape dimensions**, y **create colored rectangle** y **create colored circle** usando la biblioteca Aspose.Words. Al final tendrás un programa ejecutable que produce un archivo .docx con un rectángulo azul y un círculo rojo envueltos ordenadamente dentro de un grupo.

## Requisitos previos

- Java 17 (o cualquier JDK reciente) instalado y configurado.
- Maven o Gradle para gestionar dependencias.
- Aspose.Words for Java 23.9 o más reciente – puedes obtenerlo de Maven Central.
- Un conocimiento básico de la sintaxis de Java – no se requiere nada sofisticado.

Si te falta alguno de estos, descarga el JDK del sitio de Oracle y agrega la dependencia de Aspose.Words a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Ahora que la base está lista, pongámonos manos a la obra.

## cómo insertar forma de grupo – Visión general

La idea principal es simple: crear un `Document`, abrir un `DocumentBuilder`, insertar una **group shape**, y luego colocar formas individuales (un rectángulo y un círculo) dentro de ese grupo. El grupo actúa como un contenedor, por lo que moverlo más tarde desplazará todo lo que contiene – ideal para diseños complejos.

A continuación se muestra el código completo, listo para ejecutar. Siéntete libre de copiar‑pegarlo en una nueva clase Java llamada `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Consejo profesional:** Los valores `setLeft` y `setTop` son relativos al origen del grupo, no a la página. Esto hace que reposicionar todo el grupo sea muy sencillo más adelante.

### ¿Qué acaba de suceder?

1. **Document & Builder** – Creamos un archivo Word vacío y un `DocumentBuilder` que nos permite insertar contenido.
2. **Group Shape** – `builder.insertGroupShape()` crea un contenedor. Piensa en él como una carpeta para objetos de dibujo.
3. **Blue Rectangle** – Instanciamos un `Shape` de tipo `RECTANGLE`, le asignamos tamaño, posición y lo rellenamos de azul – ese es el paso **create colored rectangle**.
4. **Red Circle** – Mismo patrón, pero usando `ELLIPSE` para un círculo perfecto, luego lo rellenamos de rojo – esa es la parte **create colored circle**.
5. **Saving** – Finalmente guardamos todo en `GroupShapeDemo.docx`.

Ejecuta el programa (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) y abre el archivo resultante. Deberías ver un rectángulo azul a la izquierda y un círculo rojo a la derecha, ambos bloqueados dentro de una única caja de grupo.

## Agregar una forma de rectángulo

Si solo necesitas un rectángulo sin agrupar, puedes omitir la llamada `insertGroupShape()` y añadir el rectángulo directamente al cuerpo del documento. Sin embargo, agrupar te brinda la flexibilidad de mover, rotar o eliminar múltiples formas de una sola vez.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Observa cómo usamos la lógica **add rectangle shape** aquí. El rectángulo aparece en la página como un objeto independiente. En la mayoría de los escenarios reales querrás el grupo, sin embargo, porque preserva la posición relativa.

## Establecer dimensiones de la forma

Cuando veas métodos como `setWidth` y `setHeight`, recuerda que aceptan **points** (1/72 pulgada). Si prefieres milímetros, conviértelos primero:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Este fragmento demuestra **set shape dimensions** con una conversión de unidades – útil cuando las especificaciones de diseño provienen de un mockup de UI que usa unidades métricas.

## Crear un rectángulo coloreado

Colorear una forma es tan simple como llamar a `getFill().setForeColor()`. Puedes pasar cualquier `java.awt.Color`. ¿Quieres un degradado? Usa `setForeColor` para el color inicial y `setBackColor` para el final.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Esa es una forma rápida de **create colored rectangle** con un relleno degradado en lugar de un tono sólido.

## Crear un círculo coloreado

Los círculos son simplemente elipses con ancho y alto iguales. La misma lógica de color se aplica:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Si necesitas un relleno transparente, establece el canal alfa:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Ahora has dominado la técnica **create colored circle**.

## Guardar el documento

Aspose.Words te permite exportar a muchos formatos: DOCX, PDF, HTML, PNG, lo que sea. Para esta demostración nos quedamos con DOCX porque preserva las formas vectoriales perfectamente.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Cambiar el `SaveFormat` es todo lo que se necesita para generar una versión PDF del mismo arte agrupado.

## Errores comunes y cómo evitarlos

- **¿Olvidaste añadir la forma al grupo?** La forma aparecerá en la página pero no se moverá con el grupo. Siempre llama a `group.appendChild(yourShape)`.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cómo crear campos de formulario y añadir contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}