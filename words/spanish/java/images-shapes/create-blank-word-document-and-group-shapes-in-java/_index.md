---
category: general
date: 2026-08-23
description: Crea un documento Word en blanco con Aspose.Words para Java, aprende
  a agrupar formas, colorear una forma rectangular y guardar el documento como docx
  en minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: es
lastmod: 2026-08-23
og_description: Crea un documento Word en blanco con Aspose.Words para Java, luego
  observa cómo agrupar formas, colorear una forma rectangular y guardar el documento
  como docx de manera eficiente.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Crear documento Word en blanco y agrupar formas en Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Crear documento Word en blanco y agrupar formas en Java
url: /es/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco y agrupar formas en Java

Si necesitas **crear documento Word en blanco** de forma programática, Aspose.Words for Java lo hace sencillo. Este tutorial te muestra exactamente cómo **crear documento Word en blanco**, insertar un **grupo de formas en Word**, aplicar **forma de rectángulo de color**, y finalmente **guardar el documento como docx**. Al final tendrás un fragmento de código reutilizable que puedes insertar en cualquier proyecto Java.

Aprenderás:

* La dependencia requerida de Maven/Gradle para Aspose.Words.
* Cómo instanciar un documento en blanco y un `DocumentBuilder`.
* Los pasos exactos para **agrupar formas** dentro de un `GroupShape`.
* Cómo establecer colores de relleno en formas de rectángulo.
* La mejor práctica para **guardar el documento como docx** y dónde encontrar el archivo de salida.

No se asume experiencia previa con Aspose.Words, pero deberías estar cómodo con el desarrollo básico en Java y tener instalado un JDK 8 o superior.

---

## Prerequisites

| Requisito | Versión / Detalle |
|-------------|-------------------|
| Kit de desarrollo Java | 8 o superior |
| Herramienta de compilación | Maven 3+ o Gradle 6+ |
| Aspose.Words for Java | 23.12 o posterior (la última versión al momento de escribir) |
| IDE (opcional) | IntelliJ IDEA, Eclipse, VS Code, o cualquier editor compatible con Java |

---

## Step 1: Add Aspose.Words to your project

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Si estás usando un proxy corporativo, configura Maven/Gradle para obtener el paquete del repositorio de Aspose como se describe en la documentación oficial.

---

## Step 2: **Create blank Word document** with a builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

El constructor `Document` crea un contenedor `.docx` vacío en memoria. El `DocumentBuilder` te brinda una API fluida para agregar contenido, incluidas formas.

---

## Step 3: Insert a **group shapes in Word** container

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Un `GroupShape` funciona como un mini‑lienzo. Todas las formas añadidas a él se mueven juntas, lo que es exactamente **cómo agrupar formas** para mantener la consistencia del diseño.

---

## Step 4: Add the first **color rectangle shape** (red)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

La constante `ShapeType.RECTANGLE` crea un rectángulo simple. Al llamar a `getFill().setForeColor(...)` controlas la **forma de rectángulo de color**. Puedes reemplazar `java.awt.Color.RED` con cualquier constante `java.awt.Color` o un valor RGB personalizado.

---

## Step 5: Add the second **color rectangle shape** (green) and position it

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Configurar `setLeft` (o `setTop`) mueve la forma relativa a la esquina superior‑izquierda del contenedor **grupo de formas en Word**. Esto demuestra **cómo agrupar formas** con posicionamiento preciso.

---

## Step 6: **Save document as docx** and verify the result

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

El método `save` escribe automáticamente un archivo `.docx` porque la extensión del archivo es `.docx`. Si necesitas un formato diferente (p.ej., PDF), pasa el enum `SaveFormat` correspondiente.

> **Tip:** Asegúrate de que el directorio de destino (`output/` en este ejemplo) exista o créalo programáticamente con `new File("output").mkdirs();`.

---

## Full source code for quick copy‑paste

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Salida esperada:** Al abrir `GroupShapeDemo.docx` en Microsoft Word se muestra una sola página que contiene dos rectángulos coloreados (rojo a la izquierda, verde a la derecha) que se mueven juntos al seleccionar el grupo.

---

## Common questions and edge‑case handling

| Pregunta | Respuesta |
|----------|-----------|
| *¿Puedo agregar más de dos formas al mismo grupo?* | Sí. Llama a `groupShape.appendChild(yourShape)` para cada forma adicional. El grupo redimensionará automáticamente para ajustarse a la mayor extensión, o puedes ajustar manualmente su ancho/alto. |
| *¿Qué pasa si necesito un tipo de forma diferente (p.ej., elipse)?* | Reemplaza `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`. La misma lógica de color de relleno se aplica. |
| *¿Necesito disponer del objeto `Document`?* | Aspose.Words gestiona los recursos nativos internamente. Cuando la JVM finaliza, los recursos se liberan. Para aplicaciones de larga duración, llama a `doc.dispose();` si utilizas la versión **Aspose.Words for Java (Native)**. |
| *¿Cómo cambio el orden Z para que un rectángulo aparezca encima?* | Usa `groupShape.insertAfter(shape, referenceShape);` o `groupShape.insertBefore(shape, referenceShape);` para reordenar los hijos dentro del grupo. |
| *¿Puedo agrupar formas a través de diferentes secciones?* | No. Un `GroupShape` debe residir dentro de un solo párrafo o contenedor de forma. Para agrupar a través de secciones, crea grupos separados en cada sección. |

---

## Conclusion

Ahora sabes cómo **crear documento Word en blanco** con Aspose.Words for Java, **agrupar formas en Word**, aplicar estilo a la **forma de rectángulo de color**, y **guardar el documento como docx**. Este patrón escala a diseños más complejos: simplemente agrega formas adicionales, ajusta los desplazamientos y, opcionalmente, establece texto, imágenes o hipervínculos dentro del grupo.

**Próximos pasos** que podrías explorar:

* Usa **grupo de formas en Word** para crear diagramas de flujo o maquetas de UI.
* Experimenta con **guardar el documento como docx** combinado con conversión a PDF (`doc.save("out.pdf")`).
* Aplica degradados o patrones a la **forma de rectángulo de color** para un diseño visual más rico.
* Combina formas agrupadas con tablas o gráficos para documentos de informes avanzados.

Siéntete libre de modificar las dimensiones, colores o tipos de forma para que coincidan con la identidad de tu proyecto. ¡Feliz codificación!

## What Should You Learn Next?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}