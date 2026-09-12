---
category: general
date: 2026-09-11
description: Agrupa formas en Word y agrega una forma rectangular usando Aspose.Words
  para Java. Aprende cómo establecer el tamaño de la forma, agrupar objetos y guardar
  el documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: es
lastmod: 2026-09-11
og_description: Agrupa formas en Word y agrega una forma rectangular usando Aspose.Words
  para Java. Este tutorial muestra cómo establecer el tamaño de la forma, agrupar
  formas y exportar el documento.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Agrupar formas en Word – agregar rectángulo con Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Agrupar formas en Word y agregar un rectángulo con Aspose.Words
url: /es/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas en Word y agregar un rectángulo con Aspose.Words

Si necesitas **agrupar formas en Word** mientras agregas programáticamente un rectángulo, esta guía te brinda una solución completa, lista‑para‑ejecutar. Verás exactamente cómo insertar una forma de grupo, agregar una forma de rectángulo, establecer el tamaño de la forma y, finalmente, guardar el documento para que puedas ver el resultado al instante.

Trabajar con documentos de Word a menudo implica organizar varios objetos—imágenes, gráficos o formas geométricas simples—en una única unidad lógica. Agrupar esos objetos facilita mover, rotar o aplicar estilos a todos ellos juntos. En este tutorial también cubriremos **cómo agregar rectángulo** y **establecer el tamaño de la forma** para un control de diseño perfecto.

## Lo que aprenderás

* Cómo crear un nuevo documento Word con Aspose.Words para Java.  
* **Cómo agrupar formas** para que se comporten como un solo objeto.  
* **Agregar forma de rectángulo** a un grupo e insertar una imagen en el mismo grupo.  
* **Establecer el tamaño de la forma** tanto para el rectángulo como para la imagen.  
* Guardar el documento y abrirlo en Microsoft Word para verificar el resultado.

### Requisitos previos

* Java 17 o posterior instalado.  
* Maven o Gradle para gestionar dependencias.  
* Una licencia válida de Aspose.Words para Java (o una clave de evaluación gratuita).  
* Un archivo de imagen (`sample.png`) colocado en un directorio conocido (reemplaza `YOUR_DIRECTORY` con tu ruta real).

---

## Cómo agrupar formas en Word usando Aspose.Words

El primer paso es crear un `Document` y un `DocumentBuilder`. El builder te brinda una API conveniente para insertar formas, texto y otros elementos.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por qué es importante:** `DocumentBuilder` trabaja directamente con el objeto subyacente `Document`, lo que te permite insertar formas sin manejar manualmente colecciones de nodos de bajo nivel.

### Agregar una forma de grupo

Una forma de grupo es un contenedor que puede contener otras formas. Piensa en ella como una carpeta para objetos de dibujo.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

El método `insertGroupShape()` crea un nodo `GroupShape` y lo devuelve para que puedas añadir formas hijas más tarde.  

---

## Agregar una forma de rectángulo al grupo

Ahora **agregaremos una forma de rectángulo** al grupo creado previamente. El rectángulo servirá como fondo o borde para la imagen.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Consejo:** Configurar `FillColor` y `StrokeColor` hace que el rectángulo sea visible en el documento final. Si omites estas propiedades, la forma podría aparecer transparente.

### Cómo agregar un rectángulo

El código anterior muestra **cómo agregar un rectángulo** creando una instancia `Shape` con `ShapeType.RECTANGLE` y luego añadiéndola al `GroupShape`. Este patrón funciona para cualquier otro tipo de forma (p. ej., `ELLIPSE`, `POLYLINE`).

---

## Establecer el tamaño de la forma para el rectángulo y la imagen

Un dimensionado adecuado garantiza que el rectángulo y la imagen se alineen correctamente. Aquí también **establecemos el tamaño de la forma** para la imagen que insertaremos a continuación.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Tanto el rectángulo como la imagen ahora comparten las mismas dimensiones (100 × 50 puntos). Como pertenecen al mismo grupo, mover o rotar el grupo afectará a ambas formas simultáneamente.

> **¿Por qué coincidir los tamaños?** Alinear las dimensiones garantiza que la imagen quede perfectamente dentro del rectángulo, creando un efecto limpio de “imagen enmarcada”.

---

## Guardar el documento y ver el resultado

Finalmente, escribimos el documento en disco. Abrir el archivo en Microsoft Word muestra las formas agrupadas como un único objeto seleccionable.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Cuando abras `output.docx`, verás un rectángulo con la imagen dentro. Al hacer clic en la forma se seleccionan tanto el rectángulo como la imagen porque están **agrupados**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Texto alternativo de la imagen:* *group shapes in word example* – un documento Word que muestra un rectángulo y una imagen agrupados.

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si necesito un tamaño diferente para la imagen?** | Ajusta `picture.setWidth()` y `picture.setHeight()` después de la inserción. El rectángulo puede mantener su tamaño original, o también puedes redimensionarlo para que coincida. |
| **¿Puedo agregar más formas al mismo grupo?** | Sí. Llama a `group.appendChild(newShape)` para cualquier objeto `Shape` adicional. |
| **¿Cómo rotar todo el grupo?** | Utiliza `group.setRotationAngle(double angleInRadians)`. La rotación se aplica a cada forma hija. |
| **¿Qué ocurre si el archivo de imagen falta?** | `insertImage` lanza `FileNotFoundException`. Envuelve la llamada en un bloque try‑catch y proporciona una forma de marcador de posición como alternativa. |
| **¿Es posible desagrupar más tarde?** | Llama a `group.removeAllChildren()` para separar los hijos, luego insértalos de nuevo en el documento individualmente. |

---

## Conclusión

Ahora tienes un ejemplo completo y ejecutable que muestra **cómo agrupar formas en Word**, **agregar una forma de rectángulo**, **establecer el tamaño de la forma** y **guardar** el documento usando Aspose.Words para Java. Al agrupar el rectángulo y la imagen, puedes mover, redimensionar o rotar ambos como una única unidad—exactamente lo que muchos escenarios de automatización de documentos requieren.

A partir de aquí podrías explorar:

* Agregar cuadros de texto al mismo grupo (`how to add rectangle`‑style text).  
* Aplicar diferentes patrones de relleno o degradados (`set shape size` combinado con estilo).  
* Usar la misma técnica para agrupar gráficos, tablas o SmartArt (`how to group shapes` en otros tipos de objetos).  

Siéntete libre de experimentar con otros tipos de forma, colores y opciones de diseño. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Agregar forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cómo convertir Word a PDF usando Aspose.Words para Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}