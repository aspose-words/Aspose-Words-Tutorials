---
category: general
date: 2026-08-07
description: Crear un documento Word en blanco con formas agrupadas en Java usando
  Aspose.Words. Aprende cómo agrupar formas, establecer el tamaño de la forma y agregar
  formas a Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: es
lastmod: 2026-08-07
og_description: Crea un documento de Word en blanco con formas agrupadas en Java.
  Sigue esta guía para establecer el tamaño de las formas, agregar formas a Word y
  dominar cómo agruparlas.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Crear documento Word en blanco con formas agrupadas – tutorial de Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Crear documento Word en blanco con formas agrupadas en Java
url: /es/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco con formas agrupadas en Java

Si necesitas **crear un documento Word en blanco** que contenga varias formas organizadas como una sola unidad, este tutorial te muestra exactamente cómo hacerlo. Verás un ejemplo completo y ejecutable que demuestra **cómo agrupar objetos shape**, ajustar sus dimensiones y **añadir formas a Word** usando Aspose.Words para Java.

La guía recorre cada paso, desde la configuración del proyecto hasta guardar el archivo .docx final, para que puedas copiar el código directamente a tu propia aplicación. No se requieren referencias externas, y la solución funciona con Aspose.Words 23.9 o posterior.

## Requisitos previos

Antes de comenzar, asegúrate de contar con:

* Java 17 (o cualquier JDK compatible)
* Maven o Gradle para la gestión de dependencias
* Una licencia de Aspose.Words para Java (o una clave de evaluación temporal)
* Un archivo de imagen de ejemplo (p. ej., `sample.jpg`) colocado en un directorio conocido

Si falta alguno de estos elementos, instálalo primero; el resto del tutorial asume que el entorno está listo.

## Paso 1: Añadir Aspose.Words a tu proyecto

Agrega la dependencia de Aspose.Words a tu `pom.xml` (Maven) o `build.gradle` (Gradle). Esta biblioteca proporciona las clases `Document`, `DocumentBuilder`, `GroupShape` y `Shape` que se usarán más adelante.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Por qué es importante:** Sin la biblioteca, ninguna de las API de procesamiento de Word está disponible y no puedes **crear un documento Word en blanco** de forma programática.

## Paso 2: Crear un documento Word en blanco

La primera acción concreta es instanciar un objeto `Document`, que representa un **documento Word en blanco** en memoria.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* crea un **documento Word en blanco** con la configuración predeterminada (página A4, márgenes por defecto). El `DocumentBuilder` asociado te permite insertar contenido en la posición actual del cursor.

## Paso 3: Insertar una forma grupal (cómo agrupar shape)

Una *forma grupal* actúa como contenedor para otras formas. En este paso aprenderás **cómo agrupar shape** para que se muevan juntos.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

El método `insertGroupShape` coloca el contenedor en la ubicación del cursor del builder. Agrupar es esencial cuando deseas tratar varios dibujos como una única entidad; este es el núcleo de la funcionalidad **group shapes word**.

## Paso 4: Crear un rectángulo y establecer su tamaño

Ahora agrega un rectángulo al grupo. Esto demuestra **establecer el tamaño de la forma**, necesario para un diseño preciso.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*¿Por qué establecer dimensiones?* Llamar explícitamente a `setWidth` y `setHeight` garantiza que el rectángulo aparezca exactamente como se pretende, sin depender de los estilos de forma predeterminados del documento.

## Paso 5: Insertar una imagen y añadirla al grupo

Añadir una imagen muestra otro caso de uso común para **añadir formas a word**. La imagen pasa a formar parte del mismo grupo, moviéndose junto con el rectángulo.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Si el archivo de imagen falta, Aspose.Words lanza una excepción. Un consejo práctico es verificar la ruta con antelación:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Paso 6: Guardar el documento que contiene las formas agrupadas

Finalmente, persiste el **documento Word en blanco** (ahora poblado con una forma grupal) en disco.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Al abrir `GroupShapeDemo.docx` en Microsoft Word, verás un único objeto agrupado que contiene un rectángulo y una imagen. Seleccionar cualquier parte del grupo moverá todo el contenedor, confirmando que las formas fueron **agrupadas** correctamente.

### Salida esperada

* Un archivo llamado `GroupShapeDemo.docx` en el directorio especificado.
* Al abrir el archivo se muestra un contenedor de 300 × 200 puntos con:
  * Un rectángulo de 100 × 50 puntos ubicado en (20, 20).
  * Una imagen ubicada en (150, 30) dentro del mismo contenedor.

## Casos límite y variaciones

| Situación | Cómo manejarla |
|-----------|----------------|
| **Tamaño de página diferente** | Llama a `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` antes de insertar el grupo. |
| **Múltiples grupos** | Repite los pasos 3‑5 con una nueva instancia de `GroupShape`; cada grupo puede posicionarse de forma independiente. |
| **Rotar formas** | Usa `shape.setRotationAngle(45.0);` para rotar un rectángulo o imagen antes de añadirlo al grupo. |
| **Formas que no son imágenes** | Crea objetos `Shape` de tipo `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., y añádelos igual que el rectángulo. |
| **Imágenes grandes** | Escala la foto con `picture.setWidth(80.0); picture.setHeight(60.0);` para mantener el grupo dentro de sus límites originales. |

Estas variaciones te permiten adaptar el patrón central a una amplia gama de escenarios de generación de documentos.

## Consejos prácticos basados en la experiencia

* **Consejo profesional:** Establece `RelativeHorizontalPosition` y `RelativeVerticalPosition` del grupo a `RelativeHorizontalPosition.PAGE` y `RelativeVerticalPosition.PAGE` si deseas que el grupo quede anclado a la página en lugar de al cursor.
* **Cuidado con:** Añadir una forma que exceda las dimensiones del grupo; la forma será recortada en Word. Ajusta el tamaño del grupo con `group.setWidth()` y `group.setHeight()` según sea necesario.
* **Nota de rendimiento:** Si generas muchos documentos en un bucle, reutiliza una única instancia de `DocumentBuilder` y llama a `doc.clone()` para reducir la sobrecarga de creación de objetos.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco** que contiene una colección agrupada de formas usando Aspose.Words para Java. El tutorial cubrió todo el flujo de trabajo: configurar la biblioteca, crear el documento, insertar un grupo, **establecer el tamaño de la forma**, **añadir formas a word** y guardar el resultado.

A partir de aquí puedes explorar características más avanzadas, como agrupar gráficos, aplicar estilos a formas individuales o exportar el documento a PDF. Cada uno de estos temas se basa en los mismos principios demostrados en esta guía.

---


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}