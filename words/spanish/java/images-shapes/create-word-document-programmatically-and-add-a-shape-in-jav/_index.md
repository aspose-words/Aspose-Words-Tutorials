---
category: general
date: 2026-10-26
description: Aprende cómo crear un documento de Word programáticamente, agregar una
  forma y ocultar un objeto en Word usando Aspose.Words para Java – guía paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: es
lastmod: 2026-10-26
og_description: Crea documentos Word programáticamente, aprende a agregar formas y
  ocultar objetos en Word con Aspose.Words para Java. Ejemplo completo y ejecutable.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Crear documento Word programáticamente – agregar y ocultar formas en Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Crear documento Word programáticamente y agregar una forma en Java
url: /es/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word programáticamente y agregar una forma en Java

Si necesitas **crear un documento Word programáticamente**, este tutorial te muestra exactamente cómo hacerlo, agregar una forma y luego ocultar el objeto en Word. Ya sea que estés construyendo un generador de informes o un sistema de contratos automatizado, obtendrás una solución completa y lista‑para‑ejecutar en solo unos minutos.

Aprenderás a:

* Inicializar un documento Word con Aspose.Words for Java.  
* Insertar una elipse (o cualquier otra forma) usando la técnica **cómo agregar forma**.  
* Ocultar esa forma para que nunca aparezca cuando se abra el archivo, respondiendo a la pregunta **cómo ocultar forma**.  

No se requieren herramientas externas más allá de la biblioteca Aspose.Words, y el código funciona con Java 17 y versiones posteriores.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java Development Kit (JDK) 17 o superior instalado.  
* Maven o Gradle para gestionar dependencias (el ejemplo usa Maven).  
* Una licencia válida de Aspose.Words for Java (la evaluación gratuita sirve para pruebas).  

Si eres nuevo en Aspose.Words, consulta la guía oficial Getting Started, pero no necesitarás leerla para seguir este tutorial.

## Dependencia Maven

Agrega la siguiente dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Consejo:** Mantén el número de versión actualizado; las versiones más recientes incluyen correcciones de errores para el manejo de formas.

## Paso 1: Crear documento Word programáticamente – inicializando el documento

Lo primero que haces cuando **creas un documento Word programáticamente** es instanciar un objeto `Document`. Este objeto representa todo el archivo .docx en memoria.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué este paso es importante*: La clase `Document` es el punto de entrada para todas las operaciones de procesamiento de Word. Sin ella no puedes agregar páginas, párrafos ni formas.

## Paso 2: Cómo agregar forma – insertando una elipse

Ahora abordamos la parte **cómo agregar forma** del tutorial. Aspose.Words admite muchos tipos de forma (Ellipse, Rectangle, TextBox, etc.). A continuación insertamos una elipse con un ancho y alto de 50 puntos.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

El método `insertShape` devuelve un objeto `Shape` que puedes personalizar aún más—color, estilo de línea, rotación y más. Las coordenadas se miden en puntos (1/72 de pulgada).

*Por qué podrías querer agregar una forma*: Las formas son útiles para marcas de agua, elementos decorativos o marcadores de posición que luego ocultas o reemplazas.

## Paso 3: Cómo ocultar forma – haciendo el objeto invisible en Word

Para responder a la pregunta **cómo ocultar forma**, simplemente establece la propiedad `Hidden` de la forma en `true`. Esto indica a Word que trate la forma como un objeto oculto, de modo que nunca se renderice en la vista del documento ni en la impresión.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Si necesitas **ocultar objeto en Word** para un usuario o condición específica, puedes alternar esta propiedad en tiempo de ejecución según tu lógica de negocio.

> **Nota:** Las formas ocultas siguen formando parte de la estructura XML del documento. Pueden revelarse más tarde estableciendo `setHidden(false)`.

## Paso 4: Guardar el documento

Después de agregar y ocultar la forma, escribe el documento en disco.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Cuando abras `HiddenShapeDemo.docx` en Microsoft Word, verás una página en blanco porque la elipse está oculta. El documento se comporta como cualquier archivo Word normal.

## Ejemplo completo funcionando

Uniendo todas las piezas, aquí tienes el programa completo y ejecutable:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Salida esperada**

```
Document created successfully.
```

Al abrir `HiddenShapeDemo.docx` se muestra una página vacía; la elipse oculta no se renderiza, confirmando que la operación **ocultar objeto en Word** se realizó con éxito.

## Casos límite y variaciones

| Situación | Qué cambiar | Por qué |
|-----------|-------------|---------|
| Ocultar un rectángulo en lugar de una elipse | Usar `ShapeType.RECTANGLE` en `insertShape` | Marcador de posición visual diferente |
| Ocultar varias formas a la vez | Recorrer `doc.getChildNodes(NodeType.SHAPE, true)` y establecer `setHidden(true)` | Útil para procesamiento en bloque |
| Mostrar la forma solo en vista de impresión | Establecer `shape.setVisible(false)` y `shape.setPrint(true)` | Word distingue entre visibilidad en pantalla e impresión |
| Usar una unidad de medida diferente | Llamar `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Se alinea con los requisitos de tu diseño |

## Errores comunes

* **Olvidar llamar a `setHidden(true)`** – la forma aparecerá normalmente.  
* **Guardar el documento antes de ocultar la forma** – el orden importa; oculta primero y luego guarda.  
* **Usar una versión desactualizada de Aspose.Words** – las versiones antiguas pueden no incluir la API `setHidden`.  

Siempre prueba el archivo generado en la versión objetivo de Microsoft Word para asegurarte de que el estado oculto se comporte como se espera.

## Conclusión

En esta guía aprendiste a **crear documento Word programáticamente**, **agregar forma** y **ocultar objeto en Word** usando Aspose.Words for Java. El ejemplo completo muestra los pasos exactos, desde la inicialización del documento hasta guardar un archivo donde la forma nunca aparece.  

A partir de aquí puedes:

* Experimentar con otros tipos de forma (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Combinar formas ocultas con marcadores de posición para crear plantillas dinámicas.  
* Explorar las propiedades `setVisible` y `setPrint` para un control más granular sobre la visibilidad de los objetos.

¡Feliz codificación y que disfrutes automatizando tus documentos Word!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un documento Word en blanco con Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Cómo ocultar forma en un documento Word usando Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Crear documento Word Java – Agregar forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}