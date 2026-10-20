---
category: general
date: 2026-09-27
description: Crear un docx que contenga ActiveX en Java usando Aspose.Words. Aprende
  a insertar un botón de comando ActiveX paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: es
lastmod: 2026-09-27
og_description: Crea un docx que contenga ActiveX en Java con Aspose.Words. Sigue
  esta guía para insertar un botón de comando ActiveX y guardar el documento.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Crear docx con ActiveX en Java – guía completa
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Cómo crear un docx que contenga ActiveX con Java y Aspose.Words
url: /es/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear docx que contiene ActiveX con Java y Aspose.Words

Si necesitas **crear docx que contiene ActiveX**, esta guía te muestra una solución completa. Aprenderás cómo **insertar un botón de comando ActiveX** en un archivo Word usando Aspose.Words para Java, y luego guardar el resultado como un .docx que puede abrirse en Microsoft Word.

Generar un documento Word de forma programática te ahorra la edición manual y garantiza consistencia en informes, contratos o plantillas de formularios. Los pasos a continuación cubren todo, desde la configuración del proyecto hasta el manejo de problemas comunes, para que puedas integrar la técnica en cualquier aplicación Java.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java Development Kit (JDK) 8 o superior instalado.
* Maven 3.6+ (o cualquier otra herramienta de compilación que prefieras).
* Un archivo de licencia de Aspose.Words para Java (la evaluación gratuita sirve para pruebas).
* Microsoft Word instalado en la máquina objetivo si deseas verificar visualmente el control ActiveX.

Estos elementos son necesarios porque Aspose.Words proporciona la API que crea el documento, mientras que Word es necesario para renderizar el control ActiveX.

## Paso 1: Configurar el proyecto Maven

Crea un nuevo proyecto Maven o agrega la dependencia de Aspose.Words a un `pom.xml` existente:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Consejo profesional:** Mantén la versión de Aspose.Words sincronizada con las notas de la versión oficial para beneficiarte de correcciones de errores y nuevas funcionalidades de ActiveX.

## Paso 2: Escribir el código Java que crea el documento

Crea una clase llamada `ActiveXDocxCreator`. El código a continuación incluye todas las importaciones necesarias, un método `main` y comentarios detallados que explican cada operación.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Por qué cada línea es importante

* `Document` es el contenedor de todo el contenido de Word. Crear una nueva instancia te brinda un lienzo limpio.
* `DocumentBuilder` ofrece una API fluida para insertar elementos; rastrea automáticamente el punto de inserción.
* `insertForms2OleControl()` crea un marcador de posición genérico de control OLE. Aspose.Words lo trata como un contenedor ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` indica a Word que el marcador debe renderizarse como un CommandButton.
* `setCaption("Click Me")` define el texto que se muestra en el botón.
* `setLeft` y `setTop` colocan el botón relativo a los márgenes de la página. Ajusta estos valores según tu diseño.
* `setWidth` y `setHeight` son opcionales pero mejoran la apariencia del botón, especialmente cuando el tamaño predeterminado es demasiado pequeño.
* `doc.save` escribe la estructura en memoria a un archivo .docx físico que Word puede abrir.

## Paso 3: Verificar el documento generado

Abre `output/ActiveXCommandButton.docx` en Microsoft Word:

1. El documento debe mostrar una sola página con un botón etiquetado **Click Me** ubicado cerca de la esquina superior izquierda.
2. Si el botón no aparece, verifica que **los controles ActiveX estén habilitados** en el Centro de confianza de Word (Archivo → Opciones → Centro de confianza → Configuración del Centro de confianza → Configuración de ActiveX).
3. El botón funciona solo en versiones de Word para Windows que soportan ActiveX. En macOS o Word basado en web, el control se mostrará como una imagen estática.

## Paso 4: Manejo de casos límite comunes

| Situación | Motivo | Acción recomendada |
|-----------|--------|--------------------|
| El botón falta al abrir el archivo | La configuración de seguridad de Word bloquea ActiveX | Habilita “Ejecutar todos los controles sin restricciones” para ubicaciones de confianza. |
| El .docx generado no se puede abrir | Versión de Aspose.Words incompatible | Actualiza a la última versión de Aspose.Words; versiones anteriores pueden no incrustar correctamente las partes OLE requeridas. |
| Necesitas que el botón ejecute una macro | ActiveX por sí solo no contiene código macro | Combina el control ActiveX con una macro VBA que maneje el evento `Click`. Usa el método `DocumentBuilder.insertOleObject` para incrustar una plantilla habilitada para macros. |
| El diseño se desajusta en tamaños de página diferentes | Las coordenadas son puntos absolutos | Usa `builder.getPageSetup().setPageWidth` y `setPageHeight` para estandarizar el tamaño de página antes de posicionar el control. |

## Paso 5: Extender la solución

Puedes insertar otros controles ActiveX cambiando el enum `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words también soporta la inserción de **cajas de texto ActiveX**, **list boxes** y **combo boxes**. Los mismos métodos de posicionamiento (`setLeft`, `setTop`, `setWidth`, `setHeight`) se aplican.

Si necesitas colocar varios controles, llama a `builder.insertForms2OleControl()` repetidamente y ajusta las coordenadas de cada control según corresponda.

## Archivo fuente completo

A continuación se muestra todo el archivo `ActiveXDocxCreator.java` listo para copiar y pegar:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Ejecutar este programa produce un **docx que contiene ActiveX** que puedes distribuir a los usuarios finales que necesiten formularios interactivos.

## Conclusión

Ahora sabes cómo **crear docx que contiene ActiveX** usando Java y Aspose.Words, y cómo **insertar un botón de comando ActiveX** de forma programática. El tutorial cubrió la configuración del proyecto, el código fuente completo, los pasos de verificación y estrategias para abordar problemas típicos.

A partir de aquí podrías explorar:

* Añadir macros VBA para responder al clic del botón.
* Incrustar otros controles ActiveX como casillas de verificación o combo boxes.
* Automatizar la generación de formularios de varias páginas con datos dinámicos.

Experimenta con diferentes coordenadas, tamaños y tipos de control para adaptarlos a tu diseño de documento específico. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Uso de objetos OLE y controles ActiveX en Aspose.Words para Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}