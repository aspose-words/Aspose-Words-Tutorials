---
category: general
date: 2026-11-15
description: Crear una forma rectangular en Word con Java y aprender cómo agregar
  formas a Word, establecer las dimensiones de la forma y guardar el documento de
  Word de manera eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: es
lastmod: 2026-11-15
og_description: Crea una forma rectangular en un documento de Word usando Java. Aprende
  a agregar formas a Word, establecer las dimensiones de la forma y guardar el documento
  de Word en minutos.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Crear forma rectangular en Word con Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Crear forma de rectángulo en un documento de Word usando Java
url: /es/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma de rectángulo en un documento Word usando Java

Si necesitas **crear forma de rectángulo** dentro de un archivo Word, esta guía te muestra exactamente cómo hacerlo con Java. Verás cómo **añadir formas a Word**, controlar el **establecer dimensiones de la forma**, y finalmente **guardar documento Word** sin salir de tu IDE.

En las secciones siguientes obtendrás un ejemplo completo y ejecutable, una explicación de cada línea y consejos para errores comunes como problemas de tamaño y compatibilidad de documentos. No se requieren referencias externas—solo la biblioteca Aspose.Words for Java.

## Lo que aprenderás

* Cómo inicializar un `Document` y un `DocumentBuilder`.
* Cómo insertar una **group shape** y colocar un rectángulo dentro de ella.
* Cómo **definir el tamaño de la forma** usando `setWidth` y `setHeight`.
* Cómo **guardar documento Word** en formato `.docx`.
* Manejo de casos límite para diferentes tamaños de página y configuraciones de DPI.

### Requisitos previos

* Java 17 o posterior (el código también compila con Java 8).
* Aspose.Words for Java 23.10 o más reciente – puedes obtenerlo de Maven Central.
* Un entendimiento básico de la sintaxis de Java y conceptos orientados a objetos.

> **Consejo profesional:** Si planeas añadir más formas más adelante (p. ej., círculos o cuadros de texto), mantenlas dentro del mismo `GroupShape`. Esto hace que mover, rotar o formatear toda la colección sea mucho más fácil.

## Paso 1: Inicializar el documento y el builder

El primer paso es crear un archivo Word en blanco y un `DocumentBuilder` que te permite escribir contenido.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante:* Un `Document` representa todo el archivo, mientras que `DocumentBuilder` ofrece métodos de alto nivel para insertar texto, tablas y **shapes**. Sin el builder tendrías que manipular nodos de bajo nivel manualmente.

## Paso 2: Insertar una group shape para contener múltiples formas

Una **group shape** actúa como un contenedor; puedes añadir varias formas y tratarlas como un solo objeto más tarde (p. ej., mover o rotar juntas).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*¿Por qué usar una group shape?* Si más adelante decides añadir flechas, círculos o etiquetas alrededor del rectángulo, el grupo mantiene todo alineado. También simplifica el flujo de trabajo de **add shapes to Word** porque solo necesitas una llamada a `appendChild` para cada nueva forma.

## Paso 3: Crear la forma de rectángulo

Ahora creamos el rectángulo real que vivirá dentro del grupo. El constructor `Shape` necesita el `Document` propietario y el tipo de forma que deseas.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*¿Por qué un rectángulo?* `ShapeType.RECTANGLE` es la primitiva más común para resaltar secciones, crear marcadores de posición o dibujar maquetas simples de UI directamente dentro de Word.

## Paso 4: Definir el tamaño del rectángulo

Establecer las dimensiones es donde **set shape dimensions** se vuelve importante. Puedes usar cualquier unidad de medida soportada por Aspose.Words; el valor predeterminado son puntos (1 pt = 1/72 pulgada).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Nota:** Si prefieres milímetros, llama a `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` donde `1.39 in ≈ 35 mm`. Esto demuestra la flexibilidad de **define shape size**.

## Paso 5: Añadir el rectángulo a la group shape

Agregar el rectángulo al grupo creado previamente hace que aparezca en el documento.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

