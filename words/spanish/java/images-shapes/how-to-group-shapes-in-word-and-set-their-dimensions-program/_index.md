---
category: general
date: 2026-11-25
description: Cómo agrupar formas en Word usando Java y cómo establecer las dimensiones
  de una forma en un archivo DOCX con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: es
lastmod: 2026-11-25
og_description: Cómo agrupar formas en Word con la API Aspose.Words para Java y establecer
  rápidamente el tamaño de la forma en Word. Sigue la solución completa paso a paso.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Cómo agrupar formas en Word y establecer sus dimensiones – Guía de Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Cómo agrupar formas en Word y establecer sus dimensiones programáticamente
url: /es/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word y establecer sus dimensiones programáticamente

Si necesita **how to group shapes in Word** y controlar su tamaño exacto, esta guía le muestra una solución completa y ejecutable. Usando Aspose.Words for Java puede crear un rectángulo, una elipse, agregarlos a un `GroupShape`, y luego **how to set shape dimensions** como ancho y alto en un solo archivo DOCX.

Aprenderá a:

* Crear un nuevo documento de Word desde cero.  
* Insertar un `GroupShape` (nueva API en la versión 24.9).  
* Agregar un rectángulo y una elipse al grupo.  
* **Set shape size Word** precisamente con `setWidth` y `setHeight`.  
* Guardar el documento en disco.

No se requiere ninguna herramienta externa—solo Java 17+, Maven y la biblioteca Aspose.Words for Java.

## Requisitos previos

* Java Development Kit 17 o superior.  
* Maven (o Gradle) para la gestión de dependencias.  
* Aspose.Words for Java 24.9 o posterior (la API `GroupShape` se introdujo en la 24.9).  
* Familiaridad básica con la sintaxis de Java y conceptos orientados a objetos.

Si aún no ha agregado Aspose.Words a su proyecto, incluya la siguiente dependencia Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Paso 1: Crear un nuevo documento y un DocumentBuilder

La clase `Document` representa todo el archivo Word, mientras que `DocumentBuilder` ofrece una forma conveniente de agregar contenido.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*¿Por qué este paso?*  
Crear un `Document` nuevo le brinda un lienzo limpio. `DocumentBuilder` es el asistente de alto nivel que le permite insertar párrafos, tablas y, en este caso, formas.

## Paso 2: Insertar un GroupShape (nueva API en la versión 24.9)

Un `GroupShape` actúa como un contenedor; cualquier forma que agregue pasa a ser parte del mismo grupo visual.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*¿Por qué usar `GroupShape`?*  
Agrupar formas simplifica mover, rotar o aplicar formato a varios objetos a la vez. La API se añadió en la 24.9, por lo que versiones anteriores no compilarán esta línea.

## Paso 3: Crear un rectángulo, establecer su tamaño y agregarlo al grupo

Aquí demostramos **how to set shape dimensions** para un rectángulo.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*¿Por qué establecer ancho y alto explícitamente?*  
Word almacena el tamaño de la forma en puntos. Al llamar a `setWidth` y `setHeight` controla la huella visual exacta, lo cual es esencial cuando necesita un diseño preciso o al exportar a PDF.

## Paso 4: Crear una elipse, establecer su tamaño y agregarla al mismo grupo

La misma técnica **set shape size word** funciona para cualquier tipo de forma.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*¿Por qué agregar la elipse al mismo `GroupShape`?*  
Ambas formas se moverán juntas como una unidad. Esto es útil para crear íconos, logotipos o diagramas complejos que deben mantenerse alineados.

## Paso 5: Guardar el documento con las formas agrupadas

Finalmente, persista el archivo DOCX en disco.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Ejecutar este programa produce un archivo llamado **GroupShape.docx** que contiene un rectángulo y una elipse agrupados. Cuando abra el archivo en Microsoft Word, verá que las dos formas se comportan como un solo objeto—puede arrastrarlas, redimensionarlas o rotarlas juntas.

### Resultado esperado

* Un documento Word (`GroupShape.docx`) con una página.  
* Un `GroupShape` que contiene un rectángulo de 100 × 50 pt y una elipse de 80 × 80 pt.  
* Seleccionar cualquiera de las formas selecciona todo el grupo.

## Preguntas comunes y casos límite

### ¿Cómo cambiar la posición de las formas agrupadas?

Después de crear el `GroupShape`, puede establecer sus propiedades `left` y `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Estas coordenadas también se miden en puntos.

### ¿Qué pasa si necesito agregar más de dos formas?

`GroupShape` funciona como cualquier otro nodo contenedor. Llame a `groupShape.appendChild(yourShape)` por cada forma adicional. La API no limita la cantidad de hijos.

### ¿Puedo aplicar estilo (color de relleno, grosor de línea) a formas individuales?

Sí. Cada objeto `Shape` expone propiedades de formato:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### ¿El código funciona con versiones anteriores de Aspose.Words?

El método `insertGroupShape` se introdujo en la versión 24.9. Si está en una versión anterior, necesitará crear un `GroupShape` manualmente a través del árbol de nodos, lo cual es más complejo. Actualizar es la ruta recomendada.

## Consejos profesionales

* **Utilice puntos para consistencia** – La unidad interna de Word es el punto (1/72 pulgada). Convertir desde píxeles o centímetros puede generar tamaños inesperados.  
* **Agrupe antes de posicionar** – Posicione el `GroupShape` después de haber agregado todos sus hijos; de lo contrario, puede necesitar recalcular los desplazamientos.  
* **Reutilice el DocumentBuilder** – Puede insertar varios grupos en el mismo documento moviendo el cursor del builder (`builder.moveTo`) antes de cada llamada a `insertGroupShape`.

## Conclusión

Ahora tiene un ejemplo completo, de extremo a extremo, de **how to group shapes in Word** y **how to set shape dimensions** usando Aspose.Words for Java. El tutorial cubrió la creación de un documento, la inserción de un `GroupShape`, la adición de un rectángulo y una elipse, el establecimiento de su tamaño exacto y el guardado del resultado.  

A partir de aquí puede explorar:

* Agregar cuadros de texto o imágenes al mismo grupo.  
* Animar formas agrupadas con las funciones de SmartArt de Word (a través de la API).  
* Exportar las formas agrupadas a PDF o SVG para uso web.

Siéntase libre de experimentar con diferentes tipos de formas, tamaños y posiciones—agrupando obtiene un control potente sobre diseños complejos en documentos Word.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}