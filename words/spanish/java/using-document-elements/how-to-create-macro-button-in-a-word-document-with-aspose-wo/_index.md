---
category: general
date: 2026-11-22
description: Crear botón de macro en un documento de Word usando Java. Aprende a insertar
  un botón de comando, establecer el texto del botón y vincular la macro al botón
  para documentos interactivos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: es
lastmod: 2026-11-22
og_description: Crear un botón de macro en un documento de Word usando Java. Este
  tutorial muestra cómo insertar un botón de comando, establecer el texto del botón
  y vincular la macro al botón para una interactividad completa.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Crear un botón macro en un documento de Word con Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Cómo crear un botón de macro en un documento Word con Aspose.Words para Java
url: /es/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un botón macro en un documento Word con Aspose.Words para Java

Si necesitas **crear un botón macro** en un archivo Word, esta guía te muestra paso a paso los pasos exactos requeridos. Aprenderás cómo **insertar un botón de comando**, **establecer el texto del botón** y **vincular una macro al botón** para que el documento sea totalmente interactivo.

Los desarrolladores a menudo incrustan controles OLE para activar macros VBA desde dentro de un documento. Este tutorial cubre el flujo de trabajo completo, desde la configuración del proyecto hasta un ejemplo Java ejecutable que agrega un **botón interactivo** a un archivo .docx. No se necesitan scripts externos; todo se ejecuta dentro del proceso Java.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* JDK 17 o posterior instalado.
* Maven 3.8+ (o Gradle) para la gestión de dependencias.
* Aspose.Words para Java 23.9 o más reciente – la biblioteca proporciona las API `DocumentBuilder` y de control OLE.
* Familiaridad básica con Java y macros VBA.

Si falta alguno de estos elementos, instálalo primero; el resto del tutorial asume que están disponibles.

## Cómo crear un botón macro con Aspose.Words para Java

El núcleo de la solución consta de cuatro acciones:

1. **Insertar un botón de comando** control OLE en el documento.
2. **Establecer el texto del botón** (caption) que ve el usuario.
3. **Vincular la macro al botón** para que al hacer clic se ejecute la rutina VBA deseada.
4. **Guardar el documento** con la macro incrustada.

Cada acción se explica en su propia sección a continuación.

### Paso 1: Insertar botón de comando en el documento

`DocumentBuilder.insertForms2OleControl` crea un control OLE del tipo especificado. La constante `Forms2OleControlType.COMMAND_BUTTON` indica a Aspose.Words que genere un botón de comando que pueda alojar una macro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Por qué es importante:** El control OLE actúa como contenedor para la macro. Sin insertarlo, no hay un elemento visual para que el usuario haga clic.

### Paso 2: Establecer el texto del botón (caption)

El caption es la etiqueta visible en el botón. Usa `setCaption` para definir lo que el usuario ve.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Por qué es importante:** Un texto claro en el botón mejora la usabilidad. El método `setCaption` actualiza la propiedad `Caption` del control OLE, que Word muestra como la etiqueta del botón.

### Paso 3: Vincular la macro al botón

Una macro se identifica por su nombre, por ejemplo `MyMacro`. El método `setOnClick` almacena este nombre en el controlador de eventos `OnClick` del botón.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Por qué es importante:** Vincular una macro crea el comportamiento interactivo. Cuando el usuario hace clic en el botón en Word, se ejecuta la rutina VBA asociada.

### Paso 4: Añadir botón interactivo a un documento Word

Después de configurar el control OLE, puede que desees posicionarlo, cambiar su tamaño o añadir texto alrededor. `DocumentBuilder` sigue operando sobre el documento, por lo que puedes insertar párrafos antes o después del botón.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Por qué es importante:** Guardar como `.docm` preserva el código de la macro. Si lo guardas como `.docx`, la referencia a la macro se pierde.

## Ejemplo completo ejecutable

A continuación se muestra el programa Java completo, con importaciones, manejo de excepciones y comentarios que explican cada paso. Copia el código en un proyecto Maven con la dependencia de Aspose.Words y ejecútalo.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Resultado esperado

Al ejecutar el programa se genera `MacroButtonDemo.docm`. Al abrir el archivo en Microsoft Word se muestra:

* Un párrafo que dice *“Press the button to execute the macro:”*.
* Un botón etiquetado **Run Report** justo debajo del párrafo.
* Cuando haces clic en el botón, Word intenta ejecutar la macro `MyMacro`. (Debes añadir el código VBA real al documento manualmente o mediante otro paso de automatización.)

Si la macro no existe, Word muestra una advertencia de seguridad, que es el comportamiento estándar de los documentos habilitados para macros.

## Variaciones comunes y casos límite

| Escenario | Cómo adaptar el código |
|----------|-----------------------|
| **Caption de botón diferente** | Cambia la cadena pasada a `setCaption`. |
| **Múltiples botones** | Llama a `insertForms2OleControl` repetidamente, cada uno con su propio `setCaption` y `setOnClick`. |
| **Nombres de macro personalizados** | Reemplaza `"MyMacro"` por cualquier nombre de procedimiento VBA válido, por ejemplo, `"ExportToExcel"`. |
| **Restricciones de tamaño del botón** | Ajusta los valores de `setWidth` y `setHeight`; Word respeta los puntos que proporciones. |
| **Incrustar la macro programáticamente** | Usa `Document.getBuiltInDocumentProperties().add("Macros", …)` o un paso separado de inyección VBA; Aspose.Words no escribe código VBA por sí mismo. |

**Consejo profesional:** Siempre prueba el `.docm` generado en una máquina con la seguridad de macros configurada en *Enable all macros* para desarrollo. En producción, firma la macro con un certificado de confianza para evitar avisos de seguridad.

## Lista de verificación de solución de problemas

* **El botón no aparece** – Verifica que el documento se guarde como `.docm` y se abra en una versión de Word que soporte controles OLE.
* **La macro no se ejecuta** – Asegúrate de que el nombre de la macro coincida exactamente, incluidas mayúsculas y minúsculas, y que la macro exista en el proyecto VBA del documento.
* **El caption del botón se trunca** – Incrementa el ancho del botón usando `setWidth` para acomodar texto más largo.
* **Desplazamiento inesperado del diseño** – Usa `builder.moveTo` para posicionar el cursor con precisión antes de insertar el control.

## Conclusión

Ahora sabes cómo **crear un botón macro** en un documento Word usando Java, **insertar un botón de comando**, **establecer el texto del botón** y **vincular una macro al botón** para lograr plena interactividad. El ejemplo completo muestra cada llamada API requerida, explica por qué cada paso es importante y brinda orientación para variaciones comunes.

A continuación, podrías explorar:

* **Agregar un botón interactivo** a plantillas existentes en lugar de crear un documento nuevo.
* **Inyectar código VBA programáticamente** usando el Open XML SDK o una herramienta de automatización secundaria.
* **Combinar varios controles OLE** (casillas de verificación, listas) para construir formularios ricos.

¡Experimenta con diferentes captions, nombres de macro y tamaños de botón para adaptarlos a tu caso de uso específico! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}