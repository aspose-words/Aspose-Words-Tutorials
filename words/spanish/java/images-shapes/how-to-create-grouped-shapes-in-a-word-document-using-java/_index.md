---
category: general
date: 2026-10-13
description: Aprende cómo crear formas agrupadas en Word con Java. Esta guía te muestra
  cómo insertar una forma de grupo, agregar una línea al grupo y agrupar múltiples
  formas en todo el documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: es
lastmod: 2026-10-13
og_description: Crea formas agrupadas en Word con Java. Sigue este tutorial completo
  para insertar una forma grupal, añadir una línea al grupo y agrupar múltiples formas
  en documentos de Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Crea formas agrupadas en Word con Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cómo crear formas agrupadas en un documento de Word usando Java
url: /es/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear formas agrupadas en un documento Word usando Java

Si necesitas **crear formas agrupadas** en un archivo Microsoft Word desde Java, este tutorial te guía a través de todo el proceso. Verás cómo **insertar forma de grupo**, colocar un rectángulo y una línea dentro del mismo contenedor, y finalmente guardar el documento con los gráficos agrupados.

Agrupar formas facilita mover, redimensionar o aplicar estilo a varios objetos de dibujo como una sola unidad—perfecto para diagramas, flujogramas o decoraciones personalizadas de página. Al final de esta guía podrás **agregar línea al grupo**, **agrupar múltiples formas en documentos Word**, y reutilizar la misma técnica para cualquier número de formas.

## Requisitos previos

- Java 17 o posterior instalado en tu máquina de desarrollo.  
- Una licencia de Aspose.Words for Java (o una evaluación gratuita).  
- Un proyecto Maven o Gradle donde puedas añadir la dependencia de Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

No se requieren bibliotecas adicionales.

## Paso 1: Insertar el contenedor de forma de grupo

El primer paso es **insertar forma de grupo** en el documento. Este contenedor alojará cada forma posterior.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` crea un objeto `Shape` vacío de tipo `GROUPSHAPE`. Piensa en él como un lienzo transparente que puede contener otros objetos de dibujo.

## Paso 2: Añadir un rectángulo al grupo

Un rectángulo suele servir como fondo visual para un conjunto de formas.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Establecer `Left` y `Top` en `0` posiciona el rectángulo en la esquina superior‑izquierda del grupo. Puedes cambiar estos valores para desplazar la forma dentro del grupo.

## Paso 3: **Agregar línea al grupo** – crear una forma de línea

Ahora **agregamos línea al grupo**. La línea aparecerá debajo del rectángulo.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

La propiedad `Top` mueve la línea 60 puntos bajo el rectángulo, creando un diseño simple apilado. También podrías establecer `Left` si necesitas un desplazamiento horizontal.

## Paso 4: Guardar el documento con las formas agrupadas

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Al abrir `GroupShapeDemo.docx` en Microsoft Word, verás un único grupo que contiene tanto el rectángulo como la línea. Seleccionar el grupo permite mover ambas formas juntas, lo que demuestra que has **agrupado múltiples formas en Word** con éxito.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo con todas las importaciones y manejo de errores. Cópialo en tu IDE, reemplaza `YOUR_DIRECTORY` por una ruta de carpeta existente y ejecútalo.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Resultado esperado

- Aparece un archivo llamado `GroupShapeDemo.docx` en la carpeta de destino.  
- Al abrir el archivo en Word se muestra un único objeto agrupado que contiene un rectángulo en la parte superior y una línea debajo.  
- Arrastrar el grupo mueve ambas formas juntas, confirmando que has **creado formas agrupadas** correctamente.

## Consejos y errores comunes

- **Consejo profesional:** Si necesitas rotar o aplicar estilo a formas individuales dentro del grupo, llama a los setters correspondientes (`setRotation`, `getFill().setForeColor`, etc.) antes de añadirlas al grupo. El grupo conservará esas propiedades visuales.  
- **Cuidado con:** Olvidar establecer la propiedad `Top` para la línea puede hacer que se superponga al rectángulo, dejando el grupo desordenado.  
- **Caso límite:** Cuando añades más de dos formas, recuerda que las coordenadas de cada hijo son relativas al origen del grupo (0,0). Planifica el diseño en consecuencia.  
- **Nota de rendimiento:** Agrupar un gran número de formas (cientos) puede aumentar ligeramente el tamaño del archivo, pero simplifica la edición posterior en Word.

## Cómo **agrupar múltiples formas en documentos Word** programáticamente

El patrón mostrado arriba—crear un contenedor de grupo, configurar cada forma hija y añadirla—funciona para cualquier número de formas: círculos, imágenes, cuadros de texto, etc. Simplemente repite los pasos “crear forma → establecer propiedades → añadir” antes de llamar a `doc.save()`.

Si necesitas **agregar línea al grupo** después de que el grupo ya contenga otras formas, puedes obtener el grupo existente con:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Esto demuestra que puedes modificar un grupo en cualquier punto del ciclo de vida del documento.

## Conclusión

Ahora sabes cómo **crear formas agrupadas** en un documento Word usando Java y Aspose.Words. Al **insertar forma de grupo**, **agregar línea al grupo** y **agrupar múltiples formas en Word**, puedes construir dibujos complejos que se comportan como un solo objeto—ideal para diagramas, plantillas y generación automática de informes.

A continuación, explora estos temas relacionados:

- **Aplicar estilos a formas agrupadas** – aprende a establecer colores de relleno, bordes y efectos para todos los hijos a la vez.  
- **Exportar formas agrupadas a PDF** – observa cómo el mismo grupo se mantiene al convertir el documento.  
- **Animar formas con VBA** – combina grupos generados en Java con macros de Word para documentos interactivos.

Siéntete libre de experimentar con diferentes tipos, tamaños y posiciones de formas. Agrupar te brinda la flexibilidad de tratar muchos objetos como uno solo, simplificando tanto el código como la interacción del usuario. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}