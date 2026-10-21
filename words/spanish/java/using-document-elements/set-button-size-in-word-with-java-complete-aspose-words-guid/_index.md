---
category: general
date: 2026-07-16
description: Establezca el tamaño del botón programáticamente en un documento de Word
  usando Aspose.Words para Java. Aprenda cómo insertar un botón ActiveX, establecer
  la ubicación del botón y más.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: es
lastmod: 2026-07-16
og_description: Establecer el tamaño del botón en un documento de Word usando Java.
  Esta guía paso a paso muestra cómo insertar un botón ActiveX, establecer la ubicación
  del botón y agregar el botón programáticamente.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Establecer el tamaño del botón en Word con Java – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Establecer el tamaño del botón en Word con Java – Guía completa de Aspose.Words
url: /es/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer el tamaño del botón en Word con Java – Guía completa de Aspose.Words

¿Alguna vez te has preguntado cómo **establecer el tamaño del botón** dentro de un archivo Word sin abrir la interfaz de usuario? No eres el único. Cuando necesitas generar un documento con formulario completado al vuelo —por ejemplo, un paquete de incorporación con un botón “Enviar”— hacerlo programáticamente ahorra horas de trabajo manual.

En este tutorial recorreremos paso a paso los pasos exactos para **insertar un botón ActiveX**, ajustar sus dimensiones, posicionarlo correctamente y, finalmente, guardar el archivo. Al final podrás **agregar botones** de forma programática a cualquier documento Word usando Aspose.Words para Java.

## Requisitos previos – Lo que necesitas antes de comenzar

- **Java Development Kit (JDK) 8+** – el código funciona con cualquier JDK reciente.  
- Biblioteca **Aspose.Words for Java** (descarga el JAR más reciente desde el sitio oficial).  
- Un **IDE** de tu elección—IntelliJ IDEA, Eclipse, o incluso un editor de texto simple sirve.  
- Familiaridad básica con la sintaxis de Java; no se requiere un conocimiento profundo de la automatización de Word.

> *Consejo profesional:* Mantén el JAR de Aspose.Words en el classpath de tu proyecto, de lo contrario obtendrás `ClassNotFoundException` en el momento en que intentes importar `com.aspose.words.*`.

## Paso 1: Crear un nuevo documento Word

Lo primero que hacemos es crear un documento en blanco y un `DocumentBuilder`. Piensa en el builder como un lápiz que nos permite dibujar cualquier cosa dentro del archivo.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por qué es importante:** El objeto `Document` representa todo el archivo .docx, mientras que el `DocumentBuilder` es la herramienta que nos permite insertar párrafos, tablas y—sí—controles ActiveX.

## Paso 2: Insertar botón ActiveX – El momento “Insertar botón ActiveX”

Ahora insertamos realmente **un botón activex** en el documento. Aspose.Words expone un método conveniente `insertForms2OleControl` que devuelve un objeto `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *¿Qué ocurre bajo el capó?* `Forms2OleControlType.COMMAND_BUTTON` le indica a Word que queremos un CommandButton clásico, el mismo tipo que arrastrarías desde la pestaña Desarrollador en la UI.

## Paso 3: Establecer el tamaño y la ubicación del botón – La lógica central “Set Button Size”

Aquí es donde brilla la palabra clave principal. **Estableceremos el tamaño del botón** y también **estableceremos la ubicación del botón** para que el control aparezca exactamente donde lo queremos en la página.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Por qué debes preocuparte:** Los puntos son la unidad de medida nativa en Word (1 punto = 1/72 de pulgada). Al ajustar `setLeft`, `setTop`, `setWidth` y `setHeight` obtienes un control pixel‑perfecto—no más “se ve bien en mi pantalla pero no en la impresora”.

> *Trampa común:* Olvidar establecer el ancho o la altura dejará el botón con el tamaño predeterminado, que puede ser demasiado pequeño para hacer clic. Siempre especifica ambos.

## Paso 4: Guardar el documento – “Crear botón en documento Word” completado

Finalmente, escribimos el archivo en disco. El nombre sugiere que estamos **creando un botón en un documento Word** dentro de un .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Al abrir `CommandButtonDemo.docx` en Microsoft Word, verás un botón **Submit** colocado a 100 pt del borde izquierdo y 150 pt del borde superior, con un tamaño de 80 × 30 pt. Hacer clic en él en la UI activará el comportamiento predeterminado de ActiveX (que luego puedes conectar con VBA si lo deseas).

### Captura de pantalla del resultado esperado

![Documento Word que muestra el botón insertado con el tamaño de botón establecido](https://example.com/images/set-button-size.png "Captura de pantalla de un archivo Word donde el tamaño del botón se ha establecido usando Aspose.Words for Java")

*Texto alternativo:* establecer el tamaño del botón en un documento Word usando Java

## Paso 5 (Opcional): Añadir más controles o dar estilo al botón

Si necesitas **agregar botones** de forma programática más allá de un único botón Submit, simplemente repite el bloque de inserción con nuevos nombres y leyendas. También puedes ajustar la fuente, el color de fondo o incluso enlazar macros VBA más adelante.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Consejo:* Mantén todas las dimensiones de los botones consistentes para lograr un aspecto profesional. Una forma rápida es almacenar ancho/alto en constantes.

## Preguntas frecuentes y casos especiales

### “¿Puedo establecer el tamaño del botón usando centímetros en lugar de puntos?”
La API de Word solo acepta puntos, pero puedes convertir centímetros a puntos (`points = cm * 28.3465`). Escribe un pequeño método auxiliar si prefieres unidades métricas.

### “¿Qué pasa si necesito que el botón aparezca en una página específica?”
Después de insertar el botón, puedes mover el cursor a una página concreta usando `builder.moveToPage(pageNumber)`. Inserta el control justo después del movimiento y luego establece su ubicación como se mostró arriba.

### “¿Esto funciona con archivos .doc (Word 97‑2003)?”
Sí—Aspose.Words maneja automáticamente los formatos antiguos. Simplemente cambia la extensión del archivo en `doc.save("Demo.doc")`.

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar‑pegar en una clase Java y ejecutar de inmediato (suponiendo que el JAR de Aspose.Words está en el classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Ejecuta el programa, abre el `CommandButtonDemo.docx` generado y verás dos botones con tamaños bien definidos listos para interactuar.

## Conclusión – Has dominado el establecimiento del tamaño del botón en Word

Acabamos de recorrer una solución completa, de extremo a extremo, para **establecer el tamaño del botón** y **establecer la ubicación del botón** usando Aspose.Words para Java. Siguiendo los pasos puedes **insertar botones activex**, **agregar botones** de forma programática y, en última instancia, **crear elementos de botón en documentos Word** que se comporten exactamente como necesitas.

¿Qué sigue? Prueba incrustar el botón dentro de una celda de tabla, o adjunta una macro VBA que valide los campos del formulario antes de enviarlo. El mismo patrón funciona para otros controles ActiveX como casillas de verificación o cuadros combinados—solo cambia `Forms2OleControlType.COMMAND_BUTTON` por el valor de enumeración correspondiente.

Si encuentras algún obstáculo, deja un comentario abajo. ¡Feliz codificación y disfruta del poder de la creación automatizada de documentos Word!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo establecer LoadOptions en Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cómo eliminar pies de página de documentos Word usando Aspose.Words para Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Guía completa para el procesamiento de documentos Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}