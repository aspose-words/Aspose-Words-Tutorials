---
category: general
date: 2026-09-24
description: Aprende a crear un documento Word en blanco en Java y agrupar formas
  como rectángulos y líneas usando Aspose.Words. Incluye código paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: es
lastmod: 2026-09-24
og_description: Crea un documento Word en blanco en Java y aprende cómo agrupar formas,
  agregar una forma rectangular y establecer el tamaño de la forma con Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Crear un documento Word en blanco y agrupar formas en Java – guía paso a
  paso
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cómo crear un documento Word en blanco y agrupar formas en Java
url: /es/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agrupar formas en Java

Si necesitas **crear un documento Word en blanco** y luego organizar varios objetos de dibujo, esta guía te muestra exactamente cómo. Usando Aspose.Words for Java puedes insertar una forma de grupo, añadir una forma rectangular, dibujar una línea y controlar el tamaño y la posición de cada forma, todo en un único programa ejecutable.

Recorrerás cada paso, desde la inicialización del documento hasta guardar el `.docx` final. Al final comprenderás **cómo agrupar formas**, **añadir una forma rectangular** y **establecer el tamaño de la forma** para que tus archivos Word se vean exactamente como deseas.

## Requisitos previos

- Java 17 o posterior (el código se compila con cualquier JDK reciente)
- Biblioteca Aspose.Words for Java (descárgala desde el [Aspose website](https://products.aspose.com/words/java))
- Un IDE o herramienta de compilación (Maven/Gradle) que pueda añadir el JAR de Aspose.Words al classpath
- Conocimientos básicos de la sintaxis de Java

> **Consejo profesional:** Usa Maven para la gestión de dependencias; agrega `com.aspose:aspose-words:23.12` (o la última versión) a tu `pom.xml`.

## Paso 1: Crear un documento Word en blanco

La primera tarea es **crear un documento Word en blanco**. Esto te brinda un lienzo limpio en el que podrás insertar formas más adelante.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante:* Un objeto `Document` representa todo el archivo `.docx`. Comenzar con un documento en blanco asegura que no haya formato oculto que interfiera con las formas que vas a añadir.

## Paso 2: Insertar una forma de grupo – el contenedor para múltiples objetos

Una **forma de grupo** actúa como un contenedor que te permite mover, redimensionar o rotar varias formas juntas. Esto es el núcleo de **cómo agrupar formas** en Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Explicación:* El método `insertGroupShape` crea un objeto `GroupShape` y lo coloca en la ubicación actual del cursor. Todas las formas posteriores que `appendChild` a este grupo serán tratadas como una única unidad.

## Paso 3: Añadir una forma rectangular y establecer su tamaño

Ahora **añadimos una forma rectangular** al grupo y **establecemos el tamaño de la forma** con precisión.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Por qué necesitas establecer el tamaño de la forma:* El ancho y la altura controlan cómo aparece el rectángulo en la página. Los métodos `setLeft` y `setTop` posicionan el rectángulo relativo al origen del grupo, dándote un control de diseño pixel‑perfecto.

## Paso 4: Añadir una forma de línea y configurar sus dimensiones

Una línea es otro objeto de dibujo común. Aplicaremos una lógica similar a **añadir una forma rectangular** a una línea, mostrando que los mismos principios de dimensionado se aplican.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Punto clave:* Aunque una línea no tiene altura, aún utilizas `setWidth` para definir su longitud. El posicionamiento (`setLeft`, `setTop`) sigue el mismo sistema de coordenadas que otras formas.

## Paso 5: Guardar el documento con formas agrupadas

Finalmente, persiste los cambios guardando el documento. Esto genera un archivo `.docx` que puedes abrir en Microsoft Word para verificar el resultado.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Resultado esperado:** Al abrir `GroupShapeDemo.docx` se muestra una página en blanco que contiene un rectángulo y una línea agrupados. Seleccionar cualquiera de las formas selecciona todo el grupo, permitiéndote moverlas juntas.

## Preguntas comunes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Puedo añadir más de dos formas al grupo?* | Sí. Llama a `group.appendChild(yourShape)` para cada forma adicional. |
| *¿Qué pasa si necesito una unidad diferente (p.ej., centímetros) para el tamaño?* | Aspose.Words usa puntos (1 punto = 1/72 de pulgada). Convierte usando `Points = centimeters * 28.3465`. |
| *¿Mantendrá el grupo su diseño cuando el documento se abra en otra máquina?* | Absolutamente. Todos los datos de tamaño y posición se almacenan en el archivo `.docx`, lo que hace que el diseño sea portátil. |
| *¿Cómo desagrupo las formas más tarde?* | Obtén el objeto `GroupShape`, luego itera sobre `group.getChildNodes(NodeType.SHAPE, true)` y mueve cada hijo fuera del grupo. |
| *¿Qué pasa si necesito rotar todo el grupo?* | Usa `group.setRotationAngle(double angleInDegrees)` antes de guardar. |

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar y pegar en tu IDE. Incluye todas las importaciones necesarias y comentarios.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Ejecuta el programa, abre `GroupShapeDemo.docx` en Microsoft Word y verás las formas agrupadas exactamente como se describe.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **agrupar formas en Word**, **añadir una forma rectangular** y **establecer el tamaño de la forma** usando Aspose.Words for Java. Al colocar formas dentro de un `GroupShape`, obtienes control total sobre el posicionamiento colectivo, el escalado y la rotación, perfecto para diagramas, flujogramas o gráficos personalizados incrustados en informes automatizados.

**Próximos pasos:**  
- Explora **cómo agrupar formas** con objetos más complejos como imágenes o cuadros de texto.  
- Experimenta con `setRotationAngle` para rotar todo el grupo.  
- Combina esta técnica con combinación de correspondencia para generar documentos personalizados que incluyan gráficos de marca.

¡Siéntete libre de adaptar el código a tus propios proyectos y compartir tus resultados en los comentarios!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular en Word con Java – Guía completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Crear documento Word Java – Añadir forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}