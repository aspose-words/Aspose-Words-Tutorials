---
category: general
date: 2026-06-20
description: Guardar documento Word con Aspose.Words en Java añadiendo una forma rectangular
  y aplicando una sombra. Aprende a insertar la forma paso a paso.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: es
og_description: Guarda un documento Word con Aspose.Words Java. Esta guía muestra
  cómo agregar una forma rectangular, aplicar una sombra e insertarla en un párrafo.
og_title: Guardar documento Word – Añadir forma rectangular y sombra en Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Guardar documento de Word – Añadir forma de rectángulo y sombra en Java
url: /es/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Guardar documento Word – Añadir forma rectangular y sombra en Java

¿Alguna vez te has preguntado cómo **guardar un documento Word** después de haber personalizado su diseño? No estás solo—la mayoría de los desarrolladores se topan con ese problema cuando necesitan enriquecer programáticamente un archivo DOCX. La buena noticia es que con Aspose.Words for Java puedes **guardar un documento Word**, insertar una forma rectangular justo donde la deseas, e incluso darle a esa forma una sombra sutil.

En este tutorial recorreremos todo el proceso: cargar un archivo existente, **añadir una forma rectangular**, configurar su **sombra**, insertar la forma en el primer párrafo y, finalmente, **guardar el documento Word**. Al final tendrás un programa Java ejecutable que genera un archivo `shadow.docx` pulido—sin necesidad de ajustes manuales.

> **Lo que necesitarás**  
> * Java 17 (o cualquier JDK reciente)  
> * Biblioteca Aspose.Words for Java (Maven/Gradle o el JAR)  
> * Un archivo DOCX de entrada (`input.docx`) en una carpeta conocida  

Si ya tienes esos elementos, vamos a sumergirnos.

---

## Guardar documento Word – Ejemplo Java completo

A continuación tienes el código fuente completo, listo para ejecutar. Cópialo en tu IDE, ajusta las rutas y pulsa **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Resultado esperado:** Después de ejecutar el programa, abre `shadow.docx`. Verás el contenido original más un rectángulo negro de 100 × 50 pt con una sombra suave justo al inicio del primer párrafo.

---

## Añadir forma rectangular a un documento Word

¿Por qué usar una forma rectangular? Piensa en ella como un ancla visual—perfecta para llamadas de atención, marcadores de posición o gráficos simples. En Aspose.Words la clase `Shape` abstrae todos los objetos de dibujo, y `ShapeType.RECTANGLE` te brinda una caja limpia sin complicaciones adicionales.

**Puntos clave al añadir una forma rectangular**

- **Las unidades son puntos** (1 pt = 1/72 in). Ajusta `setWidth`/`setHeight` para que encajen en tu diseño.  
- La forma vive dentro del árbol de nodos del documento, por lo que puedes insertarla donde sea permitido un `Paragraph` o `Run`.  
- Puedes estilizar el rectángulo (relleno, color de línea, etc.) antes de aplicar una sombra.

> **Consejo profesional:** Si necesitas un relleno transparente, llama a `rectangle.getFill().setTransparent(true);`.

---

## Aplicar sombra a la forma

Las sombras añaden profundidad. El objeto `Shadow` asociado a una `Shape` expone propiedades que se corresponden directamente con las opciones de la interfaz de Word.

| Propiedad | Qué hace | Valor típico |
|-----------|----------|--------------|
| `setVisible(true)` | Activa la sombra | `true` |
| `setColor(Color.BLACK)` | Color de la sombra | `Color.BLACK` |
| `setBlurRadius(5.0)` | Suavidad de los bordes | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Desplazamiento horizontal/vertical | `4.0` each |
| `setTransparency(0.3)` | Opacidad (0 = opaco, 1 = invisible) | `0.3` |

Cuando te preguntas **cómo aplicar sombra a una forma**, la respuesta es simplemente ajustar esas seis propiedades. Puedes experimentar: desplazamientos mayores crean una sensación de “elevación”, mientras que un radio de desenfoque más alto produce un aspecto más difuso.

> **Error común:** Olvidar `setVisible(true)` deja la forma sin sombra aunque configures otras propiedades.

---

## Cómo insertar la forma en un párrafo

Insertar una forma no es magia; es simplemente manipulación de nodos. El método `appendChild` coloca la forma al final de los nodos hijos del párrafo. Si necesitas la forma antes del texto, usa `insertBefore` en su lugar.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Ese pequeño cambio responde **cómo insertar la forma** justo donde la necesitas—antes de cualquier `Run` existente, después de un encabezado o incluso dentro de una celda de tabla (solo recupera el nodo `Cell` apropiado primero).

---

## Ejecutar el código y verificar la salida

1. **Compilar** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Ejecutar** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Abrir** `shadow.docx` en Microsoft Word o LibreOffice. Deberías ver el rectángulo con una sombra negra suave anclado al inicio del primer párrafo.

Si la forma no aparece, verifica:

- La ruta del archivo de entrada es correcta.  
- Estás usando una versión reciente de Aspose.Words (la API cambió ligeramente antes de la 20.12).  
- El documento realmente tiene al menos un párrafo (de lo contrario `getParagraphs().get(0)` lanza una `IndexOutOfBoundsException`).

---

## Preguntas frecuentes (FAQ)

**P: ¿Puedo añadir la forma a una página específica?**  
R: Sí. Recupera la `Section` o `PageSetup` objetivo e inserta la forma en un párrafo ubicado en esa página.

**P: ¿Esto funciona con archivos .doc?**  
R: Absolutamente. Aspose.Words abstrae el formato, por lo que el mismo código **guarda un documento Word** tanto si es `.doc` como `.docx`.

**P: ¿Qué pasa si necesito una forma diferente, como una elipse?**  
R: Sustituye `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`. Todas las propiedades de sombra permanecen iguales.

---

## Conclusión

Ahora sabes cómo **guardar un documento Word** mientras **añades una forma rectangular**, **aplicas una sombra** y **insertas la forma** en el primer párrafo—todo con unas pocas líneas limpias de Java. Este patrón escala: cambia el tipo de forma, ajusta la configuración de sombra o coloca la forma en tablas y encabezados. Las posibilidades son tan amplias como tus necesidades de automatización de documentos.

¿Listo para el siguiente desafío? Prueba a superponer múltiples formas, añadir texto dentro del rectángulo o generar un informe completo con gráficos y marcas de agua. Cada una de esas tareas se basa en los mismos fundamentos cubiertos aquí—así que ya vas un paso adelante.

¡Feliz codificación, y que tu automatización de Word esté libre de sombras y errores!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cómo guardar documento como PDF con Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Cómo guardar Word como PCL con Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}