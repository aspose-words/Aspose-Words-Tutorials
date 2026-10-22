---
category: general
date: 2026-09-27
description: Crear un documento Word en blanco en Java y agrupar formas usando Aspose.Words.
  Aprenda a establecer el tamaño de la forma, el color de relleno de la forma y a
  añadir un elemento hijo al grupo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: es
lastmod: 2026-09-27
og_description: Crear un documento de Word en blanco en Java con Aspose.Words. Este
  tutorial muestra cómo agrupar formas en Word, establecer el tamaño de la forma,
  establecer el color de relleno de la forma y añadir un elemento hijo al grupo.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Crear un documento Word en blanco y agrupar formas en Java – guía paso a
  paso
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cómo crear un documento de Word en blanco y agrupar formas en Java
url: /es/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agrupar formas en Java

Si necesitas **crear un documento Word en blanco** de forma programática, esta guía te muestra exactamente cómo hacerlo con Aspose.Words for Java. También aprenderás a **agrupar formas en Word**, establecer el tamaño de cada forma, aplicar un color de relleno y **agregar un hijo al grupo** para que los objetos se comporten como una sola unidad.

Trabajar con archivos Word desde código te evita el formateo manual y te permite generar informes, contratos o folletos de marketing automáticamente. Al final de este tutorial tendrás un programa Java ejecutable que produce un archivo `.docx` que contiene un rectángulo azul y una imagen, ambos agrupados.

## Requisitos previos

- Java 17 (o cualquier JDK reciente) instalado.
- Maven o Gradle para gestionar dependencias.
- Una licencia de Aspose.Words for Java (la evaluación gratuita funciona para pruebas).
- Un archivo de imagen de muestra (p. ej., `sample.jpg`) colocado en una carpeta que puedas referenciar desde el código.

> **Consejo profesional:** Mantén tus archivos de imagen en un directorio `resources` y cárgalos con `ClassLoader.getResourceAsStream` para evitar rutas absolutas codificadas.

## Paso 1: Crear un documento Word en blanco y agregar un GroupShape

El primer paso es instanciar un nuevo objeto `Document`, que representa un archivo Word vacío, y luego insertar un `GroupShape`. El grupo servirá como contenedor para cualquier forma que agregues más adelante.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Por qué es importante:* Un `GroupShape` te permite mover, rotar o formatear varias formas juntas, lo cual es esencial para diseños complejos como diagramas o marcas de agua.

## Paso 2: Insertar un rectángulo y **establecer el tamaño de la forma**

A continuación, crea un rectángulo, define sus dimensiones y añádelo al grupo. Esto demuestra la operación **set shape size**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explicación:* `setWidth` y `setHeight` controlan el tamaño exacto de la forma en puntos (1 punto = 1/72 de pulgada). Ajusta estos valores para que se adapten a los requisitos de tu diseño.

## Paso 3: **Establecer el color de relleno de la forma** para el rectángulo

El fondo del rectángulo se establece en azul usando `setFillColor`. Puedes usar cualquier constante `java.awt.Color` o crear un color RGB personalizado.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Por qué es útil:* Los colores de relleno ayudan a diferenciar visualmente los objetos, especialmente cuando luego exportas el documento a PDF o lo imprimes.

## Paso 4: Insertar una imagen y **agregar un hijo al grupo**

Ahora agrega una imagen al mismo `GroupShape`. La imagen se inserta mediante `DocumentBuilder.insertImage`, y luego se agrega al grupo para que se mueva junto con el rectángulo.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Caso límite:* Si la ruta de la imagen es incorrecta, Aspose.Words lanza `FileNotFoundException`. Usa una ruta relativa o carga la imagen desde los recursos para evitar este problema.

## Paso 5: **Guardar el documento con las formas agrupadas**

Finalmente, escribe el documento en disco. El archivo resultante contendrá el rectángulo y la imagen agrupados juntos.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Resultado esperado

- Aparece un archivo llamado `GroupShape.docx` en el directorio especificado.
- Al abrir el archivo en Microsoft Word se muestra una página en blanco con un rectángulo azul y la imagen elegida, ambos seleccionados como un solo objeto (puedes moverlos o redimensionarlos juntos).

![crear documento word en blanco con formas agrupadas](/images/grouped-shapes.png "crear documento word en blanco con formas agrupadas")

*La captura de pantalla anterior muestra las formas agrupadas finales dentro del documento Word recién creado.*

## Variaciones comunes y consejos adicionales

| Situación | Cómo manejarlo |
|-----------|-----------------|
| **Múltiples imágenes** | Inserta cada imagen con `builder.insertImage` y llama a `group.appendChild(picture)` para cada una. |
| **Tipos de forma diferentes** | Usa `ShapeType.OVAL`, `ShapeType.LINE`, etc., al construir el objeto `Shape`. |
| **Cambiar la posición del grupo** | Después de agregar todos los hijos, establece `group.setLeft(x)` y `group.setTop(y)` para mover todo el grupo. |
| **Exportar a PDF** | Llama a `doc.save("output.pdf")` después de agrupar; el PDF preservará la agrupación. |
| **Aplicación de licencia** | Si ejecutas la versión de evaluación, aparecerá una marca de agua. Instala una licencia válida para eliminarla. |

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, insertar un **GroupShape**, **establecer el tamaño de la forma**, **establecer el color de relleno de la forma** y **agregar un hijo al grupo** usando Aspose.Words for Java. Este patrón te permite crear diseños complejos y programáticos que pueden editarse posteriormente en Word o exportarse a otros formatos.

A continuación, explora cómo **agrupar formas en Word** con cuadros de texto, agregar hipervínculos a las formas o automatizar la generación de informes de varias páginas. Los mismos principios se aplican: simplemente crea formas adicionales, configura sus propiedades y añádelas al mismo grupo.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de rectángulo en Word con Java – Guía completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Crear documento Word Java – Agregar forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}