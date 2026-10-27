---
category: general
date: 2026-05-26
description: Crear una forma rectangular en un documento Word con Java y aplicar el
  efecto de sombra. Aprende cómo agregar sombra a la forma, establecer la distancia
  de la sombra y guardar el archivo.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: es
og_description: Crear una forma rectangular en un documento Word con Java, aplicar
  efecto de sombra, añadir sombra a la forma y establecer la distancia de la sombra
  con Aspose.Words.
og_title: Crear forma de rectángulo en documento Word con Java – Guía completa
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Crear forma de rectángulo en documento Word con Java – Guía completa paso a
  paso
url: /es/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma de rectángulo en un documento Word con Java – Guía completa paso a paso

¿Alguna vez necesitaste **crear una forma de rectángulo** en un documento Word con Java pero no sabías por dónde empezar? No estás solo: muchos desarrolladores se topan con este obstáculo al generar informes o facturas de forma programática. En este tutorial recorreremos paso a paso cómo **crear una forma de rectángulo**, aplicar una sombra pulida y afinar la distancia de la sombra para que el resultado luzca profesional.

Usaremos Aspose.Words para Java, una biblioteca robusta que permite manipular archivos Word sin necesidad de tener Microsoft Office instalado. Al final de esta guía podrás **crear documentos Word con Java** que **añadan sombra a la forma**, **apliquen efecto de sombra** y **establezcan la distancia de la sombra** con solo unas pocas líneas de código.

---

## Qué construirás

- Un archivo `.docx` nuevo que contiene un rectángulo cian.
- Una sombra realista que está difuminada, inclinada y parcialmente transparente.
- Control total sobre la distancia de la sombra respecto a la forma.
- Una clase Java lista para ejecutar que puedes insertar en cualquier proyecto Maven o Gradle.

Sin herramientas externas, sin pasos manuales en la UI: solo código puro.

---

## Requisitos previos

- Java 8 o superior (el código funciona en Java 11, Java 17, etc.).
- Biblioteca Aspose.Words para Java (disponible a través de Maven Central).
- Un IDE o editor de texto que prefieras (IntelliJ IDEA, Eclipse, VS Code…).
- Familiaridad básica con la sintaxis de Java.

Si nunca has añadido una dependencia Maven antes, aquí tienes el fragmento rápido:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Ahora, vamos al grano.

---

## Paso 1: Crear forma de rectángulo en un documento Word

Lo primero que necesitamos es un documento en blanco y un `DocumentBuilder`. Piensa en el builder como una pluma que escribe dentro del documento. Una vez que lo tengamos, podemos **crear una forma de rectángulo** con una única llamada a método.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Por qué es importante:** El método `insertShape` no solo crea la geometría sino que también añade la forma a la colección interna del documento, de modo que puedes comenzar a estilizarla de inmediato.

---

## Paso 2: Aplicar efecto de sombra a la forma

Ahora que el rectángulo está en la página, **aplicaremos el efecto de sombra**. Las sombras dan profundidad, haciendo que la forma parezca levantada de la página: una mejora sutil de UI que puede aumentar la legibilidad en los informes.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Consejo profesional:** Un difuminado de `5.0` se ve natural en la mayoría de los documentos mostrados en pantalla. Si vas a imprimir, quizá quieras un valor ligeramente menor para evitar una apariencia borrosa.

---

## Paso 3: Establecer distancia de sombra – Ajuste fino de la posición

Las sombras no solo se tratan de difuminado; también necesitan el desplazamiento correcto. Aquí es donde **establecemos la distancia de la sombra**. Una distancia de `7.0` puntos crea un desplazamiento moderado que se nota pero no resulta abrumador.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **¿Qué pasa si necesitas un desplazamiento mayor?** Aumenta el valor; disminúyelo para un aspecto más ajustado. Recuerda que la distancia trabaja junto con el ángulo para posicionar la sombra correctamente.

---

## Paso 4: Guardar el documento – Persistir tu trabajo

Finalmente, escribimos el documento en disco. Cambia la ruta a donde desees que se guarde el archivo.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Ejecutar la clase crea un archivo `shadow.docx` que, al abrirse en Microsoft Word o LibreOffice, muestra un rectángulo cian con una sombra gris suave inclinada a 45° y desplazada 7 puntos.

---

## Ejemplo completo y funcional

A continuación tienes el código completo, listo para copiar y pegar. Incluye todas las importaciones, comentarios y la llamada final a `save`.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Salida esperada:** Abre `shadow.docx` → verás un rectángulo cian centrado en la primera página, proyectando una sombra gris sutil ligeramente desplazada hacia abajo‑derecha. El difuminado y la transparencia de la sombra le dan un aspecto de iluminación natural.

---

## Preguntas frecuentes y casos especiales

### “¿Puedo usar una forma diferente?”

Claro. Sustituye `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.LINE` o cualquier otro enum soportado. El resto del código de sombra permanece igual.

### “¿Qué pasa si necesito múltiples sombras?”

Aspose.Words solo admite una sombra por forma. Para simular varias sombras, duplica la forma, desplaza cada copia y ajusta la transparencia.

### “¿La sombra se ve en LibreOffice?”

Sí—Aspose.Words escribe OOXML estándar, que LibreOffice interpreta correctamente. La sombra puede verse ligeramente distinta debido a los motores de renderizado, pero el efecto persiste.

### “¿Cómo cambio el color de la sombra para que coincida con mi marca?”

Simplemente reemplaza `java.awt.Color.GRAY` por cualquier `java.awt.Color` que prefieras, por ejemplo `new java.awt.Color(0, 120, 215)` para un azul corporativo.

---

## Ilustración

![crear forma de rectángulo en documento Word con Java](https://example.com/images/rectangle-shadow.png)

*Texto alternativo:* **crear forma de rectángulo** ilustración que muestra un rectángulo cian con una sombra gris en un documento Word.

---

## Recapitulación y próximos pasos

Hemos cubierto cómo **crear una forma de rectángulo**, **aplicar efecto de sombra**, **añadir sombra a la forma** y **establecer la distancia de la sombra** usando Aspose.Words para Java. El código es autónomo, se ejecuta en cualquier JDK moderno y produce un archivo `.docx` pulido listo para distribuir.

¿Quieres ir más allá? Prueba:

- Añadir texto dentro del rectángulo con `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Crear una tabla de formas para construir un diagrama.
- Exportar el documento a PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

Cada una de estas extensiones se basa en los mismos fundamentos que acabamos de explorar, por lo que te sentirás cómodo ampliando el ejemplo.

---

## Reflexiones finales

Dominar tareas como **crear documentos Word con Java** —incluyendo formas y sombras— te brinda una gran ventaja al automatizar informes, contratos o material de marketing. El enfoque mostrado aquí es limpio, mantenible y, lo más importante, fácil de ajustar para cualquier estilo visual que necesites.

Ejecuta el código, modifica el difuminado, el ángulo y la distancia, y observa cómo tus documentos pasan de ser simples a estar pulidos. Si te encuentras con algún obstáculo, deja un comentario abajo; estaré encantado de ayudar.

¡Feliz codificación!

## Tutoriales relacionados

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}