---
category: general
date: 2026-09-18
description: Crear un documento en blanco en Java y agregar un botón ActiveX. Aprender
  cómo insertar un botón de comando, crear un formulario interactivo y guardar un
  documento de Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: es
lastmod: 2026-09-18
og_description: Crea un documento en blanco en Java e inserta un botón de comando
  ActiveX. Sigue esta guía paso a paso para crear un formulario interactivo y guardar
  el archivo de Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Crear documento en blanco con un botón de comando interactivo en Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Crear documento en blanco con un botón de comando interactivo en Word usando
  Java
url: /es/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento en blanco con un botón de comando interactivo en Word usando Java

Si necesitas **crear un documento en blanco** que contenga un botón clicable, esta guía te muestra exactamente cómo hacerlo con Aspose.Words para Java. Aprenderás a construir un formulario interactivo, agregar un botón ActiveX y, finalmente, guardar el archivo Word, todo en unos pocos pasos concisos.

Insertar un botón de comando convierte un .docx estático en un formulario funcional con el que los usuarios finales pueden interactuar directamente dentro de Microsoft Word. Este tutorial también cubre **cómo insertar un botón de comando**, el manejo de problemas comunes y la ampliación de la solución para formularios más complejos.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o posterior (el código compila con JDK 17+)
* Aspose.Words para Java 23.9 o más reciente – la biblioteca proporciona `Document`, `DocumentBuilder` y `Forms2OleControl`.
* Un IDE o herramienta de compilación (Maven/Gradle) que pueda añadir la dependencia de Aspose.Words.
* Conocimientos básicos de sintaxis Java y conceptos de documentos Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Paso 1: Crear un documento en blanco

La primera operación es instanciar un nuevo objeto `Document`. Este objeto representa un archivo Word vacío listo para recibir contenido.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Crear un documento en blanco te brinda un lienzo limpio, lo cual es esencial cuando deseas **crear un documento Word** programáticamente sin ninguna plantilla preexistente.

## Paso 2: Inicializar un DocumentBuilder

`DocumentBuilder` es la clase principal para agregar texto, tablas y controles de formulario. Trabaja sobre el `Document` que acabas de crear.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder mantiene el punto de inserción actual, de modo que los comandos subsecuentes afectan la ubicación correcta en el archivo.

## Paso 3: Insertar un control de botón de comando Forms2Ole

Aspose.Words expone la clase `Forms2OleControl` para controles ActiveX. Para **agregar un botón activex**, solicitas un tipo `COMMANDBUTTON` al builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

El método `insertForms2OleControl` inserta el control en la posición actual del cursor del builder. Como el control es un objeto ActiveX, solo funciona en la versión de escritorio de Microsoft Word, no en Word Online.

## Paso 4: Configurar la apariencia y posición del botón

Puedes establecer el texto del botón, su tamaño y ubicación mediante los métodos setters del control. Los valores de posición se miden en puntos (1 punto = 1/72 de pulgada).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*¿Por qué configurar estas propiedades?* Establecer `Top` y `Left` garantiza que el botón aparezca donde esperas en la página, mientras que `Caption` define la etiqueta visible para el usuario. Si omites ancho/alto, Word asigna dimensiones predeterminadas, que pueden no coincidir con tu diseño.

### Consejo profesional
Si planeas agregar varios controles, llama a `builder.moveToDocumentEnd()` antes de cada inserción para evitar que los objetos se superpongan.

## Paso 5: Guardar el documento con el botón de comando incrustado

Finalmente, escribe el documento en disco. La extensión del archivo debe ser `.docx` (o `.doc` para versiones más antiguas de Word) para conservar el control ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Al abrir `CommandButton.docx` en Microsoft Word, verás un botón etiquetado **Click Me**. Al hacer clic, se activará la acción predeterminada de ActiveX (que, por defecto, no hace nada). Más adelante puedes adjuntar una macro o script VBA para definir un comportamiento personalizado.

## Cómo insertar un botón de comando en un formulario existente (opcional)

Si ya dispones de un formulario con campos de texto y deseas **crear un formulario interactivo** que incluya un botón, sigue estos pasos adicionales:

1. Carga el documento existente: `Document doc = new Document("ExistingForm.docx");`
2. Mueve el builder a la ubicación deseada: `builder.moveToParagraph(5, 0); // 6.º párrafo, primer nodo`
3. Inserta el botón como se muestra en el Paso 3.
4. Ajusta `Top`/`Left` del botón según el diseño del párrafo.

Este enfoque te permite enriquecer cualquier plantilla Word preconstruida con un botón ActiveX sin recrear todo el archivo.

## Casos límite y solución de problemas

| Situación | Qué comprobar | Corrección recomendada |
|-----------|---------------|------------------------|
| El botón no aparece en Word | Asegúrate de haber abierto el archivo en la versión de escritorio de Word (Word Online elimina ActiveX). | Abre el archivo en Word 2016+ de escritorio. |
| El texto de la etiqueta se corta | Verifica que el ancho del botón sea suficiente para contener el texto. | Incrementa `setWidth` hasta que la etiqueta quepa. |
| Guardado lanza `IOException` | Confirma que el directorio de salida exista y que tengas permisos de escritura. | Crea el directorio o ejecuta el programa con privilegios elevados. |
| Varios botones se superponen | Es posible que el cursor del builder no se haya movido después de la inserción anterior. | Llama a `builder.moveToDocumentEnd()` antes de insertar cada nuevo control. |

## Ejemplo completo y ejecutable

A continuación se muestra un programa Java completo, autocontenido, que puedes copiar, compilar y ejecutar. Demuestra **crear documento en blanco**, **agregar un botón activex** y **guardar el documento Word** en un solo flujo.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Salida esperada**

```
Document created: CommandButton.docx
```

Al abrir `CommandButton.docx` se muestra una sola página con un botón etiquetado **Click Me** posicionado a 100 pt del borde superior y del izquierdo.

## Conclusión

Ahora sabes cómo **crear un documento en blanco**, incrustar un **botón ActiveX** y convertir un archivo Word simple en un **formulario interactivo**. Al dominar **cómo insertar un botón de comando**, puedes ampliar este patrón para agregar casillas de verificación, cuadros combinados o incluso lógica personalizada mediante VBA.

A continuación, considera explorar estos temas relacionados:

* **Crear formulario interactivo** con campos de texto (`builder.insertField`)  
* **Agregar botón activex** que ejecute una macro VBA (`builder.insertOleObject`)  
* **Crear documento Word** a partir de una plantilla usando `Document(docTemplatePath)`  
* Convertir el .docx resultante a PDF manteniendo el botón (nota: el PDF mostrará el botón como una imagen estática).

Siéntete libre de experimentar con el tamaño, posición y etiqueta del botón para que coincidan con tu diseño UI. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crear proyecto VBA en documento Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Crear nuevo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}