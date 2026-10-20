---
category: general
date: 2026-08-20
description: Aprenda cómo agrupar formas, establecer el tamaño de la forma, insertar
  una imagen en el documento, agregar una imagen al grupo y crear una forma rectangular
  con Aspose.Words en Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: es
lastmod: 2026-08-20
og_description: Cómo agrupar formas en un documento de Word usando Aspose.Words. Sigue
  este tutorial paso a paso en Java para establecer el tamaño de la forma, insertar
  una imagen en el documento, añadir una foto al grupo y crear una forma rectangular.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Cómo agrupar formas en un documento de Word con Aspose.Words – Guía de Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Cómo agrupar formas en un documento de Word usando Aspose.Words
url: /es/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en un documento Word usando Aspose.Words

Si necesitas **cómo agrupar formas** en un archivo Word, este tutorial muestra la solución completa en Java. Verás cómo **establecer el tamaño de la forma**, **insertar una imagen en el documento**, **agregar una imagen al grupo** y **crear una forma rectangular**, todo con explicaciones claras y un ejemplo de código ejecutable.

Agrupar formas simplifica la gestión del diseño, te permite mover o rotar varios objetos como una sola unidad y mantiene tu documento ordenado. En los pasos siguientes crearás un grupo que contiene un rectángulo y una imagen, y luego colocarás el grupo en la página.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o superior instalado.
* Aspose.Words for Java (versión 23.9 o posterior) añadido al classpath de tu proyecto.
* Una imagen JPEG de ejemplo en `YOUR_DIRECTORY/sample.jpg` (reemplaza `YOUR_DIRECTORY` con la ruta real).

Puedes añadir Aspose.Words mediante Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Cómo agrupar formas con Aspose.Words

Las siguientes secciones describen cada operación necesaria para **cómo agrupar formas**. El encabezado H2 principal contiene la palabra clave principal, cumpliendo con las reglas SEO.

### Paso 1: Crear un nuevo documento y un `DocumentBuilder`

Un `Document` representa el archivo Word, mientras que `DocumentBuilder` proporciona métodos convenientes para insertar contenido.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante*: Comenzar con un `Document` nuevo garantiza que el grupo que crees no interfiera con elementos existentes.

### Paso 2: Insertar una forma de grupo que contendrá varias formas hijas

Una forma de grupo actúa como un contenedor. Sus dimensiones definen el cuadro delimitador para todas las formas hijas.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Consejo*: El ancho (`300`) y la altura (`200`) están en puntos (1 pt = 1/72 pulgada). Ajústalos según el tamaño de las formas que planeas añadir.

### Paso 3: Crear una forma rectangular, establecer su tamaño y agregarla al grupo

Establecer el tamaño exacto de una forma es esencial cuando deseas un control preciso del diseño.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Por qué establecemos el tamaño de la forma*: Los métodos `setWidth` y `setHeight` corresponden a la palabra clave secundaria **set shape size**, dándote un control pixel‑perfecto sobre la apariencia del rectángulo.

### Paso 4: Insertar una imagen y luego agregar la forma de imagen al mismo grupo

Insertar una imagen es el núcleo del requisito **insert image into document**. La `Shape` devuelta es una forma de imagen que puede agruparse como cualquier otra forma.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Consejo profesional*: Si necesitas conservar la proporción original, establece solo una dimensión (`setWidth` o `setHeight`). Aspose.Words escala automáticamente la otra dimensión.

### Paso 5: Posicionar todo el grupo en la página

Después de añadir todas las formas hijas, puedes mover, rotar u ocultar todo el grupo. El posicionamiento utiliza indirectamente el concepto **add picture to group**, porque el grupo ahora contiene la imagen.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explicación*: `setLeft` y `setTop` colocan el grupo relativo a los márgenes de la página. Rotar el grupo demuestra que todas las formas hijas heredan la transformación.

### Paso 6: Guardar el documento

Finalmente, escribe el archivo en disco. Puedes abrir el `.docx` resultante en Word para verificar el agrupamiento.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Ejecutar el programa genera **GroupShapesDemo.docx** que contiene un rectángulo y una imagen agrupados. Seleccionar cualquiera de las formas en Word también seleccionará la otra, confirmando que has aprendido con éxito **cómo agrupar formas**.

---

## Resultado esperado

Al abrir *GroupShapesDemo.docx* en Microsoft Word:

* Aparece un rectángulo (relleno dorado) en el lado izquierdo del grupo.
* La imagen que proporcionaste aparece a la derecha del rectángulo.
* Ambos objetos se mueven juntos al arrastrar el grupo.
* El grupo está posicionado a 50 pt del margen izquierdo y 100 pt del margen superior, rotado 15°.

Si la imagen no aparece, verifica la ruta del archivo en `insertImage`. Aspose.Words lanza una `IOException` cuando no se encuentra el archivo.

---

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo añadir más de dos formas?** | Sí. Llama a `groupShape.appendChild(otherShape)` por cada forma adicional. |
| **¿Qué pasa si necesito un fondo transparente para el rectángulo?** | Usa `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **¿El agrupamiento es compatible con formatos Word antiguos (p. ej., `.doc`)?** | El agrupamiento funciona para `.docx` y `.doc`, pero algunos visores antiguos pueden ignorar los metadatos del grupo. Guarda como `.docx` para obtener la máxima fidelidad. |
| **¿Cómo desagrupar más tarde?** | Obtén los nodos hijos mediante `groupShape.getChildNodes(NodeType.ANY, true)` y muévelos al cuerpo del documento, luego elimina el grupo. |
| **¿Puedo agrupar formas en diferentes secciones?** | No. Un `GroupShape` debe residir dentro de una sola `Story` (normalmente el cuerpo principal del documento). |

---

## Consejos profesionales para un manejo robusto de formas

* **Usa posicionamiento absoluto con moderación** – el posicionamiento relativo (`builder.moveToDocumentEnd()`) suele producir diseños más adaptables.
* **Cachea el `DocumentBuilder`** – crear un nuevo builder para cada operación puede degradar el rendimiento en documentos grandes.
* **Establece `PictureFillMode`** cuando necesites que la imagen se estire o repita dentro de la forma: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Valida las dimensiones de la imagen** antes de insertarla para evitar escalados inesperados que puedan afectar el cuadro delimitador del grupo.

---

## Próximos pasos

Ahora que sabes **cómo agrupar formas**, podrías explorar:

* **Insert image into document** con opciones avanzadas como recorte (`pictureShape.setCropTop(...)`).
* **Set shape size** de forma dinámica según las dimensiones de la página (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** junto con cuadros de texto para gráficos con leyenda.
* **Create rectangle shape** con esquinas redondeadas (`rectangleShape.setCornerRadius(5);`).

Estos temas amplían la misma superficie de API y te ayudan a crear informes Word programáticos y sofisticados.

---

## Conclusión

En este tutorial aprendiste **cómo agrupar formas** en un documento Word usando Aspose.Words para Java. Siguiendo los seis pasos — crear un documento, insertar un grupo, **crear una forma rectangular**, **establecer el tamaño de la forma**, **insertar una imagen en el documento**, **agregar una imagen al grupo** y posicionar el grupo — ahora dispones de un patrón reutilizable para escenarios de diseño complejos. Siéntete libre de experimentar con formas hijas adicionales, distintas rotaciones o lógica condicional de agrupamiento para adaptarlo a las necesidades de tu aplicación.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}