En este punto el rectángulo está posicionado en la esquina superior izquierda del grupo. Puedes moverlo más tarde con `rectangle.setLeft(...)` y `rectangle.setTop(...)` si necesitas una colocación precisa.

## Paso 6: (Opcional) Guardar el documento para ver el resultado

Finalmente, escribe el documento en disco. Este es el paso de **save Word document** que produce un archivo `.docx` que puedes abrir en Microsoft Word, LibreOffice o Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Ejecutar el programa crea `RectangleShapeDemo.docx` que contiene un solo rectángulo dentro de una group shape. Abrir el archivo muestra un rectángulo blanco simple—exactamente del tamaño que definiste.

### Resultado esperado

* Un archivo Word llamado `RectangleShapeDemo.docx`.
* Dentro del primer párrafo, una group shape que contiene un rectángulo de 100 pt × 50 pt.
* No se añade texto, por lo que el rectángulo aparece en una página en blanco.

## Variaciones comunes y casos límite

| Situación | Cómo adaptar el código |
|-----------|-----------------------|
| **Tamaño de página diferente** (p. ej., A4) | Llama a `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` antes de insertar la forma. |
| **DPI más alto para impresión** | Multiplica ancho/alto por el factor DPI deseado, p. ej., `rectangle.setWidth(200 * 2);` para doble resolución. |
| **Añadir una etiqueta de texto dentro del rectángulo** | Crea un `Shape` de tipo `TEXT_BOX`, establece su `setWidth`/`setHeight` para que coincida con el rectángulo, y luego añádelo al mismo `GroupShape`. |
| **Rotar el rectángulo** | Usa `rectangle.setRotationAngle(45);` para rotar 45 grados en sentido horario. |
| **Guardar como PDF en lugar de DOCX** | Reemplaza `document.save("output.docx");` por `document.save("output.pdf");` – la misma API funciona para PDF, preservando el rectángulo. |

## Consejos profesionales para una implementación robusta

1. **Reutiliza el builder** – después de insertar la group shape, puedes seguir añadiendo párrafos o tablas sin crear una nueva instancia de builder.
2. **Libera recursos** – aunque el recolector de basura de Java maneja la mayoría de los objetos, llamar explícitamente a `document.close();` (si usas streams) previene fugas de manejadores de archivo.
3. **Valida dimensiones** – antes de llamar a `setWidth`/`setHeight`, asegúrate de que los valores sean positivos; los valores negativos lanzan `IllegalArgumentException`.
4. **Compatibilidad de versiones** – el código funciona con Aspose.Words 23.x y posteriores. Versiones anteriores pueden requerir `Shape.setSize(width, height)` en lugar de los setters separados.

## Ejemplo completo y ejecutable

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Verificación del resultado:** Abre `output/RectangleShapeDemo.docx` en Microsoft Word. Deberías ver un rectángulo del tamaño especificado centrado en la parte superior de la primera página. Si el rectángulo aparece demasiado pequeño, ajusta los valores pasados a `setWidth` y `setHeight`.

## Conclusión

Ahora sabes cómo **crear forma de rectángulo** en un archivo Word usando Java, cómo **añadir formas a Word** mediante un `GroupShape`, cómo **establecer dimensiones de la forma** y **definir el tamaño de la forma**, y finalmente cómo **guardar documento Word** para su distribución. El mismo patrón funciona para otros tipos de forma, permitiéndote crear diagramas complejos programáticamente.

### ¿Qué sigue?

* Explora **add shapes to Word** insertando círculos, flechas o cuadros de texto.
* Combina múltiples formas en una sola `GroupShape` y aplica transformaciones (rotar, voltear).
* Genera informes que incrusten gráficos como formas, luego **save Word document** como PDF para compartir.

¡Siéntete libre de experimentar con las dimensiones, colores y posicionamiento para adaptarlos a tu escenario específico! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma de rectángulo en documento Word Java – Guía completa paso a paso](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Crear documento Word Java – ocultar forma y establecer color de relleno](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}