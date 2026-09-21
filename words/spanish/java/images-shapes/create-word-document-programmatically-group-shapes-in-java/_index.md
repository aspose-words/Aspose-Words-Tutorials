---
category: general
date: 2026-09-21
description: Crear un documento de Word programáticamente usando Java. Aprende cómo
  agrupar formas en Word, insertar una forma rectangular, establecer el tamaño de
  la forma y agregar formas a un documento de Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: es
lastmod: 2026-09-21
og_description: 'Crear documento de Word programáticamente con Java: esta guía muestra
  cómo agrupar formas en Word, insertar formas rectangulares, establecer el tamaño
  de la forma y agregar formas a un documento de Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Crear documento Word programáticamente, agrupar formas en Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Crear documento Word programáticamente, agrupar formas en Java
url: /es/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word programáticamente, agrupar formas en Java

Si necesitas **crear documento Word programáticamente**, esta guía te lleva paso a paso por una solución completa. Verás cómo **agrupar formas en Word**, insertar un rectángulo, establecer su tamaño y añadir otras formas, todo usando Java y la biblioteca Aspose.Words for Java.

El tutorial cubre cada paso, desde la configuración del proyecto hasta guardar el archivo .docx final. Al final podrás generar un documento Word que contiene un rectángulo y una imagen envueltos dentro de un único grupo, lo que facilita moverlos o redimensionarlos juntos. No se requiere experiencia previa con la API de Aspose.Words, pero deberías contar con un entorno básico de desarrollo Java.

## Requisitos previos

* Java Development Kit (JDK) 8 o superior  
* Maven o Gradle para la gestión de dependencias  
* Aspose.Words for Java 23.9 (o la última versión) – la biblioteca es gratuita para evaluación  
* Un archivo de imagen (p. ej., `sample.jpg`) ubicado en un directorio conocido  

Tener estos elementos listos garantiza que el código se ejecute sin configuraciones adicionales.

## Paso 1: Configurar el proyecto e importar Aspose.Words

Crea un proyecto Maven (o agrega la dependencia a tu `pom.xml` existente):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Si prefieres Gradle, añade lo siguiente a `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Una vez resuelta la dependencia, importa las clases necesarias en tu archivo fuente Java:

```java
import com.aspose.words.*;
import java.io.File;
```

## Paso 2: Crear el documento Word programáticamente

La primera operación en cualquier escenario de automatización es instanciar un objeto `Document` y un `DocumentBuilder`. El builder simplifica la inserción de texto, imágenes y formas.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

En este punto el documento solo existe en memoria. Ahora puedes comenzar a añadir formas.

## Paso 3: Insertar una forma de rectángulo – cómo insertar forma de rectángulo

Un rectángulo es una `Shape` básica con `ShapeType.RECTANGLE`. Controlas sus dimensiones con `setWidth`, `setHeight` y lo posicionas con `setTop` y `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Por qué es importante:** Establecer el tamaño y la posición explícitamente (`set shape size word`) garantiza que el rectángulo aparezca exactamente donde lo esperas, sin depender del diseño predeterminado del documento.

## Paso 4: Insertar una imagen – añadir formas al documento Word

El `DocumentBuilder` puede insertar una imagen directamente desde una ruta de archivo. Después de la inserción, puedes reposicionar la foto como cualquier otra forma.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Tanto el rectángulo como la imagen son ahora formas independientes dentro del documento.

## Paso 5: Agrupar las formas – cómo agrupar formas en Word

Agrupar formas es útil cuando deseas moverlas o redimensionarlas como una sola unidad. Aspose.Words proporciona un contenedor `GroupShape` para este propósito.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Cuando el grupo se guarda, Word trata a los dos hijos como un único objeto lógico. Más adelante puedes seleccionar el grupo y arrastrarlo, y tanto el rectángulo como la imagen se moverán juntos.

## Paso 6: Guardar el documento

Finalmente, escribe el documento en disco. La ruta debe ser accesible para el proceso Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Ejecutar el método `main` genera un archivo llamado **GroupShapeExample.docx**. Ábrelo en Microsoft Word para ver un rectángulo y una imagen bloqueados juntos dentro de un grupo. Seleccionar el grupo permite mover ambos objetos simultáneamente, confirmando que el agrupamiento se realizó con éxito.

## Resultado esperado

* Un archivo Word (`GroupShapeExample.docx`) ubicado en el directorio que especificaste.  
* Dentro del archivo, un rectángulo (relleno gris claro) aparece en la esquina superior izquierda, y la imagen se sitúa justo debajo.  
* Ambos objetos forman parte de un único grupo, de modo que arrastrar uno mueve al otro.

## Variaciones comunes y casos límite

| Situación | Recomendación |
|-----------|----------------|
| **Diferentes formatos de imagen** | Aspose.Words admite PNG, BMP, GIF y TIFF. Usa la extensión de archivo adecuada en `insertImage`. |
| **Dimensiones negativas** | La API lanza `ArgumentException`. Siempre valida el ancho y la altura antes de llamar a `setWidth` / `setHeight`. |
| **Documentos grandes** | Agrupar muchas formas puede aumentar el tamaño del archivo. Considera combinar formas en una sola imagen cuando el rendimiento sea crítico. |
| **Compatibilidad de versiones de Word** | GroupShape funciona con Word 2007 (`.docx`) y versiones posteriores. Para archivos `.doc` más antiguos, el grupo se aplanará. |
| **Posicionamiento dinámico** | Usa cálculos basados en el tamaño de página (`doc.getFirstSection().getPageSetup().getPageWidth()`) si necesitas una colocación adaptativa. |

**Consejo profesional:** Después de crear el grupo, puedes cambiar

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma de rectángulo en Word con Java – Guía completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Crear Group Shape en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}