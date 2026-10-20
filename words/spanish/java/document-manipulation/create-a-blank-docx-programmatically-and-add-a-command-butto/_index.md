---
category: general
date: 2026-10-20
description: Crea un DOCX en blanco de forma programática e inserta un botón de comando
  usando Java. Aprende el código completo para crear un documento de Word, guardarlo
  con el botón y establecer el texto del botón de comando.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: es
lastmod: 2026-10-20
og_description: Crea un DOCX en blanco de forma programática e inserta un botón de
  comando. Sigue esta guía paso a paso en Java para guardar Word con el botón y establecer
  el texto del botón de comando.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Crear un DOCX en blanco programáticamente – agregar un botón de comando
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Crear un DOCX en blanco programáticamente y añadir un botón de comando
url: /es/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un DOCX en blanco programáticamente y agregar un botón de comando

Si necesitas **crear un DOCX en blanco programáticamente**, este tutorial te muestra cómo incrustar un botón de comando directamente en el archivo. Obtendrás el *código completo para crear un documento de Word* que guarda un documento de Word con un botón, te permite **establecer el texto del botón de comando**, y funciona con la última biblioteca Aspose.Words for Java.

Incrustar controles interactivos en un archivo DOCX es útil cuando deseas distribuir plantillas que activan macros, lanzan programas externos, o simplemente guían a los usuarios con un botón clicable “Click Me”. Los pasos a continuación cubren todo, desde la inicialización de un documento en blanco hasta la persistencia del archivo final en disco.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o superior instalado.
* Maven (o tu herramienta de compilación preferida) para gestionar dependencias.
* Aspose.Words for Java 23.9 o posterior. Añade la dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Un IDE como IntelliJ IDEA o VS Code (cualquier editor que soporte Java funciona).

## Crear un DOCX en blanco programáticamente – paso a paso

Las siguientes secciones dividen el proceso en pasos claros y numerados. Cada paso explica **por qué** es necesario, no solo **qué** escribir.

### Paso 1: Inicializar un nuevo documento en blanco

Un documento en blanco es el lienzo donde colocarás el botón de comando. Aspose.Words proporciona la clase `Document` para este propósito.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Por qué es importante*: Comenzar con un `Document` vacío garantiza que no haya formato oculto ni controles existentes que interfieran con el botón que agregarás más adelante.

### Paso 2: Configurar un `DocumentBuilder`

`DocumentBuilder` es un asistente que te permite insertar contenido, incluidos controles OLE, sin tener que manejar la manipulación de nodos de bajo nivel.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante*: El builder mantiene la posición actual del cursor, por lo que el botón se colocará exactamente donde lo indiques.

### Paso 3: Insertar un botón de comando OLE

Word trata los controles interactivos como objetos OLE (Object Linking and Embedding). Aspose.Words expone `Forms2OleControl` para esto.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Por qué es importante*: Insertar el control crea un marcador de posición que puedes configurar más tarde (tipo, texto, posición).

### Paso 4: Configurar el botón – tipo, texto y ubicación

Debes definir el tipo del control (`COMMANDBUTTON`), establecer un texto visible para el usuario y colocarlo en la página.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Por qué es importante*:
* **Type** indica a Word que el control se comporta como un botón clicable.
* **Caption** es el texto que ve el usuario; cambiarlo es cómo **estableces el texto del botón de comando**.
* **Left** y **Top** controlan la ubicación exacta, lo cual es esencial cuando **add command button word** documentos que necesitan un diseño preciso.

### Paso 5: Guardar el documento con el botón incrustado

Finalmente, escribe el archivo en disco. El archivo resultante puede abrirse en Microsoft Word, donde el botón será completamente funcional.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Por qué es importante*: Este paso **guarda Word con botón** para que el control persista en diferentes máquinas. El archivo puede distribuirse como una plantilla o usarse en pipelines automáticos de generación de informes.

## Ejemplo completo funcional

Copia la clase completa a continuación en un archivo llamado `CommandButtonDemo.java`, ajusta `YOUR_DIRECTORY` a una ruta real y ejecútalo con `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Resultado esperado

Al abrir `CommandButton.docx` en Microsoft Word:

* El documento está completamente en blanco excepto por un botón etiquetado **Click Me**.
* Al hacer clic en el botón se mostrará el comportamiento predeterminado de Word (no hace nada a menos que se adjunte una macro), confirmando que el control OLE se incrustó correctamente.

## Preguntas comunes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo cambiar el tamaño del botón?** | Sí. Usa `commandButton.setWidth(double)` y `commandButton.setHeight(double)` para ajustar las dimensiones en puntos. |
| **¿Qué pasa si necesito una macro adjunta al botón?** | El botón en sí es solo un control OLE. Debes añadir una macro VBA al documento manualmente o mediante las utilidades `addMacro` de la API `Document` de Aspose.Words. |
| **¿Funcionará el botón en LibreOffice?** | LibreOffice soporta controles OLE limitados. El botón aparece, pero su comportamiento al hacer clic puede diferir. |
| **¿Cómo añadir varios botones?** | Repite los Pasos 3‑4 con una nueva instancia de `Forms2OleControl`. Ajusta `setLeft`/`setTop` para cada botón para evitar superposición. |
| **¿Es el código compatible con .NET?** | La misma lógica se aplica, pero usarías las clases de `Aspose.Words` para .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Consejos del campo

* **Consejo profesional:** Usa `builder.moveToDocumentEnd()` antes de insertar el botón si deseas que esté al final del documento, sin importar el contenido previo.
* **Cuidado con:** Valores muy pequeños de `Left`/`Top` pueden colocar el botón fuera del área imprimible, haciéndolo invisible en la vista de diseño de Word.
* **Nota de rendimiento:** Insertar muchos controles OLE puede aumentar el tamaño del archivo. Si solo necesitas una pista visual, considera usar un `Shape` simple con un hipervínculo.

## Conclusión

Ahora sabes cómo **crear un DOCX en blanco programáticamente** e incrustar un botón de comando totalmente funcional usando Java. El tutorial cubrió todo el flujo de trabajo *create word document code*, demostró cómo **guardar Word con botón**, mostró la forma correcta de **add command button word** elementos, y explicó cómo **set command button caption**.

A partir de aquí puedes:

* Añadir más controles OLE (casillas de verificación, cuadros combinados) para formularios más ricos.
* Adjuntar macros VBA para que el botón realice acciones personalizadas.
* Combinar esta técnica con combinación de correspondencia de documentos para plantillas dinámicas e interactivas.

Siéntete libre de experimentar con estilos de botones, posiciones y controles adicionales para adaptarlos a los requisitos específicos de tu negocio. Feliz codificación

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word en blanco con un botón de comando – guía paso a paso](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Cómo insertar un botón ActiveX en Word – establecer texto del botón](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Crear documento Word en blanco con Java – Guía completa de Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}