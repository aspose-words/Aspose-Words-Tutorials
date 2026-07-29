---
category: general
date: 2026-07-29
description: 'tutorial de Java para establecer el tamaño del botón: aprende cómo insertar
  un botón de comando ActiveX en un documento Word usando Java y Aspose.Words, además
  del dimensionamiento y la creación de un documento en blanco.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: es
lastmod: 2026-07-29
og_description: La guía “set button size java” muestra cómo insertar un botón de comando
  ActiveX en un archivo Word usando Java, ajustar su tamaño y guardar el documento
  de forma programática.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Establecer tamaño del botón en Java – Añadir botón de comando ActiveX a
  Word con Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Establecer tamaño del botón Java – Insertar botón de comando ActiveX en Word
url: /es/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Insertar botón de comando ActiveX en Word

¿Alguna vez te has preguntado **how to set button size java** cuando automatizas documentos de Word? Tal vez estés construyendo una herramienta de informes que necesita un botón “Submit” clicable dentro del archivo .docx. En este tutorial recorreremos todo el proceso—crear un documento Word en blanco, insertar un botón de comando ActiveX y establecer explícitamente su ancho y alto—todo con Java y Aspose.Words.

También responderemos la persistente pregunta “how to insert activex” que surge para muchos desarrolladores. Al final tendrás un programa ejecutable que genera un archivo Word que contiene un botón de comando perfectamente dimensionado, listo para una mayor personalización.

---

## Lo que necesitarás

- **Java Development Kit (JDK) 8 o más reciente** – el código se compila con cualquier JDK reciente.
- **Aspose.Words for Java** (la última versión a partir de julio 2026). Obtén el JAR desde el [Aspose website](https://products.aspose.com/words/java) o mediante Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Un IDE o un editor de texto simple—IntelliJ IDEA, Eclipse o VS Code sirven.
- Una carpeta donde deseas que se guarde el **CommandButton.docx** generado.

Eso es todo. Sin bibliotecas adicionales de interop de Office, sin trucos COM, solo Java puro.

---

## Implementación paso a paso

Dividiremos la solución en cinco pasos lógicos. Cada paso tiene un encabezado H2 dedicado; uno de ellos contiene nuestra **palabra clave principal** para satisfacer el SEO.

### 1. Configurar el proyecto e importar Aspose.Words

Primero, crea un nuevo proyecto Maven (o Gradle) y agrega la dependencia de Aspose.Words mostrada arriba. Luego, importa las clases necesarias en tu archivo fuente Java:

```java
import com.aspose.words.*;
```

> **Consejo profesional:** Si estás usando un IDE, permite que auto‑importe las clases. Ahorras mucho tiempo de escritura y evitas errores tipográficos.

### 2. java create blank word Document

Ahora realmente **java create blank word** documento. Esta es la base sobre la que más adelante **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

### 3. Inicializar DocumentBuilder e insertar el control ActiveX

El `DocumentBuilder` es un asistente que nos permite añadir contenido, párrafos, tablas y, sí, controles ActiveX. Aquí es donde respondemos **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

> **Nota:** Si necesitas un tipo de botón diferente (p. ej., una casilla de verificación), reemplaza `Forms2OleControlType.COMMANDBUTTON` con el valor de enumeración apropiado.

### 4. How to Set Button Size Java – Ajustar ancho y alto

Ahora llega el corazón del tutorial: **how to set button size java**. El control expone varias propiedades de diseño—`Left`, `Top`, `Width` y `Height`. Configurarlas directamente controla la apariencia del botón en la página.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

¿Por qué estos números? En Word, un punto equivale a 1/72 de pulgada. Así que un ancho de `120` puntos se traduce a aproximadamente 1.67 pulgadas—suficiente para una etiqueta legible, pero sin ser abrumador. Ajusta los valores para que encajen en tu diseño; las mismas propiedades también responden a la consulta **how to set button** que puedas tener.

> **Nota:** Si necesitas un tipo de botón diferente (p. ej., una casilla de verificación), reemplaza `Forms2OleControlType.COMMANDBUTTON` con el valor de enumeración apropiado.

### 5. Guardar el documento

Finalmente, guarda el documento en disco:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Reemplaza `YOUR_DIRECTORY` con una ruta absoluta o relativa en tu máquina. Después de ejecutar el programa, abre el archivo generado en Microsoft Word. Verás un botón etiquetado “Click Me” posicionado a 100 pts desde la izquierda y 200 pts desde la parte superior, con el tamaño exacto que establecimos.

---

## Ejemplo completo y funcional

A continuación se muestra la clase Java completa, lista para ejecutarse. Copia‑pega el código en `CommandButtonActiveX.java`, ajusta la ruta de salida y pulsa **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Salida esperada:** Al abrir `CommandButton.docx` en Word se muestra una sola página con un botón clicable “Click Me” colocado aproximadamente a mitad de página. Las dimensiones del botón coinciden con los valores que estableciste, confirmando que **set button size java** funciona como se espera.

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si el botón no aparece en Word?

- **Verifica la versión de Word.** Los controles ActiveX requieren la versión de escritorio de Word; Word Online los elimina.
- **Asegúrate de que la licencia de Aspose.Words esté aplicada** (si utilizas una edición de pago). Una versión de evaluación sin licencia puede insertar una marca de agua pero aún muestra el control.

### ¿Puedo cambiar la fuente o el color del botón?

Sí. Después de insertar el control, puedes acceder a su objeto OLE subyacente y manipular las propiedades VBA. Es un tema más avanzado—consulta `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` para un título rojo, por ejemplo.

### ¿Cómo manejo el evento click del botón?

Los botones de comando ActiveX disparan un evento VBA `Click`. Para que el botón sea funcional, deberás incrustar una macro en el mismo documento. Aspose.Words puede agregar un módulo de macro mediante la API `Document.getMacros()`, pero el código de la macro debe escribirse en VBA.

### ¿Qué pasa con los diferentes tipos de botón?

Aspose.Words admite muchos valores de `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, etc. Cambia la constante del enum en la llamada `insertForms2OleControl` para experimentar.

---

## Consejos profesionales para código listo para producción

1. **Usa constantes para los valores de diseño** – facilita futuros ajustes.
2. **Envuelve la ruta de guardado en un objeto `Path`** para evitar separadores específicos de la plataforma.
3. **Descarta el Document** (o usa try‑with‑resources) si procesas muchos archivos en un bucle.
4. **Valida la carpeta de salida** antes de llamar a `save` para evitar `FileNotFoundException`.

---

## Conclusión

Acabas de aprender **set button size java** creando un archivo Word en blanco, insertando un botón de comando ActiveX y configurando sus dimensiones con precisión, todo con unas pocas líneas de código Java. Esto cubre lo esencial de **how to insert activex**, **how to set button**, **java create blank word** y **insert command button word** en un único ejemplo autónomo.

¿Próximos pasos? Intenta personalizar la etiqueta del botón, agregar una macro que responda a los clics, o incrustar varios controles en la misma página. También podrías explorar la conversión del .docx resultante a PDF con Aspose.Words, preservando el botón como una imagen estática.

Siéntete libre de experimentar, y si encuentras algún problema, deja un comentario abajo. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cómo cargar documentos Word con Aspose.Words Java: Guía completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Cómo guardar documento como PDF con Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}