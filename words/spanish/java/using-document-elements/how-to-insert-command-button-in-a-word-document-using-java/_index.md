---
category: general
date: 2026-08-23
description: Aprende cómo insertar un botón de comando en un documento de Word usando
  Java y Aspose.Words. Esta guía muestra cómo agregar un control de formulario, establecer
  el nombre del botón e incrustar un botón ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: es
lastmod: 2026-08-23
og_description: Insertar botón de comando en un documento Word usando Java. Sigue
  esta guía para agregar control de formulario, establecer el nombre del botón e incrustar
  un botón ActiveX con Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Insertar botón de comando en Word con Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Cómo insertar un botón de comando en un documento de Word usando Java
url: /es/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar un botón de comando en un documento Word usando Java

Si necesita **insert command button** en un archivo Word, este tutorial le muestra una solución completa con Aspose.Words for Java. Verá cómo agregar un control de formulario, configurar su título y establecer el nombre del botón sin salir de su IDE.

La guía cubre todo lo que necesita para crear un `.docx` que contiene un botón ActiveX listo para usar en Microsoft Word. No se requiere ninguna herramienta adicional, y el ejemplo se ejecuta en Java 8+.

## Lo que aprenderá

* Cómo agregar un control de formulario de tipo **CommandButton** a un documento Word.  
* Los pasos exactos para **set button name** y **add activex button** propiedades.  
* Cómo guardar el documento para que el botón aparezca correctamente al abrirse en Word.  

Debe contar con un entorno básico de desarrollo Java y un proyecto Maven o Gradle que pueda importar la biblioteca Aspose.Words.

## Prerequisitos

| Requisito | Razón |
|-------------|--------|
| Java 8 o superior | Aspose.Words for Java se ejecuta en Java 8+. |
| Herramienta de compilación Maven o Gradle | Simplifica la adición de la dependencia Aspose.Words. |
| Licencia de Aspose.Words for Java (o prueba gratuita) | Requerida para el conjunto completo de funciones; la API funciona en modo de evaluación. |
| Un IDE como IntelliJ IDEA o Eclipse | Facilita la edición y ejecución del ejemplo. |

## Paso 1: Agregar Aspose.Words a su proyecto

Si usa Maven, agregue la siguiente dependencia a `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Para Gradle, coloque esta línea en `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Una vez que la dependencia se resuelva, puede importar las clases de la biblioteca en su archivo fuente Java.

## Paso 2: Insertar botón de comando – el código principal

Cree una nueva clase Java llamada `InsertCommandButtonDemo`. El código a continuación realiza las cuatro acciones necesarias para **insert command button**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Por qué cada línea es importante

* **Document & DocumentBuilder** – Proporcionan la representación en memoria de un archivo Word y la API para modificar su contenido.  
* **insertForms2OleControl** – Este método **adds form control** de tipo `COMMAND_BUTTON`. El objeto `Forms2OleControl` devuelto representa el control ActiveX.  
* **setName** – Asigna un identificador programático (`btnSubmit`). Las macros de Word o VBA pueden referenciar este nombre más adelante.  
* **setCaption** – Define el texto que el usuario ve en el botón, respondiendo a la pregunta “cómo agregar un botón”.  
* **save** – Escribe el `.docx` en disco, preservando el botón ActiveX incrustado.  

Ejecutar el programa crea `CommandButtonDemo.docx` en el directorio de trabajo. Abrir el archivo en Microsoft Word muestra un botón etiquetado **Submit** que puede pulsar (mostrará un cuadro de diálogo ActiveX predeterminado en modo de evaluación).

## Paso 3: Verificar el botón insertado en Word

1. Abra `CommandButtonDemo.docx` con Microsoft Word (2016 o posterior).  
2. El botón **Submit** aparece donde el cursor estaba posicionado durante la inserción.  
3. Haga clic con el botón derecho del ratón sobre el botón y elija **Properties** para ver que el campo **Name** contiene `btnSubmit`.  

Si el botón no aparece, asegúrese de que los **ActiveX controls** estén habilitados en la configuración del Trust Center de Word.

## Paso 4: Personalizar el botón (opcional)

Puede personalizar aún más el botón ajustando su tamaño, posición o agregando una macro VBA. La clase `Forms2OleControl` expone propiedades adicionales como `setWidth`, `setHeight` y `setLeft`. A continuación se muestra un ejemplo que hace el botón más grande:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Estas líneas pueden colocarse después de la llamada a `setCaption`. Demuestran la personalización **add activex button** más allá de la inserción básica.

## Problemas comunes y cómo evitarlos

| Síntoma | Causa | Solución |
|---------|-------|----------|
| El botón no aparece en Word | El documento se guardó antes de que se agregara el control | Asegúrese de que `insertForms2OleControl` se llame antes de `doc.save`. |
| El título del botón está vacío | No se llamó a `setCaption` o se llamó con una cadena vacía | Proporcione una cadena no vacía, por ejemplo, `"Submit"`. |
| VBA no puede encontrar el botón | Incongruencia entre el nombre en el código VBA y el valor de `setName` | Mantenga el nombre consistente; use `setName("btnSubmit")` y haga referencia a `btnSubmit` en VBA. |
| Advertencia de seguridad al abrir el archivo | La seguridad de macros de Word bloquea los controles ActiveX | Ajuste Trust Center > Macro Settings, o firme el documento con un certificado de confianza. |

## Ejemplo completo y ejecutable

A continuación se muestra el archivo fuente completo, listo para copiar y pegar en su IDE. Incluye las declaraciones de importación, el manejo de excepciones y un bloque de comentarios que explica cada paso importante.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Resultado esperado:** Después de ejecutar el programa, `CommandButtonDemo.docx` contiene un único botón **Submit**. Al abrir el archivo en Word se muestra el botón exactamente donde estaba el cursor del `DocumentBuilder`.

## Próximos pasos

* **Add more form controls** – Use `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, or `TEXT_BOX` para crear formularios Word completos.  
* **Combine with mail merge** – Inserte botones en un documento de combinación de correspondencia para crear formularios interactivos personalizados.  
* **Attach VBA macros** – Incruste programáticamente VBA que reaccione al evento `Click` del botón para automatización avanzada.  

Estos temas amplían naturalmente la técnica **add form control** que acaba de dominar.

### Recapitulación

Ahora sabe cómo **insert command button** en un documento Word usando Java, cómo **add form control**, cómo **set button name**, y cómo personalizar **add activex button**. El ejemplo completo funciona listo para usar, y puede adaptarlo a cualquier flujo de generación de documentos. ¡Feliz codificación!

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insertar campo de formulario Combo Box en documento Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insertar campo de formulario Check Box en documento Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}