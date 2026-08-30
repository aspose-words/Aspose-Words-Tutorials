---
category: general
date: 2026-07-29
description: Crear documento de Word en Java usando Aspose.Words. Aprende a insertar
  una forma rectangular, agrupar formas en Word y guardar el documento como docx rápidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: es
lastmod: 2026-07-29
og_description: Crea un documento Word en Java con Aspose.Words. Inserta una forma
  rectangular, agrupa formas en Word y guarda el documento como docx en minutos.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Crear documento Word con formas – Tutorial de Java Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Crear documento Word con formas en Java – Guía completa de Aspose.Words
url: /es/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word con formas en Java – Guía completa de Aspose.Words

¿Alguna vez te has preguntado cómo **crear un documento de Word** programáticamente y adornarlo con gráficos personalizados? No eres el único. Ya sea que necesites generar un informe con secciones resaltadas o diseñar un folleto al vuelo, dominar el manejo de formas en Word puede ahorrarte horas de trabajo manual.

En este tutorial recorreremos paso a paso cómo **crear un documento de Word** usando Aspose.Words para Java, **insertar una forma rectangular**, **agrupar formas en Word**, y finalmente **guardar el documento como docx**. Al final tendrás un ejemplo completamente funcional que podrás incorporar a cualquier proyecto.

## Lo que aprenderás

- Un archivo de Word nuevo generado completamente desde código Java.  
- Dos formas distintas (un rectángulo y una elipse) añadidas a la página.  
- Esas formas agrupadas mediante la API **group shapes in word**, comportándose como un solo objeto.  
- El archivo guardado en disco como un `.docx` estándar que se abre en Microsoft Word sin problemas.  

Sin herramientas externas, sin trucos XML complicados—solo Java tipado y Aspose.Words.

---

## Requisitos previos

Antes de comenzar, asegúrate de tener:

1. **Java Development Kit (JDK) 8 o superior** – el código está dirigido a Java 8+.  
2. **Aspose.Words for Java** JAR (puedes obtener la última versión desde el repositorio Maven Central).  
3. Un IDE modesto (IntelliJ IDEA, Eclipse, o incluso un editor de texto simple).  

Si ya cuentas con eso, genial—¡vamos a empezar!

---

## Implementación paso a paso

A continuación dividimos el proceso en pasos manejables. Cada paso incluye un fragmento de código, una breve explicación y un consejo que quizás no encuentres en la documentación oficial.

### ## Crear documento de Word con formas usando Aspose.Words

Lo primero que necesitas es un archivo de Word vacío con el que trabajar. Aspose.Words lo hace en una sola línea.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:**  
`Document` es el contenedor de todo—texto, tablas, imágenes y formas. `DocumentBuilder` es el asistente amigable que te permite añadir contenido sin pelearte con objetos de bajo nivel. Piensa en él como una pluma que escribe directamente sobre la página.

> **Consejo profesional:** Si planeas comenzar con una plantilla (p. ej., el membrete de la empresa), reemplaza `new Document()` por `new Document("template.docx")`.

### ## Insertar forma rectangular y otras formas

Ahora añadiremos un rectángulo azul y una elipse verde. El rectángulo muestra la palabra clave **insert rectangle shape**, mientras que la elipse demuestra que puedes mezclar tipos de forma libremente.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**¿Qué ocurre bajo el capó?**  
Cada llamada a `insertShape` crea un objeto `Shape` y lo agrega automáticamente al párrafo actual. Los métodos `setLeft`/`setTop` posicionan la forma respecto a los márgenes de la página, medidos en puntos (1 pt = 1/72 in). Ajustando estos números puedes colocar las formas donde desees.

> **Pregunta frecuente:** *¿Puedo añadir una imagen en lugar de un color sólido?*  
> Por supuesto—simplemente reemplaza el color de relleno por una imagen usando `shape.getFill().setImage("path/to/image.png")`.

### ## Agrupar formas en Word para manipularlas fácilmente

Tener dos objetos separados está bien, pero a menudo quieres moverlos juntos. Ahí es donde **group shapes in word** brilla.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**¿Por qué agrupar?**  
Cuando las formas se agrupan, cualquier transformación—mover, rotar, redimensionar—se aplica a toda la colección. Esto replica el comportamiento que obtienes al seleccionar manualmente varias formas en la UI de Word y pulsar *Group*. También simplifica el código posterior porque solo necesitas ajustar un objeto en lugar de muchos.

> **Caso límite:** Si más adelante necesitas desagrupar, llama a `group.getParentNode().removeChild(group)` y vuelve a insertar los hijos individualmente.

### ## Guardar documento como DOCX y verificar la salida

Finalmente, persistimos el archivo. Este paso cumple con el requisito **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Qué esperar:**  
Abre el `GroupShapeExample.docx` generado en Microsoft Word. Verás un rectángulo azul y una elipse verde, agrupados ordenadamente. Arrastra el grupo—ambas formas se moverán juntas, tal como ocurre en la UI.

> **Consejo:** Usa `SaveFormat.PDF` si necesitas una versión PDF; el mismo código funciona sin cambios.

### ## Ejemplo completo y errores comunes

A continuación tienes la clase Java completa, lista para ejecutar. Copia‑pega en tu proyecto, ajusta la carpeta de salida y pulsa *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **`NullPointerException` en `builder`** | Olvidar instanciar `DocumentBuilder` después de crear `Document`. | Asegúrate de ejecutar `new DocumentBuilder(doc)` antes de insertar cualquier forma. |
| **Las formas aparecen fuera de la página** | Usar valores en píxeles en lugar de puntos, o no considerar los márgenes. | Recuerda que Aspose.Words espera puntos; 72 pt = 1 in. Ajusta `setLeft`/`setTop` en consecuencia. |
| **El grupo desaparece después de guardar** | Añadir formas al grupo *después* de haber guardado el grupo. | Siempre agrupa antes de llamar a `doc.save()`. |
| **Archivo no encontrado al guardar** | El directorio de salida no existe. | Crea el directorio programáticamente (`new File("output").mkdirs();`) o usa una ruta existente. |

---

## Conclusión

Acabamos de **crear un documento de Word** desde cero, **añadir formas a Word**, **insertar una forma rectangular**, **agrupar formas en Word**, y finalmente **guardar el documento como docx**—todo con unas pocas líneas de Java. El poder de Aspose.Words reside en su modelo de objetos claro; puedes tratar un archivo de Word como un lienzo, pintar sobre él con formas y luego exportarlo donde lo necesites.

¿Te sientes aventurero? Prueba a sustituir el rectángulo por una estrella, añade texto dentro de las formas usando `Shape.getTextBox()`, o experimenta con rotación (`shape.setRotationAngle(45)`). La API es rica y las posibilidades son prácticamente infinitas.

¿Tienes preguntas sobre escenarios más avanzados—como enlazar formas a marcadores o exportar a PDF con fuentes incrustadas? Deja un comentario abajo y profundizaremos juntos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento de Word Java – Añadir forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crear forma de grupo en documento de Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}