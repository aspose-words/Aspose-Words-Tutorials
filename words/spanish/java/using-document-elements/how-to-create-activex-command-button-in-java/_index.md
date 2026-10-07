---
category: general
date: 2026-10-07
description: Crear un botón de comando ActiveX en Java y agregar programáticamente
  el botón de comando a documentos de Word. Aprender cómo establecer las posiciones
  superior izquierda del botón.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: es
lastmod: 2026-10-07
og_description: Crea un botón de comando ActiveX en Java para incrustar controles
  interactivos en tus documentos de Word. Aprende cómo agregar programáticamente el
  botón de comando, establecer su posición y personalizar su apariencia.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Crear botón de comando ActiveX en Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Cómo crear un botón de comando ActiveX en Java
url: /es/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un botón de comando ActiveX en Java

Si necesitas **crear un botón de comando ActiveX** en un documento Word usando Java, esta guía te muestra exactamente cómo. Verás un ejemplo completo y ejecutable que **agrega programáticamente un botón de comando**, lo posiciona con `setLeft` y `setTop`, y guarda el resultado como un archivo `.docx`.

Incorporar un botón interactivo te permite crear formularios, automatizar flujos de trabajo o recopilar la entrada del usuario directamente dentro de un archivo Word. Los pasos a continuación cubren todo, desde la configuración del proyecto hasta la verificación final, para que puedas copiar el código en tu propio proyecto sin perder ningún detalle.

## Requisitos previos

- JDK 17 o una versión más reciente instalada  
- Maven 3.8+ (o la herramienta de compilación que prefieras)  
- Aspose.Words for Java 23.9 o posterior – la biblioteca que proporciona `DocumentBuilder` y soporte para controles OLE  
- Familiaridad básica con la sintaxis de Java y conceptos de programación orientada a objetos  

Si utilizas Maven, agrega la dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Consejo profesional:** Usa la última versión de Aspose.Words para beneficiarte de correcciones de errores y nuevas funciones OLE.

## Paso 1: Crear un documento vacío nuevo y un DocumentBuilder

El primer paso para **crear un botón de comando ActiveX** es instanciar un `Document` vacío y un `DocumentBuilder`. El builder te brinda una API fluida para insertar contenido, incluidos los controles OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa el archivo Word en memoria, mientras que `DocumentBuilder` actúa como un cursor que te permite colocar elementos exactamente donde los necesitas.

## Paso 2: Insertar un control de botón de comando OLE

Los controles ActiveX se insertan como objetos OLE. Aspose.Words proporciona la clase `Forms2OleControl` para este propósito.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Cuando llamas a `insertForms2OleControl()`, Aspose crea automáticamente una forma de marcador de posición que alojará el botón ActiveX.

## Paso 3: Configurar las propiedades del botón

Ahora **agregas programáticamente el botón de comando** con detalles como su ProgID, título y tamaño. El ProgID más común para un botón de comando es `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Cómo establecer la posición izquierda y superior del botón

Posicionar el botón es donde la palabra clave secundaria **how to set button left top** se vuelve relevante. Los métodos `setLeft` y `setTop` aceptan valores medidos en puntos (1 punto = 1/72 pulgada).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Ajusta estos números para que se adapten a tu diseño. Por ejemplo, para alinear el botón con una celda de tabla, calcula las coordenadas de la celda y pásalas a `setLeft`/`setTop`.

## Paso 4: Guardar el documento

Finalmente, escribe el documento en disco. El archivo contendrá el botón ActiveX listo para interactuar cuando se abra en Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Ejecutar el método `main` produce `CommandButton.docx`. Abre el archivo en Word, habilita el contenido si se solicita, y verás un botón clicable etiquetado **Click Me** posicionado en las coordenadas que especificaste.

![Crear botón de comando ActiveX en Java](/images/activex-button-screenshot.png){.center width=600 alt="Captura de pantalla de crear botón de comando ActiveX en Java que muestra el botón dentro del documento Word"}

## Variaciones comunes y casos límite

### Añadir varios botones

Si necesitas varios botones, repite **Paso 2** y **Paso 3** para cada control. Recuerda ajustar `setLeft` y `setTop` para que los botones no se superpongan.

### Cambiar el comportamiento del botón

Los botones ActiveX pueden ejecutar macros VBA al hacer clic. Para adjuntar una macro, establece la propiedad `setOnAction` con el nombre de la macro:

```java
commandButton.setOnAction("MyMacro");
```

Asegúrate de que el documento de destino contenga el módulo VBA correspondiente; de lo contrario, Word mostrará un error.

### Notas de compatibilidad

- El botón funciona solo en versiones de escritorio de Word que admiten ActiveX (p. ej., Word para Windows). Aparecerá como una imagen estática en Word para Mac o editores en línea.  
- Si apuntas a un entorno mixto, considera usar un **control de contenido** (`RichTextContentControl`) en lugar de un control ActiveX.

## Código fuente completo para referencia

A continuación se muestra el ejemplo completo y autónomo que puedes copiar en un nuevo proyecto Maven y ejecutar de inmediato.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Salida esperada:** Después de la ejecución, encontrarás `CommandButton.docx` en el directorio de trabajo de tu proyecto. Al abrir el archivo en Microsoft Word se muestra un botón en la ubicación especificada con el título “Click Me”.

## Conclusión

Ahora sabes cómo **crear un botón de comando ActiveX** en Java, **agregar programáticamente un botón de comando** a un documento Word, y controlar con precisión su diseño usando los métodos **how to set button left top**. Esta técnica abre la puerta a formularios Word ricos e interactivos que pueden activar macros, lanzar aplicaciones externas o recopilar la entrada del usuario directamente dentro del documento.

### Próximos pasos

- Explora otros controles ActiveX como `Forms.TextBox.1` o `Forms.CheckBox.1`.  
- Combina varios controles con un módulo VBA para implementar formularios con todas las funciones.  
- Reemplaza ActiveX con controles de contenido si necesitas compatibilidad multiplataforma.  

Siéntete libre de experimentar con el tamaño, el título y la posición para que coincidan con el diseño de tu UI. Si encuentras problemas, verifica que la versión de Aspose.Words que estás usando admita controles OLE y comprueba que la configuración de seguridad de Word permita la ejecución de ActiveX. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Incorporar objetos OLE y controles ActiveX en documentos Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crear forma rectangular en Word con Java – Guía completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